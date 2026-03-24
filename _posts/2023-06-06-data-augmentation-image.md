---
layout: post
title: data-augmentation-image
date: 2023-06-06
url_wayback_machine: https://web.archive.org/web/20230606094012/https://www.quantmetry.com/blog/data-augmentation-image/
---
Computer vision 

06/05/2020 

#  Peu d’images labellisées ? Optez pour la Data Augmentation ! #1 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fdata-augmentation-image%2F&title=Peu%20d%E2%80%99images%20labellis%C3%A9es%20%3F%20Optez%20pour%20la%20Data%20Augmentation%20%21%20%231 "Linkedin") [ ](http://twitter.com/intent/tweet?text=Peu%20d%E2%80%99images%20labellis%C3%A9es%20%3F%20Optez%20pour%20la%20Data%20Augmentation%20%21%20%231&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fdata-augmentation-image%2F "Twitter") [ ](https://www.quantmetry.com/blog/data-augmentation-image/ "Email") [ ](https://www.quantmetry.com/blog/data-augmentation-image/ "Copy Link")

* * *

Temps de lecture : 7 minutes 

![Quantmetry.com : Peu d’images labellisées ? Optez pour la Data Augmentation ! #1](https://quantmetry.b-cdn.net/wp-content/uploads/2020/06/data-augmentation-2.jpg)

_ ✍ [ Arthur Delaitre ](https://www.linkedin.com/in/arthur-delaitre/) & [ Alice Calliger ](https://www.linkedin.com/in/alice-calliger/) _ /  Temps de lecture : 5 minutes. 

Lorsque l’on s’attaque à un sujet de reconnaissance d’image, il arrive très souvent que le jeu d’apprentissage soit petit, voire inexistant. Embêtant quand on sait que les algorithmes d’aujourd’hui raffolent de gros volumes d’images labellisées ! Une des méthodes les plus utilisées pour répondre à ce problème est la Data Augmentation (DA) – comprendre l’augmentation artificielle de la taille du dataset en utilisant des méthodes de manipulation d’image. Cette DA est réalisée en effectuant des opérations modifiant l’aspect de l’image, sans pour autant en modifier la sémantique : par exemple, en diminuant la luminosité, en effectuant une rotation, etc… 

Nous allons voir dans cet article les intérêts de la Data Augmentation, ainsi qu’une procédure de mise en place de cette méthode. Le focus sera fait sur les problèmes de reconnaissance d’images, mais cette méthode peut s’appliquer à de nombreux autres cas d’usages. Deux autres articles feront suite à celui-ci et traiteront de méthodes de Data Augmentation plus complexes : la DA par génération d’images synthétiques et la DA par transfert de style. 

####  Pourquoi augmenter ses données ? 

L’entraînement d’un réseau de neurones profond sur très peu d’images est souvent challengeant : le modèle n’ayant accès qu’à un nombre limité d’observations, il va avoir  tendance à faire de “l’overfitting”, c’est à dire sur-apprendre à partir de l’échantillon d’entraînement, sans pour autant être capable d’émettre des prédictions pertinentes sur de nouvelles images – dans ce cas les performances sont faibles sur l’échantillon de test alors qu’elles étaient bonnes sur les images d’entraînement.  Ce phénomène est bien connu des Data Scientists, qui le résolvent souvent en augmentant la taille du dataset et/ou réduisant le nombre de paramètres du modèle. La première méthode est souvent difficile à mettre en place car le travail de recueil/labellisation de nouvelles observations est laborieux. La seconde possibilité est envisageable pour un problème de reconnaissance d’images, cependant les modèles même les moins complexes peuvent contenir des centaines de milliers de paramètres, donc difficile à réaliser !   
Comme la Data Augmentation permet de générer de nouvelles images labellisées à partir de celles déjà disponibles, c’est une solution relativement facile à mettre en place, et les résultats peuvent être surprenants. 

####  Procédure d’augmentation de données 

De nombreuses bibliothèques Python permettent l’augmentation d’images. Nous allons nous concentrer ici sur l’utilisation d’imgaug [1], une des plus connues et efficaces  (d’autres librairies sont abordées par la suite)  . Elle peut être installée directement avec conda ou pip. Le premier choix qui se pose est la méthode d’augmentation : online, offline ou la combinaison des deux. 

  * Online augmentation: les images sont augmentées en direct lors de l’entraînement du réseau. Elles ne sont donc jamais sauvegardées en mémoire, et le réseau ne rencontre jamais deux fois la même image (car ces augmentations sont aléatoires). Cette méthode permet de s’assurer que le réseau voit des images variées à chaque epoch (cycle d’entraînement complet). Elle est en général appliquée par l’intermédiaire d’un _data generator_ dont on parlera un peu plus tard. 
  * Offline augmentation: les images sont augmentées en amont de l’entraînement. Cela peut être judicieux si un GPU est utilisé, afin que cette étape d’augmentation ne soit pas  le goulet d’étranglement  en termes de temps de calcul. 



![Exemple de flou gaussien](https://quantmetry.b-cdn.net/wp-content/uploads/2020/03/image1.png)

Exemple de flou gaussien. Images issues de la documentation Imgaug 

Une fois la méthode choisie, il est temps de définir en quoi consistera la pipeline de Data Augmentation. Pour cela, imgaug propose de nombreux _augmenters_ . Cela peut être des transformations géométriques, des effets de couleur, de luminosité, de résolution etc. Il suffit de les parcourir et de choisir les plus pertinents pour l’étude.   
Pour de nombreux _augmenters_ , il est possible d’utiliser un paramètre pour définir la magnitude de l’augmentation (la taille du noyau dans le cas d’un flou Gaussien par exemple). 

Une fois les augmentations choisies, on peut les représenter sous forme de pipeline imgaug, en voici un exemple : 
    
    
    
    from imgaug import augmenters as iaa
    
    seq = iaa.Sequential([
    iaa.GaussianBlur(sigma=(0, 2)),
    iaa.Multiply((0.8, 1.2)),
    iaa.Sharpen(alpha=0.5),
    iaa.Sometimes(0.5, iaa.Dropout((0.005, 0.1))),
    iaa.Sometimes(0.1, iaa.weather.Clouds()),
    iaa.Fliplr(0.5),
    iaa.Rotate((-30, 30))
    ], random_order=True)
    
    

Notez ici une fonctionnalité pratique qui permet de calibrer l’usage de certains effets par rapport à d’autres via la fonction “Sometimes()”. Elle permet de préciser la fréquence globale d’utilisation d’un effet. 

Une fois le pipeline définie, imgaug se charge de tout : une méthode permet d’augmenter des images ou batchs d’images. Si des boundings boxs sont définies sur les images, il sera nécessaire de les renseigner pour que les opérations qui modifient la position de l’objet soient répercutées sur la labellisation. 

D’autres librairies connues peuvent être utilisées, par exemple Albumentations[2] ou encore Augmentor[3]. Albumentations est un package basé notamment sur Imgaug, il présente l’avantage d’être un peu plus rapide mais est moins mature que Imgaug, étant plus récent. Augmentor comporte moins de transformations que les deux autres packages. Il apporte essentiellement des transformations affines très paramétrables. Enfin, il est aussi possible d’utiliser la DA déjà intégrée dans les frameworks, comme celle proposée par Keras[4], qui a l’avantage d’être directement disponibles au sein d’un _data generator_ . On peut retrouver l’équivalent en pytorch avec la librairie Torchvision[5]. 

####  Bonnes pratiques 

**Data Generator :** Lorsque l’on réalise de la Data Augmentation, il est souvent utile de créer un objet Data Generator. En effet, les principales bibliothèques de Machine Learning permettent l’utilisation d’un générateur de données pour l’entraînement, ce qui est particulièrement utile lorsque le dataset ne tient pas en mémoire ou qu’on souhaite effectuer des opérations sur les données.   
En keras, la classe _ImageDataGenerator_ [6] peut être utilisée. Elle permet d’appliquer une DA “online”: Les données d’entrée vont être transformées de façon aléatoire et fournies au réseau pendant l’entrainement. Il est important de noter que le réseau ne voit que les images augmentées et non pas les originales.   
Différentes méthodes sont disponibles pour augmenter les images à partir d’un dataframe ou alors directement du répertoire contenant les images. Voici un exemple d’utilisation de la méthode _.flow_from_directory(directory)_ : 
    
    
    
    #Augmentation du dataset de train
    train_datagen = ImageDataGenerator(
    rescale=1./255,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True)
    
    #Creation du data generator de train
    train_generator = train_datagen.flow_from_directory(
    'data/train',
    target_size=(150, 150))
    
    #Entrainement
    model.fit_generator(
    train_generator,
    epochs=50)
    
    

Il est possible de modifier la classe _ImageDataGenerator_ pour y intégrer une DA personnalisée utilisant la librairie Imgaug. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/03/image3-150x150.png)

Même image que précédemment mais trop floue 

**Visualisation :** Il est souvent conseillé de vérifier que l’image augmentée n’a pas été trop détériorée et que l’algorithme est toujours capable d’apprendre de ces images (l’image à droite est trop floue pour que l’algorithme puisse la comprendre par exemple). Toutes les transformations ne sont pas non plus souhaitables : par exemple retourner une image de voiture n’est pas vraiment utile car un modèle ne rencontrera que des voitures avec les roues vers le sol . Il est possible de visualiser les images générées par le data generator afin de s’assurer du rendu de ces images. 

**Introduction progressive :** L’entraînement de réseaux de neurones profonds “from scratch” peut mener à une convergence vers un minimum local de la fonction de coût, pour lequel le modèle a de mauvaises performances. L’introduction progressive d’images augmentées peut aider à entraîner le modèle, car les exemples étant de plus en plus “difficiles”, il commence par apprendre une fonction plus simple et la complexifie au cours du processus. 

####  Pour aller plus loin 

AutoAugment : Learning Augmentation Policies from Data.   
Cet article présente une méthode de recherche automatique de méthode de Data Augmentation en fonction du jeu de données.  Cette approche est intéressante car elle permet d’obtenir la suite de transformations optimales plutôt que le dataset généré, à l’inverse des approches de data augmentation utilisant les GANs, par exemple.  Cette méthode va échantillonner un ensemble de transformations auxquelles sont associés la probabilité d’utiliser cette transformation ainsi que son amplitude. Ces éléments vont être utilisés pour entraîner un réseau qui va prédire une précision R. Elle est renvoyée à un réseau de contrôle (un RNN) qui va actualiser le sous-ensemble de transformations à ré-entraîner. Plus d’informations ici: [ https://arxiv.org/abs/1805.09501 ](https://arxiv.org/abs/1805.09501)

RandAugment : Inspiré d’AutoAugment, il est cependant plus simple dans le sens où il n’utilise pas de méthode de recherche itérative mais un échantillonnage uniforme à partir d’un même sous-ensemble de transformations.   
Plus d’informations ici: [ https://arxiv.org/pdf/1909.13719.pdf ](https://arxiv.org/pdf/1909.13719.pdf)

Références :   
[1] [ https://imgaug.readthedocs.io/en/latest/ ](https://imgaug.readthedocs.io/en/latest/) : Package imgaug   
[2] [ https://albumentations.readthedocs.io/en/latest/ ](https://albumentations.readthedocs.io/en/latest/) : Package Albumentations   
[3] [ https://augmentor.readthedocs.io/en/master/ ](https://augmentor.readthedocs.io/en/master/) : Package Augmentor   
[4] [ https://keras.io/ ](https://keras.io/) : Package Keras   
[5] [ https://pytorch.org/docs/stable/torchvision/index.html ](https://pytorch.org/docs/stable/torchvision/index.html) : Package Torchvision   
[6] [ https://keras.io/preprocessing/image/ ](https://keras.io/preprocessing/image/) : Data Generator Keras 
