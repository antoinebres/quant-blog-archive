---
layout: post
title: vers-metier-machine-learning-engineer
date: 2025-06-20
url_wayback_machine: https://web.archive.org/web/20250620044404/https://www.quantmetry.com/blog/vers-metier-machine-learning-engineer/
---
IA de confiance, Machine Learning 

07/09/2022 

#  Vers le métier de Machine Learning Engineer 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fvers-metier-machine-learning-engineer%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Vers%20le%20m%C3%A9tier%20de%20Machine%20Learning%20Engineer&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fvers-metier-machine-learning-engineer%2F "Twitter") [ ](https://www.quantmetry.com/blog/vers-metier-machine-learning-engineer/ "Email") [ ](https://www.quantmetry.com/blog/vers-metier-machine-learning-engineer/ "Copy Link")

* * *

Auteur : [ Hugo Perrier ](www.linkedin.com/in/hugoperrier)

Temps de lecture : 8 minutes 

![Quantmetry.com : Vers le métier de Machine Learning Engineer](https://www.quantmetry.com/wp-content/uploads/2022/08/main-image.jpg)

En 2017 : « _Mon entreprise doit faire de l’IA, j’ai besoin de Data Scientists !_ »   
En 2022 : « _Mon entreprise doit déployer des solutions IA en production, j’ai besoin de Machine Learning Engineers !_ » 

Le Machine Learning Engineer ou MLE est le nouveau métier en demande dans les entreprises. Contrairement au Data Scientist, son rôle principal n’est pas de construire un modèle qui permet de répondre à un besoin métier mais de déployer des modèles/solutions IA en production. C’est un rôle clé car une solution IA, aussi pertinente soit-elle n’apporte aucun ROI tant qu’elle n’est pas industrialisée. 

#  Comment devenir Machine Learning Engineer ? 

Le graal est d’avoir une expérience de mise en production d’une solution IA en entreprise. Vous pourrez ainsi vous familiariser avec les (nombreux) outils et technos utilisées pour l’industrialisation. 

Il existe également des bootcamps comme la [ Yotta academy ](https://yotta-academy.com/) qui proposent des programmes intensifs et complets pour se former au métier de Machine Learning Engineer. 

Mais comment faire lorsqu’on sort d’école ou lorsqu’on effectue un changement de carrière ?   
Pas facile de faire de l’industrialisation sans avoir accès à un environnement de prod…   
Dans cet article, je vous propose un guide en 13 étapes pour se construire des bases solides en Machine Learning Engineering et se défendre lors d’un entretien d’embauche. 

### 

#  Sommaire des 13 étapes : 

  1. Définir le problème 
  2. Setup d’un environnement de développement 
  3. Choisir un template de code 
  4. Écrire des tests 
  5. Coder 
  6. Documenter votre code 
  7. Simuler un mode « train » et un mode « prod » 
  8. Intégrer mlflow 
  9. DataBase time 
  10. APIser votre code 
  11. Dockeriser votre code 
  12. Refactorer votre code 
  13. Mettre en place une intégration continue 



##  Étape 1 : Définir le problème 

Choisir un problème de Machine Learning simple qui se base sur de la donnée Open-Source. Vous pouvez par exemple utiliser : 

  * [ Titanic dataset ](https://www.kaggle.com/c/titanic) pour du ML classique 
  * [ MNIST dataset ](https://pypi.org/project/python-mnist/) pour de la CV (Computer Vision) 
  * [ IMDB movie dataset ](https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews) pour du NLP (Natural Language Processing) 



##  Étape 2 : Setup d’un environnement de développement 

Un bon environnement de développement permet de coder de façon efficace, confortable et d’éviter de nombreux bugs. Je vous suggère donc de vous familiariser avec les environnements virtuels et d’apprendre à utiliser un IDE : 

  * [ Environnement virtuel ](https://docs.python.org/fr/3/tutorial/venv.html) : Permet d’isoler vos différents projets python et d’éviter ainsi les conflits de dépendances. Les outils les plus courants sont Virtual Env et Conda. 
  * IDE (Environnement de développement intégré) : Des IDE tels que [ VSCode ](https://code.visualstudio.com/) ou [ PyCharm ](https://www.jetbrains.com/pycharm/) permettent d’explorer, d’éditer et d’exécuter du code tout en offrant pléthore de fonctionnalités qui vous faciliteront la vie ! Vous aurez par exemple du formatage automatique de code, des warnings en cas d’erreurs, des intégrations avec git, etc 



##  Étape 3 : Choisir un template de code 

Se lancer dans un projet python sans template c’est un peu comme commencer à construire une maison sans avoir de plan. Un template de code permet de séparer les différentes parties de votre code et facilitera grandement la maintenance et l’ajout de nouvelle fonctionnalités. 

On pourra ainsi séparer dans différents sous-dossiers les éléments suivants : 

  * Les scripts : Fichiers python qui seront exécutés   
Ces fichiers ne contiennent pas de détails d’implémentation mais uniquement des appels de fonctions/méthodes 
  * La configuration : yaml, json, ini, pydantic, hydra…   
Il existe une multitude de façon de gérer les configs, à vous de choisir celle qui vous convient 
  * Le code de save/load   
Ce sous-dossier contient tout le code qui permet à votre programme d’interagir avec le monde extérieur. Lecture écriture dans un fichier ou dans une base de données, appels API, etc 
  * Le « cœur » du code   
Ce sous-dossier contient les fonctionnalités principales de votre programme.   
Dans le monde de l’IA on trouvera typiquement les fonctionnalités de pre-processing, de Machine Learning et de post-processing 



Si vous ne connaissez aucun template, je vous recommande de jeter un œil à [ Kedro ](https://kedro.readthedocs.io/en/stable/) . Le tuto space flight vous accompagne pas-à-pas pour prendre en main le framework et comprendre son template de code. 

##  Étape 4 : Écrire des tests 

![](https://www.quantmetry.com/wp-content/uploads/2022/08/tests-300x200.jpg)

Dans l’approche Test Driven Design (TDD), les tests sont écrits en amont de l’implémentation des fonctionnalités. Cette approche permet, entre autres, de bien spécifier le besoin avant de coder et de s’assurer d’une couverture de test élevée.   
Le framework de test le plus utilisé en python est [ pytest ](https://docs.pytest.org/en/7.1.x/) . N’hésitez pas à prendre un peu de temps pour apprendre à l’utiliser. 

_Hint_ : Les tests vont évidemment FAIL tant que vous n’avez pas implémenté la solution 

##  Étape 5 : Coder 

Il est temps d’écrire votre code.   
L’objectif de ce guide n’est pas de développer la solution IA la plus performante possible, une solution minimale qui permet de faire des prédictions sera largement suffisante.   
Une fois les fonctionnalités implémentées, vérifiez que les tests passent 🙂 

##  Étape 6 : Documenter votre code 

Lorsque vous codez, vous devez toujours garder en tête que quelqu’un d’autre peut reprendre votre code et aura grandement besoin de documentation ! La documentation est également utile pour vous-même, combien de fois me suis-je demandé « à quoi sert cette fonction ? » alors que je l’ai moi-même écrite 6 mois plus tôt :S 

[ Sphinx ](https://www.sphinx-doc.org/en/master/) est un outil qui permet de générer une documentation au format HTML qui s’appuie directement sur les docstrings des différentes fonctions, méthodes et classes dans votre code. 

##  Étape 7 : Simuler un mode « train » et un mode « prod » 

Lors de la phase d’entraînement d’un modèle d’IA, vous allez généralement travailler sur des datasets d’entraînement avec de gros volumes de données. Ces datasets pourront par exemple être lus depuis des fichiers CSV. 

Une fois en production, la façon de charger les données peut être très différente. Vous pourriez par exemple recevoir des données au fil de l’eau via des requêtes API (format JSON). 

Essayez d’implémenter des scripts séparés pour le train et l’inférence en vous assurant que la qualité des prédictions n’est pas impactée par le mode d’ingestion de la donnée d’entrée. 

##  Étape 8 : Intégrer mlflow 

La gestion des modèles de Machine Learning est un élément fondamental du métier de MLE. Il est notamment souhaitable de tracer comment un modèle a été entraîné, quels sont ses performances, quelle version est déployée en production, etc… 

[ mlflow ](https://mlflow.org/) est un package open-source qui propose trois fonctionnalités principales : 

  * Experiment tracking : loggez tous vos entraînements de modèles (paramètres, metrics et artefacts) 
  * Model repository : stockez et versionnez les modèles entrainés 
  * Model serving : appelez votre modèle comme un micro-service découplé du code python 



Entrainez-vous à utiliser mlflow pour suivre l’historique de vos entrainements de modèles de ML et à utiliser le mlflow Model Repository pour définir une version “Production” du modèle et une version “Staging” (candidat pour une prochaine mise en production). 

##  Étape 9 : DataBase time 

  * Je cherche les données d’entrainement du modèle de NLP 
  * Je crois qu’elles sont dans le dossier /home/jean_claude/projet_loutre/2021/data.csv 
  * Non j’ai modifié des données d’entrainement, il faut utiliser le fichier data_V2.csv 
  * On a un souci, avec la migration tous les dossiers de /home ont été vidées ! 



Une base de données permet de stocker des grosses quantités de données de façon fiable et durable. A l’inverse, travailler avec des fichiers CSV peut conduire à de nombreuses erreurs. 

Je vous suggère donc de remplacer vos fichiers CSV par une base de données.   
Vous pouvez créer une base de données SQLite et interagir avec celle-ci en utilisant le package [ SQLModel ](https://sqlmodel.tiangolo.com/) . Tout est dans la merveilleuse documentation du package SQLModel ! 

_Hint_ : Si vous avez bien respecté le template de code décrit en étape 3, ces modifications ne devrait affecter que la couche de save/load et le reste du code devrait rester inchangé 

##  Étape 10 : APIser votre code 

Pour être utilisé, votre code doit être exposé. Une API fournit une interface pour qu’un utilisateur puisse faire appel à votre solution sans avoir accès au code source. 

La doc de [ FastAPI ](https://fastapi.tiangolo.com/) est le meilleur cours sur les APIs que je connaisse, je vous laisse donc suivre les tutos. Le package FastAPI est développé par le même auteur que SQLModel, chapeau @Sebastian Ramirez Montanõ ! 

##  Étape 11 : Dockeriser votre code 

![](https://www.quantmetry.com/wp-content/uploads/2022/08/docker-300x188.jpg)

Docker est un standard pour containériser son code. Docker permet de le déployer sur différents environnements (local, cloud, on-premise, etc…) et de le scaler facilement afin d’absorber les pics de charge. 

Un tutoriel est disponible sur le site de Docker.   
La doc FastAPI contient une section sur le [ déploiement d’une API via Docker ](https://fastapi.tiangolo.com/deployment/docker/) et peut donc (encore) vous faciliter la vie ! 

##  Étape 12 : Refactorer votre code 

Différentes raisons peuvent vous pousser à faire évoluer votre solution à la suite d’une mise en production. On peut par exemple imaginer un nouveau besoin, une demande de nouvelle fonctionnalité, une baisse des performances liée à une dérive des données, etc… 

Si la conception de votre code est bonne, les évolutions seront faciles et demanderont peu de modifications. Si votre solution est mal pensée, le chantier sera nettement plus conséquent.   
Je vous recommande fortement la chaîne YouTube [ ArjanCodes ](https://www.youtube.com/c/ArjanCodes) qui est géniale pour apprendre à bien concevoir son code python. 

Un exemple d’évolution pourrait être (dans un contexte NLP) le passage d’une approche embeddings + Random Forest à une approche transformers. 

Une fois le code refactoré, assurez-vous que les tests passent toujours 😉 

##  Étape 13 : Mettre en place une intégration continue 

Lorsque vous travaillez dans une équipe de développeurs, il est crucial que le code sur les branches principales (master, develop) ne contienne pas de bug !   
Pour cela, il est souhaitable de s’assurer que les tests passent avant de merger son code, c’est le but de l’intégration continue. 

Jusqu’à maintenant les tests étaient lancés manuellement avec la commande pytest. Suivez dès maintenant le guide pour apprendre à utiliser les [ github actions ](https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-python) et automatiser le lancement des tests à chaque fois que vous poussez du code sur votre repo git. 

#  Mot de la fin 

Le guide ci-dessus est très complet. Si vous suivez chacune de ces étapes assidument, vous en aurez pour quelques semaines ou mois de travail (si vous faites le test, n’hésitez pas à me faire un retour sur LinkedIn). Si vous en venez à bout, vous disposerez d’une expérience de MLOps solide. Pour tout vous dire, je connais peu de développeurs en poste aujourd’hui qui maitrisent toutes ces étapes ! 

#  Articles Connexes 

  * [ 10+ tips to deliver machine learning in production ](https://www.quantmetry.com/blog/10-rules-machine-learning-stack-production/)
  * [ Évaluer votre maturité MLOps ](https://www.quantmetry.com/blog/maturite-mlops/)
  * [ Trois questions pour identifier son cycle de vie des modèles ](https://www.quantmetry.com/blog/identifier-cycle-vie-modeles/)



_Abonnez vous à notre page Linkedin[ Quantmetry ](https://www.linkedin.com/company/quantmetry/) pour ne rien manquer de notre actualité ! _

![](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-nlp.svg)

Les membres de l’ [ expertise NLP ](https://www.quantmetry.com/experts/#nlp) exploitent le potentiel des données textuelles à l’aide de solutions d’IA à forte valeur ajoutée grâce à la maîtrise des technologies à l’état de l’art (modèles de deep-learning « pré-entrainés » BERT, ELMo, GPT-2 ou FlauBERT). 

####  ![](https://www.quantmetry.com/wp-content/uploads/2022/06/separation-1024x5.png)

![](https://www.quantmetry.com/wp-content/uploads/2022/08/hugorond-297x300.png)

**[ Hugo Perrier ](https://www.linkedin.com/in/hugoperrier/) , ** Machine Learning Engineer chez Quantmetry 

Après un parcours académique dans la physique, l’ingénierie nucléaire et la mécanique des fluides, je travaille comme consultant MLE chez Quantmetry depuis 4 ans. 
