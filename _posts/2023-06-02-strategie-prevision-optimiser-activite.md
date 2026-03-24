---
layout: post
title: strategie-prevision-optimiser-activite
date: 2023-06-02
url_wayback_machine: https://web.archive.org/web/20230602192154/https://www.quantmetry.com/blog/strategie-prevision-optimiser-activite/
---
Time Series 

23/04/2020 

#  Repenser sa stratégie de prévision et optimiser son activité 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fstrategie-prevision-optimiser-activite%2F&title=Repenser%20sa%20strat%C3%A9gie%20de%20pr%C3%A9vision%20et%20optimiser%20son%20activit%C3%A9 "Linkedin") [ ](http://twitter.com/intent/tweet?text=Repenser%20sa%20strat%C3%A9gie%20de%20pr%C3%A9vision%20et%20optimiser%20son%20activit%C3%A9&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fstrategie-prevision-optimiser-activite%2F "Twitter") [ ](https://www.quantmetry.com/blog/strategie-prevision-optimiser-activite/ "Email") [ ](https://www.quantmetry.com/blog/strategie-prevision-optimiser-activite/ "Copy Link")

* * *

Temps de lecture : 5 minutes 

![Quantmetry.com : Repenser sa stratégie de prévision et optimiser son activité](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/article-gho-min-1.png)

