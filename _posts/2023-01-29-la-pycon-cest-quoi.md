---
layout: post
title: la-pycon-cest-quoi
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129152853/https://www.quantmetry.com/blog/la-pycon-cest-quoi/
---
Uncategorized 

30/11/2016 

#  La PyCon, c'est quoi ? 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fla-pycon-cest-quoi%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=La%20PyCon%2C%20c%27est%20quoi%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fla-pycon-cest-quoi%2F "Twitter")

* * *

Temps de lecture : 13 minutes 

![Quantmetry.com : La PyCon, c'est quoi ?](https://quantmetry.b-cdn.net/wp-content/uploads/2016/11/screen-shot-12-30-18-at-02-00-pm.jpg)

La PyCon, c’est LA conférence de référence sur le langage Python. On y trouve nombre de professionnels (développeurs, chercheurs, entrepreneurs…), des étudiants ou simplement des amateurs éclairés, tous réunis par une même passion pour ce langage. 

Originaire des Etats-Unis (comme toujours), la PyCon s’est progressivement développée dans plusieurs régions du monde, et notamment en France depuis quelques années. 

Une équipe de chez Quantmetry s’est donc rendue à l’édition française de la Pycon 2016, qui s’est tenue à Rennes le week-end du 15 Octobre. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-02.01-PM.jpg)

Une édition particulièrement intéressante pour nous, puisque, cette année, une grande partie des conférences étaient consacrées à des sujets autour du traitement de la donnée et du machine learning; preuve s’il en faut de la place de plus en plus importante qu’occupe le langage Python dans l’écosystème Big Data. 

Les deux premières journées étaient consacrées à des sessions de “sprints”, c’est-à-dire des ateliers où des participants se réunissent pour participer intensivement au développement d’un projet informatique : débogage, développement de nouvelles features ou d’interfaces, tests de l’application… 

Nous avons dans le cadre de ces sprints contribué à deux projets : “Mesure Environnementale de la qualité de l’Air” et “Mapping Learning la Cartographie Assistée”. Nous avons consacré la journée du samedi aux conférences. 

Les deux dernières journées consistaient en un ensemble d’ateliers et de conférences, dont deux étaient animées par les Quantmetry Vincent et Pierre. 

##  Les sujets tendances: machine learning, performances, et web 

La conférence a attiré un grand nombre de personnes puisque nous étions plus d’une centaine le vendredi et entre 300 et 400 le samedi. Les grands thèmes des conférences étaient les suivants : 

  * Le traitement de données et le machine learning en Python 

  * Le cœur du langage avec des présentations sur les fonctions avancées natives de Python et même parfois leur fonctionnement interne (implémentation CPython, f-strings, mécanisme d’imports, asyncio, etc.) 

  * L’exécution asynchrone de code, notamment grâce à la nouvelle fonctionnalité de Python asyncio 

  * Et bien sur le web, où Python est très présent (Django, WebPush, programmation des navigateurs à l’aide de Python, etc.) 




##  Sprints 

Nous avons participé aux sprints consacrés aux deux projets décrits ci-après 

###  Mesure environnementale qualité de l’air 

####  Contexte 

L’initiateur de ce sprint est le propriétaire d’une boutique d’électronique à Paris. 

Il est parti du constat qu’il n’existait pas de dispositif de mesure de la qualité de l’air précis et en même temps abordable par le grand public. 

####  Objectifs de la solution 

Son idée est d’utiliser des briques logicielles open source et du matériel électronique communément utilisé dans le monde du Do It Yourself pour concevoir le premier kit de mesure de la qualité de l’air performant et abordable. 

####  Le projet concrètement pendant le sprint 

Le projet était déjà commencé avant la PyCon, la solution se composait d’une carte Raspberry Pi à laquelle était connectée de multiples capteurs et sur laquelle était installée le logiciel open source Home Assistant. Ce logiciel était utilisé pour restituer les données des capteurs via une interface web 

Pendant le sprint l’équipe a travaillée sur trois axes différents : 

  * Ajouter la prise en charge de nouveaux capteurs 

  * Envoyer les données mesurées par chaque dispositif dans le « cloud » afin de pouvoir effectuer des traitements plus généraux 

  * Améliorer la visualisation des données qui était très basique car elle s’effectuait à travers l’interface web de Home Assistant originellement crée pour la domotique. 




