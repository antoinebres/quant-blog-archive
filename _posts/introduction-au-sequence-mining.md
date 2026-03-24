# introduction-au-sequence-mining
Wayback Machine URL: https://web.archive.org/web/20250519103910/https://www.quantmetry.com/blog/introduction-au-sequence-mining/
Archive date: 2025-05-19

Uncategorized 

27/09/2016 

#  Introduction au Sequence Mining 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fintroduction-au-sequence-mining%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Introduction%20au%20Sequence%20Mining&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fintroduction-au-sequence-mining%2F "Twitter") [ ](https://www.quantmetry.com/blog/introduction-au-sequence-mining/ "Email") [ ](https://www.quantmetry.com/blog/introduction-au-sequence-mining/ "Copy Link")

* * *

Temps de lecture : 11 minutes 

![Quantmetry.com : Introduction au Sequence Mining](https://www.quantmetry.com/wp-content/uploads/2016/09/screen-shot-12-30-18-at-04-34-pm.jpg)

##  INTÉRÊT ET EXEMPLES D’APPLICATION DU SEQUENCE MINING 

Les séquences sont une typologie de données très largement retrouvées dans une immense variété d’applications, de la biologie au marketing en passant par la sécurité, l’industrie, le web… Elles sont également un élément fondamental dans l’étude des trois moyens de communication principaux de l’être humain : la parole, l’écriture et le langage. 

Le domaine de la biologie est à l’origine de l’analyse de séquence et est encore aujourd’hui un des domaines où le sequencemining est le plus utilisé. Les séquences biologiques permettent de mieux comprendre le comportement, la fonction ou la structure de nombreuses molécules. On retrouve en premier lieu les séquences d’ADN ou de protéines, cas d’application très largement étudiés dans la littérature scientifique relative au sequence mining. De nombreuses méthodes présentées ci-après viennent à l’origine de problématiques bio-informatiques et ont très largement trouvées leur place sur de nombreux autres cas d’application aujourd’hui. 

D’un point de vu business, les séquences peuvent permettre de décrire le comportement d’un client. Ainsi on pensera aux historiques d’achat d’un individu ou encore aux logs web qu’il génère en navigant sur internet. Les séquences peuvent également donner des informations sur les produits achetés, ou sur les pages visitées en plus de donner une information sur le comportement des clients. Une entreprise cherchera à trouver les sous-séquences les plus fréquentes afin de pouvoir optimiser, par exemple, les produits à mettre en avant. Si un produit à forte valeur ajouté est fortement couplé à un produit plus accessible, une promotion sur ce dernier serait une bonne action marketing pour l’entreprise. Les séquences permettent ici de bien comprendre le comportement des clients afin d’être le plus efficace possible dans les actions marketing. 

Un autre cas d’application concerne la maintenance prédictive. Prenons l’exemple d’une entreprise utilisant des machines connectées dans son processus de production. Chaque machine renvoie régulièrement des séquences de codes maintenances en fonction de l’activité de celle-ci. L’entreprise cherchera à anticiper les pannes sur ses machines afin d’optimiser les coûts de maintenance. L’entreprise fait donc face à un problème de sequence mining supervisé en différenciant les séquences ayant menées à des pannes dans le passé de celles identifiées comme saines a priori. 

Par ailleurs, on parle également de sequence clustering lorsque l’on cherche à regrouper les séquences similaires entre elles. On pourrait imaginer l’exemple d’un médecin qui veut regrouper ses patients en fonction de la séquence de réaction qu’ils ont eu face à un nouveau médicament. 

Enfin, citons quelques exemples d’application du séquence mining plus originaux comme l’optimisation d’une intelligence artificielle grâce à l’étude des séquences d’action des joueurs dans un jeu vidéo, la détection des paquets suspects sur un réseaux informatique, ou encore l’étude des séquences musicales afin de retrouver voire d’imiter un compositeur. La richesse des cas d’usage nous amène bien logiquement à nous intéresser aux différentes méthodes spécifiques à l’analyse de séquences. 

##  ASSOCIATION RULE MINING : IDENTIFIER LES PATTERNS LES PLUS FRÉQUENTS D’UNE SÉQUENCE 

Un des exemples majeurs de l’utilisation du sequence mining est l’analyse des paniers de consommation des clients dans les grandes surfaces ou autres magasins. L’idée est de pouvoir trouver les patterns fréquents dans les achats des consommateurs. Le but est à la fois d’identifier des produits souvent associés les uns aux autres (association rule mining) dans un même panier mais aussi de pouvoir identifier les produits menant à l’achat d’un autre produit dans le futur (le produit d’appel – ex : l’achat d’une console de jeu va entrainer l’achat de jeux vidéo dans le futur). 

Cependant, l’identification des patterns dans les séquences peut vite devenir un problème algorithmique crucial lorsque l’on traite des milliers d’articles différents sur des centaines de milliers de séquences. Il existe dans la littérature plusieurs méthodes qui permettent d’optimiser les calculs dans ces situations. 

La première étape de l’association rule mining consiste à trouver les associations les plus fréquentes dans les différentes séquences. La méthode a priori est la méthode la plus connue pour l’énumération des patterns fréquents. Il s’agit d’une méthode itérative qui cherche les associations sur 1 produit, puis 2, 3, … en prenant soin de supprimer les associations les moins fréquentes à chaque itération. La non-fréquence d’une association est déterminée par un seuil d’occurrence choisi en amont. La principale propriété de cette méthode consiste à dire que toutes les séquences contenant une sous-séquence non fréquente le sont également. Cependant cette méthode apparait comme très couteuse en temps notamment dans la phase de construction des possibles associations à chaque itération de l’algorithme (on comprend bien que la multiplicité des produits disponibles peut considérablement augmenter le nombre de combinaisons et donc le temps computationnel de l’algorithme) 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-04.34-PM-001.jpg)

