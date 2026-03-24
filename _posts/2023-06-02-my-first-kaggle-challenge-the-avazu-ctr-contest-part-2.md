---
layout: post
title: my-first-kaggle-challenge-the-avazu-ctr-contest-part-2
date: 2023-06-02
url_wayback_machine: https://web.archive.org/web/20230602191833/https://www.quantmetry.com/blog/my-first-kaggle-challenge-the-avazu-ctr-contest-part-2/
---
Uncategorized 

20/03/2015 

#  My first Kaggle challenge : the Avazu CTR contest - Part 2 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmy-first-kaggle-challenge-the-avazu-ctr-contest-part-2%2F&title=My%20first%20Kaggle%20challenge%20%3A%20the%20Avazu%20CTR%C2%A0contest%20-%20Part%202 "Linkedin") [ ](http://twitter.com/intent/tweet?text=My%20first%20Kaggle%20challenge%20%3A%20the%20Avazu%20CTR%C2%A0contest%20-%20Part%202&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fmy-first-kaggle-challenge-the-avazu-ctr-contest-part-2%2F "Twitter") [ ](https://www.quantmetry.com/blog/my-first-kaggle-challenge-the-avazu-ctr-contest-part-2/ "Email") [ ](https://www.quantmetry.com/blog/my-first-kaggle-challenge-the-avazu-ctr-contest-part-2/ "Copy Link")

* * *

Temps de lecture : 6 minutes 

