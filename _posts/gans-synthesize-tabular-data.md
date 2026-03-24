# gans-synthesize-tabular-data
Wayback Machine URL: https://web.archive.org/web/20230330205700/https://www.quantmetry.com/blog/gans-synthesize-tabular-data/
Archive date: 2023-03-30

IA de confiance, Machine Learning, Recherche et développement 

10/02/2023 

#  Data Augmentation: How do GANs synthesize tabular data in recent studies? 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fgans-synthesize-tabular-data%2F&title=Data%20Augmentation%3A%20How%20do%20GANs%20synthesize%20tabular%20data%20in%20recent%20studies%3F "Linkedin") [ ](http://twitter.com/intent/tweet?text=Data%20Augmentation%3A%20How%20do%20GANs%20synthesize%20tabular%20data%20in%20recent%20studies%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fgans-synthesize-tabular-data%2F "Twitter") [ ](https://www.quantmetry.com/blog/gans-synthesize-tabular-data/ "Email") [ ](https://www.quantmetry.com/blog/gans-synthesize-tabular-data/ "Copy Link")

* * *

Auteur : [ Anh Khoa NGO HO ](https://www.linkedin.com/in/anhkhoangoho/)

Temps de lecture : 15 minutes 

![Quantmetry.com : Data Augmentation: How do GANs synthesize tabular data in recent studies?](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/markus-winkler-irrbsnd5euc-unsplash.jpg)

“Data is the new oil” by Clive Humby highlights the importance of data in the 21  st  century. In this context, data augmentation is one of the AI trends which solves the lack of data for machine learning tasks. It is even more critical when collecting large amounts of data is difficult, especially for tabular data. Moreover, synthetic data help to protect private information contained in the original data (e.g., medical records) while sharing it with other parties and the research community. Existing applications of synthetic data include deepfake[1], oversampling for imbalanced data, and public healthcare records. 

More recently, generative models have emerged as the state-of-the-art technique in generating synthetic data, by discovering the pattern of the original data and generating new samples similar to the original data. In this article, we explore several recent studies on one of the most popular generative architectures, i.e., Generative Adversarial Network (GAN), for generating synthetic tabular data. We also discuss the challenges of the tabular data generation task and how GANs overcome these obstacles. 

#  I. Overview of GANs 

GANs are based on a game-theoretic scenario between two neural networks: a generator and a discriminator (Goodfellow, et al., 2016). The generator is a directed latent variable model deterministically generating synthetic samples from noise and tries to fool the discriminator. On the other hand, the discriminator distinguishes between real and synthetic samples of the generator (see Figure 1). 

We show a notation of GANs: 

  * Discriminator ![D_\\phi](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-159c42770a62a146441b73a560b26bc1_l3.png) : a neural network with parameters ![\\phi](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-4fb1ea7288c75ac88990d5c2da173806_l3.png)
  * Generator ![G_\\theta](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-96d19fa54e1177b4bdc8647cb3d315e6_l3.png) : a neural network with parameters ![\\theta](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-78258664e95f8ce87bb2d9a1adeb5fee_l3.png)



The objective of a vanilla GAN is ![\\min_\\theta max_\\phi v\(G_\\theta, D_\\phi\)](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-3a27f80868abe1ea3892db5ede0423a7_l3.png) where: 

![\\\[v\(G_\\theta, D_\\phi\) = E_{x \\sim p_{data}} \\log D_\\phi \(x\) + E_{z \\sim p\(z\)} \\log \(1 - D_\\phi \(G_\\theta \(z\)\)\)\\\]](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-a6795943922cf5040af8dcaa84867c82_l3.png)

  * ![x](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-c4704ca9de6180361636d38e5c10fa4a_l3.png) is sampled from the real distribution ![p_{data}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-94c47883ae7ab124ef139ed64c4c623f_l3.png) . 
  * z is noise, and the generator learns to generate samples from this noise. 
  * ![D_\\phi \(x\)](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-4919e1808e2dbc41d3126472eff4f36a_l3.png) returns the probability of being a real sample. 
  * ![E_{x \\sim p_{data}}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-6842fd5f6856b977061f2ced88eaf60a_l3.png) and ![E_{z \\sim p\(z\)}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-c51afcdbcbe94f0a09d04e9b461c7169_l3.png) are respectively the expectation with sampled from data distribution and the expectation with z sampled from its noise distribution 



For this GAN, the generator tries to increase the probability of a synthetic sample ![D_\\phi \(G_\\theta \(z\)\)](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-14fe5b5bad1bd6055ba343f16062daed_l3.png) , which means 

![\\\[\\min_\\theta v\(G_\\theta, D_\\phi\) = E_{z \\sim p\(z\)} \\log \(1 - D_\\phi \(G_\\theta \(z\)\)\).\\\]](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-b182745434b6d6a8d3cc26dddb735db9_l3.png)

On the other hand, the discriminator tries to increase the probability of a real sample and decrease the probability of the synthetic sample, 

![\\\[\\max_\\phi v\(G_\\theta, D_\\phi\) = E_{x \\sim p_{data}} \\log D_\\phi \(x\) + E_{z \\sim p\(z\)} \\log \(1 - D_\\phi \(G_\\theta \(z\)\)\).\\\]](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-ea48ff4cbf8090f92a245110be6043de_l3.png)

Note that there are several variants of GAN, e.g., Wasserstein GAN (Arjovsky, et al., 2017), PacGAN (Lin, et al., 2017), PATE-GAN (Jordon, et al., 2019), etc., which help to improve the performance of the vanilla GAN. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/picture1-300x150.png)

