---
layout: post
title: la-logistique-et-le-big-data-ils-sont-faits-pour-se-rencontrer
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129154123/https://www.quantmetry.com/blog/la-logistique-et-le-big-data-ils-sont-faits-pour-se-rencontrer/
---
Uncategorized 

15/09/2017 

#  La logistique et le big data : ils sont faits pour se rencontrer 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fla-logistique-et-le-big-data-ils-sont-faits-pour-se-rencontrer%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=La%20logistique%20et%20le%20big%20data%20%3A%20ils%20sont%20faits%20pour%20se%20rencontrer&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fla-logistique-et-le-big-data-ils-sont-faits-pour-se-rencontrer%2F "Twitter")

* * *

Temps de lecture : 8 minutes 

![Quantmetry.com : La logistique et le big data : ils sont faits pour se rencontrer](https://quantmetry.b-cdn.net/wp-content/uploads/2017/09/supplychain.jpg)

Amazon, souvent considéré comme le meilleur logisticien du monde, a fait le choix d’investir considérablement dans ses systèmes d’information, notamment dans l’exploitation de la data pour optimiser sa chaîne logistique. Même si beaucoup d’entreprises de ce secteur ont lancé de grands chantiers autour de la data, ces chantiers sont très orientés sur l’augmentation de leurs revenus et encore trop peu sur la réduction de leurs coûts, notamment au niveau de la logistique, qui offre pourtant d’importants leviers d’optimisation. 

**Les sources de données de la chaîne logistique sont très riches et diverses** : WMS (1), TMS (2), automates, objets connectés, RFID (3), données de localisation, trafic routier, données fournisseurs… Même si l’optimisation de la chaîne logistique est une réalité concrète pour de nombreux opérateurs, les opportunités créées par l’utilisation et le croisement de données hétérogènes restent à ce jour peu exploitées. 

En réalité, de nombreux investissements au sein des directions logistiques ont permis d’optimiser la chaîne d’approvisionnement : optimisation des niveaux de stockage, des emplacements de stockage, des tournées de préparation, des livraisons… mais en ne considérant que les aspects statiques. 

Or, la puissance de calcul permet désormais de traiter massivement des données en temps réel provenant de sources multiples. Cela ouvre des perspectives immenses à la logistique : 

  * Exploiter les données internes et externes permettant de mieux prévoir les volumes de charge ou les ventes à venir, notamment pour dimensionner les équipes terrain ; 

  * Mieux anticiper les risques (fournisseurs, équipements, ruptures et écarts de stock, …) pour assurer une meilleure réactivité des responsables logistiques ; 

  * Optimiser et rendre dynamique la planification des tournées en fonction des perturbations (fermetures de routes, déviations, synchronisation des feux, …) ; 

  * Intégrer les données clients afin de garantir les engagements sur la qualité de service mais également être en capacité de proposer de nouveaux services personnalisés aux clients ; 

  * Maximiser la réception des marchandises en intégrant les spécificités liées à la typologie de produit (produits frais, inflammable, poids, taille…) 




Il s’agit d’une vraie évolution dans les méthodes de travail du personnel de terrain, notamment en intégrant le temps réel dans l’activité de l’entrepôt. Cette approche permettrait d’adapter l’activité de l’entrepôt aux évènements qui surviennent au cours de la journée et de permettre aux équipes de répondre efficacement aux situations non prévues. Tous ces chantiers nécessitent évidemment de construire, en parallèle, une stratégie de conduite du changement au sein des entrepôts. Sans adhésion des équipes, aucun bénéfice à attendre. 

##  Un retour d’expérience enrichissant 

Quantmetry a collaboré étroitement avec les équipes Big Data d’un acteur français leader de la prestation logistique. L’objectif était la mise en place d’un outil d’optimisation du dimensionnement des équipes au sein des entrepôts afin d’éviter à la fois le sureffectif (occasionnant un surcoût pour l’entreprise) et le sous-effectif (pouvant occasionner des pénalités de retard ou des coûts importants en heures supplémentaires). Ainsi, notre approche conjointe s’est construite autour de deux axes : 

  1. Le calcul et l’analyse des facteurs impactant la productivité dans les entrepôts afin de la segmenter en typologies de flux (ex : manipuler des colis lourds et volumineux implique une productivité plus faible que des colis légers et petits) 

  2. La prédiction de la charge journalière à une semaine (permettant aux opérateurs un levier d’action pour embaucher dans les temps) 




Le rapport des deux permettant ainsi de prévoir à l’avance le nombre d’ETP (équivalent temps plein) nécessaire le jour J. 

Les contraintes rencontrées n’étant pas à sous-estimer, nous décidons de lister certains points d’attention à garder à l’esprit pour ce type de projet. Nous présentons également la méthodologie choisie pour répondre à la problématique posée. 

##  La non-homogénéité des données 

De nombreux prestataires logistiques doivent adapter leur solution et leurs méthodes de fonctionnement en fonction de leurs clients. Ainsi, les différentes activités au sein des entrepôts vont parfois varier du tout au tout, et les données ne seront pas toujours disponibles à la même granularité. 

Dans notre cas, par exemple, nous avons travaillé sur deux types d’entrepôts où la réception s’effectuait selon deux modes : l’un effectuait de la réception camion, l’autre de la réception container. Les processus de déchargement colis étaient donc nettement différents. Dans un cas le déchargement était identifiable grâce aux données générées par les flashs (codes barre) de colis, dans l’autre cas la réception s’effectuait en vrac sans que des flashs de colis ne soient systématiquement effectués ; nous n’avions donc pas la même remontée d’information concernant cette activité. 

De la même façon, au moment de la mise en stock, les colis pouvaient être flashés par un même identifiant-opérateur alors qu’il s’agissait en réalité d’un passage de bipeur entre deux opérateurs métier différent. Dans ces conditions, il n’est pas simple de calculer des productivités propres à chaque opérateur et de tracer de manière exacte le nombre de ressources actives dans l’entrepôt. Une vérification de cohérence entre nos estimations et la connaissance métier nous a tout de même permis d’être confiant pour la suite. 

##  La qualité des données 

Une des contraintes assez récurrente en data science est liée à la qualité des données et la méthode de stockage des données. En effet, la présence de fichiers renseignés manuellement, modifiés dans le temps et sans historisation est à l’origine d’un point d’attention non négligeable. 

Ainsi, lorsqu’il a fallu qualifier la capacité des modèles à prévoir une charge journalière pour en déduire la qualité nos performances, la comparaison avec les prévisions des entrepôts ne fut pas si évidente. Le métier se basait sur des prévisions qu’il mettait constamment à jour avec un effacement des anciennes prévisions, il était donc possible que ces prévisions puissent dater de la veille, de 3 jours ou encore d’une semaine sans que nous disposions de cette information. À l’inverse, nos prévisions étaient constantes et prédisaient toujours une semaine à l’avance. Dans un tel contexte, il est difficile de comparer ces deux types de prévisions et de quantifier le nombre de fois où le modèle est le plus performant. Par conséquent la mesure du gain d’une approche par apprentissage est moins évidente dans ces cas de figure. Néanmoins, sans tenir compte de ce cas de figure, nos résultats ont témoigné de bonnes performances mais une phase de test en conditions réelles est nécessaire afin de valider l’approche, avant toute décision d’industrialisation. 

Ces deux principaux éléments (non-homogénéité et qualité de la donnée) nous ont amené à raisonner de façon plus spécifique pour chaque entrepôt plutôt que globale. Notre choix s’est donc porté sur les activités communes aux entrepôts et centrées autour des mêmes données. 

##  Du Big Data au Small Data 

Qualité inhérente au secteur, la volumétrie des données était au rendez-vous. Une vaste quantité de données est remontée et stockée dans les différents WMS ; la valeur ajoutée à utiliser les approches innovantes, type big data, à l’ensemble de l’écosystème de la supply chain est donc indéniable. 

La dimension big data prend tout son sens pour les phases qui précèdent la modélisation. Les extractions, les nettoyages et les différents traitements sont parfois colossales et coûteux en temps. Dans notre cas, l’ensemble des données analysées rassemblait un historique de quatre ans de chaque flash de colis ou de produits passés par l’entrepôt. 

La dimension small data apparaît à l’étape de modélisation. L’objectif était de prédire chaque jour une charge pour les jours suivants. Cette dernière agrégation a considérablement réduit le jeu de donnée et embarque toute la problématique inhérente à la notion de small data. En effet, les algorithmes de machine learning sont basés sur un principe d’apprentissage par les données : plus le jeu de donnée sera grand plus l’algorithme aura la capacité à apprendre et à reproduire les saisonnalités et autres effets du passé, notamment en période de pic de charge pour la prévision des colis. 

Dans notre cas, avec un historique de 4 ans (contexte big data), soit environ 1000 jours travaillés (contexte small data), l’algorithme avait donc peu de marge de manœuvre pour apprendre et s’auto-performer . 

##  Modélisation 

Dans de tels cas de figure, certaines méthodes consistent donc à procéder de manière plus traditionnelle et à considérer des approches de modélisation par série temporelle. Cependant, cette approche consiste à modéliser la variable cible en fonction du temps et sans tenir compte des autres informations disponibles qu’un modèle de machine learning pourrait mieux capter. 

Notre méthode consiste alors à combiner des approches classiques de séries temporelles et des concepts d’algorithmes plus avancés en machine learning, comme les méthodes ensemblistes. 

Les prédictions sont effectuées en deux étapes : 

  1. Prédiction de la charge journalière, à l’aide d’un algorithme développé par Facebook : Prophet (algorithme de série temporelle revisité, basé sur des méthodes ARIMA). En sortie nous obtenons un régresseur avec de mauvaises performances prédictives, si on l’utilise seul, mais qui nous permet de capter plus finement les saisonnalités et tendances passées. 

  2. Une fois ces effets captés, nous prédisons le bruit restant (c’est à dire la différence entre les tendances prévues et le réel) à l’aide de forêts aléatoires – algorithme basé sur un principe d’agrégation de plusieurs arbres de décision. 

L’intérêt de combiner ces deux algorithmes très différents est de pallier aux faiblesses de l’un avec les forces de l’autre. 




##  Conclusion 

Notre approche et nos résultats ont suscité l’intérêt d’un déploiement de la solution en production. Si la phase de test s’avère concluante, on pourra envisager d’étendre le périmètre à l’ensemble des entrepôts (cf. notre livre blanc : Y a-t-il une vie après les POCs ?). 

En conclusion, l’une des problématiques clés à laquelle les prestataires logistiques doivent répondre est de se focaliser sur une rationalisation et harmonisation des WMS existants. 

L’analyse de données est déjà employée par la plupart des organisations au niveau de leur supply chain. Pour autant, celle-ci est pour l’heure focalisée sur le reporting et la planification et est peu imbriquée dans les opérations, tant au niveau des processus que des systèmes. Dans de nombreux cas, les prévisions des ressources est gérée en partie avec des tableaux Excel intégrant des données éparses. Et l’essentiel des investissements IT est consacré aux WMS et autres applications dédiées à la logistique interne, gérée de façon très efficace. 

C’est pourquoi Quantmetry a décidé de capitaliser sur ses connaissances dans d’autres domaines d’activités et de les adresser à ce secteur dont l’intérêt et l’appétence autour de solutions innovantes ne cesse de croître. Nous comptons aujourd’hui de nombreuses références dans de ce secteur et cet article est un exemple très concret de réponse apportée à une problématique de réduction de coût au sein des entrepôts. 

Notes : 

(1) WMS : Warehouse management system, outil de gestion des opérations (réceptions, stockage, préparation, expédition, inventaires) d’un entrepôt de stockage. 

(2) – TMS : Transport management system, outil de gestion des opérations de transport 

(3) – RFID : Radio frequency identification, technologie permettant d’identifier et de suivre un produit via une étiquette émettant des ondes radio 