D’autres algorithmes comme Eclat ou FP-growth permettent une recherche plus efficace et plus rapide et pallient aux problèmes de la méthode a priori. Si les trois algorithmes sus-cités sont basés sur de la recherche et de l’élagage d’arbre, ils s’opposent dans les méthodes de recherche entre depth-first (explorer chaque branche en profondeur avant de passer à la suivante, c’est le cas d’Ecalt) et breadth-first (explorer les voisins immédiats de chaque nœud avant de passer au niveau suivant, c’est le cas de la méthode a priori). 

Il existe encore de nombreuses alternatives notamment certaines ne nécessitant pas de seuil fixé a priori pour la sélection des patterns fréquents (algorithme OPUS). 

##  SEQUENCE CLASSIFICATION 

Dans les exemples d’applications cités en introduction, beaucoup sont des problématiques de classification. Autrement dit, étant donnée une variable cible qui distingue les séquences en plusieurs classes, on cherche à associer chaque séquence à l’une des classes. On peut ainsi citer comme exemple l’identification des séquences de logs intrusives des séquences seines, ou encore le repérage des séquences de données issues de capteurs menant à une panne pour une machine. 

Les algorithmes de classification classiques, bien connus des amateurs de machine learning, incluent notamment les Support Vector Machine, les réseaux de neurones ou autres forêts aléatoires. L’idée ici est de trouver un moyen d’appliquer ces mêmes méthodes prouvées comme efficaces à des données séquentielles en gardant en compte leurs spécificités (l’ordre d’apparition par exemple). 

La subtilité réside dans la construction d’une matrice qui puisse être exploitée par les algorithmes de machine learning. Il existe différentes manières de créer des features à partir d’un jeu de séquences : 

  * Les séquences elles même forment des features 

  * Des sous-séquences peuvent être utilisées comme features. On peut imaginer des séquences arbitraires définies en amont en fonction du cas d’application. 

  * Des informations sur certaines sous-séquences. Cette information n’est plus centrée sur les séquences mais basées sur des propriétés ou éléments extérieurs. 




