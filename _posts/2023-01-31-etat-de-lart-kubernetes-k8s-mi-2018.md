---
layout: post
title: etat-de-lart-kubernetes-k8s-mi-2018
date: 2023-01-31
url_wayback_machine: https://web.archive.org/web/20230131104822/https://www.quantmetry.com/blog/etat-de-lart-kubernetes-k8s-mi-2018/
---
Uncategorized 

27/09/2018 

#  Etat de l’art Kubernetes (K8s) mi-2018 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fetat-de-lart-kubernetes-k8s-mi-2018%2F&title=Etat%20de%20l%E2%80%99art%20Kubernetes%20%28K8s%29%20mi-2018 "Linkedin") [ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fetat-de-lart-kubernetes-k8s-mi-2018%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Etat%20de%20l%E2%80%99art%20Kubernetes%20%28K8s%29%20mi-2018&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fetat-de-lart-kubernetes-k8s-mi-2018%2F "Twitter")

* * *

Temps de lecture : 23 minutes 

![Quantmetry.com : Etat de l’art Kubernetes \(K8s\) mi-2018](https://www.quantmetry.com/wp-content/uploads/2018/09/kub1.png)

Cet article s’adresse à un public novice sur les technologies de conteneurisation (i.e. Docker et Kubernetes). Il s’agit d’une mise à jour de l’état de l’art de l’écosystème Kubernetes à mi-2018. La technologie K8s n’est pas récente, en revanche de nouveaux usages émergent du fait de son enrichissement par des solutions complémentaires. 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/kub1.png)

####  Introduction 

L’écosystème Kubernetes est fortement influencé par la mouvance de développement d’application DevOps. Notamment, lorsque la partie Dev est prépondérante au regard des aspects Ops. 

D’après Wikipédia, l’objectif d’un conteneur est le même que pour un serveur dédié virtuel : héberger des services sur un même serveur physique tout en les isolant les uns des autres. Un conteneur est cependant moins figé qu’une machine virtuelle en termes de taille de disque et de ressources allouées. 

La configuration, le déploiement et la gestion de plusieurs conteneurs pour de multiples microservices peuvent s’avérer fastidieux et se complexifier au fur et à mesure de la croissance du Système d’Information (SI). 

C’est là qu’intervient Kubernetes. K8s est un orchestrateur de conteneurs. La principale mission de ce dernier est d’automatiser le cycle de vie des conteneurs : le déploiement, les mises à jour, le contrôle d’état et les procédures de basculement. 

Ci-dessous, les différentes étapes du développement d’application dans un contexte conteneurisé 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/kub2.png)

Kubernetes tire ses origines dans le projet de recherche Google **Borg** initié dans les années 2003/2004. K8s est un projet au code source ouvert (open source) offert à la Cloud Native Computing Foundation (CNCF) en 2015. Le 6 mars 2018, Kubernetes est le premier projet de la CNCF à être gradué ( **graduated project** ) : ce statut reflète le niveau de maturité avancé de l’écosystème. Selon la CNCF, il s’agit désormais de la plate-forme d’orchestration de conteneurs la plus populaire au monde. 

####  Intérêts 

Les intérêts de cette solution sont nombreux. Elle permet de : 

  * Se focaliser sur la façon dont les **applications doivent fonctionner** , plutôt que sur des détails spécifiques d’implémentation. 
  * **Éviter l’enfermement propriétaire** : les applications sont **agnostiques à l’infrastructure physique** . Seule la configuration de la grappe (cluster) Kubernetes est spécifique à chaque hôte. 
  * Faciliter la transition et **migrer en douceur vers une nouvelle architecture** sans bouleverser les applications existantes. Par exemple, passer d’une architecture monolithique vers une architecture microservices. Ou, dans un SI plus urbanisé, évoluer d’une architecture microservices vers une architecture émergente sans serveur (serverless), également appelé Fonction en tant que Service (Function as a Service ou FaaS) 
  * **Cloisonner les logiciels** , chaque application est packagée avec toutes ses dépendances. Elles possèdent un **cycle de vie indépendant les unes des autres** . 



####  Sous le capeau 

#####  Historique 

Kubernetes est une technologie mature, forte de quinze années d’évolution. Elle a été inspirée par divers projets de recherches et solutions internes de Google : principalement Borg et Omega. Le premier est notamment à l’origine de bon nombre de technologies autour des conteneurs tel LXC, Docker, etc. 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/kub3.png)

