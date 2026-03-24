# proof-of-concept-why
Wayback Machine URL: https://web.archive.org/web/20250519110743/https://www.quantmetry.com/blog/proof-of-concept-why/
Archive date: 2025-05-19

IA Strategy 

30/10/2019 

#  POC : pour quoi faire ? 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fproof-of-concept-why%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=POC%20%3A%20pour%20quoi%20faire%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fproof-of-concept-why%2F "Twitter") [ ](https://www.quantmetry.com/blog/proof-of-concept-why/ "Email") [ ](https://www.quantmetry.com/blog/proof-of-concept-why/ "Copy Link")

* * *

Temps de lecture : 4 minutes 

![Quantmetry.com : POC : pour quoi faire ?](https://www.quantmetry.com/wp-content/uploads/2019/10/article-gbo-min.png)

Chez Quantmetry, nous consacrons 20% de notre temps sur des projets de R&D. 80% de nos projets ne sont donc pas des projets de R&D. L’ambition de ces projets n’est pas d’augmenter l’état des connaissances scientifiques ou technologiques, ni de découvrir de nouvelles approches, mais d’exploiter au mieux les connaissances et technologies existantes pour concevoir des solutions qui répondront parfaitement aux attentes des futurs utilisateurs. La réussite de ces projets sera donc évaluée par leur usage en production et leur adoption par les métiers, non par la connaissance qu’ils auront permis de créer. 

Si la plupart des projets d’IA ont aujourd’hui l’objectif d’aller en production un jour, trop peu y parviennent de façon fluide et efficiente. Après une première phase de PoC (Proof of Concept), l’industrialisation s’avère souvent bien plus douloureuse que prévu. Plus douloureuse qu’espéré serait plus exact, car rien n’a justement été prévu pour que cela se passe de façon optimale. Les attentes associées au PoC sont trop souvent éloignées de l’ambition initialement exprimée. 

Un PoC permet de valider des hypothèses  **_avant_ ** de se lancer dans un projet. Il appartient donc au mieux à la phase de  **_cadrage du projet_ ** . Il est souvent réalisé avec les métiers, par des data scientists qui travaillent dans des environnements spécifiques et sur des jeux de données limités, non représentatifs de l’environnement et des données en production. 

Comme lors de hackatons, les modèles recherchent la performance et sont développés et évalués dans des environnements de lab, parfois très éloignés de l’environnement et des contraintes de la production et qui fait l’impasse sur des points de conception pourtant structurants. 

Parmi les impasses fréquentes qui peuvent rendre une industrialisation coûteuse, voire impossible, citons notamment : 

  * les besoins de scalabilité qui n’ont pas été pris en compte (nombre d’utilisateurs cibles, temps de réponses,…) ; le code développé dans le cadre du POC n’est pas scalable, exécutable en mode distribué 
  * les choix technologiques de l’environnement du POC sont trop éloignés de l’environnement cible d’exécution 
  * les données de production ne sont pas accessibles dans les conditions adaptées au cas d’usage (qualité, temps d’accès, sécurité IT) 
  * le cas d’usage testé ne respecte pas les exigences légales (GDPR) 
  * le modèle mis au point dans le contexte de l’expérimentation n’est pas suffisamment robuste aux variations des données réelles en production 
  * le ROI du projet n’a pas été estimé et se révèle trop faible pour pousser le projet en production 
  * la gouvernance projet en place ne permet pas de mener le projet à bout (manque de sponsors, compétence et autonomie des équipes limitée, phasage /orchestration des tâches, rôles et responsabilités mal ou pas définies) 



La difficulté n’est pas liée à la complexité de ces questions, mais à leur caractère structurant. On aurait parfois pu savoir dès le début qu’on ne saura pas y répondre, ou que l’approche n’était pas la bonne. Le développement du modèle est un des aspects de la solution, et ce n’est pas toujours le plus complexe. 

**_Un POC est difficile à industrialiser parce qu’il n’est pas pensé pour être industrialisé._ **

#####  Interdisciplinarité 

En observant ces quelques exemples de causes d’échec, on constate la grande diversité de leur nature : technologique, légale, mathématique, métier, organisationnelle,… elles se situent dans des champs de connaissance distincts, et qui se spécialisent encore un peu plus chaque année. 

Pour les data scientists, le rythme de nouvelles publications ou de nouveaux algorithmes, rend très difficile le maintien de leurs expertises à un haut niveau sur des sujets aussi variés que le traitement du langage (NLP / NLU), l’analyse d’images (computer vision), ou le forecast de séries temporelles par exemple. La science des données se structure en disciplines. 

Pour des data engineers et les architectes techniques aussi, le rythme des évolutions technologiques ne permet pas de conserver le niveau d’expertise nécessaire à la fois sur des architectures cloud, on-premise, ou embarqué (AI at Edge). 

Maintenir un haut niveau d’expertise dans ces différentes disciplines est donc certainement nécessaire, mais pas suffisant. Le développement de solutions d‘IA demande de l’interdisciplarité, qui implique qu’il y ait des interactions et un enrichissement mutuel entre ces différents spécialistes. Ce qui, le plus souvent, n’est pas le contexte des PoC. 

#####  Conclusion 

Réaliser un PoC est toujours pertinent, mais gardez à l’esprit qu’il s’agit d’une  **_démarche expérimentale_ ** . Si vous avez l’ambition d’une solution en production, ou d’un produit logiciel, développez un prototype, une solution fonctionnelle, incluant dès le lancement du projet l’ensemble des parties-prenantes, métiers et IT. 

Un produit industriel n’est pas le résultat d’évolutions incrémentales réalisées à partir d’un PoC. Ce sont deux démarches bien distinctes qui ne poursuivent pas le même objectif. Il est donc essentiel que l’ambition soit claire et partagée dès le démarrage. 

#####  ✍ Article écrit par [ Guillaume Bodiou ](https://www.linkedin.com/in/guillaume-bodiou/)
