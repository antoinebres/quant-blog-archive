---
layout: post
title: synthese-de-la-6eme-edition-du-meetup-paris-data-ladies
date: 2023-06-02
url_wayback_machine: https://web.archive.org/web/20230602173250/https://www.quantmetry.com/blog/synthese-de-la-6eme-edition-du-meetup-paris-data-ladies/
---
Uncategorized 

03/05/2018 

#  Synthèse de la 6ème édition du meetup Paris Data Ladies ! 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fsynthese-de-la-6eme-edition-du-meetup-paris-data-ladies%2F&title=Synth%C3%A8se%20de%20la%206%C3%A8me%20%C3%A9dition%20du%20meetup%20Paris%20Data%20Ladies%20%21 "Linkedin") [ ](http://twitter.com/intent/tweet?text=Synth%C3%A8se%20de%20la%206%C3%A8me%20%C3%A9dition%20du%20meetup%20Paris%20Data%20Ladies%20%21&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fsynthese-de-la-6eme-edition-du-meetup-paris-data-ladies%2F "Twitter") [ ](https://www.quantmetry.com/blog/synthese-de-la-6eme-edition-du-meetup-paris-data-ladies/ "Email") [ ](https://www.quantmetry.com/blog/synthese-de-la-6eme-edition-du-meetup-paris-data-ladies/ "Copy Link")

* * *

Temps de lecture : 4 minutes 

