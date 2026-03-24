# pris-en-flagrant-delit-par-une-ia-comment-detecter-les-attaques-de-guichets-automatiques-bancaires
Wayback Machine URL: https://web.archive.org/web/20221001014509/https://www.quantmetry.com/blog/pris-en-flagrant-delit-par-une-ia-comment-detecter-les-attaques-de-guichets-automatiques-bancaires/
Archive date: 2022-10-01

Time Series 

14/10/2019 

#  Pris en flagrant délit par une IA ! Comment détecter les attaques de guichets automatiques bancaires. 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fpris-en-flagrant-delit-par-une-ia-comment-detecter-les-attaques-de-guichets-automatiques-bancaires%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Pris%20en%20flagrant%20d%C3%A9lit%20par%20une%20IA%20%21%20Comment%20d%C3%A9tecter%20les%20attaques%20de%20guichets%20automatiques%20bancaires.&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fpris-en-flagrant-delit-par-une-ia-comment-detecter-les-attaques-de-guichets-automatiques-bancaires%2F "Twitter")

* * *

Temps de lecture : 14 minutes 

![Quantmetry.com : Pris en flagrant délit par une IA ! Comment détecter les attaques de guichets automatiques bancaires.](https://quantmetry.b-cdn.net/wp-content/uploads/2019/10/article-gma-min.png)

Il existe près de 55 000 guichets automatiques bancaires (GAB) en France [1]. Chaque guichet automatique peut contenir jusqu’à 150 000 euros en liquide [2]. De quoi largement attiser les convoitises… 

####  Les attaques de GAB 

Il y a plusieurs moyens pour extraire de l’argent d’une boîte en métal : 

  * **La force brute** , par insertion de pelleteuse ou de voiture brûlée dans le GAB afin de l’ouvrir [3] (voir Figure 1). Efficace et certaine, cette technique représente un coût pour l’attaquant, qui doit acheter, louer, ou tout simplement “obtenir” un véhicule. S’il s’agit d’un engin de chantier, sa location/usurpation est facilement traçable par les services de police. 
  * **Les explosifs** , notamment en remplissant le caisson par un mélange de gaz adéquat [4]. Peu coûteuse et facile à mettre en place, cette technique peut toutefois dégrader fortement le contenu du GAB. 
  * **Le skimming** , qui consiste à augmenter la fente carte d’un [ enregistreur d’empreinte magnétique ](https://www.reddit.com/r/pics/comments/5ic7yc/thanks_reddit_you_saved_me_from_potential_credit/?ref=share&ref_source=embed&utm_content=media&utm_medium=post_embed&utm_name=32794ce5fff940348606e6621c0db6b8&utm_source=embedly&utm_term=5ic7yc) [5]. Couplé à un système de caméra caché pour obtenir le code, le fraudeur peut récupérer l’empreinte sur son téléphone à distance, imprimer une toute nouvelle carte bleue, clone de l’originale, et l’utiliser normalement. Cette technique demande des compétences assez rares ainsi qu’un investissement dans le dispositif d’enregistrement. 
  * **Le piratage informatique** , qui consiste à prendre le contrôle du logiciel du GAB et à lui ordonner de se purger de son contenu [6]. C’est l’attaque qui nécessite le plus de savoir-faire, et une connaissance pointue de la structure physique et informatique du GAB. 
  * **L’attaque de personnes** , qui consiste souvent en une diversion, qui peut aller de la prestidigitation à l’attaque au rat mort [7], en passant par la violence physique. C’est de loin la méthode la moins coûteuse, mais aussi parmi les plus risquées car elle nécessite d’agir en plein jour devant témoins. 



![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/10/bnp.png)

Figure 1 : un exemple d’attaque au chariot élévateur [8]. 

On recense ces centaines d’attaques de GAB tous les ans sur le territoire français [2]. Du point de vue de la banque, les attaques aux explosifs sont les plus coûteuses car en plus de l’argent dérobé, elles soufflent toute l’agence accueillant le GAB, empêchant des collaborateurs de se rendre sur leur lieu de travail et des clients de venir voir leurs conseillers. 

Les parades standards reposent principalement sur le renforcement physique du GAB ou la maculation automatique de billet suite à percussion. Là où la Data Science intervient, c’est sur le traitement automatisé de la vidéo-surveillance. 

####  Vidéo-surveillance : des données sous contraintes 

Les données de vidéo-surveillance sont une source directe d’informations qui permet de savoir ce qu’il se passe sur directement sur site. Ce sont donc les données de choix pour réussir à détecter les attaques de GAB. Toutefois, elles sont soumises à plusieurs contraintes : 

  * **Diversité :** tous les guichets automatiques sont équipés de caméra différentes (marques, résolution, angles de vues). 
  * **Volume :** une caméra filmant H24 génère environ 1 téraoctet de données par mois. 
  * **Loi :** le stockage de données vidéo filmant un lieu public ne peut dépasser un mois [9]. 
  * **Temps réel :** du point de vue de la banque, seul le flagrant délit a de la valeur, pour épargner le vol de billets et/ou les réparations coûteuses qui en résultent. Ses leviers d’action sont par exemple le déclenchement d’alarmes, l’intervention de la police ou la télé-interpellation [10]. 
  * **Embarqué :** pour des raisons de rapidité et de sécurité, les données doivent être traitées sur site. L’algorithme doit donc héberger directement sur le GAB, et pas sur un serveur distant. 
  * **Absence de labels :** en toute probabilité, un GAB n’a fait l’objet d’aucune attaque ces 30 derniers jours. Cette faible probabilité, combinée à la contrainte légale, rend impossible l’obtention d’extraits vidéo filmant une attaque (sur le périmètre restreint de GAB étudiés), et donc de labels. La détection doit donc être nécessairement non-supervisée. 



Toutes ces contraintes conspirent pour éloigner du champ des possibles les méthodes standards de classification d’images sur la base de jeux de données labellisées. 

####  Stratégie de détection : convertir les vidéos en séries temporelles et détecter les anomalies 

Afin de proposer une solution de détection d’attaques qui obéisse à toutes ces contraintes, on peut envisager la stratégie suivante : 

  1. Détecter des zones riches de sens (visage, mains, outils, véhicules etc.) 
  2. Traquer en temps réel la position de ces différentes zones 
  3. Enregistrer les données de détection uniquement sous forme de séries temporelles 
  4. Détecter les séries temporelles anormales 



Sur la Figure 2, on illustre le procédé de conversion de vidéo en série temporelle. Les avantages de cette méthode sont multiples. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/10/conversion.png)

Figure 2 : conversion d’une vidéo (extrait du film _Kill Bill_ ) en séries temporelles. Sur chaque image, on peut identifier des zones d’intérêts (ici un visage) et n’enregistrer que les 4 nombres qui caractérisent le cadre de détection : positions, hauteur, largeur. En appliquant cette méthode à chaque image d’une vidéo, on obtient donc 4 séries temporelles par objet détecté. 

Tout d’abord, c’est une compression et une anonymisation parfaite : impossible de reconnaître quelqu’un sur la base de quelques nombres. 

Ensuite, l’information encodée est informative : on peut savoir si une personne (ou un objet) est seul, proche ou loin de la caméra, si une personne se baisse, si ses mains sont en train de visser quelque chose en hauteur, quel est le temps de présence devant la caméra etc. 

Enfin, il existe une artillerie standard de détection d’anomalies sur des séries temporelles et de détection de séries temporelles anormales. L’avantage de l’utilisation de GAB est qu’elle est **extrêmement normée** par le logiciel : une interaction normale dure typiquement 90 secondes, le timing des gestes est dicté par les interactions logiciel et l’agencement physique du GAB (fente carte en bas à droite), la position des personnes est debout et immobile. L’information contenue dans les séries temporelles est donc suffisante pour établir un premier niveau de détection de comportements anormaux. 

La conversion en séries temporelles permet donc de résoudre les contraintes légales et de volume. On peut donc extraire un historique très vaste de données. Quant à la brique détection d’anomalies, c’est celle qui répond le mieux à l’absence de labels. La question qui reste en suspens est : peut-on opérer cette solution en temps réel ? 

####  _Deep learning_ et temps réel, un mariage compliqué 

Depuis la percée fulgurante du _deep learning_ en 2012 [11], il est difficile de ne pas considérer les possibilités qu’offrent les réseaux de neurones en matière de détection sur des images. La Figure 3 illustre les possibilités offertes par le deep learning en matière de détection. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/10/deep.png)

