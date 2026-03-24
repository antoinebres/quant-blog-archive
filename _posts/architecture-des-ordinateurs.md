# architecture-des-ordinateurs
Wayback Machine URL: https://web.archive.org/web/20230129164027/https://www.quantmetry.com/blog/architecture-des-ordinateurs/
Archive date: 2023-01-29

Uncategorized 

13/10/2015 

#  Architecture des ordinateurs 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Farchitecture-des-ordinateurs%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Architecture%20des%20ordinateurs&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Farchitecture-des-ordinateurs%2F "Twitter")

* * *

Temps de lecture : 14 minutes 

![Quantmetry.com : Architecture des ordinateurs](https://quantmetry.b-cdn.net/wp-content/uploads/2015/10/blog.jpg)

_Cet article est le premier d’une série de deux articles qui reprennent les grandes lignes d’une formation Quantmetry sur l’architecture des ordinateurs. Les biais de ma formation de physicien se feront sentir tout le long de l’article, vous êtes prévenus !_

L’architecture des ordinateurs est un sujet vaste et passionnant. Vaste car la construction d’un ordinateur mobilise des savoirs théoriques et pratiques tellement différents que l’on peut raisonnablement affirmer qu’aucune unique personne ne maîtrise totalement comment marche l’ordinateur sur lequel j’écris cet article ! Passionnant car tenter de comprendre un peu plus ces objets que sont les ordinateurs amène à quelques-unes des questions les plus profondes de la physique, de la théorie du calcul ou encore de l’épistémologie. 

Au vu de ces éléments, il est clair que l’ambition de cette série d’articles n’est pas de donner une vue détaillée de l’architecture des ordinateurs, ni même une vue d’ensemble complète. Elle est plutôt de suivre un cheminement fait de questions (plus ou moins) naturelles qui nous amènera à discuter des notions telle que celles d’information, de calcul, de portes logiques ou de machine de Turing, notions que tout le monde a croisé en dilettante au hasard de cours obligatoires, sans forcément chercher à les connecter de manière cohérente. 

Voici en vrac quelques-unes de ces questions : 

  1. Comment l’information est-elle manipulée au sein d’un ordinateur ? 

  2. Quel sens précis donner au terme « calculer » dans l’expression « un ordinateur effectue des calculs »? 

  3. Comment comprendre la notion de calcul quand on parle d’ordinateurs analogiques ou quantiques ? 

  4. Comment s’articule la théorie des machines de Turing avec les notions de calcul et d’architecture digitale ? 

  5. A quel niveau se fait l’abstraction entre la couche physique et la couche logicielle dans un ordinateur ? 

  6. L’architecture issue des machines de Turing est-elle la seule possible ? La meilleure ? Les ordinateurs analogiques ou quantiques peuvent-ils calculer des choses que nos ordinateurs digitaux ne peuvent pas calculer ? 




Dans ce premier article de la série on s’intéressera uniquement aux trois premières questions. 

##  MANIPULATION DE L’INFORMATION DANS UN ORDINATEUR 

###  L’ORDINATEUR EN TANT QUE TRANSDUCTEUR MODULÉ 

Commençons par la première question : comment l’information est-elle manipulée au sein d’un ordinateur ? L’ordinateur étant un système extrêmement complexe de traitement de l’information, il s’agit là d’une question à laquelle on ne peut donner d’emblée une réponse simple. Nous allons donc commencer par analyser des systèmes plus simples, ce qui nous permettra de développer une intuition plus formelle de la notion d’information. Ainsi, qu’y a-t-il de commun aux trois systèmes de la figure 1 ? 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/blog.jpg)

Dire que les trois sont des systèmes de traitement de l’information ne nous avance pas beaucoup dans la compréhension du problème, même si caractériser un métier à tisser comme tel peut paraître étonnant à première vue. A première vue seulement, car c’est bien en analysant cette machine vieille de plusieurs siècles que l’on comprendra ce qui fait l’essence de l’ordinateur en tant que système de traitement de l’information ! 

Un métier à tisser peut être caractérisé comme suit : il module l’énergie fournie par les muscles du tisseur ou par une machine à vapeur via une carte perforée pour construire un motif final sur un drap, sans oublier la chaleur évacuée vers l’environnement. La position des trous dans un matériau spécifique à une certaine température correspond à l’information que « contient » la carte perforée, information qui est transférée lors de la modulation depuis sa forme « carte perforée » à celle de « motif bien défini des fils du drap final ». Cette transformation a pour trait essentiel d’être causale : un schéma sur les plaques perforées aboutit à un motif sur le drap de manière univoque ainsi qu’à une émission de chaleur très spécifique à la machine utilisée (la chaleur étant générée par les frottements, son émission se fera selon des modalités différentes d’une machine à l’autre, par exemple selon l’emplacement des rouages rouillés etc.). Un gramophone quant à lui module l’énergie de rotation fournie par la main ou un moteur pour transformer l’information stockée sous forme de sillons sur un disque en une configuration temporelle spécifique d’ondes se déplaçant dans l’air. 

