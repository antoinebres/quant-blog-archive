---
layout: post
title: gouvernance-data-aventure-humaine
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129150730/https://www.quantmetry.com/blog/gouvernance-data-aventure-humaine/
---
Uncategorized 

11/04/2018 

#  La gouvernance de la data, cette aventure humaine 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fgouvernance-data-aventure-humaine%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=La%20gouvernance%20de%20la%20data%2C%20cette%20aventure%20humaine&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fgouvernance-data-aventure-humaine%2F "Twitter")

* * *

Auteur : [ Gill Morisse ](https://www.linkedin.com/in/gillmorisse/)

Temps de lecture : 13 minutes 

![Quantmetry.com : La gouvernance de la data, cette aventure humaine](https://quantmetry.b-cdn.net/wp-content/uploads/2018/04/guvernance.jpg)

_✍ Par[ Gill Morisse ](https://www.linkedin.com/in/gillmorisse/) [ ](https://www.linkedin.com/in/guillaume-hochard-phd-5580589/) _ _/ Temps de lecture : 7 minutes._

La gouvernance de la data n’est pas uniquement un défi technologique ! Gérer la donnée, c’est gérer un capital de connaissances et de savoir-faire qui émanent des activités humaines au sein des organisations. 

La data science prend enfin pied dans l’économie réelle et les cas d’usage se multiplient : maintenance prédictive des équipements, santé connectée, voiture connectée, digitalisation du quotidien de toutes les catégories d’employés. On parle de big data, d’intelligences artificielles, de machine learning, le monde devient data driven et tous les professionnels du secteur usent d’un jargon qui crée une illusion d’optique tenace : tout devient technologique, systèmes et réseaux d’information. 

Les acteurs technologiques se multiplient et promettent aux professionnels une totale maîtrise des flots de data au sein de l’entreprise. Les données vont se croiser à grande échelle pour générer une valeur qui bouleversera les équilibres concurrentiels. Les Data management systems permettront de tracer et de coordonner les flux de données et leurs traitements en conformité totale avec les nouveaux règlements européens (GDPR). 

Mais, vu des laboratoires de data science, la réalité est bien entendue différente. Une donnée, quelle qu’elle soit, n’a de valeur que si des femmes ou des hommes savent la remettre dans son contexte de production puis de traitement. Elle ne pourra être utilisée pour une application grande échelle que si d’autres personnes prennent la responsabilité d’en surveiller la qualité et de mettre en oeuvre des actions correctives bien au-delà des systèmes informatiques. Et surtout, la donnée repose sur un langage d’entreprise, des référentiels ontologiques qui nécessitent, pour être généralisés, une appropriation par toute l’entreprise d’une culture orientée data, c’est-à-dire affranchie des silos traditionnels (finance, marketing, production..). 

Loin d’être un simple fait technologique, la transformation par la data prolonge donc et accentue le rythme de transformation des organisations par le digital. Toutes les strates de la société, de l’ouvrière au top management vont désormais produire de la donnée et porter la responsabilité personnelle et collective de permettre à d’autres qu’eux d’utiliser facilement la donnée qu’ils produisent. Autant dire que les freins organisationnels sont nombreux et que l’outillage technologique est loin d’être la problématique principale. 

L’objectif de cet article sera donc double. Je rappellerai quel cadre méthodologique est en jeu pour la gouvernance de la donnée. Mais j’essaierai également de partager notre expérience et nos principales recommandations pour implémenter une gouvernance de manière pragmatique. 

####  ** LA GOUVERNANCE DE LA DATA, QU’EST-CE QUE C’EST ?  **

La gouvernance de la data est un chantier au coeur de la transformation digitale des entreprises. Après des années d’expérimentations qui ont démontré l’intérêt des intelligences artificielles, sa mise en oeuvre est une étape obligatoire vers l’industrialisation des solutions data et donc la conversion de promesses en gains. 

Pour simplifier, la gouvernance de la data poursuit trois objectifs majeurs : 

#####  Objectif #1 Favoriser l’accessibilité et le partage 

  * Favoriser l’utilisation de la donnée par des utilisateurs en garantissant la diffusion d’une connaissance et d’un savoir partagé (documentation, vision partagée…). 
  * Permettre le partage effectif de la donnée dans des conditions adaptées aux usages (access management, référentiels, interfaces, architecture…). 



![Représentation d'une voiture connectée](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/voiture.png)

_**L’exemple de la voiture connectée permet d’illustrer la complexité de ce partage :** _

_Le véhicule connecté, et bientôt autonome, est bardé de capteurs qui remontent des températures, des pressions, des images. Pour exploiter de façon pertinente une donnée de température, il faudra savoir où est situé le capteur (intérieur ou extérieur ? A l’avant ou à l’arrière ?), ce que signifie la valeur (Celsius ou Fahrenheit ? quelle est la valeur maximum ?), dans quelles conditions est-elle collectée (périodiquement ?, sur événement ?), comment interpréter une valeur aberrante (anomalie de conception ? réel défaut ?). Cette connaissance est aujourd’hui dispersée entre l’ingénierie, l’exploitation, l’IT. Comment mutualiser cette connaissance ?_

#####  Objectif #2 Gérer la qualité et l’intégrité 

  * Adopter une définition commune partagée par l’ensemble des services et des règles de gestion qui garantissent un niveau qualitatif suffisant pour l’usage attendu. Tout en sachant prévenir, détecter et corriger des erreurs. 
  * Maîtriser le cycle de vie de la donnée (data lineage) en identifiant la source, les transformations et l’utilisation. 



![Un coeur entre deux mains](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/mainmain.png)

**_Le cas d’une assurance et mutuelle illustre parfaitement cet objectif_ **

_La compréhension et la fiabilité des données sont des concepts essentiels qui garantissent une bonne utilisation et gestion. Est-ce la même notion pour tout le monde ? Est-elle accessible ? D’où vient-elle ? Comment est-elle transformée ? Quels sont les systèmes ou les processus qui l’utilisent ?_

_Dans cette compagnie d’assurance et mutuelle, plusieurs départements définissaient le chiffre d’affaires de manière différente. Une des approches proposées était de s’assurer que le chiffre d’affaires désignait la même notion et soit partagée par tous. Pour cela, Quantmetry a accompagné dans l’initialisation et la diffusion des outils organisationnels (règles de gestion, comité organisationnel…)_

#####  Objectif #3 Garantir la conformité réglementaire 

  * Renforcer et maintenir la conformité aux exigences règlementaires et notamment aux règlements européens (GDPR) : référentiel des traitements, durées de conservation, collecte du consentement, traçabilité.. 



#####  Objectif #4 Confidentialité et sécurité 

  * Renforcer la sécurité des données personnelles, sensibles ou confidentielles 
  * Clarifier et partager les process relatifs à la sécurité des données (access management…) 



L’atteinte de ces objectifs va s’appuyer sur un déploiement progressif d’un ensemble de ressources et de principes organisationnels. De manière synthétique, on peut distinguer quatre grands leviers qui soulèvent des questions clés : 

###  ![Quatre leviers pour la Data Gouvernance](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Capture-d’écran-2018-04-11-à-10.49.28.png)

#####  Levier #1 Rôles et organes de gouvernance : 

C’est certainement le levier clé. La data porte l’expertise des femmes et hommes qui la produisent. Sans un engagement clairement porté par une organisation, il ne sera pas possible d’atteindre les objectifs. 

  * Quels sont les rôles clés à mettre en œuvre au sein de l’organisation et des sociétés (Chief Data officer, Data owner, Data manager, Data Steward) et quelles sont leurs responsabilités opérationnelles ? 
  * Pour chaque périmètre de données, qui est responsable de quoi ; qui est le Data Owner ? 
  * Les comités de gouvernance à mettre en place pour définir et suivre la bonne marche de la gouvernance de la donnée : au niveau des sociétés, au niveau du groupe ? 



**_De nouveaux rôles et fonctions apparaissent ainsi et présentent la particularité de se répartir dans l’ensemble de l’organisation côté métiers et côté IT._ **

_**Le Chief Data Officer** : il s’assure de la bonne définition et mise en place du cadre de gouvernance data à l’échelle de l’entreprise. Il propose et pilote des projets stratégiques et/ou transverses en la matière, travaille avec les sponsors métiers et l’IT pour hiérarchiser et résoudre les problématiques rencontrées dans le cadre de la gouvernance data _

_**Le data manager** : Il est garant de la collecte des données d’un périmètre de données, en s’assurant de leur exploitabilité au service d’un ensemble d’usages identifiés. _   
_Il s’assure, sur ce périmètre, de la mise en œuvre des processus et politiques définis par la gouvernance de la donnée. Il contrôle l’application des contraintes réglementaires. Il anime la gouvernance opérationnelle relative à son périmètre de données_

_**Le data steward** : Il gère et administre opérationnellement tous les aspects d’un sous-ensemble de données. Il porte la responsabilité du contrôle technique des données : les aspects de sécurité, de qualité et d’accessibilité _

_**Le data owner** : Il est le référent métier au sein de l’entreprise sur un périmètre identifié de données. _   
_Il est garant des définitions métiers et des référentiels associés. Il porte la responsabilité de la qualité de la donnée. Il délivre les autorisations d’accès à la donnée, en lien avec des cas d’usage identifiés._

#####  Levier #2 Règles et normes : 

Les règles et normes structurent l’action de la gouvernance et doivent faire l’objet d’un partage et d’un consensus au sein de l’entreprise. 

  * Quel niveau de confidentialité et de sécurité faut-il mettre en place, par typologie de données ? 
  * Quel cadre de règles (qualité, cohérence, propriété, documentation…) à mettre en œuvre, préalable au chargement des données dans une plate-forme Big Data ? 
  * Quels KPI choisir pour évaluer le niveau attendu de qualité de la donnée ? 



######  Choisir des KPI de qualité 

Choisir des KPI pertinents qui peuvent faire l’objet d’un monitoring dans le temps est souvent un enjeu appréhendé d’un point de vue technique : complétude, doublons, erreurs. Loin d’être inutiles, ces KPI ne sont pourtant généralement pas suffisants pour porter l’évaluation de l’accessibilité aux données. Deux méthodologies majeures émergent pour définir des KPI adaptés au contexte : 

  * Choisir des KPI qui intègrent de manière très pragmatique la quantité de connaissances acquises et disponibles sur une data : documentation associée, ownership et intégration dans un plan de gouvernance. On peut alors distinguer plusieurs questionnements. La data est-elle :   
– définie ?   
– de qualité et monitorée par un responsable ?   
– accessible ?   
– collectée dans un datalake ou un entrepôt central ?   
– exploitable, c’est-à-dire dans un format qui permette son usage (papier, texte non structuré, fichier Excel) ? 



Ces KPI devront être mis en oeuvre par les data owners et stewards. 

![Exemple de matrice de monitoring de la qualité d’un jeu de donnée](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/matrice.png)

Exemple de matrice de monitoring de la qualité d’un jeu de donnée / Quantmetry 2018 – tous droits réservés – reproduction interdite 

  * Choisir des KPI déclaratifs qui émanent des utilisateurs de la donnée. Dans les entreprises les plus matures, ceci permet d’intégrer des feedbacks et des commentaires sur un modèle proche des E-commerçants. La palette de questions peut alors s’élargir : est-ce que la data a été utile et dans quel cas ? Quelle capacité de jointure avec les autres data du groupe ? 



#####  Levier #3 Les processus : 

Les processus permettent d’instancier les règles et normes de la gouvernance et d’identifier clairement les responsabilités des acteurs impliqués. 

  * Quels processus pour identifier et gérer la propriété (data ownership) et l’accès aux données ? 
  * Quels sont les processus pour définir, mettre en œuvre et contrôler le respect des règles et des normes (qualité, sécurité,…) ? Au chargement sur une plateforme big data, dans le cadre d’un projet consommant ou produisant de la data ? 
  * Quelles règles de gestion pour le maintien des référentiels clés ? 
  * Quels sont les processus d’audit à mettre en place pour se conformer aux réglementations internes, externes ? 



#####  Levier #4 Les systèmes d’information et les outils informatiques : 

  * Comment implémenter les standards de sécurité des données dans l’architecture IT ? (chiffrement, gestion des droits d’accès aux données,…) 
  * Quels standards d’architecture mettre en place pour la colle 


