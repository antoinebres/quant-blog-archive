# covid-19-gafam-backtracking
Wayback Machine URL: https://web.archive.org/web/20230602173734/https://www.quantmetry.com/blog/covid-19-gafam-backtracking/
Archive date: 2023-06-02

Recherche et développement 

16/04/2020 

#  Covid-19 : les GAFAM entrent en scène… pour augmenter le taux d’adoption du backtracking ? Partie 3 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fcovid-19-gafam-backtracking%2F&title=Covid-19%20%3A%20les%20GAFAM%20entrent%20en%20sc%C3%A8ne%E2%80%A6%20pour%20augmenter%20le%20taux%20d%E2%80%99adoption%20du%20backtracking%20%3F%20Partie%203 "Linkedin") [ ](http://twitter.com/intent/tweet?text=Covid-19%20%3A%20les%20GAFAM%20entrent%20en%20sc%C3%A8ne%E2%80%A6%20pour%20augmenter%20le%20taux%20d%E2%80%99adoption%20du%20backtracking%20%3F%20Partie%203&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fcovid-19-gafam-backtracking%2F "Twitter") [ ](https://www.quantmetry.com/blog/covid-19-gafam-backtracking/ "Email") [ ](https://www.quantmetry.com/blog/covid-19-gafam-backtracking/ "Copy Link")

* * *

Temps de lecture : 6 minutes 

![Quantmetry.com : Covid-19 : les GAFAM entrent en scène… pour augmenter le taux d’adoption du backtracking ? Partie 3](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/article-sho-min.png)

✍ [ Issam Ibnouhsein ](https://www.linkedin.com/in/issam-ibnouhsein-ph-d-80364919/) et [ Aleksander Dabrowski ](https://www.linkedin.com/in/aleksanderdabrowski/) / Temps de lecture : 9 minutes. 

_La crise sanitaire Covid-19, qui a d’abord éclaté en Chine, avant de se répandre un peu partout dans le monde, pose de manière aigüe une question fondamentale : doit-on utiliser tous les moyens technologiques à notre disposition pour tenter de stopper l’épidémie ? Une « bonne surveillance » des populations est-elle possible voire légitime ?_ __

_Cet article est le troisième d’une série sur l’exploitation des données personnelles pour la lutte contre l’épidémie Covid-19, qui vise à apporter_ _un éclairage aussi divers que possible sur cette question._

Nous évoquions la semaine dernière le peu d’écho qu’avaient les GAFAM dans les médias suite à l’éclatement de la crise du Covid-19. Depuis, Google et Apple ont annoncé une collaboration inédite : ils travaillent à la construction d’un socle technique commun aux appareils Android et iOS facilitant la construction de solutions de _backtracking_ . À quoi correspond précisément ce socle technique, et quelles garanties avons-nous, en tant que citoyens, autour de ce système ? C’est à ces questions que nous allons tenter de répondre dans cet article. 

Commençons par la nature de ce qui est développé. Contrairement aux initiatives récentes dans différents pays, les deux géants du numérique proposent non pas une application, mais un système intégré dans les couches les plus profondes (dites de bas niveau) de nos smartphones, à savoir leurs systèmes d’exploitation. Il consiste pour l’essentiel en des fonctionnalités de traçage des contacts basés sur la technologie Bluetooth. Leur caractère commun aux plateformes Android et iOS devrait faciliter le développement de solutions de _backtracking_ parfaitement interopérables, et la mise à disposition des fonctionnalités via une mise à jour des systèmes d’exploitation courant Mai pourrait améliorer le taux de pénétration de ces applications dans la population, estimé à seulement 12% à Singapour, alors même qu’il s’agit de l’expérience la plus aboutie en la matière. 

Le système proposé par Google et Apple se veut décentralisé et respectueux de la vie privé, chaque utilisateur devant consentir à l’activation du système de traçage sur son smartphone. Une fois le consentement obtenu, se met alors en place un système d’identification à trois étages : un ID unique, à partir duquel on peut déduire par calcul différents ID quotidiens spécifiques à cet ID unique-là, et ensuite des ID de proximité d’une durée de vie de 15 minutes. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/article-iib-ada-min-476x500.png)

Schéma des ID extrait du livre blanc publié par Google et Apple 

