# intelligibilite-deep-learning-image
Wayback Machine URL: https://web.archive.org/web/20230129165747/https://www.quantmetry.com/blog/intelligibilite-deep-learning-image/
Archive date: 2023-01-29

Computer vision 

21/02/2020 

#  Techniques d’intelligibilité en Deep Learning appliquées à l’image 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fintelligibilite-deep-learning-image%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Techniques%20d%E2%80%99intelligibilit%C3%A9%20en%20Deep%20Learning%20appliqu%C3%A9es%20%C3%A0%20l%E2%80%99image&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fintelligibilite-deep-learning-image%2F "Twitter")

* * *

Temps de lecture : 11 minutes 

![Quantmetry.com : Techniques d’intelligibilité en Deep Learning appliquées à l’image](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/article-bro-min.png)

_✍[ Bastien Roussel ](https://www.linkedin.com/in/bastienroussel/) et [ Michaël Sok ](https://www.linkedin.com/in/micha%C3%ABl-sok-656514a7/) / Temps de lecture : 20 min _

L’enjeu de l’intelligibilité d’un modèle de deep learning est double. Lors de sa conception par le data scientist, la compréhension de l’origine des biais du modèle permet de les corriger et ainsi d’atteindre de meilleures performances mais aussi de le rendre plus robuste. La compréhension du comportement du modèle permet aussi une meilleure acceptation par les métiers qui s’appuient sur ses résultats dans le cadre de leurs activités. Cet article a pour vocation de présenter les principales méthodes existantes pour interpréter des modèles de deep learning appliqués à l’image. 

####  Les techniques de base en intelligibilité des modèles de deep learning 

On peut distinguer deux grandes familles de techniques d’intelligibilité des modèles de deep learning. 

#####  Les techniques de forward propagation : basées sur des calculs de proche en proche depuis l’entrée vers la sortie du réseau neuronal 

En faisant varier chaque entrée indépendamment et en calculant l’impact de cette nouvelle valeur sur la sortie on peut déterminer les entrées qui ont le plus d’importance sur la sortie. 

Ces méthodes sont très intuitives dans leurs approches mais présentent de sérieuses limites. En outre, leur coût en calculs est très élevé puisqu’une forward propagation doit être calculée pour chaque entrée et pour chaque valeur à tester. Elles sont aussi susceptibles de sous-estimer l’importance de certaines entrées qui par leurs contributions saturent la sortie du modèle. 

Pour illustrer le problème de saturation, prenons l’exemple d’un réseau composé de deux entrées ` i_{1} ` et  ` i_{2} ` , d’une couche intermédiaire notée ` h ` et d’une couche de sortie ` y ` comme décrit ci-dessous : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/intelligibilite_1.png)

Source : Article de DeepLIFT 

On remarque que tant que la somme de  ` i_{1} ` et  ` i_{2} ` est supérieure à 1 la sortie vaut 1. Par conséquent, si on fixe ` i_{1}=1 ` et qu’on fait varier ` i_{2} ` de 1 à 0, la sortie sera insensible à cette perturbation. Pourtant, il est clair que ` i_{1} ` a autant d’importance que ` i_{2} ` . 

#####  Les techniques de backpropagation : basées sur des calculs de proche en proche depuis la sortie vers l’entrée du réseau neuronal 

Ces techniques sont beaucoup plus efficientes en terme de calcul puisque l’ensemble des contributions des entrées sont calculées en une seule passe à travers le réseau. 

Une technique classique consiste à calculer la variation de la sortie au voisinage de l’entrée pour chacune de ses dimensions. Pour cela le gradient de la couche de sortie est exprimé en fonction de chaque dimension de l’entrée. Ce calcul est réalisé de proche en proche de la manière suivante : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/intelligibilite_2.png)

Source : article medium [4] 

Dans l’exemple ci-dessus, l’entrée est de dimension 3. Le modèle présente une couche intermédiaire, constituée de 2 nœuds qui opèrent une simple addition des valeurs d’entrée, et d’un noeud de sortie opérant une multiplication des deux sorties produites par la couche intermédiaire. La sortie, notée f, est de dimension 1. 

D’après le principe de dérivation en chaîne on peut calculer la pente de f dans chacune des 3 dimensions de l’entrée au voisinage considéré. Dans ce cas, la dimension d’entrée qui a la plus grande importance sur la sortie est b. 

Bien que ces techniques soient beaucoup moins coûteuses en calculs, elles présentent encore des limites importantes : 

  * Le problème de saturation vue plus haut n’est pas résolu. 
  * La nature discontinue du gradient peut mener à des scores d’importances qui ne traduisent pas le changement infinitésimal de la sortie. 
  * Elles décrivent seulement le comportement local au voisinage d’une entrée qui peut ne pas être représentatif de l’ensemble du dataset. 



Des méthodes plus élaborées adressent les trois limites rencontrées plus haut. 

####  La méthode avancée des gradients intégrés 

La méthode des Gradients Intégrés consiste à attribuer à chaque input un score d’importance basé sur la moyenne des gradients calculés en plusieurs points d’interpolations. Ces points d’interpolations sont définis à intervalles réguliers entre une image choisie comme référence et l’image réelle qu’on a prise en input. Il est courant de choisir comme référence un fond noir ou une image bruitée. 

Dans l’exemple ci-dessous, on part d’une image noire, on l’éclaircit jusqu’à voir nettement le pont de l’image originale. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/intelligibilite_3.png)

