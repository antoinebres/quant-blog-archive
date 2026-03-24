---
layout: post
title: window-functions-spark
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129144245/https://www.quantmetry.com/blog/window-functions-spark/
---
Data Gouvernance 

25/05/2020 

#  Comment utiliser les Window Functions sur Spark 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fwindow-functions-spark%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Comment%20utiliser%20les%20Window%20Functions%20sur%20Spark&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fwindow-functions-spark%2F "Twitter")

* * *

Temps de lecture : 9 minutes 

![Quantmetry.com : Comment utiliser les Window Functions sur Spark](https://quantmetry.b-cdn.net/wp-content/uploads/2020/06/spark.jpg)

✍  [ Omar HAYAK ](https://fr.linkedin.com/in/ohayak) / Temps de lecture 12 minutes 

Si votre travail consiste à analyser des données, vous avez certainement rencontré des questions dont la réponse est intuitive mais difficile à exprimer en pur SQL/Spark. Si vous avez déjà essayé de calculer une moyenne glissante ou le rang d’une ligne, sans doute avez-vous pensé à ça : si seulement je pouvais itérer sur toutes les lignes de ma requête. Cette intuition ouvre les portes sur un labyrinthe de workarounds : écrire des jointures complexes, utiliser Excel ou faire le calcul hors base de données. Mais toutes les alternatives ne sont pas acceptables. 

En outre, il existe les _Window functions_ ou fonctions de fenêtrage qui améliorent considérablement l’expressivité de SQL et Spark. Cet article vous fera découvrir ces fonctions à travers des exemples pratiques. 

##  Définition 

Avant Spark 1.4, on pouvait distinguer deux types de fonctions : 

  * Les fonctions _built-in_ ou _UDFs_ telles que ` substr ` ou ` round ` , qui prennent des valeurs d’une seule ligne en entrée et génèrent une valeur de retour unique pour chaque ligne en entrée. 
  * Les fonctions d’agrégation, telles que ` sum ` ou ` max ` , fonctionnent sur un groupe de lignes et calculent une valeur de retour unique pour chaque groupe. 



Bien que celles-ci soient très utiles dans la pratique, il existe des opérations qui ne peuvent pas être exprimées en utilisant uniquement ces types de fonctions. Plus précisément, il n’y avait aucun moyen pour opérer sur un groupe de lignes tout en renvoyant une seule valeur pour chaque ligne en entrée.   
Cette limitation complexifie l’exécution de diverses tâches de traitement des données, tel que le calcul d’une moyenne glissante, le rang d’une ligne ou l’accès aux valeurs d’une ligne avant ou après la ligne actuelle. Heureusement pour les utilisateurs de Spark SQL, les _window functions_ introduites par Spark 1.4 comblent cette lacune. 

Une window function (fonction de fenêtrage) calcule une valeur de retour pour chaque ligne d’une table à partir d’un groupe de lignes appelé _Frame_ . Chaque ligne d’entrée peut être associée à un _Frame_ unique. Cette caractéristique fondamentale rend les fonctions de fenêtrage plus puissantes. Cela permet aux utilisateurs d’exprimer diverses tâches de traitement de données difficiles (voir impossibles) à exprimer de manière concise. 

Prenons cet exemple tiré du chapitre [ 3.5 Window Functions ](https://www.postgresql.org/docs/10/tutorial-window.html) de la documentation PostgreSQL: 
    
    
    import sys
    from pyspark.sql.window import Window
    from pyspark.sql import SparkSession
    import pyspark.sql.functions as f
    import pyspark.sql.types as t
    
    spark = SparkSession.builder \
         .master("local") \
         .appName("WindowsAreGood") \
         .getOrCreate()
    
    schema = t.StructType([
     t.StructField('depName', t.StringType(), False),
     t.StructField('empNo', t.IntegerType(), False),
     t.StructField('salary', t.IntegerType(), False),
    ])
    
    data = [
     ("sales", 1, 5000),
     ("personnel", 2, 3900),
     ("sales", 3, 4800),
     ("sales", 4, 4800),
     ("personnel", 5, 3500),
     ("develop", 7, 4200),
     ("develop", 8, 6000),
     ("develop", 9, 4500),
     ("develop", 10, 5200),
     ("develop", 11, 5200)
    ]
    sdf = spark.createDataFrame(data, schema=schema)
    

Ce code fourni le DataFrame suivant: 
    
    
    +---------+-----+------+
    |  depName|empNo|salary|
    +---------+-----+------+
    |    sales|    1|  5000|
    |personnel|    2|  3900|
    |    sales|    3|  4800|
    |    sales|    4|  4800|
    |personnel|    5|  3500|
    |  develop|    7|  4200|
    |  develop|    8|  6000|
    |  develop|    9|  4500|
    |  develop|   10|  5200|
    |  develop|   11|  5200|
    +---------+-----+------+
    

On souhaite calculer le salaire moyen par département et sans utiliser les fonctions de fenêtrage : 
    
    
    sdf.groupBy('depName').agg(f.avg('salary').alias('avg')).show()
    
    
    
    +---------+-----------------+
    |  depName|              avg|
    +---------+-----------------+
    |  develop|           5020.0|
    |    sales|4866.666666666667|
    |personnel|           3700.0|
    +---------+-----------------+
    

Pour obtenir le même résultat avec les window functions, on utilisera le module spark ` Window ` . Ce dernier contient les outils nécessaires pour manipuler les window functions, notamment l’objet ` WindowSpec ` qu’on va utiliser pour définir le Frame. Dans cet exemple, un frame est l’ensemble des lignes du même département. Plus de détails dans le chapitre suivant. 
    
    
    byDepName = Window.partitionBy('depName')
    sdf.withColumn("avg", f.avg('salary').over(byDepName)).show()
    
    
    
    +---------+-----+------+-----------------+
    |  depName|empNo|salary|              avg|
    +---------+-----+------+-----------------+
    |  develop|    7|  4200|           5020.0|
    |  develop|    8|  6000|           5020.0|
    |  develop|    9|  4500|           5020.0|
    |  develop|   10|  5200|           5020.0|
    |  develop|   11|  5200|           5020.0|
    |    sales|    1|  5000|4866.666666666667|
    |    sales|    3|  4800|4866.666666666667|
    |    sales|    4|  4800|4866.666666666667|
    |personnel|    2|  3900|           3700.0|
    |personnel|    5|  3500|           3700.0|
    +---------+-----+------+-----------------+
    

Cet exemple montre exactement la différence entre le fonctionnement d’une fonction d’agrégation et une fonction de fenêtrage. Certes, le fond des deux résultats est identique, mais le format est différent. Une fonction de fenêtrage ne regroupe pas les lignes et conserve leurs identités distinctes.   
Pour obtenir le même format à l’aide d’une agrégation, il faut ajouter une jointure avec le DataFrame initial pour chaque agrégation. 

##  WindowSpec 

` WindowSpec ` est une spécification qui définit quelles lignes sont incluses dans le frame, c’est-à-dire l’ensemble des lignes associées à la ligne actuelle. WindowSpec prend les éléments suivants lors de sa création : 

  * Partition : définit les enregistrements dans la même partition. Sans partition définie, tous les enregistrements appartiennent à une seule partition. 
  * Ordre : définit la façon dont les enregistrements dans une partition sont ordonnés, ce qui définit à son tour la position d’un enregistrement dans une partition. 
  * Cadre : définit les lignes à inclure dans la fenêtre de la ligne actuelle, en fonction de la position relative par rapport à la ligne actuelle. Par exemple : « Les trois lignes précédant la ligne actuelle vers la ligne actuelle » décrit un cadre comprenant la ligne d’entrée actuelle et trois lignes apparaissant avant. 



En pratique, on utilise les fonctions suivantes pour définir les spécifications d’une fenêtre : 

####  orderBy : 

Crée un WindowSpec avec l’ordre défini. 

####  partitionBy : 

Crée un WindowSpec avec le partitionnement défini. 

####  rowsBetween : 

Crée un WindowSpec avec les limites du cadre définies, de ` start ` (inclus) à ` end ` (inclus). Les deux ` start ` et ` end ` sont des positions par rapport à la ligne actuelle, **en fonction de sa position dans la partition.**
    
    
    windowSpec = Window.rowsBetween(-2, 1)
    sdf.withColumn("first_empNo", f.first("empNo").over(windowSpec))\
        .withColumn("last_empNo", f.last("empNo").over(windowSpec))\
        .withColumn("frame_size", f.count("empNo").over(windowSpec))\
        .show()
    
    
    
    +---------+-----+------+-----------+----------+----------+
    |  depName|empNo|salary|first_empNo|last_empNo|frame_size|
    +---------+-----+------+-----------+----------+----------+
    |    sales|    1|  5000|          1|         2|         2|
    |personnel|    2|  3900|          1|         3|         3|
    |    sales|    3|  4800|          1|         4|         4|
    |    sales|    4|  4800|          2|         5|         4|<= currentRow - 2
    |personnel|    5|  3500|          3|         7|         4|<= currentRow - 1
    |  develop|    7|  4200|          4|         8|         4|<= currentRow
    |  develop|    8|  6000|          5|         9|         4|<= currentRow + 1
    |  develop|    9|  4500|          7|        10|         4|
    |  develop|   10|  5200|          8|        11|         4|
    |  develop|   11|  5200|          9|        11|         3|
    +---------+-----+------+-----------+----------+----------+
    

Dans l’exemple ci-dessus, la fenêtre définit un frame de 4 lignes: 

  * la ligne courante 
  * les deux lignes précédentes 
  * la ligne suivante 



À l’exception des lignes aux extrémités, le frame est plus petit. 
    
    
    +---------+-----+------+-----------+----------+----------+
    |  depName|empNo|salary|first_empNo|last_empNo|frame_size|
    +---------+-----+------+-----------+----------+----------+
    |    sales|    1|  5000|          1|         2|         2|<= currentRow
    |personnel|    2|  3900|          1|         3|         3|<= currentRow + 1
    |    sales|    3|  4800|          1|         4|         4|
    |    sales|    4|  4800|          2|         5|         4|
    |personnel|    5|  3500|          3|         7|         4
