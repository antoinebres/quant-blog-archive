---
layout: post
title: maturite-mlops
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129165640/https://www.quantmetry.com/blog/maturite-mlops/
---
Data Gouvernance 

09/04/2021 

#  Évaluer sa maturité MLOps 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmaturite-mlops%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=%C3%89valuer%20sa%20maturit%C3%A9%20MLOps&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmaturite-mlops%2F "Twitter")

* * *

Auteur : [ Valentin Richer ](https://www.linkedin.com/in/valentin-richer/)

Temps de lecture : 12 minutes 

![Quantmetry.com : Évaluer sa maturité MLOps](https://quantmetry.b-cdn.net/wp-content/uploads/2021/04/article-vri.png)

####  Introduction 

La mise en production d’un modèle de Machine Learning est devenu un enjeu important pour les organisations qui ont investi dans l’intelligence artificielle. En effet beaucoup ont lancé des PoCs (Proof of Concepts) sans jamais réussir à mettre en production leurs modèles de Machine Learning ou Deep Learning pour diverses raisons : manque d’expertises, ou d’expériences, frilosité des cadres dirigeants devant une technologie inconnue, absence de processus adaptés ou encore réticence des métiers devant la perte de maîtrise ou de compréhension des décisions prises par le modèle. 

Évaluer sa maturité dans la démarche MLOps, i.e. la démarche de mise en production des modèles façon DevOps, est une des premières étapes pour identifier les pistes d’amélioration. C’est pourquoi cet article propose de reprendre chacune des étapes du MLOps et de les qualifier en 3 niveaux de maturité suivant 3 axes : Personnes, Outils, Processus. 

> _ “DevOps is the union of people, process, and products to enable continuous delivery of value to our end users.”  _ [ _ Donovan B  _ _ r  _ _ own  _ ](https://www.donovanbrown.com)

Les différentes étapes du MLOps sont : 

  1. Définition du besoin 
  2. Préparation de la donnée 
  3. Expérimentations 
  4. Validation 
  5. Déploiement 
  6. Monitoring 
  7. Réentraînement 



####  Évaluer sa maturité à chacun des étapes du MLOps 

#####  1- Définition du besoin 

La définition du besoin est la genèse de tout projet de Machine Learning. Il est important dès cette étape de définir les objectifs du projet, les critères de succès et les acteurs qui seront nécessaires à sa réalisation. Un tel projet implique souvent les métiers, les data scientists, les data engineers, les machine learning engineers, ainsi que les cadres dirigeants qui apporteront du poids au projet de part leur parrainage. 

**Définition du besoin** |  Personnes  |  Outils  |  Processus   
---|---|---|---  
Maturité faible  | 

  * Métiers 

| 

  * Ateliers d’acculturation à l’IA 

| 

  * À ce niveau de maturité, l’IA ne fait pas partie de l’organisation et les métiers peuvent avoir une certaine méfiance vis-à-vis de cette technologie méconnue. 
  * Parfois les métiers voient l’IA comme une potentielle menace plus qu’une aide, ou au contraire la voit comme un outil magique capable de résoudre tous les problèmes. 

  
Maturité intermédiaire  | 

  * Métiers 
  * Data scientists 

| 

  * Ateliers d’idéations et cas d’usage 

| 

  * Un processus d’acculturation à l’IA est en cours mais l’IA n’est pas encore perçue comme un vecteur de changement systématique. 

  
Maturité forte  | 

  * Métiers 
  * Data scientists 
  * Cadres dirigeants 

| 

  * Ateliers de cadrage réunissant tous les acteurs clés du projet 

| 

  * L’IA est au cœur de la stratégie de l’entreprise et est utilisée de manière systématique lors de nouveaux projets. 
  * Les cadres dirigeants ont confiance dans ce domaine et investissent dans tous les secteurs de l’entreprise. 
  * Le projet possède un sponsor haut placé qui va financer et porter le projet. 

  
  
#####  2- Préparation de la donnée 

Cette étape est un prérequis essentiel aux opérations de machine learning à proprement parler. Une donnée fiable et accessible est une des clés de la réussite de la création d’un modèle performant. La préparation de la donnée contient elle-même de nombreuses étapes comme la collecte, le nettoyage, le formatage, la labellisation, le stockage. 

**Préparation de la donnée** |  Personnes  |  Outils  |  Processus   
---|---|---|---  
Maturité faible  | 

  * Chaque métier est propriétaire d’une donnée fragmentée 
  * Data scientists 

| 

  * Fichiers éparses aux formats très différents (textes, tableurs, etc.) 

| 

  * La donnée est éparpillée au travers des différents processus métier sous des formats hétérogènes. 
  * Les data scientists récupèrent par eux-mêmes les données et assurent le traitement de celles-ci. 
  * Il assurent le stockage des données dans un nouveau format de façon temporaire ce qui ne favorise pas le versioning ou encore le réentraînement des modèles. 

  
Maturité intermédiaire  | 

  * Administrateurs de bases de données 
  * IT 

| 

  * Data lake 

| 

  * Les data engineers centralisent les données au sein d’un data lake. 
  * Les données sont versionnées. 

  
Maturité forte  | 

  * Administrateurs de bases de données 
  * IT 
  * Data Architect 
  * Chief Data Officer 

| 

  * Data lake / Data mesh 
  * Feature store 

| 

  * Les données sont orientées en service data mesh. 
  * La donnée est facilement accessible aux data scientists notamment grâce à un catalogue de la donnée. 
  * Tous les types de données sont gérés quel que soit leur format, leur production (stream ou batch). 
  * En plus de ces services, un feature store permet la réutilisation des features développées par les data scientists. 

  
  
#####  3- Expérimentations 

La phase d’expérimentation est la première phase du cycle de MLOps. Lors de cette phase les data scientists vont tester différents modèles, différents hyperparamètres, différentes features. Lors de cette phase l’organisation et les outils utilisés sont cruciaux car le risque est de réitérer plusieurs fois les mêmes expériences, perdre les résultats ou encore ne pas pouvoir reproduire des résultats. 

**Expérimentations** |  Personnes  |  Outils  |  Processus   
---|---|---|---  
Maturité faible  | 

  * Data scientists fraîchement diplômés 

| 

  * Les data scientists codent principalement sur Jupyter Notebooks ou aidés par des outils tels que Dataiku, Azure AutoML etc. 
  * Infrastructure  **:** Ordinateurs en local ou sur quelques GPUs présents sur des serveurs on-premises. 

| 

  * Les environnements mis à disposition sont chaotiques et difficiles à configurer. 
  * Peu de traces des expérimentations ou stockage des expérimentations dans des fichiers textes ou tableurs. 
  * Difficultés à reproduire les résultats. 

  
Maturité intermédiaire  | 

  * Data scientists fraîchement diplômés 
  * Data scientists confirmés 

| 

  * Versioning du code 
  * Tests unitaires 
  * Scripts python 
  * Environnements virtuels / Docker etc. 
  * Logs des résultats 
  * Infrastructure : Mix entre GPUs sur serveur en propre et cloud 

| 

  * Les expérimentations sont reproductibles grâce à l’utilisation d’environnements définis. 
  * Les résultats sont stockés dans une base de données mais pas toujours de façon centralisée et standardisée ce qui rend la capitalisation difficile. 

  
Maturité forte  | 

  * Data scientists fraîchement diplômés 


  * Data scientists confirmés 
  * Data scientists seniors 
  * Experts dans leur domaine 

| 

  * Versioning du code 
  * Tests unitaires 
  * Scripts python organisés grâce à template de code utilisé de manière systématique 
  * Environnements virtuels / Docker etc. 
  * Fichiers de configuration 
  * Logs des résultats de manière standard et centralisé 
  * Registre des modèles 
  * Infrastructure : Utilisation de GPUs à la volée sur le cloud. Les droits de création et d’utilisation d’environnements sont gérés grâce à un outil dédié. 

| 

  * Les data scientists possèdent des environnements qui s’adaptent à leur besoin à la volée et sur des infrastructures adaptées. 
  * Les lead data scientists et managers accordent les droits et permissions de créer et utiliser les environnements demandés. 
  * Les résultats sont systématiquement logués et centralisés de manière à favoriser des itérations rapides et collaboratives. 
  * Les modèles sont versionnés. 

  
  
#####  4- Validation du modèle 

La validation du modèle assure qu’il n’y aura pas de surprises une fois le modèle passé en production. Cette validation comporte 3 volets qui reflètent le niveau de maturité des organisations : 

  * Les performances brutes du modèle (accuracy, precision, ROC etc.). 
  * Les performances méta du modèle (temps d’inférence, besoins en CPU, GPU et/ou RAM). 
  * Les considérations éthiques liées à l’intelligence artificielle. 



**Validation du modèle** |  Personnes  |  Outils  |  Processus   
---|---|---|---  
Maturité faible  | 

  * Data scientists 
  * Métiers 

| 

  * Seuls les performances pures du modèle, i.e. les métriques comme l’accuracy, la précision, le recall sont prises en compte dans la validation du modèle. 

| 

  * Les data scientists valident le modèle seuls ou avec les métiers. 
  * Il est souvent difficile de lier les métriques du modèle à des KPIs métiers. 

  
Maturité intermédiaire  | 

  * Data scientists 
  * Métiers 
  * ML engineer 
  * IT 

| 

  * 

