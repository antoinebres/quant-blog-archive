# synthese-de-la-7eme-edition-du-meetup-paris-data-ladies
Wayback Machine URL: https://web.archive.org/web/20230606091441/https://www.quantmetry.com/blog/synthese-de-la-7eme-edition-du-meetup-paris-data-ladies/
Archive date: 2023-06-06

Uncategorized 

13/06/2018 

#  Synthèse de la 7ème édition du meetup Paris Data Ladies ! 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fsynthese-de-la-7eme-edition-du-meetup-paris-data-ladies%2F&title=Synth%C3%A8se%20de%20la%207%C3%A8me%20%C3%A9dition%20du%20meetup%20Paris%20Data%20Ladies%20%21 "Linkedin") [ ](http://twitter.com/intent/tweet?text=Synth%C3%A8se%20de%20la%207%C3%A8me%20%C3%A9dition%20du%20meetup%20Paris%20Data%20Ladies%20%21&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fsynthese-de-la-7eme-edition-du-meetup-paris-data-ladies%2F "Twitter") [ ](https://www.quantmetry.com/blog/synthese-de-la-7eme-edition-du-meetup-paris-data-ladies/ "Email") [ ](https://www.quantmetry.com/blog/synthese-de-la-7eme-edition-du-meetup-paris-data-ladies/ "Copy Link")

* * *

Temps de lecture : 4 minutes 

![Quantmetry.com : Synthèse de la 7ème édition du meetup Paris Data Ladies !](https://quantmetry.b-cdn.net/wp-content/uploads/2018/06/pdl7.png)

La 7ème édition du meetup  Paris Data Ladies  a eu lieu le 6 juin dernier, dans les locaux de Xebia. La vocation du meetup est avant tout de donner la parole aux femmes du monde de la data. Cela a bien été encore le cas mercredi soir dernier, avec au programme, 3 intervenantes provenant d’univers variés ! 

Nous vous livrons ici la synthèse de ces talks ! 

####  **Talk n°1 – Opening the black box : Model interpretability**

Manar Toumi  travaille dans la Fintech chez  Bleckwen  autour des sujets de prédiction de la fraude. Elle a abordé, pour nous, la notion d’interprétabilité des algorithmes et de comment pouvait-on faire en sorte d’expliquer leur prise de décision afin d’éviter un modèle black box où une déviance pourrait potentiellement se développer sans que l’on s’en rende compte (une approche sexiste dans le traitement des CV par exemple) … 

A titre d’exemple, un modèle linéaire se décrit très bien via les signes de chacun de ses coefficients de pondération afin de comprendre comment une feature influe sur la sortie. Une illustration simplifiée peut être prise dans le cas du scoring d’un demandeur de prêt : un patrimoine financier initial élevé aura une contribution « positive » sur la probabilité que la personne puisse rembourser son prêt, tandis qu’un montant de prêt très élevé aura tendance à diminuer la probabilité, d’où une contribution « négative ». 

C’est donc dans cet optique que Marco Tuilo Ribeiro a développé et publié en 2016 une librairie python nommé LIME (Local Interpretable Model-Agnostic Explanation). L’approche est dite locale car on étudie ici la décision prise au sein du voisinage de l’instance prédite en opposition à une approche dite globale où l’on chercherait à comprendre le comportement général de l’algorithme. Il reste cependant encore des améliorations à apporter à cette méthode car il existe une certaine instabilité en sortie de l’algorithme. En effet, selon la méthode de discrétisation adoptée, le signe d’un coefficient peut varier et donc fausser son interprétation. Il se pose donc la question essentielle de la qualité de l’approximation du modèle étudié par le modèle LIME. La communauté scientifique contribue à l’amélioration continue de la méthode et une implémentation de la démarche sur un plan global (SP-LIME) est encore attendue. 

####  **Talk n°2 – Exploration de données en Scala**

Aurore de Amaral  , ingénieure Scala chez  Xebia  , a réalisé une présentation technique autour de la méthodologie d’exploration d’un dataset grâce au langage Scala et au framework Spark. Son exposé adressait les différentes étapes de chargement d’un dataset, de transformation/formatage des données, d’extraction des features d’intérêt, puis de visualisation des données. Une présentation résolument technique et illustrée d’exemples de code concrets afin de comprendre les concepts principaux d’utilisation d’une dataframe Spark. 

####  **Talk n°3 – La question du churn chez Canal**

Delphine Gras  n’a jamais rencontré Vincent Bolloré en tant que Data Scientist chez Canal + mais cela ne l’a pas empêché de nous raconter une histoire intéressante : celle de la gestion du churn. Le churn (ou attrition dans la langue de Molière), correspond au phénomène des clients qui résilient leur abonnement avant la date d’échéance. 

L’enjeu pour la chaîne est donc de minimiser cette perte de clients en mettant en place des actions avant que le client ne décide d’envoyer sa demande de résiliation. Pour cela, un score dit de fragilité a été mis en place afin de prédire la probabilité de résiliation d’un client. Cependant ces modélisations n’ont pas suffi en 2017 pour endiguer le désabonnement des clients. C’est pourquoi les équipes marketing ont décidé de refondre les offres Canal + (bouquet TV, mensualités, durées d’engagement …) 

Ces changements pourraient sembler anodins en première approche concernant l’activité de prévision du churn. Delphine nous a alors expliqué les conséquences lourdes concernant son activité car de nombreux biais statistiques ont été introduits à cause de cette refonte. En effet, la première conséquence était qu’il n’y avait plus d’historique clients sur lequel se baser pour modéliser une nouvelle offre dont les paramètres mêmes ont changé. Le prix n’est plus le même, le type de consommation de contenu non plus, les durées d’engagement se sont mises à osciller entre 1 et 2 ans, les contrats ont été unifiés, etc… Les équipes ont donc dû recréer des bases d’apprentissage en simulant notamment des demandes de résiliation virtuelles et en adoptant des hypothèses fortes, par exemple le biais autour du changement de tarif a été simplement ignoré car chaque nouveau client faisait face au même changement de tarification. Les populations étudiées ont été redéfinies afin d’isoler spécifiquement les clients avec une durée d’échéance inférieure à un an pour apprendre sur eux. De même les clients dit « récidivistes » sont exclus à cause d’un comportement opportuniste où ils menacent de se désabonner pour profiter d’offres préférentielles. Il a en effet fallu adopter une vision « à l’abonné » et non plus contrat. 

En conclusion de sa présentation, Delphine a joué la carte de la transparence en évoquant les problèmes qu’elle avait intentionnellement omis dans sa présentation. Ainsi, les abonnés sans engagements ne sont pas pris en compte dans la gestion du churn, tout comme le phénomène d’ « effet réveil » où un client « fragile » appelé par la relation client pour le convaincre de renouveler son abonnement répond au contraire « Merci pour votre appel, j’ai besoin d’aide pour résilier ». La prise en compte de ce genre de critères dans le modèle de scoring est aujourd’hui en cours de réalisation et non encore implémentée par les équipes. 

Rédigé par Jehan Augustin-Latour, Data Consultant chez Quantmetry 
