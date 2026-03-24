---
layout: post
title: service-mesh-architecture-microservices
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129145654/https://www.quantmetry.com/blog/service-mesh-architecture-microservices/
---
IA Strategy 

09/10/2020 

#  Le rôle du service Mesh dans une architecture microservices 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fservice-mesh-architecture-microservices%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Le%20r%C3%B4le%20du%20service%20Mesh%20dans%20une%20architecture%20microservices&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fservice-mesh-architecture-microservices%2F "Twitter")

* * *

Auteur : [ Thomas Meimoun ](https://www.linkedin.com/in/thomas-meimoun-015677106/)

Temps de lecture : 6 minutes 

![Quantmetry.com : Le rôle du service Mesh dans une architecture microservices](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/tme.png)

####  Introduction 

Google, Amazon, Twitter, IBM, Netflix ou encore Airbnb, tous ont fait le choix d’utiliser les microservices. Couplés au service Mesh, ils permettent aux différents projets de gagner en agilité et en innovation. Cet article présentera les microservices et le service Mesh dans sa généralité ainsi que le service Istio. 

####  Qu’est-ce qu’un microservice ? 

#####  Présentation générale 

L’objectif des **microservices** est de remplacer les architectures dites **monolithes** . Ces dernières tentent de répondre à l’ensemble des demandes ainsi que les différents cas d’usage auxquelles l’applications pourrait face avec le temps. Le problème, c’est qu’au fur et à mesure que le projet grossit, des fonctionnalités deviennent obsolètes ou inutiles mais restent conservées. Finalement, on obtient une architecture interdépendante que cela soit en termes de **code** et de **complexité** rendant difficile la compréhension du schéma global. Le projet devient délicat ce qui implique une baisse de prise de risque et de nouveauté car la **stabilité est préférée à l’innovation** . 

Les microservices, quant à eux, cherchent à **décomposer** les différents **modules fonctionnels** répondant à un besoin unique fournissant une fonctionnalité pour un métier comme : 

  * Le login client 
  * Le panier d’achat 
  * Le chat en ligne 
  * Le paiement 
  * User Interface (UI) 



![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/09/appli.png)

Plusieurs microservices créent une application 

L’ensemble des microservices créé une **application** et l’utilisateur peut accéder à ces différents microservices via des API.  Ainsi, le but des microservices est d’offrir plus **d’évolutivité** et **d’agilité** pour les projets IT avec une équipe propre à chaque microservice. Notons aussi qu’il est possible d’utiliser un microservice seul s’il suffit aux besoins. 

#####  Les différents outils des microservices 

Après cette présentation nous pouvons distinguer trois avantages concernant les microservices : 

  1. Chaque microservice peut être **déployé** , **optimisé** et mis à **l’échelle** de façon indépendante 
  2. Gestion facilité pour les pannes et les erreurs 
  3. Chaque microservice peut être développé et déployé de façon autonome à travers différents stacks technologiques 



Avec l’essor du _cloud computing_ , les microservices sont très utiles et nécessitent trois composants fondamentaux 

  * **Conteneurisation** , comme **Docker** : Affectation d’un conteneur par unité de microservice. Cela permet d’adapter le nombre de ce microservice selon les besoins permettant ainsi une **gestion** et un **déploiement efficace** des microservices 
  * **Orchestration** , comme **Kubernetes** : Permet la gestion, la configuration et l’assignement des ressources systèmes disponibles 
  * **Service Mesh** , comme **Istio** : Service de maillage à l’aide de proxy permettant la sécurisation, la gestion et la connexion entre les microservices. Nous reviendrons plus tard sur le service Mesh 



Bien que la conteneurisation accorde un environnement propre à chaque microservice, il est important de faire attention aux différents _stacks_ technologiques utilisées pour la santé globale de l’application, comme les langages utilisés et les bases de données. 

Après avoir mis en avant les microservices et les outils nécessaires au bon déploiement de la technologie, intéressons nous plus en détail au **service Mesh** ou service de maillage permettant d’interagir entre les différents microservices. 

####  La communication entre microservices, le service Mesh 

#####  Présentation 

Afin d’expliquer le plus simplement possible le service Mesh, prenons l’exemple d’un panier sur un site en ligne. Lorsqu’un utilisateur souhaite faire des achats, il passe nécessairement par quelques microservices, comme l’authentification, l’appel à la base de données de l’inventaire des stocks, le portail de paiement mais aussi la suggestion d’articles basée sur ses goûts personnels. C’est à ce moment là que le maillage de services (service Mesh) apparaît en créant un **canal de communication** entre les microservices 

De ce fait, l’objectif d’un service Mesh est de rendre la communication entre les différents microservices accessible tout en considérant la tolérance aux pannes, la sécurisation, la robustesse et surtout l’accessibilité. Ceci est possible grâce à l’implémentation de _**service proxies** _ créant le canal de communication. on nomme ces proxy **Sidecar Pattern** . L’image suivante tente de schématiser la situation : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/09/proxy.png)

