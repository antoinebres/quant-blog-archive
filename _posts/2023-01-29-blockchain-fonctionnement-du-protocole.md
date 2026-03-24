---
layout: post
title: blockchain-fonctionnement-du-protocole
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129152359/https://www.quantmetry.com/blog/blockchain-fonctionnement-du-protocole/
---
Uncategorized 

12/04/2017 

#  Blockchain : fonctionnement du protocole 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fblockchain-fonctionnement-du-protocole%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Blockchain%20%3A%20fonctionnement%20du%20protocole&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fblockchain-fonctionnement-du-protocole%2F "Twitter")

* * *

Temps de lecture : 10 minutes 

![Quantmetry.com : Blockchain : fonctionnement du protocole](https://quantmetry.b-cdn.net/wp-content/uploads/2017/04/i5.jpg)

Ceci est le premier d’une série d’articles sur la technologie blockchain. L’objectif ici est de comprendre dans quelle mesure la technologie blockchain constitue une solution naturelle au problème de transfert d’actifs entre deux agents sans tiers de confiance. 

Le Bitcoin, projet d’échange décentralisé et sécurisé d’argent virtuel, est né suite à la crise de confiance de 2008 envers les institutions financières. Son objectif affiché était de se passer des intermédiaires de confiance dont le rôle est de certifier et d’enregistrer l’historique des transactions monétaires, à savoir les banques. 

Ce système décentralisé, constitué de milliers d’ordinateurs à travers le monde, représente en quelque sorte un registre public, anonyme et distribué : 

● Public car tout le monde peut accéder au contenu du registre sans demande de permission 

● Anonyme car chaque utilisateur n’est associé à rien d’autre qu’un ensemble d’adresses alphanumériques contenant des Bitcoins 

● Distribué car il n’existe pas d’autorité centrale de certification des transactions. 

##  Le protocole blockchain 

Pour comprendre techniquement comment ces trois propriétés s’articulent pour certifier les échanges, considérons deux personnes. Alice et Bob veulent effectuer une double transaction : un transfert d’un actif monétaire (paiement) qui déclenche ensuite un transfert d’un autre type d’actif (envoi par courrier d’un bien, réalisation d’un service, etc.). Nous allons progressivement construire une monnaie digitale dénommée « Infocoin » permettant un échange sécurisé entre les deux agents. Les solutions aux différents obstacles rencontrés nous permettront de montrer en quoi le protocole blockchain constitue une solution « naturelle » au problème de transfert sécurisé de valeur. 

###  Étape 1 : La notion de signature numérique 

Alice, qui cherche à transférer un Infocoin à Bob, peut envoyer un fichier texte où elle inscrit « Alice transfère un Infocoin à Bob ». La fragilité d’un tel système est évidente : un tiers autre qu’Alice peut très bien générer un tel fichier, ou bien falsifier le message. 

La solution à ce problème passe par l’utilisation d’une signature numérique : Alice hash le texte de départ, le crypte avec la partie privée d’une clef RSA dont elle transfère la partie publique à Bob, ainsi que le message original. Bob, en utilisant la clef publique, décryptera le message, qu’il comparera au message original reçu. Si les deux messages coïncident, alors Bob peut être certain que c’est bien Alice qui a envoyé le message (par principe, seule Alice possède la partie privée de la clef) et que ce dernier n’a pas été falsifié en cours de route (voir Fig. 1). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/I1.png)

Figure 1 : La notion de signature numérique 

###  Étape 2 : La sérialisation et le registre public 

Maintenant que l’identité d’Alice est certifiée, comment éviter qu’elle ne génère abusivement 10 fois le même message, dépensant ainsi des Infocoins qu’elle ne 

possède pas ? 

● Première solution : on associe un numéro de série à chaque Infocoin pour le rendre unique, un peu comme un billet de banque. Néanmoins, dans le cas de la banque, il existe une autorité centrale qui certifie les numéros de série et garantit leur unicité, exactement ce que l’on cherche à éviter ! 

● Deuxième solution : tenir un registre public distribué de la propriété des Infocoins sérialisés. Ainsi, Bob peut vérifier sur sa copie locale du registre que l’Infocoin n°56 appartient bien à Alice. Il diffuse ensuite un message d’acceptation de l’envoi par Alice de cet Infocoin, amenant tous les autres participants à mettre à jour leur copie locale du registre. Le nouvel état du registre, partagé par tous, indiquera donc bien que l’unique Infocoin n°56 du réseau a été transféré d’Alice à Bob. 