Figure 1: GAN structure. 

#  II. Synthetic table generation task 

Tabular data are data structured into a table form. It consists of columns and rows standing for attributes and data samples, respectively. These attributes can depend on one another and have different data types (i.e., categorical and numerical data). 

The task of synthesizing tabular data is to generate an artificial table (or multiple relational tables) based on an original tabular dataset. The synthetical table must share similar properties to the original dataset. In practice, it must satisfy the two following properties: 

  * A machine learning task on real and synthetical data must share similar performance. 
  * Mutual dependency between any pair of attributes must be preserved. Note that every sample of synthetic data must differ from the original data. 



#####  Generation task notation 

We present the notation of the generation task used in (Xu, et al., 2019). In this work, we apply GANs to learn from a single table and generate a single synthetic table. 

  * **Input** : an original table consists of ![n](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-838e41b97e5ef98519bbe6dc5a884d57_l3.png) variables (i.e., columns): ![n_c](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-b0329299a5151219d46158cd9ffb0e4b_l3.png) continuous random variables (i.e., numerical data) and ![n_d](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-3615ba6080e6c38ae5d04af16e69f57f_l3.png) discrete random variables (i.e., categorical data, ordinal data). Note that these variables follow an unknown joint distribution. ![J](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-0bfc2b6a54a7b7d06db1e0ba42f0555f_l3.png) independent samples (i.e., rows) come from this joint distribution. 
    * Columns: 
      * ![n_c](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-b0329299a5151219d46158cd9ffb0e4b_l3.png) continuous random variables: ![\\{ C_1, \\cdots , C_i, \\cdots , C_{n_c} \\}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-fa473e1ea1c312aab1e18f35eb295f2f_l3.png)
      * ![n_d](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-3615ba6080e6c38ae5d04af16e69f57f_l3.png) discrete random variables: ![\\{ D_1, \\cdots , D_i, \\cdots , D_{n_d} \\}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-b561b1b2ba1c1ee8832299c5411484a7_l3.png)
    * Row of size n at j  th  : ![\\{ c_{1,j}, \\cdots , c_{n_c,j}, d_{1,j}, \\cdots , d_{n_d, j}  \\}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-ba0069e29d563f88330d33c885bedc3c_l3.png)
    * Joint distribution: ![P\(C_{1:n_c}, D_{1:n_d}\)](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-188e3669d0745355dabed5a195a72f67_l3.png)
  * **Output** : a synthetic table ![T_{syn}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-b1bcc944999552b2174773f87827b51f_l3.png)
  * **Generative model** : ![M\(C_{1:n_c}, D_{1:n_d}\)](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-f29eab7e367949f0e752966b286c264f_l3.png) produces ![T_{syn}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-b1bcc944999552b2174773f87827b51f_l3.png)



