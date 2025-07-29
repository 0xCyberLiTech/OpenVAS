


# 🔍 Résumé pédagogique et professionnel : Principes de fonctionnement d’OpenVAS

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

> *Ce document peut être intégré dans une documentation technique, un dépôt GitHub ou utilisé en support pédagogique en formation sécurité.*
