---
layout: post
title: comment-intelligence-artificielle-capable-finir-mythique-super-mario-bros-1985
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129164307/https://www.quantmetry.com/blog/comment-intelligence-artificielle-capable-finir-mythique-super-mario-bros-1985/
---
Uncategorized 

19/07/2018 

#  Comment créer une intelligence artificielle capable de finir le mythique Super Mario Bros (1985) ? 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fcomment-intelligence-artificielle-capable-finir-mythique-super-mario-bros-1985%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Comment%20cr%C3%A9er%20une%20intelligence%20artificielle%20capable%20de%20finir%20le%20mythique%20Super%20Mario%20Bros%20%281985%29%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fcomment-intelligence-artificielle-capable-finir-mythique-super-mario-bros-1985%2F "Twitter")

* * *

Temps de lecture : 7 minutes 

![Quantmetry.com : Comment créer une intelligence artificielle capable de finir le mythique Super Mario Bros \(1985\) ?](https://quantmetry.b-cdn.net/wp-content/uploads/2018/07/mario1.png)

Quantmetry est allé à  Mario Neural Network  , un meetup hébergé chez Coddity et présenté par Clément Kérebel _._ C’est au cours d’un POC interne que Clément Kérebel, data scientist chez Coddity, s’est fixé ce défi : concevoir une IA capable de finir le premier niveau de Mario sans intervention humaine. Nous allons pour cela discuter bio-informatique : un savant mélange de biologie (génétique, théorie de l’évolution, mutations) et d’informatique (machine learning, réseau de neurones). 

####  **Quelles sont les pistes possibles pour finir un niveau de Mario ? Qu’est-ce qu’un réseau de neurones ? Quels sont les liens entre la biologie, les algorithmes génétiques et une famille de Mario ? Comment utiliser des algorithmes génériques dans les réseaux de neurones pour atteindre le drapeau final en autonomie totale?**

Dans le but de résoudre le premier niveau, une première idée serait alors de définir un grand nombre de règles basées sur la position de Mario et son entourage. Par exemple : “Si je suis à trois cases d’un trou, je saute”. C’est ce qu’on appelle un  système expert  . Le problème est multiple : si l’on veut que Mario puisse gérer toutes les situations, le nombre optimal de règles serait très important, et ces règles ne seraient pas apprises par Mario mais par un agent humain ! 

Une deuxième solution consisterait à créer une algorithme aux actions aléatoires, mais ce n’est évidemment pas une solution valable, elle a donc vite été écartée. 

Clément Kérebel s’est finalement tourné vers un système adaptatif, c.-à-d. un système qui apprend de ses propres erreurs. Mario saura ainsi, non seulement finir le premier niveau, mais il l’aura appris tout seul, comme un grand ! C’est l’idée sous-jacente à l’apprentissage par renforcement. Chaque décision de Mario peut quand à elle se réduire à un problème de classification : étant donné les informations disponibles, il doit trouver laquelle des deux actions principales (ou classes) est la plus probable pour maximiser un gain (qui reste à définir). 

Avant toute chose, que signifie précisément finir un niveau ? En pratique, il s’agit de jouer, c’est-à-dire de prendre un ensemble de décisions parmi un nombre fini de possibilités. Pour Mario, c’est très simple, il ne sait que courir (action 1), sauter (action 2) ou ne rien faire (action 3). Ainsi, on dira que Mario a joué une partie s’il a effectué une série de courses et de sauts, et qu’il finit le niveau c’est-à-dire s’il atteint le drapeau final. 

Mais alors, quelles sont les informations disponibles ? En première approximation, ce n’est autre que l’image qui apparaît à l’écran lors de la partie. C’est donc un ensemble de pixels codant une couleur ou un niveau de gris. Pour une image de 16×16 = 256 pixels, cela fait donc 256 nombres qui encodent l’information. Chaque pixel peut être simplifié à l’extrême en faisant une correspondance 1 = obstacle physique, 0 = vide. Chaque image est alors uniquement un tableau de 0 et de 1 représentant l’environnement de Mario. 

Par exemple, cette image classique du jeu Mario : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/mario2.png)

Une fois transformé en tableau, sera perçue par le réseau de neurones comme étant : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/mario3.png)

Quid du gain (c.-à-d. la fonction objectif à maximiser) dans cette partie de Mario ? Le gain est tout simplement la distance que parcourt Mario dans une partie : plus Mario va loin, plus le gain est important. 

Donc ça y est, jouer à Mario n’est finalement rien d’autre qu’un problème de classification d’images ! Rien de tel qu’un réseau de neurones pour prendre des décisions. En effet, les réseaux de neurones ont largement fait leurs preuves dans ce domaine, que ce soit pour la reconnaissance faciale ou de  cancers  . Dorénavant, un Mario sera représenté par un réseau de neurones, ni plus ni moins qu’un algorithme qui prend en entrée une image et retourne en sortie une décision ternaire (courir, sauter ou ne rien faire). Qui plus est, un Mario est entièrement caractérisé par la structure de son réseau de neurones : le nombre de couches, le nombre de neurones par couche, et le nombre de liens entre les neurones. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/mario4.png)

Toutefois, pour qu’un tel algorithme fonctionne, il faudrait le nourrir d’images labellisées, enseignant à l’algorithme “là il faut sauter” ou “là il faut courir”. Or, il est extrêmement pénible et fastidieux pour un opérateur humain de s’essayer à ce genre de pédagogie. Il faut donc que Mario apprenne tout seul comme un grand (c’était un des objectifs principaux de Clément Kérebel). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/mario5.png)

