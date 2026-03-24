---
layout: post
title: les-difficultes-et-cles-de-succes-du-role-de-product-owner-sur-un-produit-technique
date: 2025-07-09
url_wayback_machine: https://web.archive.org/web/20250709215007/https://www.quantmetry.com/blog/les-difficultes-et-cles-de-succes-du-role-de-product-owner-sur-un-produit-technique/
---
AI Product 

29/11/2023 

#  Les difficultés et clés de succès du rôle de Product Owner sur un produit technique 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fles-difficultes-et-cles-de-succes-du-role-de-product-owner-sur-un-produit-technique%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Les%20difficult%C3%A9s%20et%20cl%C3%A9s%20de%20succ%C3%A8s%20du%20r%C3%B4le%20de%20Product%20Owner%20sur%20un%20produit%20technique&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fles-difficultes-et-cles-de-succes-du-role-de-product-owner-sur-un-produit-technique%2F "Twitter") [ ](https://www.quantmetry.com/blog/les-difficultes-et-cles-de-succes-du-role-de-product-owner-sur-un-produit-technique/ "Email") [ ](https://www.quantmetry.com/blog/les-difficultes-et-cles-de-succes-du-role-de-product-owner-sur-un-produit-technique/ "Copy Link")

* * *

Auteur : [ Camille Lam ](https://www.linkedin.com/in/camille-lam/)

Temps de lecture : 4 minutes 

![Quantmetry.com : Les difficultés et clés de succès du rôle de Product Owner sur un produit technique](https://www.quantmetry.com/wp-content/uploads/2023/11/lars-kienle-ilxx7xnbrf8-unsplash-scaled.jpg)

En tant que Product Owner, la gestion d’un produit technique peut être un défi complexe et passionnant. Aujourd’hui, je suis Product Owner sur une plateforme d’ingestion de données vers un datalake, produit dit “technique” de par ses fonctionnalités moins visibles directement par l’utilisateur qu’un produit “client-facing” (un produit avec des fonctionnalités directement visibles par l’utilisateur). Cette plateforme joue un rôle crucial dans l’entreprise pour laquelle je travaille, en ingérant des données à partir de diverses sources tout en assurant une gouvernance technique rigoureuse. Cet article met l’accent sur les défis auxquels j’ai été confronté et les facteurs clés qui me semble important pour la réussite d’un tel rôle. 

![Schéma descriptif d'un produit technique](https://www.quantmetry.com/wp-content/uploads/2023/11/sans-titre.png)

_Fig.1 Schéma descriptif du produit technique_

##  Les difficultés rencontrées 

En prenant les rênes d’une plateforme d’ingestion de données , j’ai dû relever le défi de m’approprier un produit complexe. Par exemple, une fonctionnalité consiste à copier une donnée de la source vers une première zone du datalake, appelée le Bronze. Derrière celle-ci, se cache tout un processus de copie de tous les petits fichiers mis à disposition vers une zone de cache pour les regrouper et ensuite les recopier d’un seul coup vers la zone Bronze. Toutes ces petites étapes ont été réfléchies pour optimiser les performances et les coûts. 

Un autre défi majeur auquel j’ai dû faire face est la multitude d’interlocuteurs impliqués dans le processus d’ingestion. Data stewards, data producers, data owners, data knowers, data consumers, etc. tous jouent un rôle dans le processus d’ingestion. Or, ce processus n’est pas toujours clair et compris par tous, ce qui peut rendre parfois les échanges avec les interlocuteurs difficiles, car chacun ne sait pas nécessairement quand intervenir. Par exemple, la question de la validation de l’arrivée d’une donnée dans le datalake et de la personne responsable de cette validation revient de manière récurrente lors des différents comités. 

Enfin, le succès de la plateforme d’ingestion de données dépend de la conduite du changement. Ici, nous parlons d’un changement d’outil : historiquement, les data producers devaient s’occuper de la mise à disposition de leur donnée dans le datalake avec leurs propres outils. Aujourd’hui, avec la plateforme que nous proposons, toute ingestion est centralisée avec un seul outil. Certaines parties sont donc sceptiques quant à la valeur ajoutée de la plateforme, d’autres le sont moins, mais ce produit modifie leurs habitudes de travail, ce qui peut susciter tout de même des résistances et des réticences. Avant l’arrivée de la plateforme d’ingestion, ces collaborateurs pouvaient ramener de la donnée dans l’ancien datalake de manière assez simple en termes de process (ils devaient en revanche prendre en charge le développement de la pipeline eux-mêmes). A la suite de la naissance de la plateforme d’ingestion, le process devient plus complexe – mais plus fiable et la donnée devient gouvernée – et demande plusieurs phases de validation et/ou de revue de la donnée avant de pouvoir la pousser via l’outil dans le datalake. 

##  **Les clés de succès**

Pour surmonter les difficultés rencontrées en tant que Product Owner, certaines clés de succès se sont avérées efficaces. Tout d’abord, il est primordial d’écouter attentivement les utilisateurs et de les rassurer, en mettant un accent particulier sur ceux qui expriment des réticences face au nouveau produit. En comprenant leurs griefs et en identifiant les « quick wins », j’ai pu apporter des changements significatifs qui améliorent rapidement la satisfaction globale des utilisateurs. 

Dû au fait que le produit était déjà en production, il a fallu sécuriser rapidement le volet support. Mettre en place un calendrier de support avec une personne dédiée à cette tâche s’est avéré utile. Ensuite, afin d’encourager l’adoption, il a fallu expliquer les avantages tangibles du produit, montrer comment il résout les problèmes existants et mettre en valeur ses fonctionnalités clés. Par exemple, la mise en place de nouveaux connecteurs d’ingestion, comme Kafka Connect, est intéressante pour les utilisateurs ayant déjà des topics Kafka existants, car elle ne nécessite aucun développement complexe de leur part. 

D’autre part, afin de renforcer la confiance dans la plateforme, il a fallu collaborer avec l’ensemble de l’équipe pour stabiliser l’existant avant d’ajouter de nouvelles fonctionnalités importantes. La fiabilité de la plateforme est un élément essentiel pour consolider son adoption et sa réputation auprès des utilisateurs et des parties prenantes. Concrètement, on a rencontré une période du projet où il a fallu dédier 60% de l’énergie de l’équipe à la stabilisation de la plateforme, 30% au support et 10% au développement de nouvelles fonctionnalités. 

Enfin la communication joue un rôle central dans le succès du Product Owner. En communiquant efficacement avec les sponsors et en collaborant étroitement avec les experts tels que les data architects, j’ai pu bénéficier de leurs conseils et des meilleures pratiques. Travailler main dans la main avec la cellule de data gouvernance s’est avéré très utile pour établir des processus, des normes et des bonnes pratiques qui garantiront le succès à long terme du produit. 

##  **Conclusion**

Être Product Owner d’une plateforme d’ingestion de données technique n’est pas une tâche aisée, mais c’est un rôle crucial pour l’entreprise. Les défis résident dans la compréhension du produit existant, la gestion de la gouvernance technique et l’adhésion des utilisateurs face aux changements. Cependant, en écoutant les utilisateurs, en consolidant l’existant, en fournissant les fonctionnalités attendues, en m’appuyant sur mon équipe technique compétente et en collaborant avec des experts, j’ai pu mener à bien ce projet complexe et transformer la plateforme en un atout majeur pour l’entreprise. L’alliance entre la compréhension des besoins des utilisateurs et la mise en place d’une gouvernance solide constitue les pierres angulaires du succès pour cette passionnante aventure de gestion de produit technique. Au sein de l’expertise [ AI Product ](https://www.quantmetry.com/experts/#aiproduct) de Quantmetry, nos Product Owners sont spécialisés dans la gestion des projets qui mêlent technicité et aspect communiquant. Nous avons une panoplie de retours d’expérience sur ce type de projet, n’hésitez pas à nous [ contacter ](mailto:kbienvenu@quantmetry.com) pour plus d’informations. 

[ ![Ai Product](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-AI-Product.svg) ](https://www.quantmetry.com/experts/#aiproduct)

Les membres de l’ [ expertise AI Product ](https://www.quantmetry.com/experts/#aiproduct) conçoivent, développent et industrialisent des produits IA de plus en plus complexes (Web et mobile apps, API, etc.) en s’appuyant sur une approche « ROIste ». 

* * *

![Camille Lam](https://www.quantmetry.com/wp-content/uploads/2023/11/microsoftteams-image-1.png)

[ Camille Lam  ](https://www.linkedin.com/in/camille-lam/)

Senior Data Consultante - Product Owner 

Senior Data Consultante/Product Owner dans l'expertise AI Product, je suis spécialisée dans le développement de produits et d'applications. J'ai dirigé des projets de grande envergure pour des clients variés, du secteur de la construction au luxe, en passant par l'industrie minière, l'énergie et le secteur de la vente au détail. Mon expertise s'étend de la gestion de projets à la supervision d'équipes. 
