



## Prérequis :

Avoir Docker + docker compose d'installé et opérationnel/

Pour permettre à l’utilisateur actuel d’exécuter docker et donc de démarrer le conteneurs, ils doivent être ajoutés au groupe d’utilisateurs Docker.

Pour effectuer la modification du groupe Pour être efficace, soit vous déconnecter et vous reconnecter, soit utiliser SU.

Ajouter l’utilisateur actuel au groupe docker et appliquer les modifications de groupe à l’environnement de shell actuel :

```bash
sudo usermod -aG docker $USER && su $USER
```

Installer des dépendances :

Il y a quelques dépendances requises pour les étapes suivantes, comme curl, qui est requis pour télécharger des fichiers à partir de ce guide.

```bash
sudo apt install ca-certificates curl gnupg
```

## Passons maintenant au déploiement d'OpenVAS :

Pour télécharger le fichier de composition du docker **Greenbone Community Edition**, un répertoire de destination doit être créé.

Créer un répertoire de téléchargement :

```bash
export DOWNLOAD_DIR=$HOME/greenbone-community-container && mkdir -p $DOWNLOAD_DIR
```

**Important**

- Assurez-vous toujours d’utiliser la **dernière version** du fichier en suivant ce guide. 
- Le fichier peut recevoir des mises à jour et des modifications importantes depuis votre dernier téléchargement de docker-compose.yml

Pour exécuter Greenbone Community vous pouvez utiliser deux méthodes :

1). Récupération manuel du fichier docker-compose.yml
2). Téléchargement du fichier docker-compose.yml

1). Récupération manuel du fichier docker-compose.yml depuis le site

Fichier : docker-compose.yml

```bash
nano docker-compose.yml
```

```
services:
  vulnerability-tests:
    image: registry.community.greenbone.net/community/vulnerability-tests
    environment:
      FEED_RELEASE: "24.10"
    volumes:
      - vt_data_vol:/mnt

  notus-data:
    image: registry.community.greenbone.net/community/notus-data
    volumes:
      - notus_data_vol:/mnt

  scap-data:
    image: registry.community.greenbone.net/community/scap-data
    volumes:
      - scap_data_vol:/mnt

  cert-bund-data:
    image: registry.community.greenbone.net/community/cert-bund-data
    volumes:
      - cert_data_vol:/mnt

  dfn-cert-data:
    image: registry.community.greenbone.net/community/dfn-cert-data
    volumes:
      - cert_data_vol:/mnt
    depends_on:
      - cert-bund-data

  data-objects:
    image: registry.community.greenbone.net/community/data-objects
    environment:
      FEED_RELEASE: "24.10"
    volumes:
      - data_objects_vol:/mnt

  report-formats:
    image: registry.community.greenbone.net/community/report-formats
    environment:
      FEED_RELEASE: "24.10"
    volumes:
      - data_objects_vol:/mnt
    depends_on:
      - data-objects

  gpg-data:
    image: registry.community.greenbone.net/community/gpg-data
    volumes:
      - gpg_data_vol:/mnt

  redis-server:
    image: registry.community.greenbone.net/community/redis-server
    restart: on-failure
    volumes:
      - redis_socket_vol:/run/redis/

  pg-gvm:
    image: registry.community.greenbone.net/community/pg-gvm:stable
    restart: on-failure
    volumes:
      - psql_data_vol:/var/lib/postgresql
      - psql_socket_vol:/var/run/postgresql

  gvmd:
    image: registry.community.greenbone.net/community/gvmd:stable
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
    image: registry.community.greenbone.net/community/gsa:stable
    restart: on-failure
    ports:
      - 127.0.0.1:9392:80
    volumes:
      - gvmd_socket_vol:/run/gvmd
    depends_on:
      - gvmd
  # Sets log level of openvas to the set LOG_LEVEL within the env
  # and changes log output to /var/log/openvas instead /var/log/gvm
  # to reduce likelyhood of unwanted log interferences
  configure-openvas:
    image: registry.community.greenbone.net/community/openvas-scanner:stable
    volumes:
      - openvas_data_vol:/mnt
      - openvas_log_data_vol:/var/log/openvas
    command:
      - /bin/sh
      - -c
      - |
        printf "table_driven_lsc = yes\nopenvasd_server = http://openvasd:80\n" > /mnt/openvas.conf
        sed "s/127/128/" /etc/openvas/openvas_log.conf | sed 's/gvm/openvas/' > /mnt/openvas_log.conf
        chmod 644 /mnt/openvas.conf
        chmod 644 /mnt/openvas_log.conf
        touch /var/log/openvas/openvas.log
        chmod 666 /var/log/openvas/openvas.log

  # shows logs of openvas
  openvas:
    image: registry.community.greenbone.net/community/openvas-scanner:stable
    restart: on-failure
    volumes:
      - openvas_data_vol:/etc/openvas
      - openvas_log_data_vol:/var/log/openvas
    command:
      - /bin/sh
      - -c
      - |
        cat /etc/openvas/openvas.conf
        tail -f /var/log/openvas/openvas.log
    depends_on:
      configure-openvas:
        condition: service_completed_successfully

  openvasd:
    image: registry.community.greenbone.net/community/openvas-scanner:stable
    restart: on-failure
    environment:
      # `service_notus` is set to disable everything but notus,
      # if you want to utilize openvasd directly, remove `OPENVASD_MODE`
      OPENVASD_MODE: service_notus
      GNUPGHOME: /etc/openvas/gnupg
      LISTENING: 0.0.0.0:80
    volumes:
      - openvas_data_vol:/etc/openvas
      - openvas_log_data_vol:/var/log/openvas
      - gpg_data_vol:/etc/openvas/gnupg
      - notus_data_vol:/var/lib/notus
    # enable port forwarding when you want to use the http api from your host machine
    # ports:
    #   - 127.0.0.1:3000:80
    depends_on:
      vulnerability-tests:
        condition: service_completed_successfully
      configure-openvas:
        condition: service_completed_successfully
      gpg-data:
        condition: service_completed_successfully
    networks:
      default:
        aliases:
          - openvasd

  ospd-openvas:
    image: registry.community.greenbone.net/community/ospd-openvas:stable
    restart: on-failure
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
        "--notus-feed-dir",
        "/var/lib/notus/advisories",
        "-m",
        "666",
      ]
    volumes:
      - gpg_data_vol:/etc/openvas/gnupg
      - vt_data_vol:/var/lib/openvas/plugins
      - notus_data_vol:/var/lib/notus
      - ospd_openvas_socket_vol:/run/ospd
      - redis_socket_vol:/run/redis/
      - openvas_data_vol:/etc/openvas/
      - openvas_log_data_vol:/var/log/openvas
    depends_on:
      redis-server:
        condition: service_started
      gpg-data:
        condition: service_completed_successfully
      vulnerability-tests:
        condition: service_completed_successfully
      configure-openvas:
        condition: service_completed_successfully

  gvm-tools:
    image: registry.community.greenbone.net/community/gvm-tools
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
  openvas_data_vol:
  openvas_log_data_vol:
```

