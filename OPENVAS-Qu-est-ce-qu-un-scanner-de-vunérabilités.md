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

## Qu'est-ce qu'un scanner de vulnérabilités

Un **scanner de vulnérabilités** est un programme permettant de détecter des failles dans des systèmes, réseaux ou applications.

### 🎯 Utilisation.

| Légale ✅ | Illégale ❌ |
|----------|-------------|
| Audit interne, tests de sécurité, conformité | Recherche de failles pour exploitation non autorisée |

> Les scanners peuvent être utilisés dans un **SIEM**, un **SOC** ou intégrés dans des stratégies de **cybersécurité préventive**.

---

## 02 - Principes de fonctionnement.

Un scanner peut être :

- Une application installable
- Une appliance virtuelle
- Un service SaaS

### 🔁 Phases classiques d’un scan :

1. Découverte de la cible (ping, ARP, TCP…)
2. Scan de ports ouverts (TCP/UDP)
3. Détection des services actifs (et leurs versions)
4. Crawl web (si appli web)
5. Sélection et exécution des modules de sécurité
6. Génération du rapport

---

## 03 - Cibles.

Un scanner peut analyser tout **dispositif joignable par IP** :

- 🖥️ Ordinateurs, serveurs
- 📱 Smartphones
- 🌐 Sites Web
- 📸 Caméras IP
- 🔌 Objets connectés, automates, robots
- ☎️ Téléphonie IP, IPBX

> 📌 Attention : la qualité du scan dépend des **modules embarqués** (ex: SNMP, SIP, etc.)

---

## 04 - Méthodes de détection

### 📇 1. Footprinting de version.

- Analyse de bannières, signatures réseau
- Croisement avec des bases comme **CVE**, **OSVDB**, **DSA**, **CPE**

> ⚠️ Sujet à **faux positifs** ou **faux négatifs**

---

### ⚔️ 2. Exploitation active.

- Utilise des **exploits connus** (ex: Metasploit, exploit-db)
- Fiable, mais parfois **intrusif/dangereux**

---

### ⚙️ 3. Scan de configuration.

- Analyse les **paramètres exposés** (SSL, DNS, mots de passe par défaut, etc.)
- Peu risqué, mais peut manquer de **contexte**

---

### 🔐 4. Scans authentifiés.

- Nécessite un **compte utilisateur** pour inspection interne
- Très fiable pour détecter les vulnérabilités **logicielles non exposées**

---

### 🌐 5. Spécificité Web.

- Nécessite des modules spécialisés type **OWASP**
- Scanners dédiés : **Burp Suite**, **ZAP**, **Wapiti**, etc.

> Détection des failles type **XSS, SQLi, LFI, RFI**, etc. après **crawling** du site.

---

## 05 - Restitution des résultats.

### 📁 Deux vues principales :

- Par vulnérabilité ➜ machines affectées
- Par machine ➜ vulnérabilités détectées

### 📉 Classification par criticité :

| Niveau       | Description |
|--------------|-------------|
| 🔴 Critique  | Exploitable facilement, contrôle à distance possible |
| 🟠 Majeure   | Exploitable, mais avec conditions |
| 🟡 Moyenne   | Impact limité ou conditions spécifiques |
| 🟢 Mineure   | Peu d’impact, nécessite une chaîne d’exploits |

> Basé sur le **CVSS v3** : score de 0 à 10 prenant en compte vecteur, complexité, privilèges, interactions, périmètre et impacts.

### 📌 Un rapport contient généralement :

- 🔹 Nom de la vulnérabilité
- 🔹 Criticité
- 🔹 Cible
- 🔹 Description & impact
- 🔹 Référence (CVE, DSA…)
- 🔹 Exploitabilité
- 🔹 Recommandations
- 🔹 Taux de confiance
- 🔹 Liens pour approfondir

---

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>

