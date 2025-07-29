<div align="center">

  ![OpenVAS](./images/OpenVAS.png)

  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=D14A4A&center=true&vCenter=true&width=650&lines=AUDIT+DE+SÉCURITÉ+AUTOMATISÉ;Identifier+•+Analyser+•+Sécuriser;OpenVAS+•+Pentesting+•+Rapports" alt="Typing SVG" />
  </a>
  
  <p align="center">
    <em>Mise à jour des conteneurs Greenbone.</em><br>
    <b>📊 Monitoring – 📈 Performance – ⚙️ Fiabilité</b>
  </p>
  
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
> 🎯 **Objectif :** proposer un contenu clair, structuré et accessible pour étudiants, curieux et professionnels de l’IT.  
> 🔗 [Mon GitHub principal](https://github.com/0xCyberLiTech)

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim" alt="Skills" />
  </a>
</p>

---

### 🎯 **Objectif de ce dépôt.**

> Ce dépôt a pour vocation de centraliser un ensemble de notions clés autour d'OpenVAS (Open Vulnerability Assessment System). Il s’adresse aux passionnés, étudiants et professionnels souhaitant mieux comprendre
> les principes de l'analyse de vulnérabilités, apprendre à installer, configurer et utiliser OpenVAS pour identifier les faiblesses de leurs systèmes, et se familiariser avec les concepts et outils essentiels
> pour renforcer la sécurité de leurs infrastructures informatiques.

---

## 💡 **Mise à jour des conteneurs communautaires Greenbone :**


```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml pull
```

Lancement des conteneurs communautaires Greenbone


```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml up -d
```

## Exécution d’une synchronisation de flux :

Pour l’analyse de vulnérabilité proprement dite, les tests de vulnérabilité, des informations de sécurité telles que les CVE, les listes de ports et les configurations d’analyse sont requises. Toutes ces données sont fournies par le Greenbone Community Feed via des images de conteneur de données.

Une synchronisation d’alimentation se compose toujours de deux parties :

- Téléchargement des modifications via l’extraction de nouvelles images de conteneur.
- Chargement des modifications dans la mémoire et une base de données par un démon.

Les deux étapes peuvent prendre un certain temps, de quelques minutes à des heures, en particulier pour le synchronisation initiale. Ce n’est que si les deux étapes sont terminées que les données synchronisées est à jour et peut être utilisé.

La première étape se fait via le docker compose pull. La deuxième étape consiste à Effectué automatiquement lorsque les démons sont en cours d’exécution.

## Téléchargement des modifications du flux :

Les données du Greenbone Community Feed sont fournies via plusieurs images de conteneur. Lorsque ces images sont démarrées, elles copient les données dans le fichier Docker volumes automatiquement. Ensuite, les données sont récupérées à partir de la volumes par les démons en cours d’exécution.

Pour télécharger les dernières images de conteneur de données de flux, exécutez :

Téléchargement des conteneurs de données de flux Greenbone Community Edition


```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml pull notus-data vulnerability-tests scap-data dfn-cert-data cert-bund-data report-formats data-objects
```

Pour copier les données des images vers les volumes, exécutez :

Démarrage des conteneurs de données de flux Greenbone Community


```bash
docker compose -f $DOWNLOAD_DIR/docker-compose.yml up -d notus-data vulnerability-tests scap-data dfn-cert-data cert-bund-data report-formats data-objects
```

## Chargement des modifications du flux :

Important :

Lorsque le contenu du flux a été téléchargé, les nouvelles données doivent être chargées par le démons correspondants. Cela peut prendre de quelques minutes à des heures, en particulier pour le chargement initial des données. Sans données chargées, les analyses contiendront résultats incomplets et erronés.

Une fois les conteneurs de la communauté Greenbone démarrés, les démons en cours d’exécution récupérera toujours le contenu du flux et chargera les données automatiquement.

### Données des tests de vulnérabilité :

Si le journal (de ospd-openvas) contient la sortie suivante, l’OpenVAS Le scanner commence à charger les nouvelles données VT :

message de chargement du journal VT ospd-openvas.


```bash
Loading VTs. Scans will be [requested|queued] until VTs are loaded. This may
take a few minutes, please wait...
```

Le chargement des données VT est terminé si le message de journal se trouve :

ospd-openvas VTs chargement du message de journal terminé.


```bash
Finished loading VTs. The VT cache has been updated from version X to Y.
```

Une fois que le scanner a connaissance des données VT, les données seront demandées par gvmd. Ceci Le message de journal suivant s’affichera :

Message de chargement du journal des VT gvmd.


```bash
OSP service has different VT status (version X) from database (version (Y), Z VTs). Starting update
```

Lorsque gvmd a fini de charger tous les VT, le message suivant s’affiche :

Message de chargement du journal de fin des VT gvmd.


```bash
Updating VTs in database ... done (X VTs).
```

## Données SCAP :

gvmd commence à charger les données SCAP contenant les informations CPE et CVE lorsque le message suivant se trouve dans les journaux :

Message du journal de chargement des données SCAP gvmd.


```bash
update_scap: Updating data from feed
```

Les données SCAP sont chargées et la synchronisation est terminée lorsque le journal (gvmd) Contient le message suivant :

gvmd Chargement des données SCAP message de fin du journal.


```bash
update_scap_end: Updating SCAP info succeeded
```

## Données CERT :

gvmd commence à charger les données CERT contenant les avis DFN-CERT et CERT-Bund lorsque le message suivant se trouve dans les journaux :

Message du journal de chargement des données CERT gvmd


```bash
sync_cert: Updating data from feed
```

Les données CERT sont chargées et la synchronisation est terminée lorsque le journal (gvmd) Contient le message suivant :

Message de fin de chargement des données CERT gvmd.


```bash
sync_cert: Updating CERT info succeeded.
```

## Données GVMD :

Le journal contient plusieurs messages lors du chargement des données gvmd. Pour les listes de ports, Ces messages sont similaires à :

Message de journal chargé de la liste des ports gvmd.


```bash
Port list All IANA assigned TCP (33d0cd82-57c6-11e1-8ed1-406186ea4fc5) has been created by admin
```

Pour les formats de rapport :

Message de journal chargé au format de rapport gvmd.


```bash
Report format XML (a994b278-1f62-11e1-96ac-406186ea4fc5) has been created by admin
```

Indice :

Les configurations de balayage ne peuvent être chargées que si les données VT sont disponibles dans gvmd et un flux L’option Importer le propriétaire est définie.

Pour les configurations d’analyse :

Message de journal chargé de la configuration d’analyse gvmd.

```bash
Scan config Full and fast (daba56c8-73ec-11df-a475-002264764cea) has been created by admin
```
---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
