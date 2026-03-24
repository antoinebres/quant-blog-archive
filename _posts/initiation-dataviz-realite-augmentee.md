# initiation-dataviz-realite-augmentee
Wayback Machine URL: https://web.archive.org/web/20250709230638/https://www.quantmetry.com/blog/initiation-dataviz-realite-augmentee/
Archive date: 2025-07-09

Computer vision 

24/06/2019 

#  Initiation à la DataViz en Réalité Augmentée 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Finitiation-dataviz-realite-augmentee%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Initiation%20%C3%A0%20la%20DataViz%20en%20R%C3%A9alit%C3%A9%20Augment%C3%A9e&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Finitiation-dataviz-realite-augmentee%2F "Twitter") [ ](https://www.quantmetry.com/blog/initiation-dataviz-realite-augmentee/ "Email") [ ](https://www.quantmetry.com/blog/initiation-dataviz-realite-augmentee/ "Copy Link")

* * *

Temps de lecture : 20 minutes 

![Quantmetry.com : Initiation à la DataViz en Réalité Augmentée](https://www.quantmetry.com/wp-content/uploads/2019/06/5b51b6806d0e2.jpg)

Cet article aborde un angle expérimental de la DataViz : l’utilisation des technologies de Réalité Augmentée (RA). Il ne s’agit pas d’une nouvelle technologie, mais les avancées en matière de puissance de calcul couplée à la miniaturisation des équipements contribuent à un réel regain d’intérêt pour ces outils. À date, les secteurs les plus avancés sont l’industrie sur des cas d’usages de maintenance et la santé pour assister les chirurgiens. 

####  Introduction 

**Le terme « Réalité Augmentée » fut inventé en 1990 par le chercheur Tom Caudell employé de la firme Boeing. Avec l’aide de son collègue David Mizell, ils inventent un procédé d’aide à l’exécution des tâches de maintenances grâce à un affichage tête haute (en anglais Head Up Display, acronyme HUD) [1]. Celui-ci se place sur la tête des techniciens afin de pouvoir superposer les schémas techniques virtuels sur la vision réelle via un dispositif optique.** **Pour un panorama plus détaillé des origines du concept je vous invite à vous reporter à l’étude [2].**

**A mon sens, la meilleure définition de la RA est celle énoncée par Philippe Fuchs et Guillaume Moreau :**

> **La réalité augmentée regroupe l’ensemble des techniques permettant d’associer un monde réel avec un monde virtuel, spécialement en utilisant l’intégration d’images réelles (IR) avec des entités virtuelles (EV) : images de synthèse, objets virtuels, textes, symboles, schémas, graphiques, … D’autres types d’associations entre mondes réels et virtuels sont possibles par le son ou le retour d’effort. [3].**

**La RA est le premier niveau d’immersion de l’utilisateur dans un monde virtuel d’après la notion du « continuum virtuel / réel » imaginée en 1994 par Paul Milgram. Pour résumer, la RA est une Interface Homme-Machine (IHM).**

**Pour interagir avec l’utilisateur, la RA repose sur la notion de « déclencheurs ». Ces derniers sont plus ou moins évolués, avec ou sans marqueurs. En l’absence de ces derniers, c’est par l’intermédiaire de coordonnées de géolocalisation – système de positionnement en extérieur / intérieur : Global Positioning System (GPS), Wifi, Bluetooth, Ultra WideBand (UWB), Internet Protocole (IP), … – stockées dans un Système d’Information (SI) que les interactions avec l’utilisateur sont rendues possibles.**

#####  Principe de fonctionnement de la RA 

#####  Concepts généraux 

L’algorithme d’un système de RA peut être résumé en six étapes : 

  1. Recherche du/des déclencheur(s) à l’aide de différents capteurs : photographique, géolocalisation, accéléromètre, gyroscope, … 
  2. Détection et calcul de la direction et/ou position du déclencheur par rapport à l’utilisateur : orientation du capteur photographique qui filme les images de la scène réelle en 2D, coordonnées GPS, … 
  3. Identification du déclencheur : marqueur, visage, coordonnées GPS, … 
  4. Détermination de(s) élément(s) virtuel(s) à superposer au(x) déclencheur(s) ou à incruster dans la scène réelle : pictogramme, vidéo, élément HTML, … 
  5. Calcul de l’orientation ainsi que les coordonnées dans le plan des éléments virtuels. Selon l’orientation de la caméra de l’utilisateur, il peut être nécessaire de déformer les éléments. 
  6. Composition de l’image finale à partir de l’image de la scène réelle capturée par le capteur photographique ainsi que le(s) élément(s) virtuel(s) généré(s). 



Actuellement, une partie de ces étapes peuvent être abstraites via l’emploi de Software Development Kit (SDK) open source ou logiciel propriétaire tel ARToolKit, Layar, D’Fusion, Vuforia, … 

##  Les prérequis de la RA 

###  Les déclencheurs 

Les déclencheurs sont classifiés en deux grandes familles : avec ou sans marqueur. 

####  Avec marqueur, également appelé tag ou pattern 

Cette catégorie regroupe l’ensemble des moyens qu’utilise un système de RA pour identifier les objets de la scène réelle avec lesquels il doit interagir : superposer un objet virtuel sur un marqueur de la scène réelle, substituer un objet de la scène réelle par un objet virtuel [4], … Ils sont au nombre de trois : 

  * Le tag fiduciaire : il s’agit du plus connu, celui-ci peut être assimilé à un QR Code, composé d’un motif géométrique abstrait en noir et blanc. 
  * Le tag graphique : Il s’agit d’un marqueur fiduciaire auquel le motif géométrique abstrait est remplacé par un logo, un texte, un symbole, … Celui-ci est délimité par un contour noir. 
  * Le tag objet ou tag naturel : Il s’agit d’un marqueur intelligent qui analyse les images de la scène réelle pour identifier les zones interactives. L’utilisation de différents descripteurs d’images permet de détecter des visages, des lieux, des objets, … Le projet SixthSense14 repose sur l’utilisation d’amer pour détecter les actions de l’utilisateur. 



Afin d’offrir une expérience utilisateur réaliste, le système doit tenir compte de l’orientation, de l’emplacement, ainsi que du déplacement du marqueur par rapport à la caméra de l’utilisateur. Il est possible de mixer l’utilisation des différents types de marqueurs. 

Ce type de capteurs comporte cependant deux contraintes majeures. Tout d’abord, ils doivent être intégrés et présents dans la scène réelle capturée pendant toute la durée de l’interaction avec l’utilisateur. De plus, ceux-ci doivent être suffisamment proches de l’utilisateur pour que le système parvienne à identifier les différents tags. En cas de perte de vue ou de non détection d’un marqueur, l’objet virtuel n’apparaît pas. 

####  Sans marqueur : le géopositionnement 

Le système de RA utilise les coordonnées de géolocalisation comme déclencheur couplé à un ou plusieurs capteur(s) inertiel(s) afin de déterminer l’orientation de l’appareil. Comme précédemment, ce procédé n’est pas exempt de défaut. En fonction de la nature du projet, la précision du signal GPS d’une dizaine de mètres peut s’avérer insuffisante. De plus, celui-ci est inutilisable dans les zones couvertes ou requiert l’exploitation d’un système de positionnement d’intérieur : Wifi, Near Field Communication (NFC), Bluetooth, UWB, … 

###  Une batterie de capteurs 

Les mesures prises en temps réel nécessitent la présence de capteurs que l’on peut regrouper en deux classes : les extéroceptifs et les proprioceptifs. 

La performance d’un système de RA requiert que l’ensemble des capteurs utilisés soit correctement calibré. Pour d’avantage d’information, je vous invite à consulter la thèse de Gaël Sourimant [5] qui consacre la majeur partie du chapitre 3 au calibrage de la caméra. 

####  Capteurs extéroceptifs 

Ces capteurs, qu’ils soient actifs (capteurs infrarouges, télémètre laser, radar, capteurs ultra-son, …) ou passifs (capteur photographique, microphone, GPS, …), renseignent le système de RA sur l’environnement externe (monde réel). 

Les capteurs de vision (Charge-Coupled Device (CCD), Complementarity Metal-Oxide-Semiconductor (CMOS), …), outre la capture des scènes du monde réel, sont souvent utilisés pour la reconnaissance de signature visuelle. L’utilisation des capteurs de géopositionnement comme le GPS permet de déterminer grossièrement l’emplacement des POI. Ceci contribue à restreindre le périmètre de recherche lors de l’utilisation des descripteurs d’images capturées à l’aide du capteur photographique : en plus des notions de couleur, texte ou forme est ajoutée une information de géolocalisation. 

####  Capteurs proprioceptifs 

Ce type de capteurs se charge d’analyser et de décrire l’environnement local. Ils sont généralement internes au système de RA et fournissent des renseignements sur l’état du système. Les smartphones et tablettes sont composés d’un grand nombre de capteurs inertiels desquels on peut citer : l’accéléromètre, le gyroscope, la boussole. 

Le gyroscope permet de prendre en compte les mouvements de la caméra souhaités ou non : déplacement, tremblements, … La boussole permet quant à elle d’affiner la précision du calcul de position réalisé grâce au GPS. 

###  Les moyens de visualisation 

La RA peut être transmise à l’utilisateur par l’intermédiaire : 

  * D’un écran standard : smartphone, tablette, moniteur, télévision, … 
  * D’un écran transparent : tablette transparente, TV transparente, lunette (Google Glass, HoloLens), HUD (par brise de voiture, casque de pilote d’avion de chasse), … 
  * D’un visiocasque : Head-Mounted Display (HMD) comme l’Oculus rift, Google Cardboard, … 



####  État de l’art 

#####  Application technique 

La démocratisation des smartphones et tablettes au cours de ces 10 dernières années a fortement contribué au développement des solutions RA étant donné que ces périphériques possèdent tous les prérequis à l’utilisation de ces technologies : nombreux capteurs intégrés (photographique, géolocalisation, mouvement, …), puissance de calcul comparable à un ordinateur pour les modèles hauts de gamme, connexion Internet permanente mais surtout ils sont déjà utilisés quotidiennement par un très grand nombre d’utilisateurs. En 2015, un français sur deux possède un smartphone. De plus, les coûts de ces technologies ne cessent de baisser. Les domaines d’application tendent à s’élargir, à date, les principaux secteurs sont : 

  * Construction / Bâtiment Travaux Publics (BTP) / Architecture : 
    * Présentation virtuelle 3D sur terrain réel d’un projet immobilier comme en témoigne, Michel Gautier, maire de Betton (solution développée par Artefacto) 
    * Aide à la décision dans le cadre de travaux urbains : superposition d’images virtuelles de canalisation ou câblage sur une surface réelle (mur, sol, …) [6] 
  * Industrie : 
    * Aide à la réalisation des tâches industrielles : conception, production, assemblage, maintenance, formation, … illustrées par les solutions AugmentedPro Maintenance et AugmentedPro Production mises au point par la société française Robocortex. 
  * Tourisme : 
    * Guide touristique virtuel : musées, monuments / lieux, … tel que l’explique Emmanuel Mahé, auteur du projet de réalité augmentée « Jardin de Versailles ». 
    * Renaissance des monuments disparus : Abbaye de Cluny, Pompéi : Présentation virtuelle 3D sur emplacement réel d’un site disparu. 
  * Défense : 
    * Informations tactiques en temps réel, superposition vision nocturne ou chaleur, … 
  * Santé : 
    * Aide à la prise de décision des chirurgiens 



#####  Impacts et enjeux 

La RA, de par son côté novateur, où l’utilisation de cette technologie n’est pas encore rependue dans nos mœurs, suscite un grand intérêt de la part des secteurs du markéting et de la publicité qui recherchent à « surprendre » des acheteurs de plus en plus volatiles dans un monde de plus en plus concurrentiel : les marques cherchent de plus en plus à se démarquer de la concurrence. C’est le cas d’Ikea, au travers de son catalogue enrichi de tags RA, permet de visualiser des meubles en taille réelle. En l’espèce, la RA permet d’apprécier les volumes d’un objet en le plaçant virtuellement dans un environnement réel. Dans un autre contexte, Pepsi surprend les usagers patientant à un arrêt de bus grâce à un écran dissimulé dans l’une des parois de l’abri bus. Des images virtuelles sont ajoutées à la scène réelle donnant l’impression d’un spectacle incongru se passant réellement dans la rue. 

La RA est une nouvelle IHM encore immature : celle-ci est à la recherche de ses codes, principes, méthodes, … L’adoption de cette technologie requiert aux utilisateurs de changer et revoir leurs habitudes. Il s’agit d’entamer un long processus global de sensibilisation auprès du grand public. Les technologies de RA contribuent à rendre plus intuitive l’utilisation des SI car ceux-ci s’intègrent mieux dans notre mode de vie habituel. 

L’insuccès du premier prototype des Google Glass sorti en 2012 (projet officiellement stoppé en janvier 2015) illustre bien le manque de maturité générale ainsi que le besoin de changer nos mentalités. Outre l’aspect technique encore perfectible, notamment au niveau de la commande vocale, l’utilisation de ce type de produit soulève trois profondes questions qui méritent une sérieuse analyse : 

  * La vie privée : la majorité des gens ne veut pas être filmée en permanence 
  * Le droit : de nouvelles applications, « Vers un encadrement juridique 3.0 ? » 
  * L’inégalité : naissance de deux mondes : « l’homme normal » vs « l’homme augmenté » 



#####  Actualité 

Quatre ans après la sortie de l’HoloLens, Microsoft a récemment dévoilé la nouvelle version de son casque de réalité mixte (ou réalité augmentée) l’HoloLens 2 à quelques journalistes. Avec ce nouveau produit l’entreprise vise uniquement les professionnels. Le casque est ainsi destiné aux ouvriers, techniciens ou ingénieurs qui oeuvrent sur le terrain pour leur permettre d’accéder aux informations contextuelles (indicateurs, alertes, guides pédagogiques, …) de manière naturelle en leur laissant les mains libres. 

Par rapport à la précédente version jugée trop peu confortable pour être portée plus de 30 minutes, l’HoloLens 2 possède plusieurs innovations technologiques qui le rendent plus léger tout en étant plus performant que son prédécesseur. « Les casques-lunettes HoloLens mis au point par Microsoft qui permettent cette réalité augmentée sont aujourd’hui trop lourds. Un opérateur ne peut les porter que 15 à 30 minutes par jour, soit quelques heures par semaine.» avait affirmé Bertrand Félix, manager Projets-consulting manufacturing chez Volvo Trucks, dans le cadre d’une interview en avril 2018 sur le projet pilote d’utilisation de l’HoloLens dans la chaîne de contrôle qualité des camions Renault. 

Parmi les améliorations on note notamment que le champ de vision a été doublé, un système de tracking de la pupille a été ajouté, que l’appareil est maintenant doté d’un système inertiel qui lui permet de se repérer en 6 dimensions et qu’il est possible de soulever la visière pour avoir une vision directe sans nécessairement avoir à enlever le casque, ce qui le rend plus naturel a utilisé et plus propice à être adopté par les utilisateurs ciblés. 

#####  Solutions Software 

Pour développer une application de Réalité Augmentée (RA) on utilisera conjointement un framework approprié aussi appelé Software Development Kit (SDK), contenant les principales fonctionnalités d’une application de RA, ainsi qu’une plateforme de développement. Les SDK mentionnés dans cette section ont en commun de présenter l’ensemble des technologies de reconnaissance « marker-based » et «markerless » disponibles sur le marché, d’intégrer le calibrage de certains modèles de lunettes de réalité augmentées et de posséder leur propre plateforme de développement (SDK Studio dans le schéma ci-dessous) simplifiée qui permet une première approche de ceux-ci en plus d’être compatible avec les principales plateformes de développement (Android Studio, XCode, Visual Studio, Unity, … ). Ces solutions sont également largement fournies en documentations, tutoriels. 

![](https://www.quantmetry.com/wp-content/uploads/2019/02/solutions_SDK_RA-1024x181.png)

Le schéma ci-dessous résume les différentes briques technologiques utiles pour le développement d’une application de RA. Le SDK regroupe les codes de fonctionnalités primaires d’une application de RA qui seront agrégés via une plateforme de développement d’application. Les applications développées peuvent s’appuyer sur une base de donnée intégrée ou externe référençant les markers et les informations associées à afficher. 

![](https://www.quantmetry.com/wp-content/uploads/2019/02/Schéma-AR-1024x593.png)

**Visual Inertial Odometry** : Les deux SDK mentionnés ci-dessus reprennent des fonctionnalités d’autres SDK open source ARKit et ARCore, développés respectivement par Apple et Google. ARKit et ARCore sont notamment exploités pour leurs technologies de « Visual Inertial Odometry » (VIO) qui permet de calculer en temps réel (30 estimations/secondes) la position de la caméra en 6 dimensions (3D translations + 3D rotations) à partir de l’information visuelle collectée par la caméra (reconnaissance visuelle : nuage de points + mesure de la distance entre les points) et de celles collectées par le système inertielle de l’appareil (accéléromètre + gyromètre). Cette technologie couplée à la détection de plan 2D permet la réalité augmentée sans marker. 

Les principaux SDK de RA présents sur le marché offrent aujourd’hui des possibilités interessantes qui permettent de se projeter dans la conception d’une application pour l’industrie. Néanmoins, la technologie présente aussi des limites dont il est important être conscient puisqu’elles conditionneront la conception de l’application en fonction de son contexte et de son utilité. 

**Points d’attention :**

  * Performance de l’algorithme de reconnaissance d’objet, est-il capable de distinguer suffisamment de détaille dans un objet complexe. Dans quelle mesure peut-on utiliser cette technologie sur des équipements industriels complexes (moteurs, …) ? 
  * Capacité des databases, peut-on stocker suffisamment de modèles 3D ? 
  * Comment reconnaitre 2 modèles 3D d’apparences similaire (du point de vue de la reconnaissance visuelle) mais différents (ex : deux équipements du même modèle) ? 
  * Distance par rapport à la cible, si on se rapproche et que l’on ne perçoit plus qu’une sous partie de l’objet comment se comporte l’application ? Quel est le cheminement logique de l’application ? (Reconnaissance en continue ou première reconnaissance + sous reconnaissance etc, …) Quelle est la distance entre la caméra et la target dans un usage type ? 



#####  **Vuforia Studio / Vuforia Engine (SDK)**

Vuforia est la plateforme de développement d’application RA de l’entreprise américaine PTC spécialisée dans le développement de logiciel pour l’industrie. 

Vuforia offre plusieurs façon de réaliser les principales étapes de fonctionnement d’une application de RA. 

![](https://www.quantmetry.com/wp-content/uploads/2019/02/Etapes_fonctionnement_RA-1024x185.png)

  * **Voir :**
    * Marker based 
      * Objet 3D 
        * 3D/CAD modèle, reconnaissance basée sur la géométrie de l’objet. 
        * Based off features (*.OD files) 
      * Image 2D 
        * Marker de type QRcode 
        * Image 
    * Markerless 
      * Détection de surface 2D 
      * VIO, détection inertielle 
  * **Reconnaître :**
    * Database embarquée : ses limites dépendent des supports utilisés notamment de la puissance de calcul disponible pour faire tourner le modèle de reconnaissance dans un temps raisonnable et du niveau de détail des cibles. Plusieurs types de cible différents peuvent être combinés. Les limites indicatives données sont de 20 objets différents + 80 images ou 1000 images pour un dataset. Il est possible de créer plusieurs dataset pour différents usages. Supporte la reconnaissance de plusieurs cibles en simultané. 
    * Cloud database : contient uniquement des cibles de type image, peut en contenir 1 million. Limité à un dataset. 
    * Cloud Recognition : limité à la reconnaissance d’une target à la fois. 
  * **Afficher :**
    * Texte 
    * Vidéo 
    * Image 
    * Modèle 3D 
    * Surface Mapping 



**Vuforia Studio :** La solution permet également une prise en main facilitée au travers de sa version studio, qui permet de développer en drag&drop. 

![](https://www.quantmetry.com/wp-content/uploads/2019/02/Vuforia_Studio.png)

**Les modèles réels 3D :** Le software permet d’appréhender des objets 3D dans le monde réel de plusieurs manières. 

  * **Vuforia Object Scanner :** Application Android qui permet de générer, éditer et tester des fichiers de types *.OD (Object Data File) qui contiennent une visualisation des caractéristiques de l’objet ainsi que leurs répartitions sur l’objet  .  A noter : Il est possible de scanner uniquement des sous-parties d’un objet. Cela peut être intéressant pour différencier des objets globalement semblables mais qui présentent des dissemblances en certaine région. Le scanner présente de bonnes performances pour les objets convexes et qui présentent suffisamment de contrastes. 



![](https://www.quantmetry.com/wp-content/uploads/2019/02/object_scanned_vuforia.jpg)

![](https://www.quantmetry.com/wp-content/uploads/2019/02/Vuforia_Obj_Scan.png)

  * **Model Target Generator :** converti un modèle 3D/CAD en un dataset compatible avec le SDK Vuforia Engine. Permet également de créer des « Guide View » à partir du modèle 3D. Les « Guide Views » sont des angles de vue pré-définit d’un objet qui permette d’initialiser un recouvrement 3D (surface mapping) de l’objet en question (cf. image ci-dessous). 



#####  Les Casques de RA 

Plusieurs casques de RA sont actuellement disponibles sur le marché. La matrice comparative ci-dessous n’est pas exhaustive mais présente la plupart des casques à destination des professionnels de l’industrie. 

On distingue principalement deux catégories. D’une part les casques de très haute performance, binoculaires et intégrant les fonctionnalités les plus avancées pour une experience visuelle et interactive la plus naturelle possible mais qui ont l’inconvenient d’être lourd et peu confortable. De l’autre les casques plus légers et qui s’apparentent plutôt à des lunettes classiques avec une projection de l’information virtuelle monoculaire, le champ de vision impacté par la RA est nettement inférieur à la première catégorie. 

Si l’immersion est importante dans une experience de RA, le confort d’un casque est primordial pour son adoption. 

![](https://www.quantmetry.com/wp-content/uploads/2019/02/matrice_casques_ra_v2-2-1024x595.png)

#####  Deep Learning et RA 

#####  Reconnaissance d’objets au coeur de la RA 

Comme mentionné plus haut une des briques centrales de la réalité augmentée est la reconnaissance. Cette reconnaissance peut s’effectuer à l’aide de nombreux capteurs, mais elle peut aussi s’effectuer directement à partir de l’image seule. Ce qui devient de plus en plus possible avec les avancées importantes des techniques de deep learning dans le domaine de la reconnaissance d’image. 

Aujourd’hui les réseaux de neurones sont capables de détecter des objets avec différents niveaux de granularité: 

![](https://www.quantmetry.com/wp-content/uploads/2019/02/Capture-d’écran-2019-06-04-à-17.13.32.png)

Chacun de ses niveaux de détection peut donner lieu à de la réalité augmentée bien que dans l’inconscient collectif on s’attende plutôt à de la reconnaissance d’objets multiples (object détection ou mieux instance segmentation dans l’image du dessus) 

La problématique avec les algorithmes de localisation d’objets est qu’ils demandent beaucoup plus d’images d’entrainement que les algorithmes de classification. Un aspect important car les cas d’usages majoritaires de la RA sont plutôt dans des secteurs spécifiques (industrie, médical, défense, BTP) dans lesquels il est difficile de se procurer des images en grand volume. Une solution pour contourner ce problème est d’utiliser des réseaux pré-entrainés et de faire de l’augmentation de données en créant des images déformées à partir des images originales. Mais il faudra quand même disposer de quelques milliers d’images d’entrainement. 

![](https://www.quantmetry.com/wp-content/uploads/2019/02/Capture-d’écran-2019-06-04-à-18.36.05.png) Un premier niveau de réalité augmentée est déjà possible avec les algorithmes de type classification, comme peut le montrer une application mobile que nous avons développé récemment pour un industriel du secteur gazier. Cette application devait détecter, à partir du flux vidéo de la caméra du smartphone, les canalisations de gaz qui devaient être repeinte ou pas. La localisation du défaut de peinture n’était pas si critique car évidente à trouver par l’opérateur, l’enjeu était plus d’objectiver la décision de repeindre ou pas l’installation. 

Il faut remarquer que bien que les casques de réalité augmenté attirent particulièrement l’attention, un appareil de choix pour cette technologie RA reste le smartphone. D’autant plus que le smartphone équipe déjà souvent les personnels susceptibles d’utiliser ces technologies, qu’il reste moins onéreux que les casques type Hololens et qu’il dispose de capacités de calcul et batterie bien plus significative. 

D’ailleurs les premières applications de réalité augmenté sont sorties sur smartphone et aujourd’hui, comme les applications Pokemon Go, navigation Google Map avec AR, ARKit, ARCore le montrent bien, l’expérience AR sur smartphone a encore de l’avenir. 

#####  Exécution des modèles Deep Learning sur les casques et smartphones 

A l’instar des technologies Web où de plus en plus de traitements s’exécutent au niveau du frontend pour offrir à l’utilisateur une expérience fluide, on observe une demande de plus plus forte pour effectuer les traitements de reconnaissance directement sur l’objet de visualisation de la RA (casque ou smartphone). Ce qui, en plus d’offrir une expérience fluide à l’utilisateur, permet également de profiter de l’expérience dans des environnements où la connexion internet n’est pas très stable, un aspect crucial si la RA est utilisée pour aider des professionnels dans leurs taches quotidiennes par exemple. 

Cette tendance amène de nouveaux challenges techniques car les interfaces de visualisation de RA que sont les smartphones et surtout les casques, ont des ressources matérielles (batterie, CPU, mémoire, stockage) beaucoup plus limitées que les PC ou serveurs. 

Il s’agit un champ de recherche encore très largement ouvert qui vise à réduire l’utilisation des ressources matérielles utilisées pour effectuer des reconnaissances, ce que l’on appel le « edge computing ». Dans le deep learning pour la reconnaissance d’image on peut citer par exemple des techniques comme: 

  * la quantification, qui vise a remplacer les paramètres par des nombres entiers, les calculs sont beaucoup moins gourmands si on les effectue avec ce type de données. 
  * le pruning qui vise a supprimer les paramètres qui ont des faibles valeurs 
  * la convolution séparable qui permet de réduire considérablement le temps de calcul de l’opération essentielle des réseaux de neurones convolutionnels: la convolution 



Ces techniques permettent de réduire d’un facteur 10 ou plus les temps d’exécution des prédictions, la mémoire utilisée et l’espace de stockage nécessaire pour enregistrer les paramètres. 

#####  Ouvertures et conclusion 

La RA est aujourd’hui une réalité, des applications comme Pokémon Go ou Google Navigation AR le prouvent bien, cette interface de visualisation a toute sa place et est très pertinente pour certains types de données. 

Néanmoins pour qu’elle se démocratise elle ne doit pas nécessiter de poser des markers sur la scène a « virtualiser », d’ou une place prédominante des algorithmes de reconnaissance d’objets. Des algorithmes utilisant idéalement uniquement les images mais pouvant aussi s’aider des divers capteurs des casques et smartphones (accéléromètres, gyroscopes, boussoles) 

Un des enjeux sera alors de pouvoir effectuer cette reconnaissance sophistiquée directement sur les interfaces de RA que sont les smartphones et les casques, et qui disposent de ressources matérielles très limitées. Si ce challenge est relevé avec succès on pourra offrir à l’utilisateur une expérience fluide, même sans connexion réseau et alors un horizon de cas d’utilisations sur casque sera ouvert, avec en premier lieu l’assistance sur des opérations nécessitant d’avoir les mains libres, comme l’assistance à la maintenance. 

#####  ✍ Ecrit par : [ Guillaume MOCQUET ](https://www.linkedin.com/in/guillaumemocquet/) ( [ @GuillaumMocquet ](https://twitter.com/GuillaumMocquet) ), [ Bastien ROUSSEL, Vincent Dejouy ](https://www.linkedin.com/in/bastienroussel/)

#####  BIBLIOGRAPHIE 

  1. CAUDELL T. P., MIZELL D. W. « Augmented reality: an application of heads-up display technology to manual manufacturing processes ». In : Proc. Twenty-Fifth Hawaii Int. Conf. Syst. Sci. 1992 [En ligne]. Proceedings of the Twenty-Fifth Hawaii International Conference on System Sciences, 1992. [s.l.] : [s.n.], 1992. p. 659‐669 vol.2. Disponible sur : < http://dx.doi.org/10.1109/HICSS.1992.183317 >
  2. ARTH C., GRASSET R., GRUBER L., LANGLOTZ T., MULLONI A., WAGNER D. The History of Mobile Augmented Reality [En ligne]. Inffeldgasse 16, 8010 Graz : Graz University of Technology, 2015. Disponible sur : < http://www.icg.tugraz.at/publications/pdf/the-history-of-mobile-augmented-reality/at_download/file >
  3. FUCHS P., MOREAU G., AUVRAY M., ÉCOLE NATIONALE SUPÉRIEURE DES MINES DE PARIS. Le traité de la réalité virtuelle. Paris : Presses de l’Ecole des mines, 2006. ISBN : 2911762622 9782911762628 2911762630 9782911762635 2911762649 9782911762642 2911762657 9782911762659. 
  4. SALAS-MORENO R. F., NEWCOMBE R. A., STRASDAT H., KELLY P. H. J., DAVISON A. J. « SLAM++: Simultaneous Localisation and Mapping at the Level of Objects ». In : 2013 IEEE Conf. Comput. Vis. Pattern Recognit. CVPR [En ligne]. 2013 IEEE Conference on Computer Vision and Pattern Recognition (CVPR). [s.l.] : [s.n.], 2013. p. 1352‐1359. Disponible sur : < http://dx.doi.org/10.1109/CVPR.2013.178 >
  5. SOURIMANT G., BOUATOUCH K. Reconstruction de scènes urbaines à l’aide de fusion de données de type GPS, SIG et Vidéo. S.l. : s.n., 2007. 
  6. BALDISSER E., CIEUTAT J.-M., GUITTON P. « Apports de la Réalité Augmentée à la Gestion de Réseaux et de Mobiliers Urbains ». In : 8èmes journées de l’Association Française de Réalité Virtuelle, Augmentée, Mixte et d’Intéraction 3D. [s.l.] : [s.n.], 2013. Disponible sur : < https://hal.archives-ouvertes.fr/hal- 00913594/document > (consulté le 12 juin 2015) 



http://www.idemployee.id.tue.nl/g.w.m.rauterberg/presentations/hci-history/tsld096.htm 

http://socialcompare.com/fr/comparison/augmented-reality-sdks : comparatif de nombreux SDK 

http://artoolkit.org/ : SDK open source pionnier et leader, acquis en mai 2015 par la société DAQRI 

https://www.layar.com : pionnier sur les technologies de RA, racheté en juin 2014 par Blippar 

http://www.t-immersion.com/products/dfusion-suite/dfusion-pro : solution propriétaire tout en un 

https://www.qualcomm.com/products/vuforia 

http://www.lesnumeriques.com/fujitsu-iris-concept-tablette-oled-transparent-etonnant-n20792.html 

http://www.psfk.com/2015/06/college-dorm-cardboard-furniture-set-room-in-a-box.html 

https://www.microsoft.com/microsoft-hololens/en-us 

https://www.google.com/get/cardboard/ 

http://www.emarketer.com/Article/2-Billion-Consumers-Worldwide-Smartphones-by-2016/1011694 

https://www.urbasee.com/index.php 

http://www.maisonapart.com/edito/construire-renover/maison-intelligente/la-realite-augmentee-s- immisce-dans-la-constructio-8748.php 

http://www.robocortex.com/ 

http://www.culturemobile.net/quotidien-intelligent/patrimoine-se-reinvente-ra 

http://culturebox.francetvinfo.fr/expositions/patrimoine/cluny-reprend-vie-grace-a-la-3d-et-a-la-realite- augmentee-39769 

http://www.ara.com/arc4/ 

http://www.ikea.com/ms/fr_FR/france/appli_catalogue_2015.html 

http://www.convinceandconvert.com/social-media-case-studies/pepsi-max-shocks-and-delights-londoners- with-augmented-reality-stunt/ 

http://www.challenges.fr/high-tech/20150116.CHA2262/la-vente-des-google-glass-suspendue.html 

http://www.laverdet-avocat.com/publications/Expertises-février-2015-Réalité-augmentée-vers-un- encadrement-juridique-3-0-Caroline-Laverdet.pdf 

https://www.theverge.com/2019/2/24/18235460/microsoft-hololens-2-price-specs-mixed-reality-ar-vr-business-work-features-mwc-2019 

https://www.lopinion.fr/edition/economie/renault-trucks-va-ameliorer-controle-qualite-realite-augmentee-145735 

https://medium.com/6d-ai/why-is-arkit-better-than-the-alternatives-af8871889d6a 

https://library.vuforia.com/content/vuforia-library/en/articles/Solution/introduction-model-targets-unity.html 
