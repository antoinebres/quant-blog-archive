# cycle-de-vie-des-modeles-ab-testing-comment-assurer-la-performance
Wayback Machine URL: https://web.archive.org/web/20230322221515/https://www.quantmetry.com/blog/cycle-de-vie-des-modeles-ab-testing-comment-assurer-la-performance/
Archive date: 2023-03-22

IA de confiance 

31/10/2022 

#  Cycle de vie des modèles & AB testing, comment assurer la performance dans un processus industriel critique ? 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fcycle-de-vie-des-modeles-ab-testing-comment-assurer-la-performance%2F&title=Cycle%20de%20vie%20des%20mod%C3%A8les%20%26%20AB%20testing%2C%20comment%20assurer%20la%20performance%20dans%20un%20processus%20industriel%20critique%20%3F "Linkedin") [ ](http://twitter.com/intent/tweet?text=Cycle%20de%20vie%20des%20mod%C3%A8les%20%26%20AB%20testing%2C%20comment%20assurer%20la%20performance%20dans%20un%20processus%20industriel%20critique%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fcycle-de-vie-des-modeles-ab-testing-comment-assurer-la-performance%2F "Twitter") [ ](https://www.quantmetry.com/blog/cycle-de-vie-des-modeles-ab-testing-comment-assurer-la-performance/ "Email") [ ](https://www.quantmetry.com/blog/cycle-de-vie-des-modeles-ab-testing-comment-assurer-la-performance/ "Copy Link")

* * *

Auteurs : [ Gauthier le Courtois du Manoir ](https://www.linkedin.com/in/gauthierlecourtois/) , [ Marketa Pichlova ](https://www.linkedin.com/in/marketa-pichlova-lallementova-2111491/) , [ Jasmin Diantouba ](https://www.linkedin.com/in/jasmin-diantouba-90b8b4100/)

Temps de lecture : 2 minutes 

![Quantmetry.com : Cycle de vie des modèles & AB testing, comment assurer la performance dans un processus industriel critique ?](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/kolleen-gladden-ij5-qcbpivy-unsplash-2-scaled.jpg)

Il y a quelques années, très peu d’entreprises industrielles parvenaient à mettre en production des modèles d’apprentissage automatique. Aujourd’hui, la situation est très différente. De nombreux processus industriels critiques dépendent d’algorithmes d’apprentissage automatique, et il est vital que la performance de ces algorithmes reste stable dans le temps. 

Le comportement humain évolue dans le temps et un modèle entrainé sur les comportements d’il y a un an n’est plus forcément adapté au monde actuel. Pour ces cas d’usages, il y a un besoin réel de détecter et de s’adapter à ces dérives de données. 

#  Du ré-entraînement automatique à l’AB testing sur alertes 

L’un des moyens populaires et efficaces de maintenir le système en fonctionnement est le ré-entraînement régulier du modèle ML en incluant les données les plus récentes. Bien que cette méthode soit simple à mettre en œuvre, elle peut devenir assez coûteuse d’un point de vue informatique et organisationnel, surtout si le système Machine Learning est complexe ou contient de nombreux modèles à maintenir. 

Dans ce cadre nous présentons en détail les différents types de stratégies de ré-entraînement du modèle, y compris les techniques de ré-entraînement basées sur alertes, qui ont été explorées pendant un projet de R&D via une collaboration [ GRTgaz ](https://www.grtgaz.com/) & Quantmetry pour la prédiction de la demande de gaz. 

#  L’AB testing et ses paramètres 

Quand on parle d’AB testing on pense très souvent à des cas d’usage marketing en premier lieu. Il existe différents types d’AB testing, canari, shadow … qui ont chacun leur cas d’usages dédiés. Dans le cas des prévisions de consommations de gaz où il y a une vérité unique, nous avons utilisé le shadow AB testing afin de pouvoir mettre en compétition plusieurs stratégies de réentrainement. 

L’AB testing n’est pas si simple à mettre en place car un certain nombre de paramètres sont à investiguer. Quelle durée pour un AB testing ? AB testing continu ou sur alertes ? Et surtout quelle métrique de comparaison favoriser pour identifier le meilleur modèle sur la période d’évaluation ? 

Pour en savoir plus sur ces paramètres, sur les résultats obtenus sur notre cas d’usage ainsi que nos recommandations pour la reproduction de ces techniques pour votre projet. 

###  👉👉 [ Découvrez l’article complet ici ](https://medium.com/@gauthierlecourtois/from-systematic-re-training-to-ab-testing-triggered-on-data-drift-alerts-how-to-ensure-performance-20f470cac123) 👈👈 

##### 

[ ![Reliable Ai](https://quantmetry.b-cdn.net/wp-content/uploads/2022/06/Logo-Expertise-Reliable-Ai.svg) ](https://www.quantmetry.com/experts/#reliableia)

Les membres de l’ [ expertise Reliable AI ](https://www.quantmetry.com/experts/#reliableia) développent des modèles performants, fiables et maîtrisés, sur l’ensemble du cycle de vie, pour une IA de confiance. 

* * *

![Gauthier le Courtois du Manoir](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/gauthier-reworked.jpg)

[ Gauthier le Courtois du Manoir  ](https://www.linkedin.com/in/gauthierlecourtois/)

Manager de l'expertise Reliable AI 

Avec aujourd’hui plus de 9 années d’expérience en conseil et la mise en oeuvre de projets data, j’aide nos clients à la mise en place d’une IA de confiance avec un faible pour l’interprétabilité des modèles et la gestion de leur cycle de vie en production. 

![Marketa Pichlova](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/marketa-reworked.png)

[ Marketa Pichlova  ](https://www.linkedin.com/in/marketa-pichlova-lallementova-2111491/)

Lead data scientist chez GRTgaz 

Je dirige l’équipe Data science au sein du Département Data de GRTgaz. J’encadre des data scientist et data engineers dans la réalisation de projets d’intelligence artificielle. 

![Jasmin Diantouba](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/jasmin-reworked.png)

[ Jasmin Diantouba  ](https://www.linkedin.com/in/jasmin-diantouba-90b8b4100/)

Senior data scientist chez GRTgaz 

Au sein de l’équipe Data science du Département Data de GRTgaz, j’interviens dans la réalisation de projets d’intelligence artificielle de bout en bout, depuis les phases de démonstrateurs jusqu’à l’industrialisation au sein de processus opérationnels. 
