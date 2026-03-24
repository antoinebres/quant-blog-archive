---
layout: post
title: mobilenet-optimisation-de-la-convolution-pour-les-reseaux-de-neurones-embarques
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129155938/https://www.quantmetry.com/blog/mobilenet-optimisation-de-la-convolution-pour-les-reseaux-de-neurones-embarques/
---
NLP 

04/03/2019 

#  MobileNet, optimisation de la convolution pour les réseaux de neurones embarqués. 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmobilenet-optimisation-de-la-convolution-pour-les-reseaux-de-neurones-embarques%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=MobileNet%2C%20optimisation%20de%20la%20convolution%20pour%20les%20r%C3%A9seaux%20de%20neurones%20embarqu%C3%A9s.&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmobilenet-optimisation-de-la-convolution-pour-les-reseaux-de-neurones-embarques%2F "Twitter")

* * *

Temps de lecture : 6 minutes 

![Quantmetry.com : MobileNet, optimisation de la convolution pour les réseaux de neurones embarqués.](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/article-3-1.png)

####  Introduction 

Aujourd’hui avec l’émergence de l’IoT et des systèmes embarqués, l’IA s’est introduite dans nos vies. Nos smartphones l’utilisent pour améliorer la qualité de nos photos, les voitures autonomes pour comprendre leur environnement. De manière générale, nos systèmes embarqués analysent de plus en plus d’images parfois volumineuses et gourmandes en ressource. 

Les réseaux de neurones et plus spécifiquement les CNN –  _ Convolution Neural Network  _ sont particulièrement appréciés pour la classification d’image, la détection d’objet, de visage et la « fine-grained classification ». Cependant, ces réseaux de neurones effectuent des  **convolutions** : des opérations très coûteuses en calcul et en mémoire. La classification d’image dans les systèmes embarqués représente donc un enjeu de taille dû aux contraintes matérielles. 

