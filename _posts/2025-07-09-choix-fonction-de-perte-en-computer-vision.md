---
layout: post
title: choix-fonction-de-perte-en-computer-vision
date: 2025-07-09
url_wayback_machine: https://web.archive.org/web/20250709223119/https://www.quantmetry.com/blog/choix-fonction-de-perte-en-computer-vision/
---
Computer vision, Machine Learning 

27/06/2022 

#  Comment choisir sa fonction de perte en Computer Vision ? - Partie 1 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fchoix-fonction-de-perte-en-computer-vision%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Comment%20choisir%20sa%20fonction%20de%20perte%20en%20Computer%20Vision%20%3F%20-%20Partie%201&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fchoix-fonction-de-perte-en-computer-vision%2F "Twitter") [ ](https://www.quantmetry.com/blog/choix-fonction-de-perte-en-computer-vision/ "Email") [ ](https://www.quantmetry.com/blog/choix-fonction-de-perte-en-computer-vision/ "Copy Link")

* * *

Auteur : [ Julian Le Gouic ](https://www.linkedin.com/in/julian-le-gouic/)

Temps de lecture : 14 minutes 

![Quantmetry.com : Comment choisir sa fonction de perte en Computer Vision ? - Partie 1](https://www.quantmetry.com/wp-content/uploads/2022/06/mlise-en-avant-2.png)

Cet article s’inscrit dans une série d’articles dédiés aux fonctions de perte (loss function) dans le domaine de la Computer Vision. Au travers des deux premiers articles, nous vous accompagnerons dans le choix de la fonction de perte pour les cas d’usage les plus fréquents en Computer Vision. Un article subséquent traitera quant à lui de cas d’usage plus complexes. 

##  Qu’est-ce que la fonction de perte ? 

###  Objectif de la fonction de perte 

Dans le cas de la Computer Vision, les modèles avec lesquels nous travaillons sont pour la plupart du temps des réseaux de neurones par convolution. Ce type de modèle, comme beaucoup d’autres modèles de Machine Learning, a pour objectif d’apprendre à faire correspondre des valeurs en sortie (ou prédiction) à des données en entrée au travers d’un apprentissage. Cet apprentissage résulte d’un algorithme d’optimisation (le plus souvent celui de la descente du gradient), visant à obtenir des poids optimaux pour chaque neurone (ou filtre de convolution dans notre cas). Lors de cette optimisation, une fonction particulière est utilisée afin d’évaluer la pertinence d’une prédiction donnée par le modèle à chaque itération d’entraînement ; il s’agit de la fonction objectif. Cette fonction peut être interprétée de deux façons : soit on cherche à maximiser son résultat, soit à le minimiser. 

###  Quel niveau d’intervention ? 

Dans le scénario d’une maximisation, on pourrait l’interpréter comme un objectif de maximiser la ressemblance entre la prédiction du modèle et la vérité. À l’inverse, lors d’un scénario de minimisation, on chercherait plutôt à réduire l’écart entre la prédiction et la vérité, autrement dit l’erreur. C’est en général ce dernier scénario qui est adopté car il est plus pertinent de diminuer l’erreur au maximum, plutôt que de maximiser sa réussite dans un contexte d’optimisation. Cette prise de position conduit à l’appellation si connue de « fonction de coût » ou « fonction de perte » (aussi appelée _loss function_ ). 

###  Intérêt de la fonction de perte 

La fonction de perte doit alors être capable de réduire toute la complexité de la prédiction du modèle en un seul nombre, interprétable par l’utilisateur, et permettant alors de classer une meilleure prédiction d’une moins bonne, afin d’aider le processus d’optimisation dans sa recherche de poids optimaux. Et c’est dans la façon dont la fonction va capturer les propriétés du problème et résumer l’erreur de prédiction que réside toute la difficulté du choix de cette fonction. Il est très important de choisir une fonction qui représente nos objectifs de modélisation et qui calcule l’erreur du modèle en concordance avec le cas d’usage qui nous intéresse. 

##  Liste des cas d’usage dans la Computer Vision 

En computer vision, il existe une multitude de cas d’usage, qui peuvent parfois s’imbriquer les uns dans les autres. Avant de plonger plus en détail dans les critères de choix d’une fonction de perte adaptée à chaque cas d’usage, nous allons rappeler les principaux cas d’usage dans la Computer Vision. Nous compléterons cette liste avec des cas d’usage plus spécifique et de fait, des fonctions de perte plus particulières dans un prochain article. 

###  Terminologie 

Avant de rentrer directement dans le vif du sujet, quelques rappels sur des concepts récurrents en Computer Vision : 

  * Mono/Multi-classes : très répandu en Machine Learning, il n’en reste pas moins important de savoir dans quelle catégorie placer lorsque l’on commence une problématique supervisée – « A-t-on à faire à une seule ou plusieurs classes à prédire ? » 
  * Mono/Multi-labels : concept plus spécifique à des domaines comme la Computer Vision ou le Natural Language Processing ; il fait référence au nombre d’entités à prédire sur une image, un texte, etc. 



Une problématique multi-labels implique du multi-classes, l’inverse n’est pas vrai pour autant. Ces différences ont bel et bien un impact au niveau de la fonction de perte, c’est pourquoi il est primordial de bien savoir où se situer avant de choisir sa fonction. 

###  La classification d’image 

La classification d’image est probablement le cas d’usage le plus répandu et le plus connu de tous. Comme son nom l’indique, il s’agit de classifier des images en fonction de ce qu’elles contiennent. Par exemple, une image contenant un chat se verra attribuer le label « chat », une image de voiture se verra attribuer le label « voiture » et ainsi de suite. Un modèle peut être entraîné à reconnaître différents objets sur différentes images. En sortie, celui-ci fournit une probabilité à l’image d’appartenir à une classe cible. 

###  La détection d’objets 

Là encore un cas d’usage assez courant, la détection d’objets consiste à déterminer l’emplacement d’un ou plusieurs objets sur une image à l’aide d’une boîte de délimitation (ou plus communément appelée _bounding box_ ). La bounding box est un simple rectangle, souvent définie par quatre coordonnées (x, y, h, w), où x, y représentent les coordonnées sur l’image d’un coin de la bounding box (souvent le coin supérieur gauche) et h, w la hauteur et largeur en pixels de la bounding box. Plusieurs représentations sont possibles. Cette fois-ci, le modèle est entraîné pour fournir en sortie ces quatre coordonnées, et non pas une probabilité d’appartenir à une classe. 

###  La segmentation sémantique 

Dans ce troisième cas d’usage, nous commençons à sortir des sentiers battus, sans pour autant trop s’en éloigner. La segmentation sémantique est un peu moins connue du grand public, mais elle est pourtant présente dans notre quotidien. Ici, on se rapproche du premier cas d’usage, à la différence que la classification d’image sera plutôt à l’échelle « macro », tandis que la segmentation sémantique, elle, sera à l’échelle « micro ». Il s’agit d’attribuer un label, non pas à l’image entière, mais à chaque pixel. À première vue, cela ne semble pas très équivoque et pourtant, cette technique est utilisée dans les voitures autonomes, l’industrie de la mode, l’analyse d’images médicales, et bien d’autres domaines. 

###  La segmentation d’instance 

Enfin, notre dernier cas d’usage pour cet article : la segmentation d’instance. Ce cas d’usage est de loin le plus compliqué des quatre présentés, du moins au niveau de la structure des modèles utilisés. Dans la segmentation d’instance, en plus de déterminer l’emplacement de chaque objet à prédire sur l’image, les objets sont également segmentés à l’échelle du pixel et donc classifiés ! Pour dire les choses simplement, c’est un peu comme si on avait à faire à la fusion des trois cas d’usage précédents. 

##  Cas d’usage n°1 : classifier une image de chat 

###  Présentation du cas d’usage 

Pour ce cas d’usage, laissez-nous vous introduire notre ami Kitty, sur lequel nous nous proposons de faire de la classification d’image. ![](https://www.quantmetry.com/wp-content/uploads/2022/06/chat-2-wp.jpg)

Ici c’est très simple, il n’y a qu’un chat sur l’image, de ce fait, on attend du modèle qu’il détermine qu’il s’agisse bien d’un chat sur cette image. En réalité, ce dernier fournira une probabilité à l’image d’appartenir à la classe « chat ». Les différentes couches de convolution vont permettre d’extraire des caractéristiques (ou _features_ ) de l’image, et une fois l’information suffisamment condensée, le modèle procèdera à l’étape de classification et fournira la probabilité, d’appartenir à la classe « chat », comprise entre 0 et 1. Si elle est suffisamment élevée (i.e. au-dessus d’un seuil fixé par avance), on peut considérer que l’image appartient à la classe. 

###  Choisir sa fonction 

###  _Entropie croisée binaire (Binary Cross-entropy)_

Pour un tel cas, nous entrons dans le cadre d’une classification binaire. Pourquoi binaire ? Il suffit d’essayer de répondre à la problématique que nous nous sommes fixés au départ : « Est-ce un chat ? Oui ou non. », soit deux issues possibles. Par conséquent, la fonction de perte la plus adaptée est la binary cross-entropy ou « entropie croisée binaire ». Issue de l’entropie croisée, elle renvoie une mesure de la dissimilarité entre deux probabilités afin de pouvoir quantifier la différence entre celles-ci. La BCE (binary cross-entropy) est en réalité un cas particulier de la cross-entropy. Soit la formule de la cross-entropy : 

$$CE = \sum\limits_{i} p_i\log q_i$$ 

Avec $p_i$ la probabilité que l’évènement $i$ se produise et $q_i$ la probabilité prédite que l’évènement $i$ se produise. En définissant $y$ comme la probabilité que notre image appartienne à la classe « chat », et $\widehat{y}$ comme la probabilité prédite par notre modèle que notre image appartienne à la classe « chat », on a alors : 

$$CE = -(y\log\widehat{y} + (1 – y)\log(1-\widehat{y})) = BCE$$ 

Et où $1-\widehat{y}$ définit la probabilité selon notre modèle de ne pas appartenir à la classe cible. Et $1-y$ la vraie probabilité de ne pas y appartenir. On retrouve nos deux évènements de notre formule originale de la cross-entropy « appartenir à la classe chat » et « ne pas appartenir à la classe chat ». Dès lors, on peut généraliser la formule pour l’entièreté de nos $N$ images dans notre jeu de données d’entraînement avec la formule suivante : 

$$BCE = -\frac{1}{N}\sum\limits_{n=1}^N [y_n\log\widehat{y_n} + (1 – y_n)\log(1 – \widehat{y_n})]$$ 

NB : À savoir que lorsque l’on parle de la « vraie probabilité » $y$, on fait référence au label de l’image. Cette probabilité est donc soit 1 (l’image est celle d’un chat), soit 0 (l’image n’est pas celle d’un chat). Cela sera valable pour l’ensemble des explications à venir. 

###  Dans le cas multi-classes 

###  _Entropie croisée catégorielle (ou Categorical Cross-Entropy)_

Pour une problématique multi-classes, il est plutôt convenu d’utiliser non pas la binary cross-entropy mais la categorical cross-entropy. En repartant de notre définition précédente de la cross-entropy on obtient la nouvelle formule : 

$$CCE = -y_c\log\widehat{y_c} \textrm{, ou simplifiée } CCE = -\log\widehat{y_c}$$ 

Avec $\widehat{y_c}$ la probabilité prédite par notre modèle que notre image appartienne à la classe $c$ parmi les $C$ classes et $y_c$ la vraie probabilité que notre image y appartienne. Attention, pour ce cas de figure, il est très important de noter que la représentation des données joue un rôle majeur dans la simplification de l’équation. Lorsque nous sommes dans un cadre multi-classes, il est d’usage de représenter ces « vraies probabilités », par un vecteur à encodage one-hot. Par conséquent, en reprenant la formule de la cross-entropy, si nous définissons chaque évènement comme celui d’appartenir à la classe $c$, alors seule la probabilité prédite par notre modèle associée à la vraie classe $c$ sera retenue dans la formule. Pour notre jeu d’entraînement complet on aurait comme formule d’origine : 

$$CCE = -\frac{1}{N}\sum\limits_{n=1}^N\sum\limits_{c=1}^C y_{c,n}\log\widehat{y_{c,n}}$$ 

En effet, puisque le vecteur $y_{c,n}$ ne contient qu’une seule valeur non-nulle, seulement un seul des termes de la deuxième somme restera. 

###  Dans le cas multi-labels 

Pour une problématique multi-labels, plus rare dans ce cas d’usage mais pas impossible, il n’est pas d’usage d’utiliser la CCE (categorical cross-entropy) malgré le multi-classes, mais plutôt la BCE (binary cross-entropy) de nouveau. Au même titre qu’il n’est pas possible de faire du multi-classes directement avec un modèle SVM, il n’est pas possible d’utiliser la CCE directement pour du multi-labels. Comme pour un SVM, il est conseillé de décomposer le problème en sous-problèmes de classification mono-classe. Dans ce cas-là, cela revient à utiliser la BCE pour chacune des prédictions, de façon indépendante, et se ramener à des sous-problèmes de classification binaire : « L’image contient-elle un élément de cette classe ? Oui ou non. ». Une fois cette question répondue pour chacune des classes, on peut calculer la somme de toutes les BCE en tant que fonction de perte globale pour l’image. 

###  Pourquoi ? 

Les avantages de la CE (cross-entropy) sont multiples : 

  * Elle permet de pénaliser la différence entre la probabilité prédite et celle attendue 
  * Le score est logarithmique et renvoie donc de petites valeurs lorsque les probabilités de la classe à prédire sont élevées, et de grandes valeurs lorsque celle-ci sont faibles 
  * Il est donc très facile de comprendre que le score cible est 0, et que l’on cherche à la minimiser, la rendant simple d’interprétation 



##  Cas d’usage n°2 : détecter le chat sur l’image 

###  Présentation du cas d’usage 

Dans ce second cas d’usage, nous augmentons la difficulté d’un cran en essayant de rajouter l’information de la localisation du chat dans nos prédictions. Nous passons donc au cas d’usage de la détection d’objet. En plus de savoir s’il s’agit bien d’un chat sur notre image, nous souhaiterions avoir sa position dans l’image. ![](https://www.quantmetry.com/wp-content/uploads/2022/06/chat-2-wp-score.png)

### 

Dans la lignée de notre exemple, nous sommes toujours dans un scénario mono-classe, et nous souhaitons ajouter une information supplémentaire en sortie de notre modèle. Pour cette raison, une deuxième branche est ajoutée à la fin du réseau de neurones principal. Celle-ci servira à calculer et raffiner les coordonnées de la bounding box de notre chat. La première branche quant à elle, est en fait celle que nous venons de voir dans le cas d’une classification et permet de déterminer à quelle classe appartient l’image, en l’occurrence ici, la classe de la bounding box. Dans cette partie, nous nous focaliserons sur quelle fonction de perte appliquer sur la deuxième branche, la première étant traitée dans la partie précédente. 

###  Choisir une fonction de perte 

Pour rappel, une bounding box se définit par 4 composantes numériques que sont : les coordonnées (x,y) de son coin supérieur gauche dans l’image, sa largeur et sa hauteur en pixels. En conséquence, nous nous situons dans un problème de régression. Plusieurs fonctions de perte sont alors disponibles. 

###  _1\. L’erreur moyenne absolue (Mean Absolute Error ou L1 Loss)_

Cette erreur issue de la distance L1 ou distance de Manhattan, se focalise sur la magnitude des prédictions. Autrement dit, elle prend en compte l’écart qu’il y a entre les prédictions, ce qui la rend plus robuste face aux données aberrantes (outliers) dans un jeu de données. En revanche, elle n’est pas très optimisée en calcul et peut contenir des minimums locaux. 

$$MAE = \frac{1}{N}\sum\limits_{n=1}^N |y_n – \widehat{y_n}|$$ 

Avec $y_n$ et $\widehat{y_n}$ les vecteurs respectifs des coordonnées réelles et des coordonnées prédites de la bounding box pour l’image $n$, et $N$ le nombre d’images dans notre jeu de données d’entraînement. 

###  _2\. L’erreur quadratique moyenne (Mean Squared Error ou L2 Loss)_

L’erreur quadratique est sûrement la fonction de perte la plus connue et la plus largement utilisée pour des problèmes de régression en Machine Learning, et les problèmes de détection d’objet en Computer Vision n’y échappent pas. Là aussi les magnitudes sont moyennées, mais à la différence d’une valeur absolue, on élève l’erreur au carré (expliquant le terme quadratique dans le nom). Au même titre que la valeur absolue de la MAE, le carré assure des valeurs toujours positives et permet une interprétation simple en fixant la valeur cible à 0. De plus, la MSE assure une dérivée en 0 existante, ce qui est utile pour notre optimisation, contrairement à la MAE qui n’est pas dérivable en 0. Néanmoins, le carré sera plus punitif envers les erreurs plus grandes, ce qui la rendra moins stable face à d’éventuels outliers. 

$$MSE = \frac{1}{N}\sum\limits_{n=1}^N (y_n – \widehat{y_n})^2$$ 

###  _3\. L’erreur quadratique logarithmique moyenne (Mean Squared Logarithmic Error)_

Enfin, cette troisième variation intègre la fonction logarithme au sein de la MSE afin de contrer le dernier point faible cité. Le logarithme évite de donner trop d’importance aux grandes erreurs et permet de pénaliser de la même façon toutes les erreurs rencontrées. 

$$MSLE = \frac{1}{N}\sum\limits_{n=1}^N (\log({y_n} + 1) -\log(\widehat{y_n} + 1))^2$$ 

Grace aux propriétés de la fonction logarithmique, l’intérieur des parenthèses pourrait se réécrire de la sorte : 

$$\log({y_n} + 1) -\log(\widehat{y_n} + 1) = \log\left(\frac{{y_n} + 1}{\widehat{y_n} + 1}\right)$$ 

On peut donc voir qu’en réalité, la fonction de perte s’attarde plutôt sur la différence relative entre la valeur réelle et prédite. Sous cette représentation, on peut aussi voir qu’elle aura tendance à moins pénaliser les sous-estimations (ratio < 1) que les surestimations (ratio > 1), la rendant asymétrique. 

###  _4\. La fonction Huber (Huber loss)_

$$   
HL_{\delta} = \begin{cases}   
\frac{1}{2}(y – \widehat{y})^2 & |y – \widehat{y}| \leq \delta\\\   
\delta|y – \widehat{y}| – \frac{1}{2}\delta^2 & \textrm{sinon}   
\end{cases}   
$$ 

Nous vous présentons une dernière fonction de perte nommée la Huber loss. Souvent rencontrée dans des problèmes de régression, elle se charge de corriger certains inconvénients rencontrés dans les fonctions de perte présentées précédemment. En effet, cette fonction est une sorte de combinaison entre la MAE et la MSE grâce à son hyperparamètre _δ_ . On peut voir qu’elle oscille entre une équation quadratique et linéaire, selon la magnitude des prédictions, la rendant moins sensible aux outliers. Par la même occasion, cela règle le problème d’un éventuel minimum local lors de l’optimisation. En revanche, l’apparition d’un hyperparamètre rend la fonction plus complexe et par conséquent plus compliquée à optimiser, demandant plus de temps d’entraînement. 

A noter qu’aucune de ces fonctions ne fait appel à la notion de multi-classes ou multi-labels. Ces notions n’interviennent pas dans la régression et dans notre cas de figure, c’est la première branche de classification qui s’occupe de cette tâche, laissant le champ libre à la branche de régression de positionner la bounding box. 

###  Pourquoi ? 

Pour ce cas d’usage, il serait recommandé d’utiliser la MSE (mean squared error) plutôt que la MAE car il est peu probable d’avoir souvent à faire à des outliers et que beaucoup de calculs seront nécessaires. Par ailleurs, la MSLE (mean squared logarithmic error) est plutôt à favoriser dans un contexte où les prédictions ne suivent pas la même échelle et où de nombreuses surestimations peuvent être sujettes à apparaître. Par exemple, dans des problématiques de prédiction de prix de maisons, qui peuvent varier du tout au tout d’une maison à l’autre. La Huber loss reste une option envisageable mais pas nécessaire pour les mêmes raisons que nous ne rencontrerons pas d’outliers très souvent, et que l’avantage de la Huber loss ne vaut pas toujours le coup face aux coûts supplémentaires d’optimisation engendrés. 

#####  À suivre… 

_La suite des cas d’usage sera présentée dans un autre article très prochainement, alors stay tuned!_ 😉 

#####  [ ![](https://www.quantmetry.com/wp-content/uploads/2022/06/logo-expertise-computer-vision-300x177.png) ](https://www.quantmetry.com/experts/#computervision)

Les membres de l’expertise Computer Vision adressent des thématiques couvrant l’ensemble du cycle de valorisation des images : de la constitution du jeu de données à l’implémentation du modèle sur des dispositifs embarqués. 

####  ![](https://www.quantmetry.com/wp-content/uploads/2022/06/separation-1024x5.png)

![](https://www.quantmetry.com/wp-content/uploads/2022/06/julian-le-gouic-150x150.png)

[ **Julian LE GOUIC** ](https://www.linkedin.com/in/julian-le-gouic)   
Data Scientist chez Quantmetry 

Passionné par le Deep Learning, je me suis très vite spécialisé vers le domaine de la Computer Vision après un double diplôme en Data Science et Informatique & Systèmes intelligents. J’applique aujourd’hui mes compétences dans diverses missions de Computer Vision, mais pas seulement ! 
