# smart-cities-et-data-science-partie-2
Wayback Machine URL: https://web.archive.org/web/20230129145743/https://www.quantmetry.com/blog/smart-cities-et-data-science-partie-2/
Archive date: 2023-01-29

Uncategorized 

29/04/2016 

#  Smart Cities et data science – Partie 2 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fsmart-cities-et-data-science-partie-2%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Smart%20Cities%20et%20data%20science%20%E2%80%93%20Partie%202&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fsmart-cities-et-data-science-partie-2%2F "Twitter")

* * *

Temps de lecture : 18 minutes 

![Quantmetry.com : Smart Cities et data science – Partie 2](https://quantmetry.b-cdn.net/wp-content/uploads/2016/04/screen-shot-12-30-18-at-05-52-pm.jpg)

Chez Quantmetry, nous avons décidé d’y voir plus clair sur le sujet Smart Cities, très à la mode depuis quelques années déjà. En particulier, nous avons décidé de considérer une dizaine de cas d’usage spécifiques, de les détailler et d’en évaluer l’intérêt pour une entreprise comme la nôtre, spécialiste dans le domaine de la Data Science. Dans la première partie de ce travail, sortie il y a quelques semaines sur notre blog, des cas d’utilisation tels que la réalisation d’un système d’éclairage adaptatif, d’une offre de stationnement dynamique ou encore d’une plateforme de marketing digital touristique ont été analysés. 

##  6\. SMART GRID ENERGIE 

L’introduction de capteurs dans le réseau électrique et chez les compteurs des usagers permet une compréhension plus fine des usages. Cette connaissance autorise la mise en œuvre de deux modes d’actions. En premier lieu, les smart grids étant un type particulier de réseau, nous pouvons mettre en œuvre toutes les améliorations propres aux systèmes de réseaux distribués vus précédemment (maintenance au plus juste, équilibrage dynamique …). D’autre part, des actions plus spécifiques au secteur de l’énergie peuvent être entreprises comme la proposition d’une tarification dynamique pour encourager les comportements vertueux (par exemple, les usages hors pics). Enfin, le déploiement de smart grids peut faciliter la création de communautés autosuffisantes et l’avènement du producteur consommateur (un client particulier peut être à la fois producteur d’énergie et consommateur grâce à des unités locales de production d’énergie). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.52-PM-001.jpg)

En termes de Data Science, nous trouvons deux sujets à traiter. Comme toujours dans la gestion des réseaux, d’importantes améliorations peuvent être produites du point de vue de la maintenance prédictive et de la priorisation des interventions, de manière à fournir aux équipes techniques une information plus détaillée sur les situations qui sont les plus risquées pour l’ensemble du réseau, et qui seront donc à traiter en priorité. Sur le moyen terme, on pourra utiliser les aperçus en tant qu’aide à la prise de décision : les modifications du réseau pourront en fait être réalisées de manière à adresser les criticités structurelles ou récurrentes détectées par les algorithmes. 

Le bénéfice attendu le plus immédiat sera l’amélioration des interventions de maintenance sur le réseau. La tarification dynamique encourageant les usages hors pics pourra donner lieu à une meilleure et plus homogène exploitation des ressources. Les données récoltées, enfin, vont aider les décisions sur les modifications structurelles à apporter au réseau pour résoudre les problèmes détectés, en simulant par exemple les effets que ces interventions auront sur le système. 

###  RÉFÉRENCES D’EXPÉRIMENTATIONS 

