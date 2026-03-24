---
layout: post
title: pourquoi-ecrire-ensemble
date: 2023-06-06
url_wayback_machine: https://web.archive.org/web/20230606084839/https://www.quantmetry.com/blog/pourquoi-ecrire-ensemble/
---
Uncategorized 

27/09/2017 

#  Pourquoi écrire ensemble ? 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fpourquoi-ecrire-ensemble%2F&title=Pourquoi%20%C3%A9crire%20ensemble%20%3F "Linkedin") [ ](http://twitter.com/intent/tweet?text=Pourquoi%20%C3%A9crire%20ensemble%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fpourquoi-ecrire-ensemble%2F "Twitter") [ ](https://www.quantmetry.com/blog/pourquoi-ecrire-ensemble/ "Email") [ ](https://www.quantmetry.com/blog/pourquoi-ecrire-ensemble/ "Copy Link")

* * *

Temps de lecture : 3 minutes 

![Quantmetry.com : Pourquoi écrire ensemble ?](https://quantmetry.b-cdn.net/wp-content/uploads/2017/09/shutterstock_407505397.jpg)

Cet article fait partie d’une série d’articles co-rédigés par [ Emmanuel Manceau ](https://www.linkedin.com/in/emmanuelmanceau/) ( [ Quantmetry ](http://www.quantmetry.com/) ), [ Olivier Denti ](https://www.linkedin.com/in/olivierdenti/) ( [ Quantmetry ](http://www.quantmetry.com/) ) et [ Magali Barreau-Combeau ](https://www.linkedin.com/in/magalibc/) ( [ OVH ](https://www.ovh.com/fr/) ) sur le sujet « Architecture – De la BI au Big Data » 

##  Introduction 

Ces articles sont le fruit d’une rencontre lors d’un petit déjeuner chez Dataiku. Je présentais le fruit de nos réflexions et de notre retour d’expérience sur l’industrialisation des projets data et Magali témoignait pour OVH sur l’organisation de la donnée chez OVH. 

Je plaidais depuis longtemps en faveur d’une structuration des données dans le datalake en les modélisant. Ce discours n’était pas bien compris jusqu’ici par les datascientist avec qui je travaillais. L’argument que j’entendais le plus souvent est : « Mais pourquoi se fatiguer à modéliser les données, on stocke l’information brute dans le datalake et ça suffit ». 

J’avais pour moi l’expérience de plusieurs projets où effectivement, nous étions partis d’une information brute contenue dans un datalake et nous avions eu toutes les peines du monde à lui donner du sens. La réalité des projets data, c’est que nous n’utilisons qu’une partie infime des données d’un datalake (pas toujours la même d’un projet à l’autre, raison pour laquelle on stocke tout préventivement) et qu’il est absolument nécessaire de redonner du sens à la donnée pour l’utiliser en entrée des modèles. Aucun datascientist n’utilise de la donnée brute en entrée d’un modèle de machine learning. 

Aussi, lorsque j’ai entendu Magali nous expliquer comment OVH avait structuré l’information dans son datalake, en organisant plusieurs couches de traitement et de consolidation de l’information pour passer de la donnée brute à de la donnée signifiante et qu’ils avaient construit des vues pour servir les besoins métiers, je me suis dit : ils ont tout compris ! 

Je le dis avec d’autant moins de scrupules que ces travaux ont été menés par OVH sans l’aide d’aucun cabinet de conseil ni intégrateur (donc pas avec Quantmetry notamment ;-). 

Aussi, de cette discussion est venue l’envie de témoigner de façon plus vaste sur l’organisation des datalake afin de faire en sorte que ceux-ci servent les intérêts des projets data, facilite l’industrialisation et le passage à l’échelle et contribue efficacement au remplacement progressif des systèmes décisionnels legacy contribuant ainsi à la maîtrise des coûts et la simplification du SI. 

  * Pour se comprendre, il faut d’abord préciser les termes du débat et les concepts employés. Fuyons les mots valise et convenons ensemble d’une définition partagée. Aussi, le premier article « [ Terminologie Data ](http://www.data-maniac.fr/language/fr/?p=3&preview=true) » porte sur la définition des concepts. 

  * Le 2ème article « Les utilisateurs et leurs besoins » précise les populations accédant aux informations du datalake et leurs attentes en termes de structuration de l’information. 

  * Le 3ème article « Datawarehouse vs big data” décrit comment passer d’une architecture décisionnelle à une architecture datalake en évitant quelques écueils. 

  * Le 4ème article « Pourquoi il faut modéliser la donnée » explicite la nécessité de modéliser, en complément de ce qui a déjà été décrit précédemment. 

  * Le 5ème article « Exposer les données du datalake » décrit les principaux composants utilisés pour rendre les données accessibles aux utilisateurs ou aux applications. 




En tant que conseil, nous avons souvent été confrontés à des datalake d’information brute peu ou mal exploitée et où la nécessité de modéliser la donnée était encore mal comprise. Il ne suffit pas de stocker pour interpréter. Si le datalake nous permet de stocker l’information brute sans la modéliser (schemaless) ce qui simplifie bien des choses, il faut la modéliser pour la comprendre et l’interpréter (schema on read). 

C’est fort de ce constat que nous avons décidé de rédiger à quatre main une série d’articles autour des datalakes et vous présenter les solutions que nous avons trouvées pour organiser l’information. 

———– 

[ Article datamaniac.fr ](http://www.data-maniac.fr/language/fr/2017/09/27/pourquoi-ecrire-ensemble/)