#  III. Challenges of tabular data generation 

#####  **Different types of data**

A typical table has different types of data e.g., date-time, real numbers, or categories. Recall that synthetical data must preserve relationships of features. A generative model must learn any dependency between any pair of attributes with different data types, e.g., numerical and categorical data. Moreover, GANs must use different activation functions for the last layer, e.g., “softmax” and “tanh”. 

#####  **Different distribution forms**

Values of the attributes can be sampled from various distribution forms. E.g., multimodal, long tail, non-Gaussian distribution, etc. Our model must memorize all distribution forms in the original table and generate all attributes from these distributions for one sample. Note that some of them are difficult to be learned by GANs: normalization of non-Gaussian data (e.g., min-max transformation) can easily cause a vanishing gradient problem(Xu, et al., 2018), and a vanilla GAN hardly models the multimodal distribution of continuous variables (Srivastava, et al., 2017; Xu, et al., 2019). 

#####  **Imbalanced categorical dat** **a**

For categorical data, we can see a common issue called “Imbalanced categorical data” in that the categories are not represented equally. In this case, the discriminator struggles to distinguish samples of minor categories, e.g., it can assign these samples to fake samples. This is more important when generating synthetical data for a classification task. 

#####  **Generation of multi-tables in a database**

The task also handles multiple relational tables. In detail, a table contains at least one unique attribute called “key” which allows each row in this table to be uniquely identified and references to a row of another table. In this case, the generative model produces a list of synthetic relational tables that preserve their mutual relationships. 

#  IV. Components for generating tabular data in GANs 

In this section, we show several components used recently in GANs to overcome the challenges of tabular data generation: preprocessing methods, conditional generators, and objective function components. The preprocessing methods help to transform tabular data into neural network inputs with a suitable format. We also see how GANs produce samples for minor categories with a conditional generator. Finally, objective function components improving synthetic data quality are discussed. 

##  IV.A. Preprocessing 

For the preprocessing step, we need several reversible transformations which allow data to be efficiently fitted by a neural network model. In the case of numerical attributes, a normalization method should be applied. For example, (Xu, et al., 2019) converted these attributes into scalars ranging in ![\(-1, 1\)](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-2b39bb00412b90dc5c500c0c2e7805b6_l3.png) since they use the “tanh” activation function[2] for their neural networks. For categorical attributes, we can use one-hot-encoding and a “softmax” activation function[3] to generate probabilities of their categories. 

###  IV.A.1. Mode-specific normalization for numerical data and mixed data 

(Xu, et al., 2018) found that a simple normalization scale can lead to saturating gradient problem (Goodfellow, et al., 2016). Moreover, the datasets used in their paper consist of attributes containing multiple modes. They proposed to cluster values of a numerical attribute by using a gaussian mixture model[4] (i.e., its distribution is a weighted sum of ![m](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-b89168665e8809c440a8b041876fbc48_l3.png) multiple modes). For this approach, a numerical attribute is represented by a one-hot vector of size ![m](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-b89168665e8809c440a8b041876fbc48_l3.png) showing the probabilities of ![m](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-b89168665e8809c440a8b041876fbc48_l3.png) modes and a scalar showing its value for the highest probability mode. 

(Zhao, et al., 2021) extended this normalization method for mixed data type[5] (Sahoo, et al., 2020), i.e., the random variable consists of both continuous and categorical values, or continuous values and missing values. The value of this variable should be equitably sampled from both distribution elements. For this normalization method, they add a binary standing for categorical modes (or missing value mode) in the one-hot vector. An example is found in Figure 2. These methods can help to simplify a complex distribution. However, (Mottini, et al., 2018) found that using Gaussian mixture models for numerical attributes reduces the quality of synthetic data. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/picture2-300x202.png)

