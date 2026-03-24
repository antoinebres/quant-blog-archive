---
layout: post
title: adapter-evolution-fraude
date: 2022-10-01
url_wayback_machine: https://web.archive.org/web/20221001021322/https://www.quantmetry.com/blog/adapter-evolution-fraude/
---
Time Series 

18/06/2019 

#  Comment s'adapter à l'évolution de la fraude ? 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fadapter-evolution-fraude%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Comment%20s%27adapter%20%C3%A0%20l%27%C3%A9volution%20de%20la%20fraude%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fadapter-evolution-fraude%2F "Twitter")

* * *

Temps de lecture : 15 minutes 

![Quantmetry.com : Comment s'adapter à l'évolution de la fraude ?](https://quantmetry.b-cdn.net/wp-content/uploads/2019/06/article-gregoire-min.png)

Le nombre de transactions bancaires sur internet augmente, et le nombre de fraudes également. De plus, les fraudeurs contournent sans cesse les barrières de protection mises en place par les banques. Comment éviter qu’un modèle anti-fraude devienne obsolète dès sa mise en production ? Voici quelques éléments de réponse apportés par l’apprentissage adaptatif. 

####  Comment la banque s’adapte-t-elle à la fraude ? 

Une banque doit pouvoir gérer des centaines de millions de transactions par an. Parmi toutes ces transactions, environ une sur mille est une fraude. 

#####  Le point de vue du fraudeur 

Une fraude typique consiste à obtenir les codes carte bleue d’une victime, à effectuer des achats en ligne à sa place et à revendre les produits obtenus sur le marché noir. Le fraudeur a tout intérêt à maximiser son gain, c’est-à-dire à perpétuer les transactions frauduleuses sans se faire bloquer par la banque. 

#####  Le point de vue de la banque 

De son côté, la banque analyse de manière semi-automatique toutes les transactions effectuées. Un système de détection (souvent un système de règles) bloque les transactions suspectes. Des experts en sécurité les analysent ensuite en détails, et peuvent confirmer ou infirmer la fraude en contactant directement le client. Toute cette étape est en réalité une étape de labellisation des transactions (voir Figure 1). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/ai-cycle.png)

Figure 1 – Le cycle de vérification d’une transaction. Lorsqu’une transaction est émise, elle est analysée par un système de blocage. Les transactions bloquées sont ensuite analysées par des experts en sécurité qui labellisent lesdites transactions. Un modèle de _machine learning_ peut alors s’entraîner sur les transactions labellisées et venir nourrir le système en place. 

Comme dans tout jeu du chat et de la souris, la banque et les fraudeurs se livrent une guerre technologique sans merci. Le comportement des fraudeurs change sans cesse et celui de la banque également. Dans ce contexte changeant rapidement (parfois en l’espace de quelques heures), la plupart des modèles de détection de fraude voient leur performance chuter : on parle de dérive des modèles. 

####  Qu’est-ce qu’une dérive de modèle ? 

#####  Persistance rétinienne infinie 

Par abus de langage, on parle de dérive de modèle dès que les performances décroissent dans le temps après la mise en production. En réalité, le modèle ne dérive pas : il a photographié l’état de la fraude à la date d’entraînement et ne s’est donc pas adapté à l’évolution des _patterns_ de fraude. En toute rigueur, c’est donc la donnée qui a dérivé (voir Figure 2). On parle alors de [ dérive conceptuelle ](https://machinelearningmastery.com/gentle-introduction-concept-drift-machine-learning/) ( _concept drift)_ [1]. Imaginez vous en train de regarder un film avec une persistance rétinienne infinie : le générique de début se mélangerait à la première scène, puis à la deuxième jusqu’à l’obtention d’une purée visuelle où plus aucun élément n’est intelligible (exemple sur le film [ Mary Poppins ](https://www.jasonshulmanstudio.com/photographsoffilms/mary-poppins-1964) ). C’est un peu ce que ressent un modèle statique entraîné sur un flux dynamique. **Il faut donc passer d’une vision photographique de la donnée à une vision cinématographique.**

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/concept_drift.gif)

Figure 2 – Exemple de données qui dérivent. Ici, on représente schématiquement une problème bi-dimensionnel. Chaque point représente une transaction, et les fraudes sont indiquées en rouge. La dynamique des fraudeurs les oblige à explorer de nouvelles stratégies de manière dynamique. Un modèle qui a appris à distinguer la cible rouge/vert à un instant t devient rapidement obsolète. 

#####  Effondrement des modèles statiques 

