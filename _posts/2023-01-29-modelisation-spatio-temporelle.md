---
layout: post
title: modelisation-spatio-temporelle
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129150427/https://www.quantmetry.com/blog/modelisation-spatio-temporelle/
---
Time Series 

27/01/2021 

#  Défis et enjeux de la modélisation spatio-temporelle. 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmodelisation-spatio-temporelle%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=D%C3%A9fis%20et%20enjeux%20de%20la%20mod%C3%A9lisation%20spatio-temporelle.&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmodelisation-spatio-temporelle%2F "Twitter")

* * *

Auteur : [ Jean-François Binvignat ](https://www.linkedin.com/in/jeanfrancoisbinvignat/)

Temps de lecture : 14 minutes 

![Quantmetry.com : Défis et enjeux de la modélisation spatio-temporelle.](https://quantmetry.b-cdn.net/wp-content/uploads/2020/11/jebi.png)

Le traitement de l’information géolocalisée n’est pas récent. La géostatistique naît dans les années 1950 en Afrique du Sud, grâce aux travaux de Danie G. Krige alors ingénieur minier. Le français Georges Matheron formalise les travaux de Krige à partir des années 1960 et consacre sa vie aux géostatistiques. On lui doit notamment le Krigeage (Kriging en anglais), une méthode d’interpolation spatiale utilisée en géologie, climatologie ou en encore météorologie. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/catherine-kriging.png)

Cependant, à l’ère du tout numérique, l’information géolocalisée n’échappe pas au Big Data, que ce soit en termes de diversité de source ou de volumétrie. La technologie, via nos smartphones, est devenue une interface naturelle à notre monde, en s’y confondant presque. Nos usages changent, et nos outils parlent, décrivant nos comportements d’une manière de plus en plus précise. 

Dans cet article nous répondrons à  plusieurs  questions : 

  * **Pourquoi le Big Data est un frein au traitement de l’information géolocalisée ?**
  * **Existe-t-il un continuum du deep learning à la modélisation spatiale et spatio-temporelle ?**
  * **Les pistes prometteuses pour faire de la géostatistique _at scale_ . **



####  **Pourquoi le Big Data est un frein au traitement de l’information géolocalisée ?**

Les méthodes développées jusqu’alors ne passent pas à l’échelle du Big Data, tout simplement. A l’instar des séries temporelles, les méthodes usuelles de géostatistiques viennent s’appuyer sur une analyse des autocorrélations spatiales. Ce qui signifie simplement que lorsque l’on fait des mesures (une température par exemple), elles sont toutes plus ou moins liées entre elles. L’intensité de leur liaison est bien souvent fonction de la distance qui les séparent les unes des autres. 

[ Dans une ressource de l’INSEE, Bouayad Agha Salima et Marie-Pierre de Bellefon donnent la définition suivante à la notion d’autocorrélation spatiale :  ](https://www.insee.fr/fr/statistiques/fichier/3635442/imet131-g-chapitre-3.pdf)

> Les indices d’autocorrélation spatiale permettent de mesurer la dépendance spatiale entre les valeurs d’une même variable en différents endroits de l’espace. Plus les valeurs des observations sont influencées par les valeurs des observations qui leur sont géographiquement proches, plus l’autocorrélation spatiale est élevée. 

Il y a deux différences majeures avec les séries temporelles : 

  1. L’autocorrélation temporelle est unidirectionnelle (passé, présent, futur), quand l’autocorrélation spatiale est omnidirectionnelle (pour un point donné, les autres points sont distribués à 360° degré autour de lui, et à des distances qui varient). 
  2. Le temps est traité généralement de manière discrète, alors que l’espace peut souvent être traité de manière continue. 



Ces deux différences suffisent à rendre quasiment inaccessible les méthodes de traitement des données géolocalisées quand le volume de donnée à traiter est élevé, puisque la complexité algorithmique de la plupart des méthodes exactes est de  Ο(  n  3  )  , ou  _ n  _ est le nombre d’observations. On observe aussi un changement de paradigme : le Krigeage a été initialement développé dans un contexte où le nombre d’observation était faible et où le coût d’acquisition d’une nouvelle observation était élevé (temps, argent), c’est le cas des sondages miniers par exemple. Une volumétrie élevée n’était pas nécessairement le goulot d’étranglement. Aujourd’hui la situation est inversée pour bon nombre de cas d’usage autour de la donnée géolocalisée : le nombre d’observation peut être très élevé, pour un coût d’acquisition faible. 

Nous ne détaillerons pas les approches usuelles de modélisation spatiale, mais vous pouvez trouver d’excellentes ressources si la formalisation mathématique de ces méthodes vous intrigue : 

  * [ Introduction to geostatistics, Geoff BOHLING  ](http://discoverspatial.in/wp-content/uploads/2018/04/IntroToGeostatistics-Geoff-Bohling.pdf)
  * [ An introduction to spatial econometrics, James P.LESAGE  ](https://journals.openedition.org/rei/3887?file=1)



####  **Que vient faire le Deep Learning dans tout ça ?**

L’apprentissage profond est basé sur des réseaux de neurones artificiels. Le concept n’est pas nouveau, puisqu’il date des années 1980, mais pour autant  [ l’utilisation massive d’architectures de réseaux de neurones de plus en plus complexes est relativement récente, et est devenue possible grâce à des ordinateurs plus puissants, et une donnée disponible en masse pour entraîner de tels algorithmes  ](https://www.lemonde.fr/pixels/article/2015/07/24/comment-le-deep-learning-revolutionne-l-intelligence-artificielle_4695929_4408996.html) . Le deep learning a révolutionné l’intelligence artificielle, en s’attaquant avec succès à des sujets de vision par ordinateur (reconnaissance d’image, détection d’objets, segmentation), de traitement du langage (détection de sentiments,  [ extraction d’entités nommées et labellisation de texte  ](https://www.quantmetry.com/labellisation-outils-statistiques-annotation/) ,  [ traduction  ](https://www.20minutes.fr/arts-stars/livres/2351955-20181010-deep-learning-homme-prend-premiere-grosse-raclee-machine-matiere-traduction) ), de traitement audio (classification de son, speech to text,  [ génération automatique de musique  ](https://magenta.tensorflow.org/) ). 

Pour vulgariser, un ensemble de traitement successifs, et adaptés à la nature de l’information traitée en entrée permet de créer une abstraction profonde. Parmi les grandes familles de « couches » (car c’est comme ça qu’on appelle ces traitements successifs) on retient celles qui permettent de traiter des images, par le biais de  [ **convolutions** ](https://colah.github.io/posts/2014-07-Conv-Nets-Modular/) , et celles permettant de traiter des séquences (du texte, des séries temporelles),  [ **Long Short-Term Memory (LSTM)** ](https://colah.github.io/posts/2015-08-Understanding-LSTMs/) et  **Gated Recurrent Unit (GRU)** étant les plus notables. Comme il est possible de combiner ces couches, tous les ingrédients sont réunis pour traiter de l’information spatiale (grâce à la convolution) et de l’information temporelle (traitement d’une séquence). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/fully-connected.png)

Vision d’un réseau de neurone (fully connected). A gauche les entrées (donnée brutes) et à droite les sorties (ce qu’on essaie d’estimer). Les couches intermédiaires sont dites “cachées”. Il s’agit dans ce cas de couches denses, mais il peut s’agir de convolutions ou de LSTM par exemple. 

Ainsi, si le domaine des séries temporelles a été sérieusement abordé par le Deep Learning, l’information spatiale est pour le moment restée assez inexplorée, et aucun standard d’architecture n’a été adopté par la communauté.  [ Les nouvelles problématiques de mobilité liées au smart cities, et le développement de nouvelles offres de service (autopartage, vélos et trottinettes en libre-service)  ](https://www.mckinsey.com/business-functions/sustainability/our-insights/an-integrated-perspective-on-the-future-of-mobility) créent un terrain fertile à la recherche et l’expérimentation de nouveaux algorithmes de Deep Learning, en partie grâce à la volumétrie de donnée générée et à la naissance de tous nouveaux cas d’usage. 

Dans la littérature récente, une architecture a retenu notre attention :  [ Spatial-Temporal Dynamic Network (STDN), proposée par Huaxiu Yao, Xianfeng Tang, Hua Wei, Guanjie Zheng, et Zhenhui Li de Pennsylvania State University, en mars 2018.  ](https://arxiv.org/pdf/1803.01254.pdf) Le papier est intéressant d’une part parce que l’approche est originale, qu’elle est testée sur un jeu de données régulièrement utilisé par la communauté scientifique (NYC Taxi), que le code est disponible sur  [ Github  ](https://github.com/tangxianfeng/STDN) , donc reproductible, et qu’enfin l’architecture est plutôt spécifique à une problématique de mobilité, qui constitue un des enjeux des prochaines décennies et sur lequel nous avons misé chez Quantmetry, en développant un programme R&D sur le sujet. 

#####  **Le problème :**

  * On observe des taxis, à New York 
  * On a des informations géolocalisées sur les départs, les arrivées et les dates associées à chacun de ces deux événements 
  * On souhaite faire des prévisions sur les arrivées et départs en fonction du temps et de la localisation 



#####  **Regardons ce qui fait que cette architecture traite de manière originale le problème :**

  * L’idée majeure est de discrétiser l’espace (la carte de New York) et de créer des zones sur lesquels les séries temporelles sont agrégées. Il y a ainsi autant de séries temporelles que de zones. Le traitement qui en découle est naturel : 
  *     * il est possible de traiter la carte comme une image, où chaque zone représente un pixel et d’y appliquer une convolution. Les auteurs utilisent la convolution non pas directement sur la carte, mais sur un voisinage de chaque “case” représenté par deux matrices carrées, l’une comptabilisant les entrées de zones, l’autre les sorties 



![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/ny.png) ![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/ny-grid.png)
