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


# <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Restitution des résultats de scan OpenVAS :

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> Objectif
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />
Après chaque analyse, **OpenVAS** (via GVM) génère un **rapport de vulnérabilités détaillé**. Ce rapport permet aux administrateurs et aux analystes de :
- Visualiser les failles identifiées,
- Évaluer leur criticité,
- Prendre des décisions pour remédier aux risques.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 1. Types de résultats générés
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

| Type de résultat        | Description                                                   |
|-------------------------|---------------------------------------------------------------|
| **Vulnérabilités**      | Failles connues détectées sur les hôtes scannés               |
| **Informations**        | Détails techniques (version de services, ports ouverts…)      |
| **Alertes**             | Risques potentiels à confirmer ou investiguer                 |
| **Recommandations**     | Correctifs suggérés, configuration à modifier                 |

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 2. Critères de classification des vulnérabilités
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

OpenVAS/GVM s'appuie sur les standards **CVSS** (Common Vulnerability Scoring System) pour évaluer la sévérité :

| Score CVSS (v3.x) | Niveau de criticité | Couleur dans GSA |
|-------------------|---------------------|------------------|
| 0.1 – 3.9 | Faible | <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Vert |
| 4.0 – 6.9 | Moyenne | <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-rd.svg" width="46" height="16" align="absmiddle" alt="[R&D]" /> Jaune |
| 7.0 – 8.9 | Élevée | <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-rd.svg" width="46" height="16" align="absmiddle" alt="[R&D]" /> Orange |
| 9.0 – 10.0 | Critique | <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ko.svg" width="42" height="16" align="absmiddle" alt="[NON]" /> Rouge |

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 3. Formes de restitution disponibles
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

| Format | Usage                                                                 |
|--------|-----------------------------------------------------------------------|
| **HTML**  | Lecture directe via interface web (GSA)                            |
| **PDF**   | Rapport formel, exportable pour les réunions ou audits            |
| **XML**   | Intégration dans d’autres outils (SIEM, automatisation)           |
| **CSV**   | Exploitation par tableur ou scripts d’analyse                     |
| **TXT**   | Version brute, lecture rapide, parsing simplifié                  |

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 4. Contenu d’un rapport typique
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> **Résumé global** : nombre de vulnérabilités par niveau.
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> **Liste des hôtes scannés** : adresse IP, nom d’hôte, statut.
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> **Détails par hôte** :
  - Ports/services détectés,
  - Vulnérabilités associées,
  - Description technique,
  - CVE liées, score CVSS,
  - Recommandation corrective.
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> **Regroupement par familles** : par type de test, protocole ou criticité.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 5. Exemples d'exploitation professionnelle
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- **Équipe SOC / RSSI** : priorisation des actions de remédiation.
- **Auditeurs sécurité** : preuve de conformité ou non-conformité.
- **Techniciens système/réseau** : application des correctifs recommandés.
- **Comités de pilotage** : rapports synthétiques (ex : top 10 des failles critiques).

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 6. Outils intégrés ou compatibles pour analyse post-scan
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- Interface GSA : filtres avancés, tri par score ou hôte.
- Export CSV + Excel : tri, regroupement, tableaux croisés.
- API GVM : automatisation du traitement des rapports.
- Intégration avec SIEM : pour corrélation et alerting.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 7. Bonnes pratiques
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Toujours **mettre à jour le feed Greenbone** avant les scans.
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Planifier des **scans réguliers** (hebdo / mensuels).
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Archiver les **rapports datés** (référence historique).
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-brain.svg" width="18" height="18" align="absmiddle" alt="" /> Analyser en priorité les **vulnérabilités critiques** et exploitables à distance.
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-crypto.svg" width="18" height="18" align="absmiddle" alt="" /> Si possible, effectuer des **scans authentifiés** pour des résultats plus précis.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Conclusion
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

La restitution des scans OpenVAS permet une **vision précise de l’exposition aux vulnérabilités**. Les rapports, s’ils sont bien analysés, deviennent de **véritables outils décisionnels** en cybersécurité.

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
