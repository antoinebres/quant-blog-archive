# hackathon-ai-labs-une-idee-claire-pour-un-objectif-a-la-portee
Wayback Machine URL: https://web.archive.org/web/20230129145219/https://www.quantmetry.com/blog/hackathon-ai-labs-une-idee-claire-pour-un-objectif-a-la-portee/
Archive date: 2023-01-29

Uncategorized 

01/09/2017 

#  Hackathon AI Labs : une idée claire pour un objectif à la portée ! 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fhackathon-ai-labs-une-idee-claire-pour-un-objectif-a-la-portee%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Hackathon%20AI%20Labs%20%3A%20une%20id%C3%A9e%20claire%20pour%20un%20objectif%20%C3%A0%20la%20port%C3%A9e%20%21&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fhackathon-ai-labs-une-idee-claire-pour-un-objectif-a-la-portee%2F "Twitter")

* * *

Temps de lecture : 6 minutes 

![Quantmetry.com : Hackathon AI Labs : une idée claire pour un objectif à la portée !](https://quantmetry.b-cdn.net/wp-content/uploads/2017/09/picture1.png)

##  Introduction : Quand on n’y connait rien en art … 

En expédition culturelle au musée d’Orsay, vous vous retrouvez devant ce tableau. 

Il vous interpelle. L’effet est saisissant : qui sont ces hommes dans cette longue caravane qui semble tout droit se diriger vers le spectateur ? Où vont-ils en réalité ? Qui a peint ce tableau ? A quelle époque ? Que voulait-il représenter ? … 

Sous ce déluge de questions, vous commencez à regretter de ne pas avoir dépensé 10€ pour obtenir l’audioguide du musée. Mais rapidement vous vous ravisez : ces audio-guides sont souvent très incomplets (ils ne décrivent qu’une petite fraction des oeuvres dans les grands musée). De surcroît, la qualité des commentaires laisse souvent à désirer. 

Vous cherchez alors des yeux le petit encart informatif qui jouxte parfois les tableaux sur le mur. Pas de chance ! Sur celui-ci il n’y en a pas. De toutes façons, sur la plupart des oeuvres, ils seront disponibles, mais ne vous donneront guère plus d’information que le nom du tableau et de son auteur. 

Catastrophe. Votre curiosité insatiable se heurte à un mur, et vos espoirs de vous cultiver s’évanouissent dans la violence de ce choc… 

C’est dans cette situation qu’on aimerait bien être accompagné par notre ami amateur d’art. Celui qui sait tout sur tout et qui connaît / reconnaît tous les tableaux : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Picture2.png)

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Picture3.png)

Dans cette situation, il est là pour vous éclairer. Il vous explique que le tableau que vous admirez s’intitule “Pèlerins allant à la Mecque”, et qu’il a été peint par Léon Belly. Il vous informe également que celui-ci a remporté une médaille de première classe au (fameux) salon de 1861 avant de vous détailler la controverse qui s’en est suivie. Il va même jusqu’à vous guider vers un autre tableau du musée, dont il dit qu’il ressemble aux Pèlerins de Belly et dont il est certain qu’il devrait vous plaire… 

Ah ! Ce qu’il est sympa et cultivé votre ami !… 

Le problème, c’est que vous n’avez pas d’ami comme ça. Le problème, c’est que souvent, nos amis dans la vraie vie sont plutôt comme ca : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Picture4.png)

Fort du constat que nous ne pouvons pas toujours compter sur nos amis, nous avons décidé de les remplacer par la technologie. C’est ainsi qu’une équipe de 4 personnes de Quantmetry a décidé de créer, le temps du hackathon AI Labs, l’ébauche de “Marty”, une intelligence artificielle de poche, experte en art, capable d’accompagner n’importe qui dans ses pérégrinations dans les musées et les expositions. 

**Cette série d’articles est un retour d’expérience sur cette épopée de 50h au cours de laquelle est né un premier prototype de Marty. Dans ce premier volet, vous allez découvrir les étapes préliminaires nécessaires afin de pouvoir bien mener un mini-projet de bout en bout au cours d’un Hackathon. Dans le deuxième, nous vous raconterons les bonnes habitudes à garder à l’esprit pendant l’événement pour ne pas perdre le nord. En nous suivant jusqu’au troisième, vous en saurez davantage sur les aspects techniques de notre projet. Bonne lecture !**

##  Le hackathon AI Labs : quésako ? 

