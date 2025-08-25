<div align="center">

  <br></br>
  
  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3EOPENVAS_" alt="Titre dynamique OPENVAS" />
  </a>
  
  <br></br>
  
  <p align="center">
    <em>Mise à jour des conteneurs Greenbone.</em><br>
    <b>📊 Monitoring – 📈 Performance – ⚙️ Fiabilité</b>
  </p>

  [![🌐 Portfolio](https://img.shields.io/badge/Portfolio-0xCyberLiTech-181717?logo=github&style=flat-square)](https://0xcyberlitech.github.io/)
  [![🔗 Profil GitHub](https://img.shields.io/badge/Profil-GitHub-181717?logo=github&style=flat-square)](https://github.com/0xCyberLiTech)
  [![📦 Dernière version](https://img.shields.io/github/v/release/0xCyberLiTech/OpenVAS?label=version&style=flat-square&color=blue)](https://github.com/0xCyberLiTech/OpenVAS/releases/latest)
  [![📄 CHANGELOG](https://img.shields.io/badge/📄%20Changelog-OpenVAS-blue?style=flat-square)](https://github.com/0xCyberLiTech/OpenVAS/blob/main/CHANGELOG.md)
  [![📂 Dépôts publics](https://img.shields.io/badge/Dépôts-publics-blue?style=flat-square)](https://github.com/0xCyberLiTech?tab=repositories)
  [![👥 Contributeurs](https://img.shields.io/badge/👥%20Contributeurs-cliquez%20ici-007ec6?style=flat-square)](https://github.com/0xCyberLiTech/OpenVAS/graphs/contributors)

</div>

---

### 👨‍💻 **À propos de moi**

> Bienvenue sur le dépôt <strong>0xCyberLiTech</strong>, votre laboratoire numérique pour l'<strong>apprentissage</strong> et la <strong>vulgarisation</strong> de la <strong>cybersécurité</strong>, de l'<strong>administration Linux Debian</strong> et de la <strong>sécurité informatique</strong>.
> Passionné par <strong>Linux</strong>, la <strong>cryptographie</strong>, la <strong>supervision réseau</strong> et les <strong>systèmes sécurisés</strong>, je partage ici des <strong>tutoriels</strong>, <strong>guides pratiques</strong>, <strong>fiches techniques</strong> et <strong>retours d'expérience</strong> pour renforcer vos compétences IT.
>
> 🎯 <strong>Objectif :</strong> Offrir un contenu structuré, accessible et optimisé pour le référencement naturel, destiné aux étudiants, professionnels, administrateurs système, experts en sécurité et curieux du monde numérique.

<p align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="420">
  </a>
</p>

---

### 🎯 **Objectif de ce dépôt.**

> Ce dépôt a pour vocation de centraliser un ensemble de notions clés autour d'OpenVAS (Open Vulnerability Assessment System). Il s’adresse aux passionnés, étudiants et professionnels souhaitant mieux comprendre
> les principes de l'analyse de vulnérabilités, apprendre à installer, configurer et utiliser OpenVAS pour identifier les faiblesses de leurs systèmes, et se familiariser avec les concepts et outils essentiels
> pour renforcer la sécurité de leurs infrastructures informatiques.

---

# 🛠️ Mise à jour des conteneurs communautaires Greenbone (GCE)

## 🔧 Prérequis

- Docker ≥ 20.x
- Docker Compose (plugin) ≥ 2.x
- Accès à internet stable (la première synchronisation peut être longue)

## 📂 Installation initiale (si ce n'est pas déjà fait)

```bash
git clone https://github.com/greenbone/community-container.git $HOME/greenbone-community-container
```

```bash
cd $HOME/greenbone-community-container
```

---

## 🔄 Mise à jour et lancement des conteneurs

```bash
export DOWNLOAD_DIR=$HOME/greenbone-community-container
```

```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml pull
```

```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml up -d
```

---

## 📥 Synchronisation du **Greenbone Community Feed**

L’analyse de vulnérabilités nécessite des données spécifiques : tests de vulnérabilité (VTs), informations CVE, listes de ports, configurations d’analyse, etc.  
Ces données sont fournies via le **Greenbone Community Feed**.

### 🧠 Deux étapes de synchronisation :

1. **Téléchargement des nouvelles données** (mise à jour des images).
2. **Chargement en mémoire et en base** (réalisé automatiquement par les démons).

⏳ Ces étapes peuvent prendre **de quelques minutes à plusieurs heures**, surtout lors de la première synchronisation.

---

## 🐳 Téléchargement des images de données

```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml pull   notus-data vulnerability-tests scap-data   dfn-cert-data cert-bund-data report-formats data-objects
```

## 🚀 Démarrage des conteneurs de données

```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml up -d   notus-data vulnerability-tests scap-data   dfn-cert-data cert-bund-data report-formats data-objects
```

---

## 🧩 Chargement des données par les démons

Une fois les conteneurs démarrés, les démons chargent automatiquement les données dans leurs bases respectives.  
Surveillez les **logs** pour vérifier la progression.

---

### ✅ **Tests de vulnérabilité (VTs)**

📌 Chargement en cours (`ospd-openvas.log`) :

```text
Loading VTs. Scans will be [requested|queued] until VTs are loaded. This may
take a few minutes, please wait...
```

📌 Chargement terminé :

```text
Finished loading VTs. The VT cache has been updated from version X to Y.
```

📌 Synchronisation avec `gvmd` :

```text
OSP service has different VT status (version X) from database (version Y, Z VTs). Starting update
```

📌 Mise à jour terminée :

```text
Updating VTs in database ... done (X VTs).
```

---

### 🛡️ **Données SCAP** (CPE & CVE)

📌 Début (`gvmd.log`) :

```text
update_scap: Updating data from feed
```

📌 Fin :

```text
update_scap_end: Updating SCAP info succeeded
```

---

### 📋 **Données CERT** (DFN-CERT, CERT-Bund)

📌 Début :

```text
sync_cert: Updating data from feed
```

📌 Fin :

```text
sync_cert: Updating CERT info succeeded.
```

---

### 🧱 **Données GVMD** (Listes, formats, configurations)

📌 Listes de ports :

```text
Port list All IANA assigned TCP (33d0cd82-57c6-11e1-8ed1-406186ea4fc5) has been created by admin
```

📌 Formats de rapports :

```text
Report format XML (a994b278-1f62-11e1-96ac-406186ea4fc5) has been created by admin
```

📌 Configurations d’analyse :

> ⚠️ Nécessite que les VTs soient déjà chargés et l’option *Importer le propriétaire* activée.

```text
Scan config Full and fast (daba56c8-73ec-11df-a475-002264764cea) has been created by admin
```

---

## 🧪 Vérification des services

Pour consulter les logs d’un service :

```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml logs -f <nom_du_service>
```

---

## 🔁 Redémarrage complet des conteneurs (si besoin)

```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml down
```

```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml up -d
```

---

## 🧾 Services lancés par Docker Compose

- `gvmd` : Gestionnaire principal de vulnérabilités
- `ospd-openvas` : Moteur de scan
- `postgres` : Base de données
- `redis` : Cache
- Services de données :
  - `notus-data`
  - `vulnerability-tests`
  - `scap-data`
  - `dfn-cert-data`
  - `cert-bund-data`
  - `report-formats`
  - `data-objects`

---

## 📚 Ressources utiles

- [📘 Documentation Greenbone](https://greenbone.github.io/)
- [📦 Dépôt Docker Community Edition](https://github.com/greenbone/community-edition)

---

🎯 *Document rédigé pour la mise en œuvre et la maintenance de la Greenbone Community Edition via Docker Compose.*

---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
