---
layout: post
title: les-chatbots-de-a-a-z
date: 2023-06-02
url_wayback_machine: https://web.archive.org/web/20230602194844/https://www.quantmetry.com/blog/les-chatbots-de-a-a-z/
---
NLP 

16/03/2017 

#  Les ChatBots de A à Z 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fles-chatbots-de-a-a-z%2F&title=Les%20ChatBots%20de%20A%20%C3%A0%20Z "Linkedin") [ ](http://twitter.com/intent/tweet?text=Les%20ChatBots%20de%20A%20%C3%A0%20Z&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fles-chatbots-de-a-a-z%2F "Twitter") [ ](https://www.quantmetry.com/blog/les-chatbots-de-a-a-z/ "Email") [ ](https://www.quantmetry.com/blog/les-chatbots-de-a-a-z/ "Copy Link")

* * *

Temps de lecture : 8 minutes 

![Quantmetry.com : Les ChatBots de A à Z](https://quantmetry.b-cdn.net/wp-content/uploads/2017/03/bots-1-930x546-1.jpg)

##  Vous avez dit ChatBot ? 

Cette semaine, Quantmetry s’intéressera à l’engouement du monde de la tech pour les ChatBots. Cet article est le premier d’une série de 3 articles, il présentera l’intérêt que peuvent représenter les ChatBots, ce qu’ils peuvent faire et leurs limites. Les deux articles suivants présenteront d’abord comment nous avons approché les ChatBots pour y inclure de l’intelligence artificielle au travers d’un cas d’usage, et comment mettre à profit les APIs dans le cadre des ChatBots. 

Un ChatBot est un logiciel pouvant communiquer avec quelqu’un par le biais d’un langage naturel. Ils peuvent servir à répondre à nos questions, sur le temps, les informations, notre agenda, mais aussi nous commander des produits ou des services, comme un taxi, un billet, des vêtements etc… 

Longtemps vibrante, la scène des agents conversationnels n’a connu un véritable essor que récemment début 2016. Il faut dire que cette volonté de parler avec des machines remonte à loin, depuis le père de l’informatique [ Alan Turing et son célèbre test ](https://fr.wikipedia.org/wiki/Alan_Turing#Vers_l.27intelligence_artificielle_:_le_test_de_Turing) . 

Pourquoi un tel essor aujourd’hui ? Tant que la poussière soulevée par cette explosion n’est pas retombée, il est difficile de répondre à cette question. Néanmoins, en assistant aux meet-ups, en rencontrant les créateurs de start-ups de ChatBots, en suivant les explications des GAFA (Google, Amazon, Facebook, Apple) concernant leurs investissements dans ce domaine, plusieurs grands types de réponses se dessinent et se répètent : 

  * **Aller là où les consommateurs sont, et sont accessibles.**




A la mi-2015, le nombre d’utilisateurs sur les 4 applications de messageries les plus utilisées dépassait le nombre d’utilisateurs des 4 applications de réseaux sociaux les plus importantes. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/messaging-apps-are-now-bigger-than-social-networks.png)

Pourtant le nombre d’utilisations commerciales et marketing des applications de messageries est bien plus réduit que sur les réseaux sociaux. Cette asymétrie d’utilisation, alors même que les opportunités sont équivalentes, a amené un certain nombre d’acteurs à se positionner sur ce marché. Pour y accéder, il fallait pouvoir entrer dans un format similaire à ce qui est offert actuellement et donc passer par des ChatBots. 

  * **Un spin-off des applications mobiles.**




La moitié des utilisateurs n’ont téléchargé presqu’aucune app en 2016 (source : [ comScore ](https://www.comscore.com/Insights/Presentations-and-Whitepapers/2016/The-2016-US-Mobile-App-Report) ). Le marché des Apps mobiles est devenu mature, et le calcul de ROI (Return On Interest) des applications mobiles est plus facile à faire. Une analyse fréquente de ce chiffre est que les utilisateurs ont déjà trop d’applications dans leurs smartphones et ne sont pas vraiment prêts à en installer d’autres facilement. 

Les ChatBots sont parfois considérés comme une version cloud des applications mobiles. Le bot Uber déployé sur Messenger par exemple permet de faire essentiellement la même chose que l’application Uber, commander un chauffeur d’un point A à un point B, mais ne nécessite pas de télécharger l’application. En ce sens les ChatBots sont un peu aux applications ce que les sites web sont aux programmes locaux sur votre machine. Reste que le changement de paradigme vers une interface textuelle constitue un véritable enjeu d’UX (Experience Utilisateur) pour lequel aucune solution standard n’existe pour l’instant. Ce changement de paradigme est aussi une chance car il apporte une véritable facilité d’interaction avec le service. 

  * **Des coûts de développements (à priori) plus réduits.**




Une grande partie des coûts induits par le développement d’une application mobile est directement reliée à l‘interface utilisateur plus qu’au développement des fonctionnalités attendues par l’App. Or, les applications de messageries ont toutes ou presque désormais développé des modules permettant de s’interfacer rapidement à leurs services. 

Résultat : pour créer un ChatBot, plus besoin de développer un front. Il suffit de développer directement le ChatBot. Certaines plateformes (comme BotFuel ou API.ai) permettent déjà de déployer un ChatBot commun pour toutes les différentes interfaces, et d’autres vous permettent de créer des ChatBots basiques facilement comme ChatFuel, ou FacebookMessenger , parfois sans même avoir besoin de passer par du code (même si les possibilités restent encore limitées au moment de cet article). 

Reste que les ChatBots constituent un problème fondamental de design et un challenge pour l’UX, et que ce challenge peut avoir un coût important et un impact sur le ROI du projet. 

##  Et l’intelligence artificielle dans tout ça ? 

Pour bien comprendre comment l’intelligence artificielle permet d’étendre massivement le champ des possibles pour les ChatBots, il faut comprendre leur principe de fonctionnement. 

Globalement, les services clients ont deux fonctions : récupérer des informations des clients et les guider en menant avec eux une conversation. 

Dans la plupart des démarchages clients et quelques services clients, les opérateurs soit naviguent au sein d’arbres de conversations qui « scriptent » l’échange, soit se basent sur des phrases pré-construites qui cadrent les éléments communiqués. Ce script ou cette base permet une standardisation, et une facilité de formation des opérateurs. 

Un ChatBot permet la navigation automatisée parmi l’ensemble de ces réponses possibles, ainsi que la récupération des informations contenues dans la conversation. Certes, il existe des ChatBots qui permettent de générer leurs propres phrases (on parle alors de Natural Language Generation). Mais ces ChatBots restent à l’heure actuelle un défi du domaine de la recherche plus que de l’industrialisation (source : [ Seattle Times ](http://www.seattletimes.com/business/baidu-research-chief-andrew-ng-fixed-on-self-taught-computers-self-driving-cars/) ) 

Là où un opérateur utilise son jugement pour savoir vers quelle branche s’orienter, un ChatBot utilisera un ensemble de règles pour naviguer dans l’arbre de conversation. Dans le cas où le nom et le prénom ont été demandés au client, c’est le jugement de l’opérateur qui permettra de savoir si le client a refusé de donner cette information, et donc qu’il faut justifier cette demande dans la réponse, ou si le message transmis contient bien un nom et un prénom et qu’il faut dans la réponse demander les prochaines informations. Dans le cas d’un ChatBot, ce jugement humain sera remplacé par un ensemble de règles permettant d’analyser les réponses des utilisateurs en fonction du contexte. On retrouve la même équivalence entre le jugement d’un opérateur et un ChatBot dans la récupération des informations clients. 

C’est dans l’établissement de ces règles que le machine learning (ou apprentissage automatique) peut assister le travail de développement de ChatBot et permettre l’obtention de bots plus intelligents et plus agréables à qui parler pour les clients. Le machine learning peut intervenir de différentes manières, à la fois pour déterminer la bonne attitude et la bonne réponse pour le client, et pour déterminer quelles sont les éléments d’information à récupérer dans les messages des clients, et à quels champs ils s’appliquent (dans ce cas on parle de Natural Langage Understanding ou NLU). 

Le machine learning peut être utilisé comme une première couche d’analyse pour interpréter les messages clients et permettre une programmation de concepts complexes à décrire finement. 

Par exemple, pour mener la conversation et savoir quoi répondre, on pourrait utiliser une représentation word2vec ou doc2vec (source : [ Christopher Olah ](http://colah.github.io/posts/2014-07-NLP-RNNs-Representations/) ) (pré-entrainé) pour tester la présence de concepts dans le message visiteur et baser les règles établies par les développeurs sur ces concepts. Sinon, on pourrait directement imaginer un modèle de machine learning prenant un message visiteur en entrée et retournant le message à répondre. 

On retrouve la même dualité d’approche dans l’extraction des informations clients. On peut se servir de « pos-tagger » pré-entrainés (ou étiqueteur morphosyntaxique) qui caractérisent la nature du mot (nom adjectif verbe etc…) et permettent à des développeurs de se guider sur cette nature pour établir les règles à appliquer. Par exemple, un pos-tagger permet de coder un algorithme de récupération de prénom en testant la nature des mots de la phrase. Sinon, cette information peut directement être rendue par un modèle de machine learning qui a été entrainé sur un historique de messages clients traités et les informations extraites correspondantes. 

Cette utilisation du machine learning permet d’inclure une certaine forme d’intelligence qui facilite grandement la vie des utilisateurs et des développeurs. Sans elle, les développeurs devraient lister l’intégralité des synonymes lorsqu’ils cherchent un mot dans une phrase. Le client devrait choisir des formulations de phrases spécifiques et l’expérience qu’il aurait du service reviendrait à cliquer sur les phrases qu’on lui propose et qui lui conviennent le mieux. Sans cette utilisation du machine learning, les développeurs devraient lister une à une toutes les manières de donner son nom, et tous les noms et prénoms possibles pour pouvoir les récupérer. 

##  Comment créer un ChatBot intelligent? 

Pour créer un ChatBot intelligent, c’est-à-dire un ChatBot incluant du machine learning, il faut des données sur lesquelles apprendre ou un modèle pré-entrainé. Dans le cas de pos-tagger ou de word2vec, ces modèles peuvent être pré-entrainés sur de larges corpus. De tels modèles pré-entrainés peuvent être trouvés pour le Français sur l’excellent site de [ Jean-Philippe Fauconnier ](http://fauconnier.github.io/#data) . 

Dans le cas contraire où on attend une application du machine learning spécifique au problème que le ChatBot doit résoudre, des données spécifiques sur ce traitement doivent être recueillies. La qualité du ChatBot dépendra directement de la qualité de ces données. Aussi, pour obtenir ces données, il faut donc qu’il existe un service de qualité, même temporaire. Pour cela, un arbre de conversation permettant de définir les parcours clients classiques doit être développé, et les opérateurs doivent autant que possible rester au sein de cet arbre en répondant au client. Ce processus sera plus facile à appliquer pour le démarchage client que pour les services clients, puisque les arbres de conversations y sont plus largement utilisés. Dans le cas où aucun arbre n’a déjà été développé, la meilleure pratique consiste à définir cet arbre de façon AGILE en modifiant et complétant un premier arbre de conversation par rapport au retour d’expérience de son utilisation par les conseillers. Une fois cet arbre défini et complet, les opérateurs seront ensuite en charge de naviguer au sein de cet arbre de conversation pour guider les clients. L’hi 
