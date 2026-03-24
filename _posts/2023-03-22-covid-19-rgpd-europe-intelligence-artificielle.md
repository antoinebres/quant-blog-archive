---
layout: post
title: covid-19-rgpd-europe-intelligence-artificielle
date: 2023-03-22
url_wayback_machine: https://web.archive.org/web/20230322213830/https://www.quantmetry.com/blog/covid-19-rgpd-europe-intelligence-artificielle/
---
Recherche et développement 

09/04/2020 

#  Data et Covid-19 : où en est l’Europe ? Quels usages pour l’intelligence artificielle ? Partie 2 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fcovid-19-rgpd-europe-intelligence-artificielle%2F&title=Data%20et%20Covid-19%20%3A%20o%C3%B9%20en%20est%20l%E2%80%99Europe%20%3F%20Quels%20usages%20pour%20l%E2%80%99intelligence%20artificielle%20%3F%20Partie%202 "Linkedin") [ ](http://twitter.com/intent/tweet?text=Data%20et%20Covid-19%20%3A%20o%C3%B9%20en%20est%20l%E2%80%99Europe%20%3F%20Quels%20usages%20pour%20l%E2%80%99intelligence%20artificielle%20%3F%20Partie%202&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fcovid-19-rgpd-europe-intelligence-artificielle%2F "Twitter") [ ](https://www.quantmetry.com/blog/covid-19-rgpd-europe-intelligence-artificielle/ "Email") [ ](https://www.quantmetry.com/blog/covid-19-rgpd-europe-intelligence-artificielle/ "Copy Link")

* * *

Temps de lecture : 4 minutes 

![Quantmetry.com : Data et Covid-19 : où en est l’Europe ? Quels usages pour l’intelligence artificielle ? Partie 2](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/article-vgo-min.png)

