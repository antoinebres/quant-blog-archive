# les-grandes-tendances-du-moment-en-times-series
Wayback Machine URL: https://web.archive.org/web/20250519111559/https://www.quantmetry.com/blog/les-grandes-tendances-du-moment-en-times-series/
Archive date: 2025-05-19

Recherche et développement, Time Series 

17/11/2023 

#  Les grandes tendances du moment en Times Series 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fles-grandes-tendances-du-moment-en-times-series%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Les%20grandes%20tendances%20du%20moment%20en%20Times%20Series&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fles-grandes-tendances-du-moment-en-times-series%2F "Twitter") [ ](https://www.quantmetry.com/blog/les-grandes-tendances-du-moment-en-times-series/ "Email") [ ](https://www.quantmetry.com/blog/les-grandes-tendances-du-moment-en-times-series/ "Copy Link")

* * *

Auteurs : [ François Culière ](https://www.linkedin.com/in/francoiscl/) , [ Ryad Belhakem ](https://www.linkedin.com/in/ryad-belhakem-phd-646276116/) , [ Hông-Lan Botterman ](https://www.linkedin.com/in/h%C3%B4ng-lan-botterman-037081236/) , [ Julien Roussel ](https://www.linkedin.com/search/results/all/?fetchDeterministicClustersOnly=true&heroEntityKey=urn%3Ali%3Afsd_profile%3AACoAAAppv3oBZfRM6368ZaJPDpS0_z83Sv3cNkE&keywords=julien%20roussel&origin=RICH_QUERY_SUGGESTION&position=0&searchId=8005bd8d-be14-4e5f-986f-8c3d1af6058a&sid=JOi&spellCorrectionEnabled=false)

Temps de lecture : 7 minutes 

![Quantmetry.com : Les grandes tendances du moment en Times Series](https://www.quantmetry.com/wp-content/uploads/2023/10/gettyimages-690073036.webp)

##  Retour sur notre visite au ECML Turin, Conférence Européenne en Machine Learning 

Participer à une conférence offre une opportunité exceptionnelle d’explorer le monde de la recherche, que ce soit pour élargir ses connaissances scientifiques, confronter ses idées à ses pairs, repérer de nouvelles opportunités ou établir des liens au sein d’un réseau professionnel. Si cette année vous n’avez pas eu la possibilité d’y assister, nous vous proposons un résumé des sujets les plus brûlants du moment ! 

L’European Conference on Machine Learning ( [ ECML ](https://2023.ecmlpkdd.org/) ) s’impose comme l’une des conférences généralistes les plus importantes en Europe, réunissant plus de 1400 participants. Elle accorde une place de choix aux séries temporelles à travers des ateliers et des papers sessions dédiées. 

À l’honneur, la conférence plénière de [ Kate Crawford ](https://www.katecrawford.net/about.html) a mis en lumière les préoccupations sociétales liées à l’essor de l’IA générative, soulevant les inquiétudes entourant des entités telles que ChatGPT, Midjourney, et d’autres. Elle a mis en avant les réalités tangibles qui sous-tendent ces technologies : des ensembles de données massifs aux annotations loin d’être neutres, une industrie de l’annotation aux retombées sociales dramatiques, et une dépendance des infrastructures aux pénuries de matériaux. Ces enjeux font écho aux priorités de l’IA de confiance telles que définies par l’Union européenne, ainsi qu’à nos propres travaux chez Quantmetry. 

La quête de performances va bien au-delà de la simple précision des algorithmes, que ce soit dans les sphères industrielles ou académiques. Trois autres piliers de l’IA de confiance ont été largement abordés dans le contexte des données temporelles : la qualité des données, l’incertitude et l’intelligibilité. Dans la suite de cet article nous balayerons ces trois sujets captivants, en nous focalisant sur les enseignements de cette année. 

##  Gestion des valeurs manquantes : Comment rétablir la confiance en la donnée ? 

La qualité des données est assurée, entre autres, par une bonne gestion des valeurs manquantes. Ces dernières restent un obstacle majeur à l’analyse des données dans de nombreuses applications, en particulier pour les données de capteurs (omniprésents dans l’industrie, le médical, les transports, …). Deux approches existent : la première consistant à imputer les données manquantes puis à réaliser la tâche d’intérêt en aval ; la seconde consiste à développer directement des modèles « robustes » aux données manquantes. 

Pour la première approche, [ Breehey Roskams-Hieter et al. [1] ](https://arxiv.org/abs/2209.15321) ont présenté des beta-Variational Auto-Encodeurs (β-VAE), plus robustes que les VAE, pour l’imputation de données génomique. Ces modèles permettent d’estimer l’incertitude associée à l’imputation, on parle d’imputation multiple. Une fois le jeu de données imputé, nous pouvons dès lors procéder à n’importe quelle tâche en aval, e.g. classification, régression ou prédiction. Cette approche est donc la plus versatile. 

A l’inverse, [ Jingwai Zuo et al. [2] ](https://link.springer.com/article/10.1007/s10618-022-00903-7) ont présenté une approche directe pour la prédiction de trafic. En quelques mots, ils modélisent conjointement le traitement des valeurs manquantes et les tâches de prévision du trafic à l’aide d’un réseau de neurones à convolution de graphes. Ils montrent que pour des motifs complexes de données manquantes, leur méthode fournit de meilleures prédictions que si on impute et prédit séparément. L’approche directe est donc à préférer lorsqu’on se focalise sur la performance d’une tâche spécifique. 

Ces travaux sont en lien direct avec ceux menés par Quantmetry sur l’imputation de données manquantes et le package open source [ Qolmat ](https://github.com/Quantmetry/qolmat) . Pour l’instant, ce dernier comprend uniquement des méthodes d’imputations, mais les récents travaux montrant l’avantages des méthodes gérant nativement les données manquantes peuvent ouvrir de nouvelles pistes pour la librairie. 

Pour une introduction aux différentes facettes de la qualité de données, c’est [ par ici ](https://www.quantmetry.com/blog/ia-confiance-donnees/) . 

##  Incertitudes : Comment associer un niveau de confiance aux prédictions d’un modèle ? 

Une meilleure gestion des incertitudes reste une préoccupation majeure dans la construction des modèles de Machine Learning. Que ce soit pour de la prévision de vente, une attribution de prêt ou un scoring de client, on souhaite souvent connaître le degré de certitude d’une prédiction pour y associer une décision métier. L’équipe de Eyke Hüllermeier a présenté les dernières recherches sur la dissociation des incertitudes aléatoriques (liées au processus de génération des données) et épistémiques (liées au manque d’information du modèle et réductible). Dans leur dernière [ publication ](https://arxiv.org/pdf/2301.12736) [3], ces chercheurs ont montré qu’il n’existe pas de fonction de perte qui permette de reconstruire fidèlement l’erreur épistémique contrairement à la reconstruction des erreurs aléatoriques. Ce résultat montre le vrai défi de dissocier les deux types d’erreur. 

Un deuxième sujet important de la conférence se trouve à l’intersection entre explicabilité et incertitude : l’explication de l’incertitude et l’incertitude des explications. [ Carlous et al. ](https://ojs.aaai.org/index.php/AAAI/article/view/26755/26527) montrent comment utiliser les valeurs de Shap sur les incertitudes d’un modèle pour monitorer sa dérive [4]. 

Enfin, de nombreux papiers reposent sur les prédictions conformes pour estimer l’incertitude. Cette approche est notamment au cœur de notre librairies open source Mapie qui permet de calibrer les prédictions d’un modèle et de calculer fidèlement l’erreur aléatorique. Cette conférence a mis en avant, pour Quantmetry et sa librairie Mapie, les défis à surmonter pour les années qui suivent.   
L’incertitude est au service de la robustesse des modèles, un des piliers de l’IA de confiance, qui a fait l’objet d’un [ article ](https://www.quantmetry.com/blog/ia-confiance-robustesse/) sur notre blog ! 

##  Intelligibilité : Comment expliquer les prédictions d’un modèle ? 

L’intelligibilité des modèles de machine learning devient une préoccupation croissante à mesure que ces modèles continuent d’impacter nos vies. Dans le domaine des séries temporelles, cet aspect est souvent négligé lors de la mise en place de solutions. L’édition 2023 d’ECML PKDD apporte des éclaircissements significatifs et présente des contributions pertinentes. L’équipe dirigée par Andreas Theissler [ [5] ](https://ieeexplore.ieee.org/iel7/6287639/9668973/09895252.pdf) propose notamment une taxonomie intéressante des méthodes existantes. Cette taxonomie repose sur la quantité d’information utilisée dans une courbe pour effectuer l’attribution, et elle se divise en trois catégories : 

1\. Utilisation d’un ou plusieurs points de la courbe, on retrouve ici les classiques SHAP et LIME (il faut noter que c’est fortement lié au processus de création de feature)   
2\. Utilisation d’une partie de la courbe, les shaplets, par exemple, tentent d’identifier des motifs caractéristiques au sein des courbes permettant de les classifier.   
3\. Utilisation de l’intégralité de la courbe, on peut citer l’ [ Explication Conceptuelle [6] ](https://ieeexplore.ieee.org/iel7/9200848/9206590/09207341.pdf?casa_token=4yqHjc-MRUgAAAAA:t9_EMHs6YvaP8Aq7lPYblgLAaY6jmZGDqAccik3SBnbxHaDk6kG-KoGIUn2o01JDUhcnUe0o0Zg) , conçue pour évaluer l’impact de features sur le comportement des modèles. 

Il est à noter que ces travaux accordent une attention limitée à la prévision dans les séries temporelles, se concentrant principalement sur la classification, qui est un domaine plus exploré. 

Le package [ Z-Time ](https://github.com/zedshape/ztime) , développé par [ Zed Lee [7] ](https://link.springer.com/article/10.1007/s10618-023-00969-x) , présente une approche intéressante. Ce modèle de classification des séries temporelles est explicatif par nature, recherchant des liens entre des abstractions temporelles (représentant des événements passés dans une série temporelle définie par une plage de valeurs) et leur comportement futur. Z-Time utilise ces abstractions temporelles ainsi que les relations temporelles entre les intervalles d’événements pour créer des caractéristiques interprétables à travers plusieurs dimensions de séries temporelles. L’évaluation expérimentale effectuée sur des ensembles de données de séries temporelles multivariées de l’UEA a montré que Z-Time atteint une efficacité comparable à celle des meilleurs classificateurs de séries temporelles multivariées non interprétables, tout en étant plus rapide que tous les classificateurs de séries temporelles multivariées interprétables. De plus, il présente l’avantage d’être robuste en cas de données manquantes. 

Cependant, les limites des travaux existants en séries temporelles sont principalement liées aux problématiques de prévision. Bien que des pistes intéressantes aient été évoquées, notamment en utilisant le principe de causalité, aucune avancée majeure, package ou méthodologie satisfaisante n’a encore été proposée. 

Pour une présentation des enjeux liés à l’intelligibilité, n’hésitez pas lire cet autre [ article ](https://www.quantmetry.com/blog/ia-confiance-explicabilite/) sur notre blog ! 

##  Conclusion 

Cette conférence nous a permis de renforcer notre connaissance de l’état de l’art sur des thèmes que nous avions dans le viseur. Mais il nous a aussi fait découvrir de nouveaux sujets inattendus, comme les approches GNN inspirées de la physique. Elle a aussi été l’occasion de riches rencontres humaines et scientifiques ! 

##  Références 

[1] Roskams-Hieter, Breeshey, Jude Wells, and Sara Wade. « Leveraging variational autoencoders for multiple data imputation. » Joint European Conference on Machine Learning and Knowledge Discovery in Databases. Cham: Springer Nature Switzerland, 2023.   
[2] Zuo, Jingwei, et al. « Graph convolutional networks for traffic forecasting with missing values. » Data Mining and Knowledge Discovery 37.2 (2023): 913-947.   
[3] V. Bengs, E. Hu ̈llermeier, and W. Waegeman. On second-order scoring rules for epistemic uncertainty quantification. In Proc. ICML, 2023.   
[4] Carlous Mougan, Dan Saattrup Nielsen, Monitoring Model Deterioration with Explainable Uncertainty Estimation via Non-parametric Bootstrap, 2022   
[5] Theissler, A., Spinnato, F., Schlegel, U., & Guidotti, R. (2022). Explainable AI for Time Series Classification: A Review, Taxonomy and Research Directions. IEEE Access.   
[6] Küsters, F., Schichtel, P., Ahmed, S., & Dengel, A. (2020, July). Conceptual explanations of neural network prediction for time series. In 2020 International joint conference on neural networks (IJCNN) (pp. 1-6). IEEE.   
[7] Lee, Z., Lindgren, T., & Papapetrou, P. (2023). Z-Time: efficient and effective interpretable multivariate time series classification. Data mining and knowledge discovery, 1-31. 

[ ![Time Series](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-Time-Series.svg) ](https://www.quantmetry.com/experts/#timeseries)

La mission de l’ [ expertise Time Series ](https://www.quantmetry.com/experts/#timeseries) est d’exploiter le potentiel de vos séries temporelles à l’aide de solutions d’IA : analyse des données historiques, prévisions de demande, de parts de marché, de production, détection d’anomalies sur des données IoT. 

* * *

![François Culière](https://www.quantmetry.com/wp-content/uploads/2023/10/fcu.jpeg)

[ François Culière  ](https://www.linkedin.com/in/francoiscl/)

Data Scientist chez Quantmetry 

Membre de l’expertise Time Series, François est en particulier passionné par les sujets de modélisation causale en contexte temporel et d’optimisation sous contrainte. 

![Ryad Belhakem](https://www.quantmetry.com/wp-content/uploads/2023/10/rbe2.jpg)

[ Ryad Belhakem  ](https://www.linkedin.com/in/ryad-belhakem-phd-646276116/)

Data Scientist chez Quantmetry 

Ryad fait partie de l’expertise Time Series. Il est passionné par les cas d’usage financiers et a en particulier travaillé sur des sujets d’intelligibilité pour faciliter l’adoption des solutions IA. 

![Hông-Lan Botterman](https://www.quantmetry.com/wp-content/uploads/2023/10/hbo.jpg)

[ Hông-Lan Botterman  ](https://www.linkedin.com/in/h%C3%B4ng-lan-botterman-037081236/)

Data scientist chez Quantmetry 

Hông-Lan fait partie de l’expertise Time Series et a participé à la librairie open source Qolmat en développant et implémentant de nouveaux algorithmes statistiques de mise en qualité des données. 

![Julien Roussel](https://www.quantmetry.com/wp-content/uploads/2023/10/1667473044944.jpg)

[ Julien Roussel  ](https://www.linkedin.com/search/results/all/?fetchDeterministicClustersOnly=true&heroEntityKey=urn%3Ali%3Afsd_profile%3AACoAAAppv3oBZfRM6368ZaJPDpS0_z83Sv3cNkE&keywords=julien%20roussel&origin=RICH_QUERY_SUGGESTION&position=0&searchId=8005bd8d-be14-4e5f-986f-8c3d1af6058a&sid=JOi&spellCorrectionEnabled=false)

Expert Time Series chez Quantmetry 

Julien anime l’expertise Time Series de Quantmetry en coordonnant la veille et la capitalisation des savoirs. Il développe en particulier les approches Reliable Time Series à travers ses missions et notre R&D. Il est également lead tech de la librairie open source Qolmat. 