![Quantmetry.com : My first Kaggle challenge : the Avazu CTR contest - Part 2](https://quantmetry.b-cdn.net/wp-content/uploads/2015/03/clavier.jpg)

##  Introduction 

In October 2014, Kaggle launched a new challenge, about optimizing click-through rate prediction (CTR) based on event data provided by Avazu Inc. I embarked on a long journey for doing my best on the challenge up to its end in February 2015. I joined forces along the way with Christophe Bourguignat, and we teamed up as « The Good Timers ». 

I have published a first article a week ago. Mostly, the algorithms which have proven effective are in the family of logistic regressions, and I will explain in this second article how we have used them, which variants we have used, and then compare with alternative methods. 

##  Preliminary remarks 

We find that this dataset is quite representative of big data: you have a lot of data, but indeed you get some strong signals (strong trends, such as the data “type of mobile phone” gives you) combined with very weak signals, brought by a very small number of samples, sometimes down to 100 amongst 40M, thus lost in an ocean of strong signals and strong noise. The complete story can be told by listening both to a few strong signals and a lot of very weak ones. Online linear algorithms have proved very effective at exploiting the two types of signals – and you need to do so in order to be in the first half of the competing teams! The caveat is that you must tune them carefully and go around their limitations – mainly being linear. 

Logistic regression is old-fashioned and not considered as very powerful. You apply it to a few simple textbook classification problems, and then you move on to more powerful algorithms. Right? Wrong! You can do a lot with linear model if you know how to use them. 

##  Algorithms 

Correct convergence is key with logistic regression. We tried three different linear learner algorithms, with three implementations, and at the end our best post was an ensemble of the three of them. 

We began with Vowpal Wabbit, which is implementing an improved version of AdaGrad in a powerful and efficient C++ engine. We did not have much success at first, but we came back to it at the end with a better learning rate – and then it performed much better. 

When Vowpal did not look promising anymore, we turned to FTRL-Proximal. FTRL-Proximal is an algorithm for training large scale logistic regressions, developed for CTR prediction (refer for instance to [ this paper ](http://jmlr.org/proceedings/papers/v15/mcmahan11b/mcmahan11b.pdf) ). 

In the situation where some features are seen a lot (millions of instances), and others are very rare (a few hundred’s or less), you don’t want to the same learning rate. FTRL-Proximal adapts the learning rate by slowing the learning feature per feature in relation with the gradient you are going through. As we decided to use it, tinrtgu published an adaptation of his Python code based on FTRL-Proximal. We downloaded it, and embarked on a long journey of additions and tuning, but still keeping the basic architecture and FTRL-Proximal powerful gradient descent. 

Something common to Vowpal and FTRL Proximal: you get many meta-parameters, and you need to test and tune them. Tuning on a reduced data set (one day vs ten days) helped, but was not enough, and we had to run full set tests to get to improved performance. Again: tuning meta-parameters is crucial on Vowpal and FTRL. On FTRL, you must find the correct values for two convergence parameters, two regularization parameters, the dropout rate and the number of epochs. 

When we felt we had gone as far as we could get with FTRL Proximal, we looked for another algorithm. [ Reviewing the literature ](https://www.microsoft.com/en-us/research/publication/web-scale-bayesian-click-through-rate-prediction-for-sponsored-search-advertising-in-microsofts-bing-search-engine/) on CTR led us to AdPredictor. 

AdPredictor is a Bayesian algorithm, developed by Microsoft for Bing. A nice property of Bayesian algorithms is that you maintain a record of the confidence you have on your learned weights along with the best estimates themselves. This means that when you learn the weights per feature, you get a different gradient descent per feature and an estimate of the confidence per feature. 

We then implemented AdPredictor as an addition to the same Python program, based on two other implementations: in Python and Java. From the start AdPredictor performed better than FTRL Proximal, and it proved very robust. Also, it required tuning only one parameter, as opposed to at least six for FTRL Proximal. 

##  Adding non-linearity 

Basically, the issue of determining click probability is not linear: it can depend on the application plus the position of the banner, plus the type of device, with no possible separation of the variables. By adding combination quadratic (like: type of device plus position of banner) or cubic features, you somewhat capture part of the complexity you would get with a 2-3 levels tree, or a 2-3 layers neural network. It improved the predictive performance of the model a lot, while still keeping a decent run time (under a few hours in total). 

As an additional non-linearity, we separated the data set to train several models: for instance, train a different model on event referring to using an application on a mobile phone as opposed to a web site. Ensembling such a model with full-set trained learners improved performance. 

##  Improving with feature engineering 

More or less, all competing teams used the same algorithms, except for AdPredictor and libFM: variants of stochastic gradient descent for logistic regressions. The huge differences in results mostly came from feature engineering. It proved difficult with lots of anonymous features (C12, C13, C14 and so on) with scrambled values (4e5fa7c, …). What we did was mostly counting of occurrences: adding the number of times we have seen this device_id, or this device_ip in the data set, or in the same day, or in the same hour, or in combination with the visited app_id or site_id. Together with the ensembling of different models, this earned our team the 22th position on the private leaderboard (amongst 1700 teams). 

A first review of the winning methods showed a lot of creativity, and we shall write something later on this blog about the most interesting or creative feature engineering procedures in this contest. 

##  What did not work 

Finally, we will describe some more methods we tested and did not found to perform. 

Tree-based algorithms like Random Forest, Extra Trees and Gradient Boosting are difficult to run on this dataset due to the sparsity of the features and the number of samples. We ran the scikit-learn implementations of Random Forest and Extra Trees on samples, but we got quite low performance. xgboost proved more promising for gradient boosting and boosted logistic regression , and could be run on 5 days of samples, but again the performance never got farther than 0.400 (very low down on the leaderboard). 

We also tested a two-stage model, by preparing features with either a tree-based model (Gradient Boosting, Random Forest) as in Practical Lessons from Predicting Clicks on Ads at Facebook, or [ with a Naive Bayes ](http://nlp.stanford.edu/pubs/sidaw12_simple_sentiment.pdf) , and again got quite poor performance. It seems some of the winning team exploited this type of procedure along with other algorithms. It will be interesting to explore how you can get this right, and combine the procedure with other types of feature engineering. 

Neural networks also proved disappointing: the neural network option on Vowpal Wabbit proved to be very slow, and overfitted a lot. Regularization would have certainly helped, but finding the correct parameters was tricky so we decided to focus on logistic regression. 

We also tried some forms of feature reduction, with LRQ on Vowpal, but again with weak results. We were somewhat persuaded from start that feature reduction would tend to crush the weak signals, leaving only the strong signals. The good results obtained with Factorization Machines could prove this is wrong, or maybe it means you need to combine adequate feature preparation (to capture the weak signals) and then you can perform dimensionality reduction. This will require further investigation. 

##  Conclusion 

I am convinced that you enter a Kaggle contest mainly for the learning experience: nothing is worth playing on a real-life data set, exploring and doing you best with competition from thousands of teams around the world. For those with a competitive spirit, this lead to tuning models till the last minutes, and along the path you learn a lot about the business problem and data science. 

The Avazu CTR challenge was clearly worth investing in as it provided a playing ground for methods, algorithms and libraries on a (moderately) big data set, with a multi-billion dollars business motivation. The lessons and insights learned here can be applied to similar click-through problems, as well as other time series events, such as web navigation logs analysis. 
