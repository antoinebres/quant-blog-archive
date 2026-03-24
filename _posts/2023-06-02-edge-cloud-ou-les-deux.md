---
layout: post
title: edge-cloud-ou-les-deux
date: 2023-06-02
url_wayback_machine: https://web.archive.org/web/20230602191147/https://www.quantmetry.com/blog/edge-cloud-ou-les-deux/
---
IA device 

02/12/2020 

#  Edge, Cloud ou les deux ? 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fedge-cloud-ou-les-deux%2F&title=Edge%2C%20Cloud%20ou%20les%20deux%20%3F "Linkedin") [ ](http://twitter.com/intent/tweet?text=Edge%2C%20Cloud%20ou%20les%20deux%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fedge-cloud-ou-les-deux%2F "Twitter") [ ](https://www.quantmetry.com/blog/edge-cloud-ou-les-deux/ "Email") [ ](https://www.quantmetry.com/blog/edge-cloud-ou-les-deux/ "Copy Link")

* * *

Auteur : [ Alexandra Lorenzo de Brionne ](https://www.linkedin.com/in/alexandra-lorenzo-de-brionne/)

Temps de lecture : 5 minutes 

![Quantmetry.com : Edge, Cloud ou les deux ?](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/alvin-lenin-u4a1l-vwwha-unsplash-scaled.jpg)

_ Selon Gartner, d’ici 2022, plus de 50 % des données générées seront créées et traitées en dehors d’un datacenter ou du Cloud.  _

De retour du SIDO 2020, le plus grand showroom européen dédié à l’IoT, l’IA et la Robotique, je suis revenue avec plusieurs questions sur l’évolution de l’Intelligence Artificielle. 

En effet, l’interaction entre les objets connectés, l’IA et le Cloud a évolué rapidement. Ces capteurs omniprésents dans notre vie quotidienne générant des quantités massives de données, la **maîtrise de ce flux** est et sera un enjeu crucial. D’ailleurs, selon Gartner, d’ici 2022, plus de 50 % des données générées seront créées et traitées en dehors d’un datacenter ou du Cloud [1]. 

Dans cet article, je propose d’analyser comment fonctionnent le Cloud computing et l’Edge computing, pour ensuite aborder la complémentarité entre ces deux outils dans le domaine de l’Intelligence Artificielle (IA). 

##  **Cloud Computing, l’informatique dans les nuages**

Ce terme désigne l’ensemble des techniques de stockage et d’accès aux données à distance dont l’hébergement est souvent externalisé. **Les données ne sont donc plus stockées en mémoire** , mais disponibles sur des serveurs distants et accessibles via internet. 

Le Cloud Computing a plusieurs avantages. Il facilite notamment l’accès à la donnée, s’adapte aux besoins croissants des entreprises en matière de stockage et réseau, et permet de maîtriser son budget informatique. 

En effet, en général, les fournisseurs Cloud fonctionnent avec un système “Pay-As-You-Go”, ce qui donne plus de flexibilité, et permet de gérer plus efficacement le stockage de données et la gestion du réseau. 

##  **Edge Computing, l’informatique en périphérie**

L’Edge Computing se différencie du Cloud Computing, car au lieu de transférer les données générées par des appareils connectés IoT vers le Cloud, il s’agit de **traiter les données directement** sur les objets ou devices connectés ou à leur périphérie. 

Cela réduit la dépendance du réseau à une connexion Internet et permet de ne faire remonter que les alertes ou des données. L’objet réduit donc la latence du traitement de l’information en gérant lui-même ses données [2]. 

##  **Le Edge Computing va-t-il remplacer le Cloud?**

Lors de la conférence [ “Edge / Cloud, où se joue la bataille de l’IA ?” ](https://www.sido-event.com/event/) , une question cruciale a été posée : est-ce la fin du Cloud Computing ? 

L’Edge IA a permis la prolifération des applications IoT en traitant et analysant les données au plus près de la source. Le temps de **latence** a été largement réduit, avec un délai de réponse quasi instantané. Finalement, sans Edge computing, les voitures autonomes n’auraient pas pu exister. 

Un autre avantage majeur de l’Edge computing est la réduction de la **bande passante** . En effet, Intel estime que les voitures autonomes équipées de centaines de capteurs embarqués généreront 40 téraoctets de données en l’espace de 8 heures de conduite. Le traitement en local de ces données rend plus pratique et avantageux l’utilisation du Edge Computing, notamment pour la vidéo haute définition, dans le cas de véhicules autonomes ou de caméras de surveillance embarquées. 

Cependant, l’Edge Computing présente un risque de **perte de données** . En effet, si un sinistre se produit dans une usine avec des objets connectés, l’absence de sauvegarde de données peut être fatale et conduire à une perte totale de celles-ci. 

De plus, la réduction de la bande passante ajoute une complexité sur la **décentralisation** , car la gestion des processus industriels sera diffusée dans différents systèmes, voire différentes technologies. 

**Avantages** |  **Inconvénients**  
---|---  
**Latence** Réduction de la distance entre les objets et les centres de traitement  .  Facilite le traitement en temps réel des données.  |  **Intelligence décentralisée** L’Edge computing ajoute une couche de complexité au système d’information des entreprises.   
**Bande Passante** Réduction des besoins en bande passante entre les capteurs et le traitement de la donnée, en entreprenant les analyses au plus près de celles-ci.  |  **Non archivage des données** Historisation des données non incluse.   
  
##  **Edge Computing et Cloud Computing : le duo gagnant**

Les fournisseurs Cloud ont bien compris que le Cloud computing et l’Edge computing sont finalement **complémentaires** , plutôt que concurrentiels ou mutuellement exclusifs. 

Par exemple, Amazon a mis en place [ AWS IoT Greengrass ](https://aws.amazon.com/fr/greengrass/) pour étendre son service Cloud aux équipements Edge, afin qu’ils puissent agir localement sur les données qu’ils génèrent, tout en utilisant le Cloud pour la gestion, l’analyse et le stockage durable. 

De même, [ Azure ](https://azure.microsoft.com/fr-fr/services/iot-edge/) propose un service pour déployer des modèles créés et formés dans le Cloud à exécuter localement. 

Selon le fondateur de NetFoundry, l’Edge computing permet un premier traitement des données avant de les transférer vers le Cloud. Cela permet d’avoir l’avantage de l’Edge computing, le temps de latence extrêmement faible et la centralisation des données grâce au Cloud. 

Les organisations qui utilisent ces deux architectures bénéficieront des synergies de solutions qui maximisent les avantages des modèles centralisés et décentralisés. 

###  **Cas concret: la voiture autonome**

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/google-waymo.gif)

> _ Vidéo immersive de Google Waymo  _

Prenons le cas de la voiture autonome. 

Pour des raisons de sécurité, certaines actions nécessitent une prise de décision en temps réel où aucun temps de latence n’est acceptable. Exemple : la nécessité de freiner ou non. 

L’Edge computing est alors une solution qui assure le traitement local des données et détermine seul les actions qui en découlent. 

Par ailleurs, l’analyse complète des données d’une flotte de véhicules autonomes ne nécessitant aucune prise de décision immédiate (autonomie, itinéraires, maintenance préventive, etc.) peut être mise à la disposition du Cloud computing. Les données sont ainsi analysées dans leur globalité, offrant de nouveaux usages et améliorant l’expérience utilisateur. 

##  **L’avenir du Edge Computing**

De nombreuses entreprises se tournent maintenant vers l’Edge Computing. Cependant, comme nous l’avons vu ce n’est pas l’unique possibilité, le Cloud Computing reste une solution viable. C’est pourquoi, les fournisseurs Cloud ont commencé à combiner les stratégies avec la technologie de l’Edge Computing. L’Edge et le Cloud ne sont donc **pas des concurrents directs** mais bien complémentaires pour répondre à l’ensemble des besoins des entreprises. 

Et l’avenir ? 

L’Edge Computing risque encore d’évoluer avec **l’apparition de la 5G** et son débit Internet dix fois plus rapide que la norme actuelle. Cela permettra une réduction du temps de latence considérable, il sera alors possible d’analyser de gros volumes de données en une fraction de seconde. 

De même, la 5G laisse entrevoir de nombreux services innovants dans de nombreux domaines (voitures autonomes, usines du futur, médecine, etc.). 

###  **Pour en savoir plus sur l’Edge AI:**

  * Un cours délivré par Intel pour mettre en place des applications de Computer Vision et l’utilisation du Deep Learning en IoT:  [ Intel Edge AI for IoT Developers from Udacity  ](https://www.udacity.com/course/intel-edge-ai-for-iot-developers-nanodegree--nd131)
  * Et si vous apprenez à programmer un service IoT avec Arduino et Raspberry Pi ?  [ Coursera  ](https://www.coursera.org/specializations/iot) [ – An Introduction to Programming the Internet Of Things (IoT) Specialization  ](https://www.coursera.org/specializations/iot)



###  **Ressources:**

[1]  [ The Edge Completes the Cloud: A Gartner Trend Insight Report  ](https://www.gartner.com/en/doc/3889058-the-edge-completes-the-cloud-a-gartner-trend-insight-report) . 2018. Bob Gill, David Smith 

[2] [ IA at the Edge, Quantmetry, Louise Rodriguez ](https://www.quantmetry.com/blog/ia-at-the-edge/) . 

[3]  [ Convergence of Edge Computing and Deep Learning: A Comprehensive  ](https://arxiv.org/pdf/1907.08349.pdf) . 2020. Xiaofei Wang, Yiwen Han, Victor C.M. Leung, Dusit Niyato, Xueqiang Yan, Xu Chen.    
[4]  [ A Beginner’s Guide to Edge Computing  ](https://medium.com/velotio-perspectives/a-beginners-guide-to-edge-computing-6cfea853aa11#:~:text=Edge%20Computing%20examples%20can%20be,Mobile%20devices) . Medium. 2019. Velotio Technologies   
[5] [ AI Paris 2019 – Résumé des conférences auxquelles nous avons assisté ](https://www.quantmetry.com/blog/ai-paris-2019-resume-conferences-quantmetry/) , Quantmetry. 
