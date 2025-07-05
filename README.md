<div align="center">

<a href="https://github.com/0xCyberLiTech">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=33FF33&center=true&vCenter=true&width=700&lines=SCANNER+DE+VULNÉRABILITÉS;OpenVAS+•+Greenbone+(GVM);Détection+•+Analyse+•+Sécurité" alt="Typing SVG" />
</a>

<p align="center">
  <em>Guide pour comprendre et utiliser OpenVAS (Greenbone).</em><br>
  <b>🛡️ Audit – 🔍 Détection – 🔐 Remédiation</b>
</p>

</div>

---

### 🧭 **Navigation Rapide**
> Guide complet pour comprendre, installer et utiliser OpenVAS (Greenbone Vulnerability Management) dans vos environnements.

<div align="center">

| Section | Description | Accès Rapide |
|:---:|:---|:---:|
| **Introduction** | Qu'est-ce qu'un scanner de vulnérabilités ? | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#-1-quest-ce-quun-scanner-de-vulnérabilités) |
| **Fonctionnement** | Les principes et phases d'un scan de sécurité. | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#-2-principes-de-fonctionnement) |
| **Installation** | Guide d'installation avec Docker Compose. | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](OpenVAS-installation-depuis-Docker-compose.md) |
| **Mise à jour** | Maintenir à jour les conteneurs Greenbone. | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](Mise_à_jour_des_conteneurs_communautaires_Greenbone.md) |

</div>

---

### 🛠️ 1. Qu'est-ce qu'un scanner de vulnérabilités ?
> Un **scanner de vulnérabilités** est un programme permettant de détecter des failles dans des systèmes, réseaux ou applications. Son utilisation peut être légale (audit, tests de sécurité) ou illégale (recherche de failles pour exploitation). Il s'intègre souvent dans des stratégies de cybersécurité préventive au sein d'un **SIEM** ou d'un **SOC**.

---

### ⚙️ 2. Principes de fonctionnement
Un scanner, qu'il soit une application, une appliance virtuelle ou un service SaaS, suit généralement ces étapes :
1.  **Découverte** de la cible (ping, ARP...).
2.  **Scan de ports** ouverts (TCP/UDP).
3.  **Détection des services** et de leurs versions.
4.  **Crawl web** (pour les applications web).
5.  **Exécution des modules** de tests de sécurité.
6.  **Génération** du rapport.

---

### 🎯 3. Cibles
> Tout dispositif joignable par une adresse IP peut être analysé : serveurs, smartphones, sites web, objets connectés, téléphonie IP, etc. La qualité du scan dépend des **modules embarqués** (SNMP, SIP, etc.).

---

### 🔍 4. Méthodes de détection

#### 1. Footprinting de version
Analyse les bannières et signatures réseau pour les croiser avec des bases de données de vulnérabilités (**CVE**, **CPE**). Cette méthode peut cependant générer des **faux positifs** ou **faux négatifs**.

#### 2. Exploitation active
Tente d'utiliser des **exploits connus** (ex: Metasploit) pour confirmer une faille. C'est une méthode fiable, mais potentiellement **intrusive**.

#### 3. Scan de configuration
Analyse les paramètres exposés (SSL, DNS, mots de passe par défaut). Moins risqué, mais peut manquer de contexte.

#### 4. Scans authentifiés
Utilise un compte utilisateur pour inspecter le système de l'intérieur, ce qui permet de détecter des vulnérabilités logicielles **non exposées** de manière très fiable.

#### 5. Spécificité Web
Nécessite des modules spécialisés (**OWASP**) pour détecter des failles de type **XSS, SQLi, LFI**, etc., après un crawling complet du site.

---

### 📊 5. Restitution des résultats
Les résultats sont classés par criticité (Critique, Majeure, Moyenne, Mineure) sur la base du score **CVSS v3**.

| Niveau | Description |
|:---:|:---|
| 🔴 **Critique** | Exploitable facilement, contrôle à distance possible. |
| 🟠 **Majeure** | Exploitable, mais avec des conditions spécifiques. |
| 🟡 **Moyenne** | Impact limité ou conditions d'exploitation complexes. |
| 🟢 **Mineure** | Peu d’impact, nécessite souvent une chaîne d’exploits. |

> Un rapport détaillé contient le nom de la vulnérabilité, sa criticité, la cible, une description, des références (CVE), des recommandations et des liens pour approfondir.

---

### 👨‍💻 **À propos de moi**

> * 💡 Passionné par Debian GNU/Linux depuis plusieurs années
> * 🎓 Autodidacte, avec un fort esprit de transmission
> * 🔐 Intéressé par la cybersécurité, les solutions open source et la performance système
> * 🧪 Toujours partant pour tester une nouvelle stack technique

---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