Ce qui est commun à ces deux systèmes est la notion de transducteur d’énergie modulé, un mot un peu savant mais qui désigne tout simplement un système qui module une forme d’énergie par une autre, le résultat de cette modulation étant restitué sous une troisième forme d’énergie. Pour les deux exemples ci-dessus, l’énergie de modulation correspond grossièrement à l’énergie interne du matériau composant la carte perforée et celle du disque gravé respectivement. Cependant, ce qui compte dans la modulation est moins la quantité d’énergie qui la définit que sa « forme », i.e. l’information qui y est stockée. Ainsi, l’énergie interne d’une carte perforée en métal froid ou légèrement chauffé n’est pas la même, pourtant les deux donneront le même résultat sur le drap final si elles contiennent les mêmes trous aux mêmes endroits. Idem pour le disque gravé, où la forme des sillons compte bien plus que la température ou la composition du matériau. L’information stockée sera retrouvée sous une nouvelle forme à la fin de l’opération de transduction : configuration spatiale précise des fils du drap, configuration temporelle précise des ondes sonores etc. En résumé, un transducteur module une source d’énergie de forme 1 suivant l’information stockée en tant que configuration d’une énergie de forme 2 pour la restituer sous forme 3. 

Bien qu’un ordinateur soit un système extrêmement complexe de traitement de l’information, vu comme un transducteur il ne fait que moduler l’énergie électrique de la batterie suivant l’information stockée sous une certaine forme d’énergie pour la restituer sous une autre forme : modulation via de l’énergie électromagnétique configurée en mémoire de façon à représenter une image ou un son, avec comme résultat final une énergie lumineuse émise par des diodes électroluminescentes sur l’écran ou une énergie cinétique de la membrane des baffles pour un son. Vu ainsi, un ordinateur ne fait fondamentalement rien de plus qu’un métier à tisser, un gramophone ou un appareil photographique. 

##  L’IMPORTANCE DES CONVENTIONS 

Malgré les similarités qui existent entre un ordinateur et un métier à tisser, il existe une différence fondamentale qui confère aux ordinateurs leur puissance actuelle. En effet, contrairement à un ordinateur qui module l’énergie d’une batterie d’une infinité de manières (schéma de frappes sur un clavier, clics, programmes etc.) pour la restituer sous plusieurs formes possibles (lumière, son, énergie électromagnétique à configuration précise stockée en mémoire etc.), un métier à tisser n’est adapté qu’à un nombre limité de cartes perforées et est conçu pour restituer l’information des cartes uniquement comme motif sur des fils d’un drap. Cette capacité de modulation quasiment sans limites de l’énergie de la batterie des ordinateurs est basée sur deux piliers : 

  * La miniaturisation des systèmes physiques pouvant stocker, lire et traiter de l’information. 

  * L’établissement de conventions très strictes concernant le format et les traitements possibles des données. 




Le premier pilier joue un rôle majeur pour la démocratisation de la capacité de calcul, tandis que le second jour un rôle crucial pour la capacité de restitution d’énergie multiforme des ordinateurs (image, son, etc.). Il est intéressant de noter concernant ce dernier point le semblant de paradoxe qui veut qu’en restreignant les formats et les opérations possibles sur les données à quelques objets abstraits (bits et opérations arithmétiques essentiellement), on aboutisse à une variété plus grande de formats en sortie ! 

Analysons plus en détail le second pilier. L’information stockée en mémoire ne représente une image ou un son que si une convention a été établie auparavant concernant l’interprétation de la configuration de l’énergie électromagnétique en mémoire : c’est la notion fondamentale de format des données. C’est en cherchant à comprendre les transformations entre formats de données que l’on peut saisir les détails des nombreuses transductions qui ont cours au sein d’un ordinateur : des centaines de transducteurs en tous genres échangent de l’énergie électrique. La plupart de ceux formant le cœur de l’ordinateur (processeur, mémoire vive, etc) ne font d’ailleurs que moduler via des circuits « en dur » ou des programmes cette énergie sans en changer la nature pour effectuer des transformations de format, ainsi que pour lire ou pour stocker de l’information. 

