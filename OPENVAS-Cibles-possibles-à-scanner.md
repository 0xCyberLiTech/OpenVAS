<div align="center">

  <br></br>
  
  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3EOPENVAS_" alt="Titre dynamique OPENVAS" />
  </a>
  
  <br></br>
  
  <p align="center">
    <em>Cibles possibles à scanner avec OpenVAS.</em><br>
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

### 👨‍💻 **À propos de moi.**

> Bienvenue dans mon **laboratoire numérique personnel** dédié à l’apprentissage et à la vulgarisation de la cybersécurité.  
> Passionné par **Linux**, la **cryptographie** et les **systèmes sécurisés**, je partage ici mes notes, expérimentations et fiches pratiques.  
>  
> Pproposer un contenu clair, structuré et accessible pour étudiants, curieux et professionnels de l’IT.  

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

# 🎯 Cibles Possibles à Scanner avec OpenVAS :

## Objectif du document  
Fournir un aperçu clair et professionnel des types de cibles que l'on peut évaluer avec **OpenVAS** (via **Greenbone Community Edition**), en illustrant avec des exemples concrets dans des contextes réalistes (entreprise, lab, audit).

---

## 🧭 Introduction :

**OpenVAS** est un scanner de vulnérabilités open source puissant, conçu pour analyser des systèmes et détecter des failles de sécurité. Il est couramment utilisé par les professionnels de la cybersécurité dans le cadre d’audits, de tests de conformité, ou d’évaluations internes.

Pour maximiser la pertinence d'un scan, il est essentiel de bien identifier les **cibles**.

---

## 🛡️ Types de cibles que l’on peut scanner avec OpenVAS :

### 1. Serveurs (Windows / Linux)
- **But** : Détection des vulnérabilités sur les services exposés, OS, ports ouverts.
- **Exemples** :
  - Serveur **Debian 12** hébergeant un site web (Apache/Nginx).
  - **Windows Server 2019** avec Active Directory.
- **Scénario pédagogique** :
  > Déployer une VM Debian avec un service SSH et HTTP. Utiliser OpenVAS pour détecter une version obsolète d’OpenSSH.

---

### 2. Équipements réseau (switch, routeurs, firewalls).
- **But** : Identifier les faiblesses liées à l’administration à distance (telnet, SNMP, HTTP).
- **Exemples** :
  - **Switch Cisco** accessible via Telnet.
  - **Pare-feu pfSense** avec interface Web.
- **Scénario pédagogique** :
  > Simuler un routeur mal configuré avec SNMP public. OpenVAS peut alerter sur l’accès non restreint.

---

### 3. Applications Web (via IP ou nom de domaine)
- **But** : Détection de vulnérabilités applicatives, mauvaises configurations, certificats expirés.
- **Exemples** :
  - CMS **WordPress** auto-hébergé.
  - Intranet d’entreprise développé en PHP.
- **Scénario pédagogique** :
  > Déployer un WordPress sur LAMP avec des plugins vulnérables. OpenVAS détectera les CVE connues.

---

### 4. Équipements IoT ou embarqués
- **But** : Évaluer la surface d’attaque des objets connectés.
- **Exemples** :
  - Caméra IP connectée.
  - NAS grand public (Synology, QNAP).
- **Scénario pédagogique** :
  > Simuler un NAS avec ports ouverts et firmware obsolète. OpenVAS indiquera les failles connues.

---

### 5. Postes clients (tests internes encadrés)
- **But** : Vérifier les failles au niveau des OS clients ou logiciels installés.
- **Exemples** :
  - Windows 10 avec Java non mis à jour.
  - Station Linux avec navigateur ou service exposé.
- ⚠️ **Attention** : Ces scans nécessitent un cadre légal strict (test interne contrôlé).

---

### 6. Infrastructure virtuelle ou cloud
- **But** : Scanner des VM internes ou hébergées chez un fournisseur.
- **Exemples** :
  - VM sur **Proxmox**, **VMware**, ou dans un cloud privé.
  - Instances **OVH / Scaleway / AWS**.
- **Scénario pédagogique** :
  > Scanner une instance cloud exposant un port SSH avec une mauvaise configuration (authentification par mot de passe).

---

### 7. Équipements industriels / SCADA (en environnement sécurisé)
- **But** : Identifier les vulnérabilités sur les systèmes OT (Operational Technology).
- **Exemples** :
  - Automate programmable Siemens.
  - Interface web d’un système de contrôle industriel.
- ⚠️ **Important** : Ces scans doivent être réalisés avec **grande précaution** pour éviter tout impact sur la production.

---

## ✅ Bonnes pratiques lors de la définition des cibles

- Toujours avoir une **autorisation écrite** pour scanner une cible.
- Isoler les tests dans un **environnement de lab** avant toute intervention en production.
- Commencer par des scans **non intrusifs**, puis progresser vers des scans plus complets.
- Éviter de scanner des cibles sensibles sans plan de mitigation ou supervision.

---

## 📌 Conclusion

OpenVAS est capable de scanner une grande variété de systèmes, des serveurs aux équipements réseau, en passant par les applications web et les postes clients. Bien définir ses cibles permet d’obtenir des résultats pertinents et exploitables, tout en respectant les cadres légaux et techniques.

La richesse des scans dépend directement de la qualité des cibles sélectionnées et de leur configuration.

---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>

