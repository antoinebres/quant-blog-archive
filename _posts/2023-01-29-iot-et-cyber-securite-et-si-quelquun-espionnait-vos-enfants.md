---
layout: post
title: iot-et-cyber-securite-et-si-quelquun-espionnait-vos-enfants
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129152107/https://www.quantmetry.com/blog/iot-et-cyber-securite-et-si-quelquun-espionnait-vos-enfants/
---
Uncategorized 

22/03/2017 

#  IoT et cyber-sécurité : et si quelqu’un espionnait vos enfants ? 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fiot-et-cyber-securite-et-si-quelquun-espionnait-vos-enfants%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=IoT%20et%20cyber-s%C3%A9curit%C3%A9%20%3A%20et%20si%20quelqu%E2%80%99un%20espionnait%20vos%20enfants%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fiot-et-cyber-securite-et-si-quelquun-espionnait-vos-enfants%2F "Twitter")

* * *

Temps de lecture : 8 minutes 

![Quantmetry.com : IoT et cyber-sécurité : et si quelqu’un espionnait vos enfants ?](https://quantmetry.b-cdn.net/wp-content/uploads/2017/03/cybersecurite-1.jpg)

** Quel est le point commun entre les feux de circulation, les machineries d’industrie lourde et les jouets pour enfants ? La question est moins farfelue que ce qu’il pourrait sembler : tous les trois seront, d’ici quelques années, connectés à Internet à travers la logique de l’Internet of Things (« IoT »). En bonne mesure, ils le sont déjà aujourd’hui. Cette connexion généralisée pourra sans doute être exploitée afin de créer de nombreux services innovants à destination des utilisateurs. Mais d’un autre côté, si elle n’est pas gérée de manière plus attentive, elle peut être source d’importants problèmes de sécurité. Nous traiterons dans cet article de la sécurité de l’IoT, alors que ses opportunités seront présentées dans un prochain post.  **

L’IoT est un domaine en pleine croissance : un rapport publié par  [ IHS ](https://www.ihs.com/Info/0416/internet-of-things.html) estime qu’il y a actuellement 15 milliards d’appareils IoT dans le monde, et qu’il y en aura quatre fois plus d’ici 2025. Cependant l’IoT pose d’importants problèmes de cyber-sécurité : de nombreux appareils et bases de données sont mal sécurisés et peuvent faire l’objet d’attaques de hackers, qui violent la vie privée, dérobent des données sensibles, ou montent des armées de botnets. Si ces failles existent depuis longtemps, l’explosion de l’IoT les rend de plus en plus présentes. Pas un mois ne passe sans qu’une nouvelle fuite de taille ne soit révélée. Par exemple, l’entreprise Cloudpets – qui fabrique des jouets connectés pour enfants – a été touchée le 27 février 2017 par une large fuite de données : des millions de messages vocaux d’enfants étaient accessibles sans identification préalable. Ce manque de protection induit de nombreux risques : non-respect de la vie privée, fuite de données sensibles, espionnage industriel, sabotage, etc. 

Dans cet article nous présentons Shodan, un moteur de recherche sur l’IoT et le deep-web qui répertorie des millions d’appareils IoT laissés sans protection, et donc accessibles par n’importe qui. Nous verrons comment l’utiliser, et les dangers qu’il représente pour les personnes privées et les entreprises. 

##  Introduction à Shodan 

Shodan est moteur de recherche développé par John Matherly en 2009, et utilisé par des acteurs de la cyber-sécurité pour trouver des appareils mal-sécurisés. Il a été dénommé le « moteur le recherche le plus effrayant d’Internet » par  [ CNN ](http://money.cnn.com/2013/04/08/technology/security/shodan/) . Contrairement aux moteurs de recherche classiques, il indexe le deep-web et l’IoT, et ne référencie pas le contenue des pages mais les bannières des appareils. 

###  Qu’est-ce qu’une bannière ? 

Afin de comprendre le fonctionnement de Shodan, il est important d’expliciter ce qu’est une bannière. Il s’agit d’une information échangée entre un serveur et un client, qui contient des renseignements sur le service utilisé par le serveur. On peut parfois voir des bannières lors d’erreurs « 404 Page Not Found ». Les bannières sont toujours communiquées entre le client et le serveur, même quand elles n’apparaissent pas à l’utilisateur. Des outils de cyber-sécurité tels que nmap ou netcat permettent de les récupérer automatiquement. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/a.png)

Exemple bannière lors d’une erreur 404. On y apprend que le port 80 de l’IP 192.168 .10.67 utilise Apache 2.2.22 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/b.png)

Exemple de capture de bannière avec netcat. On y apprend que le port 80 de la cible utilise Apache 2.0.46 

Les bannières sont utiles pour les administrateurs pour contrôler les versions installées sur leur réseau de machines. Cependant, elles contiennent des informations qui peuvent aussi être utilisées par des hackers mal intentionnés. Par exemple si la bannière d’un serveur indique que celui-ci utilise Apache2.2.22, et qu’un hacker sait que cette version est vulnérable à une certaine attaque, alors il pourra attaquer le serveur en utilisant cette faille de sécurité. 

###  Utilisation de Shodan 

[ Shodan ](http://www.shodan.io/) permet de faire des recherches sur les bannières d’appareils connectés à Internet. Par exemple on pourra chercher « Apache2.2.22 » pour avoir une liste d’adresses IP comprenant ce mot clé dans leur bannière. La recherche pourra être affinée en combinant des mots clés, ou en se limitant à une zone géographique. On peut obtenir plus d’informations sur chaque adresse IP, comme sa position géographique exacte et les ports ouverts en cliquant sur « détails ». 

Des recherches classiques combinent un nom de logiciel avec un code http. Par exemple le code http « 200 OK » assure que l’adresse est accessible sans mot de passe (en premier lieux en tout cas), alors que le code « 401 Unauthorized » indique qu’une identification sera nécessaire avant d’accéder au service. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/c.png)

Exemple de recherche sur Shodan 

##  Objets connectés privés 

Les objets connectés entrent de plus en plus dans notre quotidien : Webcam, imprimante WiFi, routeur Internet, thermostat connecté, etc. Or trop souvent leur accès n’est pas sécurisé par une identification suffisante (il n’y a pas de mot passe, ou celui-ci est le mot de passe par défaut). Cela est dû au fait que les utilisateurs ne sont pas sensibilisés à l’importance d’établir un mot de passe fort, ou que les appareils n’ont pas été conçus pour gérer les identifications. En conséquence, il suffit à un hacker de se connecter à l’adresse d’un objet mal protégé pour en prendre le contrôle. 

Un des exemples les plus communs est celui des Webcams. La recherche « WebcamXP » – un logiciel utilisé par les webcams- sur Shodan laisse apparaître plusieurs milliers d’appareils. Une grande partie de ces appareils ne sont pas protégés, ou alors utilisent une identification par défaut (identifiant « WebcamXP », pas de mot passe). Il suffit alors de s’y connecter pour en prendre le contrôle et pour observer leurs images, comme dans les exemples ci-dessous : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-11.52-AM.jpg)

