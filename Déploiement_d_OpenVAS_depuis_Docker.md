![OpenVAS](./images/OpenVAS.png)

# OnpenVAS

Prérequis :

Vous devez avoir une machine sous Linux (Debian 11 ou 12) avec Docker d’installé et docker-compose.

Vous trouverez ici un tutoriel sur l’installation de Docker, Docker-compose & Portainer.

- Installation manuelle de Docker, [disponible ici](https://github.com/0xCyberLiTech/Docker/blob/main/README.md#installation-manuelle-de-docker)

- Installation manuelle de Docker-compose, [disponible ici](https://github.com/0xCyberLiTech/Docker/blob/main/README.md#installation-manuelle-de-docker-compose)

- Installation manuelle de Portainer, [disponible ici](https://github.com/0xCyberLiTech/Docker/blob/main/README.md#mise-%C3%A0-jour-manuelle-de-portainer)

Stocker vos containers de la manière suivante :
```
~/containers/<stack-name>
```
```
mkdir -p ~/containers/<stack-name>/
mkdir -p ~/containers/openvas/
cd ~/containers/openvas/
```
Déploiement des conteneurs pour OpenVas :

Conditions préalables :

- Note.

Veuillez suivre le guide étape par étape. Les étapes ultérieures peuvent nécessiter des paramètres ou sortie d’une commande précédente.

La commande sudo est utilisée pour exécuter des commandes qui nécessitent un privilège accès sur le système.

- Installer curl :

Curl est requis pour télécharger des fichiers à partir de ce guide.
```
sudo apt install curl
```
Installation de docker-compose.

docker-compose version 1.29.0 ou plus récente est requis pour démarrer et se connecter les services de Greenbone Community Edition. La description du service L’orchestration s’effectue à l’aide de fichiers de composition. Un fichier de composition pour Greenbone Community Edition est fourni ultérieurement.


Installer le paquet Debian docker-compose.
```
sudo apt install python3 python3-pip
python3 -m pip install --user docker-compose
```
Coup monté.

Pour permettre à l’utilisateur actuel d’exécuter docker et donc de démarrer le conteneurs, ils doivent être ajoutés au groupe d’utilisateurs Docker. Pour modifier le groupe Effectivement, déconnectez-vous et reconnectez-vous ou utilisez SU.

Ajouter l’utilisateur actuel au groupe docker et appliquer les modifications de groupe pour l’environnement shell actuel.
```
sudo usermod -aG docker $USER && su $USER
```
Pour télécharger le fichier de composition docker Greenbone Community Edition, un Le répertoire de destination doit être créé.

Créer un répertoire de téléchargement.
```
export DOWNLOAD_DIR=$HOME/greenbone-community-container && mkdir -p $DOWNLOAD_DIR
```
Fichier de composition Docker.

Pour exécuter Greenbone Community Edition avec des conteneurs, les éléments suivants sont composés doit être utilisé:

Fichier de composition Docker.

```
services:
  vulnerability-tests:
    image: greenbone/vulnerability-tests
    environment:
      STORAGE_PATH: /var/lib/openvas/22.04/vt-data/nasl
    volumes:
      - vt_data_vol:/mnt

  notus-data:
    image: greenbone/notus-data
    volumes:
      - notus_data_vol:/mnt

  scap-data:
    image: greenbone/scap-data
    volumes:
      - scap_data_vol:/mnt

  cert-bund-data:
    image: greenbone/cert-bund-data
    volumes:
      - cert_data_vol:/mnt

  dfn-cert-data:
    image: greenbone/dfn-cert-data
    volumes:
      - cert_data_vol:/mnt
    depends_on:
      - cert-bund-data

  data-objects:
    image: greenbone/data-objects
    volumes:
      - data_objects_vol:/mnt

  report-formats:
    image: greenbone/report-formats
    volumes:
      - data_objects_vol:/mnt
    depends_on:
      - data-objects

  gpg-data:
    image: greenbone/gpg-data
    volumes:
      - gpg_data_vol:/mnt

  redis-server:
    image: greenbone/redis-server
    restart: on-failure
    volumes:
      - redis_socket_vol:/run/redis/

  pg-gvm:
    image: greenbone/pg-gvm:stable
    restart: on-failure
    volumes:
      - psql_data_vol:/var/lib/postgresql
      - psql_socket_vol:/var/run/postgresql

  gvmd:
    image: greenbone/gvmd:stable
    restart: on-failure
    volumes:
      - gvmd_data_vol:/var/lib/gvm
      - scap_data_vol:/var/lib/gvm/scap-data/
      - cert_data_vol:/var/lib/gvm/cert-data
      - data_objects_vol:/var/lib/gvm/data-objects/gvmd
      - vt_data_vol:/var/lib/openvas/plugins
      - psql_data_vol:/var/lib/postgresql
      - gvmd_socket_vol:/run/gvmd
      - ospd_openvas_socket_vol:/run/ospd
      - psql_socket_vol:/var/run/postgresql
    depends_on:
      pg-gvm:
        condition: service_started
      scap-data:
        condition: service_completed_successfully
      cert-bund-data:
        condition: service_completed_successfully
      dfn-cert-data:
        condition: service_completed_successfully
      data-objects:
        condition: service_completed_successfully
      report-formats:
        condition: service_completed_successfully

  gsa:
    image: greenbone/gsa:stable
    restart: on-failure
    ports:
      - 9392:80
    volumes:
      - gvmd_socket_vol:/run/gvmd
    depends_on:
      - gvmd

  ospd-openvas:
    image: greenbone/ospd-openvas:stable
    restart: on-failure
    init: true
    hostname: ospd-openvas.local
    cap_add:
      - NET_ADMIN # for capturing packages in promiscuous mode
      - NET_RAW # for raw sockets e.g. used for the boreas alive detection
    security_opt:
      - seccomp=unconfined
      - apparmor=unconfined
    command:
      [
        "ospd-openvas",
        "-f",
        "--config",
        "/etc/gvm/ospd-openvas.conf",
        "--mqtt-broker-address",
        "mqtt-broker",
        "--notus-feed-dir",
        "/var/lib/notus/advisories",
        "-m",
        "666"
      ]
    volumes:
      - gpg_data_vol:/etc/openvas/gnupg
      - vt_data_vol:/var/lib/openvas/plugins
      - notus_data_vol:/var/lib/notus
      - ospd_openvas_socket_vol:/run/ospd
      - redis_socket_vol:/run/redis/
    depends_on:
      redis-server:
        condition: service_started
      gpg-data:
        condition: service_completed_successfully
      vulnerability-tests:
        condition: service_completed_successfully

  mqtt-broker:
    restart: on-failure
    image: greenbone/mqtt-broker
    ports:
      - 1883:1883
    networks:
      default:
        aliases:
          - mqtt-broker
          - broker

  notus-scanner:
    restart: on-failure
    image: greenbone/notus-scanner:stable
    volumes:
      - notus_data_vol:/var/lib/notus
      - gpg_data_vol:/etc/openvas/gnupg
    environment:
      NOTUS_SCANNER_MQTT_BROKER_ADDRESS: mqtt-broker
      NOTUS_SCANNER_PRODUCTS_DIRECTORY: /var/lib/notus/products
    depends_on:
      - mqtt-broker
      - gpg-data
      - vulnerability-tests

  gvm-tools:
    image: greenbone/gvm-tools
    volumes:
      - gvmd_socket_vol:/run/gvmd
      - ospd_openvas_socket_vol:/run/ospd
    depends_on:
      - gvmd
      - ospd-openvas

volumes:
  gpg_data_vol:
  scap_data_vol:
  cert_data_vol:
  data_objects_vol:
  gvmd_data_vol:
  psql_data_vol:
  vt_data_vol:
  notus_data_vol:
  psql_socket_vol:
  gvmd_socket_vol:
  ospd_openvas_socket_vol:
  redis_socket_vol:
```
Description.

Le tableau suivant décrit les conteneurs fournis du fichier de composition docker et leurs services en détail.

| Conteneur |  Service |  Description    |
|-----------|----------|-----------------|
| redis-serveur | Serveur Redis | Un serveur redis avec une configuration ajustée. Utilisé pour stocker les données VT et numériser les résultats par le scanner. |
| pg-gvm | PostgreSQL | Une configuration de cluster de base de données PostgreSQL à utiliser avec gvmd. Les données réelles sont stockées dans le volume.psql_data_vol |
| gvmd | gvmd | Conteneur pour gvmd qui utilise des sockets unix dans les volumes pour communiquer avec la base de données PostgreSQL et l’analyseur ospd-openvas. Les données de flux téléchargées sont stockées dans le volume. Pour vérifier les données d’alimentation, le trousseau de clés GPG du est utilisé.gvmd_data_volgpg_data_vol |
| Gsa | Le | Conteneur exécutant le serveur Web gsad pour fournir l’application Web GSA. L’interface Web est disponible sur localhost sur le port 9392. Pour la communication avec gvmd, un socket unix dans un volume est utilisé. |
| ospd-openvas | ospd-openvas | Un conteneur fournissant le scanner de vulnérabilité. Les données VT du flux sont stockées dans le volume. Pour vérifier les données d’alimentation, le trousseau de clés GPG du est utilisé. La connexion au serveur redis est établie via un socket unix dans un volume.vt_data_volgpg_data_vol |
| mqtt-broker | Mosquitto MQTT Broker | Un MQTT Broker utilisé pour la communication entre notus-scanner, openvas-scanner et ospd-openvas. |
| notus-scanner | notus-scanner | Conteneur exécutant le scanner notus utilisé pour les contrôles de sécurité locaux. Pour vérifier les données d’alimentation, le trousseau de clés GPG du est utilisé. Les données d’alimentation pour notus-scanner lui-même sont stockées dans le fichier .gpg_data_volnotus_data_vol |
| gvm-tools |  | Un conteneur fournissant l’interface de ligne de commande gvm-tools pour interroger et contrôler gvmd et ospd-openvas. |
| gpg-data  |  | Conteneur qui copie un trousseau de clés GPG avec les clés de signature publiques de Greenbone dans le volume au démarrage. Il sort après.gpg_data_vol |
| tests de vulnérabilité |  | Conteneur qui copie les tests de vulnérabilité (VT) dans le volume au démarrage. Affiche la licence et se ferme par la suite.vt_data_vol |
| notus-data |  | Conteneur qui copie les informations de vulnérabilité de notus-scanner dans le volume au démarrage. Affiche la licence et se ferme par la suite.notus_data_vol |
| scap-data  |  | Conteneur qui copie les données CVE et CPE dans le volume au démarrage. Affiche la licence et se ferme par la suite.scap_data_vol |
| cert-bund-data |  | Conteneur qui copie les données CERT-Bund dans le volume au démarrage. Affiche la licence et se ferme par la suite.cert_data_vol |
| dfn-cert-data |  | Conteneur qui copie les données DFN-CERT dans le volume au démarrage. Affiche la licence et se ferme par la suite.cert_data_vol |
| objets_données |  | Conteneur qui copie les configurations d’analyse, les stratégies de conformité et les listes de ports dans le volume au démarrage. Affiche la licence et se ferme par la suite.data_objects_vol |
| formats de rapport |  | Conteneur qui copie les formats de rapport dans le volume au démarrage. Affiche la licence et se ferme par la suite.data_objects_vol |

