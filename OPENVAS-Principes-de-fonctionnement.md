<div align="center">

  <br></br>
  
  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3EOPENVAS_" alt="Titre dynamique OPENVAS" />
  </a>
  
  <br></br>
  
  <p align="center">
    <em>Principes de fonctionnement d'OpenVAS.</em><br>
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

<p align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="420">
  </a>
</p>

---

### 🎯 **Objectif de ce dépôt.**

> Ce dépôt a pour vocation de centraliser un ensemble de notions clés autour d'OpenVAS (Open Vulnerability Assessment System). Il s’adresse aux passionnés, étudiants et professionnels souhaitant mieux comprendre
> les principes de l'analyse de vulnérabilités, apprendre à installer, configurer et utiliser OpenVAS pour identifier les faiblesses de leurs systèmes, et se familiariser avec les concepts et outils essentiels
> pour renforcer la sécurité de leurs infrastructures informatiques.

---

# 🔍 Principes de fonctionnement d’OpenVAS :

## 🧭 1. Définition
**OpenVAS** (aujourd’hui intégré à la suite **Greenbone Vulnerability Management - GVM**) est un **outil open-source d’évaluation de vulnérabilités**. Il permet d’analyser des hôtes, services et applications afin d’identifier des **failles de sécurité connues**.

---

## ⚙️ 2. Principe général de fonctionnement

### a. 🔗 Architecture modulaire (client-serveur)
- **openvas-scanner** : effectue les analyses.
- **gvmd** : gère les tâches, utilisateurs et rapports.
- **gsad (GSA)** : interface web (Greenbone Security Assistant).
- **Greenbone Feed** : base de données de tests de vulnérabilités (NVTs).

### b. 🧪 Mécanisme d’analyse
- Utilise des **NVTs** (Network Vulnerability Tests).
- Simule des requêtes, attaques ou vérifications pour détecter :
  - Versions vulnérables,
  - Mauvaises configurations,
  - Ports/services ouverts,
  - Failles connues (CVE).

---

## 🧱 3. Composants techniques

| Composant           | Description                                                      |
|---------------------|------------------------------------------------------------------|
| `openvas-scanner`   | Réalise les tests de vulnérabilités                             |
| `gvmd`              | Gère les tâches, utilisateurs, configurations et rapports        |
| `gsad`              | Interface Web de gestion des analyses et des résultats           |
| **Greenbone Feed**  | Fournit les mises à jour des NVTs (tests de vulnérabilités)      |

---

## 🔄 4. Cycle d’analyse

1. **Mise à jour des NVTs** via le Greenbone Community Feed.
2. **Création d'une tâche de scan** (cibles, politique, timing).
3. **Lancement du scan** sur les hôtes définis.
4. **Collecte et analyse des résultats** par le manager.
5. **Rapport détaillé** : vulnérabilités, score CVSS, recommandations.

---

## 🎯 5. Objectifs professionnels

- 🛡️ Identifier et corriger les failles de sécurité.
- 📊 Se conformer aux standards (ISO 27001, PCI-DSS, RGPD…).
- 🔁 Réaliser des scans réguliers et automatisés.
- 📋 Fournir des rapports exploitables pour les RSSI/DSI/techniciens.

---

## ✅ 6. Avantages

- **Gratuit** et **open-source** (version communautaire).
- **Base de tests régulièrement mise à jour**.
- **Compatible avec de nombreux environnements** (Linux, Docker, Cloud).
- **Automatisable** via CLI/API pour CI/CD ou supervision.

---

## ⚠️ 7. Limites et précautions

- Détecte uniquement les **vulnérabilités connues** (pas de 0-day).
- Risque de **perturbation des services** si le scan est agressif.
- Certains tests nécessitent une **authentification sur la cible**.
- La lecture des rapports nécessite une **interprétation experte**.

---

## 📚 Conclusion

OpenVAS/GVM est un **outil essentiel de cybersécurité défensive**. Il permet une **analyse proactive et continue** de la surface d’attaque d’un système. Son bon usage repose sur :
- une **mise à jour fréquente** des NVTs,
- une **planification rigoureuse** des tâches,
- une **analyse sérieuse** des résultats pour mise en conformité et renforcement de la sécurité.

---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
