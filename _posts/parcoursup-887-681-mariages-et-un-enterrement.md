# parcoursup-887-681-mariages-et-un-enterrement
Wayback Machine URL: https://web.archive.org/web/20221001012312/https://www.quantmetry.com/blog/parcoursup-887-681-mariages-et-un-enterrement/
Archive date: 2022-10-01

Uncategorized 

07/06/2018 

#  Parcoursup : 887 681 mariages et un enterrement ? 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fparcoursup-887-681-mariages-et-un-enterrement%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Parcoursup%20%3A%20887%20681%20mariages%20et%20un%20enterrement%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fparcoursup-887-681-mariages-et-un-enterrement%2F "Twitter")

* * *

Temps de lecture : 11 minutes 

![Quantmetry.com : Parcoursup : 887 681 mariages et un enterrement ?](https://quantmetry.b-cdn.net/wp-content/uploads/2018/06/image.png)

Le 21 mai, le gouvernement a publié le code source de l’algorithme de Parcoursup, la nouvelle plateforme qui permet d’affecter les bacheliers vers les filières de l’enseignement supérieur. Cette plateforme, lancée au début de l’année, prend la place du système d’affectation Admission Post-Bac (alias APB). 

Que peut-on apprendre de l’algorithme Parcoursup ? En quoi diffèrent les plateformes Parcoursup et APB ? Nous tâcherons dans cet article de proposer quelques éléments de réponse à ces questions. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/1.png)

####  **Présentation de la plateforme :**

Parcoursup est donc la nouvelle plateforme dédiée à l’accueil, et à l’affectation des lycéens vers les différentes filières de l’enseignement supérieur. Ce nouveau système arrive après les critiques portées à APB, notamment à la suite de l’usage de tirages aléatoires pour sélectionner les lycéens dans certaines formations dites en “tension”, expression qui désigne les formations pour lesquelles il y a plus de candidatures que de places disponibles (comme par exemple les filières STAPS ou Psychologie). 

À l’échelle des lycéens, beaucoup de choses changent avec Parcoursup. On notera notamment que : 

  * le nombre de voeux de filières passe de 24 pour APB à 10 pour Parcoursup (mais avec possibilité de regrouper ses voeux en prépas, médecine, …) 

  * un nouveau système “d’attendus” entre en place, permettant aux élèves d’accéder à une filière sous réserve d’effectuer un complément de formation (le fameux “oui si” qui s’ajoute aux réponses possibles des élèves) 

  * il n’y a plus de hiérarchisation des voeux : contrairement à APB, un lycéen peut maintenant être accepté dans plusieurs formations en même temps, et pas uniquement dans son voeux le mieux classé, ce qui permet à l’élève de prendre une décision après les résultats d’admission (dans un délais limité). 




L’objectif avec Parcoursup est donc de s’affranchir des problèmes relevés sur APB, mais pas seulement : Parcoursup se veut être une plateforme lisible, claire, transparente. C’est dans ce sens que le code source de la plateforme a été publié. 

Avant de rentrer dans le code de la nouvelle plateforme, et afin de mieux comprendre les motivations derrières ces changement, penchons-nous dans un premier temps sur la mécanique derrière le prédécesseur de Parcoursup : Admission Post-Bac. 

####  **L’algorithme APB : à la recherche des mariages (presque) stables**

Derrière la plateforme d’affectation APB, se cache un algorithme répondant à un problème bien connu en théorie des jeux : celui des “mariages stables”. Ce problème d’affectation se présente de la manière suivante : 

Soit deux ensembles A et B à n éléments chacun. Pour chaque élément de A et de B, on a une fonction de préférence qui permet de classer tous les éléments de l’autre ensemble. On cherche alors un appariement stable, c’est à dire un appariement tel que, après appariement, il n’existe aucun couple a et b d’éléments respectivement de A et B tel que a préfère b à l’élément auquel il est apparié, et b préfère a à l’élément auquel il est apparié. 

Ce problème tient son nom d’un exemple, dans lequel on chercherait à mettre en couple n hommes et n femmes, de manière stable. 

Le problème de mariages stables a été proposé en 1962 par deux mathématiciens et économistes : David Gale et Lloyd Shapley. Ces deux scientifiques ont proposé un algorithme permettant de trouver une solution au problème, et ont de surcroît prouvé que cet algorithme menait toujours à une solution stable. 