Ces calculs sont basés sur des techniques de cryptographie détaillées dans le livre blanc que Google et Apple ont publié (voir [ ici ](https://www.apple.com/covid19/contacttracing/) ). Le calcul descendant est déterministe, tandis qu’il est impossible de remonter à l’ID unique depuis un ID quotidien ou de proximité. Les utilisateurs s’échangent leurs ID de proximité dès qu’ils sont à une distance de quelques mètres l’un de l’autre. Ces ID sont alors stockés localement sur leurs smartphones et ne sont pas destinés à être communiqués. 

Lorsqu’un utilisateur est testé positif au coronavirus, il peut consentir à remonter à un serveur central ses ID quotidiens des 14 derniers jours. Aucune autre information n’est récupérée, ce qui limite les atteintes à la vie privée. Les ID de ce serveur central (normalement tous liés à des individus testés positifs), sont téléchargés à échéance régulière par les smartphones de tous les utilisateurs. Chaque smartphone opère alors une transformation cryptographique sur les ID quotidiens récupérés pour en déduire des ID de proximité, et une comparaison de ces derniers avec ceux stockés en local permet de générer une alerte en cas de risque avéré de contamination. Il n’existe donc aucun fichier central des croisements entre individus, d’où la nature décentralisée du système. 

Que penser de cette initiative de Google et Apple ? 

Soyons clairs : elle va dans le bon sens, car elle facilitera le déploiement de solutions aidant à un déconfinement maîtrisé des citoyens dans les semaines à venir. Mais plusieurs éléments méritent à notre avis d’être soulignés. 

Tout d’abord, notons qu’il s’agit là de fonctionnalités qui seront mises à disposition via les systèmes d’exploitation iOS et Android, et il faudra des applications pour les exécuter et afficher les informations et notifications de manière ergonomique. Il n’est pas clair pour l’heure si Apple et Google souhaitent développer une telle application, ou s’ils laisseront aux pays et organisations de santé le soin d’en proposer. Un rapprochement est donc toujours possible avec les initiatives type StopCovid en France ou la solution à l’étude au niveau européen (voir [ ici ](https://github.com/DP-3T/documents/blob/master/DP3T%20White%20Paper.pdf) ), dont les délais de développement ne sont pas encore connus. Il faudra aussi être vigilants à ce que les critères d’évaluation du risque restent à la main des Etats : est-il souhaitable que ce soit Google ou Apple qui décident d’une distance de sécurité de 2m au lieu de 1m ? 

Ensuite, on constate que le consentement des utilisateurs intervient à deux moments : lors de l’activation du système de traçage, et lors de la remontée à un serveur central des ID quotidiens suite à un test positif. L’efficacité du système a donc comme pré-requis une adoption massive par les citoyens et des campagnes de tests suffisantes. Or aucun de ces deux pré-requis ne semble garanti pour les premières vagues de déconfinement. En particulier, tous les individus ne sont pas nécessairement équipés de smartphones adaptés, notamment parmi les populations âgées, qui sont aussi les plus à risque. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/article-iib-ada-2-min-500x323.png)

Taux d’équipement en smartphone par tranche d’âge en France en 2019 

Enfin, des risques d’erreur, voire de dérive, existent. Ainsi, une personne confinée chez elle mais dont la portée Bluetooth atteint des voisins libres de leurs mouvements peut fausser le suivi. Idem si la batterie du smartphone d’une personne infectée mais non encore diagnostiquée se vide. On peut même imaginer qu’un groupe d’individus malintentionnés puisse faire dérailler la stratégie de déconfinement en se déclarant positif au coronavirus après avoir maximisé les contacts les jours précédents. Cela rappelle, dans un registre il est vrai plus amusant, la congestion apparue sur Google Maps il y a quelques mois à cause d’un individu qui baladait une centaine de smartphones dans une brouette. ![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/gif_simon_weckert-1.gif) Quant au risque de dérive, il est fortement dépendant de la durée de mise à disposition de ces fonctionnalités dans les systèmes d’exploitation des smartphones. En effet, ces dernières peuvent servir à diffuser des messages publicitaires mieux ciblés en fonction des boutiques que l’on a visitées, ou encore créer une cartographie de nos points de contacts si des applications récupèrent sans consentement les ID de proximité pour les envoyer sur un serveur central. Il convient donc clairement de limiter dans le temps ce _backtracking_ Bluetooth si l’on veut éviter des scandales encore plus importants autour de la vie privée dans les années à venir. 

Comme toute solution technologique pour lutter contre la pandémie Covid-19, le système proposé par Google et Apple ne peut donc porter ses fruits qu’une fois inséré dans une stratégie plus globale des autorités locales de chaque pays, stratégie qui se doit de penser l’après-épidémie dans son recours à des outils techniques. Des discussions sont en cours entre divers Etats et ces deux géants, avec un enjeu majeur de souveraineté sanitaire et numérique à la clef. Les lignes continuent donc de bouger sur le thème de l’exploitation des données personnelles, et nous devons être collectivement attentifs au futur qui se dessine, dans l’urgence, sous nos yeux. 

#####  ✍ [ Issam Ibnouhsein ](https://www.linkedin.com/in/issam-ibnouhsein-ph-d-80364919/) et [ Aleksander Dabrowski ](https://www.linkedin.com/in/aleksanderdabrowski/)
