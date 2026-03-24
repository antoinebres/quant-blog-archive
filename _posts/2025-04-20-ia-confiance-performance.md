---
layout: post
title: ia-confiance-performance
date: 2025-04-20
url_wayback_machine: https://web.archive.org/web/20250420004449/https://www.quantmetry.com/blog/ia-confiance-performance/
---
IA de confiance, Machine Learning 

26/04/2023 

#  En intelligence artificielle, performance rime avec confiance 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fia-confiance-performance%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=En%20intelligence%20artificielle%2C%20performance%20rime%20avec%20confiance&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fia-confiance-performance%2F "Twitter") [ ](https://www.quantmetry.com/blog/ia-confiance-performance/ "Email") [ ](https://www.quantmetry.com/blog/ia-confiance-performance/ "Copy Link")

* * *

Auteur : [ Philippe Neveux ](https://www.linkedin.com/in/philippe-neveux/)

Temps de lecture : 6 minutes 

![Quantmetry.com : En intelligence artificielle, performance rime avec confiance](https://www.quantmetry.com/wp-content/uploads/2023/04/logo-performance-scaled.jpeg)

L’intelligence artificielle de Confiance est un sujet que l’on adresse tous les jours chez Quantmetry pour fournir à nos clients des algorithmes de qualité. Ce sujet est traité par l’expertise Reliable AI qui assure la connaissance et l’application de l’état de l’art des 8 thématiques de l’IA de Confiance introduites dans [ cet article ](https://www.quantmetry.com/blog/ia-confiance-decennie/) . La performance est une de ces 8 composantes. ![](https://www.quantmetry.com/wp-content/uploads/2023/04/concepts-performance.png)

#  La performance, à quoi ça sert ? 

La performance est la première thématique qui nous vient à l’esprit lorsqu’on travaille sur un projet IA. On veut savoir à quel point notre algorithme est bon dans la tâche pour laquelle il a été entraîné. Est-ce que mon modèle arrive à déterminer si un client à qui on donne un crédit pourra le rembourser à temps ? Est-ce qu’il arrive à catégoriser des mails pour les communiquer aux experts métiers référents ? Ou encore, est-ce qu’il a la capacité de prévoir un niveau de production en usine pour anticiper le prochain approvisionnement ? 

Un algorithme doit être suffisamment performant pour répondre à la problématique métier qu’il cherche à résoudre. Si un algorithme n’est pas performant il sera nécessairement difficile de lui accorder sa confiance. 

#  La performance, qu’est-ce que c’est ? 

Si nous ouvrons notre dictionnaire Larousse, la performance est : un « résultat obtenu dans un domaine précis par quelqu’un, une machine, etc. Exploit ou réussite remarquable en un domaine quelconque ». Traduit dans le contexte de l’intelligence artificielle, la performance repose sur 3 concepts. 

##  Alignement métier et technique 

Il faut définir une métrique technique pour connaître la performance d’un algorithme indépendamment du cas d’usage métier qu’il cherche à optimiser. On peut comparer la performance de différents algorithmes pour savoir lequel serait, à priori, le plus apte à aider le métier. 

Cette performance est seulement relative pour comparer la performance des algorithmes entre eux, elle ne nous donne aucune information sur la valeur ajoutée du modèle dans le processus métier cible. 

Il faut avoir la capacité de mesurer des performances métiers (un gain de chiffre d’affaires, un nombre de clients convertis, etc) pour s’assurer que les performances du modèle sont bien en adéquation avec la plus-value attendue par le métier. 

##  Contrôle des processus d’évaluation 

Contrôler le processus d’évaluation de l’algorithme, c’est être totalement transparent sur : les hypothèses, les angles morts, les biais de mesures, le contrôle du sur-apprentissage, etc. Ce processus d’évaluation de l’algorithme doit comporter le mode opératoire de mesure de la performance pendant la conception, mais aussi en opération. Comment la performance du modèle en opération est-elle mesurée et contrôlée ? 

Les performances mesurées lors de la conception doivent être les mêmes qu’en opération. 

##  **Benchmarks systématiques**

L’IA est une science expérimentale. Il n’y a aucun fondement théorique sur la bonne performance d’un algorithme. Il faut, en tout temps, comparer l’algorithme à un modèle alternatif pour assurer le gain en performance. 

Ces modèles alternatifs peuvent être des règles métiers simples, des seuils de décision, un tirage aléatoire, un modèle propriétaire, etc. C’est uniquement en comparant ces performances qu’on peut savoir si un modèle est pertinent face à un autre qui serait plus complexe, moins compréhensible, plus difficile à maintenir, ou autre. 

#  La performance, comment l’activer ? 

Afin d’assurer la performance d’un algorithme, trois actions sont à mettre en place dans les projets IA. 

##  **Aligner**

L’objectif est de lister l’ensemble des exigences métiers et les convertir en contraintes techniques. D’un côté, les data scientist auront une vision claire de la performance technique cible. D’un autre côté, les équipes métier sauront à quel point le modèle d’IA les aide lors de la mise en production de celui-ci. Cette liste d’exigences métiers et contraintes techniques doit être accompagnée de métriques et seuils de performance à atteindre ainsi qu’une qualification des coûts des différentes erreurs possibles (financiers, opérationnelles, humains, …). Le document de cadrage fonctionnel et technique est le référentiel documentaire de cette liste d’exigences. 

##  **Évaluer**

Établir un protocole d’évaluation de la chaîne de traitement complète permet d’éviter tout angle mort sur la capacité du modèle d’IA à optimiser le processus métier cible. Pour ce faire, il faut valider l’ensemble de la chaîne (cascade de modèles, pré/post-traitement inclus) sur un jeu de test dédié représentatif de l’environnement cible (postérieur et indépendant du jeu d’entraînement). Cette validation peut se faire à travers un schéma rédigé explicitant le protocole d’évaluation combiné à un code documenté. 

##  **Comparer**

Ajouter de la complexité pour gagner en performance doit avoir du sens. Contrôler et mesurer sa valeur de manière incrémentale est la meilleure méthode pour mesurer la balance gain (performance) / complexité (modèle non-intelligible, complexe à maintenir, à déployer, etc.). On peut alors définir plusieurs modèles alternatifs du plus simple (ex : naïf, aléatoire, règles métiers, linéaire, avec peu de variables) au plus compliqué (modèle ensembliste, deep learning, etc.) et comparer leurs courbes d’apprentissage (performance en fonction de la taille du jeu d’entraînement). Ces différents tests nous amènent à un comparatif documenté des performances des modèles en fonction de leur complexité ainsi que de la volumétrie des données utilisées. 

#  La performance, en vrai ça donne quoi ? 

Prenons un exemple de projet client dans lequel nous avons appliqué ces concepts dans l’octroi de crédit. Ce modèle doit déterminer pour un client un montant maximal tout en contrôlant le risque de l’ensemble des crédits déboursés (si le client à une haute capacité d’emprunt, alors un montant plus élevé lui sera accordé). Il s’agit d’un modèle de classification binaire pour un montant donné : oui/non le client remboursera son crédit, et supervisé en entraînant le modèle sur les anciens crédits déboursés. 

![](https://www.quantmetry.com/wp-content/uploads/2023/04/octroit-de-credit.png)

_Figure 2 : Schéma explicatif d’un cas d’usage d’octroi de crédit. Source : Quantmetry_

##  **S’aligner sur les objectifs métier**

Ici, deux exigences métiers étaient définies : le risque global des crédits déboursés (combien de crédits sont remboursés pour 100 crédits accordés) ainsi que le montant moyen du crédit (la moyenne des montants des crédits). En effet, un modèle peut être conservateur en proposant uniquement des crédits à faible montant pour minimiser le risque. Ces exigences métiers ont été par la suite traduites en performance technique, à savoir l’AUC-ROC pour mesurer la capacité du modèle discriminer les clients qui peuvent rembourser de ceux qui ne peuvent pas. Définir ces métriques métier nous a permis de ne pas perdre de vue l’objectif premier du projet qui est de contrôler le risque en maximisant le revenu, et non maximiser à tout prix l’AUC ROC. 

##  **Évaluer la performance**

Ici, des fenêtres temporelles ont été construites pour le jeu d’entraînement, de calibration et de test. Les métriques de performances ont été calculées sur un jeu de données postérieur au jeu d’entraînement pour respecter la causalité de l’information. En opération, le modèle prédit sur des données futures au jeu d’entraînement. Dans ce cas d’usage particulier, il est impossible de mesurer le nombre de faux négatifs (des clients à qui nous avons refusé d’accorder un crédit mais qui auraient pu le rembourser) car le jeu de données labellisés se construit après avoir décidé d’accorder ou non un crédit. C’est pour cela que les métriques métiers étaient bien plus informatives sur la qualité du modèle que les métriques techniques. De plus, pour éviter d’être complètement aveugle sur cette population, nous aurions pu automatiquement accorder des crédits à une infime partie des clients (environ 1%) et ainsi avoir des métriques de performances techniques non-biaisées. 

##  **Comparer les performances**

Notre client avait déjà entraîné un modèle de classification binaire. Nous avons, dès le début du projet, comparé notre nouveau modèle avec le leur et avec une référence qui était un modèle totalement aléatoire. Côté performance métier, nous avons ainsi pu mesurer le gain réel à utiliser notre modèle sur un mois de référence pour lequel nous avions de la donnée labellisée. Ce procédé est répliqué une fois le modèle déployé pour s’assurer qu’il est toujours aussi performant et que les exigences métiers sont toujours validées. 

Voilà, vous savez tout sur la performance ! 

[ ![Reliable Ai](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-Reliable-Ai.svg) ](https://www.quantmetry.com/experts/#reliableia)

Les membres de l’ [ expertise Reliable AI ](https://www.quantmetry.com/experts/#reliableia) développent des modèles performants, fiables et maîtrisés, sur l’ensemble du cycle de vie, pour une IA de confiance. 

* * *

![Philippe Neveux](https://www.quantmetry.com/wp-content/uploads/2022/12/1602590192671.jpeg)

[ Philippe Neveux  ](https://www.linkedin.com/in/philippe-neveux/)

Senior Data Scientist de l'expertise Reliable AI 

Philippe est un des artisans de l'expertise Reliable AI. Il travaille sur ces sujets en auditant des algorithmes au vu de la nouvelle réglementation, en déployant des modèles d'intelligence artificielle de confiance ou encore en organisant des formations assurant son mandat de responsable Formations IA de Confiance de Quantmetry 
