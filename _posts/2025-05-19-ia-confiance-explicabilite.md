---
layout: post
title: ia-confiance-explicabilite
date: 2025-05-19
url_wayback_machine: https://web.archive.org/web/20250519103151/https://www.quantmetry.com/blog/ia-confiance-explicabilite/
---
IA de confiance 

30/05/2023 

#  Intelligence artificielle de confiance et explicabilité : ouvrir la boîte noire 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fia-confiance-explicabilite%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Intelligence%20artificielle%20de%20confiance%20et%20explicabilit%C3%A9%20%3A%20ouvrir%20la%20bo%C3%AEte%20noire&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fia-confiance-explicabilite%2F "Twitter") [ ](https://www.quantmetry.com/blog/ia-confiance-explicabilite/ "Email") [ ](https://www.quantmetry.com/blog/ia-confiance-explicabilite/ "Copy Link")

* * *

Auteur : [ Cyril Lemaire ](https://www.linkedin.com/in/cyril-lemaire-77433455/)

Temps de lecture : 6 minutes 

![Quantmetry.com : Intelligence artificielle de confiance et explicabilité : ouvrir la boîte noire](https://www.quantmetry.com/wp-content/uploads/2023/05/johannes-plenio-1vzlw-ihjam-unsplash-scaled.jpg)

L’intelligence artificielle de Confiance est un sujet que l’on adresse tous les jours chez Quantmetry pour fournir à nos clients des algorithmes de qualité. Ce sujet est traité par l’expertise Reliable AI qui assure la connaissance et l’application de l’état de l’art des 8 thématiques de l’IA de Confiance introduites dans [ cet article ](https://www.quantmetry.com/blog/ia-confiance-decennie/) . L’explicabilité est une de ces 8 composantes. 

![](https://www.quantmetry.com/wp-content/uploads/2023/05/explicabilite.png)

#  L’explicabilité, à quoi ça sert ? 

La course à la performance des modèles d’IA a rendu ces derniers plus complexes et moins interprétables. Or, pour avoir confiance dans le fonctionnement d’une IA, il faut pouvoir comprendre son raisonnement. L’explicabilité est un domaine de l’IA de confiance qui s’intéresse d’une part à comprendre comment une IA génère des prédictions, et d’autre part à expliquer ces prédictions aux utilisateurs. 

#  L’explicabilité, qu’est-ce que c’est ? 

Expliquer une IA c’est : « Faire comprendre à quelqu’un un modèle, une prédiction, les éclaircir en donnant les éléments nécessaires. Être une justification, constituer une raison suffisante ; être la cause de quelque chose ». On comprend dans cette définition adaptée du Larousse que l’explicabilité dans le contexte de l’IA contient plusieurs dimensions : 

##  **Les explications doivent être pertinentes**

Une explication doit répondre systématiquement à une question du type « pourquoi… ? » ou « comment … ? » (Par exemple : pourquoi telle décision est prise ? Comment modifier la prédiction ?) Il est donc primordial de bien identifier tous les acteurs-types gravitant autour d’un système d’IA ainsi que toutes les questions qu’ils se posent au regard de son fonctionnement. Chaque acteur (data scientist, utilisateur, régulateur…) pourra avoir des questions différentes et des niveaux d’expertises différents. 

Pour qu’un système d’IA soit considéré comme explicable, il est nécessaire de trouver les solutions techniques permettant de répondre à l’ensemble de ces questions, mais également de représenter ces réponses dans un format compréhensible adapté à chaque auditeur. 

##  **Les explications doivent être fiables**

Les outils d’explicabilité en IA utilisent souvent des méthodes statistiques en surcouche d’un modèle boîte noire, par exemple SHAP calcule des valeurs de Shapley. Il n’est donc pas toujours trivial que l’explication fournie soit bien fidèle à son fonctionnement. Dans ce cas, il est nécessaire d’évaluer la fiabilité des explications via des métriques telles que l’exactitude, la complétude ou la stabilité. 

Une autre alternative est l’utilisation de modèles glass-box (explicables par nature), pour lesquels l’explication est par définition fidèle au modèle. Il existe aujourd’hui des [ modèles glass-box très performants ](https://www.quantmetry.com/blog/comment-creer-des-modeles-interpretables-sans-approximation/) et nous recommandons fortement leur utilisation pour des cas d’usages critiques. 

##  **Les explications doivent s’appuyer sur une compréhension métier des relations de cause à effet**

Les modèles de machine learning peuvent apprendre sur tout type de données sans faire aucune hypothèse de causalité (par exemple, un modèle peut prédire le temps qu’il fait en comptant le nombre de parapluies dans la rue…). L’explication d’une prédiction d’un modèle ne peut donc pas systématiquement être interprété comme sa cause. 

Dans le cas où les explications sont utilisées pour prendre des décisions, il est important de bien identifier les scénarios et les liens de cause à effet sous-jacent à l’observation de la donnée, les facteurs de confusion, et d’établir le graphe de causalité de vos variables. 

#  L’explicabilité, comment l’activer ? 

Produire un système d’IA explicable est donc un processus technique, humain et organisationnel. Ces trois actions à mettre en place constituent les étapes essentielles à suivre : 

##  **Interroger**

La première action à prendre est de clairement définir les besoins en explicabilité. Il faut donc identifier tous les acteurs-types ainsi que les questions qu’ils peuvent se poser par rapports au modèle. Pour cela il est nécessaire d’organiser des ateliers avec toutes les personnes interagissant avec les prédictions de l’IA et de lister les questions qu’ils se posent, ainsi que les leviers qu’ils attendent pour prendre des décisions éclairées. Il est également important à ce stade de bien relever le format attendu des réponses (texte, visuel, interactif…). 

Le résultat de ces ateliers peut être formalisé dans un document de cadrage qui permet de choisir les méthodes à implémenter ainsi que leur format de restitution. 

##  **Visualiser**

Une fois que les besoins ont été clairement identifiés, il est maintenant nécessaire d’implémenter les méthodes permettant de produire les réponses pertinentes. Pour chaque besoin exprimé, il faut identifier un ou plusieurs outils techniques permettant d’y répondre, les implémenter, et restituer leurs résultats de manière visuelle, adaptée au niveau de compétences de l’utilisateur. 

Il est recommandé d’utiliser autant que faire ce peut un modèle explicable par nature, qui permet de répondre de manière fiable à une bonne partie des questions sans avoir à utiliser trop de surcouches d’explicabilité. 

Quel que soit le type de modèle et d’explication utilisé, Il est important d’impliquer les utilisateurs dans le développement des interfaces de restitution afin de s’assurer que leurs besoins soient bien adressés. Il s’agit donc d’un processus itératif de développement et de prise de retours durant lequel de nouveaux besoins peuvent émerger. Cette étape tisse des liens étroits avec l’UX design. 

##  **Caractériser**

En plus de s’assurer que les explications soient pertinentes, il faut également s’assurer qu’elles soient bien représentatives du fonctionnement du modèle. Si on ne valide les explications qu’auprès des utilisateurs, on peut facilement tomber dans le piège du biais de confirmation ! 

En fonction du type de tâche, Il existe plusieurs tests et métriques permettant de vérifier la fiabilité de nos explications. On peut par exemple vérifier si plusieurs types d’explications sont d’accord entre elles (comparaison), vérifier si deux points proches ont des explications proches (stabilité) ou encore si l’explication permet de bien retrouver les prédictions du modèle (exactitude). Une fois de plus, il est recommandé d’utiliser un modèle explicable par nature afin de s’affranchir des problèmes de fiabilité de l’explication. Dans le cas contraire, il est nécessaire d’effectuer et de documenter [ une analyse de fiabilité ](https://towardsdatascience.com/building-confidence-on-explainability-methods-66b9ee575514) du système d’explicabilité. 

#  L’explicabilité en vrai ça donne quoi ? 

Avec l’arrivée imminente de l’AI Act, les organismes règlementaires vont devoir s’assurer que les IA à haut risque mises sur le marché aient un niveau satisfaisant d’explicabilité. Dans ce cadre, l’ACPR (l’Autorité de Contrôle Prudentiel et de Résolution) a organisé en 2021 un Tech Sprint sur l’explication de modèles d’octroi de crédit, qui a été gagné par l’équipe de Quantmetry ! 

Afin de proposer un système d’IA explicable, il a d’abord été nécessaire d’identifier les 4 différents acteurs : Le client (dont le crédit est accepté ou refusé par l’IA), le conseillé bancaire (ou middle office qui utilise l’outil d’IA), le concepteur (Data Scientist) et le régulateur (ici l’ACPR). Le système d’explicabilité est donc constitué d’une application interactive avec 4 pages contenant les questions identifiées pour chacun des utilisateurs, ainsi que les réponses proposées. 

Par exemple pour le client deux questions sont identifiés: 

  * _« Pourquoi mon crédit a été refusé ?»_ : la réponse sous forme de phrases dans un français compréhensible est générée à partir de l’importance calculée des variables d’entrée (en utilisant la librairie [ Shapley Regression ](https://github.com/iancovert/shapley-regression) , une alternative à SHAP). 
  * _« Comment puis-je changer la décision ? »_ : des scénarios alternatifs (contrefactuels) basés sur les caractéristiques du client et permettant d’inverser la décision du modèle sont proposés au client (en utilisant la [ librairie DICE ](https://github.com/interpretml/DiCE) ). 



![](https://www.quantmetry.com/wp-content/uploads/2023/05/laptop-streamlit.png) _Figure 1: Application Streamlit présentant les explications du modèle de risque de crédit. Chaque explication/visualisations a été pensée pour répondre aux différentes questions des utilisateurs et validées auprès de partenaires dans le domaine de la banque. Cette page présente la prédiction pour un client, les 2 questions identifiées ainsi que des phrases d’explications._

Ce système d’explicabilité est une solution pour un modèle de classification binaire en données tabulaires. Pour des tâches différentes comme le forecast (en séries temporelles) ou la segmentation (en Computer Vision) les outils utilisés et les visualisations seront très différentes. Néanmoins, la démarche à implémenter (interroger, visualiser, caractériser) pour obtenir des explications fiables et pertinentes sera toujours la même, quel que soit le cas d’usage ! 

[ ![Reliable Ai](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-Reliable-Ai.svg) ](https://www.quantmetry.com/experts/#reliableia)

Les membres de l’ [ expertise Reliable AI ](https://www.quantmetry.com/experts/#reliableia) développent des modèles performants, fiables et maîtrisés, sur l’ensemble du cycle de vie, pour une IA de confiance. 

* * *

![Cyril Lemaire](https://www.quantmetry.com/wp-content/uploads/2023/05/1620991371818.jpeg)

[ Cyril Lemaire  ](https://www.linkedin.com/in/cyril-lemaire-77433455/)

Senior Data Scientist dans l'expertise Reliable AI 

Cyril a rejoint l’expertise IA de confiance de Quantmetry après un parcours de recherche en science de l’ingénieur. En plus de ses activités de conseil, Il est le référent R&D de tous les projets liés à l’explicabilité des modèles d’iA et à la sustainability. 
