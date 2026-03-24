---
layout: post
title: architecture-des-ordinateurs-2-2
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129165135/https://www.quantmetry.com/blog/architecture-des-ordinateurs-2-2/
---
Uncategorized 

08/11/2016 

#  Architecture des ordinateurs (2/2) 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Farchitecture-des-ordinateurs-2-2%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Architecture%20des%20ordinateurs%20%282%2F2%29&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Farchitecture-des-ordinateurs-2-2%2F "Twitter")

* * *

Temps de lecture : 25 minutes 

![Quantmetry.com : Architecture des ordinateurs \(2/2\)](https://quantmetry.b-cdn.net/wp-content/uploads/2016/11/screen-shot-12-30-18-at-02-15-pm.jpg)

_Cet article est le second d’une série de deux articles qui reprennent les grandes lignes d’une formation Quantmetry sur l’architecture des ordinateurs. Les biais de ma formation de physicien se feront sentir tout le long de l’article, vous êtes prévenus !_

[ Dans le premier article de la série ](http://www.quantmetry.com/single-post/2015/10/13/Architecture-des-ordinateurs) , nous avons caractérisé les systèmes traitant de l’information comme des transducteurs modulés, et un ordinateur comme un ensemble complexe de tels transducteurs muni de conventions de représentation, l’information étant stockée soit dans l’architecture physique de l’ordinateur, soit sous forme de programme. Nous avons également clarifié ce que l’on entend par la notion de calcul : l’état final mesuré par un observateur d’un système dont on maîtrise les transformations causales entre états. L’entrée du calcul correspond alors à l’état initial du système. L’ensemble des états peut être discret, continu ou bien un espace de Hilbert dans le cas des systèmes quantiques. 

Par exemple, on peut considérer dans la figure ci-dessous que la conformation de l’eau savonneuse autour de deux anneaux correspond à une solution à énergie minimale d’une équation physique, et donc à un calcul puisque l’on peut mesurer la position de chaque point de la surface : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Sans-titre0.png)

Autres exemples de calculs différentiels, la mesure de l’intensité ou de la position pour les systèmes électrique et mécanique ci-dessous, solution d’équations d’oscillations très classiques : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-02.16-PM.jpg)

On peut également considérer des exemples d’intégrateurs analogiques, comme le système mécanique suivant : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-02.16-PM-001.jpg)

On devine aisément qu’un calcul quantique correspond simplement à la mesure de l’état final d’un système microscopique évoluant sous des contraintes censées représenter le calcul à effectuer. 

Ainsi, nous avons répondu aux trois premières questions que l’on se posait au début du premier article, à savoir : 

  1. Comment l’information est-elle manipulée au sein d’un ordinateur ? 

  2. Quel sens précis donner au terme « calculer » dans l’expression « un ordinateur effectue des calculs » ? 

  3. Comment comprendre la notion de calcul quand on parle d’ordinateurs analogiques ou quantiques ? 




Nous avions conclu le premier article en évoquant la notion de machine de Turing et son rôle essentiel pour comparer la puissance de calcul de machines différentes. Les questions qui restaient en suspens vont nous permettre de structurer la présentation de ce concept et son apport en théorie de la calculabilité : 

  1. Comment s’articule la théorie des machines de Turing avec les notions de calcul et d’architecture digitale ? 

  2. À quel niveau se fait l’abstraction entre la couche physique et la couche logicielle dans un ordinateur ? 

  3. L’architecture issue des machines de Turing est-elle la seule possible ? La meilleure ? Les ordinateurs analogiques ou quantiques peuvent-ils calculer des choses que nos ordinateurs digitaux ne peuvent pas calculer ? 




##  Calcul physique et calcul symbolique 

###  La notion d’algorithme 

Nous avons vu précédemment qu’un même calcul abstrait pouvait être effectué grâce à des machines physiquement très différentes. Nous avons nommé les transformations d’états de ces machines « calculs physiques ». Si l’on cherche à définir plus rigoureusement la notion de calcul abstrait, on est rapidement amené à s’intéresser à la notion de manipulation symbolique, et donc à celle d’algorithme. 

Un algorithme est défini comme étant une procédure non-ambiguë et finie permettant de produire la réponse à une question. En voici quelques exemples : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Sans-titre6.png)

Cette définition est censée englober tout ce qu’un humain peut calculer à l’aide d’une feuille et d’un crayon, sans contrainte de temps ni de ressources. Elle constitue une abstraction de tous les calculs que l’on cherche à implémenter dans des systèmes physiques. Reste à définir maintenant un modèle à la jonction de ces deux mondes pour justifier la pertinence de cette abstraction et pouvoir comparer les machines entre elles. 

###  La machine de Turing 

