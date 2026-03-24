---
layout: post
title: initiation-au-clustering
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129162456/https://www.quantmetry.com/blog/initiation-au-clustering/
---
Uncategorized 

01/12/2015 

#  Initiation au Clustering 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Finitiation-au-clustering%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Initiation%20au%20Clustering&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Finitiation-au-clustering%2F "Twitter")

* * *

Temps de lecture : 14 minutes 

![Quantmetry.com : Initiation au Clustering](https://quantmetry.b-cdn.net/wp-content/uploads/2015/12/screen-shot-12-30-18-at-06-57-pm.jpg)

Le machine learning est sans conteste l’un des atouts majeurs permettant de comprendre les enjeux de la société d’aujourd’hui et de demain. Parmi les différentes composantes qui constituent cette discipline, je vais me concentrer sur l’un des sous-domaines d’application qui le caractérise : le clustering. Ce champ d’études couvre des domaines ainsi que des sujets divers et variés, et permet d’étudier les problématiques associées selon des perspectives différentes. En effet, l’algorithme ne sera pas influencé par le data scientist quant aux différentes typologies qui caractérisent la population à partitionner (consommateurs, gènes, objets, textes,…) : on parle d’objectivité algorithmique. Cet article présente succinctement certains sujets d’étude de cette forme d’intelligence artificielle afin d’initier le lecteur au champ de possibilités qui lui sont associées et d’illustrer certaines méthodes sans entrer dans l’exhaustivité de celles-ci. 

##  CLUSTERING VS CLASSIFICATION : OÙ ? QUAND ? COMMENT ? 

Le terme clustering est l’un des curieux anglicismes du data scientist ; celui-ci désigne le concept de classification non supervisée, appartenant à la grande famille de l’apprentissage non supervisé. L ‘étape préliminaire de cet article va consister à distinguer les deux grands types de classification : « supervisée » (classification en anglais) ou « non supervisée » (clustering). La distinction principale est expliquée dans ce qui suit, et est accompagnée de quelques exemples illustratifs de domaines d’application et de possibilités de sujets associés à ces deux groupes de méthodes. 

  * La classification supervisée nécessite de fournir à l’algorithme une population déjà partitionnée. L’idée est de lui apprendre quelle est la loi qui régit la répartition afin qu’il puisse affecter un nouvel individu à sa classe d’appartenance. 




On pensera tout d’abord au challenge Kaggle incontournable concernant la reconnaissance de chiffres manuscrits. D’autre part, on constate une réelle ouverture du monde de l’entreprise dans sa globalité à la classification supervisée. On peut citer l’exemple d’un grand opérateur téléphonique ayant récemment décidé d’intégrer le machine learning à sa méthodologie afin de « cartographier les talents » déjà présents en interne. Cela permettra dans un premier temps de déterminer rapidement et facilement quels employés positionner sur le lancement d’un nouveau service. Grâce à ses réponses au questionnaire, l’algorithme détermine auquel des 8 profils le salarié appartient. Dans la poursuite d’un objectif complètement différent, la classification supervisée a été, il y a peu, mise au service du e-commerce à travers un challenge de Data Science concernant la catégorisation de produits en fonction de leur image et de leur description[1]. 

Enfin, parmi les incontournables domaines d’application de la classification, on citera notamment la biologie, champ d’études très vaste et bien connu de l’analyste, à travers par exemple l’établissement de diagnostics médicaux : catégorisation de la nature de tumeur associée au cancer du sein (maligne ou bégnine), stade de maladie d’un patient, etc … 

  * Le clustering vise quant à lui à déterminer une segmentation de la population étudiée sans a priori sur le nombre de classes, et à interpréter a posteriori les groupes ainsi créés. Ici, l’homme n’assiste pas la machine dans sa découverte des différentes typologies puisqu’aucune variable cible n’est fournie à l’algorithme durant sa phase d’apprentissage. 




Là encore, les exemples d’application sont divers et variés. Dans le monde de l’entreprise, on rencontre ce sous-domaine du machine learning à travers la segmentation de clientèle, sujet d’une importance considérable dans le milieu marketing. Un autre cas d’usage correspond à la détection d’outliers, applicable à de nombreux domaines. On pourra penser plus particulièrement à la détection de fraudes, que ce soit dans les transports en commun, dans le cadre d’un remboursement de santé complémentaire ou encore au sujet de la consommation électrique… Les applications sont nombreuses. 

On peut à nouveau citer le domaine du biomédical comme l’un des champs d’applications étendus de ces méthodes de classification, à travers, entre autres, le regroupement de gènes différentiels selon leur profil d’expression dans un phénomène biologique au cours du temps. 

Pour les plus mélomanes, ces algorithmes peuvent aussi être utilisés dans une problématique de recommandation, afin de répartir différentes musiques en clusters et proposer à l’utilisateur une chanson « semblable » à celle qu’il vient d’écouter. Enfin, on peut constater que quelques « sériephiles » débordent d’imagination concernant les nouveaux domaines d’applications du clustering. Certains prévoient sur la toile d’appliquer ces méthodes aux personnages de Game of Thrones afin de détecter des typologies d’individus, et qui sait, peut-être déterminer scientifiquement quels seront les vrais prétendants au trône de fer. Le clustering, il y en a définitivement pour tous les goûts. 

De nombreuses méthodes de classification non supervisée ne peuvent s’appliquer qu’à des données quantitatives. Je me placerai donc dans ce cas pour illustrer mes propos. Remarquez cependant qu’il est possible de traiter ces données en amont afin de se ramener au cas quantitatif. En effet, en présence d’un mélange de variables quantitatives et qualitatives, on peut gérer le problème d’hétérogénéité des données en réduisant d’une part les données quantitatives, et en utilisant d’autre part une méthode telle que l’Analyse Factorielle des Correspondances Multiples (AFCM) afin de créer des coordonnées quantitatives à la population. Cette méthode de réduction de dimension calculée sur les variables qualitatives correspond à une AFC du tableau disjonctif complet, et va mener à une production de scores[2]. Ces derniers peuvent alors être utilisés comme coordonnées quantitatives des individus. 

Le clustering revient à chercher une structure « naturelle » dans les données, puisqu’aucune typologie cible n’est fournie préalablement à l’algorithme. L’idée est de déterminer des classes devant être à la fois les plus homogènes possibles tout en se distinguant au mieux les unes entre les autres. C’est alors que l’on commence à toucher du bout des doigts la nécessité de déterminer une mesure de séparabilité des classes, de (dis)similarité entre les individus. 

Cette notion ne sera en réalité pas le seul choix du data scientist dans sa recherche de clusters d’individus. Les principaux seront les suivants (dans le cas quantitatif dans lequel nous nous sommes placés) : 

  * le concept de dissimilarité, de dissemblance ou encore de distance entre les individus que je viens d’évoquer. En pratique et dans notre cas, le choix de la matrice identité en tant que matrice de produit scalaire semble être élémentaire, et est néanmoins assez courant. Cependant, dans le cas de variables de variances hétérogènes, il est fortement conseillé de les réduire (comme dans le cas d’une ACP). La matrice associée au produit scalaire correspond alors à la matrice des inverses des écarts-types (sur la diagonale donc). Attention au terme utilisé pour désigner ce concept selon le type de vos individus, on ne pourra pas, par exemple, parler de distance dans le cas qualitatif, 

  * la notion d’homogénéité des classes: elle est mesurée à partir de la matrice variance-covariances intra-classe (ou interclasses pour l’hétérogénéité des classes entre elles), 

  * le nombre de classes, noté K. 




Enfin, selon la méthode retenue, il peut être nécessaire de définir un critère d’arrêt de l’algorithme (convergence vers un minimum local ou nombre d’itérations maximum fixé). 

Maintenant que vous connaissez tous les choix cornéliens que vous devrez effectuer, entrons un peu plus en détails dans la description de deux grandes catégories du clustering : la classification hiérarchique non supervisée et les méthodes de partitionnement. 

##  LA CLASSIFICATION HIÉRARCHIQUE NON SUPERVISÉE 

La première étape de cette méthode consiste à définir un tableau de distances ou de dissemblances entre les individus, qui sera recalculé à chaque étape. La Classification Ascendante Hiérarchique (CAH) va, en partant de la classification donnée par les singletons, regrouper les éléments (singletons ou classes) les plus proches jusqu’à l’obtention d’une seule classe. 

Cette méthode permet d’obtenir une représentation graphique similaire à un arbre, appelé dendrogramme. Il représente l’ensemble des classes créées au cours de l’algorithme. Celles-ci ont été regroupées au fur et à mesure des itérations en s’appuyant sur la comparaison des distances ou dissemblances entre les individus et/ou les classes. La taille des branches du dendrogramme est proportionnelle à cette mesure entre les objets regroupés. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-06.56-PM.jpg)

