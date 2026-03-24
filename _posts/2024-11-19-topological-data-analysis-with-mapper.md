---
layout: post
title: topological-data-analysis-with-mapper
date: 2024-11-19
url_wayback_machine: https://web.archive.org/web/20241119145148/https://www.quantmetry.com/blog/topological-data-analysis-with-mapper/
---
Computer vision 

13/11/2020 

#  Topological data analysis with Mapper 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Ftopological-data-analysis-with-mapper%2F "Linkedin") [ ](http://twitter.com/intent/tweet?text=Topological%20data%20analysis%20with%20Mapper&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Ftopological-data-analysis-with-mapper%2F "Twitter") [ ](https://www.quantmetry.com/blog/topological-data-analysis-with-mapper/ "Email") [ ](https://www.quantmetry.com/blog/topological-data-analysis-with-mapper/ "Copy Link")

* * *

Auteur : [ Milton Minervino ](https://www.linkedin.com/in/milton-minervino/)

Temps de lecture : 8 minutes 

![Quantmetry.com : Topological data analysis with Mapper](https://www.quantmetry.com/wp-content/uploads/2020/10/mmi.png)

##  Introduction 

**Topological data analysis** (TDA) is a recent branch of data analysis that uses topology and in particular persistent homology. TDA is used to extract meaning from the  _ shape  _ of data. 

In this article we will explore a particular technique of TDA called the  **Mapper algorithm** introduced by Singh, Memoli and Carlsson in their seminal paper  [ _ Topological Methods for the Analysis of High Dimensional Data Sets and 3D Object Recognition  _ ](https://research.math.osu.edu/tgda/mapperPBG.pdf) _ (2007).  _

Mapper is a combination of dimensionality reduction, clustering and graph networks techniques used to get higher level understanding of the structure of data. It is mainly used for: 

  * visualising the shape of data through a particular lens 
  * detecting clusters and interesting topological structures which traditional methods fail to find 
  * selecting features that best discriminate data and for model interpretability 



A flourishing literature shows its high potential in real data applications and especially in biology and medicine. Created by some founders of the celebrated silicon valley start-up  [ Ayasdi  ](https://www.ayasdi.com/) , Mapper is applied in business to customer segmentation, hot spot analysis, fraud detection, churn prediction, drug discovery, socio-economic, sensor or text data as well. 

![](https://www.quantmetry.com/wp-content/uploads/2020/10/mapper_nba.png)

Performance profiles for each of the 452 players in the NBA by using data from the 2010–2011 NBA season. The number of the covering intervals on the left-hand figure is 20 while on the right-hand is 30 (higher resolution). Graphs are colored by points per game and the lens is chosen to be the projection to the principal and secondary SVD values. For more details, see [ Extracting insights from the shape of complex data using topology ](https://www.nature.com/articles/srep01236) . Precise definitions of coverings and lenses are described in Section “The algorithm”. 

![](https://www.quantmetry.com/wp-content/uploads/2020/10/diabetes.png)

[ Identification of type 2 diabetes subgroups through topological analysis of patient similarity ](https://stm.sciencemag.org/content/7/311/311ra174)

![](https://www.quantmetry.com/wp-content/uploads/2020/10/spinal_cord_injury.png)

[ Topological data analysis for discovery in preclinical spinal cord injury and traumatic brain injury ](https://www.nature.com/articles/ncomms9581)

![](https://www.quantmetry.com/wp-content/uploads/2020/10/breast_cancer.png)

[ Topology based data analysis identifies a subgroup of breast cancers with a unique mutational profile and excellent survival ](https://www.pnas.org/content/108/17/7265)

In this article we will briefly describe what Mapper technically is, reveal the advantages that it carries and show some applications as well as an exploratory case study. In a forthcoming article we will explore how TDA and persistent homology can be used effectively with Machine Learning. 

##  The Algorithm 

Given a dataset of points, the basic steps behind Mapper are as follows: 

  1. Map to a lower-dimensional space using a  _ filter function  _ ![f](https://www.quantmetry.com/wp-content/ql-cache/quicklatex.com-adc35b8a73a1f2d55f32f40fc952699a_l3.png) , or  _ lens  _ . Common choices for the filter function include projection onto one or more axes via PCA or density-based methods. 
  2. Construct a cover ![\(U_i\)_{i\\in I}](https://www.quantmetry.com/wp-content/ql-cache/quicklatex.com-4aa7342167d1dcbdf5945a1555dd59fb_l3.png) of the projected space typically in the form of a set of overlapping intervals which have constant length. 
  3. For each interval ![U_i](https://www.quantmetry.com/wp-content/ql-cache/quicklatex.com-411724eb0c3f5f9afafc802af844bc00_l3.png) cluster the points in the  _ preimage  _ ![f^{-1}\(U_i\)](https://www.quantmetry.com/wp-content/ql-cache/quicklatex.com-a39437f8a06043933078de3c5938707d_l3.png) into sets ![C_{i,1},\\ldots,C_{i,k_i}](https://www.quantmetry.com/wp-content/ql-cache/quicklatex.com-bfb580a29f07fdfa0bd5e5cf2df58953_l3.png) . 
  4. Construct the graph whose vertices are the cluster sets and an edge exists between two vertices if two clusters share some points in common. 



![](https://www.quantmetry.com/wp-content/uploads/2020/10/algo_explication.png)

Illustration of the mapper algorithm ( [ source ](https://arxiv.org/pdf/1904.11044.pdf) ): data is represented by 2-dim black points (on the left), the filter function here is simply a height function (projection onto the y-axis) and four intervals compose the covering of the projected space; after pulling back these intervals, i.e. taking the preimage of the filter function, we cluster each preimage in a nearest neighbour fashion. The resulting Mapper graph is depicted on the right. 

The result is a compressed graph representation of the dataset representing well its structure. High flexibility is left in this procedure to the data scientist for fine tuning: the choice of the lens, the cover and the clustering algorithm. 

##  Lenses, coverings and clustering 

The choice of the lens is of great importance since the output graph will sensibly depend on this choice. In the one-dimensional case, one could choose some height function (like in the figure above), eccentricity or centrality. 

With more dimensions typical choices are standard dimensionality reduction algorithms like PCA, Isomap, MDS,  [ t-SNE  ](https://www.jmlr.org/papers/volume9/vandermaaten08a/vandermaaten08a.pdf) or  [ UMAP  ](https://arxiv.org/pdf/1802.03426.pdf) . Density-based methods such as distance to the first k-nearest neighbors are often used in biological applications (see  [ this book  ](https://www.cambridge.org/core/books/topological-data-analysis-for-genomics-and-evolution/FCC8429FAD2B5D1525AEA47A8366D6EB) for several examples). More subtle results can be achieved by projecting to some latent space coming from a variational autoencoder. 

Depending on what type of dataset you’re analyzing, the most meaningful lenses can be applied. For example, for outlier detection it will make sense to apply a lens projecting to an isolation forest score coupled with L2 norm or first PCA component (see  [ here  ](https://kepler-mapper.scikit-tda.org/notebooks/TOR-XGB-TDA.html) for one of such examples). 

Concerning the cover, a standard choice is a collection of d-dimensional intervals (i.e. a Cartesian product of d one-dimensional intervals) of the same length pairwise overlapping with a specified percentage. This is another crucial parameter since the overlaps will determine the edge creation in the Mapper’s graph. 

Lastly you are left with the choice of your favourite clustering technique. DBSCAN or hierarchical clustering are good picks in this context. It could be tricky to choose the number of clusters as hyperparameter globally: clustering is applied to every set of points resulting from the pull-back of an element of the cover, thus there may be sets of points with different numbers of clusters to select. One solution is given by stopping the agglomerative clustering according to a rule, such as spotting the first instance of a sufficiently large gap in the dendrogram (see the  [ Mapper paper  ](https://research.math.osu.edu/tgda/mapperPBG.pdf) for more details). 

##  Mapper’s strengths 

Dimensionality reduction methods suffer from  _ projection loss  _ , that is, well separated points in high dimensional space might be projected nearby in lower dimensional space.  The advantage of Mapper is that, after choosing the lens, the covering in the projected space is  _ pulled back  _ to the original high dimensional space and clustering happens here.  This is a significant improvement with respect to dimensionality reduction since  **substructures in the original space are found and highlighted** . Therefore more pertinent clusters are generally detected. 

The topological structure of the original space where data lives is visualised directly in a  **compressed graph representation** . We emphasize the fact that we obtain a graph whose edges exhibit interesting relations between data and clusters. Interesting topological substructures like loops or flares in the mapper graphs can be explored further. 

Another winning aspect of Mapper is to  **help selecting features that best discriminate data** . Once groups or interesting connected components are found, the mapper graph allows to explore why data is interconnected: it is easy to see if nodes of the mapper graph are grouped together because certain features have similar value ranges. Thus determining the explanatory variables for the group vs the rest of the data set or vs other groups become easier. The ability to color the network by a quantity of interest, by coloring each node by the average value of the quantity on the points in the collection corresponding to the node permits the explanation of various groups and the distinction of the groups in terms of the most distinguishing variables. 

Finally, the mapper visualisation can be used also for  **model explainability** . Assume we have a classification problem and we want to better understand the false positives of our model. Then through the Mapper visualisation we can explore the data structure and get new insights to proceed to error analysis and improve our predictive model. 

![](https://www.quantmetry.com/wp-content/uploads/2020/10/fraud_model_interpretability.png)

On the left side we see a Mapper graph where red points correspond to ground truth fraud. On the right the same Mapper graph is present with now red points corresponding to predicted fraud. We can now explore where the model misclassified the fraud and characterise errors according to which clusters of the Mapper graph they belong to. This can give useful insight to understand where the model failed in the classification task. Source of the figures: [ Ayasdi – Building better models using topology ](https://www.ayasdi.com/the-shape-of-the-future-building-predictive-models-using-machine-intelligence/)

![](https://www.quantmetry.com/wp-content/uploads/2020/10/cancer_genes.png)

Feature selection with Mapper for identifying driver genes in cancer. Mapper is used to see if patients with a particular alteration present a similar expression profile. Mapper finds three distinct groups with mutated genes. A group enriched in CIC, NOTCH1 and IDH1, another enriched in IDH1 and, TP53 mutations and a last one in EGFR and PTEN mutations. Source: [ Topological Data Analysis for Genomics and Evolution ](https://www.cambridge.org/core/books/topological-data-analysis-for-genomics-and-evolution/FCC8429FAD2B5D1525AEA47A8366D6EB)

##  Our test 

We tested Mapper’s potential with the  [ Heart Disease UCI dataset  ](https://archive.ics.uci.edu/ml/datasets/Heart+Disease) , a small binary classification dataset used for predicting heart disease in patients from attributes like age, cholesterol, blood pressure, thalassemia, electrocardiographic results, etc. 

Nowadays there are a few python open source libraries implementing the main TDA tools, like  [ GUDHI  ](https://gudhi.inria.fr/) ,  [ scikit-tda  ](https://scikit-tda.org/) and  [ Giotto  ](https://github.com/giotto-ai/giotto-tda) . For our test we chose to use one of the most recent: the Giotto library, which is scikit-learn compatible, oriented towards machine learning, fast-performing with C++ state-of-the-art implementations. 

With few lines of code (in pure transformer style) it is possible to easily define a pipeline producing the Mapper graph. 
    
    
    # Define filter function
    filter_func = umap.UMAP(n_neighbors=5) 
    
    # Define cover
    cover = CubicalCover(kind='balanced', n_intervals=10, overlap_frac=0.2)
    
    # Choose clustering algorithm 
    clusterer = DBSCAN(eps=10)
    
    # Initialise pipeline
    pipe = make_mapper_pipeline(
        filter_func=filter_func,
        cover=cover,
        clusterer=clusterer,
        verbose=True,
        n_jobs=-1,
    )
    
    # Plot Mapper graph
    fig = plot_static_mapper_graph(pipe, X, color_by_columns_dropdown=True, color_variable=y)
    fig.show(config={'scrollZoom': True})

This is the result: 

![](https://www.quantmetry.com/wp-content/uploads/2020/10/heart_disease_output.png)

Mapper graph associated with the heart disease dataset. Nodes are coloured by ratio of disease. 

Here we have used the UMAP two-dimensional embedding as lens function, we took a 2-dimensional covering with 10 intervals with 0.2 overlap and we clustered with DBSCAN. 

We can see the topological structure forming some potentially interesting groupings in the Mapper graphs. Brighter points (from green to yellow) correspond to nodes with high concentration of heart disease while darker nodes have a majority of absence of heart disease. At a first sight we notice that heart disease concentrates in some regions of the graph, and separated groups of absence of disease form as well. 

We can dig deeper in discriminating features using the associated colourings for understanding better the obtained groups: 

[ ![](https://www.quantmetry.com/wp-content/uploads/2020/10/heart_disease_feat1.png) ](https://www.quantmetry.com/blog/topological-data-analysis-with-mapper/heart_disease_feat1/)
     Heart rate achieved 

[ ![](https://www.quantmetry.com/wp-content/uploads/2020/10/heart_disease_feat2.png) ](https://www.quantmetry.com/blog/topological-data-analysis-with-mapper/heart_disease_feat2/)
     Exercise induced angina 

[ ![](https://www.quantmetry.com/wp-content/uploads/2020/10/heart_disease_feat3.png) ](https://www.quantmetry.com/blog/topological-data-analysis-with-mapper/heart_disease_feat3/)
     ST depression 
  


[ ![](https://www.quantmetry.com/wp-content/uploads/2020/10/heart_disease_feat4.png) ](https://www.quantmetry.com/blog/topological-data-analysis-with-mapper/heart_disease_feat4/)
     ST slope upscoping 

[ ![](https://www.quantmetry.com/wp-content/uploads/2020/10/heart_disease_feat5.png) ](https://www.quantmetry.com/blog/topological-data-analysis-with-mapper/heart_disease_feat5/)
     Thalassemia normal 

[ ![](https://www.quantmetry.com/wp-content/uploads/2020/10/heart_disease_feat6.png) ](https://www.quantmetry.com/blog/topological-data-analysis-with-mapper/heart_disease_feat6/)
     Rest ECG left ventricular hypertrophy 
  


As you can see, Mapper increases the explainability of data: different groups are characterized by defining features and ranges. For example, features correlated with heart disease seem reasonably to be ST depression, exercise induced angina and low max heart rate achieved. 

It is interesting to notice the difference with a simple UMAP projection: as mentioned in the strengths section, Mapper gives more structure and prevents projection loss by considering the pull-back of the cover. 

![](https://www.quantmetry.com/wp-content/uploads/2020/10/umap_proj.png)

Changing from DBSCAN to hierarchical clustering changes some of the graph structure but keeps basically the splitting disease / no-disease. If we consider the projection to the first two PCA coordinates one major connected component appears where presence of heart disease shifts from one side to another (see figures below). It’s interesting to try different options and focus on the most meaningful ones. 

[ ![](https://www.quantmetry.com/wp-content/uploads/2020/10/hierarchical_clust.png) ](https://www.quantmetry.com/blog/topological-data-analysis-with-mapper/hierarchical_clust/)
     Mapper graph with hierarchical clustering 

[ ![](https://www.quantmetry.com/wp-content/uploads/2020/10/pca_lens.png) ](https://www.quantmetry.com/blog/topological-data-analysis-with-mapper/pca_lens/)
     Mapper graph with 3-components PCA lens 
  


##  Conclusion 

Mapper appears as a very promising data scientist tool either for research experimentation and for business intelligence. As our test shows, open-source libraries make it straightforward to exploit the method on complex data. Mapper graphs push one step further the exploration of data, generate interesting patterns to discover and allow to have new insights. 

Its versatility enables it to adapt to different data sources, in particular images, texts, molecules, or any data with some specific underlying structure. Finally, the resulting graph improves explainability and can be used for further network analysis. 

_The author is grateful to Nicolas Brunel and Antoine Simoulin for reading carefully a preliminary version and for their valuable comments and remarks._

Willing to know more about graphs and networks? Then these blog articles could be interesting for you: [ Introduction to graph theory and its applications ](https://www.quantmetry.com/blog/tout-est-graphe-introduction-a-une-theorie-aux-applications-multiformes/) , [ Community detection, ](https://www.quantmetry.com/blog/tout-est-graphe-detection-de-communautes-theorie-et-retour-dexperience/) [ Identifying social network influencers. ](https://www.quantmetry.com/blog/tout-est-graphe-comment-identifier-les-roles-strategiques-des-influenceurs-dun-reseau/)