J’étais en charge de l’envoi des données sur le cloud, j’ai alors développé un petit module Home Assistant qui envoyait les données sur un serveur d’API REST, basé sur Django, qui enregistrait les données en base MySQL. 

####  Bilan 

Cette expérience a été très intéressante car elle m’a permis de m’immerger dans un projet IoT traitant d’un vrai sujet d’intérêt général. J’ai pu découvrir les nombreuses problématiques liées aux capteurs dans ce domaine, notamment le bruit et la dérive dans les mesures. Et enfin il a été très satisfaisant de voir qu’en un temps aussi court nous avons réussi à : 

  * Envoyer les données dans une base de données MySQL via un Web Service basé sur Django 

  * Intégrer deux nouveaux capteurs 

  * Développer une page Web requêtant Home Assistant et présentant les courbes sous forme de Dashboard 




##  Mapping learning 

####  Contexte 

Mapping learning est un projet développé par un ingénieur d’études en cartographie dans le laboratoire universitaire de Rennes RMT LETG Rennes-Costel (Climat et Occupation du sol par Télédétection). 

Le laboratoire regroupe principalement deux types de profils : 

  * D’une part, des géographes, plus ou moins compétents dans le domaine du traitement du signal / du machine learning, etc. 

  * D’autre part, des informaticiens, des spécialistes du traitement du signal et de la donnée. 




Cet ingénieur a fait les constats suivants : 

  * les géographes manquent de compétences techniques permettant d’appliquer des techniques de traitements du signal et d’images avancés 

  * les outils du marché sont très limités. Ils coûtent chers et ne couvrent qu’un ensemble très réduit de fonctionnalités 

  * La communication des informaticiens avec les experts dans ces domaines est souvent compliquée, car ces derniers n’ont pas la connaissance métier nécessaire pour manipuler efficacement les données des géographes. 




####  Objectifs 

Son projet, Mapping Learning, a pour vocation de mettre fin à l’étanchéité qui existe entre ces deux mondes dans son laboratoire. L’objectif est de développer une boîte à outils mettant à disposition un ensemble de méthodes de machine learning applicables au traitement de données cartographiques (télédétection, images satellites, signaux divers, etc), afin de faciliter la vie des géographes et d’optimiser leurs analyses. 

####  Le projet concrètement 

Maplearning est une application full Python, de taille et de périmètre aujourd’hui encore relativement modestes: 

  * Environ 5000 lignes de codes 

  * pas d’interface graphique à proprement parler : l’application gère seulement la génération automatique de rapports html. 

  * Des tests unitaires, mais pas encore complets. 

  * Prise en charge en inputs des formats classiques utilisés en cartographie / télédétection (shp, dbf, shx, etc) 

  * Une dizaine de fonctionnalité implémentées : quelques fonctions de clustering et de régression / classification (lda, arbres de décisions, knn), le tout basé sur scikit learn. 




####  Bilan 

Cette expérience était vraiment enrichissante, le format du « sprint » s’est clairement révélé efficace pour brainstormer et produire du code efficacement. Il est réellement stimulant de voir ce qu’on peut développer en seulement deux jours avec une petite équipe de développeurs motivés. A l’issue de ces deux jours, l’application : 

  * fonctionnait (i.e : passait tous les tests) sur Windows, Linux, et Mac (alors qu’elle ne fonctionnait que sur Linux initialement) 

  * était compatible Python 3 (alors qu’elle n’était compatible que Python 2 au départ) 

  * avait été enrichie de plusieurs fonctionnalités de machine learning (nouveaux modèles de classification, nouvelles métriques de performance, etc) 

  * disposait d’un fichier setup.py permettant l’installation et le lancement du projet. 

  * disposait maintenant de prototypes d’interfaces un peu plus alléchantes que de sobres rapports HTML. 




Pour terminer, voici une démonstration de l’ambiance studieuse et masculine qui a régné pendant cette journée de sprint : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/sprint_map_mapping.jpg)

##  Conférences orientés machine learning [Conférence longue – 1] Deep learning en Python 

La conférence Deep Learning était donnée par un ingénieur aéronautique. La première partie de son intervention reprenait les grandes lignes du deep learning : histoire, idées et principes théoriques, applications, etc. Il s’agissait plus d’une introduction au sujet que d’une conférence d’approfondissement. Les exemples d’applications les plus célèbres du Deep Learning y étaient présentés : 

  * voiture autonome 

  * alpha Go 

  * sous titrage automatique 

  * traduction automatique 

  * etc 