![Quantmetry.com : Synthèse de la 6ème édition du meetup Paris Data Ladies !](https://quantmetry.b-cdn.net/wp-content/uploads/2018/05/sans-titre.png)

####  Introduction 

La 6ème édition du meetup Paris Data Ladies a eu lieu le 25 avril dernier, dans les locaux de Deezer. La vocation du meetup est avant tout de donner la parole aux femmes du monde de la data. Cela a bien été le cas mercredi soir dernier, avec au programme 4 intervenantes provenant d’univers variés ! 

Nous vous livrons ici la synthèse de ces talks, ainsi que les [ supports utilisés ](https://www.slideshare.net/JustineDeshais/paris-data-ladies-6) . 

####  Talk n°1 – Real time application scaling 

[ Huikan Xiang ](https://www.linkedin.com/in/huikanxiang/) est Data engineer dans l’équipe Core Data de Deezer. Elle nous a présenté la stack utilisée par Deezer : il s’agit d’une stack Hadoop on premise comme back-end des services musicaux qu’ils fournissent. Elle est utilisée pour recommander de la musique aux utilisateurs, pour le reporting, comme moteur de paiement des royalties et comme CRM pour la gestion de la relation et des informations clients. 

Ces services ont besoin d’être fournis quasiment en temps réel. (Après avoir écouter trois morceaux de musique classique, les utilisateurs s’attendent à ce que Deezer suggère du Mozart plutôt que Despacito). 

En surcouche de la stack Hadoop, Deezer utilise donc Kafka et Spark Streaming pour effectuer ces traitements. 

Huikan Xiang a conclu sa présentation par un hands-on permettant de streamer un traitement de message Twitter en filtrant sur le hashtag #parisDataLadies ! Le code utilisé lors de sa démo est disponible [ ici. ](https://github.com/Huikan/datalady-demo)

####  Talk n°2 – Modélisation des retards de trains pour l’exploitation des grandes gares 

[ Marie de Faverges ](https://www.linkedin.com/in/marie-de-faverges-b4ba4598/) nous a présenté sa thèse CNAM/SNCF Réseau. L’objectif de ses travaux est de quantifier le risque de retards de trains quelques jours en avance, de manière à pouvoir adapter les planifications ferroviaires en zone dense. Elle s’intéresse particulièrement au périmètre des gares où le routage des trains et l’affectation de quais est difficile et où les retards se propagent rapidement. L’idée est d’anticiper les conflits en prenant en compte les risques de perturbation. Les données dont elle dispose sont les suivantes : la liste de trains qui arrivent ou partent de la gare et la liste d’itinéraires traversant la gare. Le problème est NP-complet, avec très vite des millions de combinaisons possibles. Ainsi, son étude se restreint à l’estimation du risque de retard en prédisant sa loi et uniquement sur les petits retards (inférieurs à 20 minutes). 

Elle utilise un modèle linéaire généralisé : une loi négative binomiale tronquée au-delà de 20 minutes. Pour valider son modèle, Marie présente 2 méthodes : d’abord la méthode de calibration qui vérifie la correspondance entre les probabilités prédites et les taux observés. Cette méthode peut être mise en oeuvre soit par une approche graphique où chaque groupe de trains doit être au plus près de la droite probabilité prédite / fréquence observée, soit par une approche statistique à l’aide du test de Hosmer-Lemeshow où l’hypothèse nulle ne doit pas être rejetée. Ensuite, elle utilise la méthode de discrimination, qui consiste à évaluer l’aire sous la courbe ROC pour chaque groupe de trains. Son modèle final a été entraîné sur 17 000 arrivées de TGV à Montparnasse et évalué sur un test set de 6 000 retards. Les résultats montrent une bonne calibration et une discrimination stable. 

A terme, les résultats de sa thèse permettront d’améliorer le paramétrage de l’outil de routage des trains en gare, et ce afin de limiter la propagation des retards en gare. 

####  Talk n°3 – Modélisation des couches géologiques par inversion 

[ Sophie Monnier ](https://www.linkedin.com/in/sophie-monnier-83a80629/) nous a présenté sa thèse en géophysique. La géophysique est l’étude des propriétés mécaniques des couches géologiques afin de les délimiter et de les caractériser. Sophie a travaillé sur la cartographie en trois dimensions d’une zone à l’ouest de l’Australie où la croûte océanique passe sous la couche continentale. 

Pour cela, un système d’émission/réception d’onde sismique est utilisé : à un endroit précis, une onde sismique est produite, et des capteurs alignés sur la zone à étudier enregistrent l’arrivée de cette onde. Étant donné que les propriétés mécaniques des roches dépendent de leur type, cette information de vitesse de la propagation des ondes (suivant la fréquence) permet de déduire les limites entre différentes roches et de caractériser les zones de subduction. Pour cela, les données des capteurs sont analysées dans un processus itératif. D’abord on suppose une répartition globale des vitesses de propagation pour un point donné (et donc des couches). Ensuite à partir de cette supposition on prédit les courbes qu’auraient observé les capteurs pour une même explosion. 

La différence permet d’indiquer comment modifier le profil de vitesse en profondeur, afin de mieux coller aux observations des capteurs. Ce processus est répété à la manière d’une descente de gradient en machine learning jusqu’à ce que le profil de vitesse permette de modéliser les enregistrements des capteurs. 

Elle a ainsi permis de mieux comprendre la géologie de cette partie de l’Australie. 

Cette méthode a également permis au Japon de préciser la façon dont la croûte océanique passait sous l’île. 

####  Intervention Femmes et Mathématiques 

L’ [ association Femmes et Mathématiques ](http://www.femmes-et-maths.fr/) , qui existe depuis 1987, est intervenue pour proposer aux participantes de présenter à des jeunes collégiennes et lycéennes les débouchés et métiers scientifiques qu’elles pourraient embrasser. 

Ces évènements, les journées “Filles et maths : une équation lumineuse”, proposent en effet un speed meeting d’1h30 environ, où des jeunes filles de troisième et seconde rencontrent des intervenantes du monde scientifique (astrophysique, data science etc.). Ils ont lieu en Ile-de-France mais aussi dans toute la France. 

Pour se porter volontaire pour une prochaine session, ou héberger dans vos locaux, n’hésitez pas à les contacter par mail à [ cette adresse. ](mailto:fetm@ihp.fr)

####  Conclusion 

La soirée s’est terminée par un cocktail permettant la poursuite des échanges et le networking dans une ambiance chaleureuse. 

Le prochain meetup aura lieu le 6 juin dans les locaux de Xebia, vous pouvez déjà bloquer vos agendas et vous inscrire [ ici. ](https://www.meetup.com/fr-FR/Paris-DataLadies/)