La machine de Turing est une machine abstraite consistant en : 

  * Une bande infinie composée de cellules contenant des symboles d’un alphabet fini, par exemple {0, 1, A, X, #}. 

  * Une tête de lecture/écriture sur la bande qui peut se déplacer une cellule à la fois, à droite ou à gauche. La cellule pointée par la tête est surlignée en jaune. 




![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Sans-titre7.png)

  * Un registre d’états qui enregistre les états de la machine de Turing. Parmi ces états se trouve un état « Start » associé à l’initialisation de la machine de Turing. 

  * Une table finie d’instructions qui pour un état donné de la machine de Turing et un symbole lu sur la cellule pointée par la tête donne une instruction non-ambiguë à la machine. 




![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Sans-titre8.png)

Il s’agit donc essentiellement d’une généralisation de la notion familière d’automate. La force du concept de machine de Turing est de modéliser à la fois les manipulations symboliques et des machines physiques évoluant selon un schéma causal bien défini, opérant ainsi une jonction entre les notions de calcul symbolique ou algorithme et celle de calcul physique. 

Analysons maintenant en détail l’exemple de la machine de Turing donné en définition. La machine représentée compte le nombre de A, enregistre ce nombre sous forme binaire à gauche de la séquence de A, et transforme cette séquence en une séquence de #. Voici le résultat des deux premières instructions : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Sans-titre9.png)

Et voici les transformations de la bande après quelques itérations : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Sans-titre10.png)

On peut ainsi imaginer des machines de Turing pour tout type d’algorithme : addition binaire, multiplication par 24, etc. Une question naturelle vient alors à l’esprit : faut-il nécessairement des jeux d’instructions complexes pour effectuer des calculs complexes ? La réponse, illustrée de manière spectaculaire à travers la notion de machine de Turing universelle, est non ! 

###  Machine de Turing universelle 

Considérons l’instruction suivante : 

**SUBLEQ = soustraire et bifurquer si négatif**

Plus précisément, on soustrait le contenu d’une adresse ‘b’ du contenu d’une adresse ‘a’, on stocke le résultat dans l’adresse ‘b’ et, si le résultat est négatif, on se déplace à l’adresse ‘c’, sinon on passe à l’instruction suivante. En pseudocode cela donne : 

**subleq a, b, c : Mem[b] = Mem[b] – Mem[a] ;**

**if (Mem[b] ≤ 0) goto c**

Malgré sa simplicité, on peut démontrer qu’il s’agit bien là d’une instruction universelle, i.e. d’une instruction capable de reproduire n’importe quelle autre instruction si répétée selon un schéma précis, que l’on nomme programme. L’addition peut par exemple être reproduite par des soustractions sans bifurcation comme suit : 

**ADD a, b = subleq a, Z ; subleq Z, b ; subleq Z, Z**

La première instruction stock dans Z la valeur de la différence entre a et Z (de valeur initiale 0), à savoir -a, la seconde stock dans b la différence entre b et -a, à savoir b+a, enfin la dernière instruction réinitialise la valeur de Z à 0. 

Cette instruction est ce que l’on appelle une instruction universelle : c’est une instruction capable de simuler n’importe quelle machine de Turing. Elle est donc capable d’exécuter tout algorithme ! À noter que pour passer du pseudocode de cette instruction au formalisme des machines de Turing (qui n’intègre pas de notion de déplacement à une adresse quelconque), cette dernière doit être légèrement étoffée, mais le nouveau jeu d’instructions restera relativement simple malgré son pouvoir de calcul universel. La simulation d’une autre machine de Turing sera alors faite via des programmes représentant des patterns des instructions de base stockés sur une bande. On parlera alors de machine de Turing universelle. 

Nous voyons ainsi que le concept de machine de Turing permet de comparer entre elles les capacités théoriques de calculs de machines physiques exécutant des algorithmes via des instructions, ces instructions étant associées à des transformations causales d’états. Certaines machines sont incomparables, d’autres le sont via la relation de simulation, avec notamment certaines machines qui sont universelles. C’est bien cette classe de machines de Turing universelles qui est à la base de l’architecture moderne des ordinateurs. 

##  De la machine de Turing à l’architecture digitale 

###  Réalisation physique 

En mappant les transitions entre états de la machine de Turing sur des transitions entre états d’un système physique, on peut représenter tout algorithme par un calcul physique. Le jeu d’instructions de la machine de Turing caractérisera alors tous les calculs que peut effectuer la machine physique. L’architecture de Von Neumann, représentée ci-dessous et qui est le standard d’architecture des ordinateurs numériques modernes, a été introduite par le mathématicien John Von Neumann comme mise en pratique des travaux de Turing : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Sans-titre11.png)

Un processeur est composé d’une unité arithmétique et logique, d’une unité de contrôle et d’une horloge interne. L’unité de contrôle comporte des mémoires spécifiques à l’accès en lecture/écriture très rapide et dénommées « registres » ou « mémoire cache ». Ces mémoires permettent le stockage des valeurs intermédiaires lors des calculs. Le processeur communique avec : 

  * une mémoire qui, couplée au processeur, implémente la notion de registre d’états et une partie finie de la bande mémoire, 

  * une mémoire externe qui joue le rôle de bande (potentiellement) infinie, 

  * des périphériques qui peuvent modifier les informations contenues dans la bande mémoire. 




Nous allons maintenant étudier plus en détail chacun des composants de cette architecture. 

###  L’unité arithm 