Exemple d’image de webcams trouvées sur Shodan   
Sources : Null-byte, Handelsblatt, Morning Post, Viss 

Le danger des objets IoT mal sécurisés ne réside pas uniquement dans la violation de la vie privée ; ils peuvent être infectés pour créer une armée de botnets. Ces appareils sont contrôlés à distance de manière simultanée pour réaliser des attaques informatiques d’envergure. Ainsi, en Octobre dernier, la plus grosse attaque par déni de service (« DDoS ») de l’histoire a touché un des nœuds d’Internet : Twitter, Netflix, Reddit, CNN et beaucoup d’autres sites ont été inaccessibles pendant plusieurs heures. Cela était dû à une armée d’appareils IoT mal sécurisés qui avaient été infectés par le virus Mirai. Ils ont été contrôlés simultanément pour submerger des serveurs de près de 1.2 téraoctets par seconde. Cela a mis hors de fonctionnement une partie de l’Internet américain. 

##  Capteurs industriels 

Le manque de sécurité des connexions à l’IoT ne concerne pas uniquement les appareils privés . Des milliers d’appareils industriels sont aussi accessibles sans identification.  [ On trouve par exemple ](http://money.cnn.com/gallery/technology/security/2013/05/01/shodan-most-dangerous-internet-searches/index.html) des éoliennes, des  centrales hydroélectriques, des caméras de surveillance, des feux de circulation, des pompes à chaleur, etc.  [ Un rapport ](http://money.cnn.com/2013/01/09/technology/security/infrastructure-cyberattacks/index.html) , réalisé pour le ministère de l’intérieur américain, a trouvé sur le territoire américain plus de 7 000 sites industriels contenant des contrôleurs accessibles sans identification. Quelques exemples sont présentés ci-dessous. Il est facile d’imaginer les dégâts qu’une personne mal intentionnée pourrait entrainer si elle en prenait le contrôle. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-11.52-AM-001.jpg)

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/Screen-Shot-12-30-18-at-11.52-AM-002.jpg)

Source : Dan Tentler 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/m.png)

Carte de 7 200 systèmes industriels vulnérables aux US   
Source : US Department of Homeland Security 

##  Bases de données 

En plus des appareils connectés, Shodan répertorie de nombreuses bases de données non-sécurisées. Celles-ci contiennent parfois des informations confidentielles appartenant à des entreprises, y compris les plus sécurisées. Les fuites peuvent être dues à des erreurs internes ou externes, par exemple un sous-traitant qui ne sé 
