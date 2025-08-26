<div align="center">

  <br></br>
  
  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3EOPENVAS_" alt="Titre dynamique OPENVAS" />
  </a>
  
  <br></br>
  
  <p align="center">
    <em>Un dépôt pédagogique sur les scanners de vulnérabilités.</em><br>
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

<p align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="420">
  </a>
</p>

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