Les transductions via des modulations encodées en dur sous forme de circuits peuvent sembler plus intuitives que celles encodées sous forme de programmes. Mais il suffit de se rappeler qu’à l’origine de la modulation via des programmes stockés en mémoire se trouve une modulation plus directe : l’énergie mécanique des frappes sur un clavier ! La même intelligence et réflexion humaine est requise pour concevoir un circuit et les conventions associées permettant de transformer l’information d’une certaine manière que pour concevoir un programme. La modulation via des programmes utilise simplement des circuits déjà conçus pour automatiser et démultiplier la vitesse de certaines manipulations d’information. En stockant une modulation spécifique associée à un schéma des frappes sur un clavier sous forme d’énergie électromagnétique en tant que programme en mémoire, on peut en déclencher les effets sur l’énergie fournie par la batterie grâce à un nombre plus réduit de frappes et arbitrairement plus simple d’un point de vue sémantique, par exemple l’instruction de lancement du programme. Bien comprendre cette idée est essentiel à la compréhension de la notion d’abstraction que l’on abordera plus tard. 

Pour finir cette section, voici un exemple de comment fonctionne approximativement la chaîne de transductions d’une caméra CCD, que l’on peut considérer comme un ordinateur aux fonctions spécifiques : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/lol.png)

L’énergie solaire est modulée par un objet, modulation qui correspond à l’information que l’on cherche à capter (forme, couleur etc.). Elle est ensuite stockée sous forme d’une différence spatiale de l’énergie électrique générée par les photodiodes (points rouges ou blancs sur la figure ci-dessus). La modulation de cette énergie vers une configuration temporelle se fait par une simple différentiation de la taille des chemins à parcourir pour les charges (le chemin le plus long correspond à celui issu de la rangée la plus basse de photodiodes sur la figure ci-dessus) avant de rejoindre la mémoire où elles seront stockées dans des puits de potentiel. 

On constate ainsi que la puissance de nos ordinateurs actuels en tant que systèmes de traitement de l’information se base essentiellement sur la capacité technique à générer, stocker dans des volumes faibles et à orienter très finement et selon des conventions précises des pulsations électriques à des fréquences très élevées (de l’ordre d’un milliardième de seconde) au sein de systèmes physiques. 

Nous sommes désormais mieux armés pour affronter les deuxième et troisième questions : quel sens précis donner au terme « calculer » dans l’expression « un ordinateur effectue des calculs »? Comment comprendre la notion de calcul pour les ordinateurs analogiques ou quantiques ? 

##  QUE CALCULE UN ORDINATEUR ? 

L’unité de calcul d’un ordinateur se situe au niveau du processeur. Un processeur moderne est essentiellement composé d’un ensemble de transistors gravés optiquement dans du silicium et reliés par un réseau complexe de micro-fils en cuivre. Nous avons vu que ce système effectue fondamentalement des transductions d’énergie électrique. Dans le cas le plus simple, celui d’un calculateur arithmétique, le choix de la modulation à appliquer à l’énergie électrique, lui-même lié à l’état physique du système modulateur, correspond à un choix de paramètres d’entrée pour le calcul, par exemple deux opérandes et le choix d’une opération arithmétique si le système est capable d’en effectuer plusieurs. La chaîne causale de transformation des états physiques encodée « en dur » dans les circuits correspond à la transformation vers une configuration finale du système, interprétée comme le résultat du calcul. Plus concrètement, considérons par exemple le fonctionnement de l’une des unités de base d’un processeur, une porte logique : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/capture1.jpg)

Ici l’opération est encodée en dur vu que le système est conçu pour n’effectuer qu’un seul type d’opérations, tandis que la modulation, qui consiste en l’existence ou non d’une poussée mécanique ou d’une charge électrique le long du système physique passant par les points A et B, définit les opérandes de la porte logique. L’état en bout de chaine définit quant à lui le résultat du calcul. Le calcul physique correspondant à un calcul abstrait (‘AND’ logique, ‘OR’, ‘NAND’, etc.) est encodé dans la structure causale des transformations des états du système physique « porte logique domino » ou « porte logique transistor ». Un calcul abstrait peut ainsi correspondre à des calculs physiques très différents, comme on le voit avec les deux exemples de porte ‘AND’ : l’une est basée sur la transmission d’énergie mécanique tandis que l’autre est basée sur la transmission d’énergie électrique. Un ordinateur en tant que calculateur n’est donc rien d’autre qu’un ensemble de chaînes causales d’évolutions des charges électriques encodé « en dur » sous forme de circuits modulables (la modulation pourra provenir des frappes sur un clavier ou bien de l’information stockée en mémoire sous forme de programme) et réalisant des calculs plus ou moins complexes. 
