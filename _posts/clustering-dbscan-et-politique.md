# clustering-dbscan-et-politique
Wayback Machine URL: https://web.archive.org/web/20230606094845/https://www.quantmetry.com/blog/clustering-dbscan-et-politique/
Archive date: 2023-06-06

Uncategorized 

22/04/2015 

#  Clustering, DBSCAN et politique 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fclustering-dbscan-et-politique%2F&title=Clustering%2C%20DBSCAN%20et%C2%A0politique "Linkedin") [ ](http://twitter.com/intent/tweet?text=Clustering%2C%20DBSCAN%20et%C2%A0politique&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fclustering-dbscan-et-politique%2F "Twitter") [ ](https://www.quantmetry.com/blog/clustering-dbscan-et-politique/ "Email") [ ](https://www.quantmetry.com/blog/clustering-dbscan-et-politique/ "Copy Link")

* * *

Temps de lecture : 6 minutes 

![Quantmetry.com : Clustering, DBSCAN et politique](https://quantmetry.b-cdn.net/wp-content/uploads/2015/04/screen-shot-12-31-18-at-10-05-am-001.jpg)

Avec l’attrait grandissant à la fois pour les smart cities et pour l’opendata, de plus en plus d’administrations publient des jeux de données dans l’espoir que des data-scientists en tirent de la valeur. Ainsi, le site Open data de Paris nous fournit une bonne occasion de tester un fameux algorithme de clustering : DBSCAN. Outil classique de la discipline, DBSCAN est juste un peu moins populaire que l’algorithme des k-means et moins fascinant que les self-organizing-maps : il est souvent délaissé des non-initiés. 

Contrairement à k-means, nul n’est besoin de préciser à priori le nombre de clusters. En contrepartie, 2 autres paramètres doivent être choisis : epsilon et MinPoints. Epsilon quantifie une mesure du voisinage (deux points sont voisins quand ils sont à une distance plus petite que epsilon l’un de l’autre). DBSCAN repose sur le concept de densité : un cluster est une zone de l’espace où la densité d’observations est importante. En sortie, l’algorithme génère autant de clusters que de zones de l’espace de forte densité. Les points isolés sont considérés comme des outliers (valeurs aberrantes). L’algorithme DBSCAN est expliqué plus en détails un peu plus loin dans ce post. 

##  Application aux délibérations du conseil municipal de Paris 

Mon objectif est d’illustrer cet algorithme dans un domaine spécifique : le text-mining, c’est-à-dire le traitement de données textuelles. Nous utiliserons un jeu de données regroupant les ordres du jour du conseil municipal de Paris(1). Une première approche, que j’ai pu tester dans une de mes récentes missions, est de regrouper des étiquettes dont l’écriture est similaire. A cette fin, la distance de Levenshtein(2) s’avère particulièrement efficace. 

Ici, le problème est un peu différent. Nous souhaitons savoir s’il existe des « familles » d’ordre du jour parmi l’ensemble des délibérations du conseil. Je ne m’attarde sur les premières étapes classiques en text-mining (formatage des chaînes, tokenisation, vectorisation, TF-IDF et réduction de dimension) qui me permettent d’obtenir les ordres du jour représentés comme un ensemble d’observations dans un espace à 10 dimensions (10 est un nombre arbitraire choisi pour des raisons de simplicité). Reste maintenant à rechercher des groupes de points distincts. Mais comment avoir une idée de la distance caractéristique d’un voisinage (epsilon) ? 

##  Choix de Epsilon et nombre de clusters 

Sans s’étendre sur des démonstrations mathématiques, voici un petit raisonnement intuitif à garder en mémoire. Quand Epsilon est très petit, tous les points sont très éloignés l’un de l’autre. Il n’y alors aucun cluster, puisque tous les points sont isolés et sont des outliers. En augmentant epsilon, les clusters deviennent plus nombreux. Si epsilon est très grand, alors tous les points sont dans le même cluster. (Très) schématiquement, on pourrait représenter l’évolution du nombre de clusters avec epsilon de la manière suivante : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-31-18-at-10.04-AM.jpg)

Si la distance entre observations n’a pas de signification « métier », il faut fixer epsilonarbitrairement. L’idée est donc de tester différentes valeurs et de prendre celle qui convient le mieux. Si les clusters ont réellement un sens (c’est-à-dire si les observations occupent des zones différentes de l’espace) alors on obtient un palier au niveau de la valeur la plus pertinente. Comme le calcul est assez long, une astuce est de pré-calculer en avance les distance entre chaque point, et de donner à l’algorithme non pas les points dans l’espace mais la matrice des distances. La courbe suivante m’incite à fixer epsilon à une valeur de 0.3. Je l’ai calculée sur un sous-échantillon (pour des raisons exposées plus loin), le passage à l’échelle est donc assez mauvais et le nombre de clusters sur l’ensemble diffère sensiblement. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-31-18-at-10.05-AM.jpg)

##  Résultat de la classification 

