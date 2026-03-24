# modeliser-analyser-decider-prevision
Wayback Machine URL: https://web.archive.org/web/20230129151124/https://www.quantmetry.com/blog/modeliser-analyser-decider-prevision/
Archive date: 2023-01-29

Time Series 

21/12/2020 

#  Comment mieux modéliser, analyser et décider pour vos cas d’usage en prévision ? 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmodeliser-analyser-decider-prevision%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Comment%20mieux%20mod%C3%A9liser%2C%20analyser%20et%20d%C3%A9cider%20pour%20vos%20cas%20d%E2%80%99usage%20en%20pr%C3%A9vision%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmodeliser-analyser-decider-prevision%2F "Twitter")

* * *

Auteur : [ Alexandre WILLOT ](https://www.linkedin.com/in/alexandre-willot-799585151/)

Temps de lecture : 15 minutes 

![Quantmetry.com : Comment mieux modéliser, analyser et décider pour vos cas d’usage en prévision ?](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/awi.png)

####  Introduction 

#####  Pourquoi l’initiative d’un démonstrateur ? 

La prévision est aujourd’hui une problématique business que l’on retrouve dans toutes les industries. De la prévision de la demande à celle d’indicateurs financiers en passant par la consommation énergétique, tous les domaines se confrontent à des enjeux de prévisions. Les défis techniques liés à ce domaine ne sont quant à eux pas nouveaux. Il existe d’ailleurs dans la littérature une grande variété de méthodes pour prévoir l’évolution d’une série dans le temps, dont certaines ne datent pas d’hier. 

Récemment, à l’ère des « open data », les techniques de prévision ont de nouveau évolué afin de prendre en compte des données externes et ainsi améliorer les prévisions effectuées. 

Face à toutes ces avancées, il est légitime de se demander quel est l’apport de chaque méthode et comment les combiner pour décupler leur potentiel. La question des variables à intégrer pour obtenir de meilleures performances tout en se basant sur des observations pertinentes peut elle aussi se poser. 

Chez Quantmetry, nous disposons d’un pôle composé d’experts en prévisions dont le rôle est justement de répondre au mieux à l’ensemble de ces questions. 

C’est dans ce contexte que, fin 2019, l’ASHRAE (American Society of Heating, Refrigerating and Air‑Conditioning) a lancé un challenge sur la célèbre plateforme Kaggle ( [ https://www.kaggle.com ](https://www.kaggle.com) ) : prévoir la consommation électrique de son parc de bâtiments. 

L’objectif ? Comparer les consommations prévues aux consommations observées après des travaux de rénovation et ainsi mesurer les économies d’énergie réalisées. 

Notre équipe d’experts a décidé de répondre à ce défi en proposant une application permettant notamment de benchmarker un ensemble de modèles de prévision afin de pouvoir sélectionner le meilleur sur le jeu de données considéré. 

De la création de cette application est née l’envie de condenser le savoir-faire de Quantmetry au sein d’un démonstrateur dont le rôle est d’offrir le panel le plus complet possible de nos différenciants en matière de prévision, le tout en trois onglets : **Modéliser, Analyser, et Décider** . 

Dans cet article, nous présenterons notre vision d’un projet de prévision au travers de la présentation du démonstrateur, dont nous détaillerons par la même occasion les différentes fonctionnalités techniques. 

#####  Notre vision d’un projet de prévision 

Utiliser les meilleurs outils pour prédire finement, à la fois localement et globalement, est aujourd’hui un enjeu important pour le domaine, et le Machine Learning et l’Intelligence Artificielle sont alors sans conteste de grands atouts pour y parvenir. 

Bien que la recherche de performance soit un enjeu clé, nous pensons aussi que d’autres éléments doivent être pris en compte pour construire une prévision optimale. Nous jugeons qu’il est important de pouvoir : 

  * Évaluer l’impact de **l’intégration de variables externes** comme les données météorologiques, qui peuvent jouer un rôle non négligeable dans l’amélioration des performances de la prévision. 
  * Fournir **des leviers d’explicabilité** des prédictions faites afin de quantifier l’influence de chaque variable ou comportement dans une décision prise par un modèle. 
  * Intégrer **des degrés de certitude** liés à chaque estimation. En effet, dans de nombreux cas et du fait de l’incertitude liée à chaque prévision, les méthodes classiques de prévision ne sont pas suffisantes pour répondre à une problématique donnée. Les méthodes probabilistes (qui permettent d’intégrer des intervalles de confiance aux prévisions classiques) sont alors plus adaptées pour prédire une fourchette acceptable dans laquelle la valeur réelle sera incluse. Pour aller plus loin dans l’analyse des méthodes probabilistes, on pourra se référer à un autre article de notre blog : [ les prévisions probabilistes avec DeepAR ](https://www.quantmetry.com/blog/previsions-probabilistes-deepar/) . 



Conscients de tous ces besoins, nous avons l’ambition d’apporter une réponse à l’ensemble des enjeux cités grâce à des méthodes et outils performants et sur mesure pour s’adapter à chaque problématique individuelle et ainsi augmenter significativement la valeur ajoutée des projets de prévision de nos clients. 

Pour les accompagner et être un facteur clé de succès de leurs projets de prévision, nous nous appuyons sur 4 accélérateurs : 

Un pôle d’expertise dédié à la prévision parmi l’ensemble de nos **Quanters** .   
Une **Quant Approach** définie par un accompagnement de bout en bout des projets, depuis la phase d’exploration des données jusqu’à la phase de mise en production.   
Une approche algorithmique à l’état de l’art, adaptée à chaque cas d’usage, et que nous perfectionnons toujours plus au sein de notre **Quant Lab** .   
Des **Quant Stories** multi-sectorielles, acquises auprès de dizaines de références. 

####  1\. Contexte 

#####  Les données utilisées 

En nous basant sur les données issues du challenge Kaggle que nous avons relevé, nous prenons l’exemple d’une administration qui souhaite effectuer des travaux sur ses bâtiments afin de réduire son empreinte environnementale. 

Pour mesurer l’impact des rénovations, celle-ci souhaite prévoir la consommation électrique de ses différents bâtiments avant les travaux pour la comparer à la consommation effective après les travaux. 

Nous prenons alors le rôle d’un prévisionniste dont le but serait de modéliser la consommation énergétique du parc de bâtiments pour obtenir les prévisions avant le début des travaux. 

Parmi les bâtiments que nous souhaitons rénover, nous disposons de 4 typologies très différentes dans leur comportement selon le jour de la semaine et l’heure de la journée : une école, une résidence, un parking, et des bureaux. 

#####  Les bases de la prévision de séries temporelles 

Lorsque l’on souhaite effectuer la prévision d’une série temporelle, les principales étapes à suivre sont : 

  * La **séparation de la série en deux** : un jeu d’entraînement sur lequel nous entraînons notre modèle à reconnaître les différents comportements de la série, et un jeu de test sur lequel nous effectuons des mesures de la cohérence de nos prévisions. La date charnière sera appelée la « date de cutoff ». Il est très simple de la faire varier sur notre démonstrateur. 
  * L’ **analyse du jeu d’entraînement** afin d’identifier ses différents comportements notables : la série possède-t-elle des motifs saisonniers ? Une tendance ? Est-ce que des valeurs aberrantes sont présentes et risquent de fausser les prévisions ? 
  * Dans le cas où le jeu d’entraînement comporte des valeurs manquantes ou aberrantes, il est nécessaire d’effectuer un traitement préalable sur les données en appliquant des méthodes d’ **imputation** notamment. 
  * Vient ensuite la **phase de modélisation** , lors de laquelle nous comparons un ensemble de modèles selon différents critères de performance. Une fois le modèle le plus adéquat élu, nous effectuons des tests sur sa robustesse en faisant varier la date de cutoff. 
  * Enfin, une fois les modélisations effectuées, nous étudions l’influence des différentes variables sur le comportement du modèle pour identifier les plus influentes. Nous vérifions aussi l’incertitude liée aux prévisions en analysant l’ **intervalle de confiance à 95%** associé à chaque mesure. 



Voilà, maintenant que nous avons défini les principales étapes à suivre, nous pouvons nous lancer dans leur réalisation avec notre démonstrateur ! 

####  2\. Préparation des données 

#####  Premiers pas dans le démonstrateur 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/1.png)

Une fois le démonstrateur lancé, la première chose à faire est de choisir le bâtiment à modéliser. Nous illustrerons cet article avec les données issues de l’école. 

En observant la courbe de consommation électrique au cours du temps, nous notons la présence de différents motifs de consommation, notamment un **motif quotidien** , couplé à un **motif hebdomadaire** . 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/2.png)

Nous notons aussi la présence de valeurs aberrantes (valeurs proches de 0) dont nous ne connaissons pas l’origine. 

##### 

#####  Traitement des valeurs manquantes 

Comme nous l’avons remarqué précédemment, le jeu de données présente un certain nombre de valeurs proches de zéro. Étant donné l’ordre de grandeur des valeurs prises par la consommation électrique sur les autres intervalles de temps, nous pouvons considérer que ces données proviennent d’erreurs. 

Ce phénomène arrive très fréquemment en pratique et peut s’expliquer par diverses raisons, allant de la panne de capteurs à la mauvaise remontée des mesures (et même parfois pour des raisons inexpliquées). 

Cependant, lorsque nous étudions des séries temporelles comme c’est le cas ici, laisser des mesures aberrantes ou manquantes dans le jeu d’entraînement peut avoir des répercussions néfastes sur les résultats obtenus par les prévisions qui s’en suivent. 

C’est pourquoi il est important d’avoir la possibilité de remplacer ces valeurs par des valeurs plus vraisemblables. On appelle cela **l’imputation** . C’est un sujet prépondérant dans le domaine de la prévision et nous considérons donc qu’il est nécessaire que notre démonstrateur dispose d’une telle fonctionnalité. 

#####  L’imputation sur le démonstrateur 

Nous offrons la possibilité d’imputer les valeurs manquantes ou aberrantes de trois façons différentes : 

  * La première méthode que nous proposons est une méthode assez simple qui consiste à **remplacer les valeurs manquantes par la moyenne sur le jeu d’entraînement** . Cette méthode permet d’éviter d’induire en erreur les modèles de prédiction en supprimant les valeurs éloignées du jeu de données. Elle convient uniquement lorsque la série ne contient qu’un faible taux de valeurs manquantes. 
  * La seconde méthode que nous proposons d’appliquer est la méthode dite d’ **ajustement saisonnal et d’interpolation linéaire** . Son principe est de remplacer les valeurs manquantes par une valeur calculée par la désaisonnalisation de la série, suivie d’une interpolation linéaire et d’une “resaisonnalisation” de cette même série. L’objectif de cette méthode plus avancée est de prendre en compte la saisonnalité et la tendance de la série que nous souhaitons imputer. 
  * Enfin, la dernière méthode que nous avons mise en place est une méthode issue d’un algorithme de Machine Learning : le **Gradient Boosting** . Ce modèle sera aussi proposé en tant que modèle pour la prévision et il possède la particularité de s’appuyer sur les variables externes de la série et non sur ses comportements temporels comme c’était le cas pour les méthodes précédentes. 



Les deux dernières méthodes ont l’avantage d’être plus robustes, ce qui se ressentira notamment lorsque le taux de valeurs manquantes augmentera. 

Nous donnons à titre d’exemple les prévisions effectuées par un même modèle mais avec une imputation par ajustement saisonnal et interpolation linéaire dans un cas ( _Modèle 2_ ) et sans imputation dans l’autre ( _Modèle 1_ ). Nous voyons clairement que le comportement adopté par la courbe rouge (creux soudains de consommation) n’est pas un comportement attendu et a été causé par la présence de valeurs anormales. Le second modèle a pu corriger ces erreurs grâce à l’imputation. 