Pour chacune de ces images on calcule le gradient pour chaque pixel. Plus la valeur de la dérivée locale est grande en un pixel et plus celui-ci apparaît lumineux dans la série d’image ci-dessous. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/intelligibilite_4.png)

Finalement, les valeurs des gradients sont moyennées ou sommées pour obtenir une contribution relative de chaque pixel. Les pixels ayant le plus contribué à la classification sont ceux qui sont le plus lumineux dans l’image ci-dessus. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/intelligibilite_5.png)

À noter, que puisque la méthode nécessite un calcul du gradient en plusieurs points cela implique un coût de calcul important. 

####  La méthode avancée DeepLift 

DeepLift cherche à expliquer la différence en sortie entre l’input réel et un input de référence en attribuant une contribution à chaque pixel de l’input réel. Ces contributions sont également calculées par backpropagation à l’instar du gradient. 

Contrairement au gradient qui calcule une pente locale, DeepLift calcule une pente entre l’input réel et un input de référence (notée baseline) : 

` \frac{\partial F}{\partial x} = \frac{\partial Y}{\partial x} \frac{\partial F}{\partial Y} \rightarrow \frac{\Delta F}{\Delta x} = \frac{\Delta Y}{\Delta F} \frac{\Delta F}{\Delta Y} `

` slope = \frac{y-y^{baseline}}{x-x^{baseline}} = \frac{\Delta y}{\Delta x} `

L’avantage de cette méthode est qu’elle ne nécessite qu’une seule passe à travers le réseau pour calculer les différentes contributions des pixels d’entrée. 

####  Les méthodes du framework SHAP 

Le framework SHAP propose notamment deux méthodes, implémentées notamment en python, qui dérivent l’une des gradients intégrés et l’autre de DeepLift. 

SHAP calcul des contributions à la prédiction finale pour chaque pixel de l’image d’entrée ou bien chaque pixel d’une couche caractéristique. Le principe sous-jacent est issu de la théorie des jeux en coopération où le problème est de savoir comment redistribuer équitablement le gain entre les membres d’une équipe selon leur contribution. La formule de Shapley permet de répondre à ce problème. 

#####  GradientExplainer 

**GradientExplainer** combine plusieurs idées issues des Gradients Intégrés, de la théorie de SHAP et du SmoothGrad. La technique se base sur l’espérance du gradient pour expliquer les contributions de chaque pixel. Les calculs de l’espérance du gradient pour chaque pixel d’entrée donne une bonne approximation de la valeur de Shap. 

Pour calculer l’espérance du gradient en chaque pixel de l’image d’entrée on se donne un jeu de données de référence. La méthode sélectionne 200 images aléatoirement avec remise parmi ce jeu de référence. Pour chacune des 200 images précédemment tirées, une interpolation uniforme est calculée entre l’image de référence et l’input dont on cherche à déterminer les contributions par pixel. La méthode varie de celle des gradients intégrés puisque la valeur moyenne du gradient est calculée à partir d’images interpolées issues de différentes images de références. La valeur moyenne du gradient ainsi obtenue en chaque pixel est une approximation de la contribution de ceux-ci. 

GradientExplainer offre la possibilité d’utiliser un paramètre supplémentaire appelé le local smoothing qui permet d’ajouter un bruit gaussien à l’input avant de calculer les interpolations. 

L’illustration ci-dessous est un exemple de ce qu’on peut obtenir en sortie de GradientExplainer. Dans le cas présent, les valeurs de shap ont été calculées relativement à 2 classes. Les pixels rouges représentent les pixels qui contribuent à augmenter la probabilité de l’image d’appartenir à cette classe. Inversement les pixels bleus représentent des valeurs de shap négatives. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/intelligibilite_6.png)

#####  DeepExplainer 

**DeepExplainer** est basé sur le même principe que DeepLift. Il diffère néanmoins de DeepLift puisqu’il utilise une série d’images de références pour estimer les valeurs de shap. 

Cette fois-ci les valeurs de Shap sont estimées en moyennant les pentes calculées entre l’input d’entrée et les différentes valeurs de références choisies. 

A noter, plus on prend de valeurs de références et plus l’estimation est précise en revanche le temps de calcul augmente. 

L’affichage des résultats est similaire à GradientExplainer. 

####  Les autres méthodes existantes 

Comme indiqué dans la section 1 de cet article, d’autres méthodes d’intelligibilité existent, reposant principalement sur de la backpropagation ou de la forward propagation plus classique. 

#####  Activation Layers Visualisation (Visualisation des Couches d’Activations) 

Cette méthode d’intelligibilité, est la plus intuitive au sens de réseaux de neurones convolutifs. En effet, si l’on revient à l’essence même de la convolution, cela revient à calculer une somme pondérée de pixels dans un voisinage en suivant un certain noyau. Ces noyaux permettent par exemple de faire de la détection de contours (edge detection) avec des filtres ignorant certains axes. Par exemple, le noyau 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/intelligibilite_7.png)

permet de chercher les contours suivant l’axe diagonal haut-gauche/bas-droite. 

L’objectif du réseau est donc d’entraîner les poids des noyaux de convolution pour ressortir des caractéristiques de l’image pouvant servir à accomplir la tâche, par exemple de la classification d’images. 

L’idée sous jacente de la visualisation des couches d’activations est donc finalement de faire une forward propagation d’une image en input, et de s’intéresser à l’activation des convolutions dans une des couches intermédiaires du réseau [4]. Certaines caractéristiques devraient donc ressortir spécifique à l’image, typiquement les contours de l’objet à clas 