✍ [ Michaël Sok, ](https://www.linkedin.com/in/michaël-sok-656514a7/) [ Martin Le Loc ](https://www.linkedin.com/in/martinleloc/) , [ Jean-François Binvignat ](https://www.linkedin.com/in/jeanfrancoisbinvignat/) , [ Walid Dabachine ](https://www.linkedin.com/in/walid-dabachine-1abb37102/) , [ Guillaume Hochard ](https://www.linkedin.com/in/guillaume-hochard-phd-5580589/) /  Temps de lecture : 5 minutes 

En période de crise, un besoin majeur est de pouvoir s’adapter au marché et d’organiser son activité pour les prochains jours, semaines, mois, en fonction de contraintes nouvelles (chute des ventes, perte de chiffre d’affaire, arrêt de ligne de production, indisponibilité d’acteurs clefs, etc…). Dans ces conditions, les procédures de prévision ainsi que les modèles utilisés sont mises à rude épreuve. En dépit des conditions exceptionnelles il est primordial d’assurer une “continuité” ainsi qu’une “qualité” de service pour non seulement répondre efficacement à l’immédiateté de la crise, mais également pour préparer au mieux le rebond d’activité post crise. En somme, la clé est de pouvoir  **mieux prévoir** pour ensuite  **mieux décider** . 

#####  Mieux prévoir 

Dans cette période caractérisée par un contexte incertain et par donc par l’incertitude de ce que l’on cherche à prévoir, force est de constater que de nombreux modèles de prévision sont actuellement faux et à raison ! 

En effet, ces modèles sont par essence choisis et optimisés pour modéliser des phénomènes sur des historiques de données permettant d’en déduire des évolutions futures. Une déviation très brusque, jamais observée dans l’historique de données, entraînent une déviation des prévisions et donc une baisse des performances prédictives des modèles. Dans ces conditions de crise, des actions sont donc nécessaires pour ré-ajuster le comportement des prévisions. Chez Quantmetry, notre groupe d’expertise en séries temporelles a planché sur le sujet et a identifié quatre types d’actions. 

La première action est de venir corriger les modèles existants en y ajoutant explicitement l’information indiquant l’existence d’une crise. Un réentraînement des modèles est alors nécessaire pour que le modèle prennent en compte l’information. Cependant, selon le cas d’usage et le secteur d’activité, la faible profondeur d’historique, l’horizon de prédiction (prédire dans 2 mois est une tâche actuellement beaucoup plus complexe que prédire ce qu’il se passera demain), la typologie de modélisation et la maille à laquelle est réalisée la prédiction (maille horaire, journalière, mensuelle) peut être un frein à cette solution. 

La seconde action est retravailler si cela est possible la maille de prévision, en proposant des prévisions journalières plutôt qu’hebdomadaires ou mensuelles par exemple. Cela permet d’être plus réactif en temps de crise et de prendre de meilleures décisions en anticipant une aggravation de la situation actuelle ou alors un retournement de tendance. 

Une troisième action possible est de venir renforcer les modèles existants par des modèles statistiques de prévision adaptés à des historiques de prévision courts (quelques dizaines de points suffisent pour obtenir un modèle). La performance ne sera peut être pas aussi bonne que celle obtenue via le modèle en production en période normale, mais bien meilleure qu’un modèle n’ayant pu intégrer le contexte de la crise pour s’adapter et effectuer des corrections. 

Enfin, il est possible de diversifier les prévisions, en se basant sur des hypothèses pessimistes, iso, ou optimistes afin de caractériser l’incertitude du contexte sur les prévisions en sortie. 

**En définitive, l’enjeu majeur autour de la prévision en temps de crise est de pouvoir être plus réactif, pour s’adapter à un contexte changeant rapidement, et de maintenir la confiance dans le processus de prévision en proposant des corrections et adaptation afin de mieux prédire en intégrant les facteurs d’incertitude dans la prévision, pour pouvoir ensuite mieux décider.**

#####  Mieux décider 

La réactualisation des prévisions dans un contexte de crise est donc primordial afin de redonner une visibilité aux activités stratégiques de l’entreprise.  Néanmoins, les contraintes exogènes à prendre en compte, ainsi que les différents scénarios de reprise de crise possibles sont autant de paramètres qui ne peuvent pas toujours être directement intégrés à la construction d’une prévision unique et fiable. Pour répondre à ce problème nous pouvons utiliser l’  **optimisation sous contraintes** . 

**Mais qu’est-ce que l’optimisation sous contraintes ?** Comme son nom l’indique, c’est une méthodologie qui consiste en l’optimisation d’un indicateur (appelée  **fonction de coût** en mathématiques) mais conditionné au fait que d’autres indicateurs (relié au premier indicateur) ne doivent pas dépasser un certain seuil (nos  **contraintes** ). Selon la complexité des équations, nous parlerons donc d  **’optimisation linéaire** (tous les indicateurs sont de la forme  ax + b  ), ou  **non-linéaire** si un des indicateurs ne vérifie pas cette forme (par exemple  a  1  x  \+ b  ). Il existe plusieurs manières de résoudre cette optimisation, cela peut se faire par des méthodes mathématiques dans certains cas précis (contraintes linéaires par exemple) mais demande de nombreux calculs, sont prônes à l’erreur humaine. Dans ce cas-là nous employons souvent des  **solvers** qui permette de trouver la solution. Certains sont adaptés à des optimisations linéaires (par exemple en implémentant un algorithme de  **programmation linéaire** ), d’autres à des optimisations non linéaires (par exemple en implémentant un algorithme de  **branch and bound** ) ou en se servant d’autres heuristiques (par exemple les  **algorithmes génétiques** ). 

Une question peut cependant se poser :  **Comment définir et modéliser ces contraintes ?**

Il faut tout d’abord définir le processus et identifier  **toutes les contraintes appliquées** à ce processus. Par exemple les contraintes peuvent être des coûts de production, des coûts de transports, des coûts de stockage et toute autre contrainte métier. Ensuite, simplifier un problème est souvent la clef pour une optimisation rapide. En effet, plus les contraintes sont complexes, plus la méthode de résolution devient complexe. Il faut donc être  **pragmatique** sur la complexité du problème : quelles contraintes doivent absolument être vérifiées, lesquelles peuvent être simplifiées par une contrainte potentiellement plus restrictive, mais dont la résolution est beaucoup plus rapide. Il faut donc parfois faire des  **compromis** **entre performance et complexité** . 

Ainsi sur la base de prévisions réactualisée, l’utilisation de méthodes d’optimisation sous contraintes devient nécessaire afin d’intégrer les facteurs exogènes et proposer aux décideurs des scénarios optimisés de reprise. Ainsi sur la base d’une prévision de volumes de ventes 2020 réactualisée selon un scénario médian, nous modélisons et appliquons des contraintes de production ainsi que de nouveaux ratio de marge afin de robustifier les simulations budgétaires post-crise. 

En synthèse  , une  **approche complémentaire** à la reprévision  **basée sur l’optimisation sous contraintes** permet de prendre de meilleures décisions en  **ajoutant du réalisme grâce à la modélisation de facteurs impactants complémentaires** (supply-chain, distribution, production) et en  **proposant des scénarios alternatifs de reprise** (redémarrage progressif ou en pic de l’activité, durée du confinement par pays, …). Pour illustrer ces concepts en un exemple concret, celui d’un producteur de vélo qui exporte dans le monde entier, n’hésitez pas à venir au webinar du 23 avril qui porte sur  [ **comment repenser sa stratégie de prévision et optimiser son activité** ](https://app.livestorm.co/quantmetry/reforecast-budgetaire-optimise-sous-contraintes) ! 

#####  ✍Article écrit par [ Michaël Sok, ](https://www.linkedin.com/in/michaël-sok-656514a7/) [ Martin Le Loc ](https://www.linkedin.com/in/martinleloc/) , [ Jean-François Binvignat ](https://www.linkedin.com/in/jeanfrancoisbinvignat/) , [ Walid Dabachine ](https://www.linkedin.com/in/walid-dabachine-1abb37102/) , [ Guillaume Hochard. ](https://www.linkedin.com/in/guillaume-hochard-phd-5580589/)

#### 
