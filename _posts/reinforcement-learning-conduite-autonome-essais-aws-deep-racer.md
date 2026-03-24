# reinforcement-learning-conduite-autonome-essais-aws-deep-racer
Wayback Machine URL: https://web.archive.org/web/20230129163634/https://www.quantmetry.com/blog/reinforcement-learning-conduite-autonome-essais-aws-deep-racer/
Archive date: 2023-01-29

Recherche et développement 

20/05/2019 

#  Le reinforcement learning et la conduite autonome : Nos essais sur AWS Deep racer 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Freinforcement-learning-conduite-autonome-essais-aws-deep-racer%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Le%20reinforcement%20learning%20et%20la%20conduite%20autonome%20%3A%20Nos%20essais%20sur%20AWS%20Deep%20racer&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Freinforcement-learning-conduite-autonome-essais-aws-deep-racer%2F "Twitter")

* * *

Temps de lecture : 15 minutes 

![Quantmetry.com : Le reinforcement learning et la conduite autonome : Nos essais sur AWS Deep racer](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/deep-racer-min.png)

Nous vous proposons dans cet article une introduction au reinforcement learning. Nous illustrerons notre propos par un cas d’usage de conduite autonome par l’intermédiaire du service AWS Deep Racer. Ce service est un championnat mondial de voitures miniatures et autonomes. Il vise notamment à promouvoir l’accès à une branche du machine learning de plus en plus populaire : l’apprentissage par renforcement (Reinforcement Learning en anglais). Nous avons eu accès à une version bêta du service (à l’heure de l’écriture de ces lignes il n’est pas sorti en France) et pu soumettre un modèle lors de l’AWS Summit Paris. 

####  Une introduction à l’apprentissage par renforcement 

L’apprentissage par renforcement est défini comme l’apprentissage par un  **agent** (un drone, Super Mario, une fourmis, etc) d’une séquence optimale d’actions dans un  **environnement** totalement ou partiellement connu. Cette méthode s’attaque au problème de la  **planification** (à la différence de la  **prédiction** pour l’apprentissage supervisé classique). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/Fig1.png)

_ Illustration : Schéma de fonctionnement de l’apprentissage par renforcement. L’objectif est de maximiser la somme des récompenses obtenues au cours du temps  _

Cette réalisation d’une tâche séquentielle implique que l’on soit capable de simuler  la réponse de l’environnement à des actions effectuées au cours du temps. Alors qu’un modèle de machine learning nécessite des données d’entrées statiques, un modèle d’apprentissage par renforcement a besoin d’un mécanisme permettant de générer de nouvelles données en fonction des actions choisies. Cette typologie de problème se distingue donc de l’apprentissage classique par l’existence d’une  **boucle de rétroaction entre un environnement et un agent** implémentant le modèle (l’agent étant l’entité effectuant les actions dans l’environnement). 

####  La récompense, concept central de l’apprentissage par renforcement 

Comme énoncé précédemment un agent d’apprentissage par renforcement interagit avec un environnement pour réaliser une tâche. Cependant comment guider l’agent de manière à ce qu’il apprenne quelque chose ? Contrairement à l’apprentissage supervisé il n’y a pas de label stipulant qu’il fallait prendre telle ou telle action dans une situation donnée. En revanche on sait estimer si l’agent a réalisé la tâche qu’on lui a donné ou s’il s’est trompé. L’apprentissage par renforcement reflète donc un processus d’  **essais et** d’  **erreurs** qu’on applique naturellement dans l’apprentissage d’une tâche. Par exemple, tout le monde a appris à rouler à vélo après avoir souffert de chutes maladroites, ou en comprenant comment maîtriser l’équilibre avec l’accélération, tout en étant acclamé et encouragé par nos amis ou parents. On sait donc dire si une situation dans laquelle se trouve l’agent est bonne ou mauvaise sans avoir besoin de lui dire explicitement quelle action il aurait dû réaliser. Cette notion de bonne ou mauvaise situation est quantifiée par la  **fonction de récompense.** En vérité la “vraie” quantité à optimiser est la somme des récompenses obtenues au cours du temps plutôt que la récompense instantanée. En effet une bonne action à court terme peut mener à une situation catastrophique (par exemple accélérer dans un virage si la récompense est la vitesse instantanée). 

