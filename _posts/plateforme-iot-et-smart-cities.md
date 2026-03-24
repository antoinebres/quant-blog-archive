# plateforme-iot-et-smart-cities
Wayback Machine URL: https://web.archive.org/web/20230129145026/https://www.quantmetry.com/blog/plateforme-iot-et-smart-cities/
Archive date: 2023-01-29

Uncategorized 

07/06/2016 

#  Plateforme IoT et smart cities 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fplateforme-iot-et-smart-cities%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Plateforme%20IoT%20et%20smart%20cities&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fplateforme-iot-et-smart-cities%2F "Twitter")

* * *

Temps de lecture : 7 minutes 

![Quantmetry.com : Plateforme IoT et smart cities](https://quantmetry.b-cdn.net/wp-content/uploads/2016/06/screen-shot-12-30-18-at-05-38-pm.jpg)

##  Smart cities et Internet des objets 

Les villes intelligentes (ou smart cities) sont un exemple typique de déploiement à grande échelle de l’Internet des objets (IoT, Internet of Things), dont quelques cas d’usage sont décrits dans un précédent article de ce blog (1). De la qualité de l’air et de l’eau au réseau de transports urbains en passant par l’éclairage public, on peut imaginer que presque tout dans la ville de demain sera relié, connecté et transformé en un flot continu de données qui seraient suivies et analysées par une plateforme avec peu ou pas du tout d’intervention humaine. 

Une myriade de projets à grande échelle a vu le jour partout dans le monde mais l’enjeu principal aujourd’hui est d’intégrer la technologie à une stratégie globale (2) : non seulement faut-il agréger les différentes initiatives locales pour mieux les coordonner et éviter les doublons, mais il est également nécessaire d’élargir les perspectives d’action. La ville de demain sera un acteur d’un réseau national et mondial de villes intelligentes connectées entre elles. 

Nous pouvons nous donner les moyens de ces ambitions car la technologie est là et sa progression est constante. Pour ne citer qu’un exemple, l’entreprise française Sigfox a déployé à San Francisco un réseau sans fil à bas débit destiné à faire communiquer des objets connectés. Son ambition est de couvrir 30 villes américaines avant fin 2016, du jamais vu. 

##  Les plateformes IoT : besoins, fonctionnalités et principes clefs 

###  Besoins 

Les besoins des smart cities – qui correspondent aux besoins de tout système IoT – sont multiples (3) et résumés ainsi : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.41-PM.jpg) Connectivité et Télécommunications  : réseau local en proximité géographique (coordonner les lampadaires d’une même rue, via bluetooth), ou réseau mondial via Internet (intégrer les données des réseaux sociaux pour gérer les flux de voyageurs en 4G). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.41-PM-001.jpg)

Analyse et Décision  : croisement d’informations au niveau local individuel (centrale d’alarme), ou à échelle globale (approche machine learning de maintenance prédictive des trains). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.41-PM-002.jpg)

Besoin temporel  : temps réel à chaud (alarme d’incident), ou stockage à froid de données massives (comportement des usagers). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.41-PM-003.jpg)

Action  : vers l’objet ciblé capable d’agir (boîte aux lettres connectée), ou recommandation globale (état du réseau de métro). 

Les plateformes IoT se posent en acteur majeur capable de répondre à la diversité de ces besoins récurrents du monde de l’Internet des objets. Selon Gartner (4), une plateforme IoT est une suite logicielle (SaaS, Software As A Service) ou un service cloud (PaaS, Platform As A Service) qui facilite les opérations impliquant des acteurs IoT (capteurs, appareils, réseaux), le cloud et les ressources de l’entreprise. La plateforme recueille les flux d’évènements, permet de faire des analyses spécialisées et de développer des applications, et implique des systèmes IT en back-end. La plateforme IoT peut-être développée sur l’infrastructure existante (On Premise) ou dans un cloud public ou privé (au niveau du service informatique de l’entreprise). 

###  Fonctionnalités minimales requises 

