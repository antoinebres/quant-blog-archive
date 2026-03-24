# la-terminologie-data
Wayback Machine URL: https://web.archive.org/web/20230606105643/https://www.quantmetry.com/blog/la-terminologie-data/
Archive date: 2023-06-06

Uncategorized 

27/09/2017 

#  La terminologie Data 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fla-terminologie-data%2F&title=La%20terminologie%20Data "Linkedin") [ ](http://twitter.com/intent/tweet?text=La%20terminologie%20Data&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fla-terminologie-data%2F "Twitter") [ ](https://www.quantmetry.com/blog/la-terminologie-data/ "Email") [ ](https://www.quantmetry.com/blog/la-terminologie-data/ "Copy Link")

* * *

Temps de lecture : 4 minutes 

![Quantmetry.com : La terminologie Data](https://quantmetry.b-cdn.net/wp-content/uploads/2017/09/bigdata598.jpg)

Cet article fait partie d’une série d’articles co-rédigés par [ Emmanuel Manceau ](https://www.linkedin.com/in/emmanuelmanceau/) ( [ Quantmetry ](http://www.quantmetry.com/) ), [ Olivier Denti ](https://www.linkedin.com/in/olivierdenti/) ( [ Quantmetry ](http://www.quantmetry.com/) ) et [ Magali Barreau-Combeau ](https://www.linkedin.com/in/magalibc/) ( [ OVH ](https://www.ovh.com/fr/) ) sur le sujet « Architecture – De la BI au Big Data » 

##  Concepts pré-existants au Big-Data 

###  Base Relationnelles 

Une base de données relationnelle est une base de données organisée sous forme de tables et de relations. 

###  Progiciel 

D’après Wikipedia, un progiciel « Un progiciel ( [ mot-valise ](https://fr.wikipedia.org/wiki/Mot-valise) , contraction de produit et logiciel) est un [ logiciel applicatif ](https://fr.wikipedia.org/wiki/Logiciel_applicatif) généraliste aux multiples fonctions, composé d’un ensemble de programmes paramétrables et destiné à être utilisé simultanément par plusieurs personnes ». Ce sont des applications dédiées à un sujet donné et qui ont la particularité d’être paramétrables : ajout de données dans un écran, création d’écrans nouveaux…Les projets [ CRM ](https://fr.wikipedia.org/wiki/Gestion_de_la_relation_client) (Customer Relationship Management) et [ ERP ](https://fr.wikipedia.org/wiki/Progiciel_de_gestion_int%C3%A9gr%C3%A9) (Enterprise Ressource Planning) sont principalement basés sur des progiciels. 

###  Donnée brute 

Il s’agit du plus bas niveau d’information. Elle contient une très petite quantité d’information sur les objets et les processus de l’entreprise. 

###  Donnée signifiante 

Une donnée signifiante est une donnée qui permet à un utilisateur de prendre une décision éclairée dans un contexte particulier. Elle correspond donc à une vue de la donnée. 

###  Objet métier 

Un objet métier correspond à un concept métier essentiel et stable dans le temps. Emprunté à l’architecture d’entreprise, le terme d’objet métier est de haut niveau (ex : Client, Véhicule, Facture, Commande etc.) et interagit avec les processus métiers. En pratique, un objet métier est dispersé et éclaté dans un grand nombre de systèmes et doit être reconstruit dans les référentiels pour disposer d’une vision d’ensemble. 

##  Terminologie Business intelligence 

###  ODS – Operational data store 

Popularisé par le chercheur américain Bill Inmon, l’ODS ou Operational Data Store consiste à rassembler les données de l’entreprise en une base unique. L’ODS a vocation à réaliser les traitements de qualité des données. Il stocke le niveau le plus bas de l’information uniquement. Pour des données de facturation, il stockera donc chaque facture mais pas les agrégats hebdomadaires, mensuels ou autre (c’est à dire les regroupements de données). Il n’est pas optimisé pour des requêtes de sélections massives. 

Bill Inmon le proposait comme une étape intermédiaire a la création de base analytique (ou Datamart). L’ODS ne sert pas à historiser les données, mais seulement à fournir une vision en temps réel des données actuelles 

A contrario, Ralph Kimball, l’autre grand chercheur américain du décisionnel, recommandait la création d’un Datawarhouse unique, sans passer par la création d’ODS. 

###  Data warehouse 

C’est une base de données destinée à être utilisée par des outils décisionnels ou des analystes données (data analyst). Il est optimisé pour des requêtes de sélection massive. 

C’est traditionnellement une base en lecture seule, n’alimentant pas les applications opérationnelles qui lui fournissent les données. 

Le datawarehouse contient en général les données au niveau le plus fin, ainsi que des agrégats. En cas de présence d’un ODS en amont, il peut parfois se contenter de stocker les agrégats. 

Il peut être stocké sur une base relationnelle (Oracle, DB2, Sql Server), ou une base « massivement parallèle » (Teradata, Netezza) 

###  Datamart 

Un datamart est une base de données construite pour répondre à un besoin d’analyse décisionnelle d’un métier donné. Il est optimisé pour des requêtes de sélections massives. 

Un datamart peut être isolé ou construit au sein d’un datawarehouse. Il partage parfois une ou plusieurs tables avec d’autres datamarts, ce qui permet de faire des analyses croisées. 

Un datamart peut être stocké sous forme de cube (il nécessite alors l’utilisation d’une base de données multi-dimensionnelle) ou de modèle en étoile (il peut alors être stocké dans une base relationnelle.) 

##  Terminologie Big Data 

###  Données Structurées 

Les données Structurées sont des données qui peuvent être représentées dans un format prédéfini, généralement sous la forme classique table / colonne. Dans cette catégorie, on retrouve les données en provenance de bases de données, ou bien les fichiers textes délimités, les fichiers plats, etc. 

###  Données Non Structurées 

Les données non structurées sont des données qui ne peuvent pas être représentées sous un format « classique » de base de données. Il s’agit : 

  * Des texte écrits (fichiers pdf, livres) 

  * Des fichiers audios 

  * Des fichiers video 

  * Des images… 




###  Datalake 

Le datalake est un lieu de stockage, destiné à réceptionner l’intégralité des données de l’entreprise, que ce soient des données structurées ou non structurées. Le datalake est organisé en « couche » (voir ci-dessous). 

##  Nouveaux concepts 

###  Datashore ou Enterprise Data Store 

Le Datashore expose toutes les données signifiantes de l’entreprises sous un format normalisé, que ce soit au niveau du contenu que du contenant. Il est structuré en objets métiers définis en fonction de l’organisation et des objectifs de l’entreprise. 

Ces données représentent la réalité de l’entreprise et doivent pouvoir être comprises sans connaissance des modèles techniques dont elles sont issues. 

###  Couche 

Une couche correspond à un étage dans la cheminée d’agrégation et de consolidation de l’information depuis l’information « brute » du datalake jusqu’à la donnée synthétique présentée aux utilisateurs ou en entrée d’un modèle de datascience. 

La structuration de l’information dans le datalake est organisée par couches successives, depuis le niveau brut jusqu’à l’objet métier. Certaines couches sont pérennes et stockées de façon permanente : elles peuvent servir de base à d’autres calculs, ce pour quoi elles ont été prévues initialement. D’autres couches sont purement temporaires ou destinées à un flux unique de calcul. 

###  Vue 

Une vue est une mise en forme des données agrégées ou détaillée, qui correspond à un usage particulier. Il peut y avoir plusieurs vues d’une même donnée. 

Dans les articles suivants de cette série, nous préciserons la méthodologie de définition de cette couche de présentation des données du datalake. 

————- 

Article [ datamaniac.fr ](http://www.data-maniac.fr/language/fr/2017/09/27/terminologie-data/)

[ Version EN ](http://www.data-maniac.fr/language/en/2017/09/27/big-data-architecture-data-terminology/)
