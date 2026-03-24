---
layout: post
title: tout-est-graphe-comment-identifier-les-roles-strategiques-des-influenceurs-dun-reseau
date: 2023-09-24
url_wayback_machine: https://web.archive.org/web/20230924081422/https://www.quantmetry.com/blog/tout-est-graphe-comment-identifier-les-roles-strategiques-des-influenceurs-dun-reseau/
---
Uncategorized 

07/03/2018 

#  Tout est graphe ! Comment identifier les rôles stratégiques des influenceurs d'un réseau ? 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Ftout-est-graphe-comment-identifier-les-roles-strategiques-des-influenceurs-dun-reseau%2F&title=Tout%20est%20graphe%20%21%20Comment%20identifier%20les%20r%C3%B4les%20strat%C3%A9giques%20des%20influenceurs%20d%27un%20r%C3%A9seau%20%3F "Linkedin") [ ](http://twitter.com/intent/tweet?text=Tout%20est%20graphe%20%21%20Comment%20identifier%20les%20r%C3%B4les%20strat%C3%A9giques%20des%20influenceurs%20d%27un%20r%C3%A9seau%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Ftout-est-graphe-comment-identifier-les-roles-strategiques-des-influenceurs-dun-reseau%2F "Twitter") [ ](https://www.quantmetry.com/blog/tout-est-graphe-comment-identifier-les-roles-strategiques-des-influenceurs-dun-reseau/ "Email") [ ](https://www.quantmetry.com/blog/tout-est-graphe-comment-identifier-les-roles-strategiques-des-influenceurs-dun-reseau/ "Copy Link")

* * *

Temps de lecture : 4 minutes 

