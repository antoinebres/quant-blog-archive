---
layout: post
title: approches-de-lintelligence-artificielle-partie-ii
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129153310/https://www.quantmetry.com/blog/approches-de-lintelligence-artificielle-partie-ii/
---
Uncategorized 

24/04/2018 

#  Approches de l’intelligence artificielle - Partie II 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fapproches-de-lintelligence-artificielle-partie-ii%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Approches%20de%20l%E2%80%99intelligence%20artificielle%20-%20Partie%20II&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fapproches-de-lintelligence-artificielle-partie-ii%2F "Twitter")

* * *

Temps de lecture : 10 minutes 

![Quantmetry.com : Approches de l’intelligence artificielle - Partie II](https://quantmetry.b-cdn.net/wp-content/uploads/2018/04/machinele.png)

Dans le précédent article, nous avons introduit la notion de système expert, et analysé en quoi les thèses sous-jacentes à ces modèles avaient permis l’émergence d’autres approches de l’intelligence artificielle, dites connexionnistes, qui font l’objet de cet article. 

####  **CONNEXIONNISME : SOFT COMPUTING ET EMBODIED-EMBEDDED AI**

L’exemple le plus fameux d’IA connexionniste est le réseau de neurones. Le premier papier expliquant le fonctionnement d’un neurone artificiel ou perceptron a été publié en 1957 par Frank Rosenblatt. Or il a fallu attendre la fin des années 1970 avant que les approches connexionnistes n’acquièrent définitivement les faveurs des chercheurs dans le domaine de l’IA, et ce malgré la critique radicale des systèmes experts par Dreyfus. 

Différents facteurs expliquent ce manque d’intérêt des scientifiques, parmi lesquels la publication par Marvin Minsky et Seymour Papert de l’ouvrage Perceptrons en 1969, qui a mis en lumière une limitation fondamentale du perceptron : ils ont montré qu’un réseau à une couche intermédiaire ne peut modéliser la fonction XOR que si un neurone de cette couche est connecté avec des poids non-nuls aux neurones en entrée. Or, les chercheurs à l’époque fondaient beaucoup d’espoirs sur les architectures avec peu de connexions non nulles entre neurones de la couche intermédiaires et ceux de la couche d’entrée, car elles étaient plus faciles à construire. 

C’est seulement après la publication de l’ouvrage Parallel Distributed Processing. Explorations in the Microstructure of Cognition par David Rumelhart et James McClelland en 1986, que les approches connexionnistes ont pris leur essor définitif. Les auteurs y montrent l’importance du calcul massivement parallèle permis par les neurones dans le fonctionnement de l’intelligence, qu’il s’agisse de perception, de mémoire, de langage ou de pensée. Tout le contraire des procédures symboliques qui reposent sur l’idée d’un savoir stocké dans dans unités locales et traité par des opérations séquentielles. Voici une citation du New York Times, par Daniel Coleman, qui décrit bien le changement de paradigme que le livre opère : 

« Rumelhart and McClelland propose that what is stored in memory is not specific facts or events, but rather the relationships between the various aspects of those facts or events as they are encoded in groupings of neuronal cells or patterns of cell activity. » 

On dénombre aujourd’hui deux principales variantes incarnant l’approche connexionniste de la cognition dans le domaine de l’informatique : 

  * Les trois principaux types de soft computing, à savoir : 

    * le machine learning, 

    * les systèmes intelligents flous, 

    * et les algorithmes évolutionnistes. 

  * La embodied-embedded AI, qui insiste sur l’importance de la corporéité pour l’acquisition de comportements intelligents par interaction avec l’environnement. 




Les travaux dans ces domaines sont désignés sous le nom d’IA sous-symbolique, car, contrairement à l’approche symbolique, ils ne se basent sur aucune représentation explicite du savoir. 

Nous n’allons pas nous attarder sur les modèles de type soft computing même s’il y aurait beaucoup de choses passionnantes à raconter là-dessus ! J’aimerais vous parler directement de l’approche embodied-embedded AI, qui présente des différences conceptuelles fondamentales en comparaison avec les approches de type machine learning ou algorithmes génétiques. 

####  **EMBODIED-EMBEDDED AI, L’IMPORTANCE DU CORPS POUR L’INTELLIGENCE**

Dans plusieurs de ses ouvrages, Dreyfus insiste sur le fait que les comportements intelligents de l’homme mobilisent deux attitudes bien distinctes de ce dernier vis-à-vis du monde qui l’entoure : 

  * L’attitude consciente de l’homme capable de résoudre pas à pas un problème. C’est celle qui est correctement capturée par les systèmes experts de l’IA, et que Dreyfus désigne par le vocable « Knowing-that » 



  * L’attitude quotidienne de l’homme dans son rapport à l’environnement, qui lui permet de décider les actions à entreprendre sans recourir à des manipulations symboliques, que Dreyfus désigne sous le vocable « Knowing-how » 




Selon Dreyfus, c’est bien l’attitude « knowing-how » et non l’attitude « knowing-that » qui constitue en réalité une expertise, car il s’agit bien d’être capable de sélectionner la bonne solution dans un contexte donné, en isolant les faits pertinents et non en raisonnant sur tous les faits possibles. 

Cette distinction conceptuelle trouve son origine dans les travaux de Martin Heidegger en phénoménologie de l’esprit, qui distingue la « Vorhandenheit », chose simplement là, à portée de main, de la « Zuhandenheit », chose disponible en tant qu’outil. 

Une des traductions techniques de ce problème d’adaptation au contexte si l’on se restreint à une attitude de type « knowing-that » est le problème dit du cadre : comment isoler dans l’univers d’une IA les faits impactés par une modification de l’environnement ? Par exemple, une IA dont l’univers comporte une information sur la lumière dans une pièce (éteinte ou allumée), l’état d’une porte (fermée ou ouverte) et sa situation (dans la pièce ou en dehors) doit, après avoir éteint la lumière par exemple, isoler quels faits nécessitent d’être mis à jour. 

Ce problème a fait l’objet de nombreuses tentatives de résolution jusque dans les années 1980, telles le calcul des situations, l’axiome de l’état successeur ou encore la logique des défauts [1]. Mais aucune de ces méthodes n’est parvenue à capturer la complexité et l’efficacité du sens de la situation que possèdent les systèmes biologiques intelligents. 

On peut affirmer sans ambiguïté qu’à date, les méthodes computationnalistes de l’IA, tout comme les approches du type soft computing, échouent à capturer correctement un contexte ou un sens non donné a priori, comme le montre la tâche non résolue de l’apprentissage non-supervisé en deep learning. 

L’une des premières tentatives pour intégrer le contexte dans le comportement d’une IA a été les animats de Rodley Brooks en 1987 [2]. Il s’agit de petits robots non-apprenants qui se contentent simplement de réagir à quelques caractéristiques fixes de leur environnement, comme l’existence ou non d’obstacles qu’ils vont chercher à éviter. C’est un exemple typique de embodied-embedded AI car l’IA possède une incarnation matérielle et est couplée à son environnement via des capteurs, ces deux aspects contraignant à parts égales les fonctions cognitives dont l’IA est capable. 

Aucune représentation centrale de l’environnement sous forme d’états n’existe dans les animats, et c’est par une sorte d’équilibre des actions des composants du système (qui se référent directement aux senseurs du robot) qu’une décision semble être prise par le robot en tant qu’unité cognitive. 

Cette approche représenta une réelle avancée par rapport aux vues computationnalistes de l’IA qui l’ont précédée, même si elle ne constitue pas en soi une solution au problème du cadre car le robot se contente de réagir à quelques caractéristiques isolées de son environnement. 

Par la suite, Phil Agre et David Chapman ont développé le programme Pengi, dont l’environnement est constitué non d’objets simples mais d’objets représentant des possibilités d’actions. Dreyfus y verra une première modélisation de la Zuhandenheit de Heidegger via ce que Agre et Chapman ont nommé des représentations déictiques. 

Mais cette approche est limitée par l’interprétation de la Zuhandenheit comme une fonction prédéfinie (ce qu’elle n’est pas), que l’on rencontre dans une situation prédéfinie et qui déclenche une action elle aussi prédéterminée. Ceci apparaît de manière flagrante dans l’impossibilité pour le robot d’Agre et Chapman d’intégrer l’expérience pour modifier sa perception des situations suivantes et ce qui y est pertinent pour lui. 

Ainsi, ni la représentation interne symbolique du monde, ni la modélisation de la cognition comme réponse à des caractéristiques fixes de l’environnement ne suffisent à créer des IA situées. Un commentaire de Dreyfus résume parfaitement les limitations de ces travaux [3] : 

« AI researchers need to consider the possibility that embodied beings like us take as input energy from the physical universe, and respond in such a way as to open themselves to a world organized in terms of their needs, interests, and bodily capacities without their minds needing to impose meaning on a meaningless given, as Minsky’s frames require, nor their brains converting stimulus input into reflex responses, as in Brooks’s animats. » 

Le problème d’un couplage non-représentationnel du monde et du corps reste donc entier. À cet égard, les travaux de Maurice Merleau-Ponty en phénoménologie représentent une avancée importante. Dans son ouvrage Phénoménologie de la perception, Merleau-Ponty affirme que les aptitudes acquises lors de l’expérience ne sont pas stockées en tant que représentations dans l’esprit de l’homme, mais comme situations rencontrées dans le monde qui sont de mieux en mieux discriminées. 

Par exemple, notre expérience dans une ville est intégrée dans notre esprit en tant qu’apparence de la ville pour nous, qui correspond souvent à une collection d’apparences locales plus ou moins nettes, sans carte globale parfaitement précise. 

Notre cognition est ainsi faite pour nous permettre de traiter de manière de plus en plus affinée les situations qui se présentent à nous. Existe-t-il un modèle plus technique de cette vision de la cognition ? Comment les propriétés intentionnelles d’un système dépendent-elles d’un substrat physique non-intentionnel, ainsi que d’un environnement possiblement intentionnel et non-physique ? 

Pour répondre à ces questions, il faut revenir aux hypothèses sous-jacent la plupart des modèles neurodynamiques traditionnels : 

  * Le cerveau reçoit des signaux via des capteurs 

  * Le cerveau extrait des caractéristiques abstraites à partir de ces signaux 

  * Le cerveau se constitue une représentation du monde à partir de ces caractéristiques abstraites 




Les chercheurs tentent alors généralement de comprendre comment les caractéristiques d’une carotte (orange, cône, etc.) sont reconnues puis combinées pour constituer la perception d’une carotte. Pour ce faire, on module par exemple les poids des connexions d’un réseau de neurones lors d’un apprentissage supervisé, ce qui revient à imposer une signification de l’extérieur. 

Walter Freeman, un neuroscientifique américain ayant beaucoup travaillé sur le bulbe olfactif des lapins, inverse la perspective : au lieu d’interroger le mode de constitution d’une représentation, il se demande comment un animal inséré dans un environnement déjà signifiant sélectionne les significations ? 

Il apporte une réponse à cette question en quelques points clés, issus d’une compréhension du cerveau comme un système dynamique non-linéaire : 

  * Règle de Hebb : les synapses de neurones qui tirent ensemble deviennent plus fortes si le tir synchronisé reçoit une récompense, formant ainsi une assemblée de neurones 

  * Les assemblées de neurones sont formées via les réponses de l’animal à ce qui est signifiant pour lui, et sont calibrées en retour pour réagir aux signaux pertinents dans l’environnement associés à une signification précise 

  * Les assemblées de neurones sont décrites par des états, dont ceux à énergie minimale qui forment des attracteurs et qui possèdent un bassin d’attraction 

  * Un bassin d’attraction est formé à chaque nouvelle signification pour le couple animal-environnement, par exemple une série d’olfactions de carottes récompensées par l’acte de se nourrir. 

  * Le paysage des attracteurs correspond aux classes de significations apprises par l’animal grâce à son expérience, et il se redessine globalement à chaque nouvelle signification rencontrée. 




Pour citer Freeman [4] : 

« I have observed that brain activity patterns are constantly dissolving, reforming and changing, particularly in relation to one another. When an animal learns to respond to a new odor, there is a shift in all other patterns, even if they are not directly involved with the learning. There are no fixed representations, as there are in [GOFAI] computers; there are only significances. 

[…] 

I conclude that context dependence is an essential property of the cerebral memory system, in which each new experience must change all of the existing store by some small amount, in order that a new entry be incorporated and fully deployed in the existing body of experience. This property contrasts with memory stores in computers […] in which each item is positioned by an address or a branch of a search tree. There, each item has a compartment, and new items don’t change the old ones. Our data indicate that in brains the store has no boundaries or compartments. […] Each new state transition […] initiates the construction of a local pattern that impinges on and modifies the whole intentional structure. » 

On constate ainsi l’ampleur du changement de paradigme nécessaire pour construire des IA réellement situées ! À ce titre, nous renvoyons aux travaux de Freeman sur une IA inspirée du cerveau d’une salamandre, qui apprend à trouver le chemin le plus court vers un point [5]. La combinaison de capteurs, de moteurs, et de composants simulant certaines fonctionnalités du cerveau constitue une approche embodied-embedded de l’IA où le paysage des significations est interne à l’agent. 

On le voit, les paradigmes de l’IA sont nombreux, chacun permettant de simuler des comportements intelligents via le calcul. Ils peuvent être unifiés via la notion d’agent intelligent. Ce dernier est défini comme un système qui perçoit son environnement via les données qu’il collecte et qui décide d’une action en vue d’accomplir un objectif. 

La combinaison de tels agents dans une architecture multi-agents se fait selon des modalités très variées, et l’on peut citer par exemple : 

  * Les hiérarchies : Les agents sont hiérarchisés selon une structure d’arbre, où chaque agent parent possède une relation d’autorité avec ses nœuds fils. 

  * Les coalitions : Les agents constituent des alliances temporaires avec une valeur de la coalition supérieure à la somme des valeurs individuelles, leur permettant ainsi d’atteindre des objectifs plus coûteux ou impossibles à atteindre individuellement. 

  * Les marchés : Des agents proposent des objets à la vente, sur lesquels d’autres agents peuvent renchérir, permettant ainsi de simuler des négociations 