Le hackathon auquel nous avons participé, “AI Labs”, est un événement annuel organisé par [ France is AI ](https://franceisai.com/) , dont l’objectif est de donner naissance en un week-end, à des nouvelles applications basées sur l’intelligence artificielle. 

La recette est simple : 

  * vous réunissez dans une même salle des data scientists, des développeurs, des UX designers, des business developers, … tous unis par une même passion pour l’intelligence artificielle 

  * Certains des participants pitchent leur idée d’application / start-ups pendant 1 min 

  * Un vote est organisé pour sélectionner les meilleurs projets parmis ceux pitchés 

  * Les 12 meilleurs projets sont sélectionnés 

  * Des équipes de 7-8 personnes se forment spontanément autour des différents projets et ont 48h pour développer un business plan et un prototype d’application. 

  * A la fin du week-end les équipes présentent leur travail à un jury composé d’experts qui récompense les 3 meilleurs projets 




Dans la suite de cet article, nous allons vous détailler notre expérience au cours de ce hackathon. Nous présentons les grandes étapes du déroulement du hackathon ainsi que les leçons que nous avons tirées (ce qu’il faut faire… ou ne pas faire !) 

##  Petit guide pour le futur hackathonien : les étapes préliminaires au projet 

###  Trouver le sujet parfait 

Avant de développer l’idée géniale d’une application de reconnaissance et recommandation d’art, il faut d’abord… l’identifier… et cette étape a finalement été beaucoup plus laborieuse que prévue. En effet, le sujet parfait, qui soit à la fois capable de motiver suffisamment une équipe pour passer l’intégralité de son week-end à coder et susceptible de remporter les faveurs du jury, n’est pas si simple à trouver. En effet, il doit respecter un certain nombre de contraintes : 

  * Répondre à un vrai besoin 

  * Contenir une bonne dose d’AI (Machine Learning et/ou Data Science) 

  * Être fun (à la fois dans le principe de l’application et dans les technos à mettre en place) 

  * Être prototypable en un week-end (nous partions d’une feuille blanche) 




C’est en respectant ces 4 axes que nous avons finalement, après plusieurs heures de brainstorming passionnées et houleuses, trouvé le sujet de Marty : 

  1. Répondre à un vrai besoin 

     * Aucune application de ce type n’existe (ou en tout cas n’est démocratisée et réellement utilisée) aujourd’hui en France 

  2. Contenir une bonne dose d’AI 

     * Analyse et reconnaissance automatique d’images 

     * Moteur de recommandation basé sur l’expérience utilisateur 

  3. Être fun 

     * Méthodes de matching d’images novatrices 

     * Création d’une application portable 

  4. Être prototypable en un week-end 

     * Identification d’une base de données d’images libres d’exploitation 

     * Des notions d’analyse d’images dans l’équipe 

     * Des notions de moteur de recommandation… 




###  Le lancement du Hackathon avec les one-minute pitches – vendre son idée de projet pour le faire vivre et renforcer l’équipe ! 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Picture5.png)

Une fois l’idée trouvée et l’équipe sécurisée, il faut encore passer l’épreuve des one-minute pitches pour voir son projet validé. Cette étape est cruciale car sans validation le projet passe à la trappe et l’équipe doit se ventiler sur d’autres projets qualifiés. 

Cela se fait en deux pitchs : 

  * **Un premier pitch** qui a pour but de récolter suffisamment de votes pour passer un premier filtre de sélection. Ce pitch doit pouvoir en quelques mots : 



  1. Expliquer la problématique ciblée 

  2. Clarifier les objectifs à atteindre lors du hackathon 

  3. Si possible, donner quelques éléments pour démontrer qu’ils sont atteignables 

  4. Démontrer que travailler sur le sujet vaut la peine de sacrifier un week-end. 




![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Picture6.png)

Grand succès et beaucoup de votes pour Marty lors du premier pitch 

  * **Un deuxième pitch** (si le premier est passé) qui a pour but de recruter de nouveaux membres pour consolider / rééquilibrer l’équipe. En effet pour remporter un hackathon IA Labs, le projet doit être solide sur plusieurs axes, tels que : 



  1. Sa proposition de valeur ajoutée : répond-il à besoin identifié ? 

  2. Son business plan : est-il possible de lancer une startup avec ce projet ? 

  3. Sa réalisation technique : quelle part d’IA ou de “Hack” 




L’équipe initiale de Marty était constituée quasi-exclusivement de développeurs : quatre data scientists / développeurs back-end et un chef de projet. Grâce au talent du pitcher, nous réussissons à recruter les trois meilleurs profils de tout le hackathon : un chef de projet/business developer ainsi que deux développeurs front-end. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Picture7.png)

L’équipe Marty au grand complet 

Est-ce que cette équipe suffira pour un objectif si ambitieux ? Comment gérer au mieux les énergies au cours des 50h ? Arriverons-nous à convaincre le jury de la valeur scientifique et business de notre prototype ? Rendez-vous au prochain article de cette série pour en savoir plus ! 