En 2014, Google exécute deux milliards de conteneurs par semaine avec ces systèmes. Lors de la DockerCon 2017, Docker annonce qu’il supporte désormais nativement Kubernetes. L’orchestrateur historique, Docker Swarm, n’est plus l’unique solution supportée. 

#####  Quelques notions de conteneurs 

K8s est étroitement lié à la technologie de conteneurisation sous-jacente. Docker étant le gestionnaire de conteneur le plus couramment utilisé, les exemples suivants seront basés sur cette technologie. 

Avant d’aller plus loin, il est important d’avoir en tête trois notions de base propre à cet univers : 

  * Les **images** de conteneurs : c’est un logiciel léger, autonome et exécutable comprenant tout ce qui est nécessaire pour exécuter une application: code, runtime, outils système, bibliothèques système et paramètres. 
  * Les **conteneurs** eux même : les images de conteneur deviennent des conteneurs au moment de l’exécution. Disponible pour les applications Linux et Windows, le logiciel conteneurisé fonctionnera toujours de la même manière, quelle que soit l’infrastructure. Les conteneurs isolent les logiciels de leur environnement et garantissent un fonctionnement uniforme malgré les différences, par exemple, entre le développement, la recette et la production. 
  * Le **dépôt** d’image de conteneurs (repository) : Service généralement haute disponibilité, car point unique de défaillance d’un SI architecturé autour des conteneurs. Il existe des services publics et privés, hébergés dans les nuages ou sur site : Docker Registry (projet à source ouverte), Docker Trusted Registry (partie de la version entreprise), Google Container Registry, etc. 



Ci-dessous, le schéma mettant en avant les différentes couches physique d’un serveur d’applications conteneurisées : 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/kub4.png)

Le schéma d’architecture ci-dessous illustre les interactions entre les différents composants : 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/kub5.png)

Lors de la création des images, il est important d’optimiser leur taille et de minimiser le nombre de couches (layer), comme visualisé sur le schéma ci-dessous : 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/kub6.png)

Le délai de disponibilité d’un nouveau conteneur est corrélé à sa taille et à la complexité des traitements réalisés lors de la phase de démarrage de celui-ci (i.e. l’exécution du code définit via les instructions CMD et ENTRYPOINT du Dockerfile). La construction de conteneurs optimisés repose sur deux principaux concepts : 

  * L’utilisation d’une **image racine minimaliste comme alpine Linux** en lieux et place d’une distribution standard (i.e. Ubuntu ou CentOS). Ce type d’image fait quelques dizaines de méga-octets contre plusieurs centaines pour une Ubuntu ou Debian. 
  * L’usage de la fonctionnalité **multi-stage** lors de la phase de construction des images des conteneurs Dockerfile. 



Outre les performances accrues, l’utilisation d’images minimalistes contribue fortement à renforcer la sécurité du SI. Le nombre restreint de services et/ou applications disponible réduit le périmètre des failles de sécurité. 

Un point d’attention mérite d’être apporté concernant la manière dont les données sont persistées au sein d’un conteneur. **Toutes les données stockées directement au sein du conteneur lui-même sont perdues lorsque le conteneur est supprimé** . Pour persister les données en dehors de la durée de vie des conteneurs, il faut stocker les données sur un système externe (i.e. HDFS, S3, GCS, Base de données, etc.). 

#####  Quelques notions d’orchestration de container 

Avant d’aller plus loin, il est important de rappeler la définition d’un orchestrateur. Ci-dessous, la vision de Hewlett Packard Enterprise : 

les applications sont généralement constituées de composants mis en conteneur individuellement (souvent appelés microservices) qui doivent être organisés au niveau du réseau afin que l’application puisse fonctionner correctement. Ce mode d’organisation des conteneurs est appelé **orchestration de conteneur** . 

Dans le développement moderne, les applications ne sont plus monolithiques, au contraire, elles sont composées de douzaines voire de centaines de composants mis en conteneurs, peu structurés, qui doivent fonctionner ensemble pour permettre à telle ou telle application de fonctionner correctement. **L’orchestration de conteneur désigne le processus d’organisation du travail des composants individuels et des niveaux d’application** . 

#####  Les concepts clés de K8s 

L’architecture Kubernetes repose sur trois notions fondamentales expliqué ci-après : 

  * **Pods**
  * **Services**
  * **Equilibrage de charge** (Load Balancer) 



