<div align="center">

  ![OpenVAS](./images/OpenVAS.png)

  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=D14A4A&center=true&vCenter=true&width=650&lines=AUDIT+DE+SÉCURITÉ+AUTOMATISÉ;Identifier+•+Analyser+•+Sécuriser;OpenVAS+•+Pentesting+•+Rapports" alt="Typing SVG" />
  </a>
  
  <p align="center">
    <em>Mise à jour des conteneurs Greenbone.</em><br>
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

# 🛠️ Mise à jour des conteneurs communautaires Greenbone (GCE)

## 🔄 Mise à jour et lancement des conteneurs

```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml pull
docker compose -f $DOWNLOAD_DIR/docker-compose.yml up -d
```

---

## 📥 Synchronisation du **Greenbone Community Feed**

L’analyse de vulnérabilités nécessite des données spécifiques : tests de vulnérabilité (VTs), informations CVE, listes de ports, configurations d’analyse, etc.  
Ces données sont fournies via le **Greenbone Community Feed**.

### 🧠 Deux étapes de synchronisation :

1. **Téléchargement des nouvelles données** (via mise à jour des images de conteneurs).
2. **Chargement en mémoire et en base** (réalisé automatiquement par les démons).

⏳ Ces étapes peuvent prendre **de quelques minutes à plusieurs heures**, notamment lors de la première synchronisation.

---

## 🐳 Téléchargement des images de données

```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml pull \
  notus-data vulnerability-tests scap-data \
  dfn-cert-data cert-bund-data report-formats data-objects
```

## 🚀 Démarrage des conteneurs de données

```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml up -d \
  notus-data vulnerability-tests scap-data \
  dfn-cert-data cert-bund-data report-formats data-objects
```

---

## 🧩 Chargement des données par les démons

Une fois les conteneurs démarrés, les démons chargent automatiquement les données dans leurs bases respectives.  
Surveillez les **logs** pour vérifier la progression.

---

### ✅ **Tests de vulnérabilité (VTs)**

📌 Si le chargement est en cours (`ospd-openvas.log`) :

```bash
Loading VTs. Scans will be [requested|queued] until VTs are loaded. This may
take a few minutes, please wait...
```

📌 Une fois terminé :

```bash
Finished loading VTs. The VT cache has been updated from version X to Y.
```

📌 gvmd synchronise ensuite avec :

```bash
OSP service has different VT status (version X) from database (version Y, Z VTs). Starting update
```

📌 Puis :

```bash
Updating VTs in database ... done (X VTs).
```

---

### 🛡️ **Données SCAP** (CPE & CVE)

📌 Début du chargement (`gvmd.log`) :

```bash
update_scap: Updating data from feed
```

📌 Fin du chargement :

```bash
update_scap_end: Updating SCAP info succeeded
```

---

### 📋 **Données CERT** (DFN-CERT, CERT-Bund)

📌 Début du chargement :

```bash
sync_cert: Updating data from feed
```

📌 Fin du chargement :

```bash
sync_cert: Updating CERT info succeeded.
```

---

### 🧱 **Données GVMD** (Listes, formats, configurations)

📌 Listes de ports :

```bash
Port list All IANA assigned TCP (33d0cd82-57c6-11e1-8ed1-406186ea4fc5) has been created by admin
```

📌 Formats de rapports :

```bash
Report format XML (a994b278-1f62-11e1-96ac-406186ea4fc5) has been created by admin
```

📌 Configurations d’analyse :

> ⚠️ Nécessite que les VTs soient déjà chargés et l’option *Importer le propriétaire* activée.

```bash
Scan config Full and fast (daba56c8-73ec-11df-a475-002264764cea) has been created by admin
```

---

## 🧪 Vérification des services

Pensez à utiliser la commande suivante pour consulter les logs d’un service :

```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml logs -f <nom_du_service>
```

---

## 📚 Ressources utiles

- [Greenbone Docs](https://greenbone.github.io/)
- [Dépôt officiel Greenbone Docker](https://github.com/greenbone/community-edition)

---

🎯 _Document rédigé pour la mise en œuvre et la maintenance du Greenbone Community Edition via Docker Compose._

---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
