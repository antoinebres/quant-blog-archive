---
layout: post
title: programmation-des-blockchains-et-smart-contracts
date: 2023-06-06
url_wayback_machine: https://web.archive.org/web/20230606103314/https://www.quantmetry.com/blog/programmation-des-blockchains-et-smart-contracts/
---
Uncategorized 

31/05/2017 

#  Programmation des blockchains et “smart contracts” 

[ ](http://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fprogrammation-des-blockchains-et-smart-contracts%2F&title=Programmation%20des%20blockchains%20et%20%E2%80%9Csmart%20contracts%E2%80%9D "Linkedin") [ ](http://twitter.com/intent/tweet?text=Programmation%20des%20blockchains%20et%20%E2%80%9Csmart%20contracts%E2%80%9D&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fprogrammation-des-blockchains-et-smart-contracts%2F "Twitter") [ ](https://www.quantmetry.com/blog/programmation-des-blockchains-et-smart-contracts/ "Email") [ ](https://www.quantmetry.com/blog/programmation-des-blockchains-et-smart-contracts/ "Copy Link")

* * *

Temps de lecture : 5 minutes 

![Quantmetry.com : Programmation des blockchains et “smart contracts”](https://quantmetry.b-cdn.net/wp-content/uploads/2017/05/7y7kd68t-1462762406.jpg)

_Ceci est le second d’une série de trois articles sur la technologie blockchain. L’objectif ici est de comprendre comment on peut programmer les blockchains pour définir des clauses à exécution automatique, et ainsi créer des smart contracts !_

Dans le premier article de la série, nous avons montré en quoi la technologie blockchain constituait une solution naturelle au transfert de valeur entre deux agents sans tiers de confiance. Maintenant que le fonctionnement théorique d’une blockchain a été expliqué, comment cela-t-il marche concrètement ? 

##  Programmation des blockchains et smart contracts 

On peut se brancher sur une blockchain en téléchargeant des outils spécifiques, qui vont télécharger en local tout l’historique des transactions composant la blockchain. Alice et Bob disposent alors chacun d’un portefeuille numérique : une paire de clefs privée/publique du protocole RSA, où la clef publique hashée représente une adresse dans laquelle des actifs (des Bitcoins par exemple) peuvent être « déposés » par un tiers, tandis que la clef privée permet de « dépenser » le contenu du portefeuille. Il convient de distinguer ces paires de clefs de celles servant à la signature numérique dans le cadre du protocole blockchain (voir Fig. 1). 

À noter que ce qui est en réalité associé à une adresse est un historique des transactions ayant utilisé cette même adresse, représentant ainsi une sorte de « solde », que l’utilisateur sera autorisé à utiliser dans des nouvelles transactions : il n’existe donc pas d’objet Bitcoin comme il existe une pièce d’un euro ! 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/1-4-1.png)

Figure 1 : Interface d’un outil pluggé sur la blockchain Bitcoin 

Une fois un outil téléchargé et l’accès à la plateforme assuré, une transaction correspondra à une structure de données créée, transmise via le réseau, et validée avant ajout au registre. Dans la figure 2 ci-dessous est représentée une transaction du protocole Bitcoin : la première ligne représente le hash de la transaction, la seconde la version du protocole, la troisième le nombre de transactions à partir desquelles calculer un solde pour vérifier la validité de la nouvelle transaction, la quatrième le nombre de bénéficiaires de la nouvelle transaction, et les deux suivantes des informations techniques sur le protocole. Les blocs « in » et « out » correspondent à des détails fixant les modalités d’émission et de réception du Bitcoin. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/2-4-1.png)

Figure 2 : Structure de données d’une transaction Bitcoin 

Considérons le bloc « prev_out » de la partie « in ». Il contient : 

  * Le hash de la transaction précédente dont le solde doit être consommé, 

  * Une commande « scriptSig » donnant des informations nécessaires au déverrouillage de ce solde. Cette commande est composée de deux éléments : 

    * Le premier représente une signature sur la transaction en cours via la fonction de hashage fixe du protocole et la clef privée de l’émetteur, 

    * Le second correspond à la clef publique de l’émetteur. 