Le schéma ci-dessous illustre les interactions entre ces notions : 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/kub7.png)

Tout d’abord, expliquons le concept de **pod** . Wikipédia le définit comme l’unité de base de l’ordonnancement. Un pod consiste en un ou plusieurs conteneurs qui ont la garantie d’être co-localisés sur une machine hôte et peuvent en partager les ressources. Un pod est une vue abstraite de composants conteneurisés. 

L’autre concept clef de l’architecture K8s, c’est la notion de **services** applicatifs. D’après Wikipédia, il s’agit d’un groupe de pods travaillant ensemble. Par exemple, une couche dans une application multicouche. L’ensemble des pods qui constituent un service est défini par un label selector (i.e. sur le schéma précédent, Role = frontend et Env = prod). 

Par défaut, les services ne sont pas exposés à l’extérieur de la grappe K8s. Une façon simple d’exposer un service, consiste en l’utilisation d’un service de type **équilibrage de charge** . 

Ci-dessous, un exemple d’implémentation (le bloc ingress représente l’équilibreur de charge) : 

![](https://www.quantmetry.com/wp-content/uploads/2018/12/kub8.png)

#####  Interactions entre Docker et K8s 

Kubernetes est un orchestrateur de conteneurs, il peut être vu comme un système d’exploitation dédié aux centres de données. 

Bien qu’il existe d’autres orchestrateurs, Kubernetes est à ce jour l’unique solution recommandée par la CNCF pour couvrir les besoins en orchestration de conteneur. 

K8s répond à l’ensemble des problématiques ci-dessous : 

  * Comment démarrer les conteneurs ? 
  * Comment exposer vos services containerisés ? 
  * Comment gérer les conteneurs arrêtés suite à une erreur ? 
  * Comment gérer les pannes des hôtes/nœuds ? 
  * Comment gérer la maintenance de vos hôtes/nœuds ? 
  * Comment gérer les mises à l’échelle 
    * Au niveau applicatif : plutôt scalabilité horizontal ou vertical ? 
    * Au niveau de l’infrastructure du SI : couverture géographique, haute disponibilité ? 
  * Comment gérer la multiplication du nombre de composants à déployer ? 
  * Comment gérer les mises à jour de vos composants ? 



L’un des principaux rôles de k8s consiste à planifier l’ajout/suppression des pods sur les différents noeuds qui composent la grappe kubernetes. 

#####  Aperçu de l’architecture technologique 

À l’instar de bon nombre de technologies de l’univers des données massives (en anglais Big Data), K8s repose sur le concept d’infrastructure distribuée basée sur deux entités : 

  * Un serveur **maître** (master). Généralement redondé deux fois pour garantir un service haute disponibilité. 
  * “n” serveur(s) **nœud(s)** (node(s)). Il est possible de spécialiser tout ou partie d’entre eux : calcul intensif, cartes vidéos, disque dur à mémoire, etc. 



D’un point de vue macroscopique, les deux composants clés de la technologie K8s sont : 

  * **Etcd** : D’après Wikipédia, “Unité de stockage distribuée persistante et légère de données clé-valeur développée par CoreOS, qui permet de stocker de manière fiable les données de configuration du cluster, représentant l’état du cluster à n’importe quel instant.”. **Attention** , celui du serveur maître est le principal point de défaillance (Single Point Of Failure ou SPOF) de l’ensemble de la grappe Kubernetes. 
  * **Kubelet** : Toujours d’après Wikipédia, “Responsable de l’état d’exécution de chaque nœud (c’est-à-dire, d’assurer que tous les conteneurs sur un nœud sont en bonne santé). Il prend en charge le démarrage, l’arrêt et la maintenance des conteneurs d’applications (organisés en pods) dirigés par le plan de contrôle.” 



![](https://www.quantmetry.com/wp-content/uploads/2018/12/kub9.png)

#####  Fonctionnalités K8s avancées 

Après avoir défini ce qu’était un orchestrateur de conteneur et donné un aperçu de l’architecture technologique, explorons un panel de fonctionnalités avancées en mesure de répondre aux problématiques d’orchestration induites par l’architecture distribuée de k8s. Un sujet majeur consiste à optimiser la planification des pods sur les noeuds. Dans la pratique, il est intéressant de spécialiser un certain nombre de noeuds. Par exemple, s’assurer que 
