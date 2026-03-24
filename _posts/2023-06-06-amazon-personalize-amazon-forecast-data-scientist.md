---
layout: post
title: amazon-personalize-amazon-forecast-data-scientist
date: 2023-06-06
url_wayback_machine: https://web.archive.org/web/20230606090437/https://www.quantmetry.com/blog/amazon-personalize-amazon-forecast-data-scientist/
---
Time Series 

23/09/2019 

#  Amazon Personalize, Amazon Forecast : quel rôle pour le Data Scientist ? 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Famazon-personalize-amazon-forecast-data-scientist%2F&title=Amazon%20Personalize%2C%20Amazon%20Forecast%20%3A%20quel%20r%C3%B4le%20pour%20le%20Data%20Scientist%20%3F "Linkedin") [ ](http://twitter.com/intent/tweet?text=Amazon%20Personalize%2C%20Amazon%20Forecast%20%3A%20quel%20r%C3%B4le%20pour%20le%20Data%20Scientist%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Famazon-personalize-amazon-forecast-data-scientist%2F "Twitter") [ ](https://www.quantmetry.com/blog/amazon-personalize-amazon-forecast-data-scientist/ "Email") [ ](https://www.quantmetry.com/blog/amazon-personalize-amazon-forecast-data-scientist/ "Copy Link")

* * *

Temps de lecture : 4 minutes 