On constate que chaque microservice est associé à un unique proxy Sidecar 

Le service Mesh permet de : 

  * Configurer, maintenir et sécuriser les communications entre tous ou une partie des microservices d’une application 
  * Configurer et exécuter les fonctions réseau d’un microservice : robustesse, équilibrage, panne 
  * Les fonctions réseaux sont dissociées de l’utilisation dite de “logique commerciale”, permettant ainsi aux développeurs d’avancer sur la “logique métier” de l’application tout en conservant les communications entre les canaux. De plus la communication proxy passe au dessus des protocoles standards (HTTP1.x/2.x, gRPC) offrant la possibilité aux développeurs d’utiliser la technologie qu’ils souhaitent 



#####  Les composants d’un service Mesh 

Le service Mesh s’articule ainsi autour de deux axes principaux : 

  1. **Control Plane** : Tous les proxies sont contrôlés et centralisés par ce service en spécifiant les politiques d’identifications, la génération de métriques et la configuration des _services proxies_ à travers le maillage 
  2. **Data Plane** : Assure quant à lui le maillage entre les services. Cela est rendu possible par le Sidecar qui communique avec les microservices du Control Plane, c’est les **Fonctions de réseau primitive** . De l’autre côté, il y a les **Fonctions du réseau d’application** qui grâce au service proxy maintient et gère les fonctions critiques du réseau comme la robustesse, l’équilibrage ou encore les pannes 



Ainsi, après avoir présenté globalement le service Mesh nous pouvons nous concentrer sur un des services Mesh les plus utilisés, _**Istio** _

####  Le rôle d’Istio 

**Istio** est un service Mesh **open source** permettant aux développeurs de connecter, gérer et sécuriser les communications entre les microservices. C’est une solution native de **Kubernetes** . Il existe d’autres solutions comme **Consul** ou **Linkerd** , _AWS_ propose **App Mesh** et _Microsoft_ la solution **Service Mesh Interface** . 

Bien que le service Istio soit déployable sur Kubernetes, ce dernier fonctionne aussi On-premise. 

Istio déploie des proxies appelés **Sidecar Istio** associés à chaque microservices. De ce fait le trafic se fait entre les Sidecar des services offrant des politiques d’accès entre les microservices. 

Les principales fonctionnalités d’Istio sont : 

  * La sécurisation des communications entre microservices par des politiques d’identifications 
  * Des surcouches de contrôles d’accès, de quotas et d’allocation des ressources 
  * Équilibrage automatique de la charge des ressources 
  * Des métriques, logs et trafic (entrées et sorties) au sein d’un cluster 



Comme présenté dans la section précédente, le service Mesh se divise en deux parties le Data Plane et le Control Plane. Le premier utilise des proxies appelés **Envoy** basés sur des règles de routage spécifiques et déployés auprès de chaque microservice. Le Control Plane quant à lui possède un ensemble de composants techniques tels que **Pilot** pour gérer les règles de routage qui sont définies par les administrateurs, **Citadel** se concentre sur l’authentification et la gestion des identités. Pour finir **Galley** s’occupe de la validation, l’ingestion, le processus et la distribution entre services. Le schéma suivant permet d’un rapide coup d’oeil de comprendre le fonctionnement du maillage avec Istio. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/09/istio.png)

_Principaux composants[ d’Istio ](https://istio.io/) _

Pour finir, le service Mesh possède quelques limites. Un service mesh est très **invasif** , de plus, il sert d’intermédiaire, ce qui implique la possibilité de faire face à des **ralentissements** . Aussi ce service nécessite aux développeurs des **connaissances** à la fois du **maillage de microservices et Kubernetes** afin de fournir une architecture optimale  . Pour finir, il ajoute de la **complexité** à un projet déjà existant. 

####  Conclusion 

En conclusion, les microservices permettent un _time to market_ à la fois plus **rapide** et **efficace** . Cela est valable pour le lancement de nouveaux produits, les adaptations aux besoins du marché mais aussi à l’intégration d’innovation. En contrepartie, l’augmentation de la rapidité et de la quantité des itérations nécessite un effort de synchronisation des équipes. Cet aspect est important à mentionner car il entraîne davantage d’échanges et de coordination entre les différentes équipes, ce qui signifie un alignement des objectifs entre les équipes par l’entreprise. Pour autant, le service de Mesh est encore peu utilisé dans les entreprises. 

#####  ✍  [ Article écrit par Thomas Meimoun ](https://www.linkedin.com/in/thomas-meimoun-015677106/)
