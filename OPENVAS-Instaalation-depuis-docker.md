<div align="center">

  <br></br>
  
  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3EOPENVAS_" alt="Titre dynamique OPENVAS" />
  </a>
  
  <br></br>
  
  <h2>Laboratoire numérique pour la cybersécurité, Linux & IT.</h2>

  <p align="center">
    <a href="https://0xcyberlitech.github.io/">
      <img src="https://img.shields.io/badge/Portfolio-0xCyberLiTech-181717?logo=github&style=flat-square" alt="🌐 Portfolio" />
    </a>
    <a href="https://github.com/0xCyberLiTech">
      <img src="https://img.shields.io/badge/Profil-GitHub-181717?logo=github&style=flat-square" alt="🔗 Profil GitHub" />
    </a>
    <a href="https://github.com/0xCyberLiTech/OpenVAS/releases/latest">
      <img src="https://img.shields.io/github/v/release/0xCyberLiTech/OpenVAS?label=version&style=flat-square&color=blue" alt="📦 Dernière version" />
    </a>
    <a href="https://github.com/0xCyberLiTech/OpenVAS/blob/main/CHANGELOG.md">
      <img src="https://img.shields.io/badge/📄%20Changelog-OpenVAS-blue?style=flat-square" alt="📄 CHANGELOG OpenVAS" />
    </a>
    <a href="https://github.com/0xCyberLiTech?tab=repositories">
      <img src="https://img.shields.io/badge/Dépôts-publics-blue?style=flat-square" alt="📂 Dépôts publics" />
    </a>
    <a href="https://github.com/0xCyberLiTech/OpenVAS/graphs/contributors">
      <img src="https://img.shields.io/badge/👥%20Contributeurs-cliquez%20ici-007ec6?style=flat-square" alt="👥 Contributeurs OpenVAS" />
    </a>
  </p>

</div>

<div align="center">
  <img src="https://img.icons8.com/fluency/96/000000/cyber-security.png" alt="CyberSec" width="80"/>
</div>

<div align="center">
  <p>
    <strong>Cybersécurité</strong> <img src="https://img.icons8.com/color/24/000000/lock--v1.png"/> • <strong>Linux Debian</strong> <img src="https://img.icons8.com/color/24/000000/linux.png"/> • <strong>Sécurité informatique</strong> <img src="https://img.icons8.com/color/24/000000/shield-security.png"/>
  </p>
</div>

---

<div align="center">
  
## À propos & Objectifs.

</div>

Ce projet propose des solutions innovantes et accessibles en cybersécurité, avec une approche centrée sur la simplicité d’utilisation et l’efficacité. Il vise à accompagner les utilisateurs dans la protection de leurs données et systèmes, tout en favorisant l’apprentissage et le partage des connaissances.

Le contenu est structuré, accessible et optimisé SEO pour répondre aux besoins de :
- 🎓 Étudiants : approfondir les connaissances
- 👨‍💻 Professionnels IT : outils et pratiques
- 🖥️ Administrateurs système : sécuriser l’infrastructure
- 🛡️ Experts cybersécurité : ressources techniques
- 🚀 Passionnés du numérique : explorer les bonnes pratiques

---

# Présentation — Installation et déploiement de Greenbone Community Edition (Docker)

Ce document présente, de manière professionnelle et organisée, les étapes nécessaires pour installer Docker et déployer Greenbone Community Edition à l'aide des conteneurs fournis.

--

## Dépendances d'installation

Avant de commencer, installez les dépendances requises (ex. : `curl`, `ca-certificates`, `gnupg`) :

```bash
sudo apt update
sudo apt install -y ca-certificates curl gnupg
```

Ces outils sont nécessaires pour télécharger des fichiers et ajouter des dépôts sécurisés.

--

## Installation de Docker

Docker est requis pour exécuter les services dans des conteneurs. Les étapes suivantes proviennent du guide officiel d'installation du moteur Docker.

1. Désinstallez les paquets Debian conflictuels :

```bash
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt remove -y $pkg; done
```

2. Configurez le dépôt Docker :

```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
echo \ 
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \ 
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \ 
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
```

3. Installez Docker et les paquets associés :

