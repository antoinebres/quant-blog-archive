---
layout: post
title: intelligence-artificielle-en-sante-focus-sur-un-projet-innovant-innerve
date: 2025-07-09
url_wayback_machine: https://web.archive.org/web/20250709220408/https://www.quantmetry.com/blog/intelligence-artificielle-en-sante-focus-sur-un-projet-innovant-innerve/
---
Computer vision, Machine Learning, Recherche et développement 

10/01/2024 

#  Intelligence artificielle en santé, focus sur un projet innovant : Innerve 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fintelligence-artificielle-en-sante-focus-sur-un-projet-innovant-innerve%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Intelligence%20artificielle%20en%20sant%C3%A9%2C%20focus%20sur%20un%20projet%20innovant%20%3A%20Innerve&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fintelligence-artificielle-en-sante-focus-sur-un-projet-innovant-innerve%2F "Twitter") [ ](https://www.quantmetry.com/blog/intelligence-artificielle-en-sante-focus-sur-un-projet-innovant-innerve/ "Email") [ ](https://www.quantmetry.com/blog/intelligence-artificielle-en-sante-focus-sur-un-projet-innovant-innerve/ "Copy Link")

* * *

Auteurs : [ Alexandra Lorenzo ](https://www.linkedin.com/in/alexandra-lorenzo-de-brionne/) , [ Vincent Blot ](https://www.linkedin.com/in/vincent-blot-3a2897115/) , [ Olivier Petit ](https://www.linkedin.com/in/olivier-petit-97737a108/) , [ Clovis Adam ](https://www.aphp.fr/offre-de-soin/medecin/3101225/010/01) , [ Céline Labeyrie ](https://www.aphp.fr/offre-de-soin/medecin/3167138/010/01) , [ Olivier Trassard ](https://www.researchgate.net/profile/Olivier-Trassard) , [ David Adams ](https://www.aphp.fr/offre-de-soin/medecin/504360/010/01)

Temps de lecture : 7 minutes 

![Quantmetry.com : Intelligence artificielle en santé, focus sur un projet innovant : Innerve](https://www.quantmetry.com/wp-content/uploads/2023/02/cdc-ubjjuaov9os-unsplash-1.jpg)

##  **Vers un outil de diagnostic assisté par l’IA  
**

En 2020, Quantmetry gagne le Grand Défi « L’intelligence artificielle pour une expérience améliorée du système de santé » organisé par Health Data Hub et la BPI France, pour développer un algorithme permettant d’automatiser le traitement des images médicales dans le but d’améliorer le parcours de soins des patients. Dans ce contexte, Quantmetry et le département de neurologie de [ l’hôpital _Bicêtre AP-HP_ ](https://hopital-bicetre.aphp.fr/) se sont associés pour co-construire un outil d’aide au diagnostic de la neuropathie des petites fibres (NPF). 

###  Qu’est-ce que la neuropathie des petites fibres ? 

La neuropathie des petites fibres entraîne habituellement des douleurs, parfois des pertes de sensibilité ou encore des troubles de sudation. Les causes de neuropathies atteignant exclusivement les petites fibres sont nombreuses, la plus fréquente étant le diabète. 

Par ailleurs, la prévalence de ces NPF est estimée à 53/100 000 en Europe, ce qui représente environ 6 000 patients pour l’Île-de-France et 35 000 patients pour la France entière. 

Cependant, ces neuropathies peuvent également être révélatrices d’autres neuropathies plus diffuses et sévères, parfois mortelles, comme par exemple la neuropathie amyloïde familiale pour laquelle le service de neurologie de l’hôpital Bicêtre AP-HP est le centre de référence. 

![](https://www.quantmetry.com/wp-content/uploads/2023/02/illustration.png)

La mise en é  vidence de lé  sions de ces petites fibres nerveuses est difficile, elles ne sont pas dé  tectables par des  examens é  lectrophysiologiques standards tels que l’é  lectromyogramme (EMG). De ce fait, l’examen de ré  fé  rence recommandé  pour ce diagnostic par les instances internationales des neurologues spé  cialistes en neuropathies pé  riphé  riques est  la quantification de fibres nerveuses intra-é  pidermiques à  l’aide de la biopsie cutané  e [4]. 

###  L’IA au service de la santé 

Cependant, ce diagnostic né  cessite un comptage manuel, ré  pé  titif et chronophage (jusqu’à  1H30 par pa  tient pour un analyste expé  rimenté  ).  Un travail long et fastidieux gé  né  rant une forte variabilité  et conduisant é  ventuellement à  des erreurs de comptage. 

Finalement, en utilisant l’intelligence artificielle, l’algorithme dé  veloppé  par Quantmetry a permis de : 

  * Quantifier de faç  on automatique les fibres intra-é  pidermiques 
  * Ré  duire drastiquement le temps de lecture 
  * Réduire  le coû  t mé  dical 
  * Élargir l’accessibilité de cet examen à un plus grand nombre de patients 



##  Des donné  es complexes 

La collecte et préparation des données est réalisée par les équipes de l’hôpital Bicêtre AP-HP. Chaque patient subit trois ponctions cutanées de 3 mm sur la cuisse, le poignet et la cheville. Une coloration par immunofluorescence est ensuite réalisée, sur la base des recommandations actuelles de l’EFNS (”European Federation of Neurological Societies”) et de la PNS (”Peripheral Nerve Society”) pour l’évaluation de la densité des petites fibres [5]. En utilisant un protocole d’acquisition 3D, le scanner 3DHistech P250 Flash III numérise ces données. 

Au total, nous avons 69 lames extraites entre 2017 et 2020, dont 50% provenant de patients atteints d’amyloïdose TTR et 50% suspectés de NPF.   
Par la suite, nous rendons nos données totalement anonymes, c’est-à-dire qu’aucune information sur le patient n’est disponible. En fin de compte, cette perte d’information n’a aucune incidence sur le calcul de la densité des petites fibres nerveuses. 

Pour la détection de ces fibres nous nous basons sur l’annotation réalisée par les médecins de l’APHP. Toutefois, nous devons faire face à deux enjeux : 

  * La taille de l’objet : une fibre représente moins de 0.01% d’une image de biopsie cutanée 
  * La complexité de la tâche : fibres ou membrane basale peu visible, qualité de la lame et variabilité des annotations entre opérateurs. 



En utilisant la définition de Lauria [5] des fibres nerveuses intra-épidermiques, pour l’apprentissage du modèle IA, nous crééons des « bounding box » (boîtes rectangulaires) de taille fixe centrées sur la jonction entre la membrane basale et la petite fibre. Un exemple de calcul des règles de comptage des fibres nerveuses intra-épidermique est présenté sur la Figure 2. 

![](https://www.quantmetry.com/wp-content/uploads/2023/02/lauria1.png) _Figure 2. Les règles de comptage des fibres nerveuses intra-épidermiques._

La membrane basale (M) est mise en évidence en gris clair. Tandis que les fibres $F_1$, $F_2$, $F_4$, $F_5$ traversent chacune la membrane basale en un point et sont donc comptées. De même, la fibre $F_3$ a plusieurs branches dans l’épiderme, toutefois elle traverse la membrane basale en un seul point, nous la comptons donc une seule fois. 

En revanche, les fragments de fibres $NF_1$ et $NF_2$ se ramifient dans l’épiderme, mais ne traversent pas la membrane basale dans l’épiderme, ils ne sont donc pas comptés. 

Modélisation – une méthodologie à l’état de l’art   
![](https://www.quantmetry.com/wp-content/uploads/2023/02/coarse-to-fine.png) _Figure 3. Détection de la région d’intérêt_

Notre méthode est totalement automatisée et permet à partir d’images d’une lame entière de détecter l’ensemble des petites fibres nerveuses. Nous appliquons une approche « coarse-to-fine » appliquée à l’ensemble des plans z d’une lame.   
Dans un premier temps, à l’aide d’algorithmes non supervisés, nous détectons l’ensemble des coupes de la lame, puis dans un second temps nous détectons la région d’intérêt (« Region-of-Interest ») en utilisant un algorithme de segmentation d’instance à l’état de l’art, DeepLabv3+ [2].   
Ces premières étapes permettent d’extraire la zone intra-épidermique où se trouvent l’ensemble des petites fibres nerveuses (Fig. 3). 

Ensuite, une fois la région intra-épidermique détectée, nous créons des patchs sur lesquels nous appliquons un algorithme de détection d’objets (EfficientDet [6]) sur des images RGB en 1024×1024. 

![](https://www.quantmetry.com/wp-content/uploads/2023/02/efficientdet.png)

_Figure 4. Modèle EfficientDet_

Enfin, on détecte et agrège l’ensemble des prédictions du modèle Deep Learning afin de déterminer les petites fibres nerveuses. Nous utilisons le même principe que la Non Maximal Suppression [1] pour sélectionner une fibre parmi les nombreuses entités qui se chevauchent. En nous basant sur le critère IOU dans un espace 3D, nous sélectionnons les « bounding box ». 

##  Des résultats concluants 

###  Mesure de la performance d’un modèle 

Notre première analyse se situe au niveau des fibres. Nos métriques considèrent ici chaque fibre indépendamment, quelle que soit la lame sur laquelle elle se trouve. 

Nous obtenons des métriques globales de précision et de rappel, définies comme suit : 

\begin{equation*}   
\begin{aligned}   
Recall &= \frac{TP}{TP+FN}\\\   
Precision &= \frac{TP}{TP+FP}   
\end{aligned}   
\end{equation*} 

Finalement, nous obtenons un rappel de 81% et une précision de 80%. Ces résultats mettent en évidence la capacité globale de notre algorithme à détecter des fibres intra-épidermiques. 

![](https://www.quantmetry.com/wp-content/uploads/2023/02/results.png)

###  Variabilité inter-observateurs VS résultats du modèle IA 

Dans une deuxième analyse, nous comparons notre modèle d’IA avec la variabilité inter-observateurs.   
Ainsi, quatre experts ont annoté manuellement 10 coupes sur des lames avec différents niveaux de densité de fibres intra-épidermiques. 

Nos résultats de la variabilité inter-observateurs sont représentés par une extension du graphique de Bland Altman [2].   
La Figure 6 démontre que l’IA (points rouges) produit des résultats fiables que ce soit pour les patients malades ($\le$8 fibres/mm), que les patients non malades ($>$13 fibres/mm). En effet, la densité de petites fibres intra-épidermiques prédite par l’IA se situe dans l’intervalle de confiance à 95\% en raison de la variabilité intrinsèque des opérateurs. **![](https://www.quantmetry.com/wp-content/uploads/2023/02/agreementplot.png) **

Finalement, on représente la variabilité inter-observateurs et du modèle IA pour la quantification des fibres intra-épidermiques. Un symbole noir représente chacun des quatre experts et les résultats de l’IA sont visibles par des points rouges. Nous indiquons les limites supérieures et inférieures basées sur un intervalle de confiance à 95\% par des lignes horizontales. 

##  Explicabilité du modèle IA 

Pour conclure, nous avons implémenté une nouvelle méthodologie pour automatiser et accélérer le diagnostic des neuropathies à petites fibres. Pour la suite de ce projet, notre objectif est d’apporter une meilleure explicabilité de notre IA ainsi qu’une meilleure estimation des biais algorithmiques. 

Récemment, le CCNE et le CNPEN a publié un avis rassemblant seize recommandations pour les systèmes d’intelligence artificielle appliqués au diagnostic médical (SIADM) [7].   
À cet égard, nous présentons les recommandations suivantes: 

  * Recommandation N°6 : créer les conditions de la confiance en incitant les développeurs à fournir un certain niveau d’explicabilité du SIADM qu’ils mettent sur le marché. 
  * Recommandation N°11 : veiller à limiter les biais potentiels liés à la programmation des algorithmes et aux différentes bases de données utilisées. 



Par conséquent, le besoin d’une [ IA de confiance ](https://www.quantmetry.com/lp-ia-de-confiance/) dans le domaine médical est devenue essentielle, c’est pourquoi Quantmetry a démarré une thèse CIFRE sur la thématique « Quantification des incertitudes en Computer Vision ». 

##  Remerciements 

Nous souhaitons exprimer notre profonde reconnaissance à l’hôpital Bicêtre AP-HPpour leur collaboration et nos réunions hebdomadaires notamment le Pr [ David Adams ](https://www.linkedin.com/in/david-adams-211602223/) (Chef de service de neurologie), Dr [ Clovis Adam ](https://www.aphp.fr/offre-de-soin/medecin/3101225/010/01) (Anatomo-cyto-pathologiste), Dr [ Céline Labeyrie ](https://www.linkedin.com/in/c%C3%A9line-labeyrie-1b01296a/) (neurologue) et Olivier Trassard (ingénieur IRSN). Ce projet a été rendu possible grâce au soutien du [ Health Data Hub ](https://www.health-data-hub.fr/) et la BPI France. 

##  Références 

[1] Non-maximum  suppression,  [ https://towardsdatascience.com/non-maximum-suppression-nms  ](https://towardsdatascience.com/non-maximum-suppression-nms-93ce178e177c) . 

[2] Liang-Chieh  Chen,  Yukun  Zhu,  George  Papandreou,  Florian  Schroff,  and  Hartwig  Adam.  Encoder-  decoder  with  atrous  separable  convolution  for  semantic  image  segmentation,  2018\.  [ https://arxiv.org/abs/1802.02611  ](https://arxiv.org/abs/1802.02611) . 

[3] Mark Jones, Annette Dobson, and Sue O’Brian. A graphical method for assessing agreement with the mean  between multiple observers using continuous measures.  International journal of epidemiology  , 40:1308–13, 07  2011\. [ doi: 10.1093/ije/dyr109 ](https://pubmed.ncbi.nlm.nih.gov/21737402/) . 

[4] Giuseppe Lauria, David Cornblath, Olle Johansson, Justin Mcarthur, Svein Mellgren, M Nolano, N Rosenberg,  and Claudia Sommer.  Efns guidelines on the use of skin biopsy in the diagnosis of peripheral neuropathy.  European journal of neurology : the official journal of the European Federation of Neurological Societies  , 12:  747–58, 11 2005. [ doi: 10.1111/j.1468-1331.2005.01260 ](https://pubmed.ncbi.nlm.nih.gov/16190912/) . 

[5] Giuseppe Lauria, Mayienne Bakkers, Christoph Schmitz, Raffaella Lombardi, Paola Penza, Grazia Devigili,  A Smith, Sung-Tsieh Hsieh, Svein Mellgren, Thirugnanam Umapathi, Dan Ziegler, Catharina Faber, and In  gemar Merkies.  Intraepidermal nerve fiber density at the distal leg: A worldwide normative reference study.  Journal of the peripheral nervous system : JPNS  , 15:202–7, 09 2010. [ doi: 10.1111/j.1529-8027.2010.00271.x ](https://pubmed.ncbi.nlm.nih.gov/21040142/) . 

[6] Mingxing Tan, Ruoming Pang, and Quoc V. Le. [ Efficientdet ](https://arxiv.org/abs/1911.09070) : Scalable and efficient object detection, 2020. 

[7] Avis 141 du CCNE et 4 du CNPEN « Diagnostic Médical et Intelligence Artificielle : Enjeux Ethiques » 

[ ![Computer Vision](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-Computer-Vision.svg) ](https://www.quantmetry.com/experts/#computervision)

Les membres de [ l’expertise Computer Vision ](https://www.quantmetry.com/experts/#computervision) adressent des thématiques couvrant l’ensemble du cycle de valorisation des images : de la constitution du jeu de données à l’implémentation du modèle sur des dispositifs embarqués. 
