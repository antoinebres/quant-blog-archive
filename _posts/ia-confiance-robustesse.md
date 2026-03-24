# ia-confiance-robustesse
Wayback Machine URL: https://web.archive.org/web/20250709214612/https://www.quantmetry.com/blog/ia-confiance-robustesse/
Archive date: 2025-07-09

IA de confiance 

09/05/2023 

#  La Robustesse, un impératif pour une intelligence artificielle de confiance 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fia-confiance-robustesse%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=La%20Robustesse%2C%20un%20imp%C3%A9ratif%20pour%20une%20intelligence%20artificielle%20de%20confiance&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fia-confiance-robustesse%2F "Twitter") [ ](https://www.quantmetry.com/blog/ia-confiance-robustesse/ "Email") [ ](https://www.quantmetry.com/blog/ia-confiance-robustesse/ "Copy Link")

* * *

Auteur : [ Lucas Michelis ](https://www.linkedin.com/in/lucas-michelis/)

Temps de lecture : 6 minutes 

![Quantmetry.com : La Robustesse, un impératif pour une intelligence artificielle de confiance](https://www.quantmetry.com/wp-content/uploads/2023/05/robustesse-main-img-scaled.jpg)

L’intelligence artificielle de Confiance est un sujet que l’on adresse tous les jours chez Quantmetry pour fournir à nos clients des algorithmes de qualité. Ce sujet est traité par l’expertise Reliable AI qui assure la connaissance et l’application de l’état de l’art des 8 thématiques de l’IA de Confiance introduites dans cet [ article ](https://www.quantmetry.com/blog/ia-confiance-decennie/) . La robustesse est une de ces 8 composantes. 

![](https://www.quantmetry.com/wp-content/uploads/2023/04/robustesse.png)

#  La Robustesse, à quoi ça sert ? 

Le concept de robustesse est l’un des grands piliers fondamentaux de l’IA de confiance. L’étude de la robustesse d’un modèle se fait dans le but de satisfaire deux objectifs majeurs. 

Le premier objectif est de définir le domaine sur lequel le modèle est performant et fiable : c’est ce qu’on appelle le domaine de validité. En effet, un modèle ne performe pas de manière équivalente sur tous les sous-ensembles du domaine sur lequel il est capable d’inférer. L’objectif ici est donc de définir un ensemble sur lequel le modèle est opérationnel. 

Le second objectif découle du premier : repousser les limites de validité du modèle. En effet, une fois le domaine de validité défini, il est important de comprendre pourquoi le modèle ne se comporte pas comme attendu sur tel ou tel sous-ensemble, et ensuite tenter de remédier à ces limitations. 

#  La Robustesse, qu’est-ce que c’est ? 

Afin de comprendre un peu mieux de quoi on parle lorsqu’on s’attaque à la robustesse, regardons tout d’abord sa définition la plus naïve, celle du Larousse : 

« Qui ne se laisse pas ébranler facilement, qui résiste bien aux agressions ou altérations » 

Un modèle robuste serait donc un modèle sur lequel on peut compter en toutes circonstances. Il est important de noter que, dans le cadre de l’IA de confiance, le concept de robustesse n’existe que relativement à un modèle.   
La question que l’on peut se poser est la suivante : comment faire de mon modèle un modèle robuste ? Nous avons identifié plusieurs problématiques à adresser afin de maîtriser la robustesse d’un modèle : 

##  Le contrôle du domaine de validité 

Contrôler le domaine de validité du modèle est une étape importante car elle a pour objectif de définir un cadre sur lequel le modèle est valide et opérationnel. Ceci nous permettra de définir des règles de rejet afin de rejeter les entrées qui ne sont pas valides du point de vue du modèle. De cette manière, le modèle ne devrait en aucun cas se retrouver dans une situation « inconnue » durant laquelle il doit extrapoler ce qu’il a appris à une situation nouvelle. 

##  La maîtrise de l’incertitude de la prédiction 

Le calcul des incertitudes statistiques pour chaque prédiction reste un incontournable ! En effet, même au sein du domaine de validité du modèle, la « confiance » qu’a le modèle en sa propre prédiction peut varier. D’où la pertinence de l’étude des incertitudes via des intervalles de confiance (en régression) ou des calibrations de probabilités (en classification). 

##  Contrôle de la stabilité du modèle 

Les systèmes d’IA étant de plus en plus utilisés, ils sont aussi de plus en plus sujets aux attaques adverses. Pour rappel, une attaque adverse a pour objectif de détourner l’usage d’une IA en faisant varier l’entrée de manière minime et imperceptible à l’œil humain. La perturbation étant minime, l’attaque adverse peut appartenir au domaine de validité et peut être ainsi être considérée comme valide. Afin de contrer ces agressions, il est nécessaire de maîtriser les processus aléatoires et de caractériser la résilience de la performance face à des classes de perturbations pertinentes d’un point de vue métier. 

#  La Robustesse, comment l’activer ? 

La robustesse ayant été définie, il faut maintenant être en mesure d’appliquer ce concept sur le terrain ! Ceci passe par la mise en place systématique de 3 actions : délimiter, douter et perturber. 

##  Délimiter 

L’objectif de cette action est de définir le domaine de validité du modèle (défini précédemment comme le domaine sur lequel le modèle est opérationnel) et de le prémunir contre les défaillances connues. Il existe plusieurs moyens de satisfaire ces objectifs. Cela peut passer par l’implémentation de règles de rejet de données et de leur documentation, jusqu’à une caractérisation plus complexe des situations où le modèle est moins performant, par exemple avec une analyse d’erreurs exhaustive. 

##  Douter 

L’objectif de cette action est de quantifier les incertitude des prédictions. Ceci peut s’effectuer via la définition des niveaux de confiance, et par l’étude globale et/ou individuelle des barres d’erreur sur les prédictions et la performance. 

##  Perturber 

L’objectif de cette action est de contrôler les processus aléatoires afin d’évaluer la robustesse aux perturbations. Ceci passe dans un premier temps par une garantie de la reproductibilité et la maîtrise de toutes les graines aléatoires. Dans un second temps, on peut procéder par des perturbations de données d’entrée avec des amplitudes maîtrisées afin d’évaluer la détérioration des performances 

Chacune de ces études doit être documentée afin de conserver un document qui servira de support lors des décisions opérationnelles et des audits imposés par la future réglementation. 

#  La Robustesse, en vrai ça donne quoi ? 

Fini la théorie, place à la pratique ! Nous allons en effet vous faire part d’une expérience mission abordée avec le prisme robustesse, durant laquelle nous avons pu appliquer certains concepts   
mentionnés précédemment. 

Nous sommes intervenus auprès d’un client qui utilise un modèle de prédiction des prix concurrentiels comme aide à la décision afin de calibrer ses propres prix. Le modèle en question avait une bonne performance dans la majorité des cas mais avait deux inconvénients : 

  * Il manquait de robustesse face aux éléments imprévus : crises politiques, économiques, sanitaires, etc… 
  * Il ne donnait aucun indicateur de fiabilité sur ses prédictions : les utilisateurs du modèle n’avaient donc aucun indice sur comment utiliser les prédictions. 



Le manque de robustesse face aux éléments imprévus est illustré dans le graphique ci-dessous. En effet, on y retrouve les variations de prix d’une matière première en fonction du temps, ainsi que les prédictions faites par le modèle. On remarque que le prix augmente drastiquement lors d’une crise géopolitique majeure, mais que les prédictions du modèle restent stables : le modèle ne peut pas anticiper ce genre d’évènement. 

![](https://www.quantmetry.com/wp-content/uploads/2023/06/ia-confiance-robustess-mapie.png)

L’instabilité d’un modèle face aux crises est impossible à résoudre. En effet, un modèle apprend des données passées un comportement passé, et il est impossible pour lui d’extrapoler à des situations totalement nouvelles car on sort de son domaine de validité. En revanche, l’indicateur sur la fiabilité des prédictions est une problématique que nous pouvons résoudre afin d’apporter de la valeur ajoutée ! 

Nous avons donc adopté cet angle d’attaque afin de robustifier l’utilisation du modèle : la bibliothèque [ MAPIE ](https://github.com/scikit-learn-contrib/MAPIE) (solution open-source développée par Quantmetry dans le but de quantifier les incertitudes) a été utilisée afin de rajouter des incertitudes aux prédictions du modèle. Les opérationnels sont donc maintenant en mesure de savoir à quel point le modèle est sûr de lui afin d’utiliser ses prédictions en conséquence ! Les incertitudes de prédiction sont alors utilisées comme un résumé des erreurs réalisées par le modèle dans le passé. Si l’intervalle de prédiction est large, on sait que le modèle a été mauvais dans le passé sur des points similaires, et il vaut mieux ne pas accorder trop d’importance à sa prédiction. Cela permet de circonscrire le modèle à son domaine de validité, CQFD ! 

[ ![Reliable Ai](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-Reliable-Ai.svg) ](https://www.quantmetry.com/experts/#reliableia)

Les membres de l’ [ expertise Reliable AI ](https://www.quantmetry.com/experts/#reliableia) développent des modèles performants, fiables et maîtrisés, sur l’ensemble du cycle de vie, pour une IA de confiance. 

* * *

![Lucas Michelis](https://www.quantmetry.com/wp-content/uploads/2023/04/lmi-pic.jpg)

[ Lucas Michelis  ](https://www.linkedin.com/in/lucas-michelis/)

Data Scientist chez Quantmetry 

Data scientist chez Quantmetry depuis plus de 2 ans, Lucas a eu l’occasion de travailler sur des missions diverses et variées dans le secteur de l’assurance et de l’industrie du luxe. Il accompagne maintenant l’expertise Reliable AI sur toutes les problématiques liées à l’IA de confiance. 
