---
layout: post
title: le-football-du-futur-couleur-des-chaussures-big-data-et-strategie
date: 2022-10-01
url_wayback_machine: https://web.archive.org/web/20221001013438/https://www.quantmetry.com/blog/le-football-du-futur-couleur-des-chaussures-big-data-et-strategie/
---
Uncategorized 

07/06/2017 

#  Le football du futur : couleur des chaussures, Big Data et stratégie 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fle-football-du-futur-couleur-des-chaussures-big-data-et-strategie%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Le%20football%20du%20futur%20%3A%20couleur%20des%20chaussures%2C%20Big%20Data%20et%20strat%C3%A9gie&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fle-football-du-futur-couleur-des-chaussures-big-data-et-strategie%2F "Twitter")

* * *

Temps de lecture : 12 minutes 

![Quantmetry.com : Le football du futur : couleur des chaussures, Big Data et stratégie](https://quantmetry.b-cdn.net/wp-content/uploads/2017/06/data-coaching-football.jpg)

Le football est probablement le sport le plus diffusé à travers l’Europe. Avec 380 matchs de Ligue 1 auxquels s’ajoutent les matchs de coupes, de championnats internationaux et les matchs de sélections nationales, ce sont près de 500 matchs diffusés par an (soit plus de 750 heures). Soit 15 000 heures de vidéo pour les 20 dernières années en France, et bien plus lorsqu’on ajoute les championnats étrangers : Angleterre, Allemagne, Espagne et Italie notamment pour ne citer que les grands championnats européens. La masse de données que représentent ces vidéos est donc significative. Et cela, les entraîneurs l’ont déjà compris depuis longtemps. Ce sont aujourd’hui de véritables équipes d’analystes vidéo qui s’attèlent à déceler les points forts et faibles des équipes adverses, à axer les stratégies de jeu et à affiner les recommandations pour les joueurs (Opta Sports par exemple). Sans rentrer dans les détails techniques, la suite de cet article propose une vision globale d’une manière d’automatiser le processus d’analyse vidéo des matchs de football. Enfilez vos crampons et suivez-nous jusqu’en Finale ! 

##  Football et Big Data, un mariage possible ? 

Alors que modèles prédictifs et Big Data sont utilisés en production dans de nombreux domaines, depuis le marketing prescriptif jusqu’à la maintenance prédictive, il semble tout à fait envisageable d’en utiliser les concepts pour l’analyse de dizaines de milliers d’heures de matchs passés. Si on enregistre pour un grand nombre de matchs les positions de chaque joueur et du ballon sur le terrain ainsi que leurs interactions (passes, tirs, interceptions), il serait possible: 

o De réaliser des études statistiques pour des publics divers : l’entraîneur de l’équipe, la presse spécialisée, le grand public, le monde des paris sportifs… 

o De créer des modèles pouvant répondre à la question suivante : Avec telles positions de joueurs et de ballon, quelle action a le plus de chance d’être un succès (passe réussie, dribble, tir etc.) ? Avec quel potentiel pour aboutir in fine à un but ? 

Comment arriver à enregistrer ces positions ? Deux types de solutions se dessinent : (1) Les solutions intégrant l’utilisation d’un tracking device porté par les joueurs (exemples de solutions: Catapult Sports, Benfica) et (2) les solutions détectant les joueurs à partir d’images vidéos de caméras fixes (par exemple les solutions proposées par la Technische Universität München ou Sentioscope). Seulement, il y a un léger soucis : ces solutions sont tout à fait adaptées pour décortiquer les phases d’entraînement (solutions avec tracking device) ou les matchs à domicile (chaque club est libre d’installer son système avec caméras fixes dans son stade). Par contre, elles ne peuvent pas être utilisées sur des images historiques issues de diffusions télévisées. Détecter automatiquement les joueurs à partir de ces vidéos est un exercice qui présente plusieurs difficultés majeures, comme des angles de prise de vue qui varient rapidement (selon la sensibilité du réalisateur et les déplacements du ballon) ou des moyens techniques variables. 

Utiliser la masse historique de données télévisuelles implique donc l’automatisation d’un processus spécifique de traitement et d’analyse des images : 

1\. Détection de la typologie de la captation des images 

2\. Détection des joueurs 

3\. Identification des joueurs 

4\. Détection du ballon 

5\. Identification des limites du terrain et calcul de la position des joueurs et du ballon 6. Etude des interactions entre ballon et joueurs. 

Bref, pour arriver à une base de données historiques des positions de joueurs et ballon et être en mesure de traiter en temps réel les prochains matchs, c’est tout un programme ! 

##  Détection de la typologie de la captation des images 

Cette étape consiste à évaluer quelles images peuvent être utilisées pour détecter les joueurs et leur position : caméra plan large vs. détails d’une action, pages de publicité, images du public, … Plusieurs solutions peuvent être envisagées, par exemple un algorithme de classification à partir de l’histogramme des couleurs des images tel que décrit ci-dessous. Chaque pixel des images de la vidéo contient un valeur d’intensité pour chacune les trois bandes : Rouge, Vert et Bleu. En étudiant la distribution de ces valeurs pour une image complète, on obtient une sorte de signature colorimétrique de l’image : l’histogramme des couleurs, qui peut être utilisée pour une répondre au problème de classification suivant: Quelles sont les images représentant le terrain en plan large, qui permettent de visualiser la position des joueurs sur le terrain? Dans notre cas, on s’attendra à ce que le vues en plan large aient un nombre de pixels “verts” bien supérieur aux autres types d’images. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/1-1-1.jpg)