Malheureusement, la vérification de l’unicité de l’Infocoin dépensé par Bob via le registre public s’avère insuffisante si un utilisateur malintentionné exploite la latence du réseau de communication entre les différents participants au système de monnaie digitale pour effectuer des doubles dépenses. En effet, Alice peut diffuser son message deux fois avec deux destinataires différents pour l’Infocoin, Bob et Charlie. Bob, ayant reçu l’Infocoin n°56 d’Alice, vérifiera sur son registre local qu’elle en est bien la propriétaire et diffusera un message de validation de la transaction au reste du réseau. Charlie en fera de même, son message de validation de la transaction étant accepté s’il arrive en premier, et refusé s’il arrive après celui de Bob. Du coup deux versions incompatibles du registre public seront présentes au sein du réseau : une partie des nœuds, qui a reçu la validation de Bob en premier considérera que c’est lui le propriétaire de l’Infocoin n° 56, l’autre partie considérera que c’est Charlie. Le système créé n’est donc pas encore un système viable. 

La résolution du problème de la double dépense constitue la challenge le plus important dans la construction d’une monnaie digitale, et nécessite trois étapes supplémentaires qui nous mèneront vers l’architecture technique d’une blockchain. 

###  Étape 3 : La vérification collective 

Un premier pas dans la résolution du problème de la double dépense passe par le fait que Bob attende une vérification collective de la propriété de l’Infocoin avant d’envoyer son message de validation de la transaction, qui entraîne une mise à jour des registres. Ainsi, l’envoi de deux messages contradictoires de la part d’Alice entraînera des retours contradictoires à Bob de la part du réseau, d’où une annulation de la transaction. 

La question qui se pose avec ce système de validation par 100% des nœuds du réseau est celle de la présence d’agents non-coopératifs, qui peuvent volontairement fausser la validation des transactions de leurs concurrents. Si l’on accorde le privilège de la validation à quelques nœuds uniquement, on abandonne l’objectif d’un système complètement décentralisé, tandis qu’un système basé sur le vote peut facilement être piraté en générant des fausses identités pour les nœuds du réseau. 

###  Étape 4 : La preuve de travail 

Imaginons que l’on force les nœuds du réseau à « travailler » et à donner une preuve de leur travail avant de considérer leur retour comme valable. Ce travail peut prendre la forme de la résolution d’un problème mathématique : les nœuds devront fournir la solution à un problème dont la vérification de la validité est simple, comme la résolution d’une équation h(T + N) = 0000…123, avec h une fonction de  [ hachage ](https://fr.wikipedia.org/wiki/Fonction_de_hachage) ,  T le message de la transaction, N un message aléatoire dénommé « nonce » en anglais, et m 0 au début du membre de droite de l’équation qui est encodé dans un format 16 bits. La recherche d’une solution par force brute nécessiterait de tester 16^m combinaisons pour trouver le N qui convient, tandis que la vérification de la solution N trouvée est très rapide. 

Dès qu’un nœud a trouvé une solution N valide, il la diffuse au reste du réseau qui vérifie quasi-instantanément si elle convient ou non en calculant la valeur h(T + N), avec mise à jour de la copie locale du registre si la solution est acceptée. Sachant qu’un calcul coûte de l’argent (possession d’un ordinateur, consommation d’électricité, etc.), on peut inciter les agents à effectuer les calculs en les rémunérant pour chaque transaction validée. Avec quel argent ? C’est là toute la beauté du système Bitcoin ou de ses avatars : on génère un Bitcoin ex nihilo pour justement récompenser le travail de validation d’une transaction. 

Ainsi, hormis la masse d’argent initiale créée en même temps que le protocole, la seule façon d’augmenter la masse monétaire en Bitcoins ou en Infocoins est d’effectuer des calculs de validation des transactions. Les travailleurs du réseau sont dénommés les « mineurs », tandis que leur travail est connu sous le nom de « minage ». 

###  Étape 5 : Ordre temporel des blocs 

Pour des raisons d’optimisation, on regroupe les transactions dans des blocs à valider, constitués chacun de : 

● Un hash de la liste de transactions via une fonction qui fait partie du protocole 

● Un timestamp de création du bloc 

● Le nonce trouvé par le mineur ayant validé le bloc de transactions 

● Le hash du bloc précédent, ce qui constitue une convention de pointage instaurant un ordre temporel entre les blocs 

Des techniques d’optimisation du hashage des transactions à regrouper dans le bloc existent, mais nous n’allons pas entrer dans ces détails dans cet article (voir Fig. 2). Le système composé de blocs et de pointages constitue une chaîne ordonnée de transactions, d’où la dénomination « blockchain ». 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/I2.png)

