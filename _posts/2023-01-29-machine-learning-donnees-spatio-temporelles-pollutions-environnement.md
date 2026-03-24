---
layout: post
title: machine-learning-donnees-spatio-temporelles-pollutions-environnement
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129145604/https://www.quantmetry.com/blog/machine-learning-donnees-spatio-temporelles-pollutions-environnement/
---
Time Series 

16/06/2020 

#  Machine Learning à partir de données spatio-temporelles : prioriser les zones de contrôle des pollutions diffuses par la Police de l’Environnement 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmachine-learning-donnees-spatio-temporelles-pollutions-environnement%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Machine%20Learning%20%C3%A0%20partir%20de%20donn%C3%A9es%20spatio-temporelles%20%3A%20prioriser%20les%20zones%20de%20contr%C3%B4le%20des%20pollutions%20diffuses%20par%20la%20Police%20de%20l%E2%80%99Environnement&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmachine-learning-donnees-spatio-temporelles-pollutions-environnement%2F "Twitter")

* * *

Temps de lecture : 16 minutes 

![Quantmetry.com : Machine Learning à partir de données spatio-temporelles : prioriser les zones de contrôle des pollutions diffuses par la Police de l’Environnement](https://quantmetry.b-cdn.net/wp-content/uploads/2020/06/resource-eau.jpg)

✍  [ Sophie Monnier ](https://www.linkedin.com/in/sophie-monnier-83a80629/) , [ Rémi Rosenthal ](https://www.linkedin.com/in/r%C3%A9mi-rosenthal-29a744133/) , [ François-Xavier Ferlande ](https://www.linkedin.com/in/fran%C3%A7ois-xavier-ferlande/) , [ Cyril Bécret, ](https://www.linkedin.com/in/cyrilbecret/) [ Aleksander Dabrowski ](https://www.linkedin.com/in/aleksanderdabrowski/) (Quantmetry), [ Alexandre Liccardi ](https://www.linkedin.com/in/alexandre-liccardi/) (OFB) / Temps de lecture 20 minutes 

####  Contexte 

**Les plans de contrôle** **_Eau & Nature _ ** s’intéressent à 65 thématiques variées qui déclinent localement  (1) les politiques de contrôle répondant à une stratégie nationale : qualité de l’eau, gestion de la ressource, préservation des milieux, pêche, chasse et lutte contre le braconnage, espèces protégées  (…).  En 2019, ces plans de contrôles représentaient plus de 20 000 contrôles annuels pour l’Agence Française pour la Biodiversité (AFB). Sur l’ensemble de la France, 11 % des contrôles réalisés par l’AFB ont donné lieu à des suites juridiques. Sur certains territoires, comme la Bretagne où les politiques de police de l’environnement sont prédominantes, ces taux sont de l’ordre de 30 %. Suite à la fusion de l’ONCFS et de l’AFB en janvier 2020, ce sont plus de 1 800 agents qui participeront à ces contrôles pour la nouvelle structure formée : l’Office Français de la Biodiversité. 

Pour diverses raisons (sensibilisation, orientation des politiques locales, représentation sur le territoire…), les inspecteurs de l’environnement réalisent une part importante de contrôles conformes et n’optimisent pas la recherche des non-conformités. Il est possible de se demander, quel est le coût de cette sous-optimisation, et s’ils pourraient dégager du temps pour leur permettre de valoriser des activités à haute valeur ajoutée, telles que les processus judiciaires en aval du constat d’infraction, ou le contrôle de nouvelles zones à risque. 

Dans ce contexte, le projet lauréat du premier appel à manifestation d’intérêt IA porté par le département Etalab au sein de la Direction interministérielle du numérique (DINUM) et la Direction interministérielle de la transformation publique (DITP) avec le soutien du Secrétariat général pour l’investissement (SGPI), porté par l’AFB (aujourd’hui Office Français de la Biodiversité), et appuyé de Quantmetry, vise à évaluer et mettre à disposition le pouvoir prédictif des données librement disponibles sur les plateformes gouvernementales et appuyer l’élaboration des plans de contrôles. 

Les autres porteurs du projet sont le BRGM, sur les aspects les plus techniques et informatiques, et le Ministère de la Transition Ecologique et Solidaire (la Direction Eau et Biodiversité, le réseau scientifique et technique). 

Ce projet a été réalisé dans le cadre du tout premier appel à manifestation d’intérêt intelligence artificielle, porté par la DINUM et la DITP pour le Programme d’investissement d’avenir (PIA). Cet appel à projet fait suite aux recommandations du rapport Villani en 2018. L’équipe projet a répondu à l’appel à projet en septembre 2018. Accompagné par les équipes Etalab, le projet a été lancé début 2019 et la phase de prototypage a duré jusqu’au mois d’octobre. 

Le projet exploratoire, restreint au périmètre hydrographique du Bassin Versant Loire Bretagne, consiste à définir un indice de priorisation des contrôle de pollutions diffuses (essentiellement, pollution chimique des eaux) sur une maille 5x5km du territoire. Cet indicateur, assimilable à un risque, s’appuie sur des facteurs explicatifs parlants pour les inspecteurs de police afin de guider leur intervention sur le terrain : pressions anthropiques, état de l’environnement, sensibilité des milieux naturels et historiques des contrôles précédents. 

####  Consolidation de données open sources hétérogènes 

Sur les 35 sources de données identifiées comme potentiellement utilisables : 

  * On retrouve une forte dimension géographique : plus des ⅔ ont une composante géospatiale, 
  * 95% sont des données open sources (  [ https://geo.data.gouv.fr/fr/  ](https://geo.data.gouv.fr/fr/) ,  [ https://www.eaufrance.fr/  ](https://www.eaufrance.fr/) ), ce qui les rend accessible, mais pas forcément facile à harmoniser, car répondant à des référentiels différents (administratifs, agricoles, physiques, topographiques…) 
  * la composante temporelle est très variable : 70% sont des données fixes (informations départementales, référentiels géographiques), 15% ont une temporalité faible (fréquence pluri-annuelle, années manquantes), 15% une temporalité forte (annuelle ou sub-annuelle). 



Les données sont hétérogènes sur leur granularité spatiale et sur la méthode de requêtage (cf tableau ci-dessous pour quelques exemples) : 

Data  |  Disponibilité  |  Temporalité  |  Maille géographique   
---|---|---|---  
Contrôles de police  |  Interne AFB  |  annuelle  |  Point   
Ventes de pesticides  |  Interne AFB  |  annuelle  |  code postal   
Etat physico-chimique des cours d’eau  |  API Hub’eau  [ hubeau.eaufrance.fr/  ](https://hubeau.eaufrance.fr/) |  mensuelle  |  station de mesure   
Recueil de parcelles graphique  |  geo.data.gouv  [ agreste.agriculture.gouv.fr/  ](https://agreste.agriculture.gouv.fr/) |  annuelle (années manquantes)  |  parcelle agricole   
Tendances agricoles  |  geo.data.gouv  |  annuelle  |  Canton   
Rapportage DCE  |  [ eionet.europa.eu/  ](http://www.eionet.europa.eu/) |  3 ans  |  Masse d’eau   
Référentiel communal  |  IGN  |  annuelle  |  Commune   
  
Toutes ces données sont donc récoltées, nettoyées, et mises en base  **PostgreSQL** , qui permet par son extension PostGIS la  manipulation performante et reproductible de données géolocalisées en tant que  _ geométries  _ . Les volumes de données étant importants (plusieurs dizaines de milliers d’enregistrement), Quantmetry a dû mettre en place des ingénieries dédiées : modèles et index spécifiques, requêtes de jointures spatiales SQL et intégration GDAL optimisée.  Les bibliothèques Python  _ sqlAlchemy  _ facilitent l’accès aux ressources et modèles de PostGreSQL, afin de reposer au maximum sur les capacité de traitement en base (mode ELT). Sur python, ces objets sont récupérés avec l’extension GeoPandas,  qui ajoute aux fonctions de dataanlyse Pandas  la gestion des géométries,  les opérations spatiales (jointures, intersection, union, buffer, …)  et l’affichage de  cartes. 

####  Feature Engineering géospatial : concilier des échelles différentes 

Le modèle est construit sur un maillage 5×5 km du territoire Loire Bretagne. Or, aucune de nos sources de données brutes n’est définie sur cette maille. Le  _ Feature Engineering  _ doit donc comporter une logique de changement d’échelle spatiale et d’agrégation en plus d’une phase de processing classique. Nous détaillons ci-dessous quelques sources de données intéressantes parmi celles utilisées. 

**Donnée cible : contrôles de police**

La donnée cœur de l’intervention technique est la donnée des contrôles de police. Il s’agit de données ponctuelles, où un point correspond à un contrôle daté effectué par un inspecteur de l’Environnement, sur un thème particulier. Pour cette étude, nous ne conservons que les thèmes “nitrates” et “pesticides”. Ces contrôles représentent un volume de 15 000 points de contrôles sur un historique de 10 ans avec une répartition plutôt équilibrée des classes (56% de non-conformes contre 44% de conformes).  ![Bassin Loire-Bretagne - Quantmetry](https://quantmetry.b-cdn.net/wp-content/uploads/2020/09/capture-decran-2020-06-16-a-14-00-24-min-500x264.png)

_ Bassin Loire-Bretagne.   
_ La carte présente le type de parcelles agricoles majoritaires par découpage de 5km par 5km. Les points verts et rouges représentent les contrôles passés : conforme et non-conforme. 

Ces données présentent plusieurs particularités à prendre en compte pour le  _ feature engineering  _ , notamment : 

  * 44% des mailles sont sans contrôle, et 49% des mailles ont au plus 2 contrôles sur les 10 ans 
  * Il y a une  **différence d’interprétation** importante entre les contrôles conformes et non-conformes. Un contrôle non-conforme correspond à une infraction ponctuelle, relevée et identifiée à un endroit précis, alors que plusieurs contrôles conformes peuvent en réalité représenter une investigation sur le terrain plus longue et répartie sur plusieurs secteurs. 



Le  _ feature engineering  _ consiste donc en la création d’un score de conformité, à l’échelle de la maille géographique choisie (5 x 5 km) et traduisant les points mentionnés ci-dessous. 

![Schéma du processus de création de variable cible](https://quantmetry.b-cdn.net/wp-content/uploads/2020/09/capture-decran-2020-06-16-a-14-01-33-min-500x227.png)

_ Schéma du processus de création de variable cible  _

  * _ Le score doit refléter, pour chaque maille, la contribution et l’incertitude relative des contrôles conformes (points bleus) et non conformes (points rouges)  _


  * Pour chaque maille, le score de pollution est construit à partir d’une contribution principale de la maille centrale, à laquelle s’ajoute les contributions des mailles voisines géographiquement et l’état de ces mailles dans le passé. La contribution est exponentiellement décroissante avec l’éloignement spatial ou temporel de la maille centrale 
  * Restitution du score (rouge : non conforme ; bleu : conforme) sur une carte 



####  Etat physico-chimique des rivières 

Pour cette variable, nous utilisons l’API REST Hub’eau d’Eau France, disponible en open data. Elle regroupe tous les relevés physico-chimiques (température de l’eau, taux de nitrates, …) qui ont été effectués pour les cours d’eau du territoire depuis plusieurs décennies par des stations dédiées, ainsi que 8 API supplémentaires non utilisées ici. Dans notre cas, nous sommes intéressés par les paramètres liés aux pollutions chimiques diffuses, en grande partie figurée par les engrais et les pesticides c’est-à-dire : potentiellement plusieurs dizaines parmi les quelques milliers relevés.  <
