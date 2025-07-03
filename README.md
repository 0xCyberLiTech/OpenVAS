![OpenVAS](./images/OpenVAS.png)

> Guide complet pour comprendre, installer et utiliser OpenVAS (Greenbone Vulnerability Management) dans vos environnements.

---

## 🧭 Sommaire

1. [🛠️ Qu'est-ce qu'un scanner de vulnérabilités](#01---quest-ce-quun-scanner-de-vulnérabilités)
2. [⚙️ Principes de fonctionnement](#02---principes-de-fonctionnement)
3. [🎯 Cibles](#03---cibles)
4. [🔍 Méthodes de détection](#04---méthodes-de-détection)
5. [📊 Restitution des résultats](#05---restitution-des-résultats)
6. [🐳 Installation avec Docker Compose](OpenVAS-installation-depuis-Docker-compose.md)
7. [🔄 Mise à jour des conteneurs Greenbone](Mise_à_jour_des_conteneurs_communautaires_Greenbone.md)

---

## 01 - Qu'est-ce qu'un scanner de vulnérabilités

Un **scanner de vulnérabilités** est un programme permettant de détecter des failles dans des systèmes, réseaux ou applications.

### 🎯 Utilisation

| Légale ✅ | Illégale ❌ |
|----------|-------------|
| Audit interne, tests de sécurité, conformité | Recherche de failles pour exploitation non autorisée |

> Les scanners peuvent être utilisés dans un **SIEM**, un **SOC** ou intégrés dans des stratégies de **cybersécurité préventive**.

---

## 02 - Principes de fonctionnement

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

## 03 - Cibles

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

### 📇 1. Footprinting de version

- Analyse de bannières, signatures réseau
- Croisement avec des bases comme **CVE**, **OSVDB**, **DSA**, **CPE**

> ⚠️ Sujet à **faux positifs** ou **faux négatifs**

---

### ⚔️ 2. Exploitation active

- Utilise des **exploits connus** (ex: Metasploit, exploit-db)
- Fiable, mais parfois **intrusif/dangereux**

---

### ⚙️ 3. Scan de configuration

- Analyse les **paramètres exposés** (SSL, DNS, mots de passe par défaut, etc.)
- Peu risqué, mais peut manquer de **contexte**

---

### 🔐 4. Scans authentifiés

- Nécessite un **compte utilisateur** pour inspection interne
- Très fiable pour détecter les vulnérabilités **logicielles non exposées**

---

### 🌐 5. Spécificité Web

- Nécessite des modules spécialisés type **OWASP**
- Scanners dédiés : **Burp Suite**, **ZAP**, **Wapiti**, etc.

> Détection des failles type **XSS, SQLi, LFI, RFI**, etc. après **crawling** du site.

---

## 05 - Restitution des résultats

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

## 🌐 À propos de moi

- 💡 Passionné par Debian GNU/Linux depuis plusieurs années
- 🎓 Autodidacte, avec un fort esprit de transmission
- 🔐 Intéressé par la cybersécurité, les solutions open source et la performance système
- 🧪 Toujours partant pour tester une nouvelle stack technique

---

<p align="center">
  🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessible à tous.
</p>
