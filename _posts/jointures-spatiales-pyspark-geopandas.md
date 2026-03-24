# jointures-spatiales-pyspark-geopandas
Wayback Machine URL: https://web.archive.org/web/20230602174602/https://www.quantmetry.com/blog/jointures-spatiales-pyspark-geopandas/
Archive date: 2023-06-02

Recherche et développement 

03/02/2020 

#  Optimisez vos jointures spatiales avec PySpark et Geopandas 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fjointures-spatiales-pyspark-geopandas%2F&title=Optimisez%20vos%20jointures%20spatiales%20avec%20PySpark%20et%20Geopandas "Linkedin") [ ](http://twitter.com/intent/tweet?text=Optimisez%20vos%20jointures%20spatiales%20avec%20PySpark%20et%20Geopandas&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fjointures-spatiales-pyspark-geopandas%2F "Twitter") [ ](https://www.quantmetry.com/blog/jointures-spatiales-pyspark-geopandas/ "Email") [ ](https://www.quantmetry.com/blog/jointures-spatiales-pyspark-geopandas/ "Copy Link")

* * *

Temps de lecture : 6 minutes 

![Quantmetry.com : Optimisez vos jointures spatiales avec PySpark et Geopandas](https://quantmetry.b-cdn.net/wp-content/uploads/2020/02/article-lbl-min.png)

_ [ ✍ Luis Blanche ](https://www.linkedin.com/in/luisblanche/) /  Temps de lecture : 10min _

Avec l’avènement des technologies embarquées, la quantité de données géolocalisée ne cesse d’augmenter. Les véhicules connectés et de nouvelle mobilité notamment (voitures, vélos, trottinettes en libre services) génèrent une masse colossale de ces données à une fréquence élevée. Dans un contexte de forte compétitivité (exemple des trottinettes à Paris, avec une dizaine de marques à disposition), il devient capital de traiter ces données dans un temps rapide. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/trottinette-electrique-paris.jpg)

La compétitivité des trottinettes en libre service à Paris ( [ source : trotinette-electrique-adulte.com) ](https://trottinette-electrique-adulte.com/trottinette-electrique-paris/)

Lorsqu’elles sont traitées en continu, il est possible d’utiliser des technologies qui marchent sur de faibles volumes. Mais dans le scénario d’un nouveau cas d’étude, il peut être nécessaire de joindre de la donnée spatiale à l’ensemble de notre historique. 

Les solutions qui s’offrent sont diverses et dépendent de la stack technique utilisée. Si par exemple les données sont stockées dans une base relationnelle Postgresql, il est possible de bénéficier de  [ PostGIS  ](https://postgis.net/) et de son indexation spatiale. Mais ces technologies ne sont pas toujours suffisantes pour faire face à la masse de données à traiter, et dans de nombreux cas on retrouvera plutôt un stockage de la donnée dans un écosystème distribué (HDFS, Hive, …). On pourra alors souhaiter bénéficier de la puissance de Spark. 

Seulement voilà, les outils pour le traitement de la donnée géolocalisée sous Spark et plus particulièrement **PySpark** , ne sont pas très avancés (cf  [ GIS with pySpark : A not-so-easy journey  ](https://gist.github.com/4rzael/bbd543af0cb2ee087771f42c5aefdad7) ). En particulier il n’existe pas dans le module pyspark.sql de méthode de traitement spécifiques, ni de type de données géolocalisée. 

Lorsqu’on traite de la donnée géolocalisée en python,  [ geopandas  ](http://geopandas.org/) est désormais un outil incontournable, à l’image de PostGIS pour Postgresql, geopandas dote l’écosystème pandas de capacités géospatiales. Cela inclue la fameuse indexation spatiale, qui permet de grandement accélérer les jointures. 

####  Comment ça marche ? 

Un **geopandas GeoDataFrame** , c’est un **pandas DataFrame** doté d’une colonne _geometry_ et d’une indexation spatiale à l’aide d’un **RTree** . 

Le **RTree** découpe l’espace en rectangles successivement inclus les uns dans les autres et associe une géométrie (point, ligne, polygone) à l’un de ces rectangles. Lors d’une jointure spatiale, cela permet de réduire l’espace de recherche rapidement en faisant d’abord une jointure sur ces rectangles (ce qui est extrêmement rapide car il s’agit seulement de deux comparaisons). Voir l’excellent blog de  [ Geoff Beoing  ](https://geoffboeing.com/2016/10/r-tree-spatial-index-python/) sur le sujet. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/01/1_rsz300nanspcxrd2bu5sqw.png)

Principe de **RTree** : découper l’espace en rectangles pour faciliter les jointures ( [ source : mapbox) ](https://blog.mapbox.com/a-dive-into-spatial-search-algorithms-ebd0c5e39d2a)

L’indexation spatiale par **RTree** dans **geopandas** est codée et compilée en C ce qui ajoute encore à l’efficacité des jointures spatiales ainsi faites. 

**Attention** , cela peut complexifier l’installation de **geopandas** , à cause des dépendances en C (libspatialindex).   
Si vous installez le module avec **conda** , alors il vient avec les dépendances C précompilées. Si vous utilisez **pip** , il faudra peut être installer libspatialindex et compiler avant de pouvoir bénéficier de Rtree (voir les instructions ici : [ https://pypi.org/project/Rtree/0.6.0/ ](https://pypi.org/project/Rtree/0.6.0/) ) 

#####  Exemple de jointure en geopandas : 
    
    
    import geopandas as gpd
    
    df_joined = gpd.sjoin(points, polygons, op=’intersect’)
    
    

* * *

######  **_L’idée présentée dans cet article est donc de combiner la puissance d’indexation de geopandas à celle de distribution de Spark._ **

* * *

Comment faire en pratique : grâce à l’utilisation des [ **pandas_udf** ](https://docs.databricks.com/spark/latest/spark-sql/udf-python-pandas.html) , et de la fonction **broadcast** de **pyspark.**

Voyons ce que ça peut donner sur un exemple. 

####  Exemple avec code commenté 

On dispose dispose de trajectoire GPS (par exemple les trajectoires de taxi de Microsoft disponible en téléchargement libre [ ici ](https://www.microsoft.com/en-us/research/publication/t-drive-trajectory-data-sample/?from=https%3A%2F%2Fresearch.microsoft.com%2Fapps%2Fpubs%2F%3Fid%3D152883) ). 

Et d’un autre côté d’un fichier geojson (ou shapefile, ou tout autre format que **geopandas** peut lire) avec les contours des provinces chinoises (exemple [ ici ](https://data.humdata.org/dataset/china-administrative-boundaries) ). 

On souhaite associer à chaque point de chaque trajectoire une province, pour compter par exemple les trajets inter provinces 

#####  Code complet 
    
    
    import geopandas as gpd
    from shapely import wkt
    from pyspark.sql.functions import broadcast
    
    province = gpd.load_file('...china_provinces.geojson')
    # Use a previously created spark session
    traces= spark_session.read_csv('trajectoires.csv')
    provinces_spark = spark.createDataFrame(provinces[['insee_comm', 'wkt']])
    provinces_json = provinces_spark.toJSON().collect()
    provinces_bc = spark.sparkContext.broadcast(provinces_json)
    
    @pandas_udf(schema_out, PandasUDFType.GROUPED_MAP)
    def join_provinces_bc(traces):
    """"""
    provinces = pd.DataFrame.from_records([json.loads(c) for c in provinces_bc.value])
    polygons = [wkt.loads(w) for w in provinces['wkt']]
    gdf_provinces = gpd.GeoDataFrame(provinces, geometry=polygons, crs=crs )
    geometry = gpd.points_from_xy(traces['longitude'], traces['latitude'])
    gdf_traces = gpd.GeoDataFrame(traces , geometry=geometry, crs=crs)
    joined_df = gpd.sjoin(gdf_traces, gdf_provinces, how='left', op='within')
    return joined_df[columns]
    
    traces = traces.groupby(salt).apply(join_provinces_bc)
    

#####  Explication du code ligne par ligne : 

Dans un premier temps on utilise le module geopandas pour charger le fichier de formes (provinces).   
On lit ensuite les trajectoires sous la forme d’un Spark DataFrame 
    
    
    import geopandas as gpd
    from shapely import wkt
    
    province = gpd.load_file('...china_provinces.geojson')
    traces= spark_session.read_csv('trajectoires.csv')
    
    

Puis on réalise un broadcast du GeoDataFrame des provinces. Cela permet d’avoir la donnée en cache sur chaque worker et d’éviter ainsi de perdre du temps à en IO a chaque tâche ( [ voir une très bonne explication ici ](https://github.com/TianLangStudio/mastering-apache-spark-book-zh/blob/master/spark-broadcast.adoc) ) 

Malheureusement il n’est pas possible de broadcaster un **DataFrame** et encore moins un **GeoDataFrame** , qui contient de la donnée au format [ shapely ](https://shapely.readthedocs.io/en/latest/) , inconnue de Spark.   
Alors il faut transformer notre GeoDataFrame en un objet sérialisable: un **JSON :**
    
    
    
    from pyspark.sql.functions import broadcast
    
    provinces_spark = spark.createDataFrame(provinces[['insee_comm', 'wkt']])
    provinces_json = provinces_spark.toJSON().collect()
    provinces_bc = spark.sparkContext.broadcast(provinces_json)
    
    

On peut alors construire notre **pandas_udf** de type **GROUPED_MAP.** Elle prend en entrée un pandas DataFrame et retourne un pandas DataFrame.   
Dans le décorateur **@pandas_udf** , on insère le schéma du DataFrame retourné par la fonction, et le type de pandas udf.   
Dans notre cas, le DataFrame de sortie est le même que celui en entrée, agrémenté d’une colonne contenant le code de la province. On peut construire le schéma de sortie de la façon suivante : 
    
    
    
    from pyspark.sql.types import *
    
    schema = traces.schema.fields.copy()
    schema.append(StructField("code_province", StringType(), True))
    schema_out = StructType(schema)
    
    

La fonction va recréer les deux **GeoDataFrame** et opérer la jointure spatiale en **geopandas** . Elle retourne un **DataFrame** avec les colonnes souhaitées et définies dans _schema_out_ . 
    
    
    
    @pandas_udf(schema_out, PandasUDFType.GROUPED_MAP)
    def join_provinces_bc(traces):
    
    provinces = pd.DataFrame.from_records([json.loads(c) for c in provinces_bc.value])
    polygons = [wkt.loads(w) for w in provinces['wkt']]
    gdf_provinces = gpd.GeoDataFrame(provinces, geometry = polygons, crs=crs )
    geometry = gpd.points_from_xy(traces['longitude'], traces['latitude'])
    gdf_traces = gpd.GeoDataFrame(traces , geometry=geometry, crs=crs)
    joined_df = gpd.sjoin(gdf_traces, gdf_provinces, how='left', op='within')
    
    return joined_df[columns]
    
    

On applique ensuite cette fonction au Spark DataFrame à l’aide d’un groupby et un apply.   
C’est le groupby qui va décider du partitionnement du **DataFrame** . Il est donc important de choisir correctement sur quelles clés grouper. S’il n’existe pas de clé permettant directement une répartition équilibrée de la donnée, il peut alors être opportun de créer **[ un sel ](https://dzone.com/articles/why-your-spark-apps-are-slow-or-failing-part-ii-da) . ** Celui ci permettra de repartir la donnée sur le maximum de partitions permises par la session Spark/ le cluster : 
    
    
    
    from pyspark.sql.functions import, round, rand&amp;nbsp; #&amp;nbsp; attention a ne pas confondre avec les function natives de python
    
    n_partitions = int(spark.conf.get('spark.sql.shuffle.partitions'))
    results = traces.withColumn('salt', round(rand()*n_partitions)).groupby(['salt']).apply(join_provinces_bc).drop('salt')
    
    

####  Conclusion : 

Cet article présente une solution pour **effectuer efficacement des jointures spatiales** lorsque les outils classiques ne le permettent pas. Une des **limitations** de cette méthode est le **broadcast** du fichier de géométrie à joindre, qui ne peut pas être trop gros (8GO dans spark 2.4). Néanmoins nous avons pu utiliser cette technique en conditions réelles et obtenir des **gains de performances significatifs** . 

Vous voilà donc armés pour enrichir vos données géolocalisées, et ce n’est pas l’open data qui manque en la matière ! 

_ [ ✍ Luis Blanche ](https://www.linkedin.com/in/luisblanche/) _