2). Téléchargement du fichier docker-compose.yml


```bash
pwd
```

```bash
/home/user/
```

```bash
mkdir Docker-containers
```

```bash
cd Docker-containers/
```

Il peut être téléchargé directement avec la commande suivante :

```bash
curl -f -O -L https://greenbone.github.io/docs/latest/_static/docker-compose.yml --output-dir "$DOWNLOAD_DIR"
```

- Lancement des conteneurs communautaires Greenbone :
-----------------------------------------------------
À l’aide du fichier docker compose, les images du conteneur peuvent être téléchargées (extraites) Et les conteneurs peuvent être démarrés en arrière-plan.

Téléchargement des conteneurs communautaires Greenbone

```bash
sudo docker compose -f $DOWNLOAD_DIR/docker-compose.yml -p greenbone-community-edition pull
```

- Lancement des conteneurs communautaires Greenbone :
-----------------------------------------------------

```bash
sudo docker compose -f $DOWNLOAD_DIR/docker-compose.yml -p greenbone-community-edition up -d
```

- Pour obtenir un flux continu de la sortie du journal de tous les services, exécutez ce qui suit commander :
-------------------------------------------------------------------------------------------------------------

Afficher les messages de journal de tous les services des conteneurs en cours d’exécution

```bash
sudo docker compose -f docker-compose.yml logs -f
```

Le flux de journaux peut être arrêté en appuyant sur (Ctrl-C)


- Configuration d’un utilisateur administrateur :
-------------------------------------------------

Avertissement

Par défaut, un utilisateur admin avec le mot de passe admin est créé. Ce n’est pas sûr Et il est fortement recommandé de définir un nouveau mot de passe.

Pour mettre à jour l’utilisateur administrateur avec un mot de passe de votre choix au lieu de l’icône mot de passe généré, la commande suivante peut être utilisée :

Mise à jour du mot de passe de l’utilisateur administrateur

```bash
sudo docker compose -f docker-compose.yml \
    exec -u gvmd gvmd gvmd --user=admin --new-password='MonMotDePasse'
```

Note

Veuillez faire attention si votre mot de passe comprend des caractères spéciaux comme il en a besoin à citer entre guillemets simples.$

- Démarrage de la gestion des vulnérabilités :
----------------------------------------------
Une fois que les services ont démarré et que toutes les données du flux ont été chargées, l’interface Web de Greenbone Security Assistant – GSA – peut être ouverte dans le navigateur.

Ouverture de Greenbone Security Assistant dans le navigateur :

xdg-open "http://127.0.0.1:9392" 2>/dev/null >/dev/null &

Le navigateur affichera la page de connexion de GSA et après avoir utilisé les informations d’identification Créé auparavant, il est possible de commencer par l’analyse des vulnérabilités.
