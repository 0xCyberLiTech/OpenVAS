<div align="center">

  <br></br>
  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3EOPENVAS_" alt="Titre dynamique OPENVAS" />
  </a>
  <br></br>
  
  <p align="center">
    <em>Méthodes de détection utilisées par OpenVAS.</em><br>
    <b>📊 Monitoring – 📈 Performance – ⚙️ Fiabilité</b>
  </p>

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

---

### 👨‍💻 **À propos de moi**

> Bienvenue sur le dépôt <strong>0xCyberLiTech</strong>, votre laboratoire numérique pour l'<strong>apprentissage</strong> et la <strong>vulgarisation</strong> de la <strong>cybersécurité</strong>, de l'<strong>administration Linux Debian</strong> et de la <strong>sécurité informatique</strong>.
> Passionné par <strong>Linux</strong>, la <strong>cryptographie</strong>, la <strong>supervision réseau</strong> et les <strong>systèmes sécurisés</strong>, je partage ici des <strong>tutoriels</strong>, <strong>guides pratiques</strong>, <strong>fiches techniques</strong> et <strong>retours d'expérience</strong> pour renforcer vos compétences IT.
>
> 🎯 <strong>Objectif :</strong> Offrir un contenu structuré, accessible et optimisé pour le référencement naturel, destiné aux étudiants, professionnels, administrateurs système, experts en sécurité et curieux du monde numérique.

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
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="420">
  </a>
</p>

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>

