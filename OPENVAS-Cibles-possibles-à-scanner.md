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

</details>
<!-- CIEL-PEDAGOGY-END -->


# <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> Cibles Possibles à Scanner avec OpenVAS :

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> 01 // Objectif du document
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />
Fournir un aperçu clair et professionnel des types de cibles que l'on peut évaluer avec **OpenVAS** (via **Greenbone Community Edition**), en illustrant avec des exemples concrets dans des contextes réalistes (entreprise, lab, audit).

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> Introduction :
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

**OpenVAS** est un scanner de vulnérabilités open source puissant, conçu pour analyser des systèmes et détecter des failles de sécurité. Il est couramment utilisé par les professionnels de la cybersécurité dans le cadre d’audits, de tests de conformité, ou d’évaluations internes.

Pour maximiser la pertinence d'un scan, il est essentiel de bien identifier les **cibles**.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-shield.svg" width="18" height="18" align="absmiddle" alt="" /> Types de cibles que l’on peut scanner avec OpenVAS :
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 1. Serveurs (Windows / Linux)
- **But** : Détection des vulnérabilités sur les services exposés, OS, ports ouverts.
- **Exemples** :
  - Serveur **Debian 12 (Bookworm), Debian 13 (Trixie) & Debian 14 (Forky)** hébergeant un site web (Apache/Nginx).
  - **Windows Server 2019** avec Active Directory.
- **Scénario pédagogique** :
  > Déployer une VM Debian avec un service SSH et HTTP. Utiliser OpenVAS pour détecter une version obsolète d’OpenSSH.

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 2. Équipements réseau (switch, routeurs, firewalls).
- **But** : Identifier les faiblesses liées à l’administration à distance (telnet, SNMP, HTTP).
- **Exemples** :
  - **Switch Cisco** accessible via Telnet.
  - **Pare-feu pfSense** avec interface Web.
- **Scénario pédagogique** :
  > Simuler un routeur mal configuré avec SNMP public. OpenVAS peut alerter sur l’accès non restreint.

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 3. Applications Web (via IP ou nom de domaine)
- **But** : Détection de vulnérabilités applicatives, mauvaises configurations, certificats expirés.
- **Exemples** :
  - CMS **WordPress** auto-hébergé.
  - Intranet d’entreprise développé en PHP.
- **Scénario pédagogique** :
  > Déployer un WordPress sur LAMP avec des plugins vulnérables. OpenVAS détectera les CVE connues.

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 4. Équipements IoT ou embarqués
- **But** : Évaluer la surface d’attaque des objets connectés.
- **Exemples** :
  - Caméra IP connectée.
  - NAS grand public (Synology, QNAP).
- **Scénario pédagogique** :
  > Simuler un NAS avec ports ouverts et firmware obsolète. OpenVAS indiquera les failles connues.

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 5. Postes clients (tests internes encadrés)
- **But** : Vérifier les failles au niveau des OS clients ou logiciels installés.
- **Exemples** :
  - Windows 10 avec Java non mis à jour.
  - Station Linux avec navigateur ou service exposé.
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-alert.svg" width="18" height="18" align="absmiddle" alt="" /> **Attention** : Ces scans nécessitent un cadre légal strict (test interne contrôlé).

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 6. Infrastructure virtuelle ou cloud
- **But** : Scanner des VM internes ou hébergées chez un fournisseur.
- **Exemples** :
  - VM sur **Proxmox**, **VMware**, ou dans un cloud privé.
  - Instances **OVH / Scaleway / AWS**.
- **Scénario pédagogique** :
  > Scanner une instance cloud exposant un port SSH avec une mauvaise configuration (authentification par mot de passe).

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 7. Équipements industriels / SCADA (en environnement sécurisé)
- **But** : Identifier les vulnérabilités sur les systèmes OT (Operational Technology).
- **Exemples** :
  - Automate programmable Siemens.
  - Interface web d’un système de contrôle industriel.
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-alert.svg" width="18" height="18" align="absmiddle" alt="" /> **Important** : Ces scans doivent être réalisés avec **grande précaution** pour éviter tout impact sur la production.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Bonnes pratiques lors de la définition des cibles
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- Toujours avoir une **autorisation écrite** pour scanner une cible.
- Isoler les tests dans un **environnement de lab** avant toute intervention en production.
- Commencer par des scans **non intrusifs**, puis progresser vers des scans plus complets.
- Éviter de scanner des cibles sensibles sans plan de mitigation ou supervision.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> Conclusion
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

OpenVAS est capable de scanner une grande variété de systèmes, des serveurs aux équipements réseau, en passant par les applications web et les postes clients. Bien définir ses cibles permet d’obtenir des résultats pertinents et exploitables, tout en respectant les cadres légaux et techniques.

La richesse des scans dépend directement de la qualité des cibles sélectionnées et de leur configuration.

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