Figure 2: Mode-specific normalization for ![c_{ij}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-c5a3d167505bb15a6468febf1d8b1e7c_l3.png) : mixed data attribute (i.e., missing ![\\mu_i^0](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-40a1e9e2d4e332de85fa17dc6916c67c_l3.png) and continuous values ![\\mu_i^1](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-cf72248f515da5e881c3bfeadacf0bc5_l3.png) , ![\\mu_i^2](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-36a3008c87c1eb8dc3d47443e6026b49_l3.png) and ![\\mu_i^3](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-6c757ce3466ebcc885eb4e173d7cef34_l3.png) ) at row ![j](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-ce2467e9fa2fd5eabe11444636a65165_l3.png) . 

###  IV.A.2. Smoothing for categorical variables 

In (Xu, et al., 2018; Xu, et al., 2019), noise is added into one-hot categorical representations to remove their sparsity. They add uniform noise ![\\mathcal{N}\(0, \\gamma\)](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-8c6ca5465571331e183e414dbf578f90_l3.png) (e.g., ![\\gamma=0.2](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-952067a3c1e852677cd6bd090422afac_l3.png) ) to each cell of these one-hot vectors, and then renormalize the noised representations (see Figure 3). Note that we can avoid adding noise by using cross-networks introduced by (Wang, et al., 2017). (Mottini, et al., 2018; Engelmann, et al., 2020) use these networks to transform directly one-hot vectors into continuous vectors. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/picture3-300x115.png)

Figure 3: Smoothing for a categorical attribute ![d_{ij}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-f7c09bfdc884ea75630fbe47bc7dab34_l3.png)

###  IV.A.3. Logarithm transformation 

(Zhao, et al., 2021) proposed a logarithm transformation (FENG, et al., 2014) to deal with skewed data or long-tail distribution[6] since Gaussian mixture models hardly fit the data towards the tail. Given a lower bound ![l](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-a131b806a0ae3087eb0e86160b6058a8_l3.png) and a noise ![\\epsilon](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-f787785a8197db90408facc93d1d0456_l3.png) , they replace any initial value ![\\tau](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-9d4b8fa6e96d4c058bf2136d31d96eb6_l3.png) lower than this bound by a compressed value ![\\tau^c](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-ff94968639bdb75d179cd4224dc44f7f_l3.png) : 

![\\\[ \\tau^c \\begin{cases} \\log\(\\tau\) \\text{ if } l > 0 \\\\ \\log\(\\tau - l + \\epsilon\) \\text{ where } \\epsilon > 0 \\text{ if } l \\leq 0\\end{cases} \\\]](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-fd7b8e2ed0b54097088683c800e3539f_l3.png)

This method reduces the skewness (i.e., the distance between the tail and bulk data), which helps Gaussian mixture models to encode tail values. An example of its effect is in Figure 4. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/picture4-300x145.png)

Figure 4: Long-trail distribution before (left figure) and after logarithm transformation (right figure). 

##  IV.B. Conditional Generators 

Conditional GANs, introduced by (Mirza, et al., 2014), are constructed by feeding categorical attributes to both the generator and discriminator. They generate the rest of the features based on these categorical input attributes. This helps to rebalance the imbalanced categorical data, by generating samples for minority categories (Xu, et al., 2018; Xu, et al., 2019; Zhao, et al., 2021; Engelmann, et al., 2020). An example of a conditional generator is displayed in Figure 5. 

During training, a conditional attribute is uniformly selected. A category of this conditional feature is then selected based on the logarithm of their probabilities (i.e., frequency), which gives minor categories higher chances to sample. This approach is called “training-by-sampling” (Xu, et al., 2019) (see Figure 9). For ![n](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-838e41b97e5ef98519bbe6dc5a884d57_l3.png) categorical attributes, a conditional input vector is simply a concatenation of ![n](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-838e41b97e5ef98519bbe6dc5a884d57_l3.png) one-hot vectors of these attributes, where the cell of the selected category (of the selected feature) is set to 1. We can apply this approach to continuous skewed data by selecting minor modes after mode-specific normalization. We can notice that tackling data imbalance improves the performance of the discriminator, and in general, it returns correct feedback for the generator. 

