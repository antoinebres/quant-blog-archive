---
layout: post
title: labellisation-outils-statistiques-annotation
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129152609/https://www.quantmetry.com/blog/labellisation-outils-statistiques-annotation/
---
NLP 

27/02/2020 

#  Labellisation : quels outils statistiques pour réduire le temps d’annotation ? 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Flabellisation-outils-statistiques-annotation%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Labellisation%20%3A%20quels%20outils%20statistiques%20pour%20r%C3%A9duire%20le%20temps%20d%E2%80%99annotation%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Flabellisation-outils-statistiques-annotation%2F "Twitter")

* * *

Temps de lecture : 11 minutes 

![Quantmetry.com : Labellisation : quels outils statistiques pour réduire le temps d’annotation ?](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/article-tre-min.png)

_ ✍ [ Thibaud Real ](https://www.linkedin.com/in/thibaud-real-a78b59153/) & [ Antoine Isnardy ](https://www.linkedin.com/in/antoine-isnardy/) _ /  Temps de lecture : 8 minutes. 

La performance de nombreux algorithmes d’apprentissage automatique dépend de la qualité et de la quantité des données traitées. Lorsque ces données ne sont pas déjà labellisées, il est parfois nécessaire qu’un expert annote les exemples les uns après les autres. Ce processus se révèle souvent long et fastidieux. A titre d’exemple, deux ans et demi ont été nécessaires pour annoter les premières images (3 millions) du corpus [ ImageNet ](http://www.image-net.org/) . Tout projet ne dispose pas d’autant de moyens (temporels et/ou financiers). 

Quantmetry s’intéresse aux enjeux induits par la labellisation, et plus particulièrement dans un contexte de Traitement Automatique du Langage (TAL ou NLP). Plusieurs enseignements ont déjà été partagés dans cet [ article ](https://www.quantmetry.com/labellisation-nlp/) . Le présent article traite toujours de cette question de la labellisation, mais sous un angle davantage quantitatif et statistique. Aussi, sont étudiées ici quelques stratégies permettant de **réduire l’effort d’annotation** . Ces dernières peuvent être regroupées en plusieurs objectifs complémentaires : 

  * **Réduire le nombre d’exemples** qu’il est nécessaire d’annoter pour obtenir un certain niveau de performances via l’active learning, dont proportion, une approche construite par Quantmetry et produisant des résultats intéressants. 
  * **Accélérer le processus d’annotation** en réduisant le temps que va passer un.e « annotateur.rice » à labelliser chaque exemple via l’auto-labelling. 
  * **S’adapter à un contexte changeant** en récoltant des labels rafraîchis. 



####  Stratégies pour réduire l’effort d’annotation 

Les campagnes de labellisation sont souvent menées sous contraintes de **ressources limitées** (temps, humain), et il n’est donc **pas possible d’annoter toutes les données** . Ainsi, quelle(s) stratégie(s) adopter afin d’obtenir des données annotées les plus qualitatives possibles, et qui viendront par la suite alimenter un modèle d’apprentissage automatique ? Les sections suivantes se proposent d’explorer plusieurs alternatives. 

#####  Randomisation 

Il est contre-productif d’annoter des données similaires. Le cas de données similaires survient par exemple dans des contextes où la temporalité joue un rôle clé (dataset de news, demandes d’attestations saisonnières comme des attestations scolaires à la rentrée des classes, …). Considérées dans leur ordre naturel (ou d’arrivée), ces données (i) spécialiseraient un modèle d’apprentissage automatique sous-jacent à un périmètre restreint, et le priveraient en retour de son caractère généralisable ; (ii) susciteraient l’ennui d’annotateur.rices contraints de labelliser des informations trop semblables. Une première piste simple consiste donc à **mélanger les données afin d’obtenir un dataset « équilibré »** : c’est la **randomisation** . 

#####  Active learning 

######  Principe 

Une seconde alternative consiste à utiliser l’ **Active Learning** . L’idée centrale de l’active learning est qu’un algorithme pourrait atteindre des performances raisonnables avec moins de données labellisées, si **les données à annoter** – et à partir desquelles il apprend, **sont choisies judicieusement** . L’active learning pool-based – que nous étudions ici – est un processus itératif, décrit en Fig 1. A noter qu’il existe d’autres méthodes d’Active Learning (stream-based par exemple) que nous ne détaillerons pas dans cet article. 

![Fonctionnement de l’active learning](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/image9-500x417.png)

Fig 1. Fonctionnement de l’active learning 

######  Stratégies de sélection 

L’enjeu majeur de l’active learning réside donc dans la phase de sélection des exemples parmi les données non labellisées : il faut les sélectionner de sorte que l’algorithme apprenne avec le moins de labels possibles. Nous présentons ci-dessous deux stratégies de sélection. 

**Least confident**

Une première stratégie intuitive consiste à sélectionner les instances à labelliser pour lesquelles l’algorithme est le moins certain de sa prédiction. Il s’agit de ne pas continuer à labelliser des données pour lesquelles l’algorithme est déjà performant, ce qui entraînerait au mieux une perte de temps et au pire du sur-apprentissage, mais – à l’image du boosting – de se concentrer de façon itérative sur les instances difficiles à prédire. Plus précisément, cela revient à faire labelliser les instances qui possèdent la probabilité la plus faible associée au label attribué ( **least confident** ) : ` x_{LC}^* = \underset{x}{\operatorname{argmax}} \ 1 - P_{\theta}(\hat{y} | x) ` où ` \hat{y} = \underset{y}{\operatorname{argmax}} \ P_{\theta}({y} | x) ` .   
Avec une telle méthode cependant, la distribution des autres labels n’est pas prise en compte. Une méthode dérivée est margin sampling : ` x_M^* = \underset{x}{\operatorname{argmin}} \ P_{\theta}(\hat{y_1} | x) - P_{\theta}(\hat{y_2} | x) ` où ` \hat{y_1} ` et ` \hat{y_2} ` sont les deux labels les plus probables. Cette méthode a donc pour objectif de corriger le défaut précédemment soulevé de least confident en y ajoutant la probabilité a priori du deuxième label le plus probable. Il s’agit de sélectionner les exemples pour lesquels on est le plus proche de la frontière de décision ; cette frontière de décision correspond aux régions de l’espace qui délimitent les différentes classes, et où l’algorithme a le plus de chance de se tromper. Le lecteur intéressé pourra se référer à [ l’article suivant ](http://burrsettles.com/pub/settles.activelearning.pdf) pour plus de détails sur les différentes approches concernant l’active learning. 

**Proportion**

> Un avantage intéressant de cette méthode est qu’elle ne dépend pas de l’algorithme utilisé, mais uniquement des données. 

Les stratégies introduites dans le paragraphe précédent dépendent de l’algorithme d’apprentissage utilisé (et en particulier de ses probabilités de sortie). Aussi, lors de l’utilisation successive d’un premier algorithme pour la phase de labellisation, puis d’un second – entraîné sur les exemples acquis grâce au processus d’active learning, les gains et la généralisation observés grâce audit active learning ne sont pas toujours « transférés » du premier au second algorithme (voir [ cet article ](https://arxiv.org/pdf/1807.04801.pdf) notamment). C’est cette observation qui nous a poussés à créer une autre stratégie basée sur la distribution des données, plutôt qu’une stratégie de sélection dépendant d’un algorithme, et résumée comme suit : 

  * Nous avons représenté les phrases dans un espace vectoriel (plusieurs alternatives implémentées dont représentations denses et contextuelles ou TF-IDF), qui permet d’ **associer à chaque document un vecteur** , 
  * Nous avons ensuite calculé la **matrice de similarité** entre chaque phrase via une mesure de similarité cosinus. 
  * Enfin, une procédure de **clustering** nous a permis de regrouper les phrases qui se ressemblent à partir de la matrice précédente. 
  * Lors de la phase de sélection, nous avons choisi de manière aléatoire dans chaque cluster un nombre de phrases proportionnel à la taille du cluster, et ce afin de conserver les proportions de l’espace. 



Un avantage intéressant de cette méthode est qu’elle ne dépend pas de l’algorithme utilisé, mais uniquement des données. Par conséquent, les gains associés seront observables sur n’importe quel algorithme, si jamais on décide de changer d’algorithme plus tard par exemple. 

#####  Auto labelling 

La section précédente s’attachait à réduire le nombre de données à labelliser. Une autre méthode pour réduire l’effort d’annotation est de réduire le temps passé à effectuer chaque annotation. C’est l’objectif de l’auto-labelling, qui permet de présenter à l’annotateur.rice des données pré-labellisées par un algorithme. En pratique, au bout de n données annotées, l’algorithme s’entraîne sur les données labellisées et effectue des prédictions sur des données non labellisées. Lorsque les nouvelles données sont présentées à l’annotateur.rice, l’algorithme propose alors des suggestions que l’annotateur.rice peut accepter ou modifier. 

Cette méthode possède deux intérêts majeurs : 

  * Gagner du temps, 
  * Permettre à l’annotateur.rice de se rendre compte de la performance de l’algorithme « en direct ». 



####  Implémentation et application au NER 

#####  Un mot sur le NER 

La reconnaissance d’entités nommées (NER) est une tâche classique du traitement automatique du langage. Elle consiste à détecter des objets de sens dans un texte, comme par exemple des lieux, personnes, entreprises, montants… Si les cas d’usage sont nombreux, nous pouvons citer l’extraction d’informations dans des fiches patients (avancement d’une maladie, taille de tumeur, …), ou encore l’anonymisation de documents. La NER constitue donc un bon candidat pour l’application de techniques statistiques au cours du processus de labellisation. 

Différents modèles de NER existent. Des modèles historiques comme les Conditional Random Fields (CRF – une classe de modèles statistiques prenant en compte l’interaction entre variables séquentiellement voisines) permettent d’obtenir des résultats intéressants avec un effort d’implémentation raisonnable. Ils ont par ailleurs l’avantage par rapport à d’autres modèles plus récents d’être rapides à entraîner. Pour plus de théorie, se référer à l’excellent [ cours ](https://perso.telecom-paristech.fr/essid/teach/CRF_tutorial_ISMIR-2013.pdf) de Slim Essid. Des méthodes plus récentes – à l’état de l’art – permettent d’obtenir des performances décentes avec peu de données d’entraînement. Toutes reposent sur du transfer learning. Parmi les meilleurs modèles actuels, BERT (Bidirectional Encoder Representations from Transformers) et ses dérivés sont parmi les plus populaires. On pourra se référer à cet [ article ](https://www.quantmetry.com/bert-google-ai-banc-de-test/) pour plus de détails sur leur utilisation. A noter que deux versions pré-entrainées sont désormais disponible en Français (non testées ici cependant) : [ CamemBERT ](https://arxiv.org/abs/1911.03894) et [ FlauBERT ](https://arxiv.org/abs/1912.05372) . 

> Quantmetry s’efforce d’utiliser des solutions open source dans un effort de démocratisation et de transparence ; aussi, nous avons donc décidé de nous appuyer sur Doccano, une interface de labellisation open-source, intuitive et ergonomique 

#####  Tooling 

Différents outils existent pour labelliser des données textuelles. Certains outils payants comme Prodigy intègrent des stratégies d’active learning qui ne sont pas décrites explicitement et que l’on ne peut pas contrôler. Pour plus de détails sur les solutions existantes, le lecteur curieux peut se référer à cet [ article ](https://www.quantmetry.com/labellisation-nlp/) . Quantmetry s’efforce d’utiliser des solutions open source dans un effort de démocratisation et de transparence ; aussi, nous avons donc décidé de nous appuyer sur Doccano, une interface de labellisation open-source, intuitive et ergonomique. L’interface est visible en Fig 2. Nous avons par ailleurs amélioré cet outil en y ajoutant les techniques évoquées dans la partie précédente, permettant de réduire le temps d’annotation. 

![Présentation de Doccano, un outil de labellisation open source. ](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/image5-500x211.png)

Fig 2. Doccano, un outil de labellisation open source. Source: [ https://github.com/doccano/doccano ](https://github.com/doccano/doccano)

#####  Active Learning : les résultats 

Nos expérimentations ont été menées sur le dataset [ CoNLL-2003 ](https://arxiv.org/abs/cs/0306050) . Il s’agit d’un dataset standard en NER, et qui comporte les entités suivantes : Personne, Lieu, Organisation, MISC. Notre objectif est d’appliquer à ce dataset les différentes stratégies d’active learning introduites plus haut : 

  * **Normal** : aucun traitement appliqué aux données, la labellisation est faite dans l’ordre naturel d’arrivée, 
  * **Random** : sélection aléatoire des instances à labelliser, 
  * **Least confident** : sont labellisées les instances les plus incertaines pour le modèle, 
  * **Proportion** : la labellisation est effectuée de sorte que les données annotées conservent les proportions de l’espace formé par l’ensemble des données disponibles. 



Nous avons combiné ces stratégies avec différents algorithmes permettant de résoudre la tâche de NER : CRF simple, Bert embedding + CNN + LSTM, Bert embedding + BiLSTM + CRF. A chaque itération, on choisit les 300 prochaines phrases à annoter selon une stratégie d’active learning. Concernant le CRF on réentraîne à chaque fois le modèle from scratch sur l’ensemble des données labellisées disponibles. Pour les modèles de deep learning, on utilise le modèle entraîné lors de la dernière itération et on le réentraîne, avec un faible nombre d’epochs, sur les nouvelles données labellisées ainsi qu’un sous-ensemble des données précédemment labellisées (comme décrit dans cet [ article ](https://arxiv.org/pdf/1707.05928v2.pdf) ). 

Nous analysons dans un premier temps la performance stricte de ces approches. La performance est ici vue comme le nombre d’exemples à annoter pour atteindre une performance raisonnable. La Fig 3 nous montre que le seul fait de sélectionner des phrases de manière aléatoire (stratégie random) permet d’obtenir des gains intéressants par rapport à l’ordre normal (on enlève en effet un biais intrinsèque à l’ordre naturel des données). Par ailleurs, avec le CRF simple, on observe que la stratégie least confident permet d’obtenir des gains de performance notoires par rapport à une sélection aléatoire des données. A noter que la sous-performance de least confident appliquée au BiLSTM-CRF peut s’expliquer par la sélection d’outliers, [ comme men ](https://arxiv.org/pdf/1707.05928v2.pdf)