L’identification de ces besoins nous permet de lister les fonctionnalités qui devront être intégrées dans l’architecture de la plateforme IoT, auxquelles on peut associer une « température » de traitement des données (chaud, froid, les deux) : 

  * Réception des données : gestion de multiples sources de données entrantes (en batch loads ou en flux haute fréquence). Doit être extensif et insensible aux défaillances. 

  * Stockage des données : stockage haute capacité et bas coût des flux de données entrants. A long terme, le système devra être capable de stocker durablement de grandes quantités de données, sans se soucier des coûts. 

  * Analyse de données « offline » : analyse potentiellement complexe et profonde (par exemple machine learning) d’une large quantité de données, qui devront être traitées à froid. 

  * Analyse de données en temps réel : traitement en temps réel des données entrantes, avec mise à disposition rapide des résultats. 

  * Visualisation des données : sur toutes les sources de sorties possible (stockage des données, offline ou temps réel). 

  * Traitement des tâches : traiter l’information de sortie des composants temps-réel à travers une interface de programmation (API, Application Programming Interface) web ou mobile, pour agir et prendre des décision de façon automatique ou semi-automatique. 

  * Action : vers les objets connectés. 




![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.41-PM-004.jpg)

###  Principes clefs 

Le pari des plateformes IoT est de constituer un socle sur lequel repose un système qui peut être complété et paramétré pour s’adapter au mieux aux cas d’usage. Cet enjeu est central dans la démarche smart cities, où les cas d’usage sont particulièrement variés, en constante évolution et dans le souci d’une stratégie globale comme cela a été mentionné au début de ce billet. Le but est de pouvoir développer rapidement l’offre métier IoT sans être limité par la technologie et les problèmes techniques. 

On peut encore ajouter aux fonctionnalités minimales, des principes clefs à suivre : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.41-PM-005.jpg)

Composants découplés  : plus les composants/modules sont indépendants, plus il sera facile de les maintenir, les mettre à jour ou même de les changer (s’il faut s’adapter à l’évolution des cas d’usage). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.42-PM.jpg)

Communication asynchrone  : les différents points d’entrée et de sortie doivent être capable d’enregistrer/lire les données à n’importe quelle moment sans être limités par la technologie. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.42-PM-001.jpg) Insensibilité aux défaillances  : nécessaire pour garantir une haute disponibilité et gérer une potentielle perte de donnée ou de matériel informatique. 

Architecture Lambda modifiée 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.42-PM-002.jpg)

###  Description 

Nous allons maintenant nous concentrer sur l’architecture des plateformes IoT. En particulier, nous proposons une architecture basée sur l’architecture Lambda qui a l’avantage de couvrir les besoins, fonctionnalités minimales et principes clefs mentionnés ci-dessus. Cette architecture reçoit les évènements, les archive, effectue des analyses offline et en temps réel et agrège les résultats de ces calculs en une information cohérente, tout cela à l’échelle de millions d’évènements par seconde. 

Le schéma ci-dessus détaille l’architecture en reprenant les fonctionnalités et leur « température » de traitement évoquées plus haut (chaud, froid, les deux). 

L’architecture lambda est composée de 3 couches principales (batch, serving et speed layer) auxquelles nous ajoutons une couche de décision, la decision layer. 

###  Utilisation 

  1. Les données reçues en entrée sont répartie à la fois dans la couche batch et la couche speed pour être traitées. 

  2. La couche batch pré-traite les résultats via un système de traitement distribué qui peut gérer de très grandes quantités de données. Cette couche gère aussi le data set principal (stockage append-only mis à jour régulièrement de données non traitées). Une approche pourrait être une combinaison d’une base distribuée d’Apache et de Spark. C’est ici que sont effectuées les analyses type machine-learning. 

  3. La couche speed permet d’analyser les données pour les besoins du temps réel. C’est une alternative à la couche batch, dont la latence de mise à jour est trop importante. Si la couche speed permet un traitement quasi-immédiat, elle ne gère que les données récentes et n’est pas aussi complète que la couche batch. 

  4. La couche serving agrège les informations issues des couches batch et speed pour qu’elles puissent être sollicitées en faible latence et de façon ad-hoc par la couche de décision. 

  5. Nous proposons d’ajouter une couche de décision qui permet à la fois de visualiser directement les données issues des couches serving et speed et offre une interaction à travers une interface web ou mobile. 

  6. Selon la prise de décision, il est possible d’agir directement sur les objets connectés de façon ciblée ou globale. 




Les principes clefs mentionnés ci-dessus sont parfaitement respectés : les couches batch et speed sont complètement indépendantes et asynchrones. Ceci a l’avantage de garantir l’intégrité et la pérennité des données. Si une défaillance a lieu dans la couche speed, la couche batch continue de recueillir les données sans interruption, n’affectant que le traitement du temps réel pendant la durée de la défaillance. Si la couche batch est affectée, la speed layer prendra le relais et sera davantage sollicitée le temps de régler le problème. 

###  Exemple sur un cas d’usage 
