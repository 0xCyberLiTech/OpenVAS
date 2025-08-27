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

<!--
Optimisation SEO : mots-clés cybersécurité, Linux, administration système, sécurité informatique, tutoriels, guides, expertise, formation, supervision, Docker, OpenVAS, firewall, proxy, DNS, SSH, Debian, IT, réseau, cryptographie, open source, ressources techniques, étudiants, professionnels, passionnés.
-->

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

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>
