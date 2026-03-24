# cryptage-homomorphique
Wayback Machine URL: https://web.archive.org/web/20230129145828/https://www.quantmetry.com/blog/cryptage-homomorphique/
Archive date: 2023-01-29

IA de confiance 

17/12/2020 

#  Peut-on confier des calculs sur des données sensibles à un tiers sans lui faire totalement confiance ? 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fcryptage-homomorphique%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Peut-on%20confier%20des%20calculs%20sur%20des%20donn%C3%A9es%20sensibles%20%C3%A0%20un%20tiers%20sans%20lui%20faire%20totalement%20confiance%20%3F&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fcryptage-homomorphique%2F "Twitter")

* * *

Auteur : [ Geoffray Brelurut ](https://www.linkedin.com/in/geoffray-brelurut/)

Temps de lecture : 9 minutes 

![Quantmetry.com : Peut-on confier des calculs sur des données sensibles à un tiers sans lui faire totalement confiance ?](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/article-gbr.png)

###  Peut-on confier des calculs sur des données sensibles à un tiers sans lui faire totalement confiance ? 

####  Problématique : 

La Data peut apporter énormément de valeur aux entreprises, mais elles doivent pour cela maîtriser l’énorme volume des données et parfois la vélocité avec laquelle les données sont acquises. Pour ne pas être débordées, il faut disposer de moyens de calculs importants, qui ne sont pas forcément accessibles à toutes les entreprises. 

C’est pourquoi des acteurs ont émergé pour vendre de la puissance de calcul et de l’espace de stockage sur le Cloud. Ceci soulève une nouvelle problématique : si les données apportent de la valeur, elles sont stratégiques. Peut-on donc les confier à un tiers sans les crypter ? Mais si elles sont cryptées comment ce tiers pourra-t-il effectuer tous les calculs nécessaires pour en extraire la valeur ? 

Au-delà des données stratégiques, ces questions s’appliquent à toutes les données sensibles, par exemple dans le domaine médicale. Avec ce type de données, même si les variables ne sont pas directement identifiantes, il reste facile d’identifier des dates, une taille, un poids ou un âge, afin de recouper les informations pour identifier les patients. L’anonymisation des données n’est donc pas suffisante. Un autre exemple est celui des données géolocalisées. Des données de latitude et de longitude sont facilement identifiantes et exploitables. En effet, même si le nom des variables n’est pas explicite, une fois leur nature identifiée, il n’y a que deux solutions à tester pour retrouver la localisation des observations. Cette faille peut être problématique les libertés individuelles mais également pour l’activité elle-même, par exemple si le lieu identifié est une base militaire ou un laboratoire d’expérimentation animale. 

####  Cryptage classique et limites : 

La solution pour empêcher toute exploitation des données est évidemment de les modifier pour les rendre méconnaissables. C’est ce que réalise le cryptage. Ainsi, dans une approche de cryptage classique, on considère deux interlocuteurs : l’émetteur et le récepteur. L’émetteur applique une transformation sur un message (qui peut être un texte comme un tableau de données). Cette transformation est réalisée par l’algorithme de cryptage et dépend en général d’une paire de clés : la clé publique qui permet le chiffrement des messages, et la clé privée qui permet le déchiffrement des messages. 

Lors d’un échange de données cryptées classique, le récepteur a au préalable envoyé à l’émetteur une clé à partir de laquelle le message est chiffré (la clé publique). L’émetteur envoie donc un message crypté grâce à la clé publique fournie par le récepteur. Le récepteur décode le message grâce à un algorithme de décryptage et une clé qui n’est connue que de lui (la clé privée). Si un message doit être renvoyé en réponse à l’émetteur, alors il devient le récepteur, et le schéma s’inverse : le message est crypté grâce à sa clé publique, et il le décrypte avec sa clé privée. 

Pour que ce système fonctionne, les deux clés doivent être distinctes, on parle de chiffrement asymétrique. Un exemple de chiffrement asymétrique est le protocole RSA (ici en version simplifiée) : 

Le choix de la clé publique et le cryptage des messages suivent le protocole suivant : 

  * choisir 2 nombres premiers _p_ __ __ et  _q_ __
  * calculer _n_ , tel que  _n = pq_
  * choisir un entier  _e_ __ parmi de façon judicieuse (les concepts mathématiques qui permettent de choisir sont très avancés et dépassent le périmètre de cet article) 
  * le message  _m_ __ est crypté, donc transformé en message __ _c_ __ : __ _ c =  m  e  mod(n)  _



La clé publique est donc le couple  _ (e, n)  _ . 

Pour décrypter le message, il faut trouver la racine _e me  _ modulo  _n_ __ de  _ c  _ . Ce calcul est facile si  _ p  _ et __ _q_ __ sont connus. Mais, il est très difficile de trouver  _ p  _ et  _ q  _ à partir de  _ n  _ . En pratique la clé privée est l’inverse de  _ e  _ modulo  _n_ , noté __ _d_ :  _ m =  c  d  mod(n)  _ . __ _ d  _ conserve donc toute l’information concernant  _ p  _ et  _q_ __ ainsi que le choix de __ _ e  _ .  _n_ __ est quant à elle obtenue à partir de la clé publique. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/classique-1-1024x556.png)  
---  
Figure 1 : Echange de données avec un cryptage classique   
  