Exemple de classification (en haut) et dendrogramme associé (en bas). 

Graphiquement, c’est donc à l’endroit où les branches du dendrogramme sont les plus élevées qu’il faut « couper », c’est-à-dire arrêter la répartition en classes. 

Le tracé de l’évolution de l’inertie intra-classe en fonction du nombre de clusters aide lui aussi graphiquement l’analyste au choix de K. Celle-ci diminue lorsque le nombre de classes augmente. En effet, elles sont de plus en plus homogènes, de plus en plus petites et les individus de plus en plus « proches » du centre de gravité de leur cluster. 

Puisque l’on cherche à minimiser ce critère, on aurait tendance au premier abord à vouloir sélectionner un nombre de classes K très élevé. Un tel choix ne serait néanmoins pas judicieux puisque la classification n’apporterait que très peu d’information. Son interprétation n’en serait que plus difficile. C’est pourquoi c’est en fait une diminution “brutale” de l’inertie intra-classe en fonction du nombre de clusters qu’il faut rechercher. 

Différentes stratégies d’agrégation entre deux classes A et B peuvent être considérées lors de la construction du dendrogramme, dont les plus connues sont les suivantes : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-06.56-PM-001.jpg)

  * Le saut minimum ou lien simple correspondant à la plus petite distance parmi l’ensemble des distances calculées entre un individu de A et un de B, 

  * Le saut maximum ou lien complet correspondant à la plus grande distance parmi l’ensemble des distances calculées entre un individu de A et un de B, 

  * Le saut moyen ou lien moyen correspondant à la moyenne des distances entre les individus de A et ceux de B, 

  * Le saut de Ward, qui vaut 

