---
layout: post
title: decouverte-de-snowflake-comme-solution-de-data-mesh
date: 2022-10-01
url_wayback_machine: https://web.archive.org/web/20221001010338/https://www.quantmetry.com/blog/decouverte-de-snowflake-comme-solution-de-data-mesh/
---
Data Gouvernance 

10/12/2020 

#  Découverte de Snowflake comme solution de Data Mesh 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fdecouverte-de-snowflake-comme-solution-de-data-mesh%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=D%C3%A9couverte%20de%20Snowflake%20comme%20solution%20de%20Data%20Mesh&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fdecouverte-de-snowflake-comme-solution-de-data-mesh%2F "Twitter")

* * *

Auteur : [ Olivier Denti ](https://www.linkedin.com/in/olivierdenti/)

Temps de lecture : 12 minutes 

![Quantmetry.com : Découverte de Snowflake comme solution de Data Mesh](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/snowflake2.jpg)

Snowflake est ce que l’on appelle une « Cloud Data Warehouse » car elle combine 2 caractéristiques : celle d’être une base de données de type data warehouse et la seconde est de fonctionner uniquement en mode SaaS. 

La société Snowflake est récente puisqu’elle a été créée en 2012. Mais elle a connu une croissance fulgurante ces dernières années au point d’être valorisée plus de 70 milliards de dollars fin 2020. 

Dans cet article, je vais illustrer les points saillants de cette solution par rapport aux autres solutions « Cloud native » déjà présentes comme AWS Redshift, Azure Synapse Analytics ou GCP BigQuery. J’évoquerai également les points forts de la solution qui font que Snowflake permet de construire une solution de type data-mesh. 

##  Snowflake, une solution de type Datawarehouse 

Un Data Warehouse est utilisé pour collecter, transformer, historiser et préparer les données en vue, notamment, de les présenter au travers de dashboards de type Business Intelligence ou bien d’être exploitées en vue d’entraîner des modèles de Machine Learning.   
Les solutions de type Datawarehouse sont relativement anciennes (une trentaine d’années) et très présentes dans les entreprises pour le pilotage de leur activité.   
De nombreux acteurs sont présents comme Teradata, Oracle, IBM (Netezza, Db2 Warehouse), [ Microsoft (Azure Synapse Analytics, ex « Azure SQL Datawarehouse ») ](https://azure.microsoft.com/fr-fr/services/synapse-analytics/) , [ AWS (Redshift) ](https://aws.amazon.com/fr/redshift/) , [ Google (BigQuery) ](https://cloud.google.com/bigquery) , sans oublier la plateforme [ Cloudera / Hortonworks (Impala, Hive) ](https://fr.cloudera.com/products.html) . Chaque acteur a ses spécificités. Par exemple, ils peuvent être installés on-premise, en mode hybride (on-premise et dans le Cloud managé par l’éditeur) ou dans un Cloud public uniquement. De même, le modèle économique est différent (licence à la capacité de traitement offerte, licence au volume stocké, licence à l’utilisateur, paiement à l’usage, paiement au volume de donné brassé lors des requêtes etc.). 

La particularité des Datawarehouse est de ne traiter que des données structurées (données tabulaires par exemple) ou des données semi-structurées (JSON, XML…) pour certains moteurs. Les données de types vidéo, audio, images etc. sont hébergées dans un Datalake. 

##  Une solution en mode SaaS uniquement 

Snowflake a la particularité de n’être proposée qu’en mode SaaS depuis AWS, Azure et GCP. Il ne sera donc pas possible de l’installer « from scratch » sur son DataCenter privé. 

Pourquoi ce choix ? Snowflake tire parti au maximum des **avantages du Cloud** , comme :   
– L’élasticité de la solution (pouvoir adapter les ressources de calculs aux besoins des utilisateurs)   
– Une installation standardisée (très peu d’options à sélectionner) et rapide (quelques minutes) depuis la Marketplace des Cloud Provider   
– Une haute disponibilité assurée, les données étant répliquées 3 fois sur la région choisie   
– Un coût de stockage réduit 

Snowflake ne pourra donc pas convenir à tous les usages (contraintes réglementaires notamment) du fait que les données sont hébergées en dehors de l’Entreprise. 

#  Ecosystème Snowflake 

L’écosystème autour de Snowflake est conséquent et adapté pour un usage de bout en bout, depuis les plateformes d’ETL (Talend, Trifacta, Pentaho..), de restitution (Tableau, Qlik, PowerBI…) ou d’analyses (SAS, Dataiku…). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/snowflake-ecosystem.png)

**Ecosystème** : source Snowflake 

#  En quoi Snowflake est-elle différente ? 

Outre le fait que la solution est « **Cloud Native** » et s’appuie sur les points forts des Cloud Provider, 3 caractéristiques principales font la différence : 

1.Le découplage entre le stockage des données et le « moteur » de base de données   
2.La facilité de partager des données avec des partenaires   
3.La possibilité de copier instantanément des données sans les dupliquer 

##  Snowflake : fonctionnement interne 

Les données dans Snwoflake sont stockées dans un espace de type « blob storage » comme AWS S3. 

Le requêtage des données se fait à l’aide de « serveurs », dont le nombre dépend du choix de l’utilisateur (1 à 128). 

Le nombre de serveurs s’adapte **automatiquement** (à la hausse comme à la baisse) aux sollicitations des charges de travail. Dans le cas où il n’y a aucune activité, aucun serveur n’est alloué ; quelques secondes sont nécessaires pour rendre actif un serveur. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/snowflake-internal.png)