Ci-dessous, l’algorithme de Gale-Shapley en pseudo-code (dans un “contexte APB”) : 

  1. Initialiser tous les élèves e∈E et toutes les universités u∈U à “sans affectation” 

  2. Pour un élève e∈E sans affectation, soit u son université préférée : 

     * Si u est libre, affecter e à u 

     * Si un autre élève e’∈E est déjà affecté à u : 

       * Si u préfère e à e’, affecter e à u (e’ devient sans affectation) 

       * Sinon, e reste sans affectation et on retire u des préférences de e 

  3. Répéter jusqu’à ce que chaque élève e∈E ait une affectation 




Afin d’illustrer cet algorithme, considérons l’exemple suivant : 

Gaultier, Marc et Pablo s’apprêtent à rentrer dans l’enseignement supérieur. Dans le cas de notre exemple, l’enseignement supérieur se compose de 3 écoles, n’offrant qu’une place chacune : l’école Polytechnique (X), l’école des Mines (M) et SupOptique (S). Voici les préférences de nos étudiants, et leur classement au sein de chaque école : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/2.png)

On commence l’algorithme avec Marc : son vœu préféré est X, qui est disponible, donc on l’y affecte. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/3.png)

On continue maintenant avec Gaultier : le vœu préféré de Gaultier est X, mais X est déjà affectée à Marc, donc il faut regarder les préférences de X. Malheureusement pour Gaultier, X préfère Marc, on retire donc X de la liste des vœux de Gaultier et on recommence son tour : son nouveau vœu préféré est M, qui est disponible, donc on affecte Gaultier à M. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/4.png)

On finit avec Pablo, dont le vœu préféré est S. Comme S est disponible, on y affecte Pablo, et l’algorithme se termine. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/5.png)

Concernant cet algorithme, il est bon de savoir que : 

  * la solution donnée par l’algorithme est unique, peu importe l’ordre avec lequel on traite les candidats/universités 

  * le problème de mariage stable en revanche n’a pas nécessairement de solution unique 

  * la solution proposée par l’algorithme n’est pas nécessairement optimale pour tout le monde 




L’exemple précédent illustre les deux derniers points : par exemple, une autre solution au même problème est : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/6.png)

Cette solution est encore stable, mais est cette fois-ci optimale pour les universités, là où la solution précédente l’était pour les étudiants. L’algorithme assurera en fait toujours de trouver la solution optimale parmi toutes les solutions stables pour le groupe avec lequel on démarre l’algorithme (dans notre exemple, les étudiants). 

**NB** : dans notre exemple, on considère que chaque filière ne possède qu’une seule place afin de reproduire le schéma original d’un problème de mariages stables, mais ce dernier peut très facilement se généraliser au cas d’un problème d’affectation comme celui de APB. 

Revenons-en à APB. Comme nous venons de le voir, l’algorithme de Gale-Shapley est censé proposer une solution stable, et potentiellement optimale pour au moins un des partis. Pourquoi se retrouve-t-on alors à avoir des élèves tirés aléatoirement lors des phases d’affectations, et avec des affectations qui ne semblent finalement optimales pour personne ? 

La réponse est que dans la réalité, les postulats de base du problème de mariages stables ne sont pas respectés, car en effet : 

  * les préférences des élèves ne portent pas sur l’ensemble des filières du supérieurs, mais seulement sur un nombre limité d’entre elles : on peut donc se retrouver avec des problèmes d’affectation sur des sous-ensembles de filières et d’élèves de tailles différentes, et ainsi se retrouver avec des filières avec trop (ou trop peu) de demandes 

  * les élèves n’expriment pas librement leurs préférences : une filière en tension ne sera proposée à un élève “que si elle est classée dans les premiers vœux du candidat, voire en vœu n°1 pour les licences” où la tension est particulièrement importante (PACES, STAPS, droit et psychologie), précisait-on dans le guide du candidat disponible sur la plateforme 




Un tirage aléatoire est donc effectué afin de départager les élèves ex-aequo, dans les filières non-sélectives où le nombre de candidats dépasse le nombre de places libres. 

Ainsi derrière APB, c’est une histoire de mariages stables sous contraintes entre élèves et filières du supérieur qui se joue. Nous avons maintenant les clés pour comprendre la mécanique derrière Parcoursup, alors rentrons dans le vif du sujet ! 

####  **L’algorithme Parcoursup : une histoire de mariages arrangés**

A l’origine des nouveaux algorithmes de Parcoursup, Hugo Imbert, chercheur au CNRS, et Claire Mathieu, informaticienne, mathématicienne et professeure au Collège de France, ont tenté de répondre aux incompréhensions, en partie dues aux près de 400 000 candidats sans affections le premier jour d’ouverture de la plateforme. 