![Conditional generator with a conditional vector](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/picture5-300x166.png)

Figure 5: Conditional generator with a conditional vector. There are two categorical attributes in this example data and the generator produces a synthetic sample for category 1 of attribute 2. 

##  IV.C. Classifier for semantic integrity 

(Park, et al., 2018; Zhao, et al., 2021) concentrated on preserving correlations between categorical attributes and others. For each feature, a neural network classifier ![C](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-6021ff0baf6a073fa48c36ac59d4c344_l3.png) pre-trained on the original data gives feedback to the generator: a categorical feature is predicted based on the rest of the features. In this case, the loss of a classifier means the discrepancy between the generated category and the category predicted by the classifier. This loss is added to the main objective function of GANs: 

![\\\[L_{class}^G = E_{z \\sim p\(z\)} \(| l\(G\(z\)\) - C\(remove\(G\(z\)\)\) |\)\\\]](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-0a63210278210c11264c1e91c48a8c6d_l3.png)

where ![remove\(\)](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-658c1c5c8013cd0502940126cddc785f_l3.png) removes the label of an attribute for a sample and ![l\(\)](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-ae280ac65b1abe84a6166f347165e92e_l3.png) returns this label. Note that these classifiers can share the same intermediate layers. (Zhao, et al., 2021) confirmed that this approach improves machine learning efficacy. 

##  IV.D. Information loss 

Besides classification loss, (Park, et al., 2018) also introduced information loss which is the distance between the synthetic and original data. It measures how close synthetic data is to the original one, which shows the privacy of the synthetic data. In detail, this loss matches the mean ![E](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-29b787dada8ba9dd4ad7fa6c52b9ec47_l3.png) and the standard deviation ![SD](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-70c3878809bc10709f83d7e7a42e4f61_l3.png) of each sample. This loss is also added to the main objective function of GANs. (Park, et al., 2018; Zhao, et al., 2021) proved that it improves training stability since it guides the generator to reconstruct ground-truth values. 

![\\\[L_{mean} = || E_{x \\sim p_{data} f\(x\)} - E_{z\\sim p\(z\)} f\(G\(z\)\)||_2\\\]](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-cc98970da7ba940fa97c81addf3d3116_l3.png)

![\\\[L_{sd} = || SD_{x \\sim p_{data} f\(x\)} - SD_{z\\sim p\(z\)} f\(G\(z\)\)||_2\\\]](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-39cccf2fa69ca2e66368e7bc354cb7b0_l3.png)

where ![f\(\)](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-9fa78a4c8902acbae6ec8c6dcd1c0157_l3.png) returns the features fed into the softmax layer of ![D](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-ba79d129c87d15fcdc780d747411ccae_l3.png) . 

#  V. Recent studies 

In this section, we discuss several remarkable variants of GAN such as MedGAN, Table-GAN, TGAN/CTGAN, and CTAB-GAN. Most of the models apply the components mentioned in the previous section to overcome the challenges of generating synthetic tables e.g., data with different types, long tail/multimodal distribution, and imbalanced data. 

#####  MedGAN 

**MedGAN** , proposed by (Choi, et al., 2017), generates discrete attributes of patient records (e.g., binary and count features). Recall that the vanilla GAN only processes continuous variables. To overcome this limitation, they pre-train an autoencoder (Goodfellow, et al., 2016) on the original data. Basically, an autoencoder is built to reconstruct the input samples: 

  *     * first it compresses data via an encoder projecting them into lower dimensional space, 
    * then it expands the information via a decoder projecting them back to the input space. 



This decoder helps to transform the continuous output of the generator (a feedforward neural network) into discrete variables (Figure 6). These variables are then fed into the discriminator. They also found that the discriminator trained without explicit rounding of these variables gives better performance than with rounding. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/picture6-300x188.png)

Figure 6: In MedGAN, the decoder ![Dec\(\)](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-515175b618d66437a5e724533af5a2b4_l3.png) of the autoencoder (reconstructing the input) is reused to transform the continuous output of the generator into the original format (i.e., a synthetic sample with discrete variables). 

#####  Table-GAN 

