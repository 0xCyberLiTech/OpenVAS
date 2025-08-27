<div align="center">

  <br></br>
  
  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3EOPENVAS_" alt="Titre dynamique OPENVAS" />
  </a>
  
  <br></br>
  
  <h2>Laboratoire numérique pour la cybersécurité, Linux & IT</h2>

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

<!--
Optimisation SEO : mots-clés cybersécurité, Linux, administration système, sécurité informatique, tutoriels, guides, expertise, formation, supervision, Docker, OpenVAS, firewall, proxy, DNS, SSH, Debian, IT, réseau, cryptographie, open source, ressources techniques, étudiants, professionnels, passionnés.
-->

<div align="center">
  <img src="https://img.icons8.com/fluency/96/000000/cyber-security.png" alt="CyberSec" width="80"/>
</div>

<div align="center">
  <p>
    <strong>Cybersécurité</strong> <img src="https://img.icons8.com/color/24/000000/lock--v1.png"/> • <strong>Linux Debian</strong> <img src="https://img.icons8.com/color/24/000000/linux.png"/> • <strong>Sécurité informatique</strong> <img src="https://img.icons8.com/color/24/000000/shield-security.png"/>
  </p>
</div>

---

## 🚀 À propos & Objectifs

Ce projet propose des solutions innovantes et accessibles en cybersécurité, avec une approche centrée sur la simplicité d’utilisation et l’efficacité. Il vise à accompagner les utilisateurs dans la protection de leurs données et systèmes, tout en favorisant l’apprentissage et le partage des connaissances.

Le contenu est structuré, accessible et optimisé SEO pour répondre aux besoins de :
- 🎓 Étudiants : approfondir les connaissances
- 👨‍💻 Professionnels IT : outils et pratiques
- 🖥️ Administrateurs système : sécuriser l’infrastructure
- 🛡️ Experts cybersécurité : ressources techniques
- 🚀 Passionnés du numérique : explorer les bonnes pratiques

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

---

🎯 *Document rédigé pour la mise en œuvre et la maintenance de la Greenbone Community Edition via Docker Compose.*

---

<p align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="420">
  </a>
</p>

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
