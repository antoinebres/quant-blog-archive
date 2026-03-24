---
layout: post
title: smart-cities-et-data-science-partie-1
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129151038/https://www.quantmetry.com/blog/smart-cities-et-data-science-partie-1/
---
Uncategorized 

25/02/2016 

#  Smart Cities et data science – Partie 1 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fsmart-cities-et-data-science-partie-1%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Smart%20Cities%20et%20data%20science%20%E2%80%93%20Partie%201&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fsmart-cities-et-data-science-partie-1%2F "Twitter")

* * *

Temps de lecture : 11 minutes 

![Quantmetry.com : Smart Cities et data science – Partie 1](https://quantmetry.b-cdn.net/wp-content/uploads/2016/02/screen-shot-12-30-18-at-06-19-pm.jpg)

Les Smart Cities sont à la mode ! Les think tank communiquent, les élus communiquent, les entreprises communiquent et pourtant, peu de gens sont capables d’expliquer concrètement de quoi il en retourne. 

Chez Quantmetry, nous avons décidé d’essayer d’y voir plus clair et de s’assurer que derrière le brouillard de la communication, se trouvait bien des perspectives d’avenir, des expérimentations et des projets à venir. 

Nous avons donc décidé d’accomplir un petit travail de veille sur les sujets Smart Cities et les avons évaluées au regard de leur potentiel en terme de Big Data. Cet article a donc vocation d’explorer les cas d’utilisation des Smart Cities ayant un fort contenu en Data Science. Nous avons fait le choix de n’en retenir qu’une dizaine, de les détailler et d’évaluer leur potentiel pour une entreprise comme la nôtre. Le choix d’en retenir que dix est évidemment sujet à discussion et nous espérons bien que vous nous en suggèrerez d’autres. 

_(NB : Les sujets d’économies circulaires et de démocratie participative sont certes passionnants, mais ne contiennent pas forcement beaucoup de potentiel lié aux données. Ils ont donc été écartés de notre liste)_

A noter que par respect pour nos ancêtres qui ont bâti de belles villes et compte tenu de certaines erreurs récentes d’aménagement du territoire, par modestie nous ne chercherons pas à trop généraliser le terme de ville intelligente. 

##  PRÉSENTATION DES CAS D’UTILISATION « SMART CITY » 

Chaque cas d’utilisation est abordé en suivant la même structure. La thématique est décrite d’une manière générale, en expliquant le secteur visé, les problèmes adressés et les améliorations possibles. Ensuite, nous détaillons de manière plus précise en quoi la Data Science apporte des réponses, et décrivons les bénéfices potentiels pour souligner l’’importance des enjeux. Enfin, pour chaque cas d’utilisation, nous présentons des expérimentations ayant déjà couvert, au moins partiellement, le sujet. Le présent article décrit les cinq premiers cas d’usages, les autres seront traités dans une publication à venir prochainement sur le blog. 

##  1\. ECLAIRAGE PUBLIC ADAPTATIF 

L’idée générale est de moduler l’éclairage public, de régler localement l’intensité lumineuse de chaque lampadaire en fonction de paramètres, et de prendre en compte une maintenance des équipements au plus juste (anticiper les défaillances). 

Cette régulation s’effectue en fonction des conditions extérieures : luminosité, mais aussi taux d’humidité ou encore avec des capteurs de présence (piétons à venir, flux d’automobiles). Avec la généralisation des capteurs au sein de la ville, le recueil et la centralisation de ce genre d’informations vont devenir de plus en plus simples, et des systèmes de maintenance prédictive ainsi que de priorisation des interventions autrefois inimaginables pourront être mise en œuvre avec relativement peu d’effort. 

En termes de Data Science, nous identifions deux sujets à part entière. Le premier est un sujet de type recherche opérationnelle / optimisation multicritère appliqué à la modulation lumineuse. Le second est un sujet de maintenance prédictive industrielle avec des modèles a priori plus complexes de Data Science. 

Les bénéfices attendus sont une réduction des consommations et des coûts de maintenance et une amélioration de la qualité du service (sentiment de sécurité des citoyens, remplacement immédiat des lampadaires défectueux). Enfin, en ajustant l’intensité lumineuse, les villes diminuent le niveau de la pollution lumineuse, améliorant ainsi son esthétique et son impact sur l’environnement immédiat. 

##  RÉFÉRENCES D’EXPÉRIMENTATIONS 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-06.20-PM.jpg)

L’expérimentation [ ](https://amsterdamsmartcity.com/projects/detail/id/93/slug/smart-light?lang=en<img src= "Rendered by QuickLaTeX.com") » data-type= »external »>Smart Light a eu comme cible privilégiée la réduction des consommations et l’amélioration de la sécurité dans la ville. Comme souvent arrive dans ce genre de projets, si son but et les technologies visées pour l’adresser sont clairs, les vrais résultats en termes d’objectifs atteints, de ROI, d’utilité pour les usagers restent plus flous. Une bonne pratique des projets d’innovation de datascience serait de tenir à jour cette liste d’objectifs en signalant les changements d’orientations (pivots) pour permettre une progression collective sur ces sujets. 

##  2\. OFFRE DE STATIONNEMENT DYNAMIQUE 

L’idée générale est de mettre en relation l’ensemble des parcs de stationnement d’une ville et d’agréger les informations sur les places disponibles pour aiguiller les automobilistes. Cette connaissance acquise sur l’occupation du stationnement est ensuite ré-exploitée sur une échelle de plus long terme pour travailler sur l’aménagement urbain et modéliser l’impact d’une modification de l’offre de stationnement. 

D’autres expériences sont menées sur la mise en place d’une tarification variable de l’heure de stationnement tenant compte du taux de remplissage des parkings. Cependant, ce type de dispositif se heurte à une faible acceptabilité sociale et n’est ni généralisable, ni souhaitable. 

En termes de Data Science, nous retrouvons un sujet intéressant qui mêle à la fois de l’optimisation multicritère avec des éléments plus complexes de détection de pattern (les situations d’engorgement se répètent elles ?) et de simulation. 

Pour ce qui concerne les bénéfices attendus, on peut envisager de réduire le trafic généré par les voitures recherchant une place de parking, avec un effet sensible sur la pollution dans les villes. [ Plusieurs études ](http://shoup.bol.ucla.edu/Cruising.pdf) ont en fait confirmé le rôle important joué par les automobilistes à la recherche d’une place sur les conditions globales de la circulation en ville. Le confort de conduite est aussi grandement amélioré avec une diminution des retards des conducteurs faute de place disponible. 

Les analyses effectuées dans la première phase, constituent un outil d’aide à la décision pour ce qui concerne la planification de nouvelles infrastructures de stationnement, leur positionnement dans la ville et le prix du stationnement. Un système de réservation anticipée des places de stationnement est aussi réalisable. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-06.20-PM-001.jpg)

##  RÉFÉRENCES D’EXPÉRIMENTATIONS 

[ Cet article de blog ](http://blog.rmi.org/blog_2013_10_24_smart_parking_can_transform_our_cities) se réfère à une liste de villes où des expérimentations dans ce sens ont été conduites : parmi elles San Francisco, Los Angeles, Stockholm, Beijing, Shanghai, São Paulo, et les Pays Bas. 

En particulier, la ville de Los Angeles a réalisé une expérimentation dans le quartier de Hollywood, très congestionné. Le focus était sur la tarification dynamique, sur l’information aux usagers via des applications mobiles et sur l’aide dans le contrôle plus efficace des différents parkings. Même si, comme reporté ici, la ville a obtenu des retours sur investissements déjà à trois mois du début de l’expérimentation, les améliorations pour les usagers en termes de meilleure occupation des places et de réduction du trafic inutile en ville ne sont pas clairement reportées. Comme souvent arrive, il n’est pas évident de distinguer les, tout à fait légitimes, efforts de marketing de l’entreprise qui propose ce genre de solution avec les résultats effectivement obtenus après sa réalisation. 

##  3\. TRANSPORT URBAIN OMNICANAL 

Dans une logique proche de l’optimisation du stationnement, les transports urbains se prêtent aussi à un partage des données en vue de favoriser l’intermodalité. De manière concrète, l’intermodalité consiste à proposer au voyageur une offre globale s’appuyant sur l’ensemble des moyens de transports d’une ville (une sorte de transport omnicanal, si on fait le parallèle avec le marketing). Une plateforme intermodale consolide les informations d’utilisation et d’exploitation de l’ensemble des moyens de transports à l’échelle d’une collectivité (bus, tramway, vélos, voiture, conditions de transport). Grâce à ces informations consolidées et interprétées, la ville est en mesure de proposer aux citoyens la solution la plus adaptée en tenant compte du contexte et des exigences du voyageur. 

Au niveau de la Data Science, au même titre que pour le stationnement en ville, l’intermodalité est d’abord un sujet d’optimisation de ressources sous contraintes. De manière plus large, l’ajout de nouvelles données (vidéo, conditions de circulation) et l’identification de patterns non linéaires (formation de bouchons, mesure de la congestion) rendent le sujet riche et complexe. Enfin, des algorithmes de scoring et de connaissance client sont exploités afin de tenir compte des préférences de l’utilisateur pour améliorer la préconisation. Peut-être ne faut-il pas proposer systématiquement des temps de trajet en vélo à un utilisateur quotidien d’un bus ? 

##  RÉFÉRENCES D’EXPÉRIMENTATIONS 

Plusieurs expérimentations ont été menées à des niveaux différents. Les systèmes de partage de vélos et de voitures (comme les services Velib et Autolib à Paris) utilisent déjà des méthodes d’intérêt pour la Data Science ; parmi elles, des algorithmes visant un positionnement optimal des vélos dans les stations, pour avoir plus de ressources dans les endroits où une demande plus élevée est prévue (par exemple autours des universités avant la sortie des étudiants). D’ores et déjà avec ces expérimentations partielles on peut bien voir l’ampleur des retombées positives soit pour les usagers (amélioration du service, personnalisation de l’offre, possibilité de repérer l’ensemble des informations sur une plateforme unique), soit pour les gestionnaires (meilleure connaissance des usages réels, incrément des revenus), soit pour la collectivité en général (diminution de la pollution, conditions de trafic améliorées, investissements ciblés). 

##  4\. RÉGULATION DU TRAFIC ROUTIER 

La coordination des feux de signalisation est un moyen efficace de régulation du trafic routier et de limitation des situations d’engorgement. En lissant le flux et en réduisant le nombre de véhicules passant par les goulots d’étranglement, il est ainsi possible d’augmenter le débit journalier et réduire le niveau de congestion du trafic. Par exemple, la réduction de vitesse sur le périphérique a eu pour effet de réduire les bouchons et la congestion. Malgré le côté contre intuitif de cet effet, l’explication physique vient du fait qu’en réduisant la vitesse maximale, l’amplitude des variations de vitesse a été réduite (les amateurs de mécanique des fluides savent déjà qu’il est préférable d’être dans des situations d’écoulement laminaire plutôt que chaotique). Un autre apport de la connaissance des conditions de circulation est l’utilisation de modèles pour tester l’impact de travaux routiers ou la construction de nouvelles infrastructures. 

![](https://static.wixstatic.com/media/d60f73_8c070818ec8e4e59964788f232e7e9b9~mv2.jpg/v1/fill/w_420,h_237,al_c,lg_1,q_80/d60f73_8c070818ec8e4e59964788f232e7e9b9~mv2.webp)

En termes de Data Science, il s’agit d’identifier des formes de congestion et de détecter et utiliser les moyens les plus efficaces pour les contraster. Parmi eux, on peut agir en général sur la vitesse maximale consentie ou sur la régulation de la temporisation des feux de trafic en fonction des conditions du trafic (détectées via caméras ou signaux GPS), des conditions de visibilité et en général de la météo, de la présence de piétons, de l’heure de la journée ou d’autres paramètres ressortant comme significatifs. 

Le plus direct bénéfice attendu est sans doute la réduction de bouchons et ralentissements et, de fait, du temps requis pour un déplacement. D’autres bénéfices collatéraux sont la réduction de la pollution atmosphérique et sonore, ainsi qu’une diminution du nombre d’accidents causés par les problèmes de circulation. 

##  RÉFÉRENCES D’EXPÉRIMENTATIONS 

[ La diminution de la vitesse sur le boulevard périphérique ](http://news.autoplus.fr/P%C3%A9riph%C3%A9rique-Paris-Limitation-vitesse-70-Bilan-Circulation-embouteillage-Etude-Inrix-1484973.html) de la ville de Paris a eu un effet très sensible sur la circulation, comme on peut remarquer par le fait que 36% de bouchons en moins ont été relevés. Ce genre d’effets non linéaires, souvent contre-intuiti 