L’approche classique présente deux défauts : 1) elle implique un partage de clé entre les deux interlocuteurs, qui peut donc être interceptée par un tiers, et 2) le récepteur peut décoder les données qui deviennent donc accessibles par son biais. L’approche permet donc potentiellement d’accéder aux données via le cloud provider. En fait, elle ne sécurise que le transfert de données. En effet, les clés sont un moyen d’identification mutuelle des interlocuteurs, ce qui empêche un troisième acteur d’avoir accès à l’information qu’ils échangent. Mais elle ne résout pas le problème d’un récepteur auquel on ne ferait pas confiance. 

###  Cryptage homomorphique : 

Pour pallier les défauts mentionnés précédemment, il faut pouvoir utiliser les données cryptées pour les calculs et que l’émetteur n’ait plus qu’à appliquer l’algorithme de décryptage sur le résultat renvoyé. Il faut alors que le résultat décrypté soit équivalent à celui qu’on aurait obtenu sur les données avant cryptage. Cela implique que le cryptage doit conserver les caractéristiques mathématiques des données, une propriété appelée homomorphie. C’est pourquoi on parle de cryptage homomorphique. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/10/homomorphique-1-1024x580.png)  
---  
Figure 2 : Echange de données avec un cryptage homomorphique   
  
####  Types de cryptages homomorphiques : 

Le cryptage peut être caractérisé par les opérations pour lesquelles il est homomorphique. On distingue ainsi du moins complet au plus complet : 

  * le cryptage homomorphique partiel (PHE, Partial Homomorphic Encryption) qui ne permet qu’un type d’opération : addition ou multiplication 
  * le cryptage un peu homomorphique (SHE, Somewhat Homomorphic Encryption) qui permet les deux types d’opérations, mais seulement dans des séquences bien définies 
  * le cryptage complètement homomorphique nivelé (LFHE, Leveled Fully Homomorphic Encryption) : qui permet tout type d’opération mais seulement pour des séquences de longueur définie 
  * le cryptage complètement homomorphique (FHE, Fully Homomorphic Encryption) : qui permet tout type d’opération quelque soit la longueur de la séquence. 



Un exemple de cryptage homomorphique partiel multiplicatif est le protocole RSA, dont le cryptage prend la forme : _ε_ _ (m) =  m  e  mod(n)  _ . Considérant le produit de deux messages  _ m  1  _ et  _ m  2  _ : 

_ ε(  m  1  )ε  (  m  2  ) =  m  1  e  m  2  e  mod(n)  _

_ ε(  m  1  )ε  (  m  2  ) = ε  (  m  1  m  2  )  e  mod(n)  _

_ ε(  m  _
