---
layout: post
title: valeurs-de-shapley
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129150107/https://www.quantmetry.com/blog/valeurs-de-shapley/
---
Data Gouvernance 

11/01/2021 

#  Les valeurs de Shapley en intelligibilité locale des modèles 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fvaleurs-de-shapley%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Les%20valeurs%20de%20Shapley%20en%20intelligibilit%C3%A9%20locale%20des%20mod%C3%A8les&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fvaleurs-de-shapley%2F "Twitter")

* * *

Auteurs : [ Nicolas Peltre ](https://www.linkedin.com/in/nicolaspeltre/) , [ Tangi Salaun ](https://www.linkedin.com/in/tangi-sala%C3%BCn-866689139/)

Temps de lecture : 11 minutes 

![Quantmetry.com : Les valeurs de Shapley en intelligibilité locale des modèles](https://quantmetry.b-cdn.net/wp-content/uploads/2021/01/npe.png)

De plus en plus utilisés par les entreprises, les algorithmes de Machine Learning sont parfois tellement complexes qu’ils se révèlent être de véritables boîtes noires (réseaux de neurones, SVM, forêts aléatoires…). Ces modèles perdent en explicabilité ce qu’ils gagnent en précision. 

Dans certains cas, les applications de ces modèles boîtes noires sont particulièrement sensibles : diagnostics médicaux, octroi de crédit… Pour cette raison, l’Union Européenne a mis en place [ certaines dispositions dans son RGPD ](https://www.gdpr-expert.eu/article.html?id=22#textesofficiels) (Règlement Général pour la protection des données) afin d’obliger les entreprises à expliquer simplement les prévisions des algorithmes d’apprentissage automatique qu’elles utilisent. 

Se pose également la question du **transfert de connaissances de la machine vers l’homme** , pour que l’intelligence artificielle serve également à une plus grande compréhension du domaine d’application. 

Pour répondre à ces enjeux, un nouveau champ de recherche se développe depuis plusieurs années : l’ [ intelligibilité des modèles ](https://christophm.github.io/interpretable-ml-book/) de Machine Learning, que ce soit pour des données tabulaires, du texte ou des [ images ](https://www.quantmetry.com/intelligibilite-deep-learning-image/) . Nous y avons consacré notre [ livre blanc « IA explique toi ! » ](https://www.quantmetry.com/les-livres-blancs/) . 

Dans cet article, nous nous penchons plus particulièrement sur une méthode d’intelligibilité : **les valeurs de Shapley** et leur estimation avec la bibliothèque Python [ SHAP ](https://github.com/slundberg/shap) . 

##  A quel niveau intervient l’intelligibilité ? 

L’intelligibilité vient **après l’étape de modélisation** (celle où l’on construit le modèle prédictif). Cette phase ne fait plus appel à des algorithmes prédictifs entrainés mais à des **algorithmes d’intelligibilité** , pour expliquer les prédictions du modèle prédictif précédemment construit. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/11/capture-decran-2020-11-12-a-192805-1024x476.png)

**Figure 1.** _L’intelligibilité est une étape dissociée de la modélisation_

L’objectif général de l’intelligibilité est de **mieux comprendre les modèles** ou leurs prévisions. Cela consiste à pouvoir expliquer simplement les prévisions d’un modèle. 

On distingue deux types d’intelligibilité : l’intelligibilité locale et l’intelligibilité globale. 

  * **L’intelligibilité** **_globale_ ** cherche à expliquer le modèle dans sa globalité. C’est-à-dire quelles sont les variables les plus importantes en moyenne pour le modèle. 
  * _A contrario_ , **l’intelligibilité** **_locale_ ** , consiste à expliquer la prévision _f(x)_ d’un modèle pour un individu _x_ donné. 



Dans cet article nous nous intéresserons particulièrement à l’intelligibilité locale. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/11/capture-decran-2020-11-12-a-192245-1024x506.png)

**Figure 2** . _L’intelligibilité locale explique la prédiction d’un point, tandis que l’intelligibilité globale explique le modèle dans ses grandes tendances._

##  Une méthode d’intelligibilité locale : les valeurs de Shapley en Machine Learning 

Il existe de nombreux algorithmes d’intelligibilité, souvent empiriques sans beaucoup de justifications théoriques. C’est là l’une des raisons principales pour lesquelles la bibliothèque Python [ SHAP ](https://github.com/slundberg/shap) a été créée en 2017 par Scott Lundberg à la suite de sa publication [1], pour proposer des algorithmes d’estimation des valeurs de Shapley, une méthode d’intelligibilité reposant sur la théorie des jeux coopératifs. 

Depuis son lancement, cette bibliothèque connaît un succès grandissant, notamment grâce à de meilleures justifications théoriques et des visualisations qualitatives. 

Nous présentons ci-dessous le principe général de ces valeurs de Shapley en intelligibilité. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/11/capture-decran-2020-11-15-a-165834-1024x559.png)

**Figure 3.** _SHAP permet de traduire la prédiction d’un individu en explication sous forme de somme de contributions de chacune des variables. Schéma issu du projet_ [ _Github SHAP_ ](https://github.com/slundberg/shap)

Voici un exemple de scénario illustré sur le schéma ci-dessus : un hôpital utilise un modèle prédictif pour calculer une probabilité de décès des patients en fonction de caractéristiques physiques. Sont pris en compte, l’âge, le sexe, la pression sanguine (BP pour “Blood Pressure”) et l’indice de masse corporelle (BMI pour “Body Mass Index”, IMC en français). On suppose que l’algorithme est un modèle boîte noire. 

Le Data Scientist à l’origine de ce modèle souhaite expliquer le résultat obtenu pour une patiente de 65 ans, qui a un IMC de 40 et une pression sanguine à 180. L’algorithme a prédit une probabilité de décès de 0.4. 

Expliquer la prédiction à l’aide des valeurs de Shapley consiste à attribuer à chaque variable d’entrée, plus précisément à chaque valeur décrivant l’individu considéré (“65 ans”, “Femme”, “180” de pression sanguine et “40” d’IMC) un coefficient réel. Chacun de ces coefficients indique comment cette valorisation a contribué à décaler la prévision à 0.4 de la moyenne globale de 0.1 des prédictions. La somme des contributions de Shapley est égale à cet écart : 

(1)  ![\\begin{equation*} 0.4 \(output\) = 0.1 \(base rate\) + 0.1 \(BMI\) + 0.1\(BP\) - 0.3 \(sex\) + 0.4 \(age\) \\end{equation*}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-74e695b919e468802f4da18ae2703871_l3.png)

Sur cet exemple, les valeurs de Shapley nous indiquent que l’individu est à risque en premier lieu à cause de son âge, et dans une moindre mesure à cause de sa pression sanguine et de son IMC qui sont tous deux élevés. 

A _contrario,_ le sexe du patient fait baisser ce risque de décès, sans toutefois le compenser totalement. Les valeurs de Shapley permettent de retrouver l’intelligibilité de modèles plus simples comme les régressions linéaires. 

Pour déterminer ces coefficients, les valeurs de Shapley définies en Machine Learning font appel à la théorie des jeux coopératifs. 

##  Les valeurs de Shapley ou comment répartir équitablement un gain entre plusieurs joueurs dans un jeu coopératif ? 

En théorie des jeux coopératifs, le cadre est le suivant : _n_ joueurs collaborent ensemble et obtiennent un gain _G_ . La question est : comment répartir de manière équitable le gain entre les _n_ joueurs ? 

« Équitable » signifie ici « en prenant en compte la contribution des joueurs dans l’obtention du gain ». Cela veut dire que l’on ne rémunère pas un joueur uniquement pour ce qu’il est capable d’obtenir comme gain lorsqu’il est seul, mais également pour sa **contribution au groupe** , lorsqu’il **interagit** avec les autres joueurs. 

Pour répondre à cette question, on suppose disposer du nombre de **joueurs![n](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-838e41b97e5ef98519bbe6dc5a884d57_l3.png) , ** d’une fonction 