Également, le processus  **d’essais et d’erreurs** est central en apprentissage par renforcement et est représenté par le “  **dilemme exploration/exploitation** ”. Ce dilemme stipule notamment que dans un environnement partiellement connu, on ne connaît pas avec certitude la meilleure action à effectuer et il faut donc quelquefois choisir une action dont le résultat est incertain et pas forcément celle qui amène à la récompense cumulée observée la plus grande. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/Fig2.png)

_ Une illustration du dilemme exploration/exploitation (Source: UC Berkeley AI course  _ [ _ slide  _ ](http://ai.berkeley.edu/lecture_slides.html) _ ,  _ [ _ lecture 11  _ ](http://ai.berkeley.edu/slides/Lecture%2011%20--%20Reinforcement%20Learning%20II/SP14%20CS188%20Lecture%2011%20--%20Reinforcement%20Learning%20II.pptx) _ .)  _

####  Les autres concepts prédominants 

On vient de voir l’importance de la fonction de récompense pour le problème d’apprentissage par renforcement. Cependant d’autres quantités apparaissent naturellement pour traiter cette problématique : 

  *     * **Les actions** : Ensemble de ce que peut faire l’agent à chaque instant. Cet ensemble est souvent de taille finie pour des questions de simplification. 
    * **Les états** : Une “synthèse” de l’observation de l’environnement à un temps donné, utilisé par l’agent pour choisir une action. 
    * **La stratégie** : Ce qu’apprend l’agent, une fonction qui détermine l’action choisie en fonction de l’état observé. 



  * **Episode : Il s’agit de l’ensemble des étapes ayant conduit à la réalisation d’une tâche par l’agent.  **



Pour plus d’informations sur le reinforcement learning, nous invitons le lecteur à lire  [ cet article  ](https://www.quantmetry.com/comment-apprend-on-aux-machines-a-tuer-des-aliens/) traitant du reinforcement learning dans les jeux-vidéos ainsi que  [ cet article  ](https://www.quantmetry.com/alphazero-1-algorithme-3-jeux-de-plateau-maitrises/) traitant de Alpha Zero, l’intelligence artificielle de Google Deepmind permettant de jouer à différents jeux de plateaux à un niveau inégalé (échecs, go et shogi). 

####  Formalisation du problème d’apprentissage par renforcement pour Deep Racer 

Maintenant que nous avons une meilleure compréhension de ce qu’est l’apprentissage par renforcement, essayons de transposer cette connaissance au cas d’usage “Deep Racer”. 

L’objectif de la compétition est de faire le meilleur temps au tour sur un circuit. Il s’agit donc d’un contre la montre, ce qui rend le problème plus simple car il n’y a pas de voitures adverses à gérer. Le point clé de la compétition est la conception d’une  **fonction de récompense** et la calibration des paramètres utilisés pour l’algorithme. La partie de Reinforcement Learning est gérée par l’environnement  [ Amazon SageMaker  ](https://aws.amazon.com/fr/sagemaker/) tandis que la simulation de l’environnement est contenue dans le service  [ Amazon RoboMaker  ](https://aws.amazon.com/robomaker/) . Les autres services utilisés sont S3 pour le stockage, et CloudWatch pour la visualisation et le stockage des logs et des métriques. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/Fig3.png)

_ Architecture du service Deep Racer (source :  _ [ _ AWS Deep racer  _ ](https://www.slideshare.net/AmazonWebServices/new-launch-introducing-aws-deepracer-aim367-aws-reinvent-2018) _ )  _

Remarquons que la phase d’apprentissage est réalisé sur un  **simulateur** (AWS “Robomaker”). La course en revanche est effectuée en condition réelle avec une vraie voiture miniature. Il existe donc en pratique une problématique de “domain adaptation” qui n’est pas traitée dans cet article. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/Fig4.png)

_ Illustration : Environnement d’apprentissage simulé par l’intermédiaire de AWS Robomaker  _

À chaque étape de la course, la caméra de la voiture capte une image de taille 160×120. Cela correspond à l’  **état** de l’environnement. L’agent dispose d’un ensemble d’  **actions** , e.g. virer à gauche ou à droite, donner une consigne de vitesse, avec lesquelles il peut interagir avec l’environnement, c’est-à-dire se déplacer. Dès qu’une action est faite l’agent passe à l’état suivant (la prochaine image de la caméra à l’instant t+1). L’agent continue sa suite d’états-actions appelée  **trajectoire** jusqu’à atteindre un nombre maximal d’étapes (l’horizon) ou un  **état terminal** représenté ici par une sortie de piste. Cela signe la fin d’un  **épisode** et le début d’un autre. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/Fig5.png)

_ Illustration : Exemple d’images captées par la caméra frontale de la voiture, entrée du modèle d’apprentissage par renforcement  _

Il s’agit d’un contre la montre. Il faut donc faire terminer à l’agent un tour complet de la piste le plus rapidement possible. Il faut donc inciter l’agent à produire ce comportement. Comment ? Grâce à la fonction de récompense bien entendu ! 

####  Création de la fonction de récompense pour Deep Racer 

Le choix d’une bonne fonction de récompense est un des principaux leviers permettant la résolution d’une tâche. Celle-ci décrit comment l’agent devrait se comporter. Pour le cas de Deep Racer il s’agit d’un paramètre à définir par l’utilisateur. 

Quelques critères permettent usuellement de guider le choix d’une bonne fonction de récompense : 

  * La récompense ne doit pas être trop “sparse” afin de faciliter l’apprentissage. Dans notre cas donner une récompense positive uniquement lorsque la voiture réussit à finir un tour est une mauvaise fonction de récompense, car la plupart du temps l’agent ne va rien recevoir et n’apprend donc pas efficacement. 
  * La récompense doit représenter réellement la tâche à accomplir. Il peut arriver qu’en optimisant le gain d’une récompense définie par l’utilisateur l’agent apprenne un comportement non souhaité. C’est ce qu’on appelle le phénomène de “Reward hacking”. 



Un exemple drôle est celui du robot guépard qui apprend à courir retourné sur son dos (pour plus de détails voir  [ ici  ](https://www.alexirpan.com/2018/02/14/rl-hard.html) ). D’autres exemples célèbres de reward hacking peuvent être trouvés  [ ici  ](https://t.co/mAGUf3quFQ) . 

  * Une récompense positive encourage l’agent à faire durer l’épisode le plus longtemps possible. A l’inverse une récompense négative encourage l’agent à terminer sa tâche le plus rapidement possible. 



Nous avons privilégié l’utilisation d’une récompense plus encourageante que pénalisante. La seule récompense négative a été introduite dans le cas d’une sortie de piste, car il faut absolument l’éviter. Pour le reste nous nous sommes basé sur trois points principaux pour la récompense : 

  1. Récompense positive quand la voiture reste à une distance bornée du centre de la piste. 
  2. Récompense de plus en plus positive quand l’orientation de la voiture est parallèle à la direction de la piste. Nous avons aussi considéré l’option de récompenser la répétition de la même action pour éviter des comportements instables comme le zigzags ou des virages inattendus. 
  3. Finalement nous multiplions le résultat par la vitesse afin de privilégier une allure rapide et ainsi obtenir un meilleur temps. 



![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/Fig6.png)

_ Illustration : heatmap de la récompense obtenue par l’agent pendant une simulation de 500 épisodes.  _

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/05/Fig7.png)

_ Illustration : trajectoires de l’agent au début de l’entraînement (gauche) et à la fin (droite).  _

_ Il apprend !!!  _
