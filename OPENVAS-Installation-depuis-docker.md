<!-- MASTER-HEADER-START -->
<div align="center">

<a href="https://0xcyberlitech.com/">
  <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/headers/header-openvas.svg" alt="ATELIER OPENVAS // AUDIT VULNÉRABILITÉS" width="100%" />
</a>

<p align="center">
  <a href="https://0xcyberlitech.com/"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-portal.svg" alt="Portail 0xCyberLiTech.com" width="24%" /></a>
  <a href="https://0xcyberlitech.com/soc-rd.html"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-soc-rd.svg" alt="Livre Blanc SOC Cockpit" width="24%" /></a>
  <a href="https://0xcyberlitech.com/jarvis-rd.html"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-jarvis-rd.svg" alt="Livre Blanc JARVIS IA" width="24%" /></a>
  <a href="https://github.com/0xCyberLiTech?tab=repositories"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-github.svg" alt="Catalogue des 23 Dépôts" width="24%" /></a>
</p>
<p align="center">
  <a href="README.md"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-back-readme.svg" alt="Retour au sommaire du dépôt" width="340" /></a>
</p>

<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/divider-hud.svg" alt="" width="100%" />
</div>
<!-- MASTER-HEADER-END -->

<!-- DEBIAN-TRUTH-START -->
> [!IMPORTANT]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-shield.svg" width="18" height="18" align="absmiddle" alt="" /> ** Matrice Officielle Debian — `Debian 12 (Bookworm)` · `Debian 13 (Trixie)` · `Debian 14 (Forky)`**
> - **Sources Officielles Debian.org (`gvmd`) :** `Bookworm (12)` : **`Stable-12`** &nbsp;·&nbsp; `Trixie (13 — Stable)` : **`Stable-13`** &nbsp;·&nbsp; `Forky (14 — Next-Gen)` : **`26.24.0-2`**
> - **Références Officielles :** [Paquet Debian Trixie (`gvm`)](https://packages.debian.org/trixie/gvm) &nbsp;·&nbsp; [Paquet Debian Forky (`gvm`)](https://packages.debian.org/forky/gvm) &nbsp;·&nbsp; [Documentation Officielle Debian](https://packages.debian.org/trixie/gvm)
> - **Note d'Ingénierie (Divergence 13 vs 14) :** Sous Debian 13 (Trixie) et Debian 14 (Forky), le déploiement conteneurisé s'opère exclusivement via **`docker compose` v2** (ou via le métapaquet natif `gvm` maintenu par l'équipe Debian Security Tools).

<details>
<summary><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> <b>Afficher les Encarts Ligne de Commande : Debian 13 (Trixie — Stable) vs Debian 14 (Forky — Next-Gen)</b></summary>

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Profil Production Stable — Commandes pour `Debian 13 (Trixie)`
```bash
# Debian 13 (Trixie) — Deploiement Greenbone OpenVAS via Docker Compose v2 :
docker compose up -d && docker compose ps
docker compose logs -f gvmd
```

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-rd.svg" width="46" height="16" align="absmiddle" alt="[R&D]" /> Profil Anticipation Next-Gen — Commandes pour `Debian 14 (Forky)`
```bash
# Debian 14 (Forky) — Paquet natif 'gvm' disponible dans les depots Debian Testing/Forky :
apt-cache policy gvm
docker compose pull && docker compose up -d
```

</details>
<!-- DEBIAN-TRUTH-END -->

<!-- CIEL-PEDAGOGY-START -->
<details>
<summary><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> <b>Synthèse d'Architecture, Standards Officiels &amp; Diagnostic (Niveau 1 : Fondamentaux · Niveau 2 : Repères · Niveau 3 : Diagnostic)</b></summary>

- **Niveau 1 — Fondamentaux &amp; Principe d'Architecture :** **Greenbone OpenVAS (GVM)** est une suite d'audit et de détection de vulnérabilités qui évalue la surface d'exposition des systèmes en confrontant leurs services réseau aux flux quotidiens de tests de sécurité (**NVT**, **CVE**, **OVAL**) cotés selon le standard **CVSS v3/v4**.
- **Niveau 2 — Repères Officiels (Ports IANA, Fichiers Debian &amp; Commandes de Validation) :** **Ports :** `TCP 9392` (Interface Web GSA) · `TCP 5432` (PostgreSQL interne) · Socket Redis `/run/redis-openvas/redis.sock` &nbsp;|&nbsp; **Validation officielle :** `sudo gvm-check-setup`.
- **Niveau 3 — Diagnostic d'Incidents &amp; Ingénierie Avancée :** **Diagnostic & Architecture :** Si un audit demeure bloqué à `0%`, vérifiez que la synchronisation initiale des flux de signatures (`sudo greenbone-feed-sync`) est intégralement terminée et que l'instance Redis dédiée à OpenVAS est active. Contrairement à un IDS/IPS qui analyse les attaques en cours, OpenVAS identifie préventivement les vulnérabilités logicielles et défauts de configuration.
- **Sources de Vérité Officielles Éditeurs &amp; Standards :** [Documentation Officielle Greenbone Community Edition](https://greenbone.github.io/docs/latest/) &nbsp;·&nbsp; [Base Nationale des Vulnérabilités NIST NVD](https://nvd.nist.gov/)
- **Livres Blancs &amp; 67 Podcasts Audio R&amp;D :** [Portail 0xCyberLiTech](https://0xcyberlitech.com/) &nbsp;·&nbsp; [Livre Blanc SOC Cockpit v5.5](https://0xcyberlitech.com/soc-rd.html) &nbsp;·&nbsp; [Livre Blanc JARVIS Mark-VII](https://0xcyberlitech.com/jarvis-rd.html) &nbsp;·&nbsp; [Blueprint Logiciel &amp; Matériel RTX 5080](https://0xcyberlitech.com/blueprint-jarvis.html)

</details>
<!-- CIEL-PEDAGOGY-END -->


# <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-shield.svg" width="20" height="20" align="absmiddle" alt="" /> Installation et déploiement de Greenbone Community Edition (Docker)

Ce document présente, de manière professionnelle et organisée, les étapes nécessaires pour installer Docker et déployer Greenbone Community Edition à l'aide des conteneurs fournis.

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 01 // Dépendances d'installation
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Rappel sur la commande sudo, si celle-ci n'est pas installée et configurée :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> su - root
> apt install sudo
> usermod -aG sudo username
> init 6
> ```
<!-- CODE-WINDOW-END -->

Avant de commencer, installez les dépendances requises (ex. : `curl`, `ca-certificates`, `gnupg`) :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> sudo apt update
> sudo apt install ca-certificates curl gnupg
> ```
<!-- CODE-WINDOW-END -->

Ces outils sont nécessaires pour télécharger des fichiers et ajouter des dépôts sécurisés.

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 02 // Installation de Docker
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Docker est requis pour exécuter les services dans des conteneurs. Les étapes suivantes proviennent du guide officiel d'installation du moteur Docker.

1. Désinstallez les paquets Debian conflictuels :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> for pkg in docker.io docker-doc docker compose podman-docker containerd runc; do sudo apt remove $pkg; done
> ```
<!-- CODE-WINDOW-END -->

2. Configurez le dépôt Docker :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> sudo install -m 0755 -d /etc/apt/keyrings
> curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
> sudo chmod a+r /etc/apt/keyrings/docker.gpg
> echo \
>   "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
>   "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
>   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
> sudo apt update
> ```
<!-- CODE-WINDOW-END -->

3. Installez Docker et les paquets associés :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin
> ```
<!-- CODE-WINDOW-END -->

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 03 // Mise en place - Permettre l'utilisation de Docker sans sudo
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Ajoutez l'utilisateur courant au groupe `docker` pour pouvoir exécuter Docker sans `sudo` :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> sudo usermod -aG docker $USER && su $USER
> ```
<!-- CODE-WINDOW-END -->

Vous pouvez aussi vous déconnecter/reconnecter pour que la modification de groupe soit prise en compte.

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 04 // Préparer un répertoire de téléchargement
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Créez un répertoire de travail pour télécharger le fichier `compose.yaml` et autres artefacts :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> export DOWNLOAD_DIR=$HOME/greenbone-community-container && mkdir -p $DOWNLOAD_DIR
> ```
<!-- CODE-WINDOW-END -->

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 05 // Fichier Docker Compose
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Important : utilisez toujours la dernière version du fichier `compose.yaml` fournie par Greenbone. Le fichier ci-dessous est fourni à titre d'exemple — il peut évoluer.

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```yaml
> # Fichier d'exemple (extrait)
> name: greenbone-community-edition
>
> services:
>   vulnerability-tests:
>     image: registry.community.greenbone.net/community/vulnerability-tests
>     environment:
>       FEED_RELEASE: "24.10"
>       KEEP_ALIVE: 1
>     volumes:
>       - vt_data_vol:/mnt
>
>   notus-data:
>     image: registry.community.greenbone.net/community/notus-data
>     environment:
>       KEEP_ALIVE: 1
>     volumes:
>       - notus_data_vol:/mnt
>
>   scap-data:
>     image: registry.community.greenbone.net/community/scap-data
>     environment:
>       KEEP_ALIVE: 1
>     volumes:
>       - scap_data_vol:/mnt
>
>   cert-bund-data:
>     image: registry.community.greenbone.net/community/cert-bund-data
>     environment:
>       KEEP_ALIVE: 1
>     volumes:
>       - cert_data_vol:/mnt
>
>   dfn-cert-data:
>     image: registry.community.greenbone.net/community/dfn-cert-data
>     environment:
>       KEEP_ALIVE: 1
>     volumes:
>       - cert_data_vol:/mnt
>     depends_on:
>       cert-bund-data:
>         condition: service_healthy
>
>   data-objects:
>     image: registry.community.greenbone.net/community/data-objects
>     environment:
>       FEED_RELEASE: "24.10"
>       KEEP_ALIVE: 1
>     volumes:
>       - data_objects_vol:/mnt
>
>   report-formats:
>     image: registry.community.greenbone.net/community/report-formats
>     environment:
>       FEED_RELEASE: "24.10"
>       KEEP_ALIVE: 1
>     volumes:
>       - data_objects_vol:/mnt
>     depends_on:
>       data-objects:
>         condition: service_healthy
>
>   gpg-data:
>     image: registry.community.greenbone.net/community/gpg-data
>     volumes:
>       - gpg_data_vol:/mnt
>
>   redis-server:
>     image: registry.community.greenbone.net/community/redis-server
>     restart: on-failure
>     volumes:
>       - redis_socket_vol:/run/redis/
>
>   pg-gvm:
>     image: registry.community.greenbone.net/community/pg-gvm:stable
>     restart: on-failure:10
>     volumes:
>       - psql_data_vol:/var/lib/postgresql
>       - psql_socket_vol:/var/run/postgresql
>     depends_on:
>       pg-gvm-migrator:
>         condition: service_completed_successfully
>
>   pg-gvm-migrator:
>     image: registry.community.greenbone.net/community/pg-gvm-migrator:stable
>     restart: no
>     volumes:
>       - psql_data_vol:/var/lib/postgresql
>       - psql_socket_vol:/var/run/postgresql
>
>   gvmd:
>     image: registry.community.greenbone.net/community/gvmd:stable
>     restart: on-failure
>     volumes:
>       - gvmd_data_vol:/var/lib/gvm
>       - scap_data_vol:/var/lib/gvm/scap-data/
>       - cert_data_vol:/var/lib/gvm/cert-data
>       - data_objects_vol:/var/lib/gvm/data-objects/gvmd
>       - vt_data_vol:/var/lib/openvas/plugins
>       - psql_data_vol:/var/lib/postgresql
>       - gvmd_socket_vol:/run/gvmd
>       - ospd_openvas_socket_vol:/run/ospd
>       - psql_socket_vol:/var/run/postgresql
>     depends_on:
>       pg-gvm:
>         condition: service_started
>       scap-data:
>         condition: service_healthy
>       cert-bund-data:
>         condition: service_healthy
>       dfn-cert-data:
>         condition: service_healthy
>       data-objects:
>         condition: service_healthy
>       report-formats:
>         condition: service_healthy
>
>   gsa:
>     image: registry.community.greenbone.net/community/gsa:stable-slim
>     environment:
>       MOUNT_PATH: "/mnt/web"
>       KEEP_ALIVE: 1
>     healthcheck:
>       test: ["CMD-SHELL", "test -e /run/gsa/copying.done"]
>       start_period: 5s
>     volumes:
>       - gsa_data_vol:/mnt/web
>
>   gsad:
>     image: registry.community.greenbone.net/community/gsad:stable
>     restart: on-failure
>     environment:
>       GSAD_ARGS: "--listen=0.0.0.0 --http-only --api-only -f"
>     volumes:
>       - gvmd_socket_vol:/run/gvmd
>     depends_on:
>       gvmd:
>         condition: service_started
>
>   gvm-config:
>     image: registry.community.greenbone.net/community/gvm-config:latest
>     environment:
>       ENABLE_NGINX_CONFIG: true
>       ENABLE_TLS_GENERATION: true
>     volumes:
>       - nginx_config_vol:/mnt/nginx/configs
>       - nginx_certificates_vol:/mnt/nginx/certs
>
>   nginx:
>     image: registry.community.greenbone.net/community/nginx:latest
>     ports:
>       - 127.0.0.1:443:443
>       - 127.0.0.1:9392:9392
>     volumes:
>       - nginx_config_vol:/etc/nginx/conf.d:ro
>       - nginx_certificates_vol:/etc/nginx/certs:ro
>       - gsa_data_vol:/usr/share/nginx/html:ro
>     depends_on:
>       gvm-config:
>         condition: service_completed_successfully
>       gsa:
>         condition: service_healthy
>       gsad:
>         condition: service_started
>
>   configure-openvas:
>     image: registry.community.greenbone.net/community/openvas-scanner:stable
>     volumes:
>       - openvas_data_vol:/mnt
>       - openvas_log_data_vol:/var/log/openvas
>     command:
>       - /bin/sh
>       - -c
>       - |
>         printf "table_driven_lsc = yes\nopenvasd_server = http://openvasd:80\n" > /mnt/openvas.conf
>         sed "s/127/128/" /etc/openvas/openvas_log.conf | sed 's/gvm/openvas/' > /mnt/openvas_log.conf
>         chmod 644 /mnt/openvas.conf
>         chmod 644 /mnt/openvas_log.conf
>         touch /var/log/openvas/openvas.log
>         chmod 666 /var/log/openvas/openvas.log
>
>   openvas:
>     image: registry.community.greenbone.net/community/openvas-scanner:stable
>     restart: on-failure
>     volumes:
>       - openvas_data_vol:/etc/openvas
>       - openvas_log_data_vol:/var/log/openvas
>     command:
>       - /bin/sh
>       - -c
>       - |
>         cat /etc/openvas/openvas.conf
>         tail -f /var/log/openvas/openvas.log
>     depends_on:
>       configure-openvas:
>         condition: service_completed_successfully
>
>   openvasd:
>     image: registry.community.greenbone.net/community/openvas-scanner:stable
>     restart: on-failure
>     environment:
>       OPENVASD_MODE: service_notus
>       GNUPGHOME: /etc/openvas/gnupg
>       LISTENING: 0.0.0.0:80
>     volumes:
>       - openvas_data_vol:/etc/openvas
>       - openvas_log_data_vol:/var/log/openvas
>       - gpg_data_vol:/etc/openvas/gnupg
>       - notus_data_vol:/var/lib/notus
>     depends_on:
>       vulnerability-tests:
>         condition: service_healthy
>       notus-data:
>         condition: service_healthy
>       configure-openvas:
>         condition: service_completed_successfully
>       gpg-data:
>         condition: service_completed_successfully
>     networks:
>       default:
>         aliases:
>           - openvasd
>
>   ospd-openvas:
>     image: registry.community.greenbone.net/community/ospd-openvas:stable
>     restart: on-failure
>     hostname: ospd-openvas.local
>     cap_add:
>       - NET_ADMIN
>       - NET_RAW
>     security_opt:
>       - seccomp=unconfined
>       - apparmor=unconfined
>     command:
>       [
>         "ospd-openvas",
>         "-f",
>         "--config",
>         "/etc/gvm/ospd-openvas.conf",
>         "--notus-feed-dir",
>         "/var/lib/notus/advisories",
>         "-m",
>         "666",
>       ]
>     volumes:
>       - gpg_data_vol:/etc/openvas/gnupg
>       - vt_data_vol:/var/lib/openvas/plugins
>       - notus_data_vol:/var/lib/notus
>       - ospd_openvas_socket_vol:/run/ospd
>       - redis_socket_vol:/run/redis/
>       - openvas_data_vol:/etc/openvas/
>       - openvas_log_data_vol:/var/log/openvas
>     depends_on:
>       redis-server:
>         condition: service_started
>       gpg-data:
>         condition: service_completed_successfully
>       configure-openvas:
>         condition: service_completed_successfully
>       vulnerability-tests:
>         condition: service_healthy
>       notus-data:
>         condition: service_healthy
>
>   gvm-tools:
>     image: registry.community.greenbone.net/community/gvm-tools
>     volumes:
>       - gvmd_socket_vol:/run/gvmd
>       - ospd_openvas_socket_vol:/run/ospd
>     depends_on:
>       - gvmd
>       - ospd-openvas
>
> volumes:
>   gpg_data_vol: {}
>   scap_data_vol: {}
>   cert_data_vol: {}
>   data_objects_vol: {}
>   gvmd_data_vol: {}
>   psql_data_vol: {}
>   vt_data_vol: {}
>   notus_data_vol: {}
>   psql_socket_vol: {}
>   gvmd_socket_vol: {}
>   ospd_openvas_socket_vol: {}
>   redis_socket_vol: {}
>   openvas_data_vol: {}
>   openvas_log_data_vol: {}
>   gsa_data_vol: {}
>   nginx_config_vol: {}
>   nginx_certificates_vol: {}
> ```
<!-- CODE-WINDOW-END -->

> Remarque : pour la version officielle et à jour, consultez : https://greenbone.github.io/docs/latest/

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 06 // Télécharger le fichier `compose.yaml`
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Vous pouvez télécharger directement le fichier officiel :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> curl -f -O -L https://greenbone.github.io/docs/latest/_static/compose.yaml --output-dir "$DOWNLOAD_DIR"
> ```
<!-- CODE-WINDOW-END -->

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 07 // Télécharger et démarrer les conteneurs Greenbone
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

1. Télécharger les images :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> docker compose -f $DOWNLOAD_DIR/compose.yaml pull
> ```
<!-- CODE-WINDOW-END -->

2. Lancer les conteneurs en arrière-plan :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> docker compose -f $DOWNLOAD_DIR/compose.yaml up -d
> ```
<!-- CODE-WINDOW-END -->

3. Suivre les logs (flux continu) :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> docker compose -f $DOWNLOAD_DIR/compose.yaml logs -f
> # Arrêter le flux : Ctrl-C
> ```
<!-- CODE-WINDOW-END -->

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 08 // Création / Mise à jour de l'utilisateur administrateur
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Par défaut un utilisateur `admin` est créé avec un mot de passe généré. Changez immédiatement ce mot de passe :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> docker compose -f $DOWNLOAD_DIR/compose.yaml \
>     exec -u gvmd gvmd gvmd --user=admin --new-password='<password>'
> ```
<!-- CODE-WINDOW-END -->

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> docker compose -f "$DOWNLOAD_DIR/compose.yaml" \
>     exec -u gvmd gvmd gvmd --user=admin --new-password='VotreNouveauMotDePasse'
> ```
<!-- CODE-WINDOW-END -->

Note : si votre mot de passe contient des caractères spéciaux, mettez-le entre guillemets simples.

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 09 // Accéder à l'interface web
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Après démarrage et synchronisation des flux, ouvrez :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> https://127.0.0.1
> ```
<!-- CODE-WINDOW-END -->

La synchronisation des flux peut prendre plusieurs minutes à plusieurs heures — les scans ne seront pas immédiatement disponibles.

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 10 // Script de configuration et de démarrage (option rapide)
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Greenbone fournit un script `setup-and-start-greenbone-community-edition.sh`. Exemples de commandes :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> curl -f -O https://greenbone.github.io/docs/latest/_static/setup-and-start-greenbone-community-edition.sh && chmod u+x setup-and-start-greenbone-community-edition.sh
> ```
<!-- CODE-WINDOW-END -->

Le script officiel télécharge le `compose.yaml`, télécharge et démarre les conteneurs, puis propose de définir le mot de passe `admin`.

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 11 // Astuce système - désactiver la mise en veille (Debian)
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Sur des systèmes où les scans doivent tourner longtemps, désactivez les cibles de veille :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
> ```
<!-- CODE-WINDOW-END -->

--

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 12 // Liens utiles
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- Documentation officielle Greenbone (containeurs) : https://greenbone.github.io/docs/latest/
- Fichier compose officiel : https://greenbone.github.io/docs/latest/_static/compose.yaml
- Script officiel : https://greenbone.github.io/docs/latest/_static/setup-and-start-greenbone-community-edition.sh

<!-- MASTER-FOOTER-START -->
<div align="center">
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/divider-hud.svg" alt="" width="100%" />

<a href="https://0xcyberlitech.com/">
  <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/footer-master.svg" alt="0xCyberLiTech — Architecture Cyberdéfense, Ingénierie Déterministe & IA Souveraine" width="100%" />
</a>

<p align="center"><a href="https://0xcyberlitech.com/"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/badge-antigravity.svg" alt="Architecturé par Marc & Antigravity (Google DeepMind)" width="520" /></a></p>

<sub><b>Architecturé &amp; Forgé par Marc &amp; Antigravity (Google DeepMind)</b> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/"><b>0xcyberlitech.com</b></a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/soc-rd.html">Architecture SOC Cockpit v5.5</a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/jarvis-rd.html">Architecture JARVIS Mark-VII</a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/blueprint-jarvis.html">Blueprint Matériel RTX 5080</a></sub>

</div>
<!-- MASTER-FOOTER-END -->