Exemple d’histogramme des couleurs d’une image. 

Le modèle entraîné pourra alors être en mesure de classer de nouvelles images selon qu’elles sont en plan large (exploitables) ou non. Seuls les images exploitables seront ensuite utilisées pour la détection des positions des joueurs et du ballon. 

Evaluation de la topologie des images vidéo de football. Détections des images en plan large permettant la détection des joueurs et du ballon. Dans cet exemple, seule la première partie de la vidéo peut être utilisée pour détecter les positions des joueurs et ballon. Le gros pas sur le gardien de but n’apport pas d’information. Quantmetry 2017, travaux de développement internes. 

##  Détection des joueurs 

Un joueur de foot est un objet mobile sur un fond vert… en termes d’images vidéos bien entendu. Il s’agit en fait d’amas de pixels variables se déplaçant sur un fond plus ou moins uni, analogue à celui -bien célèbre- du présentateur météo. Et pour détecter les joueurs il suffit de compter ces amas. C’est une première approche simpliste évidemment, mais qui donne des résultats assez intéressants… à condition que les joueurs ne s’agglutinent pas dans une même zone. Dans ce cas la séparation des amas de pixels est rendue difficile. 

Pour plus de précision, un modèle de détection des joueurs devra pour chaque image de la vidéo catégoriser les objets présents. 

Plusieurs méthodes peuvent être alors envisagées : 

– L’utilisation des HAAR Cascade, traditionnellement utilisées pour la détection de visages. 

Cette méthode fut proposée dès 2001 par Viola et Jones (Rapid Object Detection using a Boosted Cascade of Simple Features). Son principal intérêt réside dans sa grande rapidité de classification, d’où son utilisation courante pour l’analyse vidéo. 

Pour l’entraînement d’un modèle de type Haar-Cascade, il faut utiliser un grand nombre d’échantillons d’image « positives » (correspondant à des formes humaines) et un grand nombre d’images « négatives ». Sur une image du jeu d’entraînement, réduite à ses niveaux de gris, il s’agit à faire varier la position et l’échelle d’une fenêtre mobile (« kernel »). A chaque position et échelle sont alors calculées les valeurs de variables explicatives (« features ») en soustrayant la somme des valeurs des pixels du rectangle représenté en blanc par la somme des valeurs des pixels du rectangle représenté en noir. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/2-3-1.png)

_Haar-like features utilisées dans l’algorithme de Haar-classification d’openCV._

_Source :[ http://docs.opencv.org/2.4/modules/objdetect/doc/cascade_classification.html ](http://docs.opencv.org/2.4/modules/objdetect/doc/cascade_classification.html) _

I  l en résulte pour chaque image un grand nombre de « features » (16 000 pour une zone considérée de 24*24 pixels), nombre qui peut être réduit selon l’importance des features pour la classification (détermination de la « feature importance » à l’aide d’Adaboost). 

Ensuite, pour déterminer si un objet avec correspond à une forme humaine, l’algorithme HAAR Cascade utilise des « weak classifiers ». Chaque « weak classifier » utilise un nombre réduit de features (en moyenne 10 et généralement moins de 100) parmi les features les plus importantes. Pour l’évaluation finale, les « weak classifiers » seront appliqués les uns après les autres (c’est la notion de Cascade). Un objet sera alors considéré comme une forme humaine si tous les « weak classifiers » le classent ainsi. Pour plus d’information sur les HAAR classifier, le lecteur est invité à se référer à 

[ ce tutoriel ](http://docs.opencv.org/trunk/d7/d8b/tutorial_py_face_detection.html) . 

–  L’utilisation de HOG Classifier (histogramme de gradient orienté), parfois plus précis que la méthode HAAR Cascade, mais moins rapide. Calculer les gradients orientés d’une image consiste en chaque point à déterminer dans quelle direction les variations de valeur de pixels sont les plus fortes et de quantifier ces variations. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/3-2-2.png)

_ Détermination des directions et valeurs des gradients dans une image  _

_ Source :  [ http://www.learnopencv.com/histogram-of-oriented-gradients/ ](http://www.learnopencv.com/histogram-of-oriented-gradients/) _

A partir de ces directions de gradients et de leurs valeurs il est alors possible de déterminer la signature d’une image en termes de l’histogramme des valeurs des gradients orientés selon leur direction. Chaque classe de l’histogramme correspond à une orientation définie et la valeur de chaque classe correspond au cumul des valeurs des gradients dans cette classe. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/4-2-1.png)

_ Création des histogrammes de gradients orientés.  _

_ Source :  [ http://www.learnopencv.com/histogram-of-oriented-gradients/ ](http://www.learnopencv.com/histogram-of-oriented-gradients/) _

A l’aide d’un jeu d’entraînement comportant un grand nombre d’images « positives » de formes humaines et un grand nombre d’images « négatives » (sans formes humaines), il est possible d’entraîner un classifieur basé sur les histogrammes des gradients orientées (ou HOG). 

Pour des classifications plus rapides, il s’agira de les réaliser en plusieurs temps, en analysant d’abord une image grossière « pixellisée » avant de calculer les HOG de zones plus précises. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/6-1-2.png)

_ Détection des joueurs basé sur un HOG classifier, openCV.  _

_ Quantmetry 2017, travaux de développement internes.  _

– Dernière méthode à envisager : L’utilisation de réseaux de neurones profonds (voir  [ l’article de blog ](https://www.quantmetry.com/single-post/2016/10/18/Le-Deep-Learning-plong%C3%A9e-en-eaux-profondes) de Nicolas Gibaud), standards ou à convolution (voir les articles 