✍ [ Issam Ibnouhsein ](https://www.linkedin.com/in/issam-ibnouhsein-ph-d-80364919/) et [ Aleksander Dabrowski ](https://www.linkedin.com/in/aleksanderdabrowski/) / Temps de lecture : 7 minutes. 

_La crise sanitaire Covid-19, qui a d’abord éclaté en Chine, avant de se répandre un peu partout dans le monde, pose de manière aigüe une question fondamentale : doit-on utiliser tous les moyens technologiques à notre disposition pour tenter de stopper l’épidémie ? Une « bonne surveillance » des populations est-elle possible voire légitime ?_

**Cet article est le deuxième d’une série** sur l’exploitation des données personnelles pour la lutte contre l’épidémie Covid-19, qui vise à apporter un éclairage aussi divers que possible sur cette question épineuse. 

À l’heure même où nous écrivons ces lignes, les choses bougent en Europe. Un récent sondage indique que près de 80% des français seraient favorables à l’utilisation d’une application traçant leurs relations sociales et générant des avertissements en cas de proximité avec une personne atteinte par le coronavirus. 

La Pologne travaille de son côté sur une application, **ProteGo** , qui devrait permettre d’identifier plus rapidement les personnes à risque pour les mettre en quarantaine. Il s’agirait de la première exploitation massive par un Etat européen de données personnelles non-anonymisées dans le cadre de la lutte contre le Covid-19. Les développements se veulent respectueux du cadre du RGPD et des droits qu’il octroie aux citoyens en termes d’accès, de correction ou de portabilité des données. L’application fonctionne sur un principe similaire à celui utilisé à Singapour et détaillé dans notre premier article : une interconnexion Bluetooth de faible portée entre smartphones, un stockage local et crypté des données de croisement entre individus, et une transmission des informations pertinentes vers les autorités et les personnes présentant un risque de contamination. 

Dans un souci de transparence, le ministre du numérique polonais a rendu le code public, consultable sur la plateforme [ Github ](https://github.com/ProteGO-app/specs/blob/master/ENGLISH.md) , et ce afin que tout un chacun puisse vérifier la loyauté de l’outil, au sens que les fonctionnalités réelles correspondent bien à celles communiquées. Une application complémentaire, dénommée **Home Quarantine** , dont l’installation a été rendue obligatoire depuis le 1er avril pour les personnes en quarantaine, transmet à un serveur contrôlé par les autorités des selfies géolocalisés, afin de vérifier la proximité des patients avec leur smartphone et leur respect du confinement. Le code n’est pas public pour cette deuxième application, et le stockage ne se fait pas localement, essentiellement pour des raisons de sécurité selon les autorités. 

Malgré quelques zones d’ombre dans l’expérience polonaise, nous avons là un bel exemple d’actualisation du potentiel du RGPD : assez souple quand la situation l’exige, et suscitant autant que faire se peut, la construction de solutions respectueuses de la vie privée. Un projet européen porté par un collectif de chercheurs, se basant sur les mêmes grands principes est en cours de construction (voir [ ici ](https://github.com/DP-3T/documents/blob/master/DP3T%20White%20Paper.pdf) ). Il est probable, voire souhaitable, que ces pistes techniques soient sérieusement explorées par tous les États européens. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/data-covid-19-500x284.png)

Récapitulatif des principales approches data pour lutter contre la pandémie Covid-19 

Qu’en est-il de l’utilisation de l’intelligence artificielle, qu’on associe souvent à l’exploitation massive de données, dans la lutte contre l’épidémie Covid-19 ? Les usages restent pour l’heure limités, même s’il existe quelques initiatives en la matière. Par exemple, le projet **CovidIA** , porté par un groupe de chercheurs français, vise à développer une application d’aide au déconfinement. Avec des hypothèses sur la maladie (contagiosité, incidence, etc.), et en mixant des données de tests sur un échantillon de quelques centaines de milliers de personnes et des données de géolocalisation anonymisées, la promesse est de construire un modèle d’intelligence artificielle établissant une probabilité de contamination pour chaque individu, une sorte de test de dépistage numérique. L’outil serait bien évidemment moins efficace que des tests biologiques réels, mais aurait l’avantage de la rapidité, car au rythme croisière de 500.000 tests par jour (la France en réalise 20.000 aujourd’hui), il faudrait près de 6 mois pour tester toute la population française. Il sera important là encore, si le projet aboutit, d’être totalement transparent sur les critères d’évaluation des risques, pour éviter des situations comme celles vécues par certains citoyens chinois à cause du laisser-passer numérique sous forme de QR-code mis en place par les autorités locales. 

De son côté **DeepMind** , division d’IA avancée chez Google, a mis en libre accès les résultats de son outil de modélisation 3D de proteintes AlphaFold, très utiles pour guider les chercheurs sur la piste d’un vaccin. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/sras-min-500x374.png)

Une modélisation de protéine de SRAS-COv-2 généré par l’outil AlphaFold 

Par ailleurs, Facebook et Youtube travaillent à améliorer leurs algorithmes de détection de _fake news_ par IA faute d’agents humains disponibles, généralement beaucoup plus efficaces que les automates. Ceci est essentiel à la cohésion sociale et à l’efficacité de la gestion gouvernementale de la crise, l’effet délétère des fausses informations et théories complotistes sur la crédibilité de la parole experte n’étant plus à démontrer. De son côté, Microsoft met à disposition un site ergonomique de suivi de l’évolution de la pandémie et a publié un guide de recommandations pour sécuriser les infrastructures informatiques des hôpitaux contre les attaques. 

![Dashboard mis à disposition par Microsoft pour suivre la progression de la maladie](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/dashboard-microsoft-min-500x237.png)

Dashboard mis à disposition par Microsoft pour suivre la progression de la maladie 

Néanmoins, on ne peut qu’être étonnés de la faible place qu’occupent les GAFA dans l’espace médiatique depuis l’éclatement de la crise du Covid-19, et le temps semble bien loin où l’on débattait de leur toute-puissance, que ce soit en mal comme lors du scandale Cambridge Analytica, ou en bien pour les adeptes du solutionnisme technologique – y compris face à la mort. La catastrophe, comme le décrivait si bien Jean-Pierre Dupuy dans son ouvrage _Pour un catastrophisme éclairé_ , est « l’impossible devenu certain », tout comme cette pandémie, à la fois prévisible et inévitable. Les solutions technologiques sont utiles pour alléger le poids des catastrophes, mais la place à nouveau centrale des Etats montre qu’il faut avant tout une communauté politique pour y faire face. 

#####  ✍ [ Issam Ibnouhsein ](https://www.linkedin.com/in/issam-ibnouhsein-ph-d-80364919/) et [ Aleksander Dabrowski ](https://www.linkedin.com/in/aleksanderdabrowski/)
