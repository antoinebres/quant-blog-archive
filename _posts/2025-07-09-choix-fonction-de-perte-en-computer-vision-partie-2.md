---
layout: post
title: choix-fonction-de-perte-en-computer-vision-partie-2
date: 2025-07-09
url_wayback_machine: https://web.archive.org/web/20250709231307/https://www.quantmetry.com/blog/choix-fonction-de-perte-en-computer-vision-partie-2/
---
Computer vision, Machine Learning 

12/07/2022 

#  Comment choisir sa fonction de perte en Computer Vision ? - Partie 2 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fchoix-fonction-de-perte-en-computer-vision-partie-2%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Comment%20choisir%20sa%20fonction%20de%20perte%20en%20Computer%20Vision%20%3F%20-%20Partie%202&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fchoix-fonction-de-perte-en-computer-vision-partie-2%2F "Twitter") [ ](https://www.quantmetry.com/blog/choix-fonction-de-perte-en-computer-vision-partie-2/ "Email") [ ](https://www.quantmetry.com/blog/choix-fonction-de-perte-en-computer-vision-partie-2/ "Copy Link")

* * *

Auteur : [ Julian LE GOUIC ](https://www.linkedin.com/in/julian-le-gouic)

Temps de lecture : 6 minutes 

![Quantmetry.com : Comment choisir sa fonction de perte en Computer Vision ? - Partie 2](https://www.quantmetry.com/wp-content/uploads/2022/07/chats-julian.png)

Cet article fait suite au précédent article sur [ Comment choisir sa fonction de perte en Computer Vision ? – Partie 1 ](https://www.quantmetry.com/blog/choix-fonction-de-perte-en-computer-vision/) . Dans celui-ci, nous abordons les deux derniers cas d’usage, à savoir la segmentation sémantique et la segmentation d’instance, toujours avec notre animal favori : le chat 😽 

#  Cas d’usage n°3 : segmenter les chats sur l’image (segmentation sémantique) 

##  Présentation du cas d’usage 

Le cas d’usage de la segmentation sémantique présente de nombreuses similarités avec le premier cas d’usage sur la classification d’image. Dans les faits, au lieu de classifier une image entière, ici nous classifions chaque pixel de l’image. Pour une segmentation binaire, comme ici, la classe opposée à la classe cible est souvent appelée « autre » ou « _background_ » en anglais, puisqu’il s’agit de tout ce qui se trouve « en fond » de l’objet segmenté. ![](https://www.quantmetry.com/wp-content/uploads/2022/07/chaton-2-1024x411.png) À la différence d’une classification d’image, le nombre de prédictions est totalement différent dans ce troisième cas d’usage. En effet, puisque nous allons classifier des pixels et non des images, le nombre de prédictions sera démultiplié en fonction de la taille des images. 

##  Choisir sa fonction 

####  Entropie croisée binaire pondérée (Weighted Binary Cross-Entropy) 

En temps normal, la _binary cross-entropy_ suffit largement à effectuer le travail désiré. Cependant, rappelons-nous que nous sommes dans une classification binaire. Ce qui revient à se dire : « Est-ce que le pixel appartient à ma classe cible ? Oui ou non. ». De ce fait, il risque d’y avoir beaucoup plus de pixels appartenant à la classe _background_ qu’à notre classe cible, créant alors un déséquilibre entre les deux classes. C’est ici que nous introduisons la _weigthed binary cross-entropy_ afin de compenser le déséquilibre entre les deux classes. Elle attribue ainsi un poids plus lourd _β_ aux erreurs faites dans notre classe cible, afin de compenser le faible nombre de prédictions dans celle-ci et ne pas laisser le modèle sur-apprendre la classe _background_ . 

$$WBCE = -\frac{1}{N}\sum\limits_{n=1}^N [\beta y_n\log\widehat{y_n} + (1 – y_n)\log(1 – \widehat{y_n})]$$ 

####  Focal loss 

La _focal loss_ se présente comme une version améliorée de la BCE _(Binary Cross Entropy)_ . Elle lui attribue un poids qui tend vers zéro à mesure que la confiance dans la classe cible augmente, permettant de rééchelonner le résultat de façon dynamique. À contrario de la WBCE _(Weighted Binary Cross Entropy)_ , ce facteur est fait pour donner moins d’importance aux exemples dits « simples » et permet de se **focaliser** sur les exemples plus compliqués. Ce facteur est composé de la probabilité ressortie par le modèle $\widehat{y}$, ainsi que d’un hyperparamètre _𝛾_ : 

$$(1-\widehat{y})^{\gamma}$$ 

Mis bout à bout avec la formule de la BCE, on a : 

$$FL = -(1-\widehat{y})^{\gamma}\log\widehat{y}$$ 

En choisissant un 𝛾 > 0, l’importance donnée aux exemples « simples » est réduite, et inversement. En général, une valeur de 2 pour _𝛾_ fonctionne correctement. 

####  Indice de Jaccard (ou Intersection Over Union) 

L’indice de Jaccard est une mesure utilisée pour comparer la similarité entre deux ensembles. Dans notre cas, les deux ensembles correspondent à l’objet à prédire, et son label. Cette mesure, plus souvent appelée _IoU_ en Computer Vision, vise à donner plus d’importance aux prédictions correctement placées et à pénaliser les prédictions décalées par rapport à leur label. De cette façon, la précision des prédictions du modèle est améliorée. 

$$IoU = \frac{TP}{TP+FP+FN}$$ 

Avec _TP_ , _FP_ et _FN_ représentant respectivement le nombre de pixels en _True Positive_ , _False Positive_ et _False Negative_ . 

####  Coefficient de Dice (ou Dice loss ou F1-Score) 

Le coefficient de Dice ou encore _F1-Score_ , est une variante de l’ _IoU_ présentée précédemment. Les deux fonctions sont corrélées positivement, par conséquent, si un modèle _A_ possède un meilleur score qu’un modèle _B_ selon l’une des deux fonctions, alors il en sera de même pour l’autre fonction. La différence entre les deux fonctions se fera ressentir lorsqu’il y aura généralisation à tout le jeu de données. Au même titre que la _MSE_ _(Mean Squared Error)_ et la _MAE (Mean Absolute Error)_ , là où l’ _IoU_ ( _MSE_ ) aura tendance à pénaliser les grosses erreurs, le coefficient de _Dice_ ( _MAE_ ) aura plutôt tendance à lisser la perte pour en être le moins affecté. 

$$DSC = \frac{2TP}{2TP + FP + FN}$$ 

##  Dans le cas multi-classes/multi-labels 

En segmentation, le multi-classes induit très souvent le multi-labels car il est rare de ne pas avoir les différentes classes mixées dans une même image. Ici, le multi-labels réfère au cas d’une image qui contient des pixels pouvant provenir de plus de deux classes différentes ( _background_ exclu). 

Pour un cas multi-classes, et donc multi-labels, la _weighted binary cross-entropy_ sera encore une fois votre alliée. Néanmoins, il reste possible d’utiliser les autres fonctions telles que _Dice_ ou l’ _IoU_ , en l’appliquant à chacune des classes de l’image prédite, puis en faisant la moyenne (éventuellement pondérée) sur toutes les classes pour obtenir un score final sur l’image. C’est souvent le cas avec l’ _IoU_ , qu’on retrouve alors sous le nom _mIoU_ pour _Mean Intersect Over Union._

##  Pourquoi ? 

En segmentation, il est souvent important que le masque prédit soit suffisamment précis et ne déborde pas trop de sa cible. Pour évaluer cela, les fonctions de perte _IoU_ et _Dice_ sont les plus adaptées car elles prennent en compte la forme de la prédiction. En revanche, le choix entre les deux sera fait par le Data Scientist, en fonction de s’il désire pénaliser plus fortement son modèle lorsqu’il fournit de mauvaises prédictions à une échelle locale ou s’il préfère avoir une pénalisation plus globale sur les erreurs du modèle. 

Le choix de l’une ou de l’autre à la place d’une _focal loss_ ou d’une cross-entropy peut se justifier par le fait qu’il n’est pas nécessaire d’avoir recours à un hyperparamètre pour l’optimisation du modèle. L’introduction de poids dans la _weighted cross-entropy_ ou du _β_ dans la _focal loss_ rend la paramétrisation de la fonction de perte plus délicate. D’une manière générale, la _Dice loss_ est l’une des fonctions de perte les plus utilisées pour une tâche de segmentation sémantique. 

#  Cas d’usage n°4 : détecter et segmenter les chats sur l’image (segmentation d’instance) 

##  Présentation du cas d’usage 

Pour ce quatrième et dernier cas d’usage, nous élargissons le périmètre des précédents cas d’usage et choisissons de faire de la segmentation d’instance sur nos trois petits chats. ![](https://www.quantmetry.com/wp-content/uploads/2022/07/chaton-3-1024x409.png) Comme évoqué précédemment, la segmentation d’instance est en quelque sorte la fusion des trois précédentes méthodes. Quant au choix des fonctions de perte, aussi simple que cela puisse paraître, il sera sensiblement similaire à celui fait dans les autres cas. 

##  Choisir sa fonction 

La segmentation d’instance combine classification, régression et segmentation, il y a par conséquent 3 fonctions de perte différentes à appliquer. Au même titre que lorsque nous avions complexifié le cas d’usage 1 en rajoutant la localisation de l’objet pour faire de la détection d’objet, nous complexifions ici encore une fois la tâche en rajoutant l’instantiation à la segmentation. Puisqu’il s’agit des 3 cas d’usage que nous venons de voir, et pour éviter toute redondance, je vous invite à vous référer à ces derniers pour le choix des fonctions. 

##  Pourquoi ? 

Ici, il n’y a plus de nouveautés, et donc, plus de secrets pour vous ! Pour chacune des branches du modèles, les fonctions de perte disponibles seront les mêmes que celles des cas d’usage présentés précédemment. Cependant, nous avions mentionné que ce cas d’usage était le plus compliqué du fait de la structure des modèles utilisés. Cela se répercute en effet dans les critères de choix des fonctions de perte utilisées. Ces critères dépendront surtout de la structure du modèle ou de l’optimisation des calculs, plutôt que de la nature de la problématique en elle-même (mono-classe, multi-labels, etc…) où les choix respectifs seront finalement plus « triviaux ». 

#  Conclusion 

Vous avez désormais toutes les cartes en mains pour choisir une fonction de perte adaptée pour les cas d’usage les plus classiques de la computer vision. Comme mentionné au début de cette série d’article, toutes les fonctions existantes et tous les cas en computer vision n’ont pas été traités ici. Je traiterai des cas d’usage plus spécifiques et leurs fonctions de perte associées dans un prochain article. En attendant, je vous laisse avec ce diagramme récapitulatif qui, je l’espère, vous sera de bon usage 😉 

![](https://www.quantmetry.com/wp-content/uploads/2022/07/recap-1024x752.png)

_Abonnez vous à notre page[ Quantmetry ](https://www.linkedin.com/company/quantmetry/) pour ne rien manquer de notre actualité ! _

[ ![Computer Vision](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-Computer-Vision.svg) ](https://www.quantmetry.com/experts/#computervision)

Les membres de [ l’expertise Computer Vision ](https://www.quantmetry.com/experts/#computervision) adressent des thématiques couvrant l’ensemble du cycle de valorisation des images : de la constitution du jeu de données à l’implémentation du modèle sur des dispositifs embarqués. 

* * *

![Julian LE GOUIC](https://www.quantmetry.com/wp-content/uploads/2022/07/1618769134881.jpg)

[ Julian LE GOUIC  ](https://www.linkedin.com/in/julian-le-gouic)

Data Scientist chez Quantmetry 

Passionné par le Deep Learning, je me suis très vite spécialisé vers le domaine de la Computer Vision après un double diplôme en Data Science et Informatique & Systèmes intelligents. J’applique aujourd’hui mes compétences dans diverses missions de Computer Vision, mais pas seulement ! 
