---
layout: post
title: histoire-du-hacking-health-camp-2015
date: 2023-03-22
url_wayback_machine: https://web.archive.org/web/20230322213222/https://www.quantmetry.com/blog/histoire-du-hacking-health-camp-2015/
---
Uncategorized 

14/04/2015 

#  Histoire du Hacking Health camp 2015! 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fhistoire-du-hacking-health-camp-2015%2F&title=Histoire%20du%20Hacking%20Health%20camp%202015%21 "Linkedin") [ ](http://twitter.com/intent/tweet?text=Histoire%20du%20Hacking%20Health%20camp%202015%21&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fhistoire-du-hacking-health-camp-2015%2F "Twitter") [ ](https://www.quantmetry.com/blog/histoire-du-hacking-health-camp-2015/ "Email") [ ](https://www.quantmetry.com/blog/histoire-du-hacking-health-camp-2015/ "Copy Link")

* * *

Temps de lecture : 4 minutes 

![Quantmetry.com : Histoire du Hacking Health camp 2015!](https://quantmetry.b-cdn.net/wp-content/uploads/2015/04/screen-shot-12-31-18-at-10-07-am.jpg)

Quantmetry était à Strasbourg du 19 au 22 mars dernier pour le Hacking Health Camp, le plus grand Hackathon européen dans le domaine de la santé. A la suite des conférences inaugurales, notre équipe a été retenue pour participer au Hackathon : un marathon de travail collaboratif rassemblant des professionnels de santé, des entrepreneurs, des développeurs, des designers et des associations de patients. Un jury composé de professionnels de santé, de professeurs de médecine et d’industriels était chargé de juger la qualité des projets et de décerner des prix à la fin du Hackathon. 

##  Quantmetry au Hacking Health Camp 

Avant d’arriver au Hacking Health Camp, nous avions déjà entamé des discussions autour d’un sujet sur le cancer du sein avec l’Unité de Sénologie du CHRU de Strasbourg, ainsi qu’avec une Association de patientes qui travaille sur le thème de «La Santé du Sein». Ce sujet consistait en l’exploitation des fiches de réunion de concertation pluridisciplinaire (RCP) de l’Unité de sénologie grâce à des techniques de machine learning. 

Chaque fiche, rédigée sous forme d’un fichier Word, contient l’histoire et l’évolution de la maladie d’une patiente. Ces fiches ont été remplies et actualisées pour les milliers de patientes de l’unité durant les dernières 25 années, et constituent une source précieuse d’informations. Nous avons décidé de nous limiter dans un premier temps (pour la durée du Hackathon) à l’étude de trois classes d’indicateurs sur une sous-population de 3000 patientes : 

  * Indicateurs de contexte : ménopause, tabagisme, etc. 

  * Indicateurs de traitement : mammectomie, chimiothérapie, etc. 

  * Indicateurs de gravité de la maladie : présence ou non de certaines protéines tumorales, récidive, métastases, etc. 




Notre projet, baptisé Senometry (en référence à l’Unité de sénologie du CHRU et à notre entreprise, Quantmetry), proposait la création d’un outil de rapports statistiques, basé sur une modélisation des corrélations entre ces trois types d’indicateurs. 

L’exploitation d’un historique aussi large de données peut représenter une aide précieuse pour les médecins et la collectivité. En mettant cet outil à disposition de tous les services de sénologie de France, voire à disposition de tous les services de cancérologie ou de maladies chroniques remplissant de telles fiches (urologie, dermatologie, diabétologie, etc.), on pourrait disposer de statistiques sur des échantillons de population très significatifs, ouvrant ainsi la voie à des études quantitatives complémentaires et à l’amélioration de la compréhension clinique et phénoménologique de la maladie. La poursuite du projet permettrait d’étendre les fonctions de l’outil à l’aide à la décision médicale, avec comme impact, par exemple, une meilleure gestion des problématiques de sous-traitement et de sur-traitement. 

Par ailleurs, la possibilité d’utiliser un outil de statistique automatique représente un potentiel gain de temps pour les médecins, leur permettant de fournir régulièrement des statistiques sur la maladie et leurs pratiques (nombre de récidives, nombre de mammectomies, de reconstructions, etc.) aux différents organismes de santé nationaux ou internationaux. Ce gain de temps se traduirait également par des impacts budgétaires positifs. 

##  Notre approche pour l’analyse des fiches RCP 

Un des points les plus importants soulevés lors des conférences du Hacking Health Camp a été la protection des données personnelles. L’anonymisation des fiches RCP a donc été un point crucial et a été résolu avant le lancement du projet, suivant les conseils prodigués par un avocat et un représentant de la CNIL que les organisateurs de l’événement avaient invités pour aider les équipes. 

Une fois les données anonymisées, dé-identifiées et formatées de manière exploitable, nous avons repéré les mots-clefs correspondant aux trois types d’indicateurs évoqués précédemment, ainsi que leurs variantes (masculin, féminin, adverbe, pluriel, etc.) à travers l’utilisation d’une distance de Levenshtein s’ajustant de manière automatique. Une fois ces mots-clefs détectés, nous les avons remplacés par une racine unique. 

Cette première approche a permis d’étudier différents paramètres contextuels, thérapeutiques et pronostiques selon les tranches d’âge avec des différences significatives selon les groupes d’âge. 

Nous avons ensuite entamé une analyse plus poussée des corrélations entre les trois types d’indicateurs grâce à des techniques de machine learning. Plus précisément, nous avons cherché les facteurs aggravants et protecteurs vis-à-vis des récidives du cancer du sein. Ainsi, en moins de 30h de travail, nous avons réussi à isoler certaines corrélations contre-intuitives entre différents indicateurs chez les patientes atteintes d’un cancer du sein, un des plus complexes qui soit. 

##  Next steps! 

Nous avons été confortés dans notre conviction de l’importance de ce sujet par l’attribution du « Prix de la Solution la plus Innovante pour la Santé » par le Jury d’Experts et par le « Prix du meilleur projet » par la Banque Publique d’Investissement (BPI), obtenus en compétition avec les autres projets. 

Nous allons proposer au CHRU le développement de ce projet du stade de prototype à celui d’une solution professionnelle en travaillant sur un plus gros volume de données, ce qui permettra d’évoluer vers une forme plus opérationnelle avec à la clef une aide aux équipes de recherche et probablement des publications scientifiques. 

Nous vous tiendrons bien sûr au courant des évolutions futures de ce projet à travers le blog de Quantmetry ! 
