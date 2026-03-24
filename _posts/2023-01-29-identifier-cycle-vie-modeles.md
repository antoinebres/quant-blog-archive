---
layout: post
title: identifier-cycle-vie-modeles
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129161011/https://www.quantmetry.com/blog/identifier-cycle-vie-modeles/
---
Data Gouvernance 

27/01/2020 

#  Trois questions pour identifier son cycle de vie des modèles 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fidentifier-cycle-vie-modeles%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Trois%20questions%20pour%20identifier%20son%20cycle%20de%20vie%20des%20mod%C3%A8les&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fidentifier-cycle-vie-modeles%2F "Twitter")

* * *

Temps de lecture : 15 minutes 

![Quantmetry.com : Trois questions pour identifier son cycle de vie des modèles](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/article-gma-min-1.png)

✍ [ Grégoire Martinon / ](https://www.linkedin.com/in/gregoire-martinon/) _Temps de lecture : 20 minutes._

[ IA en production [1] ](https://www.quantmetry.com/les-livres-blancs/) , ce n’est pas une mince affaire. Dans nos précédents articles, nous avons détaillé quels étaient les grands principes de l’ [ industrialisation [2] ](https://www.quantmetry.com/projet-ia-kit-survie-production/) et du [ cycle de vie des modèles en production [3] ](https://www.quantmetry.com/premier-etape-cycle-vie-modeles/) . En pratique, il existe cependant plusieurs manières de suivre cette feuille de route, en s’adaptant aux contraintes de chacun. Il n’y a donc pas un mais plusieurs cycles de vies. Comment choisir ? Quelles sont les questions à se poser pour identifier son cycle de vie ? 

_Quelles sont les questions à se poser pour identifier son cycle de vie ?_

##  Non pas un, mais des cycles de vie 

Le cycle de vie se structure autour de **trois axes principaux** , qui permettent de caractériser le besoin du processus métier visé : le niveau de service, la vitesse de dérive et le degré d’autonomie (voir Figure 1). 

  * **Le niveau de service.** C’est le [ _Service Level Agreement_ (SLA) [4] ](https://en.wikipedia.org/wiki/Service-level_agreement) du modèle. Il est d’autant plus élevé que la vitesse et le volume des prédictions sont élevés. Il est également d’autant plus élevé que le coût de l’indisponibilité du modèle est élevé. 
  * **La vitesse de dérive.** C’est la fréquence caractéristique de mise à jour nécessaire du modèle. Elle est d’autant plus élevée que les données et la cible de prédiction évoluent rapidement. Elle doit être comparée à la vitesse et au coût d’acquisition des labels pour savoir si l’adaptation est triviale ou non. 
  * **Le degré d’autonomie.** C’est la capacité du modèle à prendre les décisions seul. Il est d’autant plus élevé que la chaîne de décision est courte, peu bureaucratique et automatisée. Il est également lié à la capacité de l’humain à remplacer l’algorithme. 



![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/trois_axes.png)

Figure 1 : les trois axes structurant le cycle de vie des modèles. Le niveau de service est lié au volume de prédictions, la vitesse de dérive à la volatilité des sources de données, et le degré d’autonomie à la complexité bureaucratique de la chaîne de décision. 

##  Trois questions… 

Afin de simplifier les choses, on peut sonder chacun de ces trois axes avec une question fermée (voir Figure 2). Pour chacune de ces questions il existe donc deux réponses possibles “oui” ou “non”. Ces questions se posent pour chaque couple entreprise – cas d’usage. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/questions-1.png)

Figure 2 : les trois questions posées par le cycle de vie des modèles en production, avec des exemples de réponses possibles. Chaque question interroge l’un des trois axes décrits précédemment : niveau de service, vitesse de dérive et degré d’autonomie. 

> _Pensez très fort à votre cas d’usage : êtes-vous capable de répondre à ces trois questions ?_
> 
> C’est un exercice mental intéressant à faire en lisant cet article : penser à un cas d’usage dans votre entreprise et répondre aux trois questions de la figure 1 par oui ou par non : 
> 
>   * Devez-vous prédire à une cadence élevée en toutes circonstances ? 
>   * Vos données ou votre cible sont-elles extrêmement volatiles dans le temps ? 
>   * L’algorithme prend-il ses décisions seul ? 
> 

> 
> **Faites le quizz maintenant en cliquant sur[ ce lien ](https://quantmetry860.outgrow.us/quizz-ia-en-production) ! **
> 
> _Question technique :_ à votre avis, en posant ces trois questions, combien de typologies de cycles de vie avons-nous défini ? 

##  …Huit réponses 

Bien vu ! Trois réponses binaires définissent huit possibilités (voir Figure 4 et Figure 5). Dans la suite de cet article, nous allons donner quelques **éléments d’implémentation du cycle de vie des modèles** propres à chacune de ces typologies avec des exemples de cas d’usage. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/arbre.png)

Figure 3 : trois questions, huit réponses. En réalité, c’est simplement un arbre de décision qui permet d’identifier huit typologies de cycle de vie des modèles, que nous allons détailler par la suite. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/cube.png)

Figure 4 : Visualisation alternative de l’arbre de décision cycle de vie des modèles. On a représenté les trois axes structurants : niveau de service, vitesse de dérive et degré d’autonomie. L’arbre de décision n’est rien d’autre qu’une partition de l’espace. Le code couleur est le même que sur la figure 3. 

##  Non, non et non : l’exemple de l’octroi de crédit 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/cube1-358x340.png) ![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/tableau1-500x185.png)

Vous êtes par exemple une banque qui met en production des **modèles d’octroi de crédit immobilier** . Les prédictions sont sporadiques mais avec des enjeux financiers énormes. 

D’un point de vue organisationnel, c’est tout le [ _model risk management_ [5] ](https://www.bankingsupervision.europa.eu/ecb/pub/pdf/trim_guide.en.pdf) qui va permettre de faire passer à vos modèles un vrai contrôle technique, avec une séparation des compétences en (1) une équipe de modélisation, qui doit optimiser la performance, et (2) une équipe de validation, qui doit optimiser la robustesse. L’optimisation jointe de ces deux objectifs antagonistes permet de **maximiser le pouvoir prédictif tout en minimisant les risques** . 

D’un point de vue scientifique, c’est la [ notion d’incertitude [6] ](https://machinelearningmastery.com/randomness-in-machine-learning/) , de biais et de robustesse qui va monopoliser votre savoir-faire. Vous allez privilégier des modèles simples, faciles à maintenir, stables dans le temps et [ intelligibles [1] ](https://www.quantmetry.com/les-livres-blancs/) . L’objectif est **d’anticiper et de quantifier les risques** longtemps à l’avance afin de provisionner le budget qui permet de répondre au pire scénario. 

D’un point de vue technologique, et en réponse au processus de validation interne, vous devez être capable d’auditer vos modèles passés, et de revenir à la version précédente de modélisation en conditions identiques (données, code, modèle, infrastructure). Au-delà de la robustesse de votre modèle, la robustesse de votre chaîne de traitement est garantie par l’utilisation de [ tests unitaires [7] ](https://research.google/pubs/pub46555/) sur la [ qualité de la donnée [8] ](https://github.com/tdda/tdda) , du modèle et du code. 

##  Non, non et oui : l’exemple du marketing digital 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/cube2-358x340.png) ![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/tableau2-500x185.png)

Vous êtes par exemple une assurance, avec un nombre limité et stable d’offres à vendre. Vous cherchez par exemple à **calculer un score d’appétence** qui débouchera sur l’envoi d’une newsletter ou d’une publicité. Le cycle de vie est sporadique, et les enjeux sont suffisamment faibles pour automatiser le processus rapidement. 

D’un point de vue organisationnel, c’est le métier qui doit piloter le modèle. Les itérations de modèles se font sur la base des retours terrains et de la politique commerciale. En l’occurrence, le modèle donne aussi un retour sur l’appétence de la clientèle, c’est un sondage. 

D’un point de vue scientifique, le _monitoring_ du modèle se fait par décompte des ouvertures de mails ou de temps passé devant la publicité. L’intelligibilité du modèle va vous permettre de **mieux comprendre les populations ciblées** par le modèle et d’itérer avec l’expertise métier au rythme des campagnes publicitaires. L’apprentissage par renforcement, combiné à une segmentation client, permet d’identifier rapidement des groupes de répondants réagissant positivement à certaines sollicitations. 

D’un point de vue technologique, le marketing digital se prête naturellement bien aux séquences d’ [ _A/B testing_ [9] ](https://thenewstack.io/deployment-strategies/) . Le monitoring gagne en efficacité s’il est **automatisé** à l’aide d’un _dashboard_ de suivi qui permet d’analyser et de segmenter les résultats de manière dynamique. 

##  Non, oui et non : l’exemple de la rétention client 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/cube3-358x340.png) ![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/tableau3-500x185.png)

Vous êtes orienté Business To Customer (B2C) ou Business To Business (B2B) et vous voulez **réaliser des campagnes de rétention** (offres promotionnelles, rendez-vous avec des conseillers) pour empêcher vos clients de partir. Vous avez un fort enjeu de connaissance client et devez faire face à la volatilité du marché, directement influencé par vos concurrents et par des événements imprévisibles (mode, politique). 

D’un point de vue organisationnel, c’est la [ data gouvernance [10] ](https://www.quantmetry.com/gouvernance-data-aventure-humaine/) qui va vous permettre d’agréger toute la connaissance client disséminée dans vos systèmes d’information. De plus, l’expertise métier est centrale dans la mesure où c’est elle qui va vous renseigner sur les scénarios d’attrition client, c’est donc le métier qui doit porter le projet. Il y a également un **réel enjeu d’acculturation du métier à la donnée** , afin d’améliorer la qualité des données saisies la plupart du temps à la main. 

D’un point de vue scientifique, vous devez traduire les scénarios métiers en variables explicatives via du _feature engineering_ . Il y a un premier enjeu d’ [ intelligibilité [1] ](https://www.quantmetry.com/les-livres-blancs/) du modèle et donc de **sélection de variables pertinentes** et parlantes au métier, l’objectif étant de convertir les prédictions du modèle en un argumentaire actionnable par le métier. Il y a un deuxième **enjeu de stabilité** du modèle, qui doit être réévalué régulièrement sur un historique récent qui colle à l’actualité et au dynamisme du secteur d’activité. 

D’un point de vue technologique, il y a un enjeu très fort de centralisation des données et d’évaluation de la [ qualité de la donnée [8] ](https://github.com/tdda/tdda) , qui peut être réalisé sur un DataLake ou directement sur le cloud. Il s’agit également de rendre accessibles les prédictions du modèle à tous les acteurs métiers, via un _dashboard_ partagé de restitution des résultats. 

##  Non, oui et oui : l’exemple de la réponse automatique de mails 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/cube4-358x340.png) ![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/tableau4-500x185.png)

Vous êtes une mutuelle ou une compagnie d’assurance, et vous devez gérer des pics de mails à certaines périodes de l’année. Par exemple à la rentrée scolaire, beaucoup de clients vous réclament des attestations scolaires, et vous voudriez **automatiser la réponse à ces mails spécifiques.** Par contre, les mails de ce type s’estompent avec le temps. 

D’un point de vue organisationnel, vous devez définir précisément quels sont les mails concernés par la réponse automatique, et quelle est la tolérance aux erreurs (faux positifs et faux négatifs). Le risque le plus élevé est d’ignorer certains mails et de générer de la friction client. 

D’un point de vue scientifique, vous devez définir un **mécanisme d’abstention de réponse automatique** en cas de doute ou en cas d’intention multiple (demande d’attestation et de remboursement par exemple). L’incertitude du modèle permet alors de nourrir ce mécanisme. Par ailleurs, les types de mails peuvent évoluer d’une année sur l’autre, ou d’un périmètre à un autre, avec des volumes de données labellisés insuffisants. L’ [ adaptation de domaine [11] ](https://arxiv.org/abs/1812.11806) permet d’ajuster votre modèle à différents segments aux labels inégaux (langue, période de l’année). Le _monitoring_ doit se faire sur la base des relances émises par les clients. 

D’un point de vue technologique, le modèle doit pouvoir **répondre en temps réel** à des mails qui arrivent au compte-goutte. Cela nécessite donc de _packager_ le modèle et de le déployer sur un serveur, par exemple avec [ MLflow [12] ](https://mlflow.org/) . Qui plus est, l’automatisation rend indispensable la mise en œuvre des bonnes pratiques de [ _CI/CD_ [13] ](https://martinfowler.com/articles/cd4ml.html) , que ce soit sur le prétraitement des mails ou sur le code de déploiement du modèle. 

##  Oui, non et non : l’exemple de la prévision de demande 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/cube5-358x340.png) ![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/tableau5-500x185.png)

Vous êtes une entreprise de prêt-à-porter et vous devez **prévoir jour après jour** la quantité de vêtements à stocker dans vos entrepôts disséminés sur tout le continent. Les prévisions du modèle impactent directement les stocks et donc le chiffre d’affaires. Dans votre stratégie, vous avez un réseau de validation et d’ajustement manuel des prédictions à la maille locale qui prend en compte des considérations spécifiques de transport, de prestataire, de territoire. 

D’un point de vue organisationnel, le rythme soutenu de production déplace la responsabilité du modèle vers la DSI. La **mixité des équipes** tant sur le plan Data Science que Data Engineering va vous permettre d’être réactif et d’assurer une bonne **réactivité en toutes circonstances** . Les prédictions de vos modèles sont fréquentes 