Dans cet article, nous étudierons comment la  [ _ Depthwise Separate Convolution  _ ](https://arxiv.org/pdf/1704.04861.pdf) proposée par Google en avril 2017  a permis d’optimiser la convolution en rendant son exécution plus rapide, moins gourmande en mémoire et donc moins consommatrice d’énergie qu’auparavant. Et cela, tout en conservant une bonne précision. 

La  _ D  _ _ epthwise Separable Convolution  _ est par exemple implémentée dans la famille de réseaux de neurones spécialisés en computer vision pour les systèmes embarqués :  [ **MobileNets** ](https://github.com/tensorflow/models/blob/master/research/slim/nets/mobilenet_v1.md) . 

####  La convolution standard dans les CNN 

Pour comprendre comment la  _ Depthwise Separate Convolution  _ a optimisé la convolution, nous allons faire un rappel de la convolution standard tel qu’elle est classiquement utilisée dans les réseaux de neurones à convolution (CNN). 

Un CNN est composé de plusieurs couches, comprenant la convolution, le ReLU, le Pooling, le Flattening, et la Full connection. 

[ ![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/image-1.png) ](https://fr.mathworks.com/solutions/deep-learning/convolutional-neural-network.html)

Afin de déterminer le contenu de l’image, celle-ci passe par deux phases : 

  * La phase de  _ Feature Learning,  _ est composée de plusieurs convolutions successives, et a pour but de faire sortir certaines caractéristiques de l’image. 
  * La phase de  _ Classification  _ , prédit si l’image en entrée est une voiture, un camion, un vélo, etc… 



Une image en couleur est généralement composée de 3 canaux : rouge, vert et bleu. Chaque pixel de l’image est constitué d’une valeur entière comprise entre 0 et 255 sur chacun des canaux. 

La convolution consiste à appliquer un filtre sur l’image. Pour cela un kernel se déplace sur la totalité de l’image d’entrée et agit comme un filtre afin de produire une image en sortie. Le kernel a pour but de  détecter des formes particulières  : 

[ ![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/image-2.png) ](http://timdettmers.com/2015/03/26/convolution-deep-learning/)

Concrètement la convolution est une somme de produits entre les valeurs RGB des pixels et les coefficients du kernel. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/Mar-06-2019-16-10-27.gif)

À chaque passage du filtre  ![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/image-4.png) sur l’image, on calcule une somme de produits entre les valeurs de chaque canal et le kernel. 

Par exemple, le premier calcule réalisé par le kernel est le suivant ![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/image-3.png)

(1*1)+(1*0)+(1*1)+ 

(1*1)+(1*0)+(1*1)+ 

(1*1)+(1*0)+(1*1) = 4  => (ce qui fait 9 multiplications) 

Dans les CNN, la convolution se fait en utilisant plusieurs kernels afin de capturer les particularités de l’image, comme ceci : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/Mar-06-2019-16-12-03.gif)

Nous avons une image en entrée de taille  D  F  ⋅  D  F  et de profondeur  M  ,  (M  étant le nombre de canaux de l’image) et un kernel  K  i  de taille  D  K  ⋅  D  K  ⋅ M  . 

Le kernel  K  i  effectue une convolution sur  **tous les canaux,** l’information est agrégée, on obtient donc e  n sortie une image de plus petite taille  D  G  2  et ayant une grande profondeur de  N  . 

Voici la même convolution, vue d’un angle différent : 

[ https://www.quantmetry.com/wp-content/uploads/2019/03/Animation_1.mp4 ](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/Animation_1.mp4)

####  Depthwise Separable Convolutions 

Dans MobileNet, la convolution est remplacée par une  _ Depthwise Separable Convolution  _ . 

La  _ Depthwise Separable Convolutions  _ s’effectue en 2 étapes : 

  * _ Depthwise Convolution  _


  * Pointwise convolution 



Le terme  _ Separable  _ est lié à l’indépendance entre ces deux étapes. 

#####  Depthwise Convolution : 

La  _ Depthwise Convolution  _ consiste à appliquer un filtre sur chaque canal, contrairement à la convolution classique qui applique un filtre sur l’ensemble des canaux. 

Voici un exemple de  _ Depthwise Convolution  _ : 

[ https://www.quantmetry.com/wp-content/uploads/2019/03/Animation_2.mp4 ](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/Animation_2.mp4)

L’image initiale composée de trois canaux (RGB) subira pour chacun de ses canaux une convolution réalisée par trois kernels différents de taille fixe et de profondeur 1. 

Chaque kernel (ici trois) va générer une image représentant une caractéristique particulière de l’image initiale. On obtient alors en sortie 3 images de plus petite taille.  **La Depthwise convolution n’augmente pas la profondeur de l’image.**

#####  Pointwise Convolution : 

La  _ Pointwise Convolution  _ consiste à combiner les sorties de la  _ Depthwise Convolution  _ , elle est aussi appelée  _ convolution 1×1  _ . 

Voici un exemple de  _ Pointwise Convolution  _ : 

[ https://www.quantmetry.com/wp-content/uploads/2019/03/Animation_3.mp4 ](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/Animation_3.mp4)

Dans cet exemple, un kernel de taille  1 ⋅ 1 ⋅ _M_ réalise une convolution sur les 3 sorties simultanément de la  _ Depthwise Convolution  _ . En utilisant  _ N  _ kernels, on obtient en sortie de la  _ Pointwise Convolution  _ une image de profondeur  _ N  _ .  **La pointwise convolution augmente la profondeur de l’image.**

####  Comparaison –  _ Standard vs Depthwise Separate Convolution  _

Prenons en exemple  une image en entrée de taille DF  2  =5  2  composée de 3 canaux  _M_ = 3  , avec un kernel de taille  D  K  2  * 1 =  3  2  et l’on souhaite obtenir en sortie une image de taille  D  G  2  3  2  et de profondeur  _N_ = 10  : 

* * *

**Convolution Classique**

* * *

Le nombre de multiplications réalisées par opération  =  D  K  2  •  M ** →  ** 3  2  • 3 = 18 ** → ![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/ligne-1.png) ![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/03/linge-1b.png) **

* * *

Le nombre de multiplications réalisées par un kernel sur l’ensemble de l’image  = DK  2  •  M  •  D  G  2  ** →  ** 3  2  • 3 • 3  2  = 243 