Pour illustrer cette obsolescence des modèles, on se propose de résoudre le problème de classification de la Figure 2 de trois manières différentes : 

  * **Méthode 1 :** on considère le jeu de données d’un bloc. On entraîne et évalue un modèle kNN ( _k-Nearest Neighbours_ ) par validation croisée. C’est la **méthode statique** . 
  * **Méthode 2 :** on considère le jeu de données comme un flux. A chaque instant, le kNN s’entraîne sur tout l’historique passé, et prédit la prochaine observation. C’est la **méthode incrémentale** . 
  * **Méthode 3 :** on considère le jeu de données comme un flux. A chaque instant, le kNN s’entraîne sur un historique récent (10 000 observations) et prédit la prochaine observation. C’est la **méthode fenêtre glissante** . 



En comparant les prédictions et les vrais labels au cours du temps, on obtient les courbes de performances décrites dans la Figure 3. On voit que le modèle incrémental tend vers un modèle statique (c’est l’effet persistance rétinienne infinie, ou _catastrophic forgetting_ ), tandis que le modèle fenêtre glissante réussit à maintenir sa performance à un niveau raisonnable. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/simulated-cumulative.png)

Figure 3 – Comparaison des performances (F-score) sur le _toy dataset_ de la figure 2. La méthode 1 est représentée en vert : on considère le jeu de données comme un bloc et on évalue un kNN par validation croisée. En bleu, c’est la méthode 2: on considère le jeu de données comme une flux, mais pour chaque prédiction du kNN, on entraîne sur l’historique passé complet. Enfin en rouge, on représente la méthode 2 : on entraîne un kNN sur une fenêtre glissante de taille fixe et on prédit la prochaine observation. 

#####  Comment construire un algorithme adaptatif ? 

On observe donc une forte valeur ajoutée à considérer l’évolution temporelle de la donnée dans un modèle prédictif [ en production ](https://www.forbes.com/sites/forbestechcouncil/2019/04/03/why-machine-learning-models-crash-and-burn-in-production/#504fab322f43) . L’apprentissage adaptatif _(adaptive learning) regroupe_ l’ensemble des algorithmes de _machine learning_ capables de s’adapter automatiquement à la dérive des données [2]. Il sont essentiellement constitués de trois briques élémentaires : 

  * un détecteur de dérive 
  * un modèle incrémental 
  * une stratégie ensembliste de combinaison des deux items précédents 



#####  Première brique élémentaire : comment détecter une dérive ? 

La fenêtre glissante évoquée plus haut est une démarche passive : le modèle s’adaptera à son historique récent **qu’il y ait ou qu’il n’y ait pas** de raison de le faire. De plus, le ré-entraînement sur fenêtre glissante est très coûteux en temps de calcul. En effet, une variation infime du jeu de données déclenche un ré-entraînement complet du modèle. Une stratégie plus efficace consiste à ne s’adapter que lorsque c’est vraiment nécessaire et à accumuler la donnée tant qu’elle ne dérive pas. Pour ce faire, on fait appel à un **détecteur de dérive** . 

Prenons l’exemple du détecteur ADWIN ( _Adaptive Windowing_ ) [3], illustré sur la Figure 4. ADWIN va suspecter qu’une dérive a pu avoir lieu à tout moment, mettons t’, dans le passé. Pour le vérifier, il isole le passé et le futur de t’ en deux sous-fenêtre disjointes W_L ( _Window Left_ ) et W_R ( _Window Right_ , voir Figure 5). Le détecteur effectue ensuite un test d’homogénéité basé sur la [ borne de Hoeffing ](https://fr.wikipedia.org/wiki/In%C3%A9galit%C3%A9_de_Hoeffding) pour décréter si oui ou non les deux sous-fenêtres sont significativement différentes. Si oui, alors une dérive est détectée, et se voit assigner la date t’. C’est ensuite à l’utilisateur (ou à l’algorithme) de prendre en compte ce signal pour s’adapter, en ré-entraînant un modèle sur l’historique post-dérive par exemple. L’efficacité de l’algorithme résulte dans sa rapidité à explorer les t’ possibles. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/window-1024x370.png)

Figure 4 – Fonctionnement de ADWIN. A chaque instant t, on suspecte qu’une dérive a eu lieu à un instant t’ < t. Pour le vérifier, on effectue un test d’homogénéité entre le passé et le futur de t’. Si une différence significative est détectée, alors on supprime la sous-fenêtre gauche. Pour être exhaustif, il faut sonder tous les t’ possibles, mais il existe des astuces (la compression exponentielle d’histogrammes) qui permettent d’agir en temps logarithmique. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/Capture-d’écran-2019-05-24-à-16.35.22.png)

Figure 5 – Pseudo-code de l’algorithme ADWIN. La fonction _significant_difference_ est simplement un test statistique d’homogénéité basé sur la borne de Hoeffding. 

#####  Deuxième brique élémentaire : comment apprendre en continu sur un flux de données ? 

Pour détecter une dérive le plus rapidement possible, il faut acquérir de l’information le plus rapidement possible, idéalement en temps réel. C’est le cas des flux de données. Nombre d’algorithmes classiques peuvent s’entraîner de manière incrémentale, notamment par descente de gradient. Toutefois, en présence de dérives sur un flux de données, trois éléments sont à prendre en compte : 

  * il est impossible d’anticiper quelle variable aura des valeurs manquantes, 
  * l’échelle de variation des variables peut changer drastiquement au cours du temps, 
  * la structure de corrélation du jeu de données évolue sans cesse. 



Ces trois contraintes mises bout à bout jouent grandement en faveur des **arbres des décisions** : ils sont robustes aux valeurs manquantes, ils sont également invariants par transformation affine, et enfin leurs performances sont faiblement impactées par les corrélations fortes entre variables. 

L’archétype de l’arbre de décision incrémental s’appelle l’arbre de Hoeffding [4]. Comme son nom l’indique (et comme ADWIN), il se base, sur la borne du même nom. La croissance de l’arbre se fait par optimisation gloutonne ( _greedy)_ (voir Figure 6) : au fur et à mesure que l’information s’accumule dans les feuilles, l’algorithme cherche une découpe optimale qui assure un gain d’entropie statistiquement significatif. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/hoeffding-tree-1024x257.png)

