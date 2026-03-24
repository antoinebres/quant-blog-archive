# blockchain-backtracking
Wayback Machine URL: https://web.archive.org/web/20230602191527/https://www.quantmetry.com/blog/blockchain-backtracking/
Archive date: 2023-06-02

Recherche et développement 

30/04/2020 

#  Covid-19 : Quel rôle pour la décentralisation dans la lutte contre le coronavirus ? 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fblockchain-backtracking%2F&title=Covid-19%20%3A%20Quel%20r%C3%B4le%20pour%20la%20d%C3%A9centralisation%20dans%20la%20lutte%20contre%20le%20coronavirus%20%3F "Linkedin") [ ](http://twitter.com/intent/tweet?text=Covid-19%20%3A%20Quel%20r%C3%B4le%20pour%20la%20d%C3%A9centralisation%20dans%20la%20lutte%20contre%20le%20coronavirus%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fblockchain-backtracking%2F "Twitter") [ ](https://www.quantmetry.com/blog/blockchain-backtracking/ "Email") [ ](https://www.quantmetry.com/blog/blockchain-backtracking/ "Copy Link")

* * *

Temps de lecture : 5 minutes 

![Quantmetry.com : Covid-19 : Quel rôle pour la décentralisation dans la lutte contre le coronavirus ?](https://quantmetry.b-cdn.net/wp-content/uploads/2020/06/covid-19.jpg)

✍ [ Issam Ibnouhsein ](https://www.linkedin.com/in/issam-ibnouhsein-ph-d-80364919/) et [ Aleksander Dabrowski ](https://www.linkedin.com/in/aleksanderdabrowski/) / Temps de lecture : 4 minutes. 

_La crise sanitaire Covid-19, qui a d’abord éclaté en Chine, avant de se répandre un peu partout dans le monde, pose de manière aigüe une question fondamentale : doit-on utiliser tous les moyens technologiques à notre disposition pour tenter de stopper l’épidémie ? Une « bonne surveillance » des populations est-elle possible voire légitime ?_ _Cet article est le quatrième d’une série sur l’exploitation des données personnelles pour la lutte contre l’épidémie Covid-19, qui vise à apporter_ _un éclairage aussi divers que possible sur cette question._

Le _contact-tracing_ via Bluetooth, évoqué dans nos derniers articles de la série, consiste en un suivi des interactions entre individus par échange de codes éphémères via leurs smartphones. Rappelons brièvement comment fonctionne le protocole proposé par Google et Apple, qui représente une implémentation possible : 

  * Les codes éphémères communiqués à un utilisateur via Bluetooth sont stockés en local sur son smartphone et ne sont pas communiqués à des tiers. 
  * Une base de données centrale communique à tous les smartphones des utilisateurs les codes éphémères émis par des personnes testées positives. 
  * Par comparaison entre codes reçus et codes éphémères stockés en local, le système prévient l’utilisateur en cas de proximité avec une personne à risque durant les 14 derniers jours. 



On ne suit donc pas la géolocalisation des individus mais simplement les contacts récents des patients atteints. Par ailleurs, il s’agit d’un système décentralisé car les interactions individuelles ne sont connues de personne : il n’existe pas de base de données centrale récapitulant celles-ci, y compris pour les patients atteints du coronavirus. 

L’application StopCovid proposée par le gouvernement français, pour partie similaire au protocole proposé par Google et Apple, viserait quant à elle à construire une base de données centrale des contacts des personnes contaminées au coronavirus, sous contrôle des autorités sanitaires compétentes. Le premier ministre Edouard Philippe a déclaré mardi dernier lors de son discours à l’Assemblée Nationale que l’application était toujours en cours de développement, et qu’une fois prête, un débat serait organisé à l’Assemblée sur son utilisation. 

![Backtracking Stopcovid Quantmetry](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/bt1-min-500x289.png)

Illustration simplifiée du fonctionnement proposé par l’application StopCovid 

Le fonctionnement centralisé proposé par StopCovid, plus intrusif, représente un frein pour beaucoup de défenseurs du **respect de la vie privée.** Par ailleurs, des difficultés techniques subsistent au vu des restrictions d’accès au Bluetooth opérées par iOS et Android pour les applications qui tournent en arrière-plan… On ne connait donc toujours pas à date si et quand cette application va voir le jour, alors même que le déconfinement progressif de la population française devrait démarrer sous deux semaines. 

La méfiance vis-à-vis d’une centralisation par l’État des données de contacts entre individus, tout comme celle entourant les intentions réelles de Google et Apple suite à leur initiative commune, nous amène à nous interroger : est-il envisageable qu’un acteur moins massif et centralisé qu’un État ou une multinationale soit à l’initiative ? 

La réponse est positive : des organisations décentralisées basées sur la **blockchain** pourraient en théorie proposer des solutions pertinentes pour lutter contre la pandémie Covid-19. Cette technologie, au cœur du protocole **Bitcoin,** cherche à décentraliser la confiance : plus besoin d’un tiers comme une banque pour vérifier que je n’utilise pas le même Bitcoin (numéro 237 par exemple) dans deux transactions différentes. Dans la blockchain, c’est l’organisation même des données, décentralisée, qui sert de rempart face à la falsification, jouant ainsi le même rôle que les mécanismes de contrôle et de certification des banques. Les échanges peuvent être généralisés à toute forme de promesse de valeur entre parties : ce sont les fameux _smart contracts_ . 

![Backtracking blockchain Quantmetry](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/bt2-min-500x271.png)

Illustration simplifiée du fonctionnement décentralisé de la blockchain 

Premier cas d’application : la **blockchain** peut servir de **base de données décentralisée** infalsifiable où seraient stockés les codes éphémères générés par les personnes testées positives au coronavirus dans le cadre du protocole Bluetooth de _contact-tracing_ . Il n’y aurait donc aucune vision centrale des contacts entre individus, ni contrôle par un tiers des données de tests : c’est un système totalement décentralisé de _contact-tracing_ . Un premier pas en ce sens est porté par le collectif Block Covid, qui souhaite mettre à disposition des États, collectivités et organismes publics une solution blockchain privée permettant de stocker de manière décentralisée et anonyme les données de tests de dépistage. Une base de données décentralisée fonctionnant sur le même principe et rendue publique pourrait servir à recueillir les codes éphémères générés par les smartphones des individus testés positifs. 

On pourrait envisager dans un second temps des _smart contracts_ mis à disposition de centres de recherche pour permettre la collecte des données nécessaires à leurs études. La structure-type d’un _smart contract_ contiendrait par exemple une clause de consentement de participation à différents types d’études, ainsi que les données nécessaires à chaque étude. Les utilisateurs pourraient contrôler de manière fine les études auxquelles ils souhaitent participer, ainsi que les données qu’ils acceptent de mettre à disposition (coordonnées GPS, codes éphémères locaux issus du _contact-tracing_ , etc.). Les transactions d’informations cryptées seraient alors réalisées automatiquement par la blockchain en respectant nativement les clauses des _smart contracts_ : du _privacy-by-design_ par décentralisation. Cela représenterait un grand pas en avant car les scientifiques peinent aujourd’hui à collecter les données utiles à la compréhension du mode de propagation de l’épidémie. Ce cas d’application n’est pas nouveau, et a déjà été discuté de nombreuses fois entre acteurs de la technologie blockchain et du monde de la santé  [1]  . Pour l’heure, il existe assez peu d’initiatives matures en ce sens, preuve qu’il reste beaucoup de chemin à parcourir avant que la blockchain ne déploie son plein potentiel. 

[1]  https://healthcaredatainstitute.com/wp-content/uploads/2015/02/livre-blanc-hdi-2017-web.pdf 

![Backtracking smart contract Quantmetry](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/bt3-min-500x204.png)

Illustration simplifiée du fonctionnement d’un smart-contract qui contrôle l’accès aux données. 

Concluons ce billet en insistant une nouvelle fois, si tant est que cela soit nécessaire, qu’aucun _solutionnisme_ technologique ne viendra à bout de l’épidémie de Covid-19. _Back-tracking_ , _contact-tracing ou_ blockchain : quel que soit l’outil utilisé, l’information la plus importante reste celle fournie par les **tests biologiques.** Une politique organisée de collecte de ces données est la seule voie d’accès à l’après Covid-19. 

#####  ✍ [ Issam Ibnouhsein ](https://www.linkedin.com/in/issam-ibnouhsein-ph-d-80364919/) et [ Aleksander Dabrowski ](https://www.linkedin.com/in/aleksanderdabrowski/)