Grâce à DBSCAN, j’obtiens des groupes de points correspondant à des ordres du jour homogènes entre eux. Comme il s’agit d’un exemple bidouillé rapidement par soucis d’illustration, l’analyse est simple et les résultats relativement pauvre. L’algorithme a permis ainsi de distinguer entre 6 groupes et un septième groupe « poubelle » contenant une grande part du jeu de données. Pour juger la pertinence de nos clusters, on cherche dans chacun d’eux les mots les plus fréquents. 

_Fréquence d’apparition des mots les plus présents par clusters._

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-31-18-at-10.05-AM-001.jpg)

Il existe évidemment de nombreux moyens de rendre ce résultat meilleur : filtrer les mots trop courants (« stopwords »), changer les étapes de réduction de dimension, etc. Mais ce n’est pas l’objet de ce post. 

##  Description de DBSCAN 

L’algorithme cherche les groupes de points proches. Pour cela, il recherche, pour chaque point, les points faisant partie de son voisinage immédiat, et il regroupe tous les points atteignables de proche en proche. Une fois tous les points regroupés, les groupes de points sont considérés soit comme des clusters soit comme des valeurs aberrantes, si le nombre d’observations est inférieur à MinPoints. 

Avantages de DBSCAN : Il n’est pas nécessaire de connaitre en avance le nombre de cluster désiré. De plus l’algorithme détecte et isole de lui-même les valeurs aberrantes. L’algorithme peut créer des clusters ayant des formes quelconques. 

Inconvénients : La notion de densité ne s’applique pas bien à tous les problèmes. En outre, elle peut varier dans l’espace et ne pas être la même en tout point. Une amélioration de DBSCAN prenant ce problème en compte existe : voir l’algorithme OPTICS. L’algorithme s’applique mal aussi quand il n’y a pas vraiment de « trous » entre les clusters. Dans ce cas, les clusters vont difficilement être séparables. 

Complexité et passage à l’échelle. 

L’algorithme cherche, pour chaque point, si les autres points sont à une distance suffisamment proche de lui : une implémentation simple aboutit à une complexité quadratique. En fait l’algorithme peut être aussi implémenté en n.log(n) en effectuant une recherche plus intelligente. Cependant les packages proposés n’ont pas toujours cette implémentation. 

Dans notre cas, le nombre d’observations est d’environ 32 000 points. Une complexité quadratique devient vite trop lourde pour mon simple laptop (le calcul des distances point par point, par exemple pour données la matrice des distances en entrée de l’algorithme, exige le calcul d’une matrice contenant 10^9 éléments, impossible à calculer avec Ipython-notebook). Notons que l’utilisation de sous-échantillons n’est pas toujours pertinente. Elle peut l’être si les observations sont peu bruitées, mais cela demande d’être validée sur d’autres échantillons. Dans le cas contraire, l’algorithme aura tendance à trouver plus de clusters et de points isolés dans un sous-échantillon (de même qu’en réduisant epsilon, mais pour d’autres raisons). 

##  DBSCAN et Big Data 

En environnement Big Data, DBSCAN n’est pas un outil facilement utilisable car les principales librairies (MLLib, mahout, etc.) n’en proposent pas d’implémentation. La pertinence de la densité, quand le nombre de points est très important, est aussi plus complexe à appréhender. Il existe certaines versions parallélisées de l’algorithme(3). En pratique, une des principales difficultés est le calcul des distances. En O(n²), cela s’avère vite impossible, tandis qu’en O(n.log(n)) il peut être envisagé. 

##  Comment l’utiliser ? 

  * En python : scipy ou scikit-learn (avec comme toujours des explications très claires : 

  * En R : package fpc 




References 

  * Le jeu de données : http://opend 

  * Distance de Levenshtein sur Wikipédia : http://fr.wikipedia.org/wiki/Distance_de_Levenshtein 

  * Article de référence sur la création de l’algorithme par trois professeurs de la TUM : Ester, M., H. P. Kriegel, Jata.paris.fr/explore/dataset/ordres_du_jour_du_conseil_municipal/. Sander, and X. Xu, “A Density-Based Algorithm for Discovering Clusters in Large Spatial Databases with Noise”. In: Proceedings of the 2nd International Conference on Knowledge Discovery and Data Mining, Portland, OR, AAAI Press, pp. 226-231. 1996 

  * Article présentant une version parallélisée de DBSCAN : Md. M.A. Patwary, D. Palsetia, A. Agrawal, W. Liao, F. Manne, A. Choudhary, « A New Scalable Parallel DBSCAN Algorithm Using the Disjoint-Set Data Structure » 

  * Article présentant l’algorithme OPTICS : M. Ankerst, M. M. Breunig, H.-P. Kriegel and J. Sander, “Ordering Points To Identify the Clustering Structure” (http://www.dbs.informatik.uni-muenchen.de/Publikationen/Papers/OPTICS.pdf). Voir aussi la page Wikipedia : http://fr.wikipedia.org/wiki/OPTIC 



