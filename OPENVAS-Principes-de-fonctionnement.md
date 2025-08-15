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