Des expérimentations concernant les réseaux d’auto-production et de consommation locale d’énergie ont déjà été menées, comme par exemple le [ projet RennesGrid. ](http://metropole.rennes.fr/actualites/urbanisme-deplacements-environnement/environnement/rennes-metropole-prime-pour-son-smart-grid/) Remarquons que sur ce sujet l’approche pragmatique qui met le réseau de producteurs-consommateurs en lien avec le reste du réseau est à considérer nécessaire, au moins pour la phase initiale de chaque projet, quand le risque serait de ne pas avoir encore une masse critique assez élevée pour garantir aux participants un apport suffisant en énergie. 

A remarquer que, même si ce projet vient de remporter des prix pour sa qualité et sa capacité d’innovation, les premiers KWh ne seront pas produits par RennesGrid avant 2017. Une description quantitative et objective de résultats et retombées pratiques générés par cette nouvelle typologie d’infrastructure n’est donc pas encore directement faisable. 

##  7\. OFFRE DE SANTÉ CONNECTÉE 

Plusieurs typologies d’interventions peuvent être imaginées dans le secteur de la santé. L’une des plus simples est de mettre en place une plateforme unifiée des ressources à disposition dans la ville (médecins généralistes, spécialistes, pharmacies, urgences) et de leurs disponibilités pour RDV et interventions de différents types. Cette plateforme pourra même être utilisée d’une façon plus proactive, par exemple en suggérant aux patients l’hôpital dans lequel le temps d’attente pour l’examen à réaliser est le plus court. On peut viser de cette manière un usage plus équilibré des ressources et une coordination des parcours de soins entre les différentes structures ; les données recueillies pourront être aussi analysées a posteriori, avec l’objectif de choisir de manière optimale les modifications à faire sur le système (par exemple, quels hôpitaux renforcer en connaissant la demande et l’offre à un niveau beaucoup plus fin que aujourd’hui). Dans l’analyse de ce cas d’usage, il faut bien considérer l’importance du traitement des données personnelles qui est centrale pour les sujets liés à la santé. 

Du point de vue de la Data Science, la partie la plus intéressante est l’aide relative à l’analyse de données sur le court terme (exploitation optimale des ressources actuellement existants via un système de réservations qui prend en compte l’utilisation globale des ressources) et sur le moyen terme (en comprenant les modifications sur le système qui l’amélioreront le plus et qui seront les plus adaptées pour adresser les criticités détectées dans la première phase). 

Pour ce qui concerne les bénéfices attendus, des améliorations sont d’abord à prévoir en termes de services offerts aux patients une fois que toutes les informations seront groupées sur une même plateforme. Une telle plateforme permettra par exemple aux citoyens de facilement repérer la structure hospitalière avec le temps d’attente le plus court pour les examens cliniques qu’ils devront subir. Les structures hospitalières, de l’autre côté, pourront optimiser leur utilisation des ressources ; en diminuant l’impact de pics d’usage, elles pourront par exemple mieux programmer le staff de chaque hôpital. Pour les décideurs et les pouvoirs publics enfin, les analyses réalisées fourniront une aide précieuse dans les choix des modifications à faire sur le système pour résoudre les problèmes détectées et pour l’améliorer ultérieurement. 

###  RÉFÉRENCE D’EXPÉRIMENTATIONS 

Les expérimentations mises en place jusqu’ici sont pour la plupart partiels, et ne traitent pas encore du problème dans sa complexité globale. 

[ Dans cette référence ](http://smartcity.bcn.cat/en/telecare-service.html) , par exemple, le projet crée par la ville de Barcelone dans le contexte du suivi à distance des personnes plus âgées est présenté. La possibilité, que la connexion en temps réel va offrir, de traiter de manière plus efficace les urgences suffit déjà à expliquer l’intérêt de ces projets pour la collectivité. 

D’autres études, plus générales mais moins directement appliqués, ont aussi bien été menées. [ Dans cet article ](http://commerce.net/wp-content/uploads/2012/04/CN-TR-05-03.pdf) , les auteurs analysent les optimisations qui seraient possibles en utilisant, dans le système sanitaire, les mêmes principes et technologies déjà mises en œuvre dans l’industrie, et en particulier dans le e-business. 

##  8\. CARTE DES CONDITIONS DE VIE 

Mieux comprendre les conditions de vie dans les différents quartiers, identifier les situations les plus défavorables pour les pouvoir adresser, prioriser au sein de la ville les interventions dans le contexte de la politique sociale, de l’instruction, de la santé puis évaluer l’effet des mesures prises. Voici quelques thématiques à aborder pour la prochaine génération d’hommes politiques. Comment comprendre d’une façon plus quantitative les hétérogénéités au sein d’une ville ? 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.52-PM-002.jpg)

Et, une fois ces caractéristiques établies, comment évaluer si les actions mises en œuvre sont effectives ? Sur ces sujets, la Data Science peut fournir une aide significative. La première étape, plus simple à réaliser en termes d’infrastructures requises, est le regroupement sur une seule plateforme des informations plus facilement quantifiables sur les conditions de vie dans les différents quartiers telles que le salaire moyen, les données statistiques recueillies par l’INSEE, les indications venant des capteurs installés pour suivre pollution lumineuse, atmosphérique ou sonore. Dans une phase plus avancée, et après un travail de Data Science plus poussé, la même plateforme pourra accueillir des informations moins directement quantifiables telles que le niveau de sécurité perçu en utilisant les données venant par exemple des messages échangés sur les réseaux sociaux. 

L’apport Data Science sera fondamental dans la modélisation des données brutes, recueillies dans une variété de formats, et obtenues à travers plusieurs outils (caméras, capteurs, informations obtenues lors d’enquêtes menées dans la population, données présents dans les différents archives de la ville). D’un point de vue technique, on aura à adresser un certain nombre de problèmes d’optimisation sous contraintes (comment choisir le quartier où chercher son appartement en connaissant les caractéristiques de l’usager). Un rôle important va aussi être joué par le traitement de données non structurées, et en particulier des applications en termes de natural language processing pour ce qui concerne le traitement statistique des messages échangés sur les réseaux sociaux. Une partie de modélisation très poussée sera nécessaire au moment où un nombre élevé de paramètres (features) sera fusionné de manière à permettre d’augmenter l’interprétabilité des résultats pour le citoyen, cette dernière n’étant pas forcément garantie par les données brutes. 

Le premier résultat attendu de ce cas d’usage sera de fournir aux citoyens les informations sur les conditions de vie dans les différents quartiers et leur donner le moyen d’agir. Dans une démarche de type open government, il y aura une réappropriation de données publiques par la population, et une transparence majeure sur les motivations derrière les choix effectués par la mairie ou par les arrondissements. De plus, l’ouverture des données permettra aux citoyens de proposer des solutions innovantes aux problématiques détectées (cet intérêt étant peut-être même à exploiter plus en profondeur, en utilisant des formats du type Hackathon sur ces typologies de données). Une telle plateforme donnera aussi aux citoyens la possibilité de se mettre en contact plus facilement et de façon moins formelle avec décideurs et autorités locales, afin de signaler les services nécessaires et pas encore fournis, les structures nécessitant une mise à jour, les quartiers et bâtiments dégradés. Dans ce contexte, il faut s’attendre que de plus en plus de cas d’usages (parfois inattendus) soient proposés après la mise à disposition d’une telle infrastructure. 

###  RÉFÉRENCES D’EXPÉRIMENTATIONS 

[ Dans ce lien ](http://rue89.nouvelobs.com/2015/12/17/a-detroit-appli-a-reenchante-rapport-a-ville-262493) , un reportage sur la façon dont une application de ce genre a permis aux habitants de Detroit à se rapprocher au renouveau de la ville. 

##  9\. PLANIFICATION URBAINE 

Dans la section précédente, les jeux de données permettant de mieux comprendre les conditions de vie dans les différents quartiers. Le même jeu d’informations peut être utilisé par les décideurs publics en vue d’aménager la ville. La partie prédictive des modèles (et, en conséquent, la nécessité d’utiliser des méthodes de machine learning plus adaptés) est centrale dans ce cas d’usage, car la valeur ajoutée sera principalement la possibilité de prévoir à l’avance l’effet des interventions programmées ; ça, en vue de limiter au maximum la gêne procurée et d’effectuer lesdites interventions de la manière la plus efficace. L’évaluation à l’avance de l’impact des travaux sur la circulation urbaine (par rapport, par exemple, à la création de bouchons) sera une information précieuse pour pouvoir décider la date la plus adaptée pour le démarrage des travaux. Dans le transport public, les décideurs vont connaitre à l’avance les changements dans les temps de déplacement dû à l’ajout au réseau urbain des lignes de transport public ou à leur prolongement. Cette information les aidera à bien choisir quels axes de transport public renforcer prioritairement. De la même manière, pour chaque situation critique détectée en suivant la logique expliquée dans la section précédente on pourra simuler différentes approches, pour finalement mettre en œuvre la plus prometteuse. A posteriori, on pourra vérifier l’impact réel des actions prises, de manière à rendre les algorithmes utilisés de plus en plus fiables. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-05.52-PM-003.jpg)

Dans ce contexte, la Data Science a sans doute un rôle central : en plus de ce qui a été dit pour le cas d’usage précédent et qui reste en bonne partie valable, il y aura ici une composante plus poussée du point de vue de la modélisation, le focus étant plutôt sur la prédiction que sur l’observation des conditions existantes. 

La connaissance quantitative améliorée des problématiques abordée, obtenue à travers la mise en œuvre de ce genre de projet, apportera de la valeur dans plusieurs phases du processus de la prise de décision. D’abord, elle permettra une identification plus rapide et ponctuelle des criticités existantes au sein de la ville. Ensuite, elle sera utile pour choisir la manière la plus adaptée d’aborder le problème identifié (en considérant des différentes possibilités et en simulant leur impact). Enfin, elle permettra un suivi des effets vraiment obtenus, pour détecter difficultés ou erreurs dans la mise en œuvre, et même pour améliorer à fur et à mesure les algorithmes utilisés pour rendre les prévisions de plus en plus en ligne avec les effets réels de chaque typologie d’interventio 