![Quantmetry.com : Tout est graphe ! Comment identifier les rôles stratégiques des influenceurs d'un réseau ?](https://www.quantmetry.com/wp-content/uploads/2018/03/censorship-free-social-network-akasha-aims-to-tackle-internet-censorship-with-blockchain-technology-950x528-1.jpg)

Cette nouvelle partie de la série d’articles sur la **théorie des graphes** vise à présenter plusieurs techniques d’identification des acteurs influents d’un réseau. En règle générale, dans un réseau, les personnes par qui l’information circule le plus souvent sont les plus influentes. En théorie des graphes, on parle de personnes centrales et on cherche donc à calculer la “centralité” des différentes personnes. 

####  **LES DIFFÉRENTES DÉFINITIONS DE CENTRALITÉ**

Il existe de nombreuses définitions de la centralité. Ici, nous en présenterons quatre, qui sont les plus communément utilisées: 

  * Degré 

  * Closeness 

  * Pagerank 

  * Betweenness 




Avant de détailler les différentes centralités, on rappelle qu’en théorie des graphes, on parle de noeuds ou sommets (les personnes dans l’analogie de l’introduction) et d’arêtes pour les liens entre noeuds (plus de détails disponibles sur les graphes et leur application dans [ cet article ](https://www.quantmetry.com/single-post/2017/11/07/Tout-est-graphe-Introduction-%C3%A0-une-th%C3%A9orie-aux-applications-multiformes) ). 

#####  Degré 

C’est la mesure de la centralité la plus simple et intuitive. Un individu peut être considéré comme important si cet individu a beaucoup de contacts directs. 

Le degré correspond donc à la somme des liens directs d’un noeud. 

Cette mesure peut être directionnelle, en prenant en compte le nombre de liens entrants ou de liens sortants vers le noeud (in-degree, out-degree). 

#####  Closeness 

Un individu aura une centralité importante au sens de la closeness, s’il est proche de tous les autres individus, soit par liens directs ou par liens indirects. 

La closeness correspond à l’inverse de la somme des liens directs et indirects d’un noeud vers tous les autres noeuds. 

La version normalisée de la closeness consiste à multiplier par (n -1) la formule de la closeness. En effet, le cas optimal est le cas où le noeud i est seulement à 1 pas des n-1 autres noeuds : 

![Graphe avec notion de "closeness" sur deux nœuds](https://www.quantmetry.com/wp-content/uploads/2020/09/Screen-Shot-2018-03-05-at-15.45.24.png)

_Graphe du club de karaté de Zachari. Ici, les deux noeuds avec la plus grande centralité sont entourées en noir. Ils sont tous les deux centraux, au sens du degré, mais semblent appartenir à deux différents groupes; le noeud 1 correspond au professeur de karaté et le noeud 34 au président du club._

#####  Pagerank / Eigenvector 

Cette mesure s’inspire de l’algorithme de Pagerank de Google, qui est à l’origine du succès de son moteur de recommandation pour déterminer les sites pertinents lors d’une recherche sur le net. Cette mesure se rapproche de la mesure du degré, car elle tient compte également du nombre de liens directs d’un noeud, mais diffère de celle-ci, car elle suppose que les liens ont des poids différents. Un lien avec un noeud aura plus de poids si ce noeud a lui-même beaucoup de liens directs ou un poids faible si celui-ci est plutôt à la périphérie du réseau. 

Un individu est donc important, au sens du Pagerank, s’il connaît lui-même des personnes qui sont importantes. 

![Meme Gandalf : "YOU SHALL NOT PASS"](https://www.quantmetry.com/wp-content/uploads/2020/09/graphes2.png)

#####  Betweenness 

Cette dernière mesure de centralité, appelée la Betweenness est différente des autres mesures, car elle ne dépend pas du nombre de liens ou de la distance du noeud par rapport aux autres noeuds. 

Un individu est central au sens de la betweenness, si deux individus du réseaux doivent obligatoirement passer par lui, pour s’échanger un message. Il a alors un rôle de “point de contrôle” ou de “pont” dans le réseau. 

La betweenness d’un noeud k correspond à la somme des plus courts chemins entre deux noeuds du réseaux qui passent par le noeud k. 

![Explication imagée des notions indegree, outdegree, betweenness et closeness](https://www.quantmetry.com/wp-content/uploads/2020/09/graphes_3.png)

_Schéma représentant les différentes mesures de centralité du noeud X_

####  **LES DIFFÉRENTS TYPES DE RÔLES**

Nous venons de voir qu’il existe de nombreuses définitions de centralité. Ainsi, deux acteurs d’un même réseau peuvent être tous les deux importants mais avec des rôles stratégiques différents. 

En se basant sur les définitions de centralité, on peut donc distinguer différents rôles stratégiques dans un réseau : 

  1. A beaucoup de contacts directs (Degré) 

  2. Proche de tous les individus (Closeness) 

  3. Connaît beaucoup de personnes influentes (Pagerank) 

  4. Point de contrôle (Betweenness) 




![Cadran avec notions d'importance pour deux nœuds différents](https://www.quantmetry.com/wp-content/uploads/2020/09/graphes_4.png)

Sur ce cadran, on peut observer 2 noeuds importants d’un réseau, mais ayant des rôles stratégiques différents. En effet, le noeud bleu est important au sens du Pagerank, car il connaît des personnes influentes. Alors que le noeud orange est important au sens de la Betweenness, car il est un point de contrôle dans le réseau. En effet, deux autres noeuds du réseau sont susceptibles de devoir passer par lui pour se transmettre un message. 

On voit donc ici qu’il est possible de différencier les types de centralités. Cependant, nous allons voir que certaines mesures sont fortement corrélées entre elles, alors que d’autres moins. C’est ce que nous allons aborder dans ce dernier paragraphe, qui présente les liens entre les centralités. 

####  **LIEN ENTRE LES CENTRALITÉS**

Le pagerank et la closeness sont des mesures très corrélées avec le degré. Ce sont des mesures qui se basent sur la fréquence entre les noeuds. Alors que la betweenness s’appuie sur la notion de chemins. 

C’est pour cela qu’il est intéressant de visualiser le pagerank en fonction de la betweenness. Cela permet d’identifier les nœuds qui ont une stratégie plus de point de passage (bas/droite) et ceux qui ont une stratégie de leader (haut/gauche). 

![Log-plot des centralisés \(données : karate.net\)](https://www.quantmetry.com/wp-content/uploads/2020/09/graphes_5.png)

####  **CAS D’APPLICATION**

Les cas d’usage des centralités sont multiples. Nous détaillons ici deux exemples d’application intéressants. 

#####  Ressources Humaines 

Les ressources humaines sont un domaine très propice à cet usage. On peut alors identifier les personnes influentes d’un réseaux. Un directeur situé en haut de la hiérarchie aura certes une centralité Pagerank importante mais il est intéressant de remarquer que sa secrétaire aura la centralité la plus élevée au sens de la Betweenness ! 

#####  Réseaux Sociaux/Marketing viral 

Transposable au phénomène de la diffusion d’un virus informatique ou d’une épidémie, on cherche en marketing viral à identifier les influenceurs (centralité de pagerank élevée) à solliciter pour diffuser un message ou une marque. 

Ainsi s’achève notre article sur la centralité et les différents rôles stratégiques des acteurs d’un réseau ! 

####  **RÉFÉRENCES**

  * [ Introduction to Social Networks ](http://gawron.sdsu.edu/python_for_ss/course_core/book_draft/Social_Networks/Social_Networks.html#social-networks)

  * “Understanding Dark Networks: A Strategic Framework for the Use of Social Network Analysis” par Daniel Cunningham, Sean Everton, Philip Murphy. 

  * [ Code source du spiderchart ](http://bl.ocks.org/chrisrzhou/2421ac6541b68c1680f8)