Ils expliquent que de nombreuses décisions techniques concernant les méthodes utilisées pour classer les candidats se sont faites dans le cadre d’un travail collaboratif avec le ministère de l’Éducation, le projet Parcoursup repartant de zéro, sans rien reprendre de APB. La mission des deux chercheurs était de transcrire en algorithme les mesures votées par le parlement dans la loi ORE (Orientation et Réussite des Étudiants). 

Un parcours du code source de Parcoursup permet notamment de constater l’importance de certains des aspects de ces nouvelles mesures, comme par exemple le poids de critères sociaux (taux de boursiers et académie des candidats) dans le classement des candidats. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/7.png)

un (petit) morceau de l’algorithme Parcoursup (la reste du code est disponible [ ici ](https://framagit.org/parcoursup/algorithmes-de-parcoursup/blob/master/java/parcoursup/ordreappel/algo/GroupeClassement.java) ) 

Un premier classement se base en fait sur des critères pédagogiques, puis un second sur des critères sociaux, nous expliquent les développeurs de l’algorithme. Ainsi, après un premier classement sur des critères pédagogiques, des élèves peuvent voir leur candidature monter dans le classement initial afin qu’une formation atteignent un taux minimum de boursiers, ou un taux minimum de résidents. Un autre arbitrage doit aussi venir se faire quant à la question des internats, explique Claire Mathieu. 

Quid de la fin de la hiérarchisation des voeux ? Cette dernière nouveauté représente un changement majeur dans la manière dont fonctionnait APB. Cette nouveauté va dans le sens des lycéens, dans la mesure où cela leur permet de ne plus avoir à classer leurs voeux de manière stratégique, plutôt que selon leurs vraies préférences, car : 

  * comme nous l’avons montré, les lycéens ne peuvent pas établir leurs préférences librement lorsque ces derniers impliquent des filières en tension 

  * en pratique, nous (les humains de la réalité) ne nous comportons pas de manière aussi rationnelle que nos homologues théoriques (les agents rationnels de la théorie des jeux) : “je peux préférer A à B, B à C, mais toutefois C à A », explique Hugo Gimbert. 




Cette question de stratégie intervient notamment dans le cas des étudiants à la recherche d’un internat, comme c’est le cas des élèves postulant à des classes préparatoires : est-ce qu’un étudiant préfère aller dans une prépa bien classée sans internat ou dans une prépa moins bien classée mais avec internat ? 

Néanmoins, ce poids qui se libère sur les épaules des lycéens se fait remplacer par un poids peut-être plus pénible encore : celui de l’attente sans affectation. Comme dit plus haut, plus de 400 000 étudiants, soit à presque la moitié, se retrouvaient sans affectation le jour d’ouverture de la plateforme, là où 653 000 (environ 80% des candidats) avait au moins une proposition à l’ouverture de la phase des réponses de APB, le 8 juin 2017. 

La hiérarchisation des vœux avec APB avait en fait l’effet de faire se libérer plus rapidement des places “occupées” par des élèves admis dans leurs premiers vœux. Reconsidérons l’exemple précédent : 

Marc postule dans cet ordre de préférence à l’école Polytechnique, l’école des Mines et SupOptique, et est admis dans chacun de ses vœux. Dans le système Parcoursup, Marc dispose de plusieurs jours pour se décider, occupant ainsi une place dans chacune de ces formations et mettant donc sur listes d’attente d’autres élèves, jusqu’à ce qu’il se décide de choisir une formation pour libérer une place dans les deux autres : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/8.png)

Tant que Marc ne se décide pas, il monopolise une place dans X, M et S, mettant des élèves sur liste d’attente dans chacune de ces filières 

Avec APB, Marc est directement affecté à son premier vœu, et n’occupe à aucun moment une place dans les autres formation auxquels il a postulé et a été accepté : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/9.png)

APB affecte directement Marc à X, son premier choix, même s’il était accepté à M et S. Les places réservées à Marc dans ces établissements sont automatiquement libérées. 

Allons plus loin dans la comparaison avec APB : nous avons vu que l’algorithme derrière APB répond à un problème de mariages stables ; qu’en est-il de l’algorithme Parcoursup ? Peut-on encore parler de problème de mariage stable si les élèves n’expriment plus leurs préférences ? 

En fait oui, mais cette fois-ci le schéma est plus subtil : dans un problème de mariages stables “classique”, les candidats classeraient leurs formations et les formations classeraient leurs candidats, puis après convergence de l’algorithme on obtiendrait une affectation. « Mais la différence”, explique Claire Mathieu, “c’est que quand en cours de route il y a besoin de savoir la préférence d’un candidat entre deux formations, pour avoir la répo 
