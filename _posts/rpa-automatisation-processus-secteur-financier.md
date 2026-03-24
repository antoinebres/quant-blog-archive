# rpa-automatisation-processus-secteur-financier
Wayback Machine URL: https://web.archive.org/web/20230606102424/https://www.quantmetry.com/blog/rpa-automatisation-processus-secteur-financier/
Archive date: 2023-06-06

IA de confiance 

30/10/2020 

#  RPA - Automatisation de processus humains dans le secteur financier 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Frpa-automatisation-processus-secteur-financier%2F&title=RPA%20-%20Automatisation%20de%20processus%20humains%20dans%20le%20secteur%20financier "Linkedin") [ ](http://twitter.com/intent/tweet?text=RPA%20-%20Automatisation%20de%20processus%20humains%20dans%20le%20secteur%20financier&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Frpa-automatisation-processus-secteur-financier%2F "Twitter") [ ](https://www.quantmetry.com/blog/rpa-automatisation-processus-secteur-financier/ "Email") [ ](https://www.quantmetry.com/blog/rpa-automatisation-processus-secteur-financier/ "Copy Link")

* * *

Auteur : [ Gaultier LE MEUR ](https://www.linkedin.com/in/gaultierlemeur/)

Temps de lecture : 9 minutes 

![Quantmetry.com : RPA - Automatisation de processus humains dans le secteur financier](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/gle-1.png)

La finance est un monde de chiffres, certes, mais c’est également un monde de confiance. Les valeurs et indices fluctuent sur les marchés financiers au bon vouloir d’une confiance que les investisseurs basent sur les rapports officiels et documents réglementaires ; les fonds d’investissement décident de l’ajout d’un titre à un portefeuille en se basant sur la confiance qu’ils ont en ce produit financier à générer un retour sur investissement… informations qu’ils retrouvent dans les documents relatifs au produit, par exemple le DICI (Document d’Information Clés pour l’Investisseur ou KIID en Anglais, _cf._ [ article de l’AMF ](https://www.amf-france.org/sites/default/files/contenu_simple/guide/guide_pedagogique/S%27informer%20sur%20%20Le%20document%20d%27information%20cle%20pour%20l%27investisseur%20%28DICI%29.pdf) ). Générer de la confiance est donc, en partie, une affaire d’information et, on le verra par la suite, d’automatisation de création, de gestion et d’exposition de cette donnée. 

Dans cet article, nous allons traiter de l’ **automatisation d’extraction d’information,** et plus largement, de l’automatisation de processus, plus connue sous le nom de **_Robotic Processus Automation_ (RPA) ** . Nous présenterons les **motivations** qui mènent à l’automatisation de processus dans le secteur financier, proposerons des **solutions** de robotisation en respectant des contraintes d’adoption, de performance et de suivi qualité et, finalement, discuterons de la **chronologie** de mise en production. 

À des fins d’illustration, nous prendrons l’exemple d’un projet réalisé en mi-2020 par Quantmetry pour un fournisseur de données financières. L’objectif de la mission était d’extraire automatiquement une information de performance financière sur des documents financiers au format PDF, appelés DICI, afin de suppléer à une action humaine répétitive et fastidieuse bien que peu complexe. 

####  Pourquoi automatiser des processus humains ? 

Selon l’étude consommateur du Gartner intitulée [ _Magic Quadrant for Robotic Process Automation_ ](https://www.gartner.com/en/documents/3988021/magic-quadrant-for-robotic-process-automation) publiée en juillet 2020, les trois principales motivations de l’achat d’une solution de RPA, comme UiPath ou Automation Anywhere, sont l’ **optimisation de l’efficacité opérationnelle, l’accélération d’un processus existant et l’optimisation des coûts** . De façon pragmatique, l’optimisation est très souvent financière (mais peut être organisationnelle ou logistique), et une rapide extrapolation de ces résultats consiste à dire que, puisque le temps c’est de l’argent, l’objectif principal serait d’ **accélérer la réalisation de processus humains** . 

Une raison justifiant l’implémentation d’un outil d’automatisation est également la **fiabilisation des résultats.** En effet, comme le met en avant [ cet article de trustpair ](https://trustpair.fr/blog/automatisation-processus-impact-services-financiers/) , les tâches parfois simples mais non moins fastidieuses inhérentes à certains métiers de la finance sont sources d’erreurs humaines (possiblement du fait de la répétition) aux conséquences parfois dramatiques (présentation de faux chiffres par exemple). Sur ce sujet, lorsque la tâche est relativement simple, que le cadre est clairement établi et que la méthode d’évaluation de la performance est bien maîtrisée, comprise et validée par toutes les parties prenantes, il semble très opportun d’étudier la conception et la mise en production d’un outil d’automatisation. 

Il est également intéressant de considérer **la scalabilité d’une solution technique** comme une raison valable d’implémentation d’une solution de RPA. Effectivement, l’augmentation de la quantité de documents à traiter est souvent moins coûteuse avec un _pipeline_ de traitement automatisé que le recrutement (et la formation) de ressources humaines supplémentaires. Qui plus est, l’utilisation d’une solution d’extraction d’information permet également de rediriger les employé.e.s vers des tâches à plus forte valeur ajoutée comme l’analyse des informations extraites. 

Les raisons présentées dans la conclusions de l’article [ How Automation Is Changing Financial Services ](https://www.digitalistmag.com/finance/2019/12/19/how-automation-is-changing-financial-services-06201930/) sont alignées avec celles énumérées précédemment : “cette solution [un RPA] permet non seulement d’ **économiser beaucoup d’argent** et de **libérer des ressources** , mais aussi d’ **accélérer le temps de traitement des demandes** et de contribuer à la mise à disposition d’informations financières **plus opportunes** dans le système”. 

Toutefois, certains freins peuvent retarder voire empêcher l’automatisation de processus humains, par exemple : 

  * la **capacité d’adaptation** de l’humain est inégalable et cela peut s’avérer déterminant lorsque le format des documents à trairer est amené à changer régulièrement ; 
  * l’ **investissement de la direction** et une stratégie claire de _change management_ sont indispensables pour l’adoption de cette solution ; 
  * les coûts d’un tel projet sont souvent élevés, le **retour sur investissement** attendu doit donc être élevé. 



####  Comment automatiser un processus humain de manière sécurisée ? 

Une solution technique dont l’ambition est d’être portée en production, notamment lorsqu’elle embarque des briques d’intelligence artificielle, nécessite une phase de prototypage incluant l’ensemble des parties prenantes, métier et IT ( [ voir article de Quantmetry ](https://www.quantmetry.com/blog/proof-of-concept-why/) ). Lors de cette phase, il faudra : 

  * porter attention à la **représentativité des documents étudiés** par rapport à la masse totale des documents à traiter dans une solution cible ; 
  * élaborer une **méthodologie détaillée et précise d’évaluation de la performance** (une vérification de l’alignement de toutes les parties prenantes est nécessaire) ; 
  * s’assurer de la **facilité d’industrialisation du prototype** qui se traduit par des contraintes fortes de développement concernant le passage à l’échelle, la configuration dans un autre environnement de déploiement et les capacités d’évolution de la solution. 



L’adoption de la solution est un sujet clé. La décision sera très fortement basée sur les performances obtenues lors de la phase de prototypage. Néanmoins, aussi bonnes seront les performances en termes de précision d’extraction (bonnes, mauvaises ou manquantes), **une réticence persistera probablement sur le passage en production** . Ce doute pourrait alors se traduire par de nombreuses questions : “Que se passera-t-il si les documents changent de format ?”, “Quid du traitement de l’information d’un nouvel émetteur de document?” (sous entendu, quelle est la capacité de généralisation de le solution ?), ou encore “Comment s’assure-t-on que la solution, aussi bonne soit-elle sur tel type de document, n’a pas une performance qui décroît au fil du temps ?”. 

La réticence au passage en production d’un processus d’automatisation est rationnelle, et même si les réponses aux questions ci-dessus sont satisfaisantes, il est souvent préférable, pour rassurer l’ensemble des parties prenantes, de commencer par l’implémentation d’ **une solution hybride** . L’idée serait de ne pas se passer des extractions humaines mais de rediriger certaines tâches vers le module automatisé. L’objectif est multiple : 

  * fiabiliser la solution conçue pendant la phase de prototypage en résolvant de possibles bugs ; 
  * comparer les résultats du processus automatisé avec ceux du processus humain ; 
  * créer un temps d’adaptation pour une adoption plus sereine. 



Un facteur clé de succès sera également l’ **adoption de la solution envisagée par les équipes habituellement en charge des extractions** . En effet, la solution hybride étant la recommandation la plus probable la mise en place d’une solution de RPA, les opérateurs devront travailler de pair avec l’outil afin de le fiabiliser. 

####  Quand lancer en production le processus d’automatisation ? 

Question temporalité, comme le souligne cet article [ Robotisation, automatisation : les questions à se poser avant de se lancer ](https://www.pwc.fr/fr/vos-enjeux/data-intelligence/robotisation-automatisation-les-questions-a-se-poser-avant-de-se-lancer.html) : “la mise à l’échelle de ce mode de robotisation **s’effectue généralement en quelques mois** . Le développement en mode continu permettra par la suite de déployer des robots en grande quantité et en peu de temps”. Pour un projet sur l’extraction d’information de documents PDFs, quelques **semaines suffisent généralement pour construire les premières briques** de traitement des documents, d’identification des zones et textes d’intérêt et d’extraction de l’information. 

Au moment du choix de _go/no go_ de la mise en production, il sera pertinent de s’être assuré de : 

  * l’obtention de résultats basés sur un **échantillon représentatif des données traitées habituellement** et jugés satisfaisants par l’ensemble des parties prenantes ; 
  * la définition d’un **processus clair d’évaluation continue des performances** (pendant la phase de _run)_ ; 
  * la **préparation des équipes** data avec la conception d’une _roadmap_ claire de mise en production et avec des rôles et responsabilités clairs et bien répartis (éventuellement un RACI). 



Dans le cas d’un développement sur mesure d’une première solution de RPA, il sera nécessaire, après validation des performances du prototype et si le choix d’industrialisation se porte vers une **solution hybride** , de prendre en compte, lors de l’élaboration de la _roadmap_ de mise en production, le **temps de conception et de développement d’une interface homme-machine (IHM)** pour les équipes en charges des extractions. L’objectif de l’IHM étant de présenter aux équipes les extractions automatiques et potentiellement des informations supplémentaires qui facilitent le travail de vérification / validation, un exemple d’IHM sera discuté dans la présentatio du cas d’usage ci-dessous. 

####  Cas d’usage : extraction d’information de documents PDFs 

Afin d’illustrer nos propos, nous allons nous intéresser à l’extraction automatique d’une information présente sur des documents appelés DICI (ou KIID), projet réalisée en 2020 par Quantmetry. 