Figure 6 – Illustration de la croissance d’un arbre de Hoeffding. L’arbre commence son apprentissage avec un seul noeud et aucune observations à sa disposition. Au fur et à mesure que les données s’accumulent dans un noeud, l’algorithme cherche une découpe statistiquement avantageuse au sens de Hoeffding. Si une telle découpe existe, le noeud est découpé et les feuilles sous-jacentes vont accumuler de la donnée, et ainsi de suite. 

Comme tout algorithme incrémental, l’arbre de Hoeffding est à mémoire infinie et est donc sujet au _catastrophic forgetting_ (syndrôme de la persistence rétinienne infinie). C’est seulement une fois combiné avec un détecteur de dérive qu’on obtient un algorithme dit adaptatif. 

#####  Troisième brique élémentaire : comment concevoir une stratégie d’adaptation ? 

La stratégie d’adaptation la plus populaire consiste à utiliser un ensemble dynamiques d’arbres de Hoeffding, interagissant au gré des détections de dérives fournies par ADWIN. L’idée est en fait celle d’un **comité d’experts dynamique** , où plusieurs modèles entraînés sur des périodes différentes votent avec une pondération indexée sur la performance courante. L’état de l’art de ce genre de stratégie est la forêt aléatoire adaptative _(adaptive random forest)_ [5], dont le principe est le suivant. 

Tout d’abord, chaque arbre individuel doit être différent de ses pairs car c’est dans la diversité des modèles que se crée la valeur de l’ensemble. Pour créer de la diversité entre les arbres, on fait appel aux techniques d’ _online bagging_ (voir Figure 7) [6], qui consistent à perturber aléatoirement le flux de données expérimenté par chaque arbre. On peut pousser plus loin la perturbation avec du _feature sampling_ (tirage au sort des variables considérées pour chaque découpe). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/online-bagging.png)

Figure 7 – Principe de l’ _online bagging_ . Pour chaque observation, on tire un nombre entier au hasard selon une loi de Poisson. Le résultat indique le nombre de duplicatas à distribuer à l’arbre. La loi de Poisson est utilisée car elle est équivalente à un échantillonnage _bootstrap_ classique quand la taille du flux tend vers l’infini. 

À ce point de l’explication, nous avons donc un ensemble diversifié d’arbres incrémentaux. La brique adaptative réside dans le détecteur de dérive ADWIN. En effet, chaque arbre voit ses performances mesurées en continu, et est muni de deux détecteurs (voir Figure 8). Le premier détecteur possède un seuil de détection faible et sert à notifier l’arbre qu’il rentre potentiellement dans une zone de turbulence (phase 1). Pour anticiper un futur remplacement de l’arbre, on plante alors un arbre alternatif (un bébé arbre). Le deuxième détecteur possède un seuil de détection élevé et sert à confirmer le premier. Si une telle confirmation a lieu (phase 2), l’arbre sénile est éjecté de l’ensemble et remplacé par son homologue juvénile (arbre devenu adolescent, et donc performant, depuis) planté en phase 1. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/ARF-tree-monitoring.png)

Figure 8 – Principe d’une forêt aléatoire adaptative. Chaque arbre est surveillé par un détecteur. Dès qu’un 
