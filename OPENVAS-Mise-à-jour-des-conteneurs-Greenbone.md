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

### 💡 **Mise à jour des conteneurs Greenbone.**

## 🔄 Mise à jour des conteneurs Greenbone

> Mettre à jour régulièrement les conteneurs **Greenbone / OpenVAS** permet d’obtenir les dernières signatures de vulnérabilités, correctifs de sécurité et améliorations du scanner.  
> Cela garantit la **fiabilité** et la **pertinence des résultats d’audit**.

---

## 🧰 Étapes de mise à jour

### 1. 🔍 Vérifier l'état actuel des conteneurs

docker ps

---

### 2. ⬇️ Récupérer les dernières images Docker officielles

docker compose pull

---

### 3. ♻️ Redémarrer les services avec les nouvelles images

docker compose down  
docker compose up -d

> ✅ Cela supprime les anciens conteneurs et relance les nouveaux avec les dernières versions disponibles.

---

### 4. 🔄 Mettre à jour les feeds Greenbone (bases de données)

#### a) 📱 Via l’interface Web (GSA) :

Connectez-vous à l’interface web de Greenbone, puis allez dans :  
`Administration → Feed Status → Update Feeds`

#### b) 🖥️ Via le terminal dans le conteneur :

docker exec -it gvm bash  
greenbone-feed-sync --type GVMD_DATA  
greenbone-feed-sync --type SCAP  
greenbone-feed-sync --type CERT

> 🕒 Cette opération peut prendre quelques minutes selon la taille des mises à jour.

---

## 📌 Remarques

- Le nom `gvm` correspond au nom du conteneur principal.  
  Adaptez-le si vous utilisez une autre configuration.
- Un redémarrage du conteneur peut être utile après la mise à jour :

docker restart gvm

---

## ✅ Vérification post-mise à jour

- Depuis l’interface web, allez dans `Feed Status` pour vérifier que tous les feeds sont **à jour**.
- Vous pouvez aussi consulter les logs du conteneur :

docker logs -f gvm

---

🔒 *Maintenir les feeds à jour est une bonne pratique essentielle pour des audits pertinents et fiables.*

---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
