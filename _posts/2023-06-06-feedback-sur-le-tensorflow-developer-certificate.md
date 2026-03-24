---
layout: post
title: feedback-sur-le-tensorflow-developer-certificate
date: 2023-06-06
url_wayback_machine: https://web.archive.org/web/20230606085939/https://www.quantmetry.com/blog/feedback-sur-le-tensorflow-developer-certificate/
---
Upskilling data 

09/09/2020 

#  Feedback sur le TensorFlow Developer Certificate 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Ffeedback-sur-le-tensorflow-developer-certificate%2F&title=Feedback%20sur%20le%20TensorFlow%20Developer%20Certificate "Linkedin") [ ](http://twitter.com/intent/tweet?text=Feedback%20sur%20le%20TensorFlow%20Developer%20Certificate&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Ffeedback-sur-le-tensorflow-developer-certificate%2F "Twitter") [ ](https://www.quantmetry.com/blog/feedback-sur-le-tensorflow-developer-certificate/ "Email") [ ](https://www.quantmetry.com/blog/feedback-sur-le-tensorflow-developer-certificate/ "Copy Link")

* * *

Temps de lecture : 4 minutes 

![Quantmetry.com : Feedback sur le TensorFlow Developer Certificate](https://quantmetry.b-cdn.net/wp-content/uploads/2020/09/article-lucgib-min.png)

En mars 2020, Google a lancé le  [ **TensorFlow Developer Certificate** ](https://www.tensorflow.org/certificate) , une nouvelle certification évaluant les compétences en TensorFlow, sa bibliothèque dédiée au deep learning. L’objectif de cet article est de vous présenter cette certification ainsi que mon retour sur l’examen. 

Si il existe déjà de nombreuses certifications en machine learning, c’est la première fois que Google, entreprise ayant pris une place importante dans le développement de ce domaine, créé sa propre certification dédiée au deep learning. 

En effet, de nombreuses certifications sont aujourd’hui remises à la fin de cours suivis en ligne et certains cloud providers ont créé des certifications spécialement dédiées au machine learning. On peut par exemple citer les certifications  [ AWS Certified Machine Learning – Specialty  ](https://aws.amazon.com/fr/certification/certified-machine-learning-specialty/) et  [ Microsoft Certified: Azure Data Scientist Associate  ](https://docs.microsoft.com/fr-fr/learn/certifications/azure-data-scientist) . GCP, qui appartient à Google, ne possède en revanche pas de certification spécifiquement dédiée au machine learning et à la data science : le TensorFlow Developer Certificate vient donc combler ce vide. 

Alors que de nombreuses certifications sont principalement théoriques et évaluent leurs candidats au travers de QCM, j’ai particulièrement apprécié passer cette certification qui est composé d’une suite de problèmes à résoudre. C’est beaucoup plus proche du travail que l’on peut être amené à faire en entreprise. 

Cette certification est présentée comme “level one”, ce qui signifie qu’elle est relativement accessible. Google ne souhaite cependant pas s’arrêter là et songe déjà à créer de nouvelles certifications plus avancées et plus spécialisées. Il se peut que les compétences des développeurs en machine learning soient ainsi davantage évaluées au travers de certifications à l’avenir. Il ne serait aussi pas surprenant que Facebook démarre à son tour un programme de certifications pour PyTorch, principale alternative à TensorFlow. 

####  Préparation de l’examen 

La première chose à faire pour se préparer à l’examen est de lire le  [ manuel du candidat  ](https://www.tensorflow.org/site-assets/downloads/marketing/cert/TF_Certificate_Candidate_Handbook.pdf) , qui explique toutes les modalités de l’épreuve. En particulier, le document énumère la liste des connaissances évaluées.    
La formation conseillée pour se préparer à l’examen est  [ TensorFlow in Practice  ](https://www.coursera.org/specializations/tensorflow-in-practice) de Laurence Moroney, disponible sur Coursera. Ce cours enseigne comment utiliser TensorFlow pour résoudre des problèmes de vision par ordinateur, de traitement du langage naturel et de séries temporelles. Pour suivre cette formation, des compétences en programmation avec Python ainsi que des connaissances en mathématiques sont nécessaires. Des connaissances préalables en machine learning sont conseillées mais pas obligatoires, bien que cela facilitera grandement la formation. Il ne m’a pas paru nécessaire d’utiliser d’autres cours pour réussir la formation mais j’avais été amené à utiliser TensorFlow à plusieurs reprises par le passé. 

Quelqu’un ayant l’habitude de développer en TensorFlow devrait pouvoir compléter cette formation en peu de temps. Par ailleurs, TensorFlow évolue rapidement et si vous n’avez pas développé depuis quelque temps en utilisant cette bibliothèque, le cours sera un bon moyen d’actualiser vos connaissances. De grandes évolutions ont par exemple été apportées l’année dernière avec l’arrivée de TensorFlow 2.0. 

[ Un document  ](https://www.tensorflow.org/site-assets/downloads/marketing/cert/Setting_Up_TF_Developer_Certificate_Exam.pdf) indique également comment préparer son ordinateur avant de commencer l’examen. En particulier, vous devez : 

  * installer PyCharm 
  * installer la bonne version de Python (Python 3.7 en juin 2020) 



L’examen se déroulant sur PyCharm, il est donc préférable de se familiariser à cet environnement avant l’épreuve. Je conseille de résoudre au maximum les exercices de la formation en utilisant PyCharm. 

####  Déroulement de l’examen 

L’examen dure 5 heures et coûte 100 USD. Contrairement à d’autres certifications, l’examen est à faire depuis chez vous, sur votre propre ordinateur. Qui plus est, vous ne serez pas surveillés par vidéo tout au long de l’examen et pourrez accéder à toutes les ressources que vous souhaitez au cours de l’épreuve. Le grand avantage de ce fonctionnement est que vous pouvez commencer l’épreuve quand vous le souhaitez, il n’y a pas d’horaire à réserver à l’avance. 

Vous devrez alors installer un plugin sur PyCharm spécialement dédié à l’examen : l’environnement virtuel dans lequel vous devrez travailler sera donc automatiquement créé. 

L’examen est composé de 5 exercices de difficulté croissante abordant les thèmes de la vision par ordinateur, du traitement naturel du langage et des séries temporelles. Il n’y a pas de surprise particulière, les exercices sont dans l’ensemble très proches de ceux faits au cours de la formation TensorFlow in Practice. 

À la fin de chaque exercice, vous devrez rendre le fichier contenant le modèle entraîné. Il sera envoyé sur les serveurs de Google, évalué, puis vous recevrez une information claire permettant de savoir à quel point le modèle envoyé est le modèle attendu. 

Les apprentissages des modèles étant à réaliser sur votre machine, un ordinateur puissant sera un gain de temps au cours de l’épreuve. Néanmoins, 5 heures me semblent largement suffisantes pour résoudre l’ensemble des problèmes et vous ne devriez pas être trop pénalisés par une puissance de calcul trop faible. 

####  Après l’examen 

Quelques jours après l’épreuve, vous recevrez un mail vous informant de votre réussite ou non à l’examen. Si vous avez réussi l’examen, félicitations ! Vous recevrez quelque jours plus tard un second mail avec votre certification, valide pour une durée de 3 ans. 

Vous pourrez également choisir de rejoindre le  [ réseau des spécialiste certifiés  ](https://developers.google.com/certification/directory/tensorflow) . C’est un réseau naissant avec la certification dont l’objectif est de regrouper des développeurs maîtrisant TensorFlow. Toute personne qui souhaite rechercher des développeurs compétents peut le faire en filtrant par certification obtenue, nombre d’années d’expériences et zone géographique. Aujourd’hui, il est uniquement possible de sélectionner “TensorFlow Delevoper Certificate” dans le champ dédié au choix de la certification, mais l’existence de ce filtre confirme de nouveau l’intention qu’a Google de proposer de nouvelles certifications à l’avenir. 

#####  ✍ [ Luc Gibaud ](https://www.linkedin.com/in/luc-gibaud/)