Figure 2 : Ordre temporel des blocs par pointage 

###  Étape 6 : Gestion des bifurcations 

Plusieurs blocs étant minés en même temps, une règle d’or est instaurée pour réguler le travail des mineurs : « la branche valide est la branche la plus longue ». Ainsi, des mineurs travaillant sur deux blocs en concurrence doivent cesser leur travail sur le bloc perdant aussitôt qu’un bloc a été validé. Après vérification de la validité du contenu du bloc, ils mettent à jour leur copie locale du registre, avec un pointage qui tient compte de l’arrivée du nouveau bloc. 

Que se passe-t-il lorsque deux mineurs finissent en même temps de miner un bloc de transactions ? Il se crée alors ce que l’on nomme une bifurcation : les mineurs continuent à miner le long des deux branches, avec potentiellement des nouvelles sous-branches qui apparaissent dès lors que des nouveaux blocs sont terminés simultanément. Cependant, dès qu’un bloc est terminé avant les autres le long d’une branche qui devient la plus longue, tous les mineurs vérifient le contenu du bloc puis doivent mettre à jour leur registre local et basculer sur cette nouvelle branche légitime (voir Fig. 3). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/I3.png)

Figure 3 : La gestion des bifurcations dans une blockchain 

##  Vérification de la robustesse du protocole 

Analysons maintenant la robustesse de ce protocole. 

Imaginons un premier type d’attaque où Alice insère dans un même bloc deux transactions incompatibles, l’une envoyant un Infocoin à Bob, l’autre envoyant le même Infocoin à Charlie. Alice peut alors miner le bloc, avec une vitesse proportionnelle aux capacités de calcul qu’elle possède. Elle peut diffuser ensuite le message de validation au reste du réseau. Néanmoins, ce type d’attaque basique est voué à l’échec car la lecture du bloc par les autres acteurs du réseau montrera clairement qu’il contient deux transactions incompatibles, entraînant ainsi son invalidation. 

Deuxième type d’attaque, Alice diffuse deux messages distincts portant sur des transactions incompatibles entre elles à destination de Bob et Charlie. Une bifurcation de minage se crée dans le réseau, mais à terme seule l’une des deux branches sera validée car considérée la plus longue, généralement celle ayant bénéficié des ressources de calcul les plus importantes. Ainsi, Bob ou Charlie saura que sa transaction n’a pas été validée, et l’échange n’aura pas lieu. Attention à un envoi prématuré de la contrepartie : la validation des blocs et les bifurcations étant une information locale, il ne faut pas considérer une transaction fraîchement validée comme fiable, au risque d’être trompé si la branche ayant validé la transaction s’avère non-légitime par la suite car plus courte qu’une autre. D’où une recommandation d’attendre 6 blocs validés suite à celui contenant la transaction lancée avant d’envoyer en toute confiance la contrepartie. En effet, on peut démontrer mathématiquement que la probabilité que plusieurs blocs suite à la bifurcation soit validés simultanément diminue exponentiellement avec le nombre de blocs, tant qu’aucun nœud ne possède plus de 50% de la capacité de calcul du réseau. À titre d’exemple, un bloc nécessite en moyenne 10 minutes pour être validé sur la blockchain Bitcoin, il faut donc généralement attendre une heure après le paiement avant l’envoi de la contrepartie. 

Pourquoi la condition sur l’absence d’un nœud avec plus de 50% de la capacité de calcul du réseau ? Ceci nous amène à considérer une dernière attaque, la plus sournoise. Alice émet deux transactions sur le même Infocoin, l’une à destination de Bob, et l’autre à destination d’elle-même. Elle attend que le réseau confir 
