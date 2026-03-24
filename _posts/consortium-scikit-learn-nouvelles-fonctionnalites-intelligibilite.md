# consortium-scikit-learn-nouvelles-fonctionnalites-intelligibilite
Wayback Machine URL: https://web.archive.org/web/20230129161952/https://www.quantmetry.com/blog/consortium-scikit-learn-nouvelles-fonctionnalites-intelligibilite/
Archive date: 2023-01-29

Recherche et développement 

06/06/2019 

#  Consortium scikit-learn - Nouvelles fonctionnalités & intelligibilité 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fconsortium-scikit-learn-nouvelles-fonctionnalites-intelligibilite%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Consortium%20scikit-learn%20-%20Nouvelles%20fonctionnalit%C3%A9s%20%26%20intelligibilit%C3%A9&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fconsortium-scikit-learn-nouvelles-fonctionnalites-intelligibilite%2F "Twitter")

* * *

Temps de lecture : 8 minutes 

![Quantmetry.com : Consortium scikit-learn - Nouvelles fonctionnalités & intelligibilité](https://quantmetry.b-cdn.net/wp-content/uploads/2019/06/article-remi-min.png)

Le 28 mai dernier se tenait le [ consortium scikit-learn ](https://scikit-learn.fondation-inria.fr/first-annual-workshop/) , à Rueil-Malmaison 

Etant un utilisateur de longue date de cette bibliothèque bien connue des amoureux de l’apprentissage automatique, Quantmetry était présent lors de ce consortium, principalement dans une optique de veille technologique. 

Nous avons décidé de vous faire un petit tour d’horizon des nouveautés et des idées futures. Allez, venez, c’est par ici … 

* * *

##  **_New Features_ – Roman Yurchak   
**

Après une introduction de Gaël Varoquaux en personne, nous enchaînons sur une présentation des nouvelles fonctionnalités introduites pour la plupart dans les versions 0.20 et 0.21 de scikit-learn. Au moment de la prise de parole de Roman Yurchak, la tension est palpable. 

###  **Pré-traitement /** **_pipelining_ **

La première évolution présentée (V0.20) est l’ajout d’un [ ColumnTransformer ](https://scikit-learn.org/stable/modules/generated/sklearn.compose.ColumnTransformer.html) . 

Ce _transformer_ est en fait un ajout de longue date de certains utilisateurs, qui préféraient prendre des DataFrames pandas en entrée plutôt que des structures _numpy_ , et suivre les transformations par colonne sur ces DataFrames. 

Le _ColumnTransformer_ permet donc simplement d’affecter au niveau des colonnes une séquence de transformations à effectuer, et ainsi de construire un _pipeline_ en conséquence. À noter que Quantmetry a récemment mis en ligne un package permettant de faire la même chose sur PySpark, [ ici ](https://pipeasy-spark.readthedocs.io/en/latest/) . 

###  **Chargement de données natif depuis OpenML**

Ce petit ajout, non sans conséquence, consiste à faciliter le chargement de sets de données directement depuis [ OpenML ](https://www.openml.org/) , une plateforme de Machine Learning collaboratif qui met à disposition des jeux de données. 

###  **EarlyStopping**

**![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/06/Capture-d’écran-2019-06-06-à-14.49.02-300x176.png) **   
L’ [ EarlyStopping ](https://en.wikipedia.org/wiki/Early_stopping) , que nous pourrions traduire par Arrêt Anticipé, est une logique assez simple en apprentissage automatique, qui consiste à **arrêter l’entraînement du modèle de manière prématurée** , lorsqu’aucune amélioration dans sa capacité de généralisation (training error vs test/validation error) n’est observée, et qui peut être très utile pour : 

  1. **Réduire le temps d’entraînement** du modèle 
  2. **Diminuer le risque de sur-apprentissage** –  _ overfitting  _



  
La version 0.20 de scikit-learn introduit donc la gestion de l’Arrêt Anticipé via un simple paramètre booléen optionnel, lors de l’instanciation du modèle 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/06/Capture-d’écran-2019-06-06-à-14.52.03.png)

###  **Power Transformer – “** **_make data more gaussian-like”_ **

Une autre classe dédiée à la transformation a été introduite dans la version 0.20 : le [ PowerTransformer ](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.PowerTransformer.html#rf3e1504535de-2) . Le but de ce _Transformer_ est de **réduire l’asymétrie** ( _skewness_ ) sur un jeu de données, et ainsi d’ [ approcher une distribution normale ](https://en.wikipedia.org/wiki/Power_transform) , la normalité étant un _a priori_ à l’application de bon nombre d’algorithmes. Deux méthodes sont disponibles pour réaliser la transformation : la [ transformée de Yeo-Johnson ](https://fr.wikipedia.org/wiki/Transform%C3%A9e_de_Yeo-Johnson) et la [ méthode Box-Cox ](https://fr.wikipedia.org/wiki/Transform%C3%A9e_de_Box-Cox) . 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/06/Capture-d’écran-2019-06-06-à-15.04.23.png)

Dans scikit-learn le λ est déterminé automatiquement, pour chacune des colonnes 

###  **Gradient Boosting : où en sommes-nous ?**

Une nouvelle implémentation du _gradient boosting_ , nommée **_Histogram Based Gradient Boosting_ ** , a aussi vu le jour dans les dernières versions. Cette implémentation consiste principalement à agréger les données d’entrée, dans le but d’en faire des paquets de nombres entiers, en amont de l’entraînement. 

Elle présente donc une étape supplémentaire de pré-traitement ( _integer-values bins_ ), qui permet au gradient boosting entraîné a posteriori de bénéficier de structures de données internes spécifiques aux nombres entiers, et donc de s’entraîner plus rapidement. 

Nous notons aussi que cette version : 

  * est **plus rapide à entraîner** que l’algorithme historique de _gradient boosting_ de scikit-learn, et plus **adaptée à de fortes volumétries de données ;**
  * est annoncée plus rapide que XGBoost, et un peu moins que lightGBM ; 
  * voit le jour dans un **nouveau _namespace_ nommé _sklearn.experimental_ ** , qui, comme son nom l’indique, donne accès à des méthodes en cours de définition, qui fournissent par conséquent des garanties limitées en matière de robustesse. 



![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/06/HistBaseImport.png)

##  Notre avis 

Des efforts considérables ont été faits par les équipes de l’INRIA. Néanmoins, les implémentations actuelles des algorithmes de _gradient boosting_ de scikit-learn souffrent toujours d’un manque de pragmatisme, et donc de support face à des problématiques de la vie réelle que nous rencontrons fréquemment en mission chez Quantmetry, parmi lesquelles : 

  * la **gestion de valeurs manquantes** qui n’est pas gérée nativement par l’algorithme de sklearn, mais qui est gérée par lightGBM ; 
  * la gestion des variables contiguës ( **données catégorielles** ) qui, elle, est gérée par _xgboost_ , _lightGBM_ , et bien évidemment _CatBoost._



Nous gardons donc un œil sur les évolutions des méthodes de boosting sur scikit-learn. L’approche par histogramme est élégante et puissante, et pourra sûrement se révéler bénéfique à la communauté. Dans un futur proche, nous continuerons à utiliser des algorithmes plus robustes et plus performants, comme XGBoost, lightGBM et CatBoost (Yandex). 

##  **Imputation de valeurs manquantes**

La plupart des estimateurs présents dans l’écosystème python ne peuvent pas être entraînés sur des jeux de données contenant des valeurs manquantes (le [ _Gradient Boosting Classifier_ ](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingClassifier.html) est un exemple typique). L’approche naïve consiste à remplacer les valeurs manquantes d’une variable par la moyenne/médiane pour des variables numériques, ou par le mode pour les variables catégorielles. Néanmoins, dans de nombreux cas d’usages, ce type de pré-traitement, accessible via le [ SimpleImputer ](https://scikit-learn.org/stable/modules/generated/sklearn.impute.SimpleImputer.html) , limitera les performances du modèle entraîné en amont. De cette limite est née une nouvelle classe, tout aussi simple d’utilisation, qui vise ces cas d’usages spécifiquement : [ IterativeImputer ](https://scikit-learn.org/stable/modules/generated/sklearn.impute.IterativeImputer.html) . Cette méthode d’imputation, inspirée de la bibliothèque R [ MICE ](https://cran.r-project.org/web/packages/mice/mice.pdf) , réalise l’imputation en exprimant tour à tour chaque variable comme fonction de la précédente, via un estimateur. 

Étape par étape, nous avons donc : 

  1. Une **imputation initiale** très simple est effectuée : la moyenne est utilisée par défaut. Nous gardons en mémoire les emplacements des valeurs manquantes. 
  2. Tour à tour — par défaut par ordre décroissant du nombre de valeurs manquantes : Chacune des variables contenant des valeurs manquantes est **exprimée comme fonction des autres variables** , via une régression par exemple ; Les valeurs manquantes sont remplacées via la fonction estimée en a). 
  3. L’étape 2. constituant ce qui s’appelle un cycle, nous répétons un nombre de cycles (paramètre _max_iter_ dans scikit-learn). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/06/MICE.png)

Le jeu de données d’origine  , puis l’  imputation initiale  (moyenne), et le  jeu de données final  après imputation via MICE 

Enfin, nous notons que _MICE_ doit pour l’instant être importé en passant par le _namespacesklearn.experimental_ , tout comme les méthodes de _GradientBoosting_ vues précédemment. 




* * *

##  **_Intelligibilité_ par Guillaume Lemaître **

C’est Guillaume Lemaître qui prend ensuite la parole pour nous présenter les derniers travaux concernant l’intelligibilité. 

_NB : Dans ce chapitre l’intelligibilité est traitée au sens global (explication des variables à l’échelle du modèle), par opposition aux explications locales, qui, quant à elles, tentent d’expliquer les contributions au moment de la prédiction, et pour une entrée donnée._

###  **Importance des variables**

Une approche classique pour évaluer l’impact des variables d’entrée sur l’estimation de la variable de sortie est d’étudier l’importance des variables ( _Feature Importance_ ). 

Dans le cas des modèles se basant sur des arbres (forêts aléatoires, maximisation du gradient …etc.), ce type d’indicateur donne une **mesure de l’impact global des variables** , découvert lors de l’entraînement, et qui traduit le poids de chaque nœud ( _split_ ) dans le modèle. 

Néanmoins, quelques situations bien connues nous amènent à apporter une critique sur cet indicateur. Le cas dans lequel plusieurs variables sont **corrélées entre elles** est un exemple typique. Dans ce cas précis, les variables en question se « partagent » l’importance d’un point de vue global, et leurs importances respectives sont diminuées. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/06/importance.png)

Ici l’expérience et l’âge sont fortement corrélées, ce qui donne des Features Importances plutôt élevées, mais en dessous de la “réalité ». 

Ici, l’expérience et l’âge sont fortement corrélées, donnant ainsi des Features Importances plutôt élevées, mais en-dessous de la « réalité ». 

Le cas extrême serait d’avoir un grand nombre de variables, qui seraient toutes corrélées entre elles, et se partageraient l’importance de manière plutôt équitable. Une analyse naïve amènerait certainement à supprimer toutes ces variables (qui ont respectivement une importance faible), ce qui entraînerait très certainement une forte chute dans les performances du modèle. Une analyse des corrélations semble donc nécessaire … 

###  **L’importance des permutations —** **_permutation importance_ **

Plus récemment, la  _ permutation importance  _ a fait parlé d’elle. Ce type d’approche, historiquement accessible via le package  [ eli5  ](https://eli5.readthedocs.io/en/latest/) , et bientôt  [ directement dans scikit-learn  ](https://github.com/scikit-learn/scikit-learn/pull/13146) ,  **agnostique** du modèle utilisé et donc plus générique que l’importance des variables, consiste à mélanger aléatoirement les valeurs d’une variable avant d’  **évaluer la baisse de performance liée à cette permutation** . Plus robuste et plus générale que la  _ Feature Importance  _ , cette dernière approche ne résout pas complètement les problèmes de corrélations évoqués précédemment, en plus de présenter des différences sur les importances entre le jeux d’entraînements et le jeux de test … 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/06/permutations.png)

Proposition : à choisir entre deux variables corrélées, pourquoi ne pas calculer le delta de  _ permutation importance  _ entre le test set et le train set, et choisir la variable qui présente le delta le plus faible (  _ la permutation importance la plus stable  _ ) ? 

###  **Notre avis**

Il n’y a pas de méthode magique pour expliquer les contributions des variables d’entrée suite à la construction d’un modèle prédictif. Les travaux menés chez Quantmetry par [ Jean-Matthieu Schertzer ](https://www.linkedin.com/in/jean-matthieu-schertzer-23340461/) , ainsi que les récentes missions réalisées, nous montrent que les méthodes qui existent ne sont que des outils, de plus en plus **nécessaires, mais insuffisants à l’explication profonde et complète des contributions** . 

En effet, l’évaluation automatisée des contributions, rendue possible par de nouvelles méthodes ( _Permutation Importance_ étant une de ces méthodes) ne signifie pas que le travail d’intelligibilité s’arrête là. Une analyse plus fine, en partenariat avec les métiers et toujours au regard de leurs cas d’usages, reste nécessaire à la construction d’explications tangibles. 

En pratique, grâce à l’analyse des corrélations et des causalités, nous en apprenons davantage sur le problème à modéliser. Ces analyses nous permettent, entre autres : 

  * de 