**Table-GAN** of (Park, et al., 2018) focuses on privacy and semantic integrity. Therefore, they introduced information loss (see D) to control the privacy level of the generated data and the loss of classifiers (see V.C) to preserve correlations between categorical features and the rest of the features. To control privacy, they added a threshold of the mean ![\\delta_{mean}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-cd34cca2fbb6c2f6f739c69000872535_l3.png) and the standard deviation ![\\delta_{sd}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-2f6f3c64835f683e972c2013dd9798e7_l3.png) of features into the information loss. 

![\\\[L_{info}^G = \\max\(0, L_{mean} - \\delta_{mean}\) + \\max\(0, L_{sd} - \\delta_{sd}\)\\\]](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-aef513d52ce7a247e003eee1acce5cc9_l3.png)

Different from MedGAN, this model is based on convolutional neural networks (CNNs)(Goodfellow, et al., 2016) where a sample is represented by a matrix of features. In detail, the generator includes deconvolutional layers (i.e., from a noise vector to a matrix of features) and the discriminator includes convolutional layers (i.e., from the matrix of features to a probability), as shown in Figure 7. They concluded that CNNs can help to capture the correlations between features. However, it is unclear whether different matrix representations (i.e., different orders of the attributes) return the same generation performance. Based on their experiments, they found that using the original vector format leads to a sub-optimal performance due to its limited convolution computations. 

![Table-GAN based on CNNs](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/picture7-300x62.png)

Figure 7: Table-GAN based on CNNs: the generator and the discriminator follow deconvolution and convolution processes, respectively. Source: (Park, et al., 2018). 

#####  TGAN and CTGAN 

**TGAN** (Xu, et al., 2018) generates features one by one (following their original order in the table) by using an LSTM[7] (Hochreiter, et al., 1997; Graves, 2013; Goodfellow, et al., 2016). These models use mode-specific normalization for numerical data (see A.1) and smoothing for categorical data (see V.A.2). In this case, the LSTM-based generator returns these values ![v_{1:n_c,j}, u_{1:n_c,j}, d_{1:n_d,j}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-6eb625af84b392458e414cf067093799_l3.png) one by one for each row ![j](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-ce2467e9fa2fd5eabe11444636a65165_l3.png) . Note that this model also uses an attention mechanism ![a_{1:n_c}, a_{1:n_c}, a_{1:n_d}](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-0ffcad13eb1fb20a3c220637e9067a6c_l3.png) to weight the relationships between the current attribute to the previously generated features. An example of TGAN is displayed in Figure 8. 

![example of TGAN](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/picture8-300x165.png)

Figure 8: An example of TGAN for two numerical features and two categorical features. The model generates each component of numerical features and a value of categorical features one by one. Each output (e.g., ![d_1](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-ff3adc59a16ddc5530a119da5a55cdcc_l3.png) ) is based on a noise vector ![z](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-0a070b0c7dfed77cd4ee8de32f537611_l3.png) , the previously generated output (e.g., the representation before activation function ), and an attention matrix (e.g., ![a_2](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-3e4ba84d44c74d3a207e5d4442fc0dc2_l3.png) ). ![v](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-d4ccd0c2ec1d1439acae17f02e30d9cc_l3.png) and ![u](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-411f7d22b3b4c61d1a91c3d63c010a99_l3.png) are the two elements for a numerical attribute (mode-specific normalization) and ![d](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-11c8e4dacef3cf0f9927d1e4c3d009c4_l3.png) stands for a categorical attribute. Source: (Xu, et al., 2018). 

Considering tabular data as a sequence of features by using LSTM is computationally less efficient and does not perform better than a simple feedforward neural network (Engelmann, et al., 2020). Moreover, the lack of an appropriate order of generating features can lead to an incorrect correlation between them. Therefore, their follow-up **CTGAN** (Xu, et al., 2019) uses feedforward neural networks for their generator and their discriminator. Moreover, it is based on the Wasserstein GAN, which improves the performance of the GAN (Arjovsky, et al., 2017). CTGAN also includes a conditional generator, tackling the data imbalance. We show the architecture of CTGAN in Figure 9. 