Que manque-t-il au déverrouillage du solde ? Il faut considérer pour cela le bloc « out » de la transaction précédente. Tout comme le bloc « out » de notre nouvelle transaction, il est composé d’une valeur de transaction en Bitcoin (valeur transmise par Alice à Bob) et d’un programme dans le langage « Script », spécifique à la blockchain Bitcoin et basé sur la notion de pile. Ce bout de code permet de s’assurer que seul Bob pourra bien dépenser la valeur transmise par Alice. L’exécution de la transaction entre Alice et Bob consiste alors en la concaténation du bloc scriptSig de la transaction en cours Tx2 avec le scriptPubKey de la transaction précédente Tx1 (voir Fig. 3). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/3-3-1.png)

Figure 3 : Verrouillage et déverrouillage d’un Bitcoin 

L’exécution de la concaténation scriptSig(Tx2) + scriptPubKey(Tx1) suit les étapes suivantes : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/4-3.png)

Ainsi, scriptSig d’une transaction fournit les opérandes au programme scriptPubKey de la transaction précédente, déverrouillant ainsi le solde d’Alice pour un transfert de Bob vers un tiers Charlie. Les modalités de ce dernier transfert sont quant à elle fixées dans la partie scriptPubKey de Tx2. On constate ainsi qu’il s’agit d’un fonctionnement récursif : l’opération de déverrouillage est en réalité exécutée depuis le premier bloc de la blockchain jusqu’à la transaction en cours à chaque nouvelle transaction ! Des arborescences N-N sont possibles : plusieurs transactions sont analysées en entrée pour calculer le solde à transférer vers plusieurs tiers. 

Le bout de code contenu dans scriptPubKey est variable, avec quelques scripts très utilisés correspondant à des opérations standards sur la blockchain Bitcoin : 

• pay-to-public-key-hash (P2PKH, 98% des transactions entre 2009 et 2014) 

• public-key 

• multi-signature (limité à 15 clefs) 

• pay-to-script-hash (P2SH) 

• data output (OP_RETURN) 

Le langage Script est sans boucle et donc non Turing complet. Ceci présente à la fois des avantages et des inconvénients. 

Parmi les avantages de ce langage, l’absence de bombe logique (une boucle qui ne termine jamais car la condition est toujours vérifiée, exemple : while 0 < 1 do … ) n’est pas des moindres, assurant ainsi une grande sécurité au protocole Bitcoin car il est très difficile de réaliser des attaques de déni de services. La simplicité volontaire du langage, et la variabilité relativement limitée des programmes que l’on peut créer assurent à chaque nœud du réseau la possibilité d’exécuter des transactions, ainsi qu’un temps de transaction prévisible. Les inconvénients de ce type de langage sont que l’on ne peut pas coder n’importe quel type de transaction. En particulier, on ne peut traiter des données externes pour déclencher des actions. Ces limitations ont été à l’origine de la création de blockchains basées sur des langages Turing complet, permettant ainsi la programmation sans limitation de transactions ou « smart contracts », y compris avec un recours à des données extérieures (voir Fig. 4 pour un morceau de code et une interface graphique de création de smart contracts de la blockchain Ethereum). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/7-2.png)

Figure 4 : Langage Solidity et Mist Browser de la blockchain Ethereum 

L’objectif à terme est de permettre une création facilitée de contrats dont les clauses sont exécutées automatiquement, dès que les conditions sont réunies, et sans recours à un tiers. Ces conditions correspondent en général à une combinaison des informations liées aux deux parties de la transaction et d’informations extérieures. Par exemple, déclencher l’ouverture d’une voiture ou d’une maison en location dès l’approche du loueur, rembourser automatiquement un agriculteur selon les modalités de son contrat d’assurance suite à des événements climatiques dont l’information est disponible en ligne, ou encore encoder des transactions financières basées sur des informations issues des marchés financiers. 

Nous vous donnons rendez-vous sur le blog pour en savoir plus sur les usages concrets de la technologie blockchain dans notre troisième et dernier article de la série ! 

##  Références : 

[ http://www.michaelnielsen.org/ddi/how-the-bitcoin-protocol-actually-works/ ](http://www.michaelnielsen.org/ddi/how-the-bitcoin-protocol-actually-works/)
