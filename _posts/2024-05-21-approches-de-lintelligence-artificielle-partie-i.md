---
layout: post
title: approches-de-lintelligence-artificielle-partie-i
date: 2024-05-21
url_wayback_machine: https://web.archive.org/web/20240521212358/https://www.quantmetry.com/blog/approches-de-lintelligence-artificielle-partie-i/
---
Uncategorized 

17/04/2018 

#  Approches de l’intelligence artificielle - Partie I 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fapproches-de-lintelligence-artificielle-partie-i%2F "Linkedin") [ ](http://twitter.com/intent/tweet?text=Approches%20de%20l%E2%80%99intelligence%20artificielle%20-%20Partie%20I&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fapproches-de-lintelligence-artificielle-partie-i%2F "Twitter") [ ](https://www.quantmetry.com/blog/approches-de-lintelligence-artificielle-partie-i/ "Email") [ ](https://www.quantmetry.com/blog/approches-de-lintelligence-artificielle-partie-i/ "Copy Link")

* * *

Temps de lecture : 6 minutes 

![Quantmetry.com : Approches de l’intelligence artificielle - Partie I](https://www.quantmetry.com/wp-content/uploads/2018/04/artcile3.jpg)

Ceci est le premier d’une série de deux articles sur le domaine de l’intelligence artificielle, qui permettra, je l’espère, d’ouvrir les lecteurs aux approches autres que le machine learning ! 

####  **INTRODUCTION**

Définir de manière précise et définitive à quoi correspond l’intelligence artificielle (IA) est une tâche ardue, voire impossible. On désigne généralement par ce terme l’ensemble des techniques permettant d’intégrer des comportements intelligents dans une machine. Les conditions nécessaires à la création d’une telle machine mobilisent ainsi des domaines de connaissance aussi variés que la robotique, la biologie, le traitement du signal, la logique, la statistique, ou encore l’optimisation sous contraintes. 

Le débat sur la définition d’un comportement intelligent et les moyens de le reproduire sont vifs au sein de la communauté des chercheurs : Peut-on formaliser des principes logiques simples expliquant les comportements intelligents ? L’intelligence peut-elle être reproduite via des manipulations symboliques ? La connaissance de la biologie humaine ou animale est-elle nécessaire à la compréhension de l’intelligence ? Autant de questions à propos desquelles aucun consensus n’a émergé ces dernières décennies, tant le sujet de l’intelligence est complexe. 

Mais l’on peut néanmoins définir quelques paradigmes qui guident les chercheurs en informatique dans leurs travaux : la cybernétique comme approche historique, puis les approches symbolique et sous-symbolique à partir des années 1950. 

####  **LES DIFFÉRENTES APPROCHES DE L’IA**

La cybernétique est un terme proposé en 1947 par le mathématicien américain Norbert Wiener pour désigner une vision unifiée de l’automatique, de l’électronique et de la théorie de l’information de Shannon. Son étymologie renvoie à la notion de pilote, ou de gouverneur, exprimant ainsi son objectif d’étude de l’information et de sa structure dans les interactions entre systèmes. 

Le paradigme cybernétique est basé sur quelques concepts clefs très simples : 

  * La boîte noire, qui est un système dont « on décide » d’ignorer le fonctionnement interne mais dont on connaît la fonction d’association entre entrée et sortie 

  * L’émetteur, qui envoie une information vers son environnement 

  * Le récepteur, qui intègre des informations depuis son environnement 

  * L’émission, la transmission, et la réception de l’information comme flux 

  * La rétroaction comme information de retour, indispensable à toute logique d’autorégulation 




![Représentation d'une boucle de rétroaction](https://www.quantmetry.com/wp-content/uploads/2018/12/ARTICLE-1.png)

Figure 1 : Représentation d’une boucle de rétroaction 

Appliquée à la cognition, cette approche très globale de la dynamique de l’information va se décomposer en deux branches principales complémentaires l’une de l’autre : 

  * Le **cognitivisme** , qui assimile les processus mentaux à des manipulations symboliques à partir de règles, dans une approche top-down de la cognition 

  * Le **connexionnisme** , qui envisage la cognition comme un processus émergeant de réseaux d’unités simples interconnectées (le plus souvent des modélisations de réseaux neuronaux), dans une approche bottom-up. 




####  **COGNITIVISME ET SYSTÈMES EXPERTS**

L’informatique naissante, de par la centralité de la notion d’algorithme, va d’abord se focaliser sur l’approche cognitiviste. Il en est ainsi du fameux article Computing machinery and intelligence d’Alan Turing en 1950, qui marque l’apparition de l’IA en tant que problème de recherche. Le papier étudie la possibilité de simuler une intelligence grâce à un ordinateur manipulant des symboles. 

Un peu plus tard, lors de l’été 1956 sur le campus de Dartmouth, John McCarthy, Marvin Minsky, Allen Newell, Herbert Simon et d’autres se réunissent pour discuter les méthodes symboliques, les premiers systèmes experts, ainsi que les avantages comparés des systèmes de raisonnement inductifs et déductifs. Là encore, une approche de la cognition de type top-down, connue aujourd’hui sous le nom d’ **IA symbolique ou GOFAI** (Good Old-Fashioned AI). On s’accorde à considérer ces ateliers comme fondateurs de l’IA en tant que discipline académique. 

Les systèmes experts constituent l’exemple le plus connu de GOFAI. Leur but est de simuler les capacités d’un expert dans un domaine donné, en se basant sur une **base de faits** , une **base de règles** , et un **moteur d’inférence** , qui choisit les bonnes règles pour gérer des faits entrants afin de produire des nouveaux faits. 

![Fonctionnement d'un système expert](https://www.quantmetry.com/wp-content/uploads/2018/12/ARTICLE-2.png)

Figure 2 : Fonctionnement d’un système expert 

Voici un exemple très simple de système expert : 

  * Base de faits : 

    * Marie est la sœur de Jean 

    * Jean est le frère de Pierre 

    * Claude est la mère de Pierre 

  * Base de règles : 

    * si x est le frère de y alors la mère de x est aussi la mère de y 

  * Déductions possibles du moteur d’inférence : 

    * Claude est la mère de Jean 

    * Claude est la mère de Marie 




L’enjeu central pour les systèmes experts est donc de sélectionner la bonne base de faits et de règles pour internaliser les connaissances de l’expert et les informations concernant le cas à traiter. 

Mais du coup, quelle différence avec une succession de boucles « if < règle> then < fait > » ? L’exemple cité est simpliste, mais dans des situations réelles, on peut se retrouver à gérer un nombre très important de faits et de règles interdépendantes, rendant ainsi inefficace et très lent tout programme basé sur la manipulation brute de boucles. Par exemple, dans le cas où aucune optimisation du calcul n’est réalisée, la sortie d’une boucle conditionnelle peut imposer de parcourir en intégralité toutes les autres boucles, et ce à chaque fois qu’elle est exécutée. 

On comprend alors l’importance du moteur d’inférence, dont le rôle est de détecter des conditions communes entre règles, ou encore les règles qui ne sont pas affectées par un fait nouveau, afin d’optimiser la chaîne de raisonnement aboutissant à un fait nouveau à partir des faits donnés en entrée. 

**Remarque** : _Les moteurs d’inférence peuvent implémenter différents types de logiques déductives : une logique d’ordre 0 lorsque les raisonnements se font sur des relations logiques entre propositions, une logique d’ordre 1 lorsque les propositions utilisent des variables, des quantificateurs, des connecteurs logiques et des prédicats, et enfin une logique d’ordre 2 lorsque les variables utilisées dans les raisonnements se réfèrent à des fonctions ou à des prédicats. Il existe également des variantes selon le sens du raisonnement du moteur : un moteur à chaînage avant lorsque l’on part d’une prémisse pour arriver à une conclusion, un moteur à chaînage arrière lorsque l’on part d’une hypothèse pour essayer de trouver les antécédents compatibles, et enfin un moteur à chaînage mixte qui combine les deux._

Pour comprendre les limites de ces systèmes experts, il faut faire un pas en arrière, et interroger les conceptions fondamentales qui sous-tendent l’approche cognitiviste de l’IA, à savoir : 

  * La **thèse fonctionnaliste** , qui admet l’autonomie des sphères matérielle et informationnelle de la description du complexe cerveau/esprit. La cognition est ainsi caractérisée par des états internes et des processus de transition entre états décrits par des règles formelles au niveau informationnel et des relations de causalité au niveau physique. 

  * La **thèse computationnaliste** , qui affirme que les transitions entre états d’un point de vue informationnel sont discrètes et donc descriptibles par des algorithmes 

  * La **thèse représentationnaliste** , qui affirme que les états sont dotés d’un contenu renvoyant à des entités externes dont ils dépendent causalement, leur conférant ainsi une valeur sémantique. 




L’un des plus grands critiques de ces thèses, en particulier de la thèse computationnaliste, est le philosophe américain Hubert Dreyfus. Ses publications _Alchemy and Artificial Intelligence_ (1964), _What computers Can’t Do_ (1972) et _Mind over Machine_ (1986), abordent plusieurs problèmes de fond posés par l’approche symbolique quant à la simulation artificielle d’une intelligence. Un des arguments clés de Dreyfus est que la nature désincarnée de la manipulation symbolique ne peut rendre compte du sens que peuvent posséder ces symboles pour la machine qui les manipule, ce sens devant toujours être fourni de « l’extérieur ». 

Cette critique du computationnalisme, qui n’a toujours pas reçu de réponse satisfaisante aujourd’hui, a néanmoins permis l’émergence d’approches nouvelles basées sur le paradigme connexionniste. Parmi celles-ci le machine learning, et plus généralement les modèles de soft computing, mais également toute une série de théories relevant de la embodied-embedded artificial intelligence (AI) qui cherchent à développer des IA avec une réelle capacité d’adaptation au contexte. 

Elles feront l’objet des deux prochains articles ! 
