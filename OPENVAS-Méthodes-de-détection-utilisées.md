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

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>