![CTGAN architecture](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/picture9-300x108.png)

Figure 9: CTGAN architecture. Critic C(.) replaces the role of the discriminator for Wasserstein GAN. We can see how a conditional vector is constructed. ![D_1](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-d29364854cba63297b0027327e173556_l3.png) and ![D_2](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-87d3e456aca02461e434fa7d38816d2d_l3.png) are categorical attributes. ![\\alpha](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-3826e29eb436f6f2a5e7f16f9f6c7538_l3.png) and ![\\beta](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-5437f5621533cfecea6c943a00b52cab_l3.png) are the two elements for a numerical attribute (mode-specific normalization) and ![d](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-11c8e4dacef3cf0f9927d1e4c3d009c4_l3.png) stands for a categorical attribute. Source: (Xu, et al., 2019). 

#####  CTAB_GAN 

**CTAB-GAN** of (Zhao, et al., 2021) uses an extended version of mode-specific normalization, which processes the mixed data. It includes a classifier (a feedforward neural network) for semantic integrity and computes the information loss to improve training stability. The generator and the discriminator are based on the architecture of Table-GAN (i.e., CNNs). 

In addition, we should mention the work of (Engelmann, et al., 2020): their CWGAN is based on a conditional Wasserstein GAN (Arjovsky, et al., 2017) and a cross-network (Wang, et al., 2017) for data oversampling. (Rajabi, et al., 2021) would like to improve the fairness in data (e.g., all genders should have a similar salary). The objective function of their model TabFairGAN includes fairness constraints: penalizing the difference of an attribute (e.g., salary) between different categories (e.g., female and male). 

#  VI. Conclusions 

In this article, we explored the components used in recent studies that help GANs overcome the challenges in tabular data generation. 

  * Mode-specific normalization and smoothing methods are for pre-processing different data types, which helps GANs to easily learn tabular data. 
  * Conditional generators and the training-by-sampling improve the data generation performance by rebalancing the data input. 
  * Classification and information loss help to preserve feature correlation, control data privacy and improve training stability. 



These recent studies broaden the ability of GANs in data augmentation. In fact, collecting large-size tabular data is hard and time-money consuming, especially medical records and customer data. GANs can produce good-quality synthetic data for under-resourced applications. This can improve the performance of machine learning models and reduce the problem of imbalanced and skewed data. Many clients of Quantmetry must deal with their low-resource data, hence GANs open a highway to overcome the lack of data and enhance the performance of their tasks. 

One remaining challenge is the generation of multi-tables in a database, where GANs can handle unique keys (i.e., it must learn how all the attributes from all the generated tables are related through these keys). Another difficult problem is how to add constraints into synthetic data e.g., an attribute must be positive, negative, or in an interval; all values of an attribute are always larger/smaller than the values of another attribute; etc. More work is needed there to design GAN components and generation strategies that overcome these obstacles. 

I would like to extend my sincere thanks to Ali JABBARI, Grégoire MARTINON, Cyril LEMAIRE, Louis LACOMBE, and Geoffray BRELURUT for constructive criticism of this blog article. 

#  VII. Bibliography 

**Goodfellow Ian, Bengio Yoshua and Courville Aaron** Deep Learning [Book]. – [s.l.] : MIT Press, 2016. 

**Xu Lei [et al.]** Modeling Tabular Data using Conditional GAN [Conference]. – 2019. 

**Zhao Zilong [et al.]** CTAB-GAN: Effective Table Data Synthesizing [Conference]. – 2021. 

**Sahoo Saswata and Chakraborty Souradip** Learning Representation for Mixed Data Types with a Nonlinear Deep Encoder-Decoder Framework [Journal]. – 2020. 

**Srivastava Akash [et al.]** VEEGAN: Reducing Mode Collapse in GANs using Implicit Variational Learning [Conference] // NIPS. – 2017. 

**Xu Lei and Veeramachaneni Kalyan** Synthesizing Tabular Data using Generative Adversarial Networks. – 2018. 

**Wang Ruoxi [et al.]** Deep & Cross Network for Ad Click Predictions [Conference] // AdKDD and TargetAd. – 2017. 