```bash
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

--

## Mise en place — Permettre l'utilisation de Docker sans sudo

Ajoutez l'utilisateur courant au groupe `docker` pour pouvoir exécuter Docker sans `sudo` :

```bash
sudo usermod -aG docker $USER && su $USER
```

Vous pouvez aussi vous déconnecter/reconnecter pour que la modification de groupe soit prise en compte.

--

## Préparer un répertoire de téléchargement

Créez un répertoire de travail pour télécharger le fichier `compose.yaml` et autres artefacts :

```bash
export DOWNLOAD_DIR=$HOME/greenbone-community-container && mkdir -p "$DOWNLOAD_DIR"
```

--

## Fichier Docker Compose

Important : utilisez toujours la dernière version du fichier `compose.yaml` fournie par Greenbone. Le fichier ci-dessous est fourni à titre d'exemple — il peut évoluer.

```yaml
# Fichier d'exemple (extrait)
name: greenbone-community-edition

services:
  vulnerability-tests:
    image: registry.community.greenbone.net/community/vulnerability-tests
    environment:
      FEED_RELEASE: "24.10"
      KEEP_ALIVE: 1
    volumes:
      - vt_data_vol:/mnt

  notus-data:
    image: registry.community.greenbone.net/community/notus-data
    environment:
      KEEP_ALIVE: 1
    volumes:
      - notus_data_vol:/mnt

  scap-data:
    image: registry.community.greenbone.net/community/scap-data
    environment:
      KEEP_ALIVE: 1
    volumes:
      - scap_data_vol:/mnt

  cert-bund-data:
    image: registry.community.greenbone.net/community/cert-bund-data
    environment:
      KEEP_ALIVE: 1
    volumes:
      - cert_data_vol:/mnt

  dfn-cert-data:
    image: registry.community.greenbone.net/community/dfn-cert-data
    environment:
      KEEP_ALIVE: 1
    volumes:
      - cert_data_vol:/mnt
    depends_on:
      cert-bund-data:
        condition: service_healthy

  data-objects:
    image: registry.community.greenbone.net/community/data-objects
    environment:
      FEED_RELEASE: "24.10"
      KEEP_ALIVE: 1
    volumes:
      - data_objects_vol:/mnt

  report-formats:
    image: registry.community.greenbone.net/community/report-formats
    environment:
      FEED_RELEASE: "24.10"
      KEEP_ALIVE: 1
    volumes:
      - data_objects_vol:/mnt
    depends_on:
      data-objects:
        condition: service_healthy

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
    restart: on-failure:10
    volumes:
      - psql_data_vol:/var/lib/postgresql
      - psql_socket_vol:/var/run/postgresql
    depends_on:
      pg-gvm-migrator:
        condition: service_completed_successfully

  pg-gvm-migrator:
    image: registry.community.greenbone.net/community/pg-gvm-migrator:stable
    restart: no
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
        condition: service_healthy
      cert-bund-data:
        condition: service_healthy
      dfn-cert-data:
        condition: service_healthy
      data-objects:
        condition: service_healthy
      report-formats:
        condition: service_healthy

  gsa:
    image: registry.community.greenbone.net/community/gsa:stable-slim
    environment:
      MOUNT_PATH: "/mnt/web"
      KEEP_ALIVE: 1
    healthcheck:
      test: ["CMD-SHELL", "test -e /run/gsa/copying.done"]
      start_period: 5s
    volumes:
      - gsa_data_vol:/mnt/web

  gsad:
    image: registry.community.greenbone.net/community/gsad:stable
    restart: on-failure
    environment:
      GSAD_ARGS: "--listen=0.0.0.0 --http-only --api-only -f"
    volumes:
      - gvmd_socket_vol:/run/gvmd
    depends_on:
      gvmd:
        condition: service_started

  gvm-config:
    image: registry.community.greenbone.net/community/gvm-config:latest
    environment:
      ENABLE_NGINX_CONFIG: true
      ENABLE_TLS_GENERATION: true
    volumes:
      - nginx_config_vol:/mnt/nginx/configs
      - nginx_certificates_vol:/mnt/nginx/certs

  nginx:
    image: registry.community.greenbone.net/community/nginx:latest
    ports:
      - 127.0.0.1:443:443
      - 127.0.0.1:9392:9392
    volumes:
      - nginx_config_vol:/etc/nginx/conf.d:ro
      - nginx_certificates_vol:/etc/nginx/certs:ro
      - gsa_data_vol:/usr/share/nginx/html:ro
    depends_on:
      gvm-config:
        condition: service_completed_successfully
      gsa:
        condition: service_healthy
      gsad:
        condition: service_started

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
      OPENVASD_MODE: service_notus
      GNUPGHOME: /etc/openvas/gnupg
      LISTENING: 0.0.0.0:80
    volumes:
      - openvas_data_vol:/etc/openvas
      - openvas_log_data_vol:/var/log/openvas
      - gpg_data_vol:/etc/openvas/gnupg
      - notus_data_vol:/var/lib/notus
    depends_on:
      vulnerability-tests:
        condition: service_healthy
      notus-data:
        condition: service_healthy
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
      - NET_ADMIN
      - NET_RAW
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
      configure-openvas:
        condition: service_completed_successfully
      vulnerability-tests:
        condition: service_healthy
      notus-data:
        condition: service_healthy

  gvm-tools:
    image: registry.community.greenbone.net/community/gvm-tools
    volumes:
      - gvmd_socket_vol:/run/gvmd
      - ospd_openvas_socket_vol:/run/ospd
    depends_on:
      - gvmd
      - ospd-openvas