Portrait de Charles Darwin, photo : Julia Margaret Cameron 

####  **Comment le faire?**

En faisant appel à la théorie de l’évolution et de la sélection naturelle de M. Darwin ! L’idée est de transformer le jeu en une compétition implacable, où une population initiale de “Mario aléatoires” (c’est-à-dire de réseaux de neurones générés aléatoirement) s’affrontent pour aller le plus loin possible dans le niveau (c.-à-d. survivre). Il s’agit ensuite de faire évoluer cette population initiale de Marios en lui appliquant une pression de sélection, comme dans la nature ! 

Faire évoluer une population de Mario ? Mais qu’est-ce que ça veut dire ? C’est très simple, il n’y a que deux manières de faire évoluer une population : soit on fait muter un individu (on parle de mutation), soit on fait reproduire deux individus parents pour créer un enfant (on parle alors de reproduction ou crossover). 

La mutation, c’est très simple. Pour un Mario, donc pour un réseau de neurones donné, on peut : 

  1. Créer un nouveau lien entre deux neurones 
  2. Créer un nouveau neurone intermédiaire 
  3. Changer le poids des liens existants. Le tout de manière aléatoire. 



Quant à la reproduction, on peut par exemple résumer le réseau de neurones du père (Mario) par une liste de liens entre neurones, résumer de même le réseau de la mère (Maria) par une liste de liens, et concaténer les deux : on obtient un réseau de neurones avec deux fois plus de liens ! Ça commence à faire beaucoup, surtout qu’il y a plusieurs générations qui vont se reproduire ! Alors quand un nouveau petit Mario naît, on divise par deux son nombre de connexions, en taillant dans le tas au hasard. Le nouveau né aura donc quelques connexions héritées de son père, et quelques autres héritées de sa mère, sans oublier toutes les mutations que l’on peut forcer en cours de route. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/mario6.png)

Voilà, la petite famille de Mario prend son essor, la population initiale peut croître, se multiplier et se diversifier grâce aux mutations et reproductions. Hélas, une telle population nécessite des ressources importantes, et il est impossible de garder tous les Marios en mémoire en espérant trouver la perle rare qui finira le niveau ! Il faut donc appliquer une pression de sélection, pour garder un nombre gérable de Marios. Et évidemment, l’objectif est de sélectionner les individus les plus performants à chaque génération, c.-à-d. ceux qui vont le plus loin dans le niveau ! La stratégie de notre orateur : à chaque génération, il ne conserve que les 3 meilleurs individus, et les fait se reproduire entre eux pour générer 15 nouveaux nés. Comme les parents sont triés sur le volet, leurs enfants sont plutôt débrouillards, et certains s’en sortent même mieux que leurs géniteurs grâce aux mutations qu’ils ont subi. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/mario7.png)

Les algorithmes qui se basent sur des générations d’individus sont dits génétiques, en référence à la fameuse sélection naturelle de Darwin. Alors, est-ce que ça marche ? Oui ! Clément Kérebel ne s’est pas privé de faire une simulation en direct de cette méthode : partant de 15 Marios très simples au départ (pas de neurones intermédiaires et des poids aléatoires), nous avons pu constater qu’une vingtaine de générations étaient suffisantes pour obtenir un Mario capable de finir le premier niveau ! Les premières générations sont très peu habiles (car purement aléatoires), mais l’évolution de la population d’une génération à l’autre (reproduction + mutation) ainsi que la pression de sélection (les Marios les moins performants n’ont pas le droit de se reproduire) permettent une amélioration collective et graduelle ! Les mutations/reproductions permettent aux individus d’explorer de nouvelles possibilités (par exemple, sauter en avançant), tandis que la pression de sélection permet de  capitaliser sur la réussite des générations précédentes. 

Dans l’ensemble, ces algorithmes génétiques sont plutôt prometteurs, mais sont gouvernées par un nombre très importants de paramètres (Comment sélectionner les individus ? Combien d’individus par génération ? Combien de mutation ? etc.). De plus, à la manière d’un k-means, il existe des minima locaux renfermant toute une population dans une suite infernale d’échecs. Il faut donc recommencer la simulation plusieurs fois pour espérer trouver un Mario gagnant. Néanmoins, l’avantage considérable des algorithmes génétiques est qu’ils se parallélisent très bien : puisque que chaque individu d’une génération est autonome son parcours peut être calculé sur un processeur séparé. 

Beaucoup d’améliorations sont envisageables après cette première exploration. Notamment, on pourrait complexifier la tâche en incluant les ennemis mobiles dans le jeu, ou améliorer l’algorithme en prenant en compte la vitesse des obstacles. Clément Kérebel a essentiellement utilisé la bibliothèque  Keras  , et projette même de mettre en open-source son environnement basé sur les algorithmes génétiques. 

####  **Une application immédiate ?**

Optimiser les réseaux de neurones d’applications existantes avec des algorithmes génétiques plutôt que des grilles de recherche, ou (encore mieux) apprendre à des  voitures autonomes à conduire  !Un Mario qui joue tout seul ? Mission accomplie ! On passe à  Starcraft  ou à  Dota 2  ? 

✍Écrit par [ Grégoire Martinon ](https://www.linkedin.com/in/gregoire-martinon/) et [ Gaultier Le Meur ](https://www.linkedin.com/in/lemeurgaultier/)