Figure 3 : possibilités offertes par les réseaux de neurones en terme de détection. De gauche à droite : la détection de visage, la détection de repères faciaux, la détection de poses corporelles, la détection de poses manuelles, la détection d’objets, et la détection de masques. 

Toutefois, le _deep learning_ coûte cher, en temps de calcul notamment. Par exemple, sur un Mac standard, il faut compter entre 1 et 5 secondes de temps de calcul pour traiter une image ! D’après les développeurs de l’algorithme de détection d’objets Yolo_v3 [12], il est possible de réduire le temps de calcul d’un facteur 5 à 6, pourvu qu’on se dote d’une carte graphique Pascal Titan X à 2000 euros sur la marché [13]… Dernière solution : louer des ressources sur le cloud, ce qui est complètement incompatible avec l’exigence d’algorithme embarqué mentionnée plus haut. 

En réalité, ce problème fait couler beaucoup d’encre dans le monde de la recherche et nourrit depuis plusieurs années une littérature intensive sur la compression des réseaux de neurones (voir à ce propos notre article de blog [14]). 

####  Le _tracking_ , l’alternative temps réel au deep learning 

Face à cette barrière scientifique, technologique et pécuniaire que représente le _deep learning_ temps réel, une solution retient notre attention : c’est le _tracking_ [15]. En effet, les données vidéo ne sont pas un flux d’images aléatoires, elles ont une auto-corrélation forte : deux images consécutives sont, la plupart du temps, très similaires. Le _tracking_ est une famille d’algorithmes qui va justement prendre en compte cette structure particulière pour amoindrir le temps de calcul (voir Figure 4). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/10/tracking_deep_learning.png)

