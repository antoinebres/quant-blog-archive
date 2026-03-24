---
layout: post
title: bi-vs-big-data
date: 2023-06-06
url_wayback_machine: https://web.archive.org/web/20230606094308/https://www.quantmetry.com/blog/bi-vs-big-data/
---
Uncategorized 

23/01/2017 

#  BI vs Big Data 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fbi-vs-big-data%2F&title=BI%20vs%20Big%20Data "Linkedin") [ ](http://twitter.com/intent/tweet?text=BI%20vs%20Big%20Data&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fbi-vs-big-data%2F "Twitter") [ ](https://www.quantmetry.com/blog/bi-vs-big-data/ "Email") [ ](https://www.quantmetry.com/blog/bi-vs-big-data/ "Copy Link")

* * *

Temps de lecture : 5 minutes 

![Quantmetry.com : BI vs Big Data](https://quantmetry.b-cdn.net/wp-content/uploads/2017/01/screen-shot-12-30-18-at-01-55-pm.jpg)

Happy Birthday ! Depuis début janvier 2014, l’intérêt en France pour le Big Data a dépassé celui pour l’informatique décisionnelle (selon Google Trends). Tous les acteurs du marché de la BI sont en effervescence et cherchent depuis quelques années à se positionner vis à vis de ces nouvelles technologies. L’avènement du Big Data et de Hadoop sonne-t-il la fin de la BI traditionnelle ? Quels impacts pour les architectures et les applications BI actuelles? Quels apports pour les utilisateurs ? Quelques éléments de réponse. 

##  1\. Il était une fois la BI… 

La Business Intelligence (Informatique Décisionnelle) répond depuis de nombreuses années aux besoins de reporting et d’aide à la décision des entreprises en leur fournissant des outils de consolidation et de restitution des données. 

Initialement orientée à l’analyse des données des systèmes opérationnels de l’entreprise, la BI se distingue par la mise en place de modèles de données spécifiques (MDD décisionnels) répondant à une double problématique fonctionnelle et technique. Le modèle décisionnel doit en effet s’astreindre des modèles des applications sources pour fournir aux utilisateurs une vue fonctionnelle cohérente avec les objectifs d’analyse tout en optimisant les performances techniques d’interrogations par une structuration dédiée au requêtage. Les données y sont généralement catégorisées en faits (indicateurs, mesures) et en dimensions (axes d’analyses) et organisées selon un modèle multidimensionnel dénormalisé (modèle en étoile). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/1-1-2.jpg)

Figure 1 – Exemple de modèle de données en étoile 

Les fondements théoriques de l’architecture décisionnelle datent des années 1980 et ont ensuite été largement popularisées dans les années 90 notamment par Ralph Kimball dans « The Data Warehouse Toolkit » et Bill Ilmon avec « Building the Data Warehouse » 

Bien qu’il n’existe pas d’architecture de référence d’un système décisionnel, ce type d’application repose généralement sur une architecture en couche organisée autour de ses trois fonctions essentielles : 

– Des traitements d’intégration des données assurent la collecte sélective d’informations depuis les systèmes sources et opèrent une mise en conformité (formatage, datacleaning, transcodification, etc.) vers le modèle de stockage décisionnel. 

– Les informations sont stockées généralement dans un SGBD relationnel (prédominance SQL) qui héberge le DataWareHouse (DWH) divisé en couches logiques (ODS, Datamarts dédiés, Cubes OLAP …) dont la modélisation dépend des besoins et des contraintes de reporting. 

– Des outils de restitution accèdent aux données depuis le DWH par l’intermédiaire de rapports prédéfinis ou de requêtes ad-hoc possédant des fonctionnalités de présentation et de diffusion des données variées. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/45.jpg)

Figure 2 – Schéma simplifié d’une chaine décisionnelle 

L’évolution des SI et de leurs usages au cours des dernières années a amplifié la création et la consommation de données, poussant les architectures BI dans leurs limites à tous les niveaux. 

