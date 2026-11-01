<!-- MASTER-HEADER-START -->
<div align="center">

<a href="https://0xcyberlitech.com/">
  <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/headers/header-openvas.svg" alt="ATELIER OPENVAS // AUDIT VULNÉRABILITÉS" width="100%" />
</a>

<p align="center">
  <a href="https://0xcyberlitech.com/"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-portal.svg" alt="Portail 0xCyberLiTech.com" width="24%" /></a>
  <a href="https://0xcyberlitech.com/soc-rd.html"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-soc-rd.svg" alt="Livre Blanc SOC Cockpit" width="24%" /></a>
  <a href="https://0xcyberlitech.com/jarvis-rd.html"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-jarvis-rd.svg" alt="Livre Blanc JARVIS IA" width="24%" /></a>
  <a href="https://github.com/0xCyberLiTech?tab=repositories"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-github.svg" alt="Catalogue des 23 Dépôts" width="24%" /></a>
</p>
<p align="center">
  <a href="README.md"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-back-readme.svg" alt="Retour au sommaire du dépôt" width="340" /></a>
</p>

<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/divider-hud.svg" alt="" width="100%" />
</div>
<!-- MASTER-HEADER-END -->

<!-- DEBIAN-TRUTH-START -->
> [!IMPORTANT]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-shield.svg" width="18" height="18" align="absmiddle" alt="" /> ** Matrice Officielle Debian — `Debian 12 (Bookworm)` · `Debian 13 (Trixie)` · `Debian 14 (Forky)`**
> - **Sources Officielles Debian.org (`gvmd`) :** `Bookworm (12)` : **`Stable-12`** &nbsp;·&nbsp; `Trixie (13 — Stable)` : **`Stable-13`** &nbsp;·&nbsp; `Forky (14 — Next-Gen)` : **`26.24.0-2`**
> - **Références Officielles :** [Paquet Debian Trixie (`gvm`)](https://packages.debian.org/trixie/gvm) &nbsp;·&nbsp; [Paquet Debian Forky (`gvm`)](https://packages.debian.org/forky/gvm) &nbsp;·&nbsp; [Documentation Officielle Debian](https://packages.debian.org/trixie/gvm)
> - **Note d'Ingénierie (Divergence 13 vs 14) :** Sous Debian 13 (Trixie) et Debian 14 (Forky), le déploiement conteneurisé s'opère exclusivement via **`docker compose` v2** (ou via le métapaquet natif `gvm` maintenu par l'équipe Debian Security Tools).

<details>
<summary><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> <b>Afficher les Encarts Ligne de Commande : Debian 13 (Trixie — Stable) vs Debian 14 (Forky — Next-Gen)</b></summary>

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Profil Production Stable — Commandes pour `Debian 13 (Trixie)`
```bash
# Debian 13 (Trixie) — Deploiement Greenbone OpenVAS via Docker Compose v2 :
docker compose up -d && docker compose ps
docker compose logs -f gvmd
```

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-rd.svg" width="46" height="16" align="absmiddle" alt="[R&D]" /> Profil Anticipation Next-Gen — Commandes pour `Debian 14 (Forky)`
```bash
# Debian 14 (Forky) — Paquet natif 'gvm' disponible dans les depots Debian Testing/Forky :
apt-cache policy gvm
docker compose pull && docker compose up -d
```

</details>
<!-- DEBIAN-TRUTH-END -->

<!-- CIEL-PEDAGOGY-START -->
<details>
<summary><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> <b>Synthèse d'Architecture, Standards Officiels &amp; Diagnostic (Niveau 1 : Fondamentaux · Niveau 2 : Repères · Niveau 3 : Diagnostic)</b></summary>

- **Niveau 1 — Fondamentaux &amp; Principe d'Architecture :** **Greenbone OpenVAS (GVM)** est une suite d'audit et de détection de vulnérabilités qui évalue la surface d'exposition des systèmes en confrontant leurs services réseau aux flux quotidiens de tests de sécurité (**NVT**, **CVE**, **OVAL**) cotés selon le standard **CVSS v3/v4**.
- **Niveau 2 — Repères Officiels (Ports IANA, Fichiers Debian &amp; Commandes de Validation) :** **Ports :** `TCP 9392` (Interface Web GSA) · `TCP 5432` (PostgreSQL interne) · Socket Redis `/run/redis-openvas/redis.sock` &nbsp;|&nbsp; **Validation officielle :** `sudo gvm-check-setup`.
- **Niveau 3 — Diagnostic d'Incidents &amp; Ingénierie Avancée :** **Diagnostic & Architecture :** Si un audit demeure bloqué à `0%`, vérifiez que la synchronisation initiale des flux de signatures (`sudo greenbone-feed-sync`) est intégralement terminée et que l'instance Redis dédiée à OpenVAS est active. Contrairement à un IDS/IPS qui analyse les attaques en cours, OpenVAS identifie préventivement les vulnérabilités logicielles et défauts de configuration.
- **Sources de Vérité Officielles Éditeurs &amp; Standards :** [Documentation Officielle Greenbone Community Edition](https://greenbone.github.io/docs/latest/) &nbsp;·&nbsp; [Base Nationale des Vulnérabilités NIST NVD](https://nvd.nist.gov/)
- **Livres Blancs &amp; 67 Podcasts Audio R&amp;D :** [Portail 0xCyberLiTech](https://0xcyberlitech.com/) &nbsp;·&nbsp; [Livre Blanc SOC Cockpit v5.5](https://0xcyberlitech.com/soc-rd.html) &nbsp;·&nbsp; [Livre Blanc JARVIS Mark-VII](https://0xcyberlitech.com/jarvis-rd.html) &nbsp;·&nbsp; [Blueprint Logiciel &amp; Matériel RTX 5080](https://0xcyberlitech.com/blueprint-jarvis.html)

</details>
<!-- CIEL-PEDAGOGY-END -->


# <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Principes de fonctionnement d’OpenVAS :

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 1. Définition
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />
**OpenVAS** (aujourd’hui intégré à la suite **Greenbone Vulnerability Management - GVM**) est un **outil open-source d’évaluation de vulnérabilités**. Il permet d’analyser des hôtes, services et applications afin d’identifier des **failles de sécurité connues**.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> 2. Principe général de fonctionnement
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

### a. <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-network.svg" width="18" height="18" align="absmiddle" alt="" /> Architecture modulaire (client-serveur)
- **openvas-scanner** : effectue les analyses.
- **gvmd** : gère les tâches, utilisateurs et rapports.
- **gsad (GSA)** : interface web (Greenbone Security Assistant).
- **Greenbone Feed** : base de données de tests de vulnérabilités (NVTs).

### b. <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Mécanisme d’analyse
- Utilise des **NVTs** (Network Vulnerability Tests).
- Simule des requêtes, attaques ou vérifications pour détecter :
  - Versions vulnérables,
  - Mauvaises configurations,
  - Ports/services ouverts,
  - Failles connues (CVE).

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> 3. Composants techniques
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

| Composant           | Description                                                      |
|---------------------|------------------------------------------------------------------|
| `openvas-scanner`   | Réalise les tests de vulnérabilités                             |
| `gvmd`              | Gère les tâches, utilisateurs, configurations et rapports        |
| `gsad`              | Interface Web de gestion des analyses et des résultats           |
| **Greenbone Feed**  | Fournit les mises à jour des NVTs (tests de vulnérabilités)      |

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-rd.svg" width="46" height="16" align="absmiddle" alt="[R&D]" /> 4. Cycle d’analyse
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

1. **Mise à jour des NVTs** via le Greenbone Community Feed.
2. **Création d'une tâche de scan** (cibles, politique, timing).
3. **Lancement du scan** sur les hôtes définis.
4. **Collecte et analyse des résultats** par le manager.
5. **Rapport détaillé** : vulnérabilités, score CVSS, recommandations.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 5. Objectifs professionnels
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-shield.svg" width="18" height="18" align="absmiddle" alt="" /> Identifier et corriger les failles de sécurité.
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Se conformer aux standards (ISO 27001, PCI-DSS, RGPD…).
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Réaliser des scans réguliers et automatisés.
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> Fournir des rapports exploitables pour les RSSI/DSI/techniciens.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> 6. Avantages
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- **Gratuit** et **open-source** (version communautaire).
- **Base de tests régulièrement mise à jour**.
- **Compatible avec de nombreux environnements** (Linux, Docker, Cloud).
- **Automatisable** via CLI/API pour CI/CD ou supervision.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-alert.svg" width="18" height="18" align="absmiddle" alt="" /> 7. Limites et précautions
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- Détecte uniquement les **vulnérabilités connues** (pas de 0-day).
- Risque de **perturbation des services** si le scan est agressif.
- Certains tests nécessitent une **authentification sur la cible**.
- La lecture des rapports nécessite une **interprétation experte**.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Conclusion
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

OpenVAS/GVM est un **outil essentiel de cybersécurité défensive**. Il permet une **analyse proactive et continue** de la surface d’attaque d’un système. Son bon usage repose sur :
- une **mise à jour fréquente** des NVTs,
- une **planification rigoureuse** des tâches,
- une **analyse sérieuse** des résultats pour mise en conformité et renforcement de la sécurité.

<!-- MASTER-FOOTER-START -->
<div align="center">
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/divider-hud.svg" alt="" width="100%" />

<a href="https://0xcyberlitech.com/">
  <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/footer-master.svg" alt="0xCyberLiTech — Architecture Cyberdéfense, Ingénierie Déterministe & IA Souveraine" width="100%" />
</a>

<p align="center"><a href="https://0xcyberlitech.com/"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/badge-antigravity.svg" alt="Architecturé par Marc & Antigravity (Google DeepMind)" width="520" /></a></p>

<sub><b>Architecturé &amp; Forgé par Marc &amp; Antigravity (Google DeepMind)</b> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/"><b>0xcyberlitech.com</b></a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/soc-rd.html">Architecture SOC Cockpit v5.5</a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/jarvis-rd.html">Architecture JARVIS Mark-VII</a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/blueprint-jarvis.html">Blueprint Matériel RTX 5080</a></sub>

</div>
<!-- MASTER-FOOTER-END -->