**Architecture** : source Snowflake 

Le coût est déterminé selon la quantité de données stockées et du nombre de secondes où les serveurs ont été sollicités.   
Retrouvez plus de détails sur les coûts via cette URL [ https://docs.snowflake.com/en/user-guide/warehouses-overview.html ](https://docs.snowflake.com/en/user-guide/warehouses-overview.html)

##  Snowflake versus AWS Redshift 

Les données dans [ AWS Redshift ](https://aws.amazon.com/fr/redshift/) sont stockées au sein des nœuds de calcul Redshift. Au fur et à mesure que la volumétrie des données augmente, il est alors nécessaire d’ajouter des nœuds Redshift (et de re-équilibrer les données au sein du cluster, ce qui peut durer plusieurs jours). Il y a donc une **corrélation très forte entre volume de données et capacité de calculs.**   
Le modèle économique est au nombre de nœuds Redshift provisionnés : le coût est le même que le cluster ne traite aucune requête ou que le cluster soit très sollicité. 

##  Snowflake versus GCP BigQuery 

Tout comme Snowflake, le stockage des données et le « moteur » de [ GCP BigQuery ](https://cloud.google.com/bigquery) sont séparés, permettant d’évoluer indépendamment. La capacité de calcul du « moteur » s’adapte en fonction de la sollicitation afin de répondre aux requêtes le plus rapidement possible. 

Le modèle économique dépend de la quantité de données stockées (comme Snowflake) et du volume de données brassées lors de la requête. Il s’agit donc d’un **paiement à l’usage** mais, contrairement à Snowflake, non pas basé sur la capacité de calcul du « moteur », mais sur la quantité de données requêtées. 

##  Snowflake versus Azure Synapse Analytics 

[ Azure Synapse Analytics ](https://azure.microsoft.com/fr-fr/services/synapse-analytics/) est une solution complète de traitement de la donnée (de l’intégration, leur transformation, le Machine Learning, le DataLake, la Visualisation…). Elle intègre la brique « SQL Data Warehouse » qui s’apparente aux fonctionnalités de Snowflake. Cette brique SQL permet d’interroger les données stockées dans Azure Data Lake ou dans Azure Blob Storage, en utilisant des ressources provisionnées (comme Redshift) ou à la demande. 

##  Quelques spécificités de Snowflake versus autres compétiteurs 

|  **Snowflake** |  **Redshift** |  **Azure Synapse Analytics** **(ex Azure SQL DW)** |  **BigQuery**  
---|---|---|---|---  
**Elasticité** |  Automatique et limité au nombre de serveurs max allouables  |  Manuelle  |  Manuelle  |  Automatique et non limité   
**Gestion des index** |  Non  |  Limité (sort key)  |  Oui  |  Non   
**Distribution des données** |  Automatique  |  Hash, round-Robin, Replicate  |  Hash, round-Robin, Replicate  |  Automatique   
**ACID (*)** |  Oui  |  Eventuellement Cohérente  |  Oui  |  Oui   
**Clés Unique / Primaire / Etrangère (**)** |  Oui  |  Non  |  Primaire et Unique  |  Non   
  
(*) ACID : Atomicité, Cohérence, Isolation, Durabilité 

(**) : dans le cas de larges tables, positionner des clés est contre-productif du fait de la lenteur induite par les vérifications lors des modifications des données. Ces propriétés peuvent être toutefois intéressantes à mettre en œuvre dans le cas de tables de références à volumétrie faible (référentiel produits, base clients…) afin d’en garantir la qualité (cas des doublons notamment). 

#  L’architecture de Snowflake 

L’architecture Snowflake est composée de 3 couches. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/snowflake-archi.png)

**Architecture** : source Snowflake 

##  Cloud Services 

« Cloud Services » est un ensemble de services coordonnant les activités à travers Snowflake. Ces services relient tous les différents composants de Snowflake afin de traiter les demandes des utilisateurs, de la connexion à l’envoi des requêtes. 

##  Query Processing 

L’exécution de la requête est effectuée dans la couche de traitement. Snowflake traite les requêtes en utilisant des « entrepôts virtuels » (virtual warehouse). Chaque **entrepôt virtuel** est un cluster de calcul MPP composé de plusieurs nœuds de calcul alloués par Snowflake à partir d’un Cloud provider (AWS, Azure ou GCP). 

Chaque entrepôt virtuel est une grappe de calcul indépendante qui ne partage pas les ressources de calcul avec d’autres entrepôts virtuels. Par conséquent, chaque entrepôt virtuel n’a pas d’impact sur les performances des autres entrepôts virtuels. 

Il est donc possible d’avoir plusieurs « virtual warehouse » pour son projet, chacun pouvant être responsable d’une activité (chargement de données, requêtes pour le dashboarding, requêtes ad-hoc par des analystes…). Ainsi, on peut limiter les contentions : dans le cas où un chargement massif de données est réalisé, cela n’aura pas d’impact sur les requêtes provenant des utilisateurs, les capacités de calcul étant différentes. 

##  Database Storage 

Lorsque les données sont chargées dans Snowflake, Snowflake réorganise ces données dans leur format interne optimisé, compressé et en colonnes. Snowflake stocke ces données optimisées dans des « **blob storage** » (comme AWS S3, offrant un coût de stockage réduit et une durabilité de 99,999999999 %). 

Snowflake gère tous les aspects de la manière dont ces données sont stockées. L’organisation, la taille des fichiers, la structure, la compressio 
