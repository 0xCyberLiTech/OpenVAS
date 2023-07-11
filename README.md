![OpenVAS](./images/OpenVAS.png)

# OnpenVAS

## Sommaire :

| Cat | Etapes |
|------|------| 
| - A. | [Qu'es qu'un scanner de vulnérabilités.](#balise_01) |
| - B. | [Principes de fonctionnement.](#balise_02) |
| - C. | [Cibles.](#balise_03) |
| - D. | [Méthodes de détection.](#balise_04) |
| - E. | [Restitution des résultats.](#balise_05) |

<a name="balise_01"></a>
# - A. Qu'es qu'un scanner de vulnérabilités.

En sécurité informatique, un scanner de vulnérabilités est un programme conçu pour identifier des vulnérabilités dans une application, un système d'exploitation ou un réseau.

## Utilisation.

Les scanners de vulnérabilités peuvent être utilisés dans des objectifs licites ou illicites :

- Objectifs licites : les experts en sécurité informatique ou les entreprises utilisent les scanners de vulnérabilités pour trouver les failles de sécurité des systèmes informatiques et des systèmes de communications de leurs entreprises dans le but de les corriger avant que les pirates informatiques ne les exploitent ;

- Objectifs illicites : les pirates informatiques utilisent les mêmes outils pour trouver les failles dans les systèmes des entreprises pour les exploiter à leur avantage.

Cet outil peut être une brique intégrée d'une solution de sécurité plus large : un SIEM ou un SOC par exemple.

<a name="balise_02"></a>
# - B. Principes de fonctionnement :

Les scanners de vulnérabilités se présentent sous plusieurs formes : 
logiciel à installer sur son système, machine virtuelle pré-configurée (virtual appliance) ou encore en SaaS dans le Cloud.

Un scanner de vulnérabilités se "lance" sur une ou plusieurs cibles, dans un réseau interne ou sur Internet. Ces cibles (URL, adresse IP ou sous-réseau) sont renseignées par l'utilisateur lorsqu'il désire mener son scan. La plupart des outils suivent le schéma de scan suivant :

- Cartographie des cibles actives (attente d'une réponse ICMP, ARP, TCP, etc. pour déterminer si la cible répondra au scanner)
- Détection des ports TCP et UDP accessibles sur la cible (scan de ports)
- Détection des services actifs (SSH, HTTP, etc.) sur chacun de ces ports et de leurs versions (phase de footprinting)
Éventuellement : utilisation d'un compte fourni pour se connecter sur la machine et lister les programmes non visibles depuis le réseau (navigateur, liseuse, suite bureautique, etc.).
- Éventuellement : reconnaissance des applications Web accessibles et construction de l'arborescence de chaque site Web (phase dite de crawling).
- Sélection des modules de sécurité à lancer sur la cible selon les services précédemment reconnus.
- Lancement des modules de sécurité.
- Génération du rapport de sécurité.

Un scanner de vulnérabilités est donc un outil complexe qui peut faire appel à de nombreux programmes spécifiques pour chacune des tâches pré-citées.

<a name="balise_03"></a>
# - C. Cibles.

Un scanner de vulnérabilités est théoriquement capable de tester tout élément joignable par une adresse IP :

- Ordinateur
- Serveur
- Routeur, commutateur, pare-feu
- Smartphone
- Objet connecté
- Site Web
- Automate, robot, machine
- Caméra IP
- IPBX, poste téléphonique sur IP
- etc.

Le fait de pouvoir atteindre un équipement n'implique cependant pas forcément que son niveau de sécurité puisse être audité correctement. Pour cela, le scanner doit embarquer les modules de sécurité idoines dans son catalogue. Par exemple, si une cible ne possède que le port UDP 161 ouvert avec le service SNMP, un scanner pourra reconnaître que cette cible est active mais ne pourra juger son niveau de sécurité qu'en incorporant des modules d'attaque contre SNMP.

<a name="balise_04"></a>
# - D. Méthodes de détection.

Pour établir la présence d'une vulnérabilité, un scanner dispose de plusieurs méthodes.

- Footprinting de version.

  Cette première méthode est la plus répandue. L'outil tente de déterminer la nature et la version d'un service, par exemple: apache httpd 2.4.2.

  Pour cela, il peut se fier aux bannières présentées par les différents services, rechercher des motifs caractéristiques d'une version dans les réponses du serveur (notamment dans les en-têtes), etc.

  Une fois que la version est déterminée, l'outil utilise une base qui associe à chaque version d'un outil, la liste des vulnérabilités publiquement connues sur celui-ci.

  De telles bases sont publiquement accessibles et enrichies par l'éditeur de la solution concernée, par un État ou encore par une communauté.

  La base la plus connue est celle des CVE publiée par le MITRE,(cette base est passé au format JSON depuis 2022). Une alternative indépendante est l'Open Source Vulnerability Database (OSVDB)1. Ces bases tentent donc de 
  recenser toutes les vulnérabilités découvertes et de les associer aux produits vulnérables. Généralement seuls les produits les plus connus font l'objet d'une entrée dans ces deux bases. Pour rappel, les vulnérabilités 
  non connues et non publiées sont dites zero day. Certains éditeurs maintiennent aussi leur propre base : Debian Security Advisory (DSA) pour Debian, CSA pour Cisco, RHSA pour RedHat, idem pour Wordpress, Gentoo, Drupal, 
  etc.

  De manière symétrique, la dénomination des programmes et de leurs versions a été normalisée avec les CPE2 (également maintenu par le MITRE) afin de pouvoir faire des associations en base de données plus simples.

  Cette méthode est cependant notoirement sujette aux faux positifs et aux faux négatifs. De nombreux programmes ne laissent pas transparaître leur version (désactivation des bannières, etc.), le scanner ne pourra donc 
  pas en déduire leurs vulnérabilités (faux négatifs). Inversement, des programmes peuvent donner leur version mais avoir subi un rétroportage des correctifs et donc, ne pas souffrir des vulnérabilités officiellement 
  rattachées à cette version (faux positifs). Ce dernier cas se produit très fréquemment sur les versions paquetagées par les distributions Linux comme Debian ou Ubuntu.

  En outre, les informations fournies par la base CVE et par la normalisation CPE ne sont pas toujours suffisantes pour identifier la présence d'une vulnérabilité.
  Par exemple, dans le cas d'une vulnérabilité comme la CVE-2017-01433 (liée à l'attaque WannaCry), on constate que toute machine Microsoft Windows 8.1 utilisant SMB v1 est vulnérable d'après les informations fournies par 
  le NVD4 et la terminologie CPE. Or, une telle machine disposant des correctifs de sécurité appropriés (KB40122135) sera bel et bien protégée de cette vulnérabilité, et représentera ainsi un faux positif.
  Il faut donc affiner une telle analyse à partir des alertes de sécurité en provenance des éditeurs, qui indiquent de manière plus précise les conditions de vulnérabilité.

- Exploitation active.

  Lorsque des vulnérabilités sont publiquement dévoilées, elles sont parfois accompagnées d'un exploit (terme anglosaxon prononcé "exploite" ou "exploïte") qui est un programme permettant de les exploiter automatiquement.

  Un scanner de vulnérabilités peut donc recourir à cet exploit pour vérifier la présence d'une vulnérabilité. Dans ce cas-là, le scanner n'a pas besoin de se fier à la version du programme qu'il audite, il se fie à la 
  réussite ou à l'échec de l'exploit.

  Plusieurs bases d'exploits existent, telles que exploit-db6 (maintenue par la communauté à l'origine de Kali Linux, distribution dédiée au test d'intrusion) ou encore celle de l'outil Metasploit (publié par Rapid7 qui 
  propose notamment le scanner de vulnérabilités Nexpose).

  Cette méthode est donc très efficace, mais souffre de deux inconvénients. Premièrement, il existe peu de vulnérabilités pour lesquelles un exploit est disponible : pour donner un ordre de grandeur, il existe environ 100 
  000 CVE enregistrées7 et moins de 4 000 exploits dans Metasploit[réf. nécessaire]. Deuxièmement, certains exploits peuvent avoir des effets de bord significatifs et perturber le fonctionnement de la machine auditée 
  (pouvant aller jusqu'à un plantage). Ils doivent donc être utilisés avec parcimonie et être rigoureusement qualifiés.

- Scan de configuration.

  Certaines vulnérabilités ne proviennent pas d'un défaut dans le code source du programme mais simplement d'un mauvais réglage de celui-ci dans un certain contexte. Les scanners de vulnérabilités peuvent donc détecter 
  certaines vulnérabilités en analysant la configuration distante du service audité (ce qui est un service généralement prévu par celui-ci).

  Ceci concerne par exemple les options de sécurité activées sur les cookies, les cipher suite dans la configuration SSL, les transferts de zone pour un serveur DNS, les mots de passe par défaut inchangés, les services 
  par défaut laissés activés, etc.

  Cette méthode est généralement sans risque (excepté tester les mots de passe par défaut qui peut bloquer des comptes après trop d'échecs) et la base des bonnes pratiques est relativement simple à maintenir (par rapport 
  à celle des nouvelles vulnérabilités où l'on compte en moyenne 13 nouvelles CVE par jour). Cependant, il y a des risques de faux positifs puisque le scanner de vulnérabilités n'est pas forcément à même de connaître le 
  contexte et donc de juger si la configuration en question est adaptée ou non (exemple : un transfert de zone DNS est problématique vers Internet mais relativement sans danger dans un réseau interne).

- Scans authentifiés.

  Bien que la plupart des scanners soient "sans agent", donc ne nécessitant aucune installation sur la machine cible, ils fournissent souvent la possibilité d'utiliser un compte renseigné par l'utilisateur pour mener des 
  tests authentifiés.

  Lors d'un scan authentifié, le scanner utilise des modules appelés "local security check" qui consistent à consulter la base des programmes installés et leur version (en interrogeant le registre Windows ou pour Linux 
  aptitude, pacman, emerge, etc.). En se basant sur les alertes de sécurité des éditeurs (DSA, CSA, RHSA, etc.), le scanner pourra constater la présence ou l'absence de programmes ayant des vulnérabilités connues.

  L'intérêt principal de cette méthode est de ne pas se limiter à la surface visible de la machine depuis le réseau. En effet, une machine ayant un navigateur obsolète pourrait facilement être compromise par un logiciel 
  malveillant, mais le navigateur étant un programme client et non pas serveur, il n'émet pas sur un port (puisqu'il consomme un service) comme le ferait par exemple un serveur SSH (qui fournit un service). Donc, en 
  l'absence de scan authentifié, le risque peut demeurer totalement inconnu de l'utilisateur du scanner de vulnérabilités.

  Avec cette méthode, le scanner de vulnérabilités amorce une démarche de Patch management : il permet la détection des anomalies, même s'il ne les corrige pas lui-même.

  Cette méthode est fiable (peu de faux positifs/négatifs), ne risque pas d'engendrer d'instabilités sur le système audité et est rapide[réf. nécessaire]. Elle peut se substituer aux méthodes de footprinting et 
  d'exploitation active mais pas à celle du scan de configuration qui demeure complémentaire. En revanche, elle nécessite de fournir des comptes valides pour chaque machine auditée.

- Spécificité des applications Web :

  Les méthodes pré-citées ne sont pas suffisantes pour attester de la sécurité d'un site Web. Elles permettent de savoir si le serveur Web sous-jacent (exemples : Apache, nginx, IIS) est exempt de vulnérabilités mais ne 
  peuvent pas connaître la sécurité de l'application Web (ou du service Web) propulsée par ce serveur Web.

  L'application Web peut souffrir de défauts de conception dans leur code source qui entraînent l'apparition de failles applicatives. Comme chaque site Web est unique, le scanner ne peut pas se fier à une quelconque base 
  de connaissances. Néanmoins, les failles applicatives sont un sujet exhaustivement traité par l'OWASP, qui est une communauté œuvrant pour la sécurité des applications Web. L'OWASP recense toutes les familles de 
  vulnérabilités Web et les attaques qui y sont associées. Certains scanners implémentent donc des modules de détection de ces familles de failles. D'autres scanners se spécialisent même exclusivement dans cette tâche 
  (Burp suite, Zap, Wapiti...).

  La recherche automatisée de failles applicatives web est un sujet complexe : ici, le scanner ne peut pas utiliser un exploit créé spécifiquement pour fonctionner sur un cas particulier bien connu. Le module d'attaque 
  doit pouvoir s'adapter à tous les sites Web quelle que soit leur architecture. Pour cela, les tests Web incorporent une phase appelée "crawling" qui consiste à cartographier le site Web et tous ses points d'entrées de 
  données (en suivant tous les liens ou même en tentant de deviner la présence de certaines pages : /admin, /phpmyadmin, etc.). Les points d'entrées sont ensuite soumis à des motifs d'attaque adaptatifs spécifiques aux 
  familles d'attaques: injections SQL, XSS, LFI, RFI, traversée d'arborescence, etc.

  Les scanners permettent généralement aussi de fournir un compte ou un cookie de session pour accéder aux parties réservées aux utilisateur authentifiés.

  Les scanners Web sont cependant limités puisque des opérations complexes, comme remplir un formulaire d'assurance en ligne, ne peuvent être menées de bout en bout car elles peuvent nécessiter de renseigner des 
  informations contextuelles et cohérentes que le scanner ne peut pas deviner.

  En pratique, les scanners Web peuvent néanmoins remonter des informations pertinentes pour des technologies très répandues, telles que les CMS. Des outils spécialisés pour chaque famille de CMS peuvent alors être 
  utilisés, comme WPScan [archive] pour l'analyse de sites WordPress.

<a name="balise_05"></a>
# - E. Restitution des résultats.

La visualisation et la restitution des résultats se fait traditionnellement via deux paradigmes[réf. nécessaire]. Premièrement, une vue par vulnérabilité permettant de lister toutes les vulnérabilités identifiées dans le scan et de donner pour chacune d'elles la liste des machines affectées. Deuxièmement, une vue par machine listant les cibles de l'audit associées à la liste de leur vulnérabilités respectives.

Traditionnellement, en sécurité informatique, les vulnérabilités sont restituées par ordre de criticité suivant une échelle à 4 niveaux :

- Critiques : les vulnérabilités permettant généralement une prise de contrôle ou une exécution de commande à distance dont l'exploitation est relativement simple.
- Majeures : les vulnérabilités permettant une prise de contrôle ou une exécution de commande à distance dont l'exploitation demeure complexe.
- Moyennes : les vulnérabilités ayant des impacts limités ou dont l'exploitation nécessite des conditions initiales non triviales.
- Mineures : les vulnérabilités ayant des impacts faibles ou nuls à moins d'être combinées à d'autres vulnérabilités plus importantes.

L'état de l'art associe à chaque vulnérabilité un score entre 0 et 10 appelé CVSS (pour Common Vulnerability Scoring System) qui dépend des caractéristiques de cette vulnérabilité. La version 3 du CVSS prend en compte, au minimum, les éléments suivants :

- Vecteur d'attaque : est-ce que l'attaquant peut venir de n'importe où ou bien doit-il avoir une position de départ privilégiée ?
- Complexité : exploiter la vulnérabilité est-il trivial (par exemple si un exploit existe) ou bien hautement technique ?
- Privilèges requis : l'attaquant doit-l disposer d'accès préalables (un compte utilisateur par exemple) pour pouvoir mener son action ?
- Interaction nécessaire avec un utilisateur : l'attaquant doit-il amener la victime à effectuer une action pour que son attaque réussisse (comme l'inciter à cliquer sur un lien) ?
- Périmètre : est-ce qu'une exploitation permet à l'attaquant d'avoir accès à de nouvelles cibles ?
- Impacts : une exploitation réussie entraîne-t-elle des pertes de confidentialité/disponibilité/intégrité ?

Le score CVSS est régulièrement utilisé par les scanners de vulnérabilités pour pondérer les risques associés à une cible.

Les scanners doivent donner à l'utilisateur tous les éléments pertinents pour sa compréhension de la vulnérabilité. Traditionnellement, une description de vulnérabilité comporte les éléments suivants :

- Le nom de la vulnérabilité.
- Sa criticité.
- La cible touchée.
- Une brève description de sa nature.
- Une référence à une base de connaissance type CVE, DSA...
- Une mention de la simplicité de l'exploitation.
- Une description de l'impact en cas d'exploitation réussie.
- Une ou plusieurs préconisations pour la résoudre.

Parfois, d'autres éléments y sont ajoutés :

- Le niveau de confiance à accorder à la vulnérabilité : quantification du risque qu'il s'agisse ou non d'un faux positif.
- S'il existe ou non un exploit automatique.
- Un extrait des données ayant permis au module de sécurité de conclure à la présence de cette faille.
- La famille de vulnérabilité (authentification, mise à jour, etc.).
- Des liens pour en savoir plus (notamment pour des explications plus détaillées du fonctionnement technique de la vulnérabilité).

Source : https://fr.wikipedia.org/wiki/Scanner_de_vuln%C3%A9rabilit%C3%A9
