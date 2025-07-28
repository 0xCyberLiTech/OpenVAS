<div align="center">

  ![OpenVAS](./images/OpenVAS.png)

  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=D14A4A&center=true&vCenter=true&width=650&lines=AUDIT+DE+SÉCURITÉ+AUTOMATISÉ;Identifier+•+Analyser+•+Sécuriser;OpenVAS+•+Pentesting+•+Rapports" alt="Typing SVG" />
  </a>
  
  <p align="center">
    <em>Tuto - Déploiement de Greenbone Community Edition (OpenVAS) via Docker sur Debian 12..</em><br>
    <b>📊 Monitoring – 📈 Performance – ⚙️ Fiabilité</b>
  </p>
  
  [![🔗 Profil GitHub](https://img.shields.io/badge/Profil-GitHub-181717?logo=github&style=flat-square)](https://github.com/0xCyberLiTech)
  [![📦 Dernière version](https://img.shields.io/github/v/release/0xCyberLiTech/OpenVAS?label=version&style=flat-square&color=blue)](https://github.com/0xCyberLiTech/OpenVAS/releases/latest)
  [![📄 CHANGELOG](https://img.shields.io/badge/📄%20Changelog-OpenVAS-blue?style=flat-square)](https://github.com/0xCyberLiTech/OpenVAS/blob/main/CHANGELOG.md)
  [![📂 Dépôts publics](https://img.shields.io/badge/Dépôts-publics-blue?style=flat-square)](https://github.com/0xCyberLiTech?tab=repositories)
  [![👥 Contributeurs](https://img.shields.io/badge/👥%20Contributeurs-cliquez%20ici-007ec6?style=flat-square)](https://github.com/0xCyberLiTech/OpenVAS/graphs/contributors)

</div>

---

### 👨‍💻 **À propos de moi.**

> Bienvenue dans mon **laboratoire numérique personnel** dédié à l’apprentissage et à la vulgarisation de la cybersécurité.  
> Passionné par **Linux**, la **cryptographie** et les **systèmes sécurisés**, je partage ici mes notes, expérimentations et fiches pratiques.  
>  
> 🎯 **Objectif :** proposer un contenu clair, structuré et accessible pour étudiants, curieux et professionnels de l’IT.  
> 🔗 [Mon GitHub principal](https://github.com/0xCyberLiTech)

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim" alt="Skills" />
  </a>
</p>

---

### 🎯 **Objectif de ce dépôt.**

> Ce dépôt a pour vocation de centraliser un ensemble de notions clés autour d'OpenVAS (Open Vulnerability Assessment System). Il s’adresse aux passionnés, étudiants et professionnels souhaitant mieux comprendre
> les principes de l'analyse de vulnérabilités, apprendre à installer, configurer et utiliser OpenVAS pour identifier les faiblesses de leurs systèmes, et se familiariser avec les concepts et outils essentiels
> pour renforcer la sécurité de leurs infrastructures informatiques.

---


## 🛡️ Déploiement de Greenbone Community Edition (OpenVAS) via Docker.

## 🧰 Prérequis

- Tuto validé sur **Debian 12**.
- Docker + Docker Compose doivent être installés.

| Catégorie | Sujet | Accès Rapide |
|:---:|:---|:---:|
| **Tutos & Outils** | Installation manuelle de Docker & Docker Compose | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](https://github.com/0xCyberLiTech/Docker/blob/main/DOCKER-et-DOCKER-COMPOSE-Installation-manuelle.md) |
| **Tutos & Outils** | Installation manuelle de Portainer | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](https://github.com/0xCyberLiTech/Docker/blob/main/PORTAINER-Installation-manuelle.md) |

- Exécuter la procédure sous **`su`** pour éviter les problèmes de permission.
- Ajouter l’utilisateur courant au groupe `docker` :

```bash
sudo usermod -aG docker $USER && su $USER
```

- Installer les dépendances nécessaires :

```bash
sudo apt install ca-certificates curl gnupg
```

---

## 🐳 Déploiement de Greenbone avec Docker

### 📁 Créer le répertoire de travail

```bash
export DOWNLOAD_DIR=$HOME/greenbone-community-container
mkdir -p $DOWNLOAD_DIR
cd $DOWNLOAD_DIR
```

> ⚠️ **Important**  
> Veillez à toujours utiliser la **dernière version** du fichier `docker-compose.yml`, disponible dans la documentation officielle :  
> https://greenbone.github.io/docs/latest/22.4/container/index.html

---

## 📦 Obtenir le fichier `docker-compose.yml`

### 1️⃣ Méthode manuelle

Créer le fichier :

```bash
nano docker-compose.yml
```

Coller le contenu du fichier officiel :
👉 Voir ici : [docker-compose.yml](https://greenbone.github.io/docs/latest/_static/docker-compose.yml)

---

### 2️⃣ Téléchargement automatique

Créer un répertoire et télécharger le fichier :

```bash
mkdir -p ~/Docker-containers && cd ~/Docker-containers
curl -f -O -L https://greenbone.github.io/docs/latest/_static/docker-compose.yml --output-dir "$DOWNLOAD_DIR"
```

---

## ▶️ Lancement des conteneurs

Télécharger les images Docker :

```bash
sudo docker compose -f $DOWNLOAD_DIR/docker-compose.yml -p greenbone-community-edition pull
```

Démarrer les conteneurs en arrière-plan :

```bash
sudo docker compose -f $DOWNLOAD_DIR/docker-compose.yml -p greenbone-community-edition up -d
```

---

## 📋 Logs et supervision

Afficher les logs des services :

```bash
sudo docker compose -f $DOWNLOAD_DIR/docker-compose.yml logs -f
```

Arrêtez l’affichage avec `Ctrl + C`.

---

## 🔐 Configuration de l’utilisateur admin

Par défaut, un utilisateur `admin` avec le mot de passe `admin` est créé.

> 🔐 **Il est fortement recommandé de le changer immédiatement.**

Changer le mot de passe :

```bash
sudo docker compose -f $DOWNLOAD_DIR/docker-compose.yml     exec -u gvmd gvmd gvmd --user=admin --new-password='MonMotDePasse'
```

> ⚠️ Si le mot de passe contient des caractères spéciaux, entourez-le de **guillemets simples** `'...'`

---

## 🌍 Accès à l’interface Web

Lancer l’interface Greenbone Security Assistant (GSA) dans votre navigateur :

```bash
xdg-open "http://127.0.0.1:9392" 2>/dev/null >/dev/null &
```

Utilisez les identifiants définis précédemment pour vous connecter.

---

## 📚 Références

- 📘 [Documentation officielle Greenbone](https://greenbone.github.io/docs/latest/container/container.html)
- 🐙 [Dépôt GitHub du projet](https://github.com/greenbone/greenbone-community-container)

---

## ✅ Auteur

- GitHub : [0xCyberLiTech](https://github.com/0xCyberLiTech)

---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
