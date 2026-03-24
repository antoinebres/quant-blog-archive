---
layout: post
title: tout-savoir-onnx
date: 2023-01-31
url_wayback_machine: https://web.archive.org/web/20230131105330/https://www.quantmetry.com/blog/tout-savoir-onnx/
---
Uncategorized 

26/10/2018 

#  Tout ce que vous avez toujours voulu savoir sur ONNX 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Ftout-savoir-onnx%2F&title=Tout%20ce%20que%20vous%20avez%20toujours%20voulu%20savoir%20sur%20ONNX "Linkedin") [ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Ftout-savoir-onnx%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Tout%20ce%20que%20vous%20avez%20toujours%20voulu%20savoir%20sur%20ONNX&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Ftout-savoir-onnx%2F "Twitter")

* * *

Temps de lecture : 3 minutes 

![Quantmetry.com : Tout ce que vous avez toujours voulu savoir sur ONNX](https://www.quantmetry.com/wp-content/uploads/2018/10/onnx1.png)

####  Open Neural Network Exchange : Interopérabilité des frameworks 

Comment surmonter les contraintes techniques pour le déploiement en production des modèles ? Fruit d’une collaboration entre AWS, Facebook et Microsoft, ONNX permet le transfert des modèles de deep learning entre différents frameworks 

Aujourd’hui les Data Scientists font face à une multiplicité de frameworks pour le développement d’algorithmes de Deep Learning : Caffe2, PyTorch, Apache MXNet, Microsoft Cognitive Toolkit et TensorFlow. Le choix de l’environnement de travail est souvent régi par des contraintes extérieures et indépendantes du cas d’usage. Une fois la modélisation effectuée dans un cadre spécifique, il est difficile de l’exporter pour l’industrialiser dans un environnement différent. 

Ces nouveaux défis opérationnels qui ralentissent la phase de mise en production ne cessent d’apparaître et de plus en plus de fournisseurs s’efforcent de trouver des solutions pour sortir de l’impasse. 

Facebook a commencé sa collaboration avec Microsoft en septembre 2017 pour lancer ONNX dans le but d’assurer l’interopérabilité de l’écosystème du Deep Learning. Depuis, Amazon Web Services, AMD, ARM, Huawei, IBM, Intel, NVIDIA et Qualcomm se sont joints à l’effort ; plus récemment, Baidu, Bitmain, MediaTek et Preferred Networks y ont également participé. 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/onnx1.png)

Cartographie des frameworks de Deep Learning 

ONNX répond à cette problématique d’export de modèle d’un framework à l’autre et permet de déployer dans un nouvel environnement un modèle entraîné dans un framework spécifique. 

####  Concrètement comment ça marche ? 

Imaginons que vous développez un modèle d’analyse d’image permettant de détecter les humeurs à partir d’expression du visage. Vous décidez d’utiliser une série de photos labellisées pour l’entraînement d’un réseau neuronal convolutionnel (CNN) qui vous permettra de prédire l’humeur d’une personne à partir d’une photo. 

Une fois le modèle entraîné vous souhaitez l’intégrer dans une application IOS afin qu’il soit utilisable sur mobile. Initialement développé avec Pytorch, l’intégration est incompatible avec CoreML le framework d’Apple pour les modèles de machine learning. 

ONNX permet d’effectuer la conversion du modèle au format CoreML en conservant les hyperparamètres et les poids du modèle entraîné. 

Nous présentons une illustration de conversion d’un modèle de pytorch à CoreM issu de cet excellent article de Stefano Attardi sur la construction d’une application iOS intégrant un modèle de machine learning  https://attardi.org/pytorch-and-coreml 

Dans un premier temps le modèle s’exporte au format ONNX qui est une représentation sérialisée du modèle dans un fichier protobuf : 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/onnx2.png)

Puis le modèle est chargé dans ce nouveau format : 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/onnx3.png)

Pour être converti au format CoreML : 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/onnx4.png)

ONNX préserve les paramètres et les hyperparamètres retenus à la suite de la phase d’entraînement. Il facilite également la conversion des types de données d’un framework à l’autre. 

Ce transfert permet d’éviter le processus très coûteux en temps et en GPU de la phase d’entraînement du modèle. 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/onnx5.png)

####  L’écosystème : Quand Google fait bande à part 

L’initiative Open Neural Network Exchange a été lancée par Facebook, Amazon et Microsoft : on remarque que le géant du web brille par son absence parmis ces contributeurs. ONNX a été conçu nativement pour s’interfacer avec la majorité des frameworks à l’exception de TensorFlow de Google (pour lequel il existe un convertisseur tiers). 

Cette configuration semble être le scénario classique où le leader du marché, Google, a peu d’intérêt à renverser sa position dominante et les plus petits joueurs se regroupent pour contrer le gorille. 

Heureusement les dernières versions d’ONNX ont sorti Tf2onnx qui permet de convertir un graphe Tensorflow en graphe ONNX. 

Tf2onnx en est à ses débuts et variera puisque TensorFlow supporte environ 4 fois plus d’opérations que la version ONNX actuelle. Mais les modèles standards semblent utiliser principalement des opérations qu’ONNX supporte. 

Avec l’émergence de framework pour développer des algorithmes de Deep Learning, le besoin de portabilité est plus important que jamais. ONNX est un outil puissant pour permettre l’interopérabilité entre les frameworks et le nombre d’acteurs qui rejoignent la communauté ONNX ne cesse de grandir : on espère voir les contraintes de mise en production des modèles diminuer. 

#####  Références : 

https://www.linuxjournal.com/content/onnx-open-neural-network-exchange-format 

http://www.cuelogic.com/blog/machine-learning-on-ios-and-android/ 

✍Écrit par [ Adèle Guillet ](https://www.linkedin.com/in/ad%C3%A8le-guillet-376a1b84/) et [ Fouad Talaouit ](https://www.linkedin.com/in/fouadtalaouit/)
