---
layout: post
title: ai-production-hard-part
date: 2025-04-20
url_wayback_machine: https://web.archive.org/web/20250420005013/https://www.quantmetry.com/blog/ai-production-hard-part/
---
Data Gouvernance 

30/01/2020 

#  AI in production : now the hard part 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fai-production-hard-part%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=AI%20in%20production%20%3A%20now%20the%20hard%20part&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fai-production-hard-part%2F "Twitter") [ ](https://www.quantmetry.com/blog/ai-production-hard-part/ "Email") [ ](https://www.quantmetry.com/blog/ai-production-hard-part/ "Copy Link")

* * *

Temps de lecture : 8 minutes 

![Quantmetry.com : AI in production : now the hard part](https://www.quantmetry.com/wp-content/uploads/2020/01/quantmetry-gregoire-martinon.png)

_ ✍ [ Grégoire Martinon ](https://www.linkedin.com/in/gregoire-martinon/) / Temps de lecture : 10 minutes _

####  [ Revivez la table ronde de DataJob !  ](https://www.youtube.com/watch?v=_TjGkRuYplo)

Intelligence artificielle en production et cycle de vie des modèles, c’était le sujet de la table ronde à la dernière édition de DataJob ! 

####  Intervenants 

Quatre intervenants issus du milieu académique et de grandes entreprises sont venus témoigner. 

  * **Jacob Montiel :** il a travaillé en tant qu’ingénieur logiciel chez GE Aviation à Mexico, dans une équipe de maintenance prédictive aéronautique. Il a ensuite fait une thèse à Télécom ParisTech en _stream mining_ . Il est également le contributeur principal de la librairie scikit-multiflow. 
  * **John Whitbeck :** titulaire d’un doctorat en informatique, il a travaillé chez Criteo avant de rejoindre Liftoff, une entreprise à forte croissance internationale spécialisée dans les enchères publicitaires sur applications mobiles. Liftoff génère actuellement plus de 300 millions de prédictions à la seconde, et ré-entraîne automatiquement plusieurs centaines de modèles chaque jour. 
  * **Renan Borne :** il a travaillé quinze ans chez Société Générale Corporate and Investment Banking en trading électronique. Depuis trois ans il est Chief Architect chez AXA Investment Managers, dans le département transformation data. AXA IM gère 760 milliards de dollars d’actifs et compte 2 330 employés à travers le monde. 
  * **Héloïse Nonne :** titulaire d’un doctorat en physique quantique, elle est désormais Head of Data Science and Engineering à ITNOVEM, centre d’expertise de la SNCF. Elle dirige des projets construisant des solutions d’intelligence artificielle de bout en bout, appliquées, entre autres, à la maintenance prédictive et à l’optimisation de la consommation d’énergie. La SNCF exploite actuellement un parc de 15 000 trains et pilote 270 To de données sur le cloud. 



####  La gestion du cycle de vie est difficile 

> Une bonne stratégie pour limiter le risque est de toujours garder un humain dans la boucle. 

![](https://www.quantmetry.com/wp-content/uploads/2020/02/hard.jpg)

#####  Pourquoi faut-il réentraîner les modèles constamment en production ? 

**Jacob Montiel.** Le _machine learning_ classique fait l’hypothèse que les données sont identiquement distribuées entre le jeu d’entraînement et le jeu de prédiction. Or aujourd’hui, la donnée arrive en grand volume et est en évolution constante. C’est le cas par exemple sur les marchés financiers, qui sont très instables et volatils. Quand un nouveau signal arrive, un modèle statique va l’interpréter, à tort, comme du bruit. C’est pourquoi il faut concevoir une phase de mise à jour du modèle. 

#####  Comment intégrer la notion de risque dans le cycle de vie des modèles ? 

**Renan Borne.** Cela dépend du modèle. Certains modèles servent juste à donner de grandes tendances globales. Le diagnostic qui en découle est donc relativement robuste aux changements. D’autres modèles sont plus critiques, dans la mesure où ils cherchent à détecter des nouveaux signaux de faible intensité. Dans ce cas, la validation du modèle est difficile à automatiser. Une bonne stratégie pour limiter le risque est de toujours garder un humain dans la boucle : en corrélant les prédictions du modèles avec des éléments plus globaux, on peut s’assurer que le modèle ne contredit pas les éléments de contexte qui n’ont pas été ingérés par le modèle. 

#####  Quelle est la partie la plus difficile dans le cycle de vie des modèles ? 

**Héloïse Nonne.** La partie la plus difficile est de relier l’apport de l’intelligence artificielle au besoin métier. A la fin, il s’agit de prendre une décision : Quelle décision ? Quelle est sa criticité ? Qui la prend ? Le modèle doit être conçu pour répondre à ces questions. Par exemple à la SNCF, la maintenance des stations d’aiguillage est très critique, c’est un enjeu de sécurité. Doit-on détecter une maintenance d’urgence, très coûteuse (arrêt du trafic, dépêchement de main d’oeuvre), ou bien anticiper et réaliser une opération de prévention ? Ce sont deux problématiques complètement différentes. Une autre difficulté est la conduite du changement : en production, il y a toujours une longue phase de test et d’allers-retours entre utilisateurs métier et concepteurs du modèle. C’est quelque chose de très difficile dans la mesure où ce sont deux mondes complètement différents qui se rencontrent et qui ont du mal à se comprendre. 

####  Les compétences requises par le cycle de vie 

> Les profils les plus rares sont ceux qui combinent compréhension du besoin métier et maîtrise de l’intelligence artificielle. 

![](https://www.quantmetry.com/wp-content/uploads/2020/02/skills-500x245.jpg)

#####  Quelles compétences sont nécessaires pour gérer le cycle de vie et comment les organiser ? 

**John Whitbeck.** Il faut un certain nombre de compétences techniques : d’une part, une appétence forte en ingénierie logiciel pour construire des chaînes de traitement robustes, et d’autre part un haut degré de maîtrise scientifique pour apporter une réponse pertinente aux enjeux métiers. Pour les petites structures, il faut savoir chasser les rares personnes qui ont les deux domaines de compétences, et les organiser en une équipe réactive et responsable de bout en bout : depuis la conception scientifique jusqu’à la réalisation industrielle. Pour les plus grandes structures, un premier modèle (par exemple chez Google, Facebook, Baidu) consiste à mélanger les ingénieurs et les data scientists dans des équipes projet mixtes. Un second modèle (par exemple chez Uber ou Stripe) consiste à construire une interface (ou API) entre les équipes data science et les équipes de production : tant que les data scientists respectent cette interface, les modèles peuvent facilement partir en production. 

#####  Quels sont les profils les plus demandés et les plus difficiles à trouver ? 

**Héloïse Nonne.** Dans une grande structure comme la SNCF, il vous faut certains profils très spécifiques dans les équipes métiers. Il vous faut par exemple une personne ayant une compréhension profonde du besoin métier mais qui a une appétence pour l’intelligence artificielle, capable d’apprendre la technique, d’en comprendre les possibilités et les limitations. C’est ça qui est particulièrement difficile : trouver ce type de profil, les embarquer sur des projets, entretenir le lien avec les équipes techniques. La vraie question devient alors : comment mettre une équipe en production ? 

####  Les solutions propres au cycle de vie 

> Celui qui met le modèle en production doit pouvoir détecter les problèmes avant que l’utilisateur final ne les remarque. 

![](https://www.quantmetry.com/wp-content/uploads/2020/02/solve-500x321.jpg)

#####  Comment adapter le machine learning au problème des données non-stationnaires ? 

**Jacob Montiel.** Il existe un champ de recherche autour de cette thématique, c’est le _stream mining_ . L’hypothèse de base est que les données arrivent en flux continu, pendant une durée indéterminée, potentiellement infinie, et que le signal sous-jacent peut évoluer de manière imprévisible. L’objectif est alors de concevoir des algorithmes qui se mettent à jour de manière autonome, tout en étant robustes aux changements et le plus efficaces possible dans les gestion des ressources informatiques. On peut alors construire une boucle de rétroaction entre la performance prédictive du modèle et son processus de mise à jour : c’est un cycle de vie algorithmique. Comme pour le machine learning classique, il y a cette volonté de faire parti du monde open-source. La librairie scikit-multiflow permet justement aux personnes du secteur industriel de tester et d’expérimenter ces solutions qui viennent du monde académique. 

#####  Quelles architectures et technologies sont pertinentes pour le cycle de vie ? 

**Renan Borne.** Chez AXA IM, nous travaillons sur deux dimensions : l’autonomie des Data Scientists et l’appropriation des techniques DevOps standards. D’un point de vue technique, nous avons fait le choix d’un développement sur le cloud Azure, afin de rapprocher la donnée des Data Scientists. Par ailleurs, ces derniers sont habitués à utiliser Python et Jupyter. Il faut donc réussir à intégrer ces pratiques dans la même chaîne de traitement que les autres applications. Pour caricaturer, il faut pouvoir partir d’un processus d’idéation, de développement, et ensuite pouvoir appuyer sur un bouton “passage en production”. On se base alors sur des fabriques logiciel pour les modèles. 

#####  Quelle stratégie pour surveiller et consolider les chaînes de traitements ? 

**John Whitbeck.** En intelligence artificielle, il est très difficile de réaliser des tests unitaires. Typiquement, il peut y avoir des erreurs qui passent inaperçues dans les données. Qui plus est, il est impossible d’isoler les sous-parties d’un modèle de _machine learning_ : la modification d’une seule variable d’entraînement va modifier l’ensemble des paramètres du modèle. Enfin, la notion de succès est floue car les prédictions d’un modèle sont toujours inexactes : on ne peut que définir des seuils d’exactitude en deça desquelles une alarme est déclenchée. En réalité, avant même de modéliser, il faut se poser les bonnes questions : Comment la donnée est-elle distribuée? A quelle vitesse évolue-t-elle ? Avec quel délai peut-on s’en rendre compte ? A quelle fréquence peut-on réentraîner le modèle ? Est-ce que les données d’entraînement sont représentatives des données de production ? Et même une fois que vous avez entraîné votre modèle, le travail n’est pas terminé : vous devez l’évaluer en production, en réalisant des A/B testings en direct, basés sur l’apport financier immédiat du modèle. D’une manière générale, celui qui met le modèle en production doit pouvoir détecter et résoudre les problèmes avant que l’utilisateur humain ne le remarque. 

####  En résumé 

![](https://www.quantmetry.com/wp-content/uploads/2020/02/capture-decran-2020-02-06-a-09-45-16-500x500.png)

Le cycle de vie est donc la gestion organisationnelle, scientifique et technique des modèles en production. Parmi les difficultés évoquées, on retiendra : 

  * **La volatilité :** le monde extérieur est instable et chaotique, ce même que les données. 
  * **L’incertitude :** les modèles ne peuvent pas être fiables à 100%, il faut souvent juger les prédictions à l’aune d’une intelligence situationnelle intrinsèquement humaine. 
  * **La coopération :** il existe un gouffre entre le monde opérationnel et le monde technique de l’intelligence artificielle, difficile à combler en termes de profils et de compétences. 



A ce titre, la Data Science semble entrer dans une phase de maturation qui intègre de nouveaux champs de compétences : 

  * **L’ingénierie logicielle,** qui répond au besoin de robustesse des chaînes de traitement de la donnée. C’est le profil ML Engineer qui commence à se définir. 
  * **La coordination des équipes,** qui répond au besoin d’insertion des prédictions algorithmiques dans un processus métier. C’est le profil de Product Owner. 



Au-delà de l’enjeu organisationnel, qui est de taille dans la bonne conduite du cycle de vie, des solutions scientifiques et techniques se mettent progressivement en place : 

  * **Le _stream mining_ : ** c’est la science des flux de données non-stationnaires, qui propose une intégration algorithmique du cycle de vie des modèles. 
  * **L’architecture :** qui vise à raccourcir les distances pour atteindre les gisements de donnée et à optimiser la qualité des traitements. 
  * **La robustesse :** qui doit adapter les techniques CI/CD à la logique floue et probabiliste de l’intelligence artificielle en général. 



_Quantmetry sort son nouveau livre blanc,[ IA en production ](https://www.quantmetry.com/les-livres-blancs/) , disponible gratuitement. _

✍ [ Grégoire Martinon ](https://www.linkedin.com/in/gregoire-martinon/)
