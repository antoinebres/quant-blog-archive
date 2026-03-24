# chatbot-a-la-demande-avec-les-apis
Wayback Machine URL: https://web.archive.org/web/20230724162220/https://www.quantmetry.com/blog/chatbot-a-la-demande-avec-les-apis/
Archive date: 2023-07-24

NLP 

18/07/2017 

#  Chatbot à la demande avec les APIs 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fchatbot-a-la-demande-avec-les-apis%2F&title=Chatbot%20%C3%A0%20la%20demande%20avec%20les%20APIs "Linkedin") [ ](http://twitter.com/intent/tweet?text=Chatbot%20%C3%A0%20la%20demande%20avec%20les%20APIs&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fchatbot-a-la-demande-avec-les-apis%2F "Twitter") [ ](https://www.quantmetry.com/blog/chatbot-a-la-demande-avec-les-apis/ "Email") [ ](https://www.quantmetry.com/blog/chatbot-a-la-demande-avec-les-apis/ "Copy Link")

* * *

Temps de lecture : 7 minutes 

![Quantmetry.com : Chatbot à la demande avec les APIs](https://quantmetry.b-cdn.net/wp-content/uploads/2017/07/screen-shot-12-30-18-at-10-29-am.jpg)

On désigne par API (application programming interface) un ensemble d’outils permettant à deux applications de s’interfacer et de fonctionner de concert. 

Les APIs connaissent depuis quelques années un regain d’intérêt dans le monde de l’IT. De plus en plus de compagnies proposent des APIs ouvertes au public : citons celles bien connues de Google, Facebook et Twitter. 

Bien que cette idée ne date pas d’hier, son succès actuel s’explique par plusieurs facteurs. Parmi ceux-ci figure l’apparition des smartphones. IHS Markit estime que 6 milliards de ces petits appareils seront en circulation en 2020, soit une croissance de 50% par rapport à 2016. 

Avec la diversité des systèmes d’exploitation dont ces smartphones sont pourvus (Android, iOS, Windows, etc.), de plus en plus de développeurs d’applications mobiles optent pour la stratégie du back-end as a service (BaaS). Cette architecture s’appuie sur le paradigme client-serveur et consiste à positionner le back-end de l’application sur un serveur distant et de ne mettre à disposition du mobile uniquement que le front, les deux étant interfacés au moyen d’une API. 

On peut généraliser le phénomène aux autres objets connectés, avec le développement de la communication inter-machine, où les APIs sont devenues essentielles. De manière plus générale, toutes les grandes tendances innovantes de l’IT (Cloud, Big Data, IoT, etc.) favorisent l’utilisation des APIs et les placent au centre de leurs dispositifs. 

Aujourd’hui, une véritable économie autour des APIs est en train de prendre forme, que d’aucuns nomment le B2D (business to developer). Les fournisseurs d’API permettent à des communautés de développeurs de bâtir de nouvelles applications autour de leurs services et d’étendre leurs possibilités. En mettant ainsi à disposition ces APIs, les fournisseurs bénéficient d’une rente supplémentaire. Les développeurs qui consomment ces services, quant à eux, s’épargnent l’effort de développer des briques compliquées et peuvent les intégrer directement dans leurs solutions. 

##  APIs et data science 

S’agissant de la science des données, les APIs s’avèrent être très utiles, et ceci à plus d’un titre. Elles constituent d’abord un très bon moyen d’enrichir son historique de données. Les APIs simplifient aussi l’architecture générale en permettant plus de modularité entre les sources de données et les modèles d’une part, et entre le modèle et le front-end d’autre part. 

Enfin, les APIs apportent de l’agilité dans le développement et l’industrialisation des modèles de data science. En effet, ces modèles ont généralement leur propre cycle de développement (préparation des données, entraînement du modèle, validation, amélioration, etc.) qui est indépendant de celui du reste de l’environnement applicatif, ils s’intègrent donc mieux dans un projet modulaire. 

##  API REST 

Avec l’augmentation du nombre d’APIs et leur succès croissant, en particulier les APIs publiques, les fournisseurs sont confrontés à de nouvelles problématiques. Tout d’abord, de nombreuses APIs aux fonctions connexes ou identiques adoptent des designs radicalement différents les unes des autres, et il arrive parfois que les plus récentes réinventent la roue. De plus, devant le nombre important et la diversité des clients de ces APIs, il est impératif d’assurer leur scalabilité pour satisfaire toute la demande. Sans compter que beaucoup de ces APIs seront amenées à durer relativement longtemps, elles doivent donc dès l’origine être conçues pour être faciles à maintenir et à faire évoluer. 

Si bien qu’une nécessité de standardisation s’est faite ressentir très tôt. Ceci a donné lieu à l’apparition d’une multitude de philosophies de standards de développement. Une de celles qui ont eu le plus de succès est connue sous l’acronyme REST (representational state transfer) : c’est un modèle d’architecture basé sur le protocole HTTP, qui induit tout un ensemble de règles et de bonnes pratiques. 

##  Tutoriel Flask 

Pour toutes ces raisons, nous avons choisi de mettre en place une API REST dans l’architecture de notre chatbot. Nous avons utilisé pour cela la célèbre librairie Flask de Python. Flask est un framework de développement web qui se veut minimaliste, et qui confère à son utilisateur une liberté de conception, très appréciable pour réaliser une API. Flask repose sur le protocole WSGI (web server gateway interface), qui permet d’interfacer l’application Python (notre API) et le serveur HTTP. 

Notre API a pour fonction de fournir une abstraction du modèle au front-end. On obtient une architecture modulaire dont les trois principales briques constitutives (back-end, API, front-end) peuvent être développées séparément. 

Dans la suite de ce tutoriel, nous admettrons avoir un modèle de chatbot sérialisé prêt à l’emploi au format [ pickle ](ftp://ftp.traduc.org/pub/lgazette/html/2007/143/lg143-C.html) (model.pk). Ce modèle produit une réponse du bot en fonction d’une conversation en entrée (une liste ordonnée des messages à un instant donné). Au risque de me répéter, je vous renvoie vers [ cet ](https://www.quantmetry.com/single-post/2017/05/04/Sous-le-capot-dun-Chatbot-le-cerveau-de-Skynet) article pour plus détails sur la modélisation. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-10.31-AM.jpg)

La première chose à faire est d’instancier une application Flask (app). C’est cette instance qui, grâce à WSGI, va pouvoir traiter les requêtes réceptionnées par le serveur web. 

Nous avons aussi utilisé la base de données MongoDB. Par souci de simplification, une classe DBManager a été créée pour gérer l’interaction avec MongoDB. Sachez toutefois qu’il existe une librairie ( [ Flask-PyMongo ](https://flask-pymongo.readthedocs.io/en/latest/) ) proposant un connecteur entre Flask et MongoDB. 

Nous stockons le modèle sérialisé dans la variable model. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-10.31-AM-001.jpg)

Design 

Avant d’aller plus loin dans le code, il nous faut réfléchir au design de l’API, en respectant au mieux les principes REST. Le paragraphe qui suit est un peu complexe, donc restez concentrés ! 

Le paradigme REST met en œuvre deux concepts fondamentaux que sont les ressources et les représentations. Une ressource désigne tout objet, abstrait ou concret, identifié par un URL qui lui est propre (deux ressources ne peuvent avoir le même URL à moins d’être identiques). On appelle représentation toute description complète ou partielle obtenue après accès à la ressource grâce à l’URL associé. Une ressource peut avoir plusieurs représentations différentes. Une représentation peut aussi servir à mettre à jour une ressource, on parle de changement d’état de la ressource. 

Dans l’optique de notre chatbot, un utilisateur de ce service doit pouvoir réaliser deux actions : mettre à jour l’état d’une conversation (la conversation est créée si elle n’existe pas déjà), et obtenir la dernière réponse du bot. 

Si on transpose ce schéma dans le paradigme REST, on peut alors définir une ressource comme étant une conversation, et une représentation de cette ressource comme étant le dernier message de cette conversation (qui sera théoriquement toujours un message du bot, ce dernier répondant toujours à son interlocuteur). 

Pour ce qui est de l’URL de chaque conversation, il sera tout simplement composé de l’adresse de l’API et d’un identifiant unique, séparés d’un slash. 

A présent, il nous faut un moyen de distinguer les deux actions que l’on souhaite implémenter (mise à jour et obtention de la représentation d’une conversation). L’architecture REST étant basée sur le protocole HTTP, nous allons associer un verbe HTTP à chacune de ces actions. Voici quelques-uns des verbes HTTP les plus communs, ainsi que leur fonction : 

– GET : obtention d’une représentation de la ressource ; 

– POST : sert entre autres à créer une ressource sous-jacente à la ressource ciblée dans la requête ; 

– PUT : mise à jour totale de la ressource ; 

– PATCH : mise à jour partielle de la ressource. 

Nous choisirons le verbe PATCH pour la mise à jour des conversations et GET pour avoir accès au dernier message bot de chaque conversation. 

Code 

Une fois notre API conceptualisée, nous pouvons enfin nous atteler au code Python! La première fonction à implémenter est celle qui permet de mettre à jour une conversation. Nous utilisons pour cela le décorateur Python app.route fourni par Flask. Ce décorateur va intercepter toute requête PATCH dont l’URL contient l’identifiant de la conversation considérée et va appeler la fonction update_conversation. Cette fonction va insérer le message dans la conversation en base (ou créer la conversation si elle n’existe pas). Deux cas se présentent alors : si le message inséré est de type bot, le code réponse 200 est renvoyé (il signifie simplement que le serveur a traité la requête avec succès). Sinon, une redirection est effectuée avec un code réponse 303 pour accéder à la fonction get_answer (voir ci-après). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-10.31-AM-002.jpg)

Pour ce qui est de l’accès à une représentation (équivalent ici au dernier message de type bot de la conversation), nous développons une fonction analogue nommée get_answer. Celle-ci va appliquer le modèle sur la conversation considérée, et générant un message bot sui sera renvoyé au client au format JSON, avec un code 200. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-10.31-AM-003.jpg)

Enfin, ces quelques lignes de code mettront l’API en marche. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-10.31-AM-004.jpg)

Cet article clôt (pour le moment) la thématique des chatbots. Nous avons vu pourquoi et comment implémenter une simple API REST pour chatbot. Maintenant, c’est à vous de jouer ! 
