---
layout: post
title: premier-etape-cycle-vie-modeles
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129154041/https://www.quantmetry.com/blog/premier-etape-cycle-vie-modeles/
---
IA Strategy 

20/01/2020 

#  En route vers le cycle de vie des modèles ! 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fpremier-etape-cycle-vie-modeles%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=En%20route%20vers%20le%20cycle%20de%20vie%20des%20mod%C3%A8les%20%21&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fpremier-etape-cycle-vie-modeles%2F "Twitter")

* * *

Temps de lecture : 25 minutes 

![Quantmetry.com : En route vers le cycle de vie des modèles !](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/article-gma-min.png)

_ ✍ [ Grégoire Martinon ](https://www.linkedin.com/in/gregoire-martinon/) / Temps de lecture : 20 minutes. _

[ IA en production [1] ](https://www.quantmetry.com/les-livres-blancs/) , ce n’est pas une mince affaire. Les modèles d’intelligence artificielle ont ceci de particulier qu’ils sont probabilistes et qu’ils dépendent fortement des données qu’ils ingèrent. Les données elles-mêmes sont soumises aux aléas du monde qui les génère ! En conséquence, la plupart des modèles prédictifs voient leurs performances chuter [ dès la mise en production [2] ](https://www.forbes.com/sites/forbestechcouncil/2019/04/03/why-machine-learning-models-crash-and-burn-in-production/#3a0395262f43) . Il faut alors ré-entraîner le modèle pour espérer maintenir son niveau de fonctionnement : c’est ce qu’on appelle le cycle de vie. 

####  Dessine-moi un cycle de vie 

Les entreprises digitales ont déjà un cycle de vie à gérer, **celui de la donnée** (voir Figure 1). Il consiste principalement à ingérer la donnée à la source, à la valider et à la redistribuer auprès des acteurs ou des solutions métier. Le cycle de vie de la donnée est déjà quelque chose de complexe et technique à gérer, mais qui s’accompagne via des [ méthodes de gouvernance [3] ](https://www.quantmetry.com/gouvernance-data-aventure-humaine/) . 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/definition-1024x315.png)

Figure 1 : le cycle de vie des modèles est une conséquence du cycle de vie des données. D’abord pour prédire, le modèle doit être branché sur des données émises au jour le jour. Ensuite pour le ré-entraînement, le modèle doit avoir la possibilité de s’adapter sur des données fraîches et labellisées pour maintenir sa performance. 

Arrive alors un nouvel élément : le **modèle prédictif** . Cela peut être une moyenne, une règle métier ou un modèle de _machine learning_ , il s’agit dans tous les cas d’un mécanisme qui se nourrit de données passées pour propager une information vers le futur. Le modèle va donc devoir se brancher sur le cycle de vie des données de deux manières différentes : pour s’entraîner d’une part et pour prédire d’autre part. 

> Or, un modèle figé est un risque. 

Pensez par exemple à un système de [ détection de fraude [4] ](https://www.quantmetry.com/adapter-evolution-fraude/) , où l’adaptation des fraudeurs rend caduque tout modèle statique. En réalité, la donnée n’est autre qu’un signal émis par le monde extérieur, et ce monde est en constante évolution. En termes plus techniques, l’hypothèse selon laquelle “les données sont indépendantes et identiquement distribuées”, omniprésente en intelligence artificielle, est violée dans la réalité. 

D’ailleurs, quand la performance du modèle chute, un abus de langage courant affirme que “le modèle a dérivé”. Or c’est complètement faux : ce sont les données qui ont évolué, pas le modèle, et c’est justement là tout le problème. 

Le cycle de vie est la science qui va permettre de résoudre les problèmes suivants : comment surveiller un modèle ? comment détecter une baisse de performance ? comment s’adapter à l’évolution de la donnée ? 

####  Bien conduire son cycle de vie 

Bien gérer son cycle de vie, c’est faire preuve de bon sens. Et ce bon sens est déjà acquis dans d’autres domaines de la vie courante. On peut par exemple filer la métaphore de la voiture (voir Figure 2 et Table 1). On distingue alors deux phases : la mise en production du modèle et son cycle de vie. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/metaphore-1024x484.png)

Figure 2 : Le cycle de vie des modèles repose sur du bon sens, et peut être comparé au cycle de vie d’une voiture. Le modèle est le moteur, et le système d’information (SI) la voiture. La direction du SI (DSI) est en charge de conduire le modèle et le métier est en charge de donner les directions à suivre. Comme pour une voiture, le cycle de vie des modèles va devoir anticiper les pannes et apporter des solutions à tous les niveaux. 

#####  Mise en production 

C’est le processus de développement de l’intelligence artificielle jusqu’à son utilisation. 

Le data scientist (l’ingénieur automobile) crée un modèle (un moteur). 

Or un modèle isolé n’a aucune valeur en soi. Il ne prend sa valeur qu’un fois inséré dans un code de qualité (le châssis) qui doit gérer l’interaction du modèle avec le monde extérieur. C’est ce code et ce modèle qui sont livrés à la DSI (le conducteur). La DSI ne sait pas créer un modèle, mais elle sait le déployer (elle sait conduire). 

Un troisième acteur prend place, c’est le métier (le copilote). Il ne sait ni créer ni déployer un modèle, mais il détermine son cas d’usage métier (il donne l’itinéraire du trajet et tient le budget). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/analogie-1-475x500.png)

Table 1 : dictionnaire d’analogies entre le déploiement d’un service automobile et le déploiement d’un service d’intelligence artificielle. 

#####  Cycle de vie 

C’est tout ce qui advient au cours de l’existence du modèle une fois mis en service. 

La conduite du changement (le code de la route) permet d’insérer le modèle dans le processus de l’entreprise, en définissant des droits d’accès, d’utilisation et en permettant l’adhésion du plus grand nombre. 

Ensuite, pour prédire correctement, les données servies au modèle (l’essence) doivent obéir à des standards de qualité (Diesel, SP 98), sous peine de fournir des valeurs aberrantes, voire inexistantes. 

Le  _monitoring_ de modèle permet de surveiller son bon fonctionnement, sa performance et les retours terrains (de même qu’il est impensable de vendre une voiture sans tableau de bord). 

L’anticipation des problèmes en production passe par une phase d’audit, ou de validation interne (c’est le contrôle technique). 

Enfin, en cas de problème, il s’agit de déterminer le degré d’autonomie de l’utilisateur : peut-il se contenter de réparer un bug mineur (remettre du liquide de refroidissement), ou doit-il ré-entraîner le modèle sur un nouveau jeu d’entraînement rafraîchi (dépanneuse puis garage constructeur) ? 

Ces grandes étapes du cycle de vie des modèles relèvent donc essentiellement du bon sens qui s’applique au déploiement de toute solution  _ à l’échelle  _ . 

####  Objectifs du cycle de vie 

Pour résumer le cycle de vie va devoir anticiper tous les aléas qui surviennent dans la vie d’un modèle en production et fournir des solutions idoines. Les trois principaux objectifs du cycle de vie sont (voir Figure 3) : 

  * **mesurer le retour sur investissement (ROI) :** le modèle étant en production, il est primordial de mesurer son impact métier et son retour sur investissement, si possible en euros. Comme toute mesure, elle doit s’accompagner d’incertitudes. 
  * **évaluer le risque :** il s’agit de construire un modèle robuste aux changements, en tenant compte non seulement du bénéfice de la performance mais aussi du coût de maintenance (acquisition de données labellisées, ré-entraînement, redéploiement). 
  * **assurer la non-régression :** au-delà des dérives de données, il faut aussi se prémunir des dérives proactives de modèle (autrement dit les bugs). C’est toute la méthodologie DevOps appliquée à l’intelligence artificielle qui entre en jeu, on parle même de [ DataOps ou MLOps [5] ](https://www.oreilly.com/radar/lessons-learned-turning-machine-learning-models-into-real-products-and-services/) . 



![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/objectifs-1024x466.png)

Figure 3 : Objectifs du cycle de vie. Étant la science des modèles en production, le cycle de vie est naturellement la science de la mesure du retour sur investissement (ROI). C’est aussi la science de la mesure du risque et des incertitudes, qui ont autant si ce n’est plus de valeur en production que la performance. Enfin, il s’agit d’assurer la non-régression du service d’intelligence artificielle en renforçant les flux de traitements pour les rendre plus robustes. 

####  Les questions que posent le cycle de vie 

> L’organisation, ou plutôt l’absence d’organisation, est le premier frein à la mise en place d’un cycle de vie des modèles. 

Dans un projet de _machine learning_ de bout en bout, on peut distinguer trois niveaux de réalisation (voir Figure 4) : 

  * **organisationnel :** c’est le volet qui va s’intéresser aux responsables, aux compétences et à l’impact métier. L’organisation, ou plutôt l’absence d’organisation, est le premier frein à la mise en place d’un cycle de vie des modèles. 
  * **scientifique :** c’est le volet qui va s’intéresser à la robustesse des modèles, à l’efficacité d’un système de détection de dérive, et aux solutions de redressement de la performance. 
  * **technologique :** c’est le volet qui assure le branchement du modèle au cycle de vie de la donnée. Il va s’intéresser à la qualité de la donnée, à la gestion d’un historique (ou d’une banque) de modèles, ainsi qu’au déploiement rapide et sûr de la solution préconisée par le volet scientifique. 



![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/questions-1024x452.png)

Figure 4 : les questions que pose le cycle de vie des modèles, d’un point de vue organisationnel, scientifique et technologique. 

####  Le cycle de vie pas à pas 

Aujourd’hui, les problèmes et les questions que posent le cycle de vie sont bien identifiés par le marché. C’est plutôt l’aspect mise en oeuvre des solutions qui fait défaut. Dans cette partie, on propose donc une feuille de route cycle de vie des modèles (voir Figure 5), qui répond à la question suivante : 

> “Je m’apprête à mettre un modèle en production, que dois-je faire et par où commencer ?” 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/autoroute-1024x418.png)

Figure 5 : feuille de route cycle de vie des modèles. Avant d’entrer sur l’autoroute, il faut emprunter une voie d’accélération avec trois étapes obligatoires (en vert) : définir le projet cycle de vie et les ressources à y allouer (1), consolider une chaîne de traitements robuste (2), et installer un système de monitoring (3). Une fois ces pré-requis mis en place, on peut alors aborder le cycle de vie des modèles proprement dit, en s’attaquant à la robustesse du modèle (4), au système de détection de dérive (5), à l’intelligibilité de la dérive (6), à l’adaptation du modèle (7), aux tests en conditions réelles (8) et à la documentation continue (9). 

#####  Etape 1 : définir les responsables 

> Le profil de _product owner_ est le plus rare et le plus difficile à trouver. 

Il s’agit de définir qui construit le moteur, qui conduit, et qui fait le plein. Le cycle de vie des modèles ne peut pas exister s’il n’est mis entre les mains d’un responsable ( _product owner_ ), avec une bonne compréhension métier, dont la mission est de construire et de maintenir le modèle en production. C’est le profil le plus rare et le plus difficile à trouver. Il doit gérer une équipe comprenant au minimum (voir Figure 6) : 

  * **un responsable qualité de donnée :** souvent un (ou plusieurs) _data engineer_ , il doit construire et assurer la qualité de la donnée d’entrée, en consolidant un référentiel de donnée. Il doit agir côté DSI et côté DataLab. 
  * **un responsable robustesse du modèle :** souvent un _data scientist,_ il doit non seulement assurer la performance du modèle mais également quantifier sa robustesse et donc son incertitude. Il doit agir côté DataLab et côté métier. 
  * **un responsable mise en production :** c’est le profil _ML engineer_ , qui doit savoir orchestrer et mettre en oeuvre la chaîne de traitement sur la plateforme de production. Il doit agir sur tous les fronts DSI, DataLab et métier. 
  * **un responsable surveillance et alerte :** souvent un _data analyst_ orienté métier ou _data science_ , il est en charge de surveiller les indicateurs de performance du modèle et d’alerter les bons éléments en cas de problème. 



![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/etape1-500x418.png)

Figure 6 : exemple d’une organisation projet cycle de vie qui a fait ses preuves. Le point clef est de définir un responsable côté métier ( _product owner_ ), qui ait à la fois une sensibilité sur les enjeux techniques et sur les enjeux _business_ . Sa mission est d’orchestrer toutes les compétences nécessaires au cycle de vie. 

C’est la mixité et la proximité des compétences qui assure la réactivité et la fluidité du système. Par ailleurs, il faut réussir à octroyer une certaine autonomie à chaque pôle de responsabilité, en rédigeant un document d’exploitation qui permet de gérer rapidement les problèmes connus les plus courants. 

#####  Etape 2 : consolider les flux de traitements 

> Il y a globalement quatre points faillibles dans une chaîne de traitements : les données, le code, le modèle et l’infrastructure. 

C’est le contrôle technique 