**Mottini Alejandro, Lheritier Alix and Acuna-Agost Rodrigo** Airline Passenger Name Record Generation using Generative Adversarial Networks [Conference] // ICML 2018 – Workshop on Theoretical Foundations and Applications of Deep Generative Models. – 2018. 

**Engelmann Justin and Lessmann Stefan** Conditional Wasserstein GAN-based Oversampling of Tabular Data for Imbalanced Learning. – 2020. 

**Mirza Mehdi and Osindero Simon** Conditional Generative Adversarial Nets. – 2014. 

**Park Noseong [et al.]** Data Synthesis based on Generative Adversarial Networks [Conference] // VLDB. – 2018. 

**Arjovsky Martin, Chintala Soumith and Bottou Léon** Wasserstein GAN. – 2017. 

**Lin Zinan [et al.]** PacGAN: The power of two samples in generative adversarial networks. – 2017. 

**Jordon James, Yoon Jinsung and Schaar Mihaela van der** PATE-GAN: Generating Synthetic Data with Differential Privacy Guarantees [Conference] // ICLR 2019 Conference. – 2019. 

**Choi Edward [et al.]** Generating Multi-label Discrete Patient Records using Generative Adversarial Networks [Conference] // Machine Learning in Health Care (MLHC). – 2017. 

**Hochreiter Sepp and Schmidhuber Jürgen** Long Short-Term Memory [Conference] // Neural Computation. – 1997. 

**Graves Alex** Generating Sequences With Recurrent Neural Networks. – 2013. 

**Rajabi Amirarsalan and Garibay Ozlem Ozmen** TabFairGAN: Fair Tabular Data Generation with Generative Adversarial Networks. – 2021. 

**C Feng [et al.]** Log-transformation and its implications for data analysis [Journal]. – [s.l.] : Shanghai Arch Psychiatry, 2014. 

[1] [ https://en.wikipedia.org/wiki/Deepfake ](https://en.wikipedia.org/wiki/Deepfake)

[2] [ https://www.ml-science.com/tanh-activation-function ](https://www.ml-science.com/tanh-activation-function)

[3] [ https://en.wikipedia.org/wiki/Softmax_function ](https://en.wikipedia.org/wiki/Softmax_function)

[4] [ https://scikit-learn.org/stable/modules/mixture.html ](https://scikit-learn.org/stable/modules/mixture.html)

[5] A nice presentation about mixed data type: [ https://www.ima.umn.edu/materials/2018-2019/SW11.7-9.18/27702/Markatou_IMA_November2018.pdf ](https://www.ima.umn.edu/materials/2018-2019/SW11.7-9.18/27702/Markatou_IMA_November2018.pdf)

[6] [ https://en.wikipedia.org/wiki/Long_tail ](https://en.wikipedia.org/wiki/Long_tail)

[7] [ https://en.wikipedia.org/wiki/Long_short-term_memory ](https://en.wikipedia.org/wiki/Long_short-term_memory)

[ ![Reliable Ai](https://quantmetry.b-cdn.net/wp-content/uploads/2022/06/Logo-Expertise-Reliable-Ai.svg) ](https://www.quantmetry.com/experts/#reliableia)

Les membres de l’ [ expertise Reliable AI ](https://www.quantmetry.com/experts/#reliableia) développent des modèles performants, fiables et maîtrisés, sur l’ensemble du cycle de vie, pour une IA de confiance. 

* * *

![Anh Khoa NGO HO](https://quantmetry.b-cdn.net/wp-content/uploads/2022/10/12038086-1096919003654671-1999639680772938750-n.jpg)

[ Anh Khoa NGO HO  ](https://www.linkedin.com/in/anhkhoangoho/)

Data Scientist chez Quantmetry 

PhD in Computer Science and Natural Language Processing. Passionate about Deep Learning and generative models, I work in a research team at Quantmetry which develops state-of-the-art methods to solve industrial problems. I am also part of the trusted AI expertise whose objective is to develop efficient, reliable and controlled models, over the entire life cycle, for trusted AI. 