Cette première partie s’adressait clairement à public néophyte sur le deep learning, voire néophyte sur le machine learning en général. 

La deuxième partie, plus technique, présentait l’écosystème Python autour du deep learning. La bonne nouvelle, c’est que celui-ci s’est bien enrichi ces dernières années, et il existe aujourd’hui des bibliothèques dont les interfaces sont simplifiées, et qui permettent de prendre le sujet en main beaucoup plus facilement. 

Petite histoire simplifiée de l’écosystème Python Deep Learning 

####  Hier 

Il y a quelques années, si on voulait développer des réseaux de neurones profonds en Python, il fallait utiliser Theano. Theano est une excellente librairie Python qui permet de faire du calcul symbolique efficacement. Pour résumer, il s’agit d’entrer manuellement les objets mathématiques de notre réseau de neurones (fonctions d’activation, fonctions de combinaison, ou encore la fonction de coût) et Theano calcule ensuite et optimise les expressions en entrée (calcul du gradient de la fonction de coût par exemple), puis compile le tout. Cette compilation peut se faire : 

  * en C (pour faire tourner le modèle sur un CPU) 

  * en CUDA (pour faire tourner le modèle sur des GPUs (dix fois plus rapide) 




Theano fonctionne très bien, a de très bonnes performances en termes de vitesse, mais est un peu laborieux à prendre en main. Il faut définir des variables symboliques, veiller à bien les typer, définir des expressions à partir de ces variables dans une syntaxe propre à Theano, etc. Le développement et le débogage peuvent être longs et il y a réellement un coût d’entrée non négligeable. 

####  Aujourd’hui 

Aujourd’hui, nous vivons dans un monde meilleur, où l’amour et les réseaux de neurones profonds sont à la portée de tous, grâce à de nouvelles bibliothèques simples et efficaces : 

  * TensorFlow: c’est une librairie développée par Google, et qui fait globalement la même chose que Theano : du calcul numérique grâce à des graphes d’opérations. TensorFlow dispose d’une API Python assez haut niveau. En clair, vous pouvez en quelques heure développer un petit réseau de neurones simple avec TensorFlow. 

  * Keras : A l’origine, Keras était une surcouche de Theano, permettant d’offrir une API de plus haut niveau à ceux qui ne voulaient pas s’embêter avec Theano et désiraient pouvoir construire rapidement un modèle. Keras a par la suite ajouté la possibilité d’utiliser TensorFlow au lieu de Theano en “back” (le fait que le développeur de l’application travaille chez Google y est peut-être pour quelque chose …). Je ne connais personnellement pas du tout cette librairie, mais d’après le speaker, elle est réellement bien faite et facile à prendre en main. Il a d’ailleurs terminé la conférence en montrant un bout de code permettant de construire un réseau tout simple et de lancer un entrainement (une sorte de “Hello Word” du Deep Learning) : le résultat, sans compter la préparation des données, tenait en une dizaine de ligne (on est bien loin du “Hello Word” de Theano !) 




##  Theano vs TensorFlow ? 

Plusieurs questions ont porté sur les différences de performance entre Theano et TensorFlow. Selon le speaker, la machinerie derrière ces deux librairies est très similaire, et elles reposent d’ailleurs un grand nombre de bibliothèques communes. Donc, d’après lui, pas besoin de se poser la question à moins d’avoir un problème très spécifique, ou que la performance soit vraiment un critère essentiel. 

##  Atelier : Introduction à Théano 

#####  ![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/tp_theano.jpg)

En complément à la formation théorique, une séance de TP a été consacrée à une introduction à Théano. 

La séance était très intéressante car menée par un étudiant en thèse donnant déjà des TP sur ce sujet. L’intervenant est alors venu avec des notebook IPython sur lesquels nous avons expérimenté Theano en implémentant des algorithmes de régression logistique et linéaires. Très bonne séance pour mettre le pied à l’étrier avec cette bibliothèque avancée qui demande une approche un peu particulière dans la structuration du code et des algorithmes. 

##  [Conférence longue – 2] Modélisation Inférence et apprentissage de réseaux Bayesiens avec PyAgrum 

Conférence très intéressante qui présentait PyAgrum, une bibliothèque Python qui permet de créer et d’entrainer des réseaux bayésiens. 

###  Les réseaux bayésiens c’est quoi ? 
