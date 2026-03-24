---
layout: post
title: auditer-chatgpt-un-enjeu-de-survie-pour-les-llms-en-europe
date: 2025-05-19
url_wayback_machine: https://web.archive.org/web/20250519113535/https://www.quantmetry.com/blog/auditer-chatgpt-un-enjeu-de-survie-pour-les-llms-en-europe/
---
IA de confiance, NLP 

15/09/2023 

#  Auditer ChatGPT, un enjeu de survie pour les LLMs en Europe 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fauditer-chatgpt-un-enjeu-de-survie-pour-les-llms-en-europe%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Auditer%20ChatGPT%2C%20un%20enjeu%20de%20survie%20pour%20les%20LLMs%20en%20Europe&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fauditer-chatgpt-un-enjeu-de-survie-pour-les-llms-en-europe%2F "Twitter") [ ](https://www.quantmetry.com/blog/auditer-chatgpt-un-enjeu-de-survie-pour-les-llms-en-europe/ "Email") [ ](https://www.quantmetry.com/blog/auditer-chatgpt-un-enjeu-de-survie-pour-les-llms-en-europe/ "Copy Link")

* * *

Auteurs : [ Hadrien Strichard ](https://www.linkedin.com/in/hadrien-strichard-19a14218b/) , [ Grégoire Martinon ](https://www.linkedin.com/in/gregoire-martinon/) , [ Aymen Mejri ](https://www.linkedin.com/in/aymen-m-1b10b0122/) , [ Hao Li ](http://www.linkedin.com/in/hao-li-phd/)

Temps de lecture : 20 minutes 

![Quantmetry.com : Auditer ChatGPT, un enjeu de survie pour les LLMs en Europe](https://www.quantmetry.com/wp-content/uploads/2023/09/falseorange.png)

Introduit par OpenAI en novembre 2022, ChatGPT a bouleversé notre société par ses performances sans précédent et son adoption fulgurante. Derrière ce chatbot se trouve un puissant modèle de langage, GPT-4 (ou 3.5 pour la version gratuite). Depuis, le nombre de modèles du même genre a explosé (Google Bard, Llama, Claude…). Qui sont-ils ? Que peut-on faire avec ? Sont-ils dangereux ? Peut-on les auditer pour garantir un usage sécurisé ? 

Dans cet article : 

  1. Qu’est-ce qu’un LLM ? 
  2. L’histoire technologique de ChatGPT 
  3. Pourquoi tout le monde en parle ? 
  4. Que peut-on faire avec un LLM ? 
  5. Est-ce que c’est dangereux ? 
  6. Comment faire face à ses risques ? 
  7. Comment auditer de tels modèles ? 
  8. Conclusion : que peuvent faire Quantmetry et Capgemini Invent ? 



##  Qu’est-ce qu’un LLM ? 

L’intelligence artificielle, ou IA, est un domaine technologique visant à donner des capacités de l’intelligence humaine à des machines [1]. Une IA générative est une IA capable de générer du contenu, comme du texte ou des images. Les modèles de fondation sont un paradigme récent en intelligence artificielle générative, et sont souvent les briques fondamentales derrière des applications comme Dall-E ou MidJourney [2]. Dans le cas d’une IA générant du texte, on parle alors de LLM (Large Language Model), dont GPT est un exemple rendu populaire par le logiciel ChatGPT [3]. Des définitions plus complètes sont dans la Figure 1. 

![Définitions intelligence artificielle](https://www.quantmetry.com/wp-content/uploads/2023/09/definitions-llm.png)

Figure 1 : Définitions gigognes, de l’intelligence artificielle à ChatGPT [30] 

##  L’histoire technologique de ChatGPT 

**En 2017** , une équipe de chercheurs crée un nouveau modèle de traitement automatique du langage (aussi appelé NLP – Natural Language Processing). Ce modèle, le **Transformer** , permet d’obtenir des performances spectaculaires pour des tâches sur des données séquentielles, comme du texte ou des données temporelles [4]. Notamment, en utilisant la technologie de l’attention, parue en 2015 [5], le transformer parvient à repousser très loin les limites des modèles précédents concernant la longueur des textes traités ou générés. Technologiquement, un transformer est une architecture complexe utilisant des réseaux de neurones récurrents et des systèmes d’attention. 

En **2018** , OpenAI va s’inspirer des Transformers, et notamment de la partie utilisant de l’attention masquée (le décodeur), car cette partie est spécialisée dans la génération de texte. Ainsi, l’entreprise américaine va mettre au point la première version de **GPT** – Generative Pre-trained Transformer [6]. La même année sort BERT, un modèle NLP par Google aussi inspiré des Transformers [7]. Ensemble, BERT et GPT lancent l’ère des LLMs. 

Améliorant les performances de son modèle, OpenAI va continuer avec **GPT-2 en 2019** et **GPT-3 en** **2020** [8]. Ces deux modèles constituent une véritable rupture avec les autres LLMs, notamment les variantes de BERT, car ce sont des modèles fonctionnant en meta-learning. Le meta-learning est un type de modèle en Machine Learning où le modèle « apprend à apprendre », c’est-à dire que le modèle sait répondre à des tâches différentes que celles avec lesquelles il a été entrainé. 

La volonté d’OpenAI est que les modèles GPT puissent effectuer n’importe quelle tâche NLP sans avoir besoin de toute une base de données pour l’entrainer, seulement d’une consigne et éventuellement de quelques exemples. OpenAI est parvenu à faire du **meta-learning** une force, grâce à des architectures et des bases de données toujours plus grandes, massivement récupérées sur internet. 

Pour aller plus loin, OpenAI sort du cadre du NLP avec ses modèles suivants et adapte sa technologie aux images. C’est ainsi que OpenAI publie en **2021 et 2022 Dall-e 1 et Dall-e 2** , des générateurs d’images [9]. Cela lui permettra, pour GPT-4, de passer sur un modèle multi-modal capable de comprendre plusieurs types de données. 

Avant GPT-4, OpenAI publie **InstructGPT** (GPT 3.5) [10], conçu pour mieux répondre aux demandes des utlisateurs et aux risques grandissants. C’est avec GPT-3.5 qu’OpenAI lance **ChatGPT fin 2022** [3]. En **mars 2023** , une version aux performances encore meilleure et avec une sécurité renforcée sort en premium sur ChatGPT, c’est **GPT-4** [11]. Contrairement aux premières versions, GPT-3.5 et GPT-4 ont un fort intérêt commercial via le produit ChatGPT. OpenAI est donc passé sur du closed source, ne révèle plus le fonctionnement des modèles, et est devenu une entreprise (c’était à la base une association à but non lucratif). Pour le futur, beaucoup de rumeurs circulent, mais on peut s’attendre à ce qu’OpenAI essaye d’aller plus loin encore dans l’idée d’un prompt pour toutes les tâches et types de données. 

##  Pourquoi tout le monde en parle ? 

###  **OpenAI a réussi deux tours de force**

Open AI a réussi deux tours de force avec ChatGPT. Le premier est technologique. Les performances de GPT-3.5 et GPT-4 sont impressionnantes et inégalées. OpenAI a réussi son pari d’avoir, grâce au meta-learning, un modèle ultra-polyvalent pouvant répondre correctement à toutes les demandes, même celles qu’il n’a jamais vu avant. En effet, GPT-4 obtient de meilleurs résultats sur des tâches spécifiques que des modèles spécialisés [11]. 

Le deuxième tour de force d’OpenAI est celui de la démocratisation. En déployant sa technologie sous la forme d’un ChatBot (ChatGPT) accessible à tous via une interface simple, Open AI a permis à tout le monde d’avoir accès aux performances de ses LLMs surpuissants. L’ouverture au grand public permet aussi à OpenAI de récolter plus de données et des feedbacks pris en compte par le modèle. 

###  **Une adoption fulgurante**

La fulgurance de l’adoption de la technologie GPT via ChatGPT est un cas inédit dans l’histoire. Jamais une plateforme internet ou une technologie n’avait été adoptée aussi rapidement par le monde entier (cf Figure 2). ChatGPT représente aujourd’hui 200 millions d’utilisateurs et 2 milliards de visites par mois [13]. 

![Vitesse d’atteinte des 100 millions d’utilisateurs par application](https://www.quantmetry.com/wp-content/uploads/2023/09/timetoreach100m.png)

Figure 2 : Vitesse d’atteinte des 100 millions d’utilisateurs en mois [12] 

Ce dynamisme d’usage se retranscrit dans le monde technologique et scientifique. Le nombre de LLMs explosent, avec des concurrents venus de Google (Bard), Meta (Llama) ou encore Huggingface (HuggingChat, version française et open source). Leurs applications aussi, les LLMs sont implémentés dans les moteurs de recherche par exemple, ou au sein d’autres technologies comme l’impressionnant Auto-GPT qui permet d’utiliser GPT-4 en agent autonome. Quant au monde de la recherche, les publications concernant les LLMs connait une croissance phénoménale (Figure 3). 

![Nombre de publications scientifiques cumulées sur les LLMs](https://www.quantmetry.com/wp-content/uploads/2023/09/llm-publication.png)

Figure 3 : Nombre de publications scientifiques cumulées sur les LLMs [14] 

###  **Des opportunités, des fantasmes et des craintes**

L’arrivée retentissante de ChatGPT dans notre société a engendré une fascination pour les LLMs. Beaucoup voient dans ces gigantesques modèles de grandes opportunités. Les nouveaux états de l’art établis par GPT-4 ont ouvert le champ des cas d’usages, et de nombreuses institutions cherchent à les exploiter. Par exemple, certains hôpitaux s’en servent pour améliorer et automatiser l’extraction des conditions médicales des dossiers des patients [15]. 

D’un autre côté, ces mêmes percées en performances suscitent de nombreuses craintes : précarisation de l’emploi, triche aux examens, danger pour la vie privée… Ainsi, on voit fleurir dans les médias une kyrielle d’articles plus inquiétant les uns que les autres. Ces craintes semblent d’autant plus justifiées qu’elles sont exprimées par certains des personnages les plus emblématiques de la tech, comme Elon Musk ou Geoffrey Hinton (cf Figure 4). 

Cependant, il n’est pas toujours aisé de distinguer le risque réel de la peur irrationnelle. Comme souvent lors d’une avancée technologique, le fantasme du robot prenant le contrôle comme dans Terminator revient, ou du moins celui d’un modèle atteignant l’intelligence d’un cerveau humain avec même une certaine forme de conscience. On peut néanmoins relever que ce dernier fantasme est le but affiché par OpenAI sous le nom d’AGI (Artificial General Intelligence) [17]. 

Que ces opportunités et ces craintes soient des fantasmes ou des réalités, GPT-4 et les autres LLMs ont pour sûr bouleversé notre société et représentent un jalon technologique considérable. 

![Articles de journaux craintes et fantasmes LLMs](https://www.quantmetry.com/wp-content/uploads/2023/09/headlines.png)

Figure 4 : Articles de journaux concernant les craintes et fantasmes autour des LLMs [16] 

##  Que peut-on faire avec un LLM ? 

Un LLM peut : 

  1. Générer du contenu en langage naturel – C’est ce qu’ils font de mieux car c’est ce pour quoi ils ont été entrainés. Ils cherchent au mieux à respecter les contraintes qui leur ont été données. 
  2. Reformuler du contenu – Il s’agit de donner au LLM un texte de base et une consigne telle que faire une synthèse, traduire, changer des termes ou corriger des fautes. 
  3. Rechercher du contenu – On peut demander à un LLM, à partir d’un corpus, de retrouver et restituer des informations. 



Ces trois usages relevés dans le monde scientifique [18] sont illustrés dans la Figure 5. 

![Exemples de Prompt et réponses de ChatGPT](https://www.quantmetry.com/wp-content/uploads/2023/09/exemplesllm.png)

Figure 5 : Exemples de Prompt et réponses de ChatGPT pour illustrer les 3 usages d’un LLM 

###  **Comment utiliser un LLM ?**

Il y a trois applications possibles pour un LLM, résumé en Figure 6. La première est l’application directe, où on utilise seulement le LLM pour les tâches qu’il sait accomplir. C’est, a priori, le cas d’un chatbot tel que ChatGPT qui implémente directement la technologie GPT-4 [3]. Cette application, la plus commune, et aussi une des plus risquées car le LLM agit souvent comme une boite noire très dure à évaluer. 

Le cas d’usage émergeant est celui de l’application auxiliaire. Pour limiter les risques, le LLM est ici implémenté comme étant un outil auxiliaire au sein d’un système. Par exemple, dans un moteur de recherche, le LLM peut être utilisé comme interface de restitution des résultats, mais n’est pas utilisé pour la recherche d’information. L’inconvénient est que le LLM est loin d’être pleinement exploité. Ce cas d’usage a été appliqué au corpus constitué de rapports du GIEC [19]. 

L’application orchestre est certainement l’implémentation des LLMs qui va concentrer les recherches des grandes entreprises pour le futur. Dans une application orchestre, le LLM, en plus d’être l’interface d’échange et de restitution avec l’utilisateur, est aussi le cerveau du système dans lequel il est implémenté. Le LLM comprend donc la tâche, fait appel ou non à des outils auxiliaires de son système (ex : Wolfram Alpha pour des calculs mathématiques), puis restitue le résultat. Le LLM agit ici moins comme une boite noire mais l’évaluation des risques d’un tel système dépendra aussi beaucoup des outils auxiliaires. Le meilleur exemple à ce jour est Auto-GPT, un agent autonome basé sur GPT-4 [20]. 

![trois applications possibles d’un LLM](https://www.quantmetry.com/wp-content/uploads/2023/09/application-llm.png)

Figure 6 : Les trois applications possibles d’un LLM [30] 

###  Focus sur le Chatbot citant ses sources 

Comme expliqué dans la partie précédente, utiliser un LLM comme outil auxiliaire pour restituer les résultats d’un système intelligent plus global est un usage qui se démocratise beaucoup en ce moment. Ainsi, on limite les risques du LLM en limitant son usage à ce qu’il sait faire de mieux, générer du texte. 

Un cas d’usage précis qui émerge chez nos clients est celui d’un chatbot citant ses sources. Ce cas d’usage permet de palier à un des grands défauts des LLMs : l’opacité de leur interprétabilité (i.e. l’impossibilité de comprendre pourquoi et à partir de quelles sources le LLM a abouti à son résultat). Néanmoins cela a pour inconvénient d’être loin de pleinement utiliser les capacités du LLMs. 

Pour rentrer dans le détail technique du chatbot citant ses sources (illustré en Figure 7), le modèle va prendre en entrée une requête de l’utilisateur, que le modèle transforme en embedding (i.e. vectorisation de mots ou ensembles de mots qui capturent les relations sémantiques et syntaxiques). Au préalable, le modèle dispose d’un corpus de textes déjà transformés en embeddings. Il s’agit ensuite de trouver les embeddings du corpus les plus proche de l’embedding requête. Il y a pour cela des techniques de de recherche des plus proches voisins. 

Une fois qu’on a repéré les éléments du corpus pouvant aider pour la réponse, on les transmet à un LLM pour qu’il en fasse la synthèse. À côté de sa réponse, on pourra fournir les éléments ayant servis à la concevoir. Le LLM n’est donc qu’une interface de restitution d’un moteur de recherche. À noter cependant qu’un LLM peut éventuellement être aussi utilisé pour effectuer l’embedding. 

![](https://www.quantmetry.com/wp-content/uploads/2023/09/agentconversationnel.png)

Figure 7 : Schéma technique d’un agent conversationnel citant ses sources [30] 

##  Est-ce que c’est dangereux ? 

Utiliser un LLM n’est pas sans risque, voici une cartographie (Figure 8) des dangers liés à leurs usages. À noter qu’il n’existe pas de référentiel standard pour cela [11][21]. Quelques réponses issues des premières versions de GPT-4 sont en Figure 9 [11]. 

![Cartographie risques LLMS](https://www.quantmetry.com/wp-content/uploads/2023/09/risques.png)

Figure 8 : Cartographie des risques liés aux LLMS [30] 

Certains de ces dangers sont liés au modèle en lui-même (ou à l’entreprise le développant) : les données du modèle comportent toutes sortes de biais, les résultats ne sont pas traçables, les données utilisateurs ou les droits d’auteurs ne sont pas ou peu protégés, etc. 

D’autres sont liés à l’usage de ces modèles. Les utilisateurs parviennent à contourner les mesures de sécurité des modèles et à les utiliser pour des fins malveillantes, comme générer un message de haine ou de propagande. 

Enfin, les LLMs ont des conséquences sociales, environnementales et culturelles qui peuvent être néfastes. Ce sont des modèles gigantesques qui consomment énormément de stockage et d’énergie. Leur arrivée dans notre société a fragilisé des emplois et fut un des sujets de la grève des scénaristes à Hollywood par exemple [15]. Enfin, ils remettent en question les frontières de l’art sur des sujets littéraires, comme Dall-e l’avait fait sur de l’art graphique [15]. 

![Exemples risques LLMs](https://www.quantmetry.com/wp-content/uploads/2023/09/risque-exemples.png)

Figure 9 : Exemples de risques liés aux LLMs [11] 

##  Comment faire face à ces risques ? 

###  **Les développeurs de LLMs investissent dans des garde-fous**

Cette fois-ci encore, l’exemple d’OpenAI et de ChatGPT est intéressant. OpenAI a investi 6 mois de recherche pour établir des garde-fous et sécuriser l’utilisation des modèles GPT. Il est important dans un premier temps de souligner les avancées qu’ils ont obtenues. Pour une majorité de requêtes risquées, ChatGPT refuse de répondre. Quant à ses réponses, elles sont plus performantes sur les benchmarks évaluant des aspects comme la véracité ou la toxicité. De plus, contrairement à des modèles antérieurs qui prenaient aussi en compte le feedback des utilisateurs, ChatGPT n’a pas dérivé et on peut même dire qu’il s’est amélioré depuis son déploiement [11]. 

Néanmoins, on est encore loin d’un modèle suffisamment sécurisé. Les garde-fous établis sont contournables et des exemples de prompts permettant de les transgresser fleurissent sur internet (les DAN – Do Anything Now). Ces DANs se basent souvent sur le fait que les garde-fous de ChatGPT sont construits par alignement sur les humains – le modèle cherche au plus à satisfaire l’utilisateur, quitte à outrepasser son cadre éthique ou à créer un biais de confirmation. Par ailleurs, l’opacité du modèle et de ses données est à la source des problèmes de droits d’auteurs ou de biais incontrôlés. Quant au benchmark d’évaluation sur lesquels GPT-4 est performant, les suspicions de contamination avec la base de données d’entrainement nuit à leur valeur objective. Enfin, malgré des efforts annoncés pour réduire leurs tailles, les modèles d’OpenAI consomment beaucoup de ressources [15]. 

Parmi les nombreux autres LLMs étant apparus depuis, certains se revendiquent plus éthiques ou sûrs, mais cela se fait parfois au détriment de la performance, aucun n’est sans faille, et il n’existe pas pour l’instant de méthode d’évaluation claire et fiable sur le sujet. 

####  La sécurité en 5 étapes pour GPT-4 

Pour rentrer plus en détail sur le sujet de l’implémentation des garde-fous, toujours en prenant GPT-4 pour exemple, cela a été fait en 5 étapes par OpenAI, comme montré en Figure 10 [11]. 

  1. **Adversarial testing :** des experts de domaines variés ont été embauchés pour tester les limites de GPT-4 et trouver ses failles 
  2. **Supervised policy :** Après son entrainement, des annotateurs montrent au modèle des exemples de réponses voulus pour l’affiner (fine-tuning). 
  3. **RBRM :** ces classifieurs ont pour rôle de décider si un prompt et / ou sa réponse sont « valides » (ex : un classifieur qui permet d’invalider les demandes toxiques) 
  4. **Reward model :** des annotateurs humains entrainent un modèle de récompense en classant 4 possibles réponses du modèle du meilleur ou moins aligné. 
  5. **Reinforcement learning :** avec des techniques d’apprentissage par renforcement, le modèle prend en compte les retours des utilisateurs. 



![](https://www.quantmetry.com/wp-content/uploads/2023/09/microsoftteams-image.png)

Figure 10 : Pipeline de Sécurité de GPT-4 [11, 30] 

###  Des gouvernements et des institutions inquiets 

Plusieurs pays ont pris la décision d’interdire ChatGPT (cf Figure 11) [22]. La plupart d’entre eux (Russie, Corée du nord, Iran…) l’ont fait pour des raisons de protection de données, mais aussi de contrôle de l’information ou de concurrence avec les USA. Certains pays occidentaux l’ont interdit puis réautorisé, comme l’Italie, et d’autres envisagent l’interdiction. Pour ces derniers, les raisons évoquées sont la cybersécurité, la protection des mineurs, et la conformité avec les lois en vigueur (ex : RGPD). 

![Cartographie pays ayant interdit ChatGPT](https://www.quantmetry.com/wp-content/uploads/2023/09/mappemonde.png)

Figure 11 : Cartographie des pays ayant interdit ChatGPT [30] 

Parmi les institutions ayant interdit ou restreint ChatGPT (cf Figure 12), on retrouve des entreprises de la tech (Apple, Amazone, Samsung…) et des acteurs financiers (J.P.Morgan, Bank of America, Deutsche Bank…), tous inquiets pour la protection de leur données (une fuite a eu lieu chez Samsung par exemple) [23]. 

Les institutions scientifiques, comme les revues littéraires, l’interdisent pour un enjeu de confiance face au risque d’articles rédigés subrepticement par des machines. Enfin, certaines institutions s’inquiètent de la triche possible avec de tels outils. Il est intéressant de voir l’ambivalence du positionnement dans la recherche ou l’éducation car certaines institutions voient au contraire les LLMs comme une source d’opportunités et de progrès [24]. 

![Cartographie institutions ayant interdit ChatGPT ](https://www.quantmetry.com/wp-content/uploads/2023/09/institutions.png)

Figure 12 : Cartographie des institutions ayant interdit ChatGPT [30] 

###  Le régulateur Européen 

Sur ce blog, de nombreux articles ont déjà mentionné le futur EU AI Act qui régulera les intelligences artificielles [25]. On rajoutera cependant ici que ce texte de loi a été modifié suite à la fulgurante adoption de ChatGPT, nous en résumons les conséquences Figure 13. Désormais, l’Union Européenne définit le concept de GPAI (General Purpose AI – IA à but général) [2]. Il s’agit d’un système d’IA qui peut être utilisé et adapté à un large éventail d’applications pour lesquelles il n’a pas été conçu spécifiquement. Les règlementations sur les GPAIs concernent donc les LLMs ainsi que tous les autres types d’IA génératives. 

Les GPAIs sont concernés par tout un panel de restrictions, résumé ici en trois parties : 

  * Transparence documentaire et enregistrement administratif, ce qui ne devrait pas être très compliqué à implémenter. 
  * Management du risque et mise en place de protocoles d’évaluation. Ces aspects sont plus compliqués à implémenter mais faisables pour les fournisseurs de LLMs, comme l’a esquissé OpenAI avec ChatGPT [11]. 
  * Gouvernance de la donnée (RGPD et éthique) et respect des droits d’auteurs. La marche pour ses dimensions-ci est très haute pour les fournisseurs de LLMs qui sont loin de pouvoir les garantir à l’heure actuelle. 



L’Union Européenne va donc considérer les LLMs comme des IA risquées et les fournisseurs de LLMs ont encore beaucoup de travail avant d’atteindre le futur seuil de conformité. Néanmoins, certains pensent que cette future loi est par certains aspects trop peu applicables et par d’autres trop facilement contournable. 

![Conséquence EU AI Act sur LLMS](https://www.quantmetry.com/wp-content/uploads/2023/09/conformitegpai.png)

Figure 13 : Conséquence de l’EU AI Act sur les LLMS [30] 

L’évaluation de la conformité d’un modèle est un des cœurs de métiers de Quantmetry, particulièrement en rapport avec l’EU AI Act. Sur le sujet des LLMs en particulier, des chercheurs de Stanford ont publié un article de blog dans lequel ils évaluent la conformité de 10 LLMs à la future loi européenne [31]. Les résultats sont en Figure 14. Pour établir une note de conformité, les chercheurs ont extrait 12 exigences du projet de loi pour lesquels ils ont établi une rubrique de notation, puis des annotateurs ont été chargé de mener une évaluation à partir des informations publiques. L’article identifie les problèmes de droits d’auteur, de gestion de la donnée et des risques, et de l’évaluation comme les principaux manquements actuels, ce qui rejoint notre analyse ci-dessus. Les chercheurs estiment que 90% de conformité est un objectif réaliste pour les fournisseurs de LLMs (le meilleur élève est actuellement à 75% pour une moyenne à 42% sur les 10 LLMs évalués). 

![Résultat évaluation de conformité par les chercheurs de Stanford](https://www.quantmetry.com/wp-content/uploads/2023/09/stanford.png)

Figure 14 : Résultat de l’évaluation de conformité par les chercheurs de Stanford [31] 

###  Quelques conseils 

Face à tous ses risques, on ne peut que conseiller à chacun de faire attention par lui-même. Apprendre quelques techniques de prompt engineering pour avoir des prompts amenant des réponses sûres et de qualité peut être une bonne piste [26]. Il faut aussi faire attention aux fuites de données via les chatbots gratuits, par exemple sur la version gratuite de ChatGPT. Si vous êtes sensibles à la protection de l’information, la version payante ne conserve pas vos données a priori. Enfin, la Figure 15 vous donne un schéma pour utiliser avec précaution des outils comme ChatGPT. 

![](https://www.quantmetry.com/wp-content/uploads/2023/09/diagram.png)

Figure 15 : Schéma pour utiliser ChatGPT avec précaution [27] 

##  Comment auditer de tels modèles ? 

![Auditer LLM](https://www.quantmetry.com/wp-content/uploads/2023/09/audit.png)

Figure 16 : Trois approches pour auditer un LLM [28] [30] 

###  Audit organisationnel 

Il y a trois approches possibles pour auditer un LLM, résumées en Figure 16, et qui sont complémentaires [28]. On peut tout d’abord procéder à un audit organisationnel afin de vérifier que l’entreprise développant le LLM travaille de manière responsable et s’assurer, par exemple, de la conformité des processus et des systèmes de management. 

Il sera possible d’en faire chez nos clients qui ne sont pas des fournisseurs de LLMs mais souhaitent les spécialiser davantage, afin de s’assurer de leur bon emploi. 

###  Audit du modèle de fondation 

Comme évoqué précédemment, auditer le modèle de fondation est le focus actuel de la recherche scientifique. Pour un tel audit, il faudrait pouvoir explorer le jeu de donnée (inaccessible en réalité), faire des bancs de tests sur des benchmarks et datasets reconnus (mais se confronter au problème de contamination), et mettre en place des stratégies adversariales pour détecter les limites du modèle. Si on rentre plus dans le détail, il existe une multitude de tests possibles afin d’évaluer les aspects suivants du modèle [29] : 

  * **La responsabilité** – il s’agit de comprendre comment se matérialise les risques, de trouver les limites du modèle, typiquement avec des stratégies adversariales 
  * **La performance** – il s’agit d’évaluer via des datasets, des bancs de test ou des tests de Turing, la qualité du langage, les compétences et connaissances du modèle, ainsi que la véracité de ses propos (cf Figure 17 et 18). 
  * **La robustesse** – on cherche ici à évaluer la fiabilité des réponses grâce à des mesures de calibrations ou de stabilité face à des stratégies de prompt engineering 
  * **L’équité** – plusieurs méthodes existent pour chercher à identifier et quantifier les biais même sans accès au jeu de données, mais restent limitées à cause de cela. Par exemple, compter les associations de mots malheureuses (homme-survie, femme-jolie) 
  * **Frugalité** – certaines mesures d’inférence peuvent être faites pour estimer l’impact environnemental du modèle mais restent aussi limitées sans l’accès aux infrastructures des fournisseurs. 



![](https://www.quantmetry.com/wp-content/uploads/2023/09/eval1.png)

Figure 17 : Performance de GPT-4 sur Truthful QA [11] 

![](https://www.quantmetry.com/wp-content/uploads/2023/09/eval2.png)

Figure 18 : Performance de GPT-4 sur des examens humains [11] 

###  Audit du cas d’usage 

Quantmetry et Capgemini Invent travaillent aujourd’hui ensemble pour définir un cadre de travail qui permettra à nos clients d’auditer leurs systèmes d’IA basés sur des LLMs. Cet audit aura pour but premier de vérifier que l’impact du système sur l’utilisateur est contrôlé. Pour cela, des batteries de test seront effectuées pour vérifier la conformité aux régulations mais aussi aux besoins du client. Nous développons actuellement des méthodes de diagnostics sur les impacts long terme, sociaux et environnement de leur usage au sein d’une entreprise. Enfin, il s’agit de créer des systèmes pouvant évaluer les risques et les biais ainsi que les processus opérationnels, de gestion et de feedbacks. Les méthodes utilisées sont souvent inspirées, mais adaptées, de celles pour auditer le modèle de fondation. 

##  Conclusion : que peuvent faire Quantmetry et Capgemini Invent ? 

###  Vue globale des acteurs autour des LLMs 

Beaucoup d’acteurs se positionnent autour des LLMs. Il y a tout d’abord les entreprises qui fournissent et développent les LLMs et autres modèles de fondation, typiquement OpenAI, mais aussi HuggingFace, Anthropic, Meta etc. Ces entreprises évoluent souvent au sein des géants de la tech comme Microsoft ou Google car ces derniers possèdent les infrastructures pour développer de tels modèles. Ensuite, on retrouve des outils technologiques permettant d’utiliser ces modèles, comme Langchain, un cadre de travail permettant de développer des applications autour des LLMs. Enfin, on peut penser aux acteurs qui, à partir des LLMs, viennent développer une multitude de produits (Github Copilot, Einstein GPT, ou encore une fois le chatbot du GIEC Climate Q&A) [19]. 

##  Où se positionnent Capgemini Invent et Quantmetry ? 

Dans le sillage de l’enthousiasme médiatique lié à l’adoption massive de ChatGPT, saisir le plein de l’IA Generative et des LLMs en en maitrisant les risques est au cœur de l’agenda stratégique d’un nombre croissant de nos clients. Nos clients doivent avancer vite, sur un chemin complexe et risqué, et la distance directe entre la technologie et ses utilisateurs finaux rend les erreurs immédiatement visibles, avec des impacts directs sur l’engagement des utilisateurs métiers ou l’image de marque vis-à-vis des clients. 

Fort de notre expérience dans l’accompagnement de transformations majeures et de nos expertises spécifiques en intelligence artificielle, notre ambition est d’accompagner nos clients à toutes les étapes de leur réflexion, depuis la prise de conscience jusqu’au développement et au déploiement à l’échelle de cas d’usages à la valeur mesurée. Au-delà de notre rôle dans la définition de la stratégie d’ensemble et la conception et la mise en œuvre des cas d’usages, nous proposons également à nos clients de bénéficier de notre expertise sur l’IA de confiance pour les aider à comprendre, à mesurer et à mitiger les risques liés à cette technologie, en toute sécurité et conformité par rapport aux attentes du régulateur européen. 

A ce titre, nos équipes travaillent aujourd’hui à des méthodes d’audit spécifiques par catégories de cas d’usages, en nous inspirant des méthodes déployées par le milieu académique pour l’audit de modèle pour avancer dès maintenant sur des solutions concrètes. 

##  Références 

[1] [ Intelligence artificielle – LAROUSSE ](https://www.larousse.fr/encyclopedie/divers/intelligence_artificielle/187257)

[2] [ EU AI Act ](https://www.europarl.europa.eu/meetdocs/2014_2019/plmrep/COMMITTEES/CJ40/DV/2023/05-11/ConsolidatedCA_IMCOLIBE_AI_ACT_EN.pdf)

[3] [ ChatGPT ](https://openai.com/blog/chatgpt) , [ Alpaca ](https://crfm.stanford.edu/2023/03/13/alpaca.html) , [ Llama ](https://ai.facebook.com/blog/large-language-model-llama-meta-ai/) , [ Bard ](https://blog.google/technology/ai/google-bard-updates-io-2023/)

[4] [ Attention is all you need 2017 ](https://arxiv.org/abs/1706.03762)

[5] [ Bahdanau 2015 ](https://arxiv.org/pdf/1409.0473.pdf?ref=blog.floydhub.com) , [ Luong 2015 ](https://arxiv.org/abs/1508.04025)

[6] [ GPT 2018 ](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf)

[7] [ BERT 2018 ](https://arxiv.org/abs/1810.04805)

[8] [ GPT-2 2019 ](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) , [ GPT-3 2020 ](https://arxiv.org/pdf/2005.14165.pdf)

[9] [ Dall-e 1 2021 ](https://arxiv.org/abs/2102.12092) , [ Dall-e 2 2022 ](https://arxiv.org/pdf/2204.06125v1.pdf)

[10] [ InstructGPT 2022 ](https://arxiv.org/abs/2203.02155)

[11] [ GPT-4 2023 ](https://arxiv.org/pdf/2303.08774.pdf)

[12] [ Time to reach 100M ](https://businessday.ng/technology/article/chatgpt-is-fastest-app-to-hit-100m-users-in-history/)

[13] [ Number of ChatGPT users 2023 ](https://explodingtopics.com/blog/chatgpt-users)

[14] [ A Bibliometric Review of Large Language Models Research from 2017 to 2023 ](https://arxiv.org/pdf/2304.02020.pdf)

[15] [ Conference Good in Tech ChatGPT ](https://www.goodintech.org/preview/EventDetails.html?id=31)

[16] [ Yann LeCun ](https://www.zdnet.fr/actualites/chatgpt-n-a-n-a-rien-de-revolutionnaire-selon-yann-lecun-39953050.htm) , [ Yuval Noah Harari ](https://www.paudal.com/2023/04/23/yuval-noah-harari-i-dont-know-if-humans-can-survive-artificial-intelligence/) , [ Bill Gates ](https://www.lesechos.fr/tech-medias/hightech/pour-bill-gates-chatgpt-est-la-plus-grande-revolution-depuis-les-annees-1980-1918130) , [ Geoffrey Hinton ](https://www.lemonde.fr/pixels/article/2023/05/02/geoffrey-hinton-pionnier-de-l-ia-quitte-google-et-dit-regretter-son-invention_6171773_4408996.html) , [ IA aussi dangereuse que pandémie ](https://www.lemonde.fr/economie/article/2023/05/30/l-intelligence-artificielle-serait-aussi-dangereuse-que-les-pandemies-ou-la-guerre-nucleaire-selon-des-leaders-du-secteur_6175471_3234.html) , [ Code Red ](https://www.nytimes.com/2022/12/21/technology/ai-chatgpt-google-search.html) , [ Fracture numérique ](https://www.lemonde.fr/idees/article/2023/04/21/intelligence-artificielle-chatgpt-aggrave-considerablement-la-fracture-numerique_6170482_3232.html)

[17] [ OpenAI : Planning for AGI ](https://openai.com/blog/planning-for-agi-and-beyond)

[18] [ Azure OpenAI Service ](https://azure.microsoft.com/en-us/blog/chatgpt-is-now-available-in-azure-openai-service/)

[19] [ Climate Q&A ](https://huggingface.co/spaces/Ekimetrics/climate-question-answering)

[20] [ Auto-GPT ](https://www.blogdumoderateur.com/auto-gpt-definition-acces-alternatives-exemples/)

[21] [ Ethical and social risks of harm from Language Models ](https://arxiv.org/abs/2112.04359) , [ Assessing Language Model Deployment with Risk Cards ](https://arxiv.org/abs/2303.18190) , [ Droit d’auteurs et IA ](https://www.adagp.fr/fr/actualites/ia-et-droit-dauteur-ladagp-en-appelle-une-regulation-sur-trois-points)

[22] [ Le grand continent ](https://legrandcontinent.eu/fr/2023/04/05/qui-interdit-chatgpt/) , [ Le Monde: l’Italie lève l’interdiction ](https://www.lemonde.fr/pixels/article/2023/04/29/chatgpt-l-italie-autorise-de-nouveau-le-programme-d-intelligence-artificielle_6171513_4408996.html)

[23] [ 8 entreprises avertissent leurs employés ](https://www.msn.com/en-us/money/companies/8-companies-warning-their-employees-to-stay-away-from-chatgpt/ss-AA1bEcqg) , [ Les banques inquiètes pour leurs données ](https://www.forbes.com/sites/brianbushard/2023/02/24/workers-chatgpt-use-restricted-at-more-banks-including-goldman-citigroup/) , [ Companies against ChatGPT ](https://fortune.com/2023/05/19/chatgpt-banned-workplace-apple-goldman-risk-privacy/)

[24] [ ICML interdit ChatGPT ](https://intelligence-artificielle.developpez.com/actu/340092/L-une-des-conferences-les-plus-prestigieuses-au-monde-sur-l-IA-bannit-l-utilisation-de-chatGPT-et-tous-les-outils-de-langages-IA-dans-la-redaction-d-articles-universitaires/) , [ Science Po interdit ChatGPT ](https://www.francetvinfo.fr/internet/intelligence-artificielle-sciencespo-paris-interdit-l-utilisation-de-chatgpt-a-ses-etudiants_5625743.html) , [ Stack overflow interdit ChatGPT ](https://www.zdnet.fr/actualites/stack-overflow-interdit-les-reponses-du-chatbot-chatgpt-d-openai-39950914.htm) , [ Universités et Recherche vs ChatGPT ](https://www.lunion.fr/id452699/article/2023-02-03/universites-recherche-la-resistance-anti-chatgpt-grandit)

[25] [ Quant Blog – Comprendre AI act et l’IA de confiance ](https://www.quantmetry.com/blog/ia-confiance-decennie/)

[26] [ Prompt Engineering ](https://www.hellowork.com/fr-fr/medias/ia-chatgpt-prompt-ingenieur-metier.html)

[27] [ Schéma Is it safe to use chatgpt ](https://www.linkedin.com/posts/conner-cowling_is-it-safe-to-use-chatgpt-for-your-task-activity-7027306263155793920-XI82/?originalSubdomain=md)

[28] [ Auditing large language models: a three-layered approach ](https://arxiv.org/abs/2302.08500)

[29] [ Holistic Evaluation of Language Models ](https://crfm.stanford.edu/helm/latest/)

[30] Ressource Quantmetry 

[31] [ Stanford Compliance evaluation ](https://crfm.stanford.edu/2023/06/15/eu-ai-act.html)

[ ![NLP](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-nlp.svg) ](https://www.quantmetry.com/experts/#nlp)

Les membres de l’ [ expertise NLP ](https://www.quantmetry.com/experts/#nlp) exploitent le potentiel des données textuelles à l’aide de solutions d’IA à forte valeur ajoutée grâce à la maîtrise des technologies à l’état de l’art (modèles de deep-learning « pré-entrainés » BERT, ELMo, GPT-2 ou FlauBERT). 

[ ![Reliable Ai](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-Reliable-Ai.svg) ](https://www.quantmetry.com/experts/#reliableia)

Les membres de l’ [ expertise Reliable AI ](https://www.quantmetry.com/experts/#reliableia) développent des modèles performants, fiables et maîtrisés, sur l’ensemble du cycle de vie, pour une IA de confiance. 

* * *

![Hadrien Strichard](https://www.quantmetry.com/wp-content/uploads/2023/09/hadrien.png)

[ Hadrien Strichard  ](https://www.linkedin.com/in/hadrien-strichard-19a14218b/)

Stagiaire Data Scientist chez Capgemini Invent 

Hadrien a rejoint Capgemini Invent pour son stage de césure du master « Data Science for Business » (X - HEC). Son goût pour la littérature et le langage l’a amené à vouloir faire des LLMs le centre d’intérêt principal de son stage. Plus particulièrement, il souhaite contribuer à rendre ces IAs plus éthiques et sûres. 

![Grégoire Martinon](https://www.quantmetry.com/wp-content/uploads/2023/09/gregoire.png)

[ Grégoire Martinon  ](https://www.linkedin.com/in/gregoire-martinon/)

Senior Expert IA de Confiance chez Quantmetry 

Grégoire anime l’expertise IA de confiance de Quantmetry. Il structure la veille et dirige les orientations scientifiques sur le thème IA de confiance. Il est le référent R&D de tous les projets visant à établir une méthodologie de certification des IAs. 

![Aymen Mejri](https://www.quantmetry.com/wp-content/uploads/2023/09/aymen.png)

[ Aymen Mejri  ](https://www.linkedin.com/in/aymen-m-1b10b0122/)

Data Scientist NLP chez Quantmetry 

Titulaire de deux masters en ingénierie et d'un master en science des données, j'ai décidé d'orienter ma carrière vers le domaine de l'intelligence artificielle, et plus particulièrement vers le traitement du langage naturel. Je fais partie de l'expertise NLP de Quantmetry. 

![Hao Li](https://www.quantmetry.com/wp-content/uploads/2023/09/hao-1.png)

[ Hao Li  ](http://www.linkedin.com/in/hao-li-phd/)

Manager Data Scientist chez Capgemini Invent 

Hao est Lead Data Scientist, référent sur les sujets NLP et spécifiquement sur la stratégie, l’acculturation, la méthodologie, le business dévelopment, R&D et la formation sur le thème de la Generative AI. Il anime des solutions d’innovation en confrontant la Generative AI, l’IA traditionnelle et Data. 