![Quantmetry.com : Amazon Personalize, Amazon Forecast : quel rôle pour le Data Scientist ?](https://quantmetry.b-cdn.net/wp-content/uploads/2019/09/article-gho-min.png)

Mardi 4 Septembre 2019, Quantmetry était présent chez D2SI au [ Meetup AWS User group ](https://www.meetup.com/fr-FR/French-AWS-UG/) présenté par [ Megan BOS ](https://www.linkedin.com/in/megan-bos-4b450041/) , Global Business Development Manager for  [ **Amazon Personalize** ](https://aws.amazon.com/fr/personalize/) & [ **Amazon Forecast** ](https://aws.amazon.com/fr/forecast/) . 

Megan était venue présenter ces deux services, dont une version préliminaire avait été annoncée à [ re:Invent 2018 ](https://aws.amazon.com/fr/new/reinvent/) . 

A l’image d’autres services IA d’AWS, Amazon Personalize et Amazon Forecast promettent la mise en production d’API de manière rapide (moins de 2h) et intuitive. Selon AWS, aucun data scientist n’est requis pour utiliser ces services managés. De cette manière, AWS assure à ses clients et à ses utilisateurs une démocratisation de l’IA/du ML. 

####  Amazon Personalize 

Actuellement, un client qui souhaite implémenter un moteur de recommandation a deux choix : soit le développer en interne, soit outsourcer le développement auprès d’un prestataire. Personalize souhaite se positionner comme entre-deux : développer en interne grâce à des technologies Amazon. 

Personalize s’intègre évidemment à tout l’écosystème AWS. Les données exploitées en entrée du pipeline de traitement sont stockées sur S3 et la partie AutoML est assurée par Sagemaker. 

![Amazon Personalize pipeline](https://quantmetry.b-cdn.net/wp-content/uploads/2019/09/Amazon-Personalize-pipeline.png)

En entrée, le pipeline de traitement attend une donnée  _ cleanée  _ / formattée. On remarque que la configuration de la métrique de performance n’est pas prise en compte par la partie AutoML. Les métriques de performance utilisées sont détaillées [ ici ](https://docs.aws.amazon.com/fr_fr/personalize/latest/dg/working-with-training-metrics.html) . 

Amazon Personalize souhaite répondre aux problèmes récurrents liés à l’implémentation de tels moteurs de recommandations : 

  * **Refléter précisément le contexte et le comportement des utilisateurs**
  * **S’adapter en temps réel** aux intentions des utilisateurs 
  * Faire des recommandations pertinentes aux  **nouveaux utilisateurs**
  * Les  **nouveaux articles** doivent intégrer les recommandations malgré le manque de données sur leur popularité 



Assurer le  **passage à l’échelle** sur des milliers d’utilisateurs et de produits, le tout, à moindre frais : 

**Type de dépenses** |  **Prix**  
---|---  
Générer des recommandations  |  voir détail [ ici ](https://aws.amazon.com/fr/personalize/pricing/)  
Ingestion de données  | 
    
    
    *** QuickLaTeX cannot compile formula:
    0.05 par GB</span></td>
    </tr>
    <tr>
    <td><span style="font-weight: 400;">Temps d'entraînement</span></td>
    <td><span style="font-weight: 400;">
    
    *** Error message:
    Please use \mathaccent for accents in math mode.
    leading text: ... style="font-weight: 400;">Temps d'entraî
    
    

0.24 par heure   
  
** Exemple d’un cas d’usage réalisé :  **

Basé sur l’historique d’achat et les données clients, un food retailer propose des offres promotionnelles adaptées : au moment le plus opportun (une demi-heure avant l’heure d’un repas par exemple), avec le produit le plus opportun (tel ou tel plat). 

Les secteurs du retail classique, de la banque, de l’immobilier ou encore des médias regorgent de use cases où Amazon Personalize peut être utilisé. 

####  Amazon Forecast 

Amazon Forecast est récent dans la stack AWS : la version opérationnelle du service a été lancée en août 2019. Forecast, adapté aux problèmes de  _ forecasting  _ , poursuit les mêmes objectifs que Personalize : démocratiser le ML en proposant un service managé se basant sur les technologies AWS. 

Ce service se concentre sur les problèmes liés au S&OP (voir notre [ article ](https://www.quantmetry.com/evolution-outils-methodes-forecast-quelles-perspectives-sop-demain/) ) : 

  * Prévisions des ventes lors du démarrage d’un nouveau produit 
  * Prise en compte de la saisonnalité 
  * Intégration de variables exogènes aux données : variations des prix, événement de l’année (fêtes et jours fériés). 



Pour obtenir des prévisions fiables, le nombre de séries temporelles nécessaires est de l’ordre du millier. 

L’architecture d’AWS Forecast est sensiblement la même que celle de Personalize : 

![Amazon Forecast pipeline](https://quantmetry.b-cdn.net/wp-content/uploads/2019/09/Amazon-Forecast-pipeline.png)

Le choix de l’algorithme final se fait parmi une sélection de cinq algorithmes : deux de Deep Learning (dont DeepAR, dont nous parlerons dans un prochain article) et trois de modèles statistiques (dont Prophet et ETS). L’utilisateur a la possibilité de configurer les hyperparamètres de ces modèles afin d’optimiser les prédictions réalisées. 

La gestion du cycle de vie du modèle et les stratégies de réentraînement sont laissés à la charge de l’utilisateur : il est donc nécessaire d’avoir des connaissances en Machine Learning pour faire perdurer son API dans le temps. D’autant que la facturation est plus élevée que pour Personalize : 

**Type de dépenses** |  **Prix**  
---|---  
Générer des forecasts  | 
    
    
    *** QuickLaTeX cannot compile formula:
    0.60 par 1 000 forecasts</span></td>
    </tr>
    <tr>
    <td><span style="font-weight: 400;">Ingestion de données</span></td>
    <td><span style="font-weight: 400;">
    
    *** Error message:
    Please use \mathaccent for accents in math mode.
    leading text: ...le="font-weight: 400;">Ingestion de donné
    
    

0.088 par GB   
Temps d’entraînement  |  $0.24 par heure   
  
De notre point de vue, l’affirmation qu’aucun data scientist n’est nécessaire à la mise en place de ces process nous semble un peu optimiste. Etant donné que la grande majorité du travail du data scientist dans une première itération projet est la phase de cleaning, d’enrichissement et de sélection de données, il est dur d’imaginer un forecast pertinent et performant sans donnée d’entrée de qualité. 

Si le cas d’usage est très simple, encore faudra-t-il avoir un minimum de connaissance dans les services AWS afin de paramétrer correctement la chaîne complète. 

Au final, la phase automatisée représente une partie mineure de la chaîne de valeur de la donnée, chaîne où un data scientist a bien entendu toute sa place. 

La mise en place de ce service managé peut être séduisante pour la simplicité apparente de son implémentation, mais doit bien sûr être évaluée au regard de l’utilisation qui en est faite par les utilisateurs finaux, de la fréquence de prédiction et de mise à disposition des données. Le coût d’appel peut vite faire monter la facture, et l’utilisation d’autres services AWS peut être alors plus avantageux. 

**Références**

[ https://docs.aws.amazon.com/fr_fr/personalize/latest/dg/what-is-personalize.html  ](https://docs.aws.amazon.com/fr_fr/personalize/latest/dg/what-is-personalize.html)

[ https://docs.aws.amazon.com/fr_fr/forecast/latest/dg/what-is-forecast.html  ](https://docs.aws.amazon.com/fr_fr/forecast/latest/dg/what-is-forecast.html)

#####  ✍Article écrit par [ Antoine de Daran ](https://www.linkedin.com/in/antoine-de-daran/?locale=en_US) et [ Guillaume Hochard ](https://www.linkedin.com/in/guillaume-hochard-phd-5580589/)