Figure 4 : différence entre la détection et le _tracking_ de zone d’intérêt (ici un visage). La détection est renouvelée à l’identique pour chaque image, tandis que le tracking capitalise sur les images précédentes pour trouver la réponse plus rapidement. 

Le principe du _tracking_ est simple et on l’illustre ci-après pour la détection de visages pour fixer les idées. Sachant le visage sur l’image _n_ , on veut déduire où se trouve le visage sur l’image _n+1_ . Une manière simple de faire est d’utiliser un produit de convolution : le visage cible est testé sur toutes les positions possible de l’image source, et on retient la localisation pour laquelle le recouvrement du signal est le plus fort (voir Figure 5). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/10/convolution.png)

Figure 5 : principe du produit de convolution. On teste toutes les positions possibles et pour chacune on relève le recouvrement (somme du produit des pixels 2 à 2). La nouvelle position du visage est attribuée à la zone de recouvrement le plus fort. 

En théorie, c’est une manière sûre de déduire la nouvelle position du visage. En pratique, le produit de convolution est très coûteux en temps de calcul, de par l’exhaustivité des produits effectués et des localisations testées. Cependant, grâce au théorème de convolution [16], on peut réduire le nombre d’opérations à une seule ! Le tour de passe-passe est accompli en passant dans l’espace de Fourier : 

_La transformée de Fourier d’un produit de convolution entre f et g est le produit des transformées de Fourier de f et de g._

On illustre son fonctionnement sur la Figure 6. La philosophie est identique au _machine learning_ : 

  * **Phase d’apprentissage :** on part d’une image labellisée (comprendre : avec un visage identifié). On la sépare en des variables explicatives _X_ (les pixels noir et blanc), et une variable cible _Y_ (une image binaire indiquant là où se trouve le visage). L’astuce consiste à transformer _X_ et _Y_ dans l’espace de Fourier. Dans cet espace, le théorème de convolution nous donne d’un coup d’un seul le filtre _F_ qui relie _X_ à _Y_ : c’est simplement le rapport des deux images transformées. 
  * **Phase d’inférence :** une nouvelle image non-labellisée arrive (comprendre : sans visage détecté pour l’instant). On la passe dans l’espace de Fourier. Par application du filtre, on trouve la transformée de Fourier de la réponse. En repassant dans l’espace réel, on obtient la prédiction ` \hat{Y} ` de localisation. 



![](https://quantmetry.b-cdn.net/wp-content/uploads/2019/10/fft.png)

Figure 6 : application du théorème de convolution au _tracking_ . C’est en réalité du _machine learning_ . Plus précisément, il s’agit de construire un modèle linéaire dans l’espace de Fourier. L’apprentissage ne requiert qu’une image et est instantané. 

En réalité, le _tracking_ n’est rien d’autre qu’un modèle linéaire dans l’espace de Fourier, et dont le théorème de convolution fournit une solution analytique. L’absence de descente de gradient rend l’apprentissage instantané sur une jeu d’entraînement qui consiste en une seule image : l’image précédente (en réalité dans [15] c’est une poignée d’images qui est utilisée, à des fins de stabilisation). 

Par rapport à un réseau convolutif à une couche, le temps de calcul est donc accéléré car : 

  * la ph 