Prenons l’exemple d’une classification de séquences de logs web. Chaque identifiant de visiteur a une séquence qui lui est propre et que l’on cherche à caractériser par des features. Si l’on suit les points détaillés plus haut, l’ensemble de la séquence forme la première features. Ensuite on peut regrouper certaines successions de logs (et donc de pages web) dans des features spécifiques. Par exemple, on veut savoir si le visiteur est allé directement de la page d’accueil à la page de contact. Un point d’attention concerne le nombre de combinaisons possibles qui augmente exponentiellement avec le nombre de pages ce qui rend complexe la création de features pertinentes. Enfin, on peut ajouter des informations qui ne sont plus basées sur le contenu de la séquence mais sur un comportement plus générales, comme le temps passé sur certaines pages ou le navigateur utilisé. 

Une fois cette phase de création de features effectuée, on obtient une matrice à laquelle on peut associer la cible de notre choix. Toutes les informations sont maintenant rassemblées pour pouvoir utiliser les algorithmes de classification classiques de type SVM. 

A noter qu’un grand nombre d’éléments distincts dans les séquences (on parle d’alphabet) peut mener à un très grand nombre de features. Dans ce cas il est tout à fait possible et conseillé d’utiliser des méthodes de réduction de dimension (ACP, régression LASSO, Elastic Net, …) pour revenir dans un espace de dimension plus facile à traiter et échapper au fléau de la dimension (concept traité précédemment sur le blog de Quantmetry). 

##  ALLER PLUS LOIN 

###  SEQUENCE CLUSTERING 

Le sequence clustering est une méthode très utilisée en bio-informatique qui consiste à rapprocher des séquences qui se ressemblent. L’algorithme utilisé et la distance calculée entre les différentes observations doivent prendre en compte la spécificité des données stockées en séquences. Les principaux cas d’application sont le clustering des séquences d’ADN et de protéines, mais on trouve également des exemples d’utilisation de ces méthodes dans l’analyse des séquences de logs web. 

Un des principaux points d’attention sur la similarité entre plusieurs séquences est le fait qu’elle peut être due à une similarité sur certaines sous-séquences sur plusieurs intervalles. Autrement dit, la similarité entre séquences n’est pas transitive. C’est ce point qui différencie vraiment le clustering de séquences d’une forme plus traditionnelle de clustering (sujet déjà abordé plus en détails sur ce blog). 

L’algorithme le plus courant pour le sequence clustering est basé sur le principe des chaines de Markov de premier ordre. Une chaine de Markov de premier ordre modélise la probabilité de l’état courant d’une séquence en fonction de l’état de celle-ci au temps précédent (appelé probabilité de transition). L’idée est modéliser chaque classe (ou cluster) par une chaine de Markov qui lui est propre. Ainsi, on associe à chaque classe une matrice de dimension (où le nombre d’états, c’est-à-dire la dimension de l’alphabet de la séquence) correspondant aux probabilités de transition de chacun des m états vers les autres. Autrement dit, la probabilité qu’une séquence appartienne à une classe spécifique correspond à la probabilité qu’elle soit générée par la chaine de Markov sous-jacente (et donc par la matrice des probabilités de transition). 

À partir de ce principe, un algorithme comme EM (Expectation-Maximization) peut être utilisé pour réaliser le clustering. Le principe est le suivant : 

  1. Initialisation aléatoire des paramètres des chaines de Markov (les probabilités de transition d’un état à un autre – d’un élément de l’alphabet de la séquence à un autre) 

  2. Associer chaque séquence à une classe en fonction de sa probabilité d’être générée par la chaine de Markov sous-jacente (en fonction des probabilités de transition) 

  3. Recalculer les probabilités de transition des chaines de Markov empiriquement à partir des séquences présentes dans chaque classe 

  4. Répéter les deux étapes précédentes jusqu’à convergence (i.e. quand les classes sont stables et qu’il y n’y a plus de changement) 




