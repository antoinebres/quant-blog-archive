---
layout: post
title: exemples-adverses-erreurs-features
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129155215/https://www.quantmetry.com/blog/exemples-adverses-erreurs-features/
---
Time Series 

18/05/2020 

#  Les exemples adverses ne sont pas des erreurs, ce sont des features ! 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fexemples-adverses-erreurs-features%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Les%20exemples%20adverses%20ne%20sont%20pas%20des%20erreurs%2C%20ce%20sont%20des%20features%20%21&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fexemples-adverses-erreurs-features%2F "Twitter")

* * *

Temps de lecture : 10 minutes 

![Quantmetry.com : Les exemples adverses ne sont pas des erreurs, ce sont des features !](https://quantmetry.b-cdn.net/wp-content/uploads/2020/06/erreur.jpg)

✍ [ Michaël Sok ](https://www.linkedin.com/in/michaël-sok-656514a7/) / Temps de lecture : 12 minutes 

Sous ce titre racoleur se cache un article particulièrement intéressant rédigé par Ilyas et al. pour l’édition 2019 de la fameuse conférence scientifique NeurIPS [ [1] ](https://nips.cc/Conferences/2019/) (en anglais  _ Adversarial Examples are not Bugs, They are Features  _ [ [2] ](https://papers.nips.cc/paper/8307-adversarial-examples-are-not-bugs-they-are-features) ). En effet, comme son nom l’indique, cet article se focalise sur le domaine des attaques adverses et pose le postulat que les exemples adverses ne sont pas dépendants d’un modèle en particulier, mais plutôt des  _ features  _ qu’il apprend et qui sont intrinsèques au jeu de données. 

####  Comment définissons-nous les  _ features  _ ? 

Avant d’entrer dans le vif du sujet, redéfinissons ce que nous appellerons par la suite  _ feature  _ . Une  _ feature  _ se définit comme étant une caractéristique intrinsèque du jeu de données qu’un modèle extrait et sur lequel il se base pour effectuer sa prédiction. Par exemple, pour un humain cela pourrait se caractériser par la profondeur d’une image, le contour de l’objet etc. Une définition plus formelle d’une  _ feature  _ est une fonction de correspondance  ` f ` entre l’espace des données en entrée ` X ` et l’espace réel ` \mathbb{R} ` . 

` f : X \rightarrow \mathbb{R} `

Dans le cas particulier d’un réseau de neurones, les _features_ sont les données de sortie de l’avant-dernière couche de ce réseau. Ainsi la sortie de l’intégralité du réseau serait équivalente à celle d’une régression sur ces _features_ : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/adversarial_examples_features.png)

_ Features  _ obtenues par un réseau de neurones quelconque 

Ici, nous avons donc le réseau de neurones  ` g ` qui peut se définir formellement de la manière suivante : 

` g(x) = a\left(w_0 + \sum_{i=1}^{m}w_i f_i(x)\right) `

avec ` a ` la fonction d’activation de la couche finale,  ` f_i ` les différentes  _ features  _ apprises par  ` g ` et  ` w_i ` les poids de la régression utilisés dans la dernière couche de prédiction. 

Il faut donc bien distinguer les  _ features  _ de cet article qui se définissent comme les caractéristiques intrinsèques d’un jeu de données et qui sont pertinentes pour la tâche de prédiction et la définition habituelle du mot “  _ features  _ ” qui est souvent équivalente au sens de variables explicatives. 

####  Que recherchons nous dans une  _ feature ?  _

Il est évident que nous cherchons à ce que les  _ features  _ apprises par notre modèle soit causales, c’est à dire qu’une variation de la dite  _ feature  _ **cause** une variation dans la variable cible. Il est cependant très compliqué de trouver de telles relations et surtout de l’exprimer mathématiquement. Une alternative est d’exprimer la corrélation entre deux variables. L’indice le plus connu pour cela est le coefficient de corrélation de Pearson : 

` \rho_{X, Y} = \frac{\text{cov}\left(X, Y\right)}{V(X)V(Y)} = \frac{\mathbb{E}\left[\left(X-\mu_X\right)\left(Y - \mu_Y\right)\right]}{V(X)V(Y)} `

qui étudie l’existence d’une quelconque relation linéaire entre deux variables  ` X ` et  ` Y ` . Cet indice étant défini, les auteurs de l’article se sont ensuite placés dans un cadre de classification binaire, avec ` y \in \{-1, 1\} ` afin de faciliter les calculs. 

Sous hypothèse faible de variables centrées réduites, nous pouvons donc écrire la corrélation de la manière suivante : 

` \rho_{X, Y} = \mathbb{E}\left[XY\right] `

Et c’est de cette définition que nous allons partir pour écrire les caractéristiques pertinentes pour une  _ feature  _ : 

  * Une  _ feature  _ est pertinente pour accomplir la tâche de prédiction si elle est suffisamment corrélée avec la variable cible. Nous dirons ainsi qu’une  _ feature  _ ` f_i ` est ` \rho ` –  utile si sa corrélation est supérieure à ` \rho ` : ` \mathbb{E}\left[f_i(x)y\right] > \rho ` . 
  * Si une  _ feature  _ ` f_i ` reste pertinente pour accomplir la tâche de prédiction, même lorsque les données d’entrées sont perturbées, alors nous dirons qu’elle est ` \gamma ` – robustement utile. Cela se traduit par une corrélation qui reste supérieure à ` \gamma ` même lors de perturbations sur les données d’entrée selon une stratégie d’attaque ` \Delta ` : ` \mathbb{E}\left[\inf_{\delta \in \Delta(w)}f_i(x+\delta)y\right] ` > ` \gamma ` . 



De par ces définitions, il devient intuitif de penser qu’un modèle robuste à une certaine stratégie d’attaque semble apprendre des  _ features  _ robustement-utiles tandis qu’un modèle classique apprendrait simplement des  _ features  _ utiles qui lui semble hautement prédictives sans a priori sur une certaine stratégie d’attaque. 

####  Que se passe-t-il si nous exacerbons les _features_ robustement utiles ? 

#####  Création d’un dataset « robuste » 

Il existe de nombreux exemples démontrant la “faiblesse” des réseaux de neurones face à des attaques adverses comme par exemple la création d’un patch qui transformerait n’importe quelle classification d’un modèle en grille pain [ [3] ](https://arxiv.org/pdf/1712.09665.pdf) . 

Si nous suivons les définitions précédentes, ce ne serait finalement dû qu’à l’existence de  _ features  _ hautement prédictives mais finalement peu robustes face à des attaque adverses. Pour vérifier ce postulat, les auteurs de l’article [ [2] ](https://papers.nips.cc/paper/8307-adversarial-examples-are-not-bugs-they-are-features) ont essayé de créer un jeu de données permettant d’apprendre des  _ features  _ robustement utiles. Les auteurs se sont servis d’un modèle entraîné par entraînement adverse, dit robuste, et ont exacerbé les  _ features  _ apprises par celui-ci, à la manière d’une méthode de transfert de style  . 

Plus concrètement, Ilyas et al. ont essayé de créer des observations qui ont la  **même représentation** par le modèle robuste que les données d’origine. La méthode consiste en une descente de gradient initialisée par une observation choisie de manière aléatoire. Durant chaque étape de la descente de gradient, les observations sont projetées dans l’espace possible des images. C’est avec ce processus de sélection aléatoire que les auteurs espèrent ne retenir que les  _ features  _ pertinentes pour le modèle robuste sans s’encombrer des potentielles  _ features  _ utiles mais non robustes. 

Le pseudo-algorithme utilisé dans l’article pour obtenir un jeu de données exacerbant les  _ features  _ apprises est le suivant : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/adversarial_examples_pseudoalgo-1.png)

Pseudo-Algorithme pour créer un jeu de données robuste ` D_R `

L’objectif est donc bien de minimiser la représentation d’un modèle robuste entre deux observations choisies de manière indépendante dans le jeu de données. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/adversarial_examples_frog.png)

Exemple de transformation du jeu de données en jeu de données robuste 

#####  Les résultats après entraînement sur le dataset « robuste » 

**E** **n se servant de ce jeu de données robuste** , nous pouvons entraîner un modèle de manière classique et s’intéresser aux résultats. Nous observons alors un modèle à la fois bon sur un jeu de données test suivant une distribution habituelle et qui obtient également des résultats non triviaux sur un jeu de données perturbées par une stratégie d’attaque ! 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/adversarial_examples_results.png)

Résultats sur Restricted-ImageNet avec  un jeu de données de test classique  et  un jeu de données perturbé par attaque adverse  . **À** **g** **auche** avec un modèle entraîné sur le jeu de données d’entraînement d’origine, **au m** **ilieu** avec un modèle entraîné par entraînement adverse sur le jeu de données d’entraînement d’origine et à **d** **roite** avec un modèle entraîné sur le jeu de données constitué par reconstitution des  _ features  _ robustes 

Cela nous apprend que si nous retirons du jeu de données toutes les  _ features  _ utiles mais non robustes (les  _ features  _ ignorées par le modèle robuste), alors un modèle entraîné par méthode standarde sur ce jeu de données ignore aussi ces  _ features  _ . Il est donc peu affecté face à la stratégie d’attaque utilisée pour entraîner le modèle robuste. 

Ce jeu de données est cependant forcément conditionné par l’existence de ce fameux modèle “robuste”. En effet le modèle robuste pré-traite les données de manière à ne laisser en place que les  _ features  _ robustes comme pertinentes. 

#####  Un changement de paradigme 

Cela laisse donc bien supposer qu’un modèle classique apprend des  _ feat  _
