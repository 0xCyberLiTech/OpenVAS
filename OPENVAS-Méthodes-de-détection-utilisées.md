<p align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="./images/OpenVAS.png" alt="Logo OpenVAS" width="500">
  </a>
</p>

<div align="center">

  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=D14A4A&center=true&vCenter=true&width=650&lines=AUDIT+DE+SÉCURITÉ+AUTOMATISÉ;Identifier+•+Analyser+•+Sécuriser;OpenVAS+•+Pentesting+•+Rapports" alt="Typing SVG" />
  </a>
  
  <p align="center">
    <em>Méthodes de détection utilisées par OpenVAS.</em><br>
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
> Pproposer un contenu clair, structuré et accessible pour étudiants, curieux et professionnels de l’IT.  
> 🔗 [Mon GitHub principal](https://github.com/0xCyberLiTech)

<p align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim" alt="Skills" alt="Logo techno" width="300">
  </a>
</p>

---

### 🎯 **Objectif de ce dépôt.**

> Ce dépôt a pour vocation de centraliser un ensemble de notions clés autour d'OpenVAS (Open Vulnerability Assessment System). Il s’adresse aux passionnés, étudiants et professionnels souhaitant mieux comprendre
> les principes de l'analyse de vulnérabilités, apprendre à installer, configurer et utiliser OpenVAS pour identifier les faiblesses de leurs systèmes, et se familiariser avec les concepts et outils essentiels
> pour renforcer la sécurité de leurs infrastructures informatiques.

---

# 🔍 Méthodes de Détection Utilisées par OpenVAS :

**OpenVAS** (aujourd’hui intégré à la suite Greenbone Community Edition) est un scanner de vulnérabilités réseau open-source. Son objectif principal est de **détecter les failles de sécurité** présentes sur des systèmes, applications et équipements réseau. Pour ce faire, OpenVAS utilise plusieurs **méthodes de détection complémentaires**, lui permettant de couvrir un large éventail de vecteurs d’attaque.

## 1. Scan par signatures (NVTs)
- OpenVAS repose sur un ensemble de **tests de vulnérabilités nommés NVTs (Network Vulnerability Tests)**.
- Ces NVTs sont des scripts écrits en langage NASL (Nessus Attack Scripting Language) qui contiennent des signatures spécifiques pour identifier des vulnérabilités connues (CVE).
- Le scanner compare les services détectés avec une base de données de failles connues.
- Mécanisme similaire à un antivirus, mais orienté réseau et systèmes.

## 2. Détection par bannière (Banner Grabbing)
- Méthode passive qui consiste à **collecter les bannières de services** (par exemple celles fournies par un serveur web ou SSH).
- Ces bannières révèlent souvent la version du logiciel ou du système, permettant de les croiser avec des bases de vulnérabilités.
- Utilisée pour l'identification non intrusive de logiciels vulnérables.

## 3. Analyse active de services
- OpenVAS interagit activement avec les services détectés (FTP, HTTP, SMTP, etc.) pour **tester leur comportement face à des requêtes spécifiques**.
- Permet de **vérifier la présence effective** d’une vulnérabilité, au-delà de la simple détection par version.
- Exemples : envoi de paquets malformés, test de débordement de mémoire tampon, injection SQL, etc.

## 4. Scan d’authentification
- Si des **identifiants valides** sont fournis (login SSH, Windows (SMB), SNMP, etc.), OpenVAS peut effectuer des analyses **authentifiées**.
- Cela permet une **détection plus précise et approfondie** des vulnérabilités logicielles, des mauvaises configurations ou des logiciels obsolètes.
- Méthode recommandée pour les audits internes.

## 5. Détection de configuration incorrecte
- OpenVAS vérifie aussi les **mauvaises pratiques de sécurité** : services exposés inutilement, certificats TLS faibles, ports ouverts non justifiés, etc.
- Ces vérifications relèvent de la **compliance** ou de l’**hygiène sécuritaire**.

## 6. Scan basé sur les vulnérabilités connues (base CVE/CPE)
- OpenVAS utilise les bases de données standards comme :
  - **CVE** (Common Vulnerabilities and Exposures)
  - **CPE** (Common Platform Enumeration) pour l’identification des logiciels
- Cela permet de faire le lien entre un logiciel détecté et les failles associées.

## 7. Analyse contextuelle et corrélation
- OpenVAS peut **corréler plusieurs résultats** pour affiner la détection.
- Exemple : croiser un logiciel vulnérable détecté avec une configuration non sécurisée pour renforcer la priorité du risque.

---

## 🎯 Conclusion

OpenVAS adopte une approche **hybride et modulaire** pour la détection des vulnérabilités, combinant **analyse passive et active**, **détection basée sur les signatures**, **vérification comportementale**, et **analyse contextuelle**. Ces méthodes en font un outil puissant pour réaliser des **audits de sécurité réseau** et **identifier les risques** présents dans une infrastructure informatique.

---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>

