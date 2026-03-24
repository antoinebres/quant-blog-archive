# data-mesh-deployer-des-data-domains-jouons-au-jeu-des-7-erreurs
Wayback Machine URL: https://web.archive.org/web/20250709213203/https://www.quantmetry.com/blog/data-mesh-deployer-des-data-domains-jouons-au-jeu-des-7-erreurs/
Archive date: 2025-07-09

Data Gouvernance, Data Strategy 

25/10/2023 

#  Déployer des Data Domains : jouons au jeu des 7 erreurs ! 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fdata-mesh-deployer-des-data-domains-jouons-au-jeu-des-7-erreurs%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=D%C3%A9ployer%20des%20Data%20Domains%20%3A%20jouons%20au%20jeu%20des%207%20erreurs%20%21&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fdata-mesh-deployer-des-data-domains-jouons-au-jeu-des-7-erreurs%2F "Twitter") [ ](https://www.quantmetry.com/blog/data-mesh-deployer-des-data-domains-jouons-au-jeu-des-7-erreurs/ "Email") [ ](https://www.quantmetry.com/blog/data-mesh-deployer-des-data-domains-jouons-au-jeu-des-7-erreurs/ "Copy Link")

* * *

Auteurs : [ Vlad Flamind ](https://www.linkedin.com/in/vflamind/) , [ Théo Vialard ](https://www.linkedin.com/in/th%C3%A9o-vialard-093708ab/)

Temps de lecture : 83 minutes 

![Quantmetry.com : Déployer des Data Domains : jouons au jeu des 7 erreurs !](https://www.quantmetry.com/wp-content/uploads/2023/10/pietro-jeng-n6b49ltx7nm-unsplash-scaled.jpg)

La notion de data domains est centrale, pilier à part entière du Data Mesh. Dans cet article, nous vous partagerons 7 convictions pour réussir votre transformation autour des domaines. 

#  Pourquoi constituer des Data Domains : La formule magique de Broda 

Pour ceux qui ne le connaissent pas encore, je vous invite à lire les publications d’Eric Broda, expliquant plusieurs concepts clés du Data Mesh. 

Dans son papier, il explique que deux facteurs participent largement au succès de la mise en place de produits Data : 

  1. L’approche « Product-thinking » appliquée à la donnée assure la réponse systématique d’un produit à un besoin client majeur, quelles que soit son évolution dans le temps 
  2. Les « Data Domains » : le maillon essentiel pour déployer et faire évoluer les produits, parce qu’ils sont (a) responsables de la santé de la donnée sur leur périmètre (b) composés de profils pluridisciplinaires capables de tenir cette responsabilité 



[ ![The anatomy of a data product](https://www.quantmetry.com/wp-content/uploads/2023/10/data-products-eric-broda.png) ](https://towardsdatascience.com/the-anatomy-of-a-data-product-d3140f068311)

_Source : The anatomy of a data product, Eric Broda, Towards Data Science, Aug 19 2022_

Le succès de la mise en place de data products repose sur la responsabilité de data domains envers un périmètre de données clair. Dans cet article nous partagerons notre retour d’expérience sur l’approche de découpage des data domaines et sur les erreurs à éviter lors de leur déploiement. 

#  Les 7 erreurs communes lors du découpage et du déploiement des Data Domains 

__

##  **Démarrer le jeu sans fixer les règles**

Avant toute étape de découpage des données par domaines, la phase préliminaire consiste à accorder toutes les parties prenantes de la donnée sur des besoins clairs et des principes de découpages associés qui serviront lors des étapes suivantes. A titre d’exemple, pour favoriser la fluidité des échanges, l’utilisateur de la donnée devra facilement trouver le responsable de cette dernière en ayant un point de contact unique. Pour ce faire, le principe à définir pourrait être que chaque métier ait un nombre limité de domaines associés (par exemple, la Direction Marketing utilise des données dont seulement 2 data domaines seront responsables). 

_Exemples de principes de découpage adoptés chez nos clients_

**Besoin** |  **Principe adopté**  
---|---  
**Garantir** le bon niveau de **sponsorship / leadership** |  Un nombre limité de data domains, chacun contenant le maximum d’objets data   
**Eviter** tout **chevauchement de périmètre** entre data domains  |  Chaque objet métier inclus dans un seul et unique data domain dans la mesure du possible   
**Garantir** un **point de contact unique** pour la communauté  |  Pour chaque métier, un nombre limité de data domains associés   
**Rendre** **opérant** la **maitrise du cycle de vie** de la donnée  |  Un data domain doit être le reflet de quartiers fonctionnels   
  
Dans cette première étape, fixer des principes de sélection propres à la fois aux domains consommateurs et producteurs permet de s’assurer que les priorités sont définies de manière pertinente et pragmatique. 

_Exemples de principes de sélection des data domains consommateurs et producteurs définis chez l’un de nos clients_

**Critères de priorisation des data domains Consommateurs** |  **Critères de priorisation des data domains Producteurs**  
---|---  
1\. Le data domain consomme des **données à fort enjeux** économiques / règlementaires pour l’activité de l’entreprise  |  1\. Un **programme majeur** existe autour du data domain   
2\. Un ou plusieurs métier(s) couvert(s) par le data domain sont déjà **membres du comité de direction data** |  2\. Les données alimentent des **processus règlementaires**  
3\. Un **data domain officer** a été pré-identifié  |  3\. Les données sont parmi **les plus consommées** par les autres data domains, notamment par les consommateurs priorisés   
4\. Les données alimentent des **KPI clés**  
5\. Les données alimentent des **cas d’usages soutenant la stratégie d’entreprise**  
  
__

##  **Partir à l’aventure sans avoir pensé la stratégie : approche top-down et bottom-up**

Chez Quantmetry, nous privilégions généralement un mix des deux approches, afin de bénéficier d’une information la plus exhaustive et fiable possible. 

Thématiques  |  **Approche TOP DOWN** |  **Approche BOTTOM UP**  
---|---|---  
Principes  |  Déterminer les objets métiers à partir des documents métiers et/ou organisationnels puis les data domains  |  Déterminer les objets métiers à partir des documents informatiques (découpage des applicatifs…) puis les data domains   
Démarche  |  Découper l’entreprise à partir de documents métiers (processus, organisation…)  Identifier les objets métiers associés à ce découpage avec les métiers (par exemple en partant des processus)  Associer les objets métiers à des data domains  |  Recenser les objets métiers à l’aide d’un découpage informatique (par exemple au sein de chaque applicatif)   
Avantages  |  Lien fort avec le fonctionnement de l’entreprise  Identification du cycle de vie des objets métiers  |  Exhaustivité des objets métiers collectés   
Inconvénients  |  Obtention souvent compliquée d’un document permettant un découpage exhaustif et pertinent de l’entreprise  Décorrelé de l’existant SI  |  Découpage par l’IT décorrelé des métiers  Présence de concepts informatiques non souhaités   
Quand s’en servir  |  Dès que possible s’il y a des éléments existants sur lesquels s’appuyer  |  Si l’approche TOP DOWN n’est pas possible ou en complément de l’approche TOP DOWN   
  
__

##  **Penser que le découpage des Data Domains n’est qu’une affaire de data**

Les documents usuels permettant de décrire les données ne permettent pas d’expliquer réellement le sens métier. Ils ont davantage vocation à décrire techniquement la donnée pour favoriser sa gestion. 

Pour comprendre davantage la raison ou l’activité nécessitant l’utilisation d’une donnée, il est nécessaire de recenser les objets métiers, c’est-à-dire les concepts contenant des données et manipulés dans le cadre des processus de l’entreprise. Par exemple, un contrat est un objet métier, manipulé dans le cadre de multiples processus et contenant des données comme le nom du client, son ID client, son numéro de contrat, les services souscrits, entre autres. 

Le découpage des Data Domains nécessite ainsi un travail préalable de recensement des objets métiers. Cela permettra aux métiers de s’accorder sur une terminologie commune (qu’est-ce qu’un client ? quels sont ses attributs ?) et d’être le plus exhaustif et pragmatique possible lors du découpage des données en Data Domains. 

Sous-estimer le temps nécessaire pour réaliser cette étape est une autre erreur, puisqu’elle nécessite d’étudier les processus de l’entreprise en profondeur. 

__

##  **Garder en l’état le bon vieux framework de gouvernance des données**

Le Data Domain Ownership est un pilier de l’approche Data Mesh. Rare sont les évolutions sur l’un des piliers qui n’entraine pas des changements sur le second. Le déploiement de data domaines représente un changement organisationnel profond, où chaque domaine devra assumer de nouvelles responsabilités et gagner en autonomie. Dans ce cadre, faire évoluer le cadre de gouvernance des données est essentiel pour s’assurer de leur prise d’autonomie tout en garantissant une cohérence globale favorisant l’échange de données entre domaines. 

![](https://www.quantmetry.com/wp-content/uploads/2023/10/gouv.png)

De surcroit, l’opérationnalisation des Data Domains requiert de monter un équipage avec certains nouveaux rôles pour le faire naviguer : data owner, data steward, data domain officer, data product owner. 

__

##  **Laisser le navire voguer sans boussole**

L’opérationnalisation des data domaines demande requiert de fixer un cap et de le suivre. Pour cela, le Data Domain Officer est le gardien de la boussole : avec l’aide de son équipage, il définira un cadre de déploiement du Data Domain avec une feuille de route, des objectifs, et des lignes directrices. 

**MANDAT**

**Construire le data domain** : d _éfinir le TOM et assurer son déploiement continu_

**Animer le data domain** : _faire vivre son data domain et l’intégrer à la gouvernance fédérale_

**Gouverner le patrimoine** : _assurer l’accessibilité, la qualité et la conformité des données_

**Gouverner les projets data** : _piloter le sourcing, la priorisation et le suivi des projets data_

**PRINCIPALES RESPONSABILITES**

En adéquation avec la gouvernance du Groupe 

  * **Décline la stratégie Groupe** au niveau de son data domain 
  * **Structure le modèle opérationnel** : organisation, processus clés, comités, outils, budgets… 
  * **Identifie, recrute ou nomme si besoin les contributeurs au niveau de son domaine** : data owner, data steward, data scientist, data analyst, data engineer, responsable applicatif, expert métier… 
  * **Dégage du budget et des moyens** sur son domaine 
  * **Assure l’acculturation** générale des collaborateurs aux sujets data 
  * **S’assure du bon niveau de compétences** des contributeurs via la formation si nécessaire 
  * **Remonte les KPI** à l’entité centrale en charge de la gouvernance des données 



__

##  **On verra plus tard pour les Data Products**

L’un des premiers chantiers du Data Domain Officer sera de définir les Data Products prioritaires à déployer. L’un des freins que nous rencontrons chez nos clients réside dans la compréhension de ce terme à grande échelle, la fixation de règles autour de ce concept et l’accompagnement tech pour soutenir le déploiement des premiers Products ; gestion des accès, déploiement des infrastructures, exposition des données, etc. 

Déployer des Data Domaines opérants est une transformation profonde, semée d’embuches. Voici **3 convictions** que nous portons pour appréhender au mieux ce changement : 

  * La connaissance des processus de l’entreprise et des données associées est un prérequis pour avancer sereinement 
  * Fixer des règles en amont et définir un mode opératoire sont essentiels pour aligner toutes les parties prenantes sur une stratégie de transformation objective, qui ne laisse pas la place aux débats 
  * L’opérationnalisation des Data Domaines engendre des changements organisationnels qui doivent être accompagnés d’une évolution plus ou moins profonde sur les 3 autres piliers 



_Contactez[ Quantmetry ](mailto: communication@quantmetry.com) et nos experts _ [ Jonathan Cassaigne ](mailto: jcassaigne@quantmetry.com) , [ Vlad Flamind ](mailto: vflamind@quantmetry.com) , [ Gill Morisse ](mailto: gmorisse@quantmetry.com) et [ Théo Vialard ](mailto: tvialard@quantmetry.com) _pour en savoir davantage sur notre approche de déploiement des Data Domains._

[ ![Data Strategy](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-Data-Startegy.svg) ](https://www.quantmetry.com/experts/#aistrategy)

Les membres de l’ [ expertise Data & Strat ](https://www.quantmetry.com/experts/#aistrategy) définissent une stratégie data et mettent en place le plan opérationnel de transformation pour tirer le meilleur des données au service des enjeux et des objectifs business. 

* * *

![Vlad Flamind](https://www.quantmetry.com/wp-content/uploads/2023/10/1516330826388-1.jpeg)

[ Vlad Flamind  ](https://www.linkedin.com/in/vflamind/)

Senior Manager 

Depuis plus de 10 ans, j'accompagne les entreprises dans l'élaboration et le mise en oeuvre de leurs stratégies de transformation. Je développe un expertise particulière sur les enjeux data et IA. 

![Théo Vialard](https://www.quantmetry.com/wp-content/uploads/2023/10/photo-tvi.png)

[ Théo Vialard  ](https://www.linkedin.com/in/th%C3%A9o-vialard-093708ab/)

Senior Data Consultant 

Consultant en Data Strategy, j’accompagne les entreprises depuis plus de 5 ans dans la définition et la mise en place de leurs plans de transformation digital et data. 