Plus d’informations autour de cet algorithme est disponible [ dans cet article scientifique. ](http://web.ist.utl.pt/diogo.ferreira/papers/ferreira07approaching.pdf)

![](https://www.quantmetry.com/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-04.34-PM-002.jpg)

En parallèle de ce premier algorithme, il existe d’autres méthodes de clustering. Pour certaines séquences textuelles une métrique comme la distance de Levenshtein peut permettre de regrouper les séquences les plus proches les unes des autres. Cette distance permet de calculer le nombre de changements (suppression, ajout, mouvement) nécessaires pour passer d’une séquence à une autre. Par exemple, la séquence AABBAAAB et la séquence AABBBAAB ont une distance de Levenshtein de 1 (un A remplacé par un B dans la deuxième séquence). 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-04.34-PM-003.jpg)

Par ailleurs, l’algorithme Dynamic Time Warping (DTW) peut être utilisé pour rapprocher des séquences audio, vidéo ou toutes autres données linéairement séquentielles. Cette méthode consiste à modifier non linéairement l’axe temporel des séquences pour les traiter dans un espace similaire. La distance entre les éléments de chaque séquence est calculée dans le nouvel espace temporel, permettant de rapprocher les séquences les plus semblables. Cette technique permet de de comparer des séquences qui ne s’effectuent pas forcément à la même vitesse ou dans un même espace temporel. Concrètement, on pourrait rapprocher sous forme de séquences audio le discours de deux personnes ayant des vitesses de locutions très différentes. Cet algorithme est justement très utilisé dans le domaine du speech recognition pour cette faculté à s’affranchir de certaines différences temporelles et à capter par conséquent des similarités plus complexes. 

Plus d’informations spécifiques au Dynamic Time Warping pour la comparaison de séquences est disponible sur [ ce blog ](https://jeremykun.com/2012/07/25/dynamic-time-warping/) . 

###  SEQUENCE LABELING 

Le sequence labeling est une forme de sequence mining qui consiste à associer à chaque élément d’une séquence un label à partir d’une liste de labels définies a priori. Le principal cas d’application de cette méthode se trouve dans le Natural Language Processing (NLP) lorsque l’on cherche à caractériser le rôle de chaque mot dans une phrase. On associe à chaque élément des séquences un label qui sera verbe, nom, adjectif, etc. Il existe des dictionnaires listant les différents labels possibles pour caractériser les mots d’une phrase (celui de l’université de Pennsylvanie par exemple). 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-04.34-PM-004.jpg)

Les modèles les plus classiques permettant d’identifier le rôle de chaque mot dans une phrase incluent les modélisations par chaine de Markov cachée (HMM) ainsi que les Conditional Random Fields (CRF). Cet article scientifique présente plus en détail l’approche par Condictional Random Fields tout en l’appliquant à l’exemple du Natural Language Processing. 

Un inventaire des différents algorithmes utilisés pour le sequence labeling ainsi que leur explication mathématique est accessible à [ cette adresse. ](http://www.machinelearning.org/proceedings/icml2007/papers/206.pdf)

Nous avons balayé ensemble les principaux cas d’utilisation et méthodes liés au sequence mining. Il est certain que la donnée sous forme de séquence se retrouve dans de nombreux cas de figure et demande une attention particulière pour un traitement optimal. Les démarches classiques de classification ou de clustering se retrouvent bouleversées par la temporalité et le séquencement des données. 

Cependant, des méthodes avancées de machine learning viennent résoudre ces problèmes pour répondre aux nombreux cas d’application liés aux séquences. Ainsi, la biologie et le marketing sont des domaines dans lesquels le sequence mining est déjà utilisé depuis quelques années respectivement pour l’analyse de séquences de protéines et pour l’analyse de comportements d’achat. Par ailleurs, de nombreux cas d’usage prometteurs viennent s’ajouter à la liste notamment autour du Natural Language Processing ou encore de la reconnaissance de voix. 