en considérant d comme la distance euclidienne et gA et gB les barycentres des classes considérées, wA et wB étant les pondérations respectives des classes A et B. 




Deux questions se posent alors en pratique : quel saut choisir et pourquoi ?Voici quelques éléments généraux de réponse. Le lien simple va être associé à l’arbre couvrant minimal. Il génère des classes de diamètres très différents et a une tendance à l’effet de chaînage : il favorise généralement l’agrégation plutôt que la création de nouveaux clusters et présente une sensibilité aux individus bruités. 

Le lien complet créera quant à lui des classes compactes et arbitrairement proches. Il est lui aussi sensible au bruit.Le lien moyen correspond à un bon compromis entre séparation et diamètre des classes, c’est en fait un bon compromis entre lien simple et lien complet. Néanmoins, les clusters présenteront généralement des variances proches. 

Enfin, à chaque itération (ou étape de regroupement), le saut de Ward choisit de minimiser l’augmentation de l’inertie intra-classe. Ce lien aura tendance à créer des classes plutôt sphériques et d’effectifs égaux pour un même niveau du dendrogramme. Il présente aussi une certaine facilité d’utilisation : même dans le cas où la distance entre individus n’est pas euclidienne, son expression n’est pas modifiée. C’est pour l’ensemble de ces raisons que la palme d’or du choix le plus courant des utilisateurs revient sans conteste au saut de Ward. 

Il est important de noter que la classification hiérarchique non supervisée est assez chronophage. Elle n’est à appliquer qu’à des datasets peu conséquents en termes de nombre d’individus. Le dendrogramme est d’ailleurs de moins en moins lisible lorsque ce nombre augmente. Je vous présenterai en fin d’article une manière de remédier à ce type d’inconvénients. 

##  MÉTHODES DE PARTITIONNEMENT (OU DE CENTRES MOBILES) 

###  LES DIFFÉRENTES MÉTHODES 

L’originalité de cette méthode provient de son caractère contradictoire, dans le sens où son appartenance aux algorithmes d’apprentissage non supervisé s’oppose à la nécessité d’un nombre de classes K fixé a priori pour cette méthode. Il est important de noter que ces algorithmes sont bien moins conséquents en temps de calculs que ceux introduits précédemment. 

Je vais principalement détailler ici la méthode des nuées dynamiques et j’aborderai ensuite les variantes existantes. Le principe est le suivant : 

  * Initialisation : Les k centres initiaux sont généralement choisis par tirage aléatoire ou par utilisation des centres d’une méthode de clustering déjà appliquée à la population. 

  * Les individus sont affectés à la classe dont le centre est le plus « proche » [3] 

  * Les étapes suivantes sont réitérées : 




– Les barycentres de ces classes sont calculés et deviennent les nouveaux centres. 

– Les individus sont alors affectés à la nouvelle classe dont le centre est le plus proche, et ce procédé est réitéré. 

  * L’algorithme s’arrête selon un critère défini par l’utilisateur. 




Selon la métrique choisie préalablement choisie. 

Deux variantes principales de la méthode des nuées dynamiques existent et se classent dans la famille des méthodes de partitionnement : 

  * Les K-means de MacQueen : le choix des centres des classes est effectué par tirage pseudo- aléatoire. Contrairement à la méthode précédente, la méthode K-means de MacQueen n’attend pas d’avoir réaffecté tous les individus pour modifier la position des centres (qui correspondent aux barycentres). À chaque fois qu’un individu est réaffecté à une classe, le centre corres 



