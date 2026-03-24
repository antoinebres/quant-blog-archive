---
layout: post
title: ces-algorithmes-chasseurs-de-fraudeurs
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129153432/https://www.quantmetry.com/blog/ces-algorithmes-chasseurs-de-fraudeurs/
---
Uncategorized 

11/05/2017 

#  Ces algorithmes chasseurs de fraudeurs 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fces-algorithmes-chasseurs-de-fraudeurs%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Ces%20algorithmes%20chasseurs%20de%20fraudeurs&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fces-algorithmes-chasseurs-de-fraudeurs%2F "Twitter")

* * *

Auteurs : [ Gill Morisse ](https://www.linkedin.com/in/gillmorisse/) , [ Robin Lespes ](https://www.linkedin.com/in/robin-lespes-785a2127/) , [ Romain de San Nicolas ](https://www.linkedin.com/in/rdesannicolas/)

Temps de lecture : 7 minutes 

![Quantmetry.com : Ces algorithmes chasseurs de fraudeurs](https://quantmetry.b-cdn.net/wp-content/uploads/2017/05/1-6-1.png)

Face aux comportements de plus en plus réactifs, innovants et coordonnés des fraudeurs, les entreprises se dotent d’intelligences artificielles basées sur des algorithmes complexes. Mais la conception et l’industrialisation de tels systèmes relèvent du défi pour des entreprises qui doivent faire évoluer leurs organisations, se confronter à d’épineuses questions juridiques et d’une manière plus générale, repenser leur relation avec leurs clients. Dans une série d’articles dédiés, Quantmetry vous accompagnera dans la découverte de ce champ d’application passionnant, qui n’en est qu’aux prémices et qui illustre bien les impacts du Big Data. 

Dans les secteurs de la banque, de l’assurance ou encore des télécommunications, les comportements frauduleux sont à l’origine de pertes financières considérables. En France en 2014, les fraudes à la carte bancaire s’élevaient à 500 Millions d’euros* ; quant aux fraudes à l’assurance (fausses souscriptions, récupération de franchises, sinistres fictifs), elles représentaient 2,5 Md€* soit environ 5% des primes en dommages et sont en constante augmentation. 

De plus, les systèmes anti-fraude traditionnels basés sur des règles métier automatisées présentent souvent une rigidité dans la prise de décision qui a pour conséquence de bloquer des dossiers sains et génèrent donc un manque à gagner. 

Pour relever ces défis, les entreprises de ces secteurs commencent progressivement à se saisir des opportunités offertes par le big data. Voici un tour d’horizons des principales techniques utilisées dans la lutte anti-fraude. 

##  Exploiter de nouvelles données pour mieux contextualiser un individu 

En matière d’attribution de crédit, les modèles de scoring traditionnels s’appuient sur des techniques de régression logistique (soit des systèmes très robustes, fiables dans le temps mais contournables et bloquant de nombreux dossiers sains) et n’exploitent qu’une faible partie du référentiel de données client. 

Pour concevoir de nouveaux outils de machine learning, les data scientists exploitent l’open data (les données de l’Insee par exemple), les données transactionnelles, de localisation ou encore de navigation, ce qui permet de re-contextualiser de manière fine un individu demandant un prêt. Ces nouvelles typologies de données introduisent l’idée qu’un individu n’est pas forcément défini par une photo à un instant T de son patrimoine mais qu’il se situe bien dans un dynamique sociale et économique que seuls de grands volumes de données peuvent restituer. 

##  Les méthodes supervisées ; repérer les signaux faibles pour prédire la fraude 

Quel que soit le secteur, la méthode mathématique principalement utilisée pour exploiter ces volumes importants de données est la classification binaire supervisée, le but étant de prédire l’apparition d’un évènement de fraude. 

Cette approche nécessite la récupération d’un historique de données labellisées (individus identifiés comme sains ou fraudeurs avérés) et repose généralement sur des modèles constitués d’ensembles d’arbres de décision, comme le célèbre « Gradient Boosting Tree », et en particulier son implémentation XGBoost très populaire sous R ou Python. Utilisés également pour de la maintenance prédictive, ces modèles ont comme particularité de détecter et d’exploiter des signaux faibles en repérant des corrélations complexes entre un grand nombre de variables. 

En effet, la fraude correspond à un évènement rare, et le jeu de données est donc fortement déséquilibré : les “positifs”, c’est-à-dire les fraudeurs, ne représentent qu’une faible proportion de la totalité des observations (en deçà de 10%, voire parfois en deçà de 1%). 

Différentes techniques sont disponibles pour répondre à cette problématique, comme par exemple le resampling(duplication des positifs ou exclusion de négatifs), le weighting (attribution d’une pondération plus forte aux observations positives) ou encore l’utilisation d’un « base_score » (un paramètre permettant de réduire la proportion de fraudeurs à atteindre pour que le modèle considère positif un sous-espace des données). 

##  Relever les défis de la pression de sélection et de dégradation de la base d’apprentissage 

Les décisions prises sur la base des résultats d’un modèle en production modifient le comportement des fraudeurs et la nature des données émises, on parle de pression de sélection. Que fait-on alors des nombreux dossiers rejetés par les systèmes de contrôle déjà en place ? Doit-on tous les considérer comme fraudeurs avérés au risque d’introduire des « faux-positifs » dans le jeu de données ? Doit-on les écarter (Méthodologie KGB pour Known Good Bad) pour s’affranchir de ce biais quitte à creuser le déséquilibre entre les classes ? Ces choix peuvent altérer fortement la qualité de l’apprentissage du modèle et donc ses performances finales. Des techniques de « débiaisage » telle que la reclassification itérative, ou la mise en place d’un « groupe de contrôle » constitué par un ensemble d’individus pour lesquels aucun contrôle n’est réalisé (situation sans modèle, sans règles), font partie des solutions qui permettent aux data scientists d’entraîner leurs modèles sur des données non biaisées. 

##  Les méthodes non supervisées ou semi-supervisées ; détecter les anomalies comportementales et contrer l’inventivité des fraudeurs 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/1-6-1.png)

_Le comportement des fraudeurs s’adapte aux contrôles_

_Illustration, Quantmetry 2017, diffusion interdite sans accord_

Les méthodes supervisées sont performantes mais ne sont applicables que si les comportements frauduleux sont bien définis et que le nombre de cas enregistrés est suffisant. Or les arnaqueurs sont rusés et cherchent sans cesse à contourner les processus de contrôle. Il peut alors être pertinent d’adopter, en complément, des approches dites non-supervisées, qui consistent à assimiler la fraude à une anomalie et donc à détecter les pratiques qui dévient du comportement « normal ». 

Les algorithmes de clustering tels que le K-means ou Dbscan (dont nous avions parlé en deux articles de blog [ [ 1 ](https://www.quantmetry.com/single-post/2015/04/22/Clustering-DBSCAN-et-politique) ], [ [ 2 ](https://www.quantmetry.com/single-post/2015/12/01/Initiation-au-Clustering) ]) associés à la détection d’anomalies statistiques en sont une première approche. Il s’agit de regrouper les comportements et d’identifier les individus s’éloignant des « centroïdes », c’est à dire des barycentres des comportements de leurs pairs. Ils seront de fait déclarés comme cas anormaux. 

Dans le cas où l’on sait identifier les dossiers sains, il s’agit d’apprentissage semi-supervisé, qui présente l’avantage de ne pas confondre les cas de fraudes communs avec des comportements normaux. Les auto-encodeurs en sont un exemple innovant basé sur des réseaux de neurones spécifiques ayant une architecture en double entonnoirs décrite dans [ un article précédent ](https://www.quantmetry.com/single-post/2016/04/15/HARO-SUR-LA-FRAUDE-) . 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/7-1-1.png)

_Le clustering et la détection d’anomalies statistiques_

_Graphique illustratif, Quantmetry 2017, diffusion interdite sans accord_

##  Supervisés ou non, les algorithmes anti-fraude ne doivent pas faire abstraction ni des enjeux économiques, ni des enjeux réglementaires 

Un système anti-fraude n’est, en effet, pas seulement un calculateur de probabilité de fraude d’un individu. Sa finalité première est de réduire les pertes sèches et les coûts de renonciation. Il est en effet préférable de valider 10 dossiers frauduleux qui coûtent au total 1000 euros que de ne valider à tort qu’un seul dossier qui vaut 5 000 euros. La probabilité de fraude mesurée par un algorithme est donc généralement multipliée à l’impact financier que représente le dossier, ce qui a pour effet d’inciter le modèle à classifier comme douteux les dossiers présentant le risque financier le plus élevé. 

En cela, les nouvelles méthodologies apportées par la data science ne proposent pas d’apports substantiels aux logiques développées dans les domaines du risque. En revanche, la variété des traitements possibles, le croisement de grands volumes de données permettent d’accroître la précision du risque et d’arbitrer de manière plus fine, dans une logique ROiste mieux maîtrisée et mieux adaptée aux modèles économiques des sociétés. 

Mais si il est un domaine où le big data soulève de nombreuses interrogations, c’est sans conteste le domaine réglementaire. L’automatisation d’une partie d’une chaîne de décisions qui impactent la vie quotidienne des consommateurs, l’utilisation de données personnelles à des fins de contrôle peuvent être perçues comme des intrusions d’autant plus inquiétantes qu’elles sont difficiles à décrypter. 

Saisi de ces questions, le parlement Européen a adopté en avril 2016 le [ Règlement général sur la protection des données ](http://eur-lex.europa.eu/legal-content/FR/TXT/HTML/?uri=CELEX:32016R0679) ( [ RGPD ](http://eur-lex.europa.eu/legal-content/FR/TXT/HTML/?uri=CELEX:32016R0679) ) applicable dans l’ensemble des membre de l’union Européenne en mai 2018. Celui-ci institue notamment des sanctions plus importantes pour les entreprises (jusqu’à 20 millions d’euros ou 4 % du chiffre d’affaires total) et une meilleure coordination des autorités de protection des données, dont la CNIL, prévoit par exemple la possibilité pour le demandeur d’un prêt d’obtenir une information claire sur la logique qui sous-tend l’algorithme utilisé et le droit de demander une intervention humaine, c’est à dire la prise en compte de la responsabilité de l’analyste et son respect du code de conduite de l’établissement. 

La lutte contre la fraude dans un monde de plus en plus digitalisé est un enjeu important, que ce soit dans les secteurs de la banque, des assurances, ou des télécommunications. Correction de biais dans les données, statistiques descriptives, algorithmes prédictifs sont autant de leviers d’aide à la décision complémentaires qui, associés aux systèmes existants et aux contrôles manuels, peuvent limiter notablement les pertes du chiffre d’affaires. D’autres pistes méthodologiques sont à l’étude, comme l’analyse des réseaux sociaux et la détection d’appartenance à des communautés de fraudeurs. Mais aussi perfectionnées soient-elles, ces techniques ne pourront s’affranchir de la prise en compte de contraintes réglementaires, organisationnelles et technologiques qui sont autant de défis pour bâtir de manière pérenne des dispositifs de lutte anti-fraude industrialisés et adaptés au contexte des entreprises. 

Ce sont ces évolutions que nous aurons l’occasion de traiter de manière plus détaillée dans ce cycle d’articles dédiés à un sujet qui illustre la manière dont le big data transforme l’activité des entreprises. 

* Sources : 

-Rapport annuel de l’Observatoire de la sécurité des cartes de paiement | Exercice 2014 

– [ Rapport de l’Agence pour la lutte contre la fraude à l’assurance (Alfa) ](http://www.argusdelassurance.com/digest/analyses-donnees/les-chiffres-2014-de-la-fraude-a-l-assurance-dommages-rapport-alfa.96078)