Au niveau de l’intégration, les données structurées qui étaient historiquement traitées par la BI ne sont plus la norme en termes d’information. Aujourd’hui, 80% des données sont semi ou non structurées et difficilement adressables avec les technologies classiques de l’informatique décisionnel. Les données ne sont plus émises vers les systèmes de reporting de façon quotidienne ou mensuelle mais doivent être consultables en temps réel. Les sources de données se sont multipliées et dépassent largement le cadre du SI de l’entreprise (Réseaux sociaux, Public Data etc.) 

Au niveau du stockage, les temps de traitements observés ne sont aujourd’hui plus toujours satisfaisant dès que la volumétrie de donnée manipulée explose… et les volumes de données devraient augmenter d’un facteur x30 d’ici 2020 ! En complément, l’ajout d’une nouvelle source de donnée demande généralement une évolution complète de la chaine décisionnelle entrainant des délais contre productifs. 

Au niveau de la restitution, la maintenance de datamarts et de couches sémantiques dédiées à un type d’analyse n’est aujourd’hui plus assez agile pour répondre aux évolutions permanentes du besoin de consommation de données des utilisateurs. La démocratisation des outils de reporting rend les utilisateurs demandeurs d’outils de type self-service (BI à la demande) leur permettant de produire de nouveaux rapports, de calculer de nouveaux indicateurs ou de requêter directement les données eux-mêmes mais restent souvent bridés pour des questions de performance. La restitution en tableaux de bord structurés ou au mieux en Dashboard interactif n’est plus au niveau comparée aux interfaces graphiques riches proposées sur le Web. 

##  2\. …Et le Big Data arriva 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/57.jpg)

Figure 3 – Google Trends: BI vs Big Data de 2004 à aujourd’hui en France 

Il est facile de lire entre les précédentes lignes que les limites de la BI actuelle trouvent certaines de leurs réponses dans la définition globalement partagée du Big Data qu’il soit à 3, 4 ou 5 V (Volume, Variété, Vélocité, …) pour autant les deux notions ne sont pas à mettre en concurrence. La BI doit être vue comme un type d’usage de la Data, là où le terme Big Data recouvre souvent les données, les usages et les outils associés. 

Les nouvelles technologies Big Data permettent d’envisager de nouvelles solutions pour les systèmes décisionnels existants. Dans cette logique, l’ensemble des éditeurs « traditionnels » de la BI (ETL et reporting notamment) proposent aujourd’hui un panel complet de connecteurs Hadoop et de fonctionnalités BigData. 

Le changement de paradigme actuel, d’une définition du modèle à l’écriture des données vers une définition à la lecture, ouvre de nouvelles possibilités prometteuses en termes d’architectures BI. 

  * L’intégration des données dans le Datalake n’est plus sélective limitant les cycles incrémentiels de récolte de nouveaux indicateurs. 

  * Les capacités temps-réel des plateformes Hadoop permettent de s’astreindre des batchs périodiques pour aller vers un vrai reporting temps-réel. 

  * Le calcul distribué (Spark par exemple) et les méthodes de stockage avancées permettent l’exécution de traitements analytiques avec un rapport cout/performances jusqu’ici inatteignable. 

  * … et encore beaucoup d’autres synergies à mettre en œuvre. 




Le Big Data et ses outils permettent donc de voir émerger de nouveaux cas d’usage et de nouvelles solutions techniques permettant d’y répondre grâce notamment à une capacité de traitement analytique améliorée. La BI peut (et doit) profiter de cette rupture technologique pour se réinventer et évoluer vers plus d’agilité, de performance et de convivialité pour l’utilisateur. L’enjeu à venir est donc moins de statuer sur la mort ou la survie de la BI que d’identifier et de mettre en œuvre les actions de transformation vers un système BI utilisant tout le potentiel du Big Data. 
