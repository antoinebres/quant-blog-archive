# recommandations-spark-2021
Wayback Machine URL: https://web.archive.org/web/20230606093143/https://www.quantmetry.com/blog/recommandations-spark-2021/
Archive date: 2023-06-06

Data Gouvernance 

06/11/2020 

#  Nos recommandations pour réussir l'adoption d'Apache Spark en 2021 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Frecommandations-spark-2021%2F&title=Nos%20recommandations%20pour%20r%C3%A9ussir%20l%27adoption%20d%27Apache%20Spark%20en%202021 "Linkedin") [ ](http://twitter.com/intent/tweet?text=Nos%20recommandations%20pour%20r%C3%A9ussir%20l%27adoption%20d%27Apache%20Spark%20en%202021&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Frecommandations-spark-2021%2F "Twitter") [ ](https://www.quantmetry.com/blog/recommandations-spark-2021/ "Email") [ ](https://www.quantmetry.com/blog/recommandations-spark-2021/ "Copy Link")

* * *

Auteurs : [ Jean-Yves Stephan ](https://www.linkedin.com/in/jystephan/) , [ Alexandre Henry ](https://www.linkedin.com/in/alexandre-henry-mle/)

Temps de lecture : 7 minutes 

![Quantmetry.com : Nos recommandations pour réussir l'adoption d'Apache Spark en 2021](https://quantmetry.b-cdn.net/wp-content/uploads/2020/11/ahe.png)

_Cet article est rédigé conjointement avec :  
[ Data Mechanics ](https://www.datamechanics.co) , une start-up soutenue par YCombinator et fondée par d’anciens ingénieurs de Databricks, commercialise une plateforme Spark de nouvelle génération déployée sur Kubernetes. Leur mission est de rendre Spark plus facile à utiliser et plus rentable, avec un focus sur les tâches de data engineering. _

####  Qu’est-ce qui rend Apache Spark populaire ? 

Dans le monde de la data science et du data engineering, [ Apache Spark ](http://spark.apache.org/) est la technologie de pointe pour travailler avec de grands volumes de données. La communauté des développeurs Spark est florissante : la plupart des entreprises ont déjà adopté ou sont en train d’adopter Apache Spark. Sa popularité est due à 3 raisons principales : 

  1. **C’est rapide** . Il peut traiter de grands volumes de données (à l’échelle du GB, TB ou PB) grâce à sa parallélisation native. 
  2. **Spark dispose d’API en Python (PySpark), Scala/Java, SQL et R** . Ces API permettent une migration simple des charges de travail Python « mono-machine » (non distribuées) vers un fonctionnement à l’échelle avec Spark. Par exemple, la bibliothèque Koalas a récemment été publiée, ce qui permet aux développeurs Python de transformer facilement leur code Pandas en Spark. Le fait que du code Python/Scala puisse être exécuté donne également aux développeurs beaucoup plus de flexibilité que les cadres de travail uniquement SQL comme Redshift et BigQuery. 
  3. **Spark est très polyvalent** . Apache Spark dispose de connecteurs pour pratiquement tous les stockages de données, et les clusters Spark peuvent être déployés dans n’importe quel plates-forme cloud ou on-premise. 



![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/11/apache-spark-data-mechanics.png)

####  Quels sont les principaux points douloureux d’Apache Spark ? 

Adopter Spark, c’est aussi avoir à relever des challenges : 

  1. **Le premier défi** est le fait qu’il est difficile pour les débutants de comprendre comment leur code est interprété et distribué par Spark. Vous devez apprendre les subtilités de Spark et atteindre un certain niveau d’expertise pour être capable de débugger votre application lorsqu’elle ne fonctionne pas comme prévu (par exemple, débugger une erreur de mémoire), et pour comprendre puis optimiser sa rapidité d’exécution. Spark présente de nombreuses configurations qui sont complexes à mettre en place pour les débutants. Par conséquent, la plupart des développeurs Spark ont tendance à s’en tenir aux paramètres par défaut, sans se rendre compte à quel point cela peut nuire à la stabilité et aux performances de leurs applications. 
  2. **Le deuxième défi** est la gestion de l’infrastructure. Quelle devrait être la taille de notre cluster Spark ? Quel type de machines virtuelles et de stockage dois-je choisir ? Comment devrions-nous collecter et visualiser les logs et les métriques ? Ces défis se présentent sous deux formes différentes entre les déploiements on-premise (avec Hortonworks, Cloudera, MapR) et les déploiements dans le cloud (AWS : EMR, GCP : Dataproc, Azure : HDInsight). 
     1. **Pour les déploiements on-premise** , le principal défi est le compromis coût/vitesse sur la taille du cluster. Si vous **sur-dimensionnez** votre cluster, vos coûts feront boule de neige et vous souffrirez la plupart du temps d’une faible utilisation et d’un sur-approvisionnement en ressources de votre cluster. Si vous **sous-dimensionnez** votre cluster, il ne pourra pas supporter les pics de charge de travail et vous devrez mettre en place des files d’attente prioritaires pour vous assurer que les charges de travail critiques pour votre mission ne sont pas retardées. 
     2. **Pour les déploiements cloud,** l’élasticité du cloud provider résout ce problème car les ressources peuvent être ajoutées ou retirées à la volée. Cela signifie également que les coûts ne sont pas limités et qu’il appartient à chaque utilisateur de Spark de dimensionner et de configurer ses applications de manière appropriée et de s’assurer qu’elles sont stables et rentables. Bien que les services soient dits « gérés », le véritable fardeau de la gestion et de la configuration repose toujours sur les équipes data qui utilisent le cluster Spark. 



Passons maintenant en revue les meilleures pratiques et les recommandations de Data Mechanics pour relever ces défis. 

####  Simplifier la gestion de l’infrastructure Spark grâce à une approche serverless 

[ Data Mechanics ](https://www.datamechanics.co/blog-post/video-tour-of-data-mechanics-the-serverless-spark-platform) est une plate-forme Spark gérée, déployée sur un cluster Kubernetes, cluster qui est hébergé directement sur l’espace cloud des clients. Elle est disponible sur les 3 grands fournisseurs cloud (AWS, GCP et Azure) et constitue une alternative aux plateformes comme Databricks, Amazon EMR, Google Dataproc et Azure HDInsight. Jean-Yves, un ancien ingénieur de Databricks, maintenant co-fondateur de Data Mechanics, explique 3 caractéristiques principales qui permettent une approche serverless pour Apache Spark. 

  * **C’est Dockerisé.**



Kubernetes a un support natif pour les conteneurs Docker. Ces conteneurs vous permettent de créer vos dépendances en une fois (sur votre ordinateur local) et d’exécuter votre application partout de manière cohérente : sur votre ordinateur local, pour du développement et des tests ; ou dans le cloud sur des données de production. 

En utilisant Docker plutôt que des scripts d’initialisation lents et des téléchargements de dépendance à l’exécution, vos applications Spark seront plus rentables et stables. Avec les optimisations appropriées, vous pouvez a [ ccélérer votre cycle de développement Spark avec Docker ](https://www.datamechanics.co/blog-post/spark-and-docker-your-spark-development-cycle-just-got-ten-times-faster) de sorte qu’il faut moins de 30 secondes entre le moment où vous apportez une modification à votre code et celui où il est déployé sur notre plate-forme. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/11/spark-docker-development-iteration-cycle-with-logo.png)

  * **Il est en mode autopilote.**



Nous pensons qu’une plateforme Spark « gérée » devrait faire plus que simplement démarrer des machines virtuelles lorsque vous en faites la demande. Elle devrait en fait décharger ses utilisateurs de la gestion de l’infrastructure. C’est pourquoi notre plateforme ajuste dynamiquement et automatiquement les paramètres d’infrastructure et les configurations Spark les plus importants : taille des clusters, type d’instance, types de stockage, niveau de parallélisme, gestion de la mémoire, configurations du shuffle, etc. Cela rend Spark 2x plus stable et plus rentable, comme cela a été illustré lors du [ Spark Summit 2019 via une success story ](https://databricks.com/session_eu19/how-to-automate-performance-tuning-for-apache-spark) . 
