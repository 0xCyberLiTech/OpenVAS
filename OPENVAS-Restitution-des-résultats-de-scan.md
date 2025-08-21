<div align="center">

  <br></br>
  
  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3EOPENVAS_" alt="Titre dynamique OPENVAS" />
  </a>
  
  <br></br>
  
  <p align="center">
    <em>Restitution des résultats de scan OpenVAS.</em><br>
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

# 📊 Restitution des résultats de scan OpenVAS :

## 🎯 Objectif
Après chaque analyse, **OpenVAS** (via GVM) génère un **rapport de vulnérabilités détaillé**. Ce rapport permet aux administrateurs et aux analystes de :
- Visualiser les failles identifiées,
- Évaluer leur criticité,
- Prendre des décisions pour remédier aux risques.

---

## 📁 1. Types de résultats générés

| Type de résultat        | Description                                                   |
|-------------------------|---------------------------------------------------------------|
| **Vulnérabilités**      | Failles connues détectées sur les hôtes scannés               |
| **Informations**        | Détails techniques (version de services, ports ouverts…)      |
| **Alertes**             | Risques potentiels à confirmer ou investiguer                 |
| **Recommandations**     | Correctifs suggérés, configuration à modifier                 |

---

## 📐 2. Critères de classification des vulnérabilités

OpenVAS/GVM s'appuie sur les standards **CVSS** (Common Vulnerability Scoring System) pour évaluer la sévérité :

| Score CVSS (v3.x) | Niveau de criticité | Couleur dans GSA |
|-------------------|---------------------|------------------|
| 0.1 – 3.9         | Faible              | 🟢 Vert          |
| 4.0 – 6.9         | Moyenne             | 🟡 Jaune         |
| 7.0 – 8.9         | Élevée              | 🟠 Orange        |
| 9.0 – 10.0        | Critique            | 🔴 Rouge         |

---

## 📊 3. Formes de restitution disponibles

| Format | Usage                                                                 |
|--------|-----------------------------------------------------------------------|
| **HTML**  | Lecture directe via interface web (GSA)                            |
| **PDF**   | Rapport formel, exportable pour les réunions ou audits            |
| **XML**   | Intégration dans d’autres outils (SIEM, automatisation)           |
| **CSV**   | Exploitation par tableur ou scripts d’analyse                     |
| **TXT**   | Version brute, lecture rapide, parsing simplifié                  |

---

## 🧭 4. Contenu d’un rapport typique

- ✅ **Résumé global** : nombre de vulnérabilités par niveau.
- 🖥️ **Liste des hôtes scannés** : adresse IP, nom d’hôte, statut.
- 🧱 **Détails par hôte** :
  - Ports/services détectés,
  - Vulnérabilités associées,
  - Description technique,
  - CVE liées, score CVSS,
  - Recommandation corrective.
- 🗂️ **Regroupement par familles** : par type de test, protocole ou criticité.

---

## 📈 5. Exemples d'exploitation professionnelle

- **Équipe SOC / RSSI** : priorisation des actions de remédiation.
- **Auditeurs sécurité** : preuve de conformité ou non-conformité.
- **Techniciens système/réseau** : application des correctifs recommandés.
- **Comités de pilotage** : rapports synthétiques (ex : top 10 des failles critiques).

---

## 🧰 6. Outils intégrés ou compatibles pour analyse post-scan

- Interface GSA : filtres avancés, tri par score ou hôte.
- Export CSV + Excel : tri, regroupement, tableaux croisés.
- API GVM : automatisation du traitement des rapports.
- Intégration avec SIEM : pour corrélation et alerting.

---

## 📌 7. Bonnes pratiques

- ✅ Toujours **mettre à jour le feed Greenbone** avant les scans.
- 📅 Planifier des **scans réguliers** (hebdo / mensuels).
- 📁 Archiver les **rapports datés** (référence historique).
- 🧠 Analyser en priorité les **vulnérabilités critiques** et exploitables à distance.
- 🔐 Si possible, effectuer des **scans authentifiés** pour des résultats plus précis.

---

## 📝 Conclusion

La restitution des scans OpenVAS permet une **vision précise de l’exposition aux vulnérabilités**. Les rapports, s’ils sont bien analysés, deviennent de **véritables outils décisionnels** en cybersécurité.

---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>

