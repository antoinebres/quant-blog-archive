# chat-gpt-et-les-secrets-des-large-language-models
Wayback Machine URL: https://web.archive.org/web/20250328151507/https://www.quantmetry.com/blog/chat-gpt-et-les-secrets-des-large-language-models/
Archive date: 2025-03-28

IA de confiance, NLP 

23/08/2023 

#  Chat GPT et les secrets des Large Language Models 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fchat-gpt-et-les-secrets-des-large-language-models%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Chat%20GPT%20et%20les%20secrets%20des%20Large%20Language%20Models&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fchat-gpt-et-les-secrets-des-large-language-models%2F "Twitter") [ ](https://www.quantmetry.com/blog/chat-gpt-et-les-secrets-des-large-language-models/ "Email") [ ](https://www.quantmetry.com/blog/chat-gpt-et-les-secrets-des-large-language-models/ "Copy Link")

* * *

Auteur : [ Armand Joulin ](https://www.linkedin.com/in/armand-joulin-0274254/)

Temps de lecture : 3 minutes 

![Quantmetry.com : Chat GPT et les secrets des Large Language Models](https://www.quantmetry.com/wp-content/uploads/2023/07/mojahid-mottakin-1na806zwupg-unsplash.jpg)

_ Arrivés avec fracas sur le devant de la scène avec  _ _ ChatGPT  _ _ , les LLM  _ _ (Large  _ _ Language  _ _ _ _ Models  _ _ ) constituent un champ extrêmement prometteur  _ _ de l’IA générative.  _ [ **_ Armand  _ ** **_ Joulin  _ ** ](https://www.linkedin.com/in/armand-joulin-0274254/) _ , ex-directeur de recherche chez FAIR  _ _ (Meta) et développeur du LLM open source  _ _ LLaMa  _ _ , explique leur  _ _ fonctionnement dans la perspective de leur utilisation par les entreprises.  _ ​ 

Immédiate sensation médiatique,  ChatGPT  a très vite suggéré tout le  parti qu’il serait possible de tirer d’un LLM (Large  Language  Model), c’est-  à-dire d’une **IA capable de comprendre et de générer du texte à la** **manière d’un être humain** . Toutefois, les capacités impressionnantes de  ChatGPT  ne doivent pas occulter ses limitations si on le considère sous  l’angle d’une solution d’entreprise. On ne peut ni l’étudier pour disséquer  son comportement, ni l’adapter aux besoins spécifiques d’un cas d’usage  pour par exemple s’assurer de la véracité du contenu généré ou qu’il  explicite ses sources.  . Face aux restrictions de cette boîte noire, la  question est donc de savoir si un LLM alternatif serait envisageable  ou s’il  faut développer des outils autour de  ChatGPT  pour apporter ces  fonctionnalités  .  ​ 

Le principe des LLM est de construire des séquences de mots par une  approche probabiliste. À partir d’un vaste corpus de textes, le modèle  apprend les enchaînements de mots les plus probables et utilise ce même  principe lorsqu’il doit à son tour générer de nouvelles phrases. C’est une  méthode relativement frustre et ancienne, mais qui donne aujourd’hui  d’excellents résultats grâce à **deux avancées majeures** : d’une part, **la** **possibilité de mettre en œuvre des puissances de calcul phénoménales** ;  d’autre part, **l’existence de volumes astronomiques de données sur** **lesquelles entraîner le modèle** .  ​ 

Lorsqu’on dispose de ces deux éléments, et des compétences  appropriées, le développement d’un LLM est somme toute assez  rectiligne : on choisit un ensemble de textes, on délimite et on restreint  le vocabulaire (  tokens  ), on entraîne un réseau de neurones (transformer)  pour bâtir le modèle probabiliste, et enfin, on optimise ce dernier à l’aide  de méthodes mathématiques (algorithme du gradient,  rétropropagation…) et d’interactions humaines. 

La performance d’un LLM dépend pour commencer du soin avec lequel on  aura constitué le corpus de textes d’apprentissage. Il doit être énorme  ( **plusieurs centaines de milliards de** **tokens pour ChatGPT** ), le cas échéant  spécialisé, et, surtout, de bonne qualité, car le modèle se contente de  reproduire ce qu’il a appris. En d’autres termes, mieux vaut, comme le  LLM open source  LLaMa  , développé par Meta, se baser sur  Wikipedia  et  ArXiv  que sur  Reddit  et 4chan ! Ensuite, bien sûr, plus on dispose de  moyens et de temps, meilleurs sont les résultats. Entraîner  LLaMa  a  nécessité **2 000 GPU** pendant trois semaines pour **65 milliards de** **paramètres** . Rares sont les organisations qui, comme  OpenAI  ou Google,  peuvent mobiliser plus de puissance encore, et ce pendant plusieurs  mois.  ​ 

Au-delà des remarquables aptitudes d’induction et de génération des  LLM,  ChatGPT  se distingue par la qualité, l’objectivité et la clarté de ses  réponses (même s’il arrive d’être mis en défaut). Ceci tient aux  spécificités de la phase d’optimisation et de spécialisation du modèle, sur  laquelle  OpenAI  reste très discret, mais qui a sans doute impliqué de très  nombreux échanges avec des opérateurs humains. Cet apprentissage  actif nécessite lui aussi des moyens très importants pour parvenir à  rapprocher le comportement du LLM des réflexes conversationnels d’un  individu en chair et en os. Par exemple, un LLM est très perméable aux  contenus toxiques, qu’on est bien obligé de lui montrer si on veut pouvoir  lui dire ensuite de les éviter ! Et plus le modèle est vaste, plus il est  vulnérable, de sorte qu’il peut devenir contradictoire de vouloir des  réponses qui soient riches, mais aussi sans risques.  ​ 

Fondés sur des principes assez simples, **les LLM ont des capacités** **impressionnantes** qu’illustre avec éclat  ChatGPT  . Pour atteindre son  niveau de sophistication, ce dernier a néanmoins bénéficié de  moyens  hors de portée de la plupart des organisations. Comme le montre  cependant  LLaMa  , on peut obtenir des résultats très satisfaisants avec  des ressources plus modestes et faire du LLM un outil d’entreprise, dans  le cadre de limitations connues et acceptées en amont.  ​ 

* * *

![Armand Joulin ](https://www.quantmetry.com/wp-content/uploads/2023/07/armand-joulin.jpeg)

[ Armand Joulin  ](https://www.linkedin.com/in/armand-joulin-0274254/)

Ex-Directeur de recherche chez FAIR, Meta 