volumes:
  gpg_data_vol: {}
  scap_data_vol: {}
  cert_data_vol: {}
  data_objects_vol: {}
  gvmd_data_vol: {}
  psql_data_vol: {}
  vt_data_vol: {}
  notus_data_vol: {}
  psql_socket_vol: {}
  gvmd_socket_vol: {}
  ospd_openvas_socket_vol: {}
  redis_socket_vol: {}
  openvas_data_vol: {}
  openvas_log_data_vol: {}
  gsa_data_vol: {}
  nginx_config_vol: {}
  nginx_certificates_vol: {}
```

> Remarque : pour la version officielle et à jour, consultez : https://greenbone.github.io/docs/latest/

--

## Télécharger le fichier `compose.yaml`

Vous pouvez télécharger directement le fichier officiel :

```bash
curl -f -L -o "$DOWNLOAD_DIR/compose.yaml" https://greenbone.github.io/docs/latest/_static/compose.yaml
```

--

## Télécharger et démarrer les conteneurs Greenbone

1. Télécharger les images :

```bash
sudo docker compose -f "$DOWNLOAD_DIR/compose.yaml" pull
```

2. Lancer les conteneurs en arrière-plan :

```bash
sudo docker compose -f "$DOWNLOAD_DIR/compose.yaml" up -d
```

3. Suivre les logs (flux continu) :

```bash
sudo docker compose -f "$DOWNLOAD_DIR/compose.yaml" logs -f
# Arrêter le flux : Ctrl-C
```

--

## Création / Mise à jour de l'utilisateur administrateur

Par défaut un utilisateur `admin` est créé avec un mot de passe généré. Changez immédiatement ce mot de passe :

```bash
docker compose -f "$DOWNLOAD_DIR/compose.yaml" \
    exec -u gvmd gvmd gvmd --user=admin --new-password='VotreNouveauMotDePasse'
```

Note : si votre mot de passe contient des caractères spéciaux, mettez-le entre guillemets simples.

--

## Accéder à l'interface web

Après démarrage et synchronisation des flux, ouvrez :

```
https://127.0.0.1
```

La synchronisation des flux peut prendre plusieurs minutes à plusieurs heures — les scans ne seront pas immédiatement disponibles.

--

## Script de configuration et de démarrage (option rapide)

Greenbone fournit un script `setup-and-start-greenbone-community-edition.sh`. Exemples de commandes :

```bash
curl -f -O https://greenbone.github.io/docs/latest/_static/setup-and-start-greenbone-community-edition.sh \
  && chmod u+x setup-and-start-greenbone-community-edition.sh
./setup-and-start-greenbone-community-edition.sh
```

Le script officiel télécharge le `compose.yaml`, télécharge et démarre les conteneurs, puis propose de définir le mot de passe `admin`.

--

## Astuce système — désactiver la mise en veille (Debian)

Sur des systèmes où les scans doivent tourner longtemps, désactivez les cibles de veille :

```bash
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

--

## Liens utiles

- Documentation officielle Greenbone (containeurs) : https://greenbone.github.io/docs/latest/
- Fichier compose officiel : https://greenbone.github.io/docs/latest/_static/compose.yaml
- Script officiel : https://greenbone.github.io/docs/latest/_static/setup-and-start-greenbone-community-edition.sh

--

## Suite proposée

Si vous souhaitez, je peux :
- valider/corriger le `compose.yaml` officiel et l'insérer ici;
- créer un script d'installation personnalisé basé sur ce document;
- ou committer ce fichier dans le dépôt.

---

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>

