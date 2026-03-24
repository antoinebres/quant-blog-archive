# directions-financieres-data-science
Wayback Machine URL: https://web.archive.org/web/20230606104048/https://www.quantmetry.com/blog/directions-financieres-data-science/
Archive date: 2023-06-06

Time Series 

07/04/2020 

#  Les directions financières à l'heure de la Data Science 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fdirections-financieres-data-science%2F&title=Les%20directions%20financi%C3%A8res%20%C3%A0%20l%27heure%20de%20la%20Data%20Science "Linkedin") [ ](http://twitter.com/intent/tweet?text=Les%20directions%20financi%C3%A8res%20%C3%A0%20l%27heure%20de%20la%20Data%20Science&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fdirections-financieres-data-science%2F "Twitter") [ ](https://www.quantmetry.com/blog/directions-financieres-data-science/ "Email") [ ](https://www.quantmetry.com/blog/directions-financieres-data-science/ "Copy Link")

* * *

Temps de lecture : 7 minutes 

![Quantmetry.com : Les directions financières à l'heure de la Data Science](https://quantmetry.b-cdn.net/wp-content/uploads/2020/04/capture-decran-2020-04-16-a-16-01-56.png)

✍ [ Guillaume Hochard ](https://www.linkedin.com/in/guillaume-hochard-phd-5580589/) , [ Victor Gouin ](https://www.linkedin.com/in/victor-gouin-38874b/) et [ Guillaume Besson ](https://www.linkedin.com/in/gbesson/) / Temps de lecture : 7 minutes. 

#####  Les directions financières passent encore 80% de leur temps à produire la donnée et seulement 20% du temps à l’analyser. 

Un sondage du cabinet PwC en 2019 a mis en lumière le fait que la majorité des directeurs financiers estimaient que leurs équipes passaient plus de 80% de leur temps à produire de la donnée, pour ne passer que moins de 20% à les analyser. 

La finance d’entreprise est en effet un secteur historiquement riche en données. Si la croissance des volumes de données a bénéficié à ce secteur, en lui permettant de produire des analyses toujours plus nombreuses et plus fines, les traitements habituels ne sont plus adaptés à l’explosion des volumétries de données constatées au cours de ces dernières années. 

De plus, l’environnement économique étant de plus en plus complexe, incertain et mouvant, les prévisions financières sont confrontées à un triple enjeu : bien sûr une robustesse accrue de la prévision, mais aussi la capacité à être mise à jour rapidement et régulièrement, ainsi que la capacité à expliquer ses résultats. 

#####  La Data Science permet de proposer rapidement des prévisions fiables et intelligibles. 

Dans ces montagnes de données, de tableaux croisés et de reporting financiers, se cachent des informations qui, mieux exploitées, peuvent être génératrices de valeur. L’analyse de séries temporelles (c.a.d. de toute valeur indexée par le temps) croisées à des données internes à l’entreprise, mais aussi externes (données open-data, non collectées par l’entreprise) peut être utilisée selon trois axes, tous porteurs de valeur : 

  1. **Prévoir,** améliorer les prévisions et l’adaptabilité de celles-ci, avec un choix de modélisation assurant la fiabilité, la rapidité, la précision et l’intelligibilité des prévisions du modèle. Sur ces 4 axes, nous avons développé une méthodologie éprouvée permettant : 
     * **Fiabilité :** des prévisions robustes reposant sur de multiples variables, internes ou externes, et sur de meilleurs modèles de prévisions (statistiques & Machine Learning) 
     * **Rapidité** : des prévisions disponibles en quelques minutes, mises à jour régulièrement (quotidienne, hebdomadaire, mensuelle, trimestrielle) ou à la demande selon le besoin métier 
     * **Précision** : des prévisions précises, décomposées à différentes mailles (temporelle, géographique, segment client, …) selon les besoins d’analyses 
     * **Intelligibilité** : des prévisions interprétables où le poids de chaque variable est évalué et compréhensible, ce qui est indispensable pour s’affranchir de la complexité naturelle de ce type d’analyse. 
  2. **Expliquer (le passé)** : la compréhension du passé est incontournable pour rendre intelligible les prévisions du modèle mis en place, et comprendre les écarts entre les prévisions passées et la réalité. 
  3. **Décider** : sur la base de ces prévisions, le métier va pouvoir agir, prendre des décisions. Afin d’ **optimiser cette prise de décision** , la fourniture des intervalles de confiance permettent de prendre en compte l’incertitude sur la prévision et de pondérer le risque, en particulier dans les problèmes asymétriques (par exemple, quel est le coût de commander à tort une pièce de rechange et de la stocker par rapport au coût d’immobilisation d’un matériel si cette pièce n’est pas disponible). Ainsi, exprimer les coûts associés à chaque décision est indispensable pour piloter son activité dans une démarche _Data & ROI driven _ . 
  4. **Anticiper :** un modèle de prévision peut également être utilisé pour **anticiper** certaines situations difficiles à prévoir, en **simulant des scénarios et en étudiant leur impact sur les risques** . Pour ce faire, il est possible de prendre en compte l’incertitude sur les variables explicatives via des **analyses de sensibilité** et de créer des **scénarios alternatifs** , également appelés « what-if scenarios », simulant une situation optimiste, pessimiste, ou un entre deux. 



#### 

#####  Les spécificités d’un projet pour une Direction Financière vues par notre expert Prévisions et Séries Temporelles 

Pour illustrer cette démarche en quatre temps, [ Guillaume Hochard, ](https://www.linkedin.com/in/guillaume-hochard-phd-5580589/) expert en séries temporelles, nous donne son retour d’expérience sur un projet de prévision financière réalisé pour une Direction Financière. 

######  Bonjour Guillaume, peux-tu nous raconter ta dernière mission avec une direction financière ? 

Oui bien sûr ! Une direction financière souhaitait prévoir son chiffre d’affaires mois par mois, sur un horizon de 16 mois, sur chacun de ses secteurs d’activités. En effet, les prévisions de chiffre d’affaires sont réalisées début septembre pour l’atterrissage à l’année N, et pour déterminer le budget global du groupe de l’année N+1. 

######  Reprenons nos 4 axes : tout d’abord concernant la capacité de prévision, as-tu réussi à développer un modèle de prévision plus performant ? 

Cela n’a pas été simple, car le modèle utilisé actuellement par le client était déjà particulièrement performant, mais oui nous avons réussi à réduire l’erreur de prévision de manière notable ! 

######  Quels ont été les challenges en terme de prévision ? 

Pour un expert data, le challenge principal a été d’identifier les données pertinentes et tirer parti de l’expérience métier pour la traduire en variables explicatives pouvant entrer dans la modélisation. Le choix du modèle est quand à lui aussi capital, car il doit être intelligible pour que les prévisions puissent être analysées, décomposées, comprises et utilisées par le métier. De plus, en complément, il est capital de fournir un intervalle de confiance autour des prévisions, caractérisant l’incertitude du modèle et l’incertitude sur certaines variables explicatives dont la valeur dans le futur est incertaine (par exemple, la valeur d’un indicateur type PIB ou PIM n’est pas connue avec certitude 16 mois à l’avance). 

######  Comment as-tu sélectionné les données et le modèle de prévision ? 

En complément de son patrimoine de données, basé sur l’historique de son chiffre d’affaire réalisé les années précédentes, il est possible d’analyser la série temporelle augmentée de données exogènes pour réaliser des prévisions, à l’aide de méthodes statistiques (par exemple : les méthodes SARIMAX ou VARMAX peuvent être de bons candidats pour la modélisation), de méthodes de _Machine Learning_ (par exemple, les forêts aléatoires ou le _gradient boosting_ ) ou pourquoi pas, si le volume de données le permet une approche _Deep Learning_ (nb: il faut au moins 300 à 400 séries temporelles pour utiliser par exemple, avec un niveau de performance correct, l’algorithme DeepAR – [ retrouvez notre article sur cet algorithme ici ](https://www.quantmetry.com/previsions-probabilistes-deepar/) ). 

À l’aide des données historiques et des données exogènes (données météorologiques par exemple), il est possible d’expliquer certains pics de chiffre d’affaire ou de mettre en évidence des journées ayant été impactées par des conditions météorologiques sévères (chutes de neige, tempête, …). 

######  Les nouveaux modèles de prévisions se doivent d’être réactifs : comment cela s’est traduit avec ce modèle ? 

La mise à jour des prévisions peut être effectuée chaque mois, en intégrant les résultats réalisés et en ré-entraînant le modèle, afin de fournir des corrections aux prévisions réalisées précédemment. Des corrections sur les variables explicatives incertaines (par exemple, valeur du PIB au troisième et quatrième trimestres) peuvent également être intégrées au modèle afin de fournir des prévisions ajustées. A ce sujet, je prépare un article dédié à la prévision en temps de crise qui sera bientôt publié sur le blog. 

######  Concernant l’axe 2, l’explication : qu’est-il possible de faire avec ce modèle ? 

Le modèle de prévision mis en place, nous avons utilisé des outils d’interprétabilité afin d’expliquer chaque prévision du modèle et de la décomposer en contributions des variables explicatives ( [ pour en savoir plus, retrouvez notre article de blog sur ce sujet ici ](https://www.quantmetry.com/intelligibilite-dun-modele-lie-un-dispositif-cle-de-la-conformite/) ). Ceci permet d’expliquer les écarts entre les prévisions et le chiffre d’affaire réalisé, en identifiant par exemple des effets calendaires spécifiques (position d’un jour férié dans le mois, position des vacances par rapport à un jour férié, …) qui peuvent avoir un impact sur l’activité de l’entreprise. 

######  Concernant les axes 3 et 4 (décider et anticiper) : peux-tu nous dire si le modèle permet ce type d’analyses ? 

Oui ! Le modèle est également utilisé à des fins de gestion des risques, en estimant les écarts de chiffres d’affaires réalisés sous des hypothèses optimistes, pessimistes, ou iso par rapport à l’année en cours. La génération de prévisions sous ces différentes hypothèses permet de mieux gérer l’incertitude et de réaliser les arbitrages financiers nécessaires, en connaissance des risques. Par exemple, il est possible de générer des prévisions afin de mesurer quel impact peut avoir une incertitude sur une croissance du PIB de 1% ou de 1,5% sur le chiffre d’affaire global. 

#####  Vers un 80/20 en faveur de l’analyse de données ! 

La fonction finance d’entreprise est un secteur clé de l’entreprise, qui aide l’ensemble des autres fonctions de l’entreprise à prendre les bonnes décisions au bon moment, à partir des analyses produites. 

Notre sentiment est que le contexte économique actuel va encore renforcer cette responsabilité dans les années à venir et que les directions financières, qui reposent trop souvent sur des outils et des méthodes de captation et de traitement de données encore peu optimisés, vont devoir évoluer progressivement. 

La Data Science devient alors un allié de choix pour répondre à ces problématiques, en ouvrant la voie à des prévisions non seulement plus fiables, rapides et détaillées, mais en proposant également des outils d’analyses complémentaires (intervalles de confiance, what if scénarios, …). 

Il deviendrait alors totalement envisageable qu’elles consacrent 80% de leur temps à analyser les données d’ici quelques années ! 

#####  ✍ [ Guillaume Hochard ](https://www.linkedin.com/in/guillaume-hochard-phd-5580589/) , [ Victor Gouin ](https://www.linkedin.com/in/victor-gouin-38874b/) et [ Guillaume Besson ](https://www.linkedin.com/in/guillaumebesson/)
