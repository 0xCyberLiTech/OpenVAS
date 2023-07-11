![OpenVAS](./images/OpenVAS.png)

# OnpenVAS

Prérequis :

Vous devez avoir une machine sous Linux (Debian 11 ou 12) avec Docker d’installé et docker-compose.

Vous trouverez ici un tutoriel sur l’installation de Docker, Docker-compose & Portainer.

- Installation manuelle de Docker, [disponible ici](https://github.com/0xCyberLiTech/Docker/blob/main/README.md#installation-manuelle-de-docker)

- Installation manuelle de Docker-compose, [disponible ici](https://github.com/0xCyberLiTech/Docker/blob/main/README.md#installation-manuelle-de-docker-compose)

- Installation manuelle de Portainer, [disponible ici](https://github.com/0xCyberLiTech/Docker/blob/main/README.md#mise-%C3%A0-jour-manuelle-de-portainer)

Prenez par habitude de stocker vos containers de la manière suivante :
```
~/containers/<stack-name>
```
```
mkdir -p ~/containers/<stack-name>
mkdir -p ~/containers/openvas
```
Déploiement des conteneurs pour OpenVas :

On va commencer pas créer le fichier docker-compose.yml et ensuite l’ouvrir avec nano :
```
touch docker-compose.yml
nano docker-compose.yml
```
Copier le code au complet ci-dessous dans le fichier docker-compose.yml.
```
version: '3.8'
# Ubuntu 22.04
services:
  redis-server:
    image: greenbone/redis-server
    restart: on-failure
    volumes:
      - redis_socket_vol:/run/redis/

  gpg-data:
    image: greenbone/gpg-data
    volumes:
      - gpg_data_vol:/mnt

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
      - vt_data_vol:/var/lib/openvas
      - psql_data_vol:/var/lib/postgresql
      - gvmd_socket_vol:/run/gvmd
      - ospd_openvas_socket_vol:/run/ospd
      - psql_socket_vol:/var/run/postgresql
    depends_on:
      - pg-gvm

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
    cap_add:
      - NET_ADMIN # for capturing packages in promiscuous mode
      - NET_RAW # for raw sockets e.g. used for the boreas alive detection
    security_opt:
      - seccomp=unconfined
      - apparmor=unconfined
    command: [
      "ospd-openvas",
      "-f",
      "--config", "/etc/gvm/ospd-openvas.conf",
      "--mqtt-broker-address", "mqtt-broker",
      "--notus-feed-dir", "/var/lib/notus/advisories",
      "-m", "666",
    ]
    volumes:
      - gpg_data_vol:/etc/openvas/gnupg
      - vt_data_vol:/var/lib/openvas
      - notus_data_vol:/var/lib/notus
      - ospd_openvas_socket_vol:/run/ospd
      - redis_socket_vol:/run/redis/
    depends_on:
      - redis-server
      - gpg-data

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
      NOTUS_SCANNER_PRODUCTS_DIRECTORY: /var/lib/notus
    depends_on:
      - mqtt-broker
      - gpg-data

volumes:
  gpg_data_vol:
  gvmd_data_vol:
  psql_data_vol:
  vt_data_vol:
  notus_data_vol:
  psql_socket_vol:
  gvmd_socket_vol:
  ospd_openvas_socket_vol:
  redis_socket_vol:

```
Enregistrer et fermer le fichier docker-compose.yml.

Télécharger les différentes images :
```
docker-compose -p greenbone-community-edition pull
```
Une fois les images téléchargés, démarrer les :
```
docker-compose -p greenbone-community-edition up -d
```
Vous pouvez vérifier que les conteneurs sont bien démarrés avec la commande :
```
sudo docker ps
```
- Synchronisation des tests de vulnérabilités et des données de vulnérabilités. Cette phase va être plus longue, l’injection des données de vulnérabilités et les tests, pour le moment OpenVAS ne contient aucune données.

Pour cette partie, il faut prévoir 1 à 2 heures.

On va commencer par injecter les différents tests de vulnérabilité, pour cela entrer la commande :
```
docker-compose -p greenbone-community-edition exec -u ospd-openvas ospd-openvas greenbone-nvt-sync
```
Il faut maintenant patienter pour passer à la suite, car celle-ci sont en cours d’injection dans la base de données, le seul moyen que j’ai trouvé pour vérifier l’avancement, c’est de vérifier la charge CPU avec la commande htop.

Quand la charge du serveur est de nouveau faible, on peut considérer que l’injection des données en base est terminée.

- Synchronisation des données SCAP, CERT et GVMD.

Maintenant, on va passer à la synchronisation des données SCAP, CERT et GVMD, le procédure est identique pour la synchronisation des tests, après le téléchargement, patienter pendant l’injection dans la base de données.

- SCAP :
```
docker-compose -p greenbone-community-edition exec -u gvmd gvmd greenbone-feed-sync --type SCAP
```
- CERT :
```
docker-compose -p greenbone-community-edition exec -u gvmd gvmd greenbone-feed-sync --type CERT
```
- GVMD :
```
docker-compose -p greenbone-community-edition exec -u gvmd gvmd greenbone-feed-sync --type GVMD_DATA
```
Le scanner de vulnérabilité est prêt à être utilser.

Utiliser le scanner de vulnérabilités – Greenbone – OpenVAS

OpenVAS s’utilise à l’aide d’un navigateur Internet, depuis un navigateur Internet, entrer l’ip ou l’url du serveur sur le port 9392 : http://ip:9392

Les identifiants par défaut sont admin / admin.

