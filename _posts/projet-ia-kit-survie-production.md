# projet-ia-kit-survie-production
Wayback Machine URL: https://web.archive.org/web/20250709231351/https://www.quantmetry.com/blog/projet-ia-kit-survie-production/
Archive date: 2025-07-09

Data Gouvernance 

15/01/2020 

#  Projet IA : votre kit de survie pour la mise en production 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fprojet-ia-kit-survie-production%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Projet%20IA%20%3A%20votre%20kit%20de%20survie%20pour%20la%20mise%20en%20production&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fprojet-ia-kit-survie-production%2F "Twitter") [ ](https://www.quantmetry.com/blog/projet-ia-kit-survie-production/ "Email") [ ](https://www.quantmetry.com/blog/projet-ia-kit-survie-production/ "Copy Link")

* * *

Temps de lecture : 11 minutes 

![Quantmetry.com : Projet IA : votre kit de survie pour la mise en production](https://www.quantmetry.com/wp-content/uploads/2020/01/article-cle-min.png)

✍ [ Mathieu Ringoot ](https://www.linkedin.com/in/mathieu-ringoot-ab4199a3/) & [ Charlotte Ledoux ](https://www.linkedin.com/in/charlotte-ledoux-53b43253/) _/ Temps de lecture : 10 minutes._

Comme expliqué dans notre précédent article “  [ _ POC: pour quoi faire?  _ ](https://www.quantmetry.com/proof-of-concept-why/) _ ”  _ , le POC a ses limites et n’est tout simplement pas fait pour être industrialisé. Rappelons que le POC est nécessaire lorsque l’idée n’a pas encore été acceptée, que vous souhaitez tester une  hypothèse ou une idée innovante. Cela vous donnera une réponse sur la viabilité de l’idée. 

Avant d’entrer dans le vif du sujet du passage en production des projets data attardons nous un peu sur le projet de Clémence. Regardons de plus près la méthode qu’elle a utilisée dans sa société de location de bungalows pour prévoir son taux de remplissage. Elle est partie en quête de ses fidèles data scientists au sein du Datalab pour relever le défi de la prévision. Armés d’un jeu de données et d’une caisse débordant d’algorithmes l’équipe de data science est partie creuser le problème de Clémence. Malheureusement en repartant à leurs bureaux traiter cette problématique entre pairs ils n’ont pas regardé la représentativité des données fournies par Clémence. Ils ne se sont pas aperçus que le format avait évolué par rapport à leur jeu de test. Comme un malheur arrive rarement seul, Clémence a reçu une forte pression sur ce projet avec des délais de livraison très court. Afin de répondre aux contraintes les équipes ont développé au plus vite une solution sur leur environnement propre afin de s’affranchir des délais du service informatique. 

Ce n’est non sans mal que l’équipe a réussi à fournir un algorithme de prévision dans les temps. Clémence a été rapidement convaincue des résultats et a voulu déployer ce nouvel outil.  En lecteur assidu que vous êtes vous pressentez déjà le dénouement de cette histoire.  Ce POC, construit avec des données non représentatives sur une infrastructure différente de celle de production, n’a jamais pu passer à l’échelle et a demandé énormément de développements supplémentaires. 

Afin d’éviter les écueils rencontrés par Clémence nous allons vous présenter notre méthode de  **mise en production de produit IA** au travers du projet de Myrtille travaillant pour un assureur sur un sujet de fraude. Vous l’aurez compris notre méthode va se concentrer sur le passage à l’échelle des algorithmes de data science et non sur le développement d’un POC. 

Avant de parler du produit IA de Myrtille nous allons poser les bases de cette méthode et l’élément essentiel de cette dernière : le prototype. Pour rappel voici un tableau comparatif du POC et du Prototype : 

![](https://www.quantmetry.com/wp-content/uploads/2020/01/tableau-1.png)

Le Prototype est une première ébauche du produit utilisé pour visualiser et comprendre comment le système fonctionnera et comment il sera reçu par l’utilisateur final. Le Prototype n’est qu’une étape dans la construction d’une solution IA, au sein d’un processus complet permettant de passer de l’idée dans l’esprit du client à la mise en production de la solution, mais nous y reviendrons. Regardons ci-dessous dans son ensemble le cycle de développement de la solution :  **il convient d’intégrer dès le départ du projet une vision sur l’architecture cible et les contraintes et exigences associées au projet,** afin d’anticiper le Pilote et le Run. 

![](https://www.quantmetry.com/wp-content/uploads/2020/01/phase.png)

Revenons maintenant à Myrtille, chef de projet data au sein du Datalab chez un assureur depuis plusieurs années. Avec son n+1, elle a collecté les initiatives data auprès des BU et les a priorisé en fonction de la valeur métier estimée et de la faisabilité technique. Le sujet de détection de fraude est ressorti comme priorité N°1 pour l’entité Réclamations.  Il est à noter qu’avoir une liste de sujets prioritaires est un point de départ essentiel mais que cela ne représente hélas que la première marche de ce long escalier qu’est la mise en production. 

Attaquons ensemble la seconde marche qui entame réellement la mise en projet : à savoir le cadrage. 

####  Le Cadrage, pour anticiper les contraintes 

Myrtille a bien compris que l’enjeu métier serait d’identifier des patterns de fraudes existants et d’anticiper les modes opératoires innovants. Dès l’initialisation du projet, il était clair que le but était un déploiement en production et que ce n’était pas un projet purement exploratoire (vous l’aurez compris nous ne parlerons pas de POC ici). 

Myrtille vise un gain financier pour son entité métier, elle réalise une première estimation de P&L (Profit & Loss) sur le périmètre visé en Run, en se basant sur la valeur métier estimée (combien de fraudes seront évitées?).  Lors des premiers ateliers avec ses collègues des métiers, elle cadre les besoins des futurs utilisateurs et commence à définir les KPIs souhaités : pourcentage de transactions traitées automatiquement, taux de transactions vraiment frauduleuses, … Elle réalise également des ateliers de préparation de l’architecture technique de la solution avec des acteurs de la DSI (architecte d’entreprise, RSSI, responsable applicatif, responsable infrastructure IT…). Cela permet aussi d’anticiper la mise en production en répondant aux questions sur le mode d’accès à l’application, le nombre d’utilisateurs estimé, le temps de réponse souhaité, le volume de transactions à traiter par jour, le taux de disponibilité… Nous nous souviendrons de Clémence avec son développement hors sol et des conséquences de ce dernier. 

En parallèle, un audit sur la maturité des données nécessaires au modèle est impératif. Mais pourquoi donc faire de la data gouvernance… Est-ce vraiment utile ? Et oui, c’est un point primordial du cadrage ! En effet cet audit a permis d’évaluer les données suivant 4 dimensions : définition, qualité, accessibilité et exploitabilité. Ainsi nous nous assurons en amont que les données existent, sont stockées en quantité suffisante et dans un format exploitable. 

Notre cadrage est maintenant terminé, nous avons abordé ces trois dimensions : métiers, IT et données. Il est grand temps de rentrer dans le vif du projet avec le développement de notre prototype (on avait dit qu’on y reviendrait). 

####  Le Prototype, pour accélérer la mise en production 

Pendant la construction du modèle, Myrtille a mis en place des interactions hebdomadaires itératives entre son équipe projet et les métiers afin de préciser l’objectif business ou le réorienter. Nous parlons bien ici du coeur de la future solution qu’est le modèle. Les itérations permettent d’intégrer les feedbacks du métier dans le processus et de choisir les features adaptées. Les processus itératifs sont aussi facilement adaptables aux pratiques Agiles (sentez-vous libre d’appliquer la méthode de votre choix: Scrum, Kanban,…). Cela a également permis de s’inscrire dans les processus métiers existants, afin de garantir l’adoption et la pertinence de la solution. 

Si le prototype est développé dans un environnement type “bac à sable” qui n’est pas représentatif de l’environnement final (laissons ce chantier à la phase Pilote), les data scientists de l’équipe de Myrtille ont néanmoins pris soin de respecter les bonnes pratiques du développement logiciel : 

  * Utilisation d’un outil de gestion de version telle la référence Git, 
  * Implémentation des design patterns favorisant la réutilisation du code sans copier/coller, tels que la modélisation objet, 
  * Application fortement modulaire : il est facile de réutiliser un composant développé dans un autre contexte, 
  * Existence de traitements automatisés en vue de l’industrialisation, 
  * Mise en place de tests unitaire et de fonctionnement. 



C’est avec le sourire de satisfaction du travail bien fait que Myrtille va clore la phase de prototype avec la revue de _Go / No-Go_ . Piloter efficacement un projet c’est également savoir l’arrêter si nécessaire. L’objectif de cette revue est de s’assurer que notre prototype répond aux attentes des métiers, que l’architecture cible est définie et (très important) validée par l’IT et que le code répond aux standards de déploiement. 

Myrtille, pilote experte de projets data passe cette formalité et conserve son sourire pour attaquer la prochaine phase : le Pilote. 

####  Le Pilote, pour automatiser les flux 

Là où le prototype se concentrait sur le développement du modèle, le pilote a pour but de développer toute la “tuyauterie” nécessaire au fonctionnement du modèle dans un environnement de production; comprendre la mise en place des flux entrants, l’intégration du modèle et le développement des interfaces de restitution (API, application web). 

Myrtille a bien intégré que la réussite du déploiement de ce cas de détection de fraude réside dans la capacité de l’organisation à déployer et automatiser ses workflows de mise en production sans créer de goulot d’étranglement. Dans cette optique, il convient d’utiliser les outils utilisés par les principes DevOps. Le schéma ci-dessous peut illustrer une méthode DevOps applicable au projet de Myrtille : 

![](https://www.quantmetry.com/wp-content/uploads/2020/01/cycle.png)

Une question naturelle serait de se demander si une application incluant une brique Data Science peut être fidèle à des principes DevOps? Il est en effet possible d’appliquer ces principes non sans quelques ajustements. Par exemple c’est lors de cette phase de Pilote que les tests spécifiques au Machine Learning (sensibilité, reproductibilité) ou à la data science de manière générale (on manquait un peu de Buzzwords dans cet article pour le référencement) doivent être ajoutés. Ces tests seront garants de la santé du modèle dans ce monde de brutes qu’est la production. 

Malgré ce bref focus technique Myrtille reste alerte sur l’objectif d’un pilote qui, outre un premier déploiement restreint, est surtout là pour valider et quantifier les apports métiers de la solution. Pour cela nous suivrons tout au long de cette phase les KPIs métiers et la qualité de données définies lors du cadrage (vous savez la phase dont on a parlé il y a une éternité ?). 

Après tout ce travail abattu ne serait-il pas temps de regarder l’humain derrière tout ça ? 

####  L’équipe pluridisciplinaire, nécessaire à chaque étape 

Une équipe est quelque chose de vivant qui est amenée à évoluer au gré des différentes étapes du projet. Nous noterons cinq profils essentiels (ceci n’est bien sûr pas une liste exhaustive et des profils complémentaires peuvent apparaître). 

  * Le product owner 
  * Le data architect 
  * Le data scientist 
  * Le data engineer 
  * Le développeur Front 



Regardons comment la typologie de l’équipe de Myrtille a évolué au cours du projet : 

![](https://www.quantmetry.com/wp-content/uploads/2020/01/charge.png)

Notons la présence du data architect dans les premières phases du projet. Il prendra le rôle de garant vis à vis des responsables IT pour la pertinence de l’architecture cible et accompagnera les équipes techniques lors de la construction du prototype et du pilote. 

Et si nous parlions un peu plus de Myrtille et de son rôle dans le projet? 

Myrtille a le rôle de Product Owner. C’est un rôle essentiel car il est garant de l’adéquation du produit avec les besoins utilisateurs. Le Product Owner en tant que capitaine doit avoir une vision claire de la trajectoire qu’il souhaite insuffler à son produit. C’est avec cette vision claire et suffisamment partagée avec son équipe que le produit pourra se développer et convaincre ses utilisateurs. Comme le disait Sénèque: “Il n’est pas de vent favorable pour celui qui ne sait pas où il va”. Un autre élément à garder à l’esprit pour un Product Owner est de toujours garder l’utilisateur final au centre de sa vision. 

Comme pour le prototype une revue de _Go / No-Go_ clôture le pilote, il s’agira cette fois de mesurer les gains effectifs générés par le projet et son adoption par les utilisateurs pilotes afin de valider sa pertinence. Myrtille en Product Owner avisée a pris soin d’accompagner ses utilisateurs avec un plan de conduite du changement afin de maximiser l’adoption. 

Il est temps d’attaquer la dernière étape de ce projet : la mise en production. 

####  Le Run, et son contrôle opérationnel 

Myrtille a préparé en amont son plan de déploiement comprenant notamment son programme de formation et sensibilisation à cette nouvelle solution, ainsi que le plan d’ouverture du service et le mode d’exploitation (monitoring, contrôles). Elle a tout prévu avec le futur responsable d’application du service informatique qui reprendra la main sur la solution. 

La mise en production d’un modèle n’est en effet que le début d’une phase opérationnelle qui va nécessiter une mise en place de contrôles sur : 

  * L’ingestion des données, accompagnée de KPIs à mettre en oeuvre, ainsi que sur la QA/QC (Quality Assurance/Quality Control) 
  * Le contrôle opérationnel du run, sur les données d’entrée, sur les performances (comparaison entre les performances théoriques et celles obtenues), sans oublier la vérification des biais. 



Malgré tous ces contrôles, au fil du temps, les fraudeurs inventeront de nouvelles techniques pour outrepasser les barrières anti-fraude, ainsi le modèle de détection de fraude entraîné à l’instant T deviendra rapidement obsolète. Comment faire pour mettre en production des modèles assurant une performance constante des systèmes anti-fraude? 

Une solution est de mettre en place des algorithmes adaptatifs de type “comités d’experts” (forêts aléatoires adaptatives). Ces algorithmes s’entraînent de manière incrémentale sur un flux de données, ont un système de surveillance de performances intégré, et réinitialisent leurs mémoires automatiquement et de manière optimale quand leur performance fait défaut. De fait, en prenant en compte la dynamique temporelle des fraudeurs, Myrtille a réussi à faire augmenter le nombre de fraudes bloquées à raison sans impacter la gêne client, et le système de priorité des investigations a vu sa rentabilité croître de 20%. 

####  L’intégration continue, pour faire évoluer le produit 

Le déploiement en continu permet d’automatiser la livraison des versions intermédiaires du produit. L’idée est de commencer par un produit basique et de l’enrichir au fil des itérations. Cela permet à l’équipe technique de livrer plus facilement et plus fréquemment les versions d’un produit au fur et à mesure qu’il est construit. L’objectif est de disposer d’un produit fonctionnel qui soit testé et directement utilisable. Par exemple, dès qu’une évolution est soumise, elle sera automatiquement compilée, intégrée, testée et déployée. Ce fonctionnement repose sur la mise en place d’une stack CI/CD, utilisant des pipelines avec les principales étapes suivantes : versioning, tests unitaires, tests d’intégration, build et publication.  Si les tests unitaires et d’intégrations ne passent pas, les étapes suivantes ne sont pas exécutées. 

Idéalement, le temps entre la création d’une nouvelle feature et le moment où elle est testée par un utilisateur final doit être court et fréquent. Il faut cependant rester réaliste dans la fréquence des _releases_ et ne pas confondre vitesse et précipitation afin de conserver un haut niveau de qualité. 

Cette dernière notion d’intégration conclut le cycle de notre méthodologie projet pour une mise en production efficace. Myrtille poursuivra l’animation de son produit en entamant plusieurs nouveaux cycles correspondant à de nouvelles fonctionnalités. 

Si cet article vous a plu et que vous souhaitez en apprendre plus, nous vous invitons à lire notre livre blanc  [ _ IA en production  _ ](https://www.quantmetry.com/download/13083/) _ .  _

#####  ✍ [ Mathieu Ringoot ](https://www.linkedin.com/in/mathieu-ringoot-ab4199a3/) & [ Charlotte Ledoux ](https://www.linkedin.com/in/charlotte-ledoux-53b43253/)

#####  **Bibliographie**

[ https://martinfowler.com/articles/continuousIntegration.html  ](https://martinfowler.com/articles/continuousIntegration.html)

[ https://storage.googleapis.com/pub-tools-public-publication-data/pdf/aad9f93b86b7addfea4c419b9100c6cdd26cacea.pdf  ](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/aad9f93b86b7addfea4c419b9100c6cdd26cacea.pdf)
