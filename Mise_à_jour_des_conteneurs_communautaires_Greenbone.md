![OpenVAS](./images/OpenVAS.png)

# Mise à jour des conteneurs communautaires Greenbone.

Pour mettre à jour les conteneurs communautaires Greenbone vers la dernière version, il est nécessaire de lancer la commande suivante :

Téléchargement des conteneurs communautaires Greenbone.
```
cd ~/greenbone-community-container/
docker-compose -f docker-compose.yml -p greenbone-community-edition pull
```
Lancement des conteneurs communautaires Greenbone.
```
docker-compose -f docker-compose.yml -p greenbone-community-edition up -d
```
Exécution d’une synchronisation de flux.

Pour l’analyse des vulnérabilités, les tests de vulnérabilité, des informations de sécurité telles que les CVE, les listes de ports et les configurations d’analyse sont requises. Toutes ces données sont fournies par le Greenbone Community Feed via un flux dédié Images de conteneur de données.

Une synchronisation de flux se compose toujours de deux parties :

Téléchargement des modifications via l’extraction de nouvelles images de conteneur

Chargement des modifications en mémoire et dans une base de données par un démon.

Les deux étapes peuvent prendre un certain temps, de quelques minutes à quelques heures, en particulier pour le synchronisation initiale. 
Ce n’est que si les deux étapes sont terminées que les données synchronisées est à jour et peut être utilisé.

La première étape se fait via le docker-compose pull. La deuxième étape est Effectué automatiquement lorsque les démons sont en cours d’exécution.

Téléchargement des modifications de flux.

Les données du Greenbone Community Feed sont fournies via plusieurs Images de conteneurs. 

Lorsque ces images sont démarrées, elles copient les données dans le Volumes Docker automatiquement. 

Ensuite, les données sont récupérées à partir du volumes par les démons en cours d’exécution.

Pour télécharger les dernières images de conteneur de données de flux, exécutez.

Téléchargement des conteneurs de données de flux Greenbone Community Edition.
```
docker-compose -f $DOWNLOAD_DIR/docker-compose.yml -p greenbone-community-edition pull notus-data vulnerability-tests scap-data dfn-cert-data cert-bund-data report-formats data-objects
```
Pour copier les données des images vers les volumes exécutés.

Démarrage des conteneurs de données de flux Greenbone Community.
```
docker-compose -f $DOWNLOAD_DIR/docker-compose.yml -p greenbone-community-edition up -d notus-data vulnerability-tests scap-data dfn-cert-data cert-bund-data report-formats data-objects
```
Chargement des modifications de flux.

Important :

Lorsque le contenu du flux a été téléchargé, les nouvelles données doivent être chargées par le démons correspondants. Cela peut prendre plusieurs minutes jusqu’à plusieurs heures, en particulier pour le chargement initial des données. Sans données chargées, les analyses contiendront résultats incomplets et erronés.

Une fois les conteneurs communautaires Greenbone démarrés, les démons en cours d’exécution récupérera toujours le contenu du flux et chargera les données automatiquement.

Données de tests de vulnérabilité.

Si le journal (de ospd-openvas) contient la sortie suivante, OpenVAS Le scanner commence à charger les nouvelles données VT :

Message du journal de chargement ospd-openvas VT.
```
Loading VTs. Scans will be [requested|queued] until VTs are loaded. This may
take a few minutes, please wait...
```
Le chargement des données VT est terminé si le message du journal peut être trouvé:

ospd-openvas VTs chargement du message de journal terminé.
```
Finished loading VTs. The VT cache has been updated from version X to Y.
```
Une fois que le scanner a pris connaissance des données VT, les données seront demandées par gvmd. Ceci Le message de journal suivant s’affiche :

Message de chargement du journal de chargement des VT gvmd.

OSP service has different VT status (version X) from database (version (Y), Z VTs). Starting update ...

Lorsque gvmd a terminé le chargement de tous les VT, le message suivant s’affiche :

VT gvmd chargement du journal terminé.
```
Updating VTs in database ... done (X VTs).
```
Données SCAP.
```
gvmd commence à charger les données SCAP contenant les informations CPE et CVE lorsque le
```
message suivant se trouve dans les journaux :

Message du journal de chargement des données SCAP gvmd.
```
update_scap: Updating data from feed
```
Les données SCAP sont chargées et la synchronisation est terminée lorsque le journal (gvmd).

Contient le message suivant :

gvmd message du journal SCAP de chargement des données terminé.
```
update_scap_end: Updating SCAP info succeeded
```
Données CERT.

gvmd commence à charger les données CERT contenant les avis DFN-CERT et CERT-Bund lorsque le message suivant se trouve dans les journaux :

Message du journal de chargement des données gvmd CERT.
```
sync_cert: Updating data from feed
```
Les données CERT sont chargées et la synchronisation est terminée lorsque le journal (gvmd) 
Contient le message suivant :

gvmd CERT data finished loading log message.
```
sync_cert: Updating CERT info succeeded.
```
Données GVMD.

Le journal contient plusieurs messages lorsque les données gvmd sont chargées. Pour les listes de ports, Ces messages sont semblables à :

Message de journal chargé de la liste des ports gvmd.
```
Port list All IANA assigned TCP (33d0cd82-57c6-11e1-8ed1-406186ea4fc5) has been created by admin
```
Pour les formats de rapport :

Format de rapport gvmd Message de journal chargé.
```
Report format XML (a994b278-1f62-11e1-96ac-406186ea4fc5) has been created by admin
```
Indice.

Les configurations d’analyse ne peuvent être chargées que si les données VT sont disponibles dans gvmd et un flux Propriétaire de l’importation est défini.

Pour les configurations d’analyse :

Message du journal chargé de la configuration de l’analyse gvmd.
```
Scan config Full and fast (daba56c8-73ec-11df-a475-002264764cea) has been created by admin
```


