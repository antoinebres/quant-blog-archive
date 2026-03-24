# la-segmentation-bayesienne-appliquee-aux-irm-cerebraux
Wayback Machine URL: https://web.archive.org/web/20250709210938/https://www.quantmetry.com/blog/la-segmentation-bayesienne-appliquee-aux-irm-cerebraux/
Archive date: 2025-07-09

Computer vision 

02/06/2022 

#  La segmentation Bayésienne appliquée aux IRM cérébraux 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fla-segmentation-bayesienne-appliquee-aux-irm-cerebraux%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=La%20segmentation%20Bay%C3%A9sienne%20appliqu%C3%A9e%20aux%20IRM%20c%C3%A9r%C3%A9braux&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fla-segmentation-bayesienne-appliquee-aux-irm-cerebraux%2F "Twitter") [ ](https://www.quantmetry.com/blog/la-segmentation-bayesienne-appliquee-aux-irm-cerebraux/ "Email") [ ](https://www.quantmetry.com/blog/la-segmentation-bayesienne-appliquee-aux-irm-cerebraux/ "Copy Link")

* * *

Auteur : [ Julien Roussel ](https://www.linkedin.com/in/julien-roussel-b626104a)

Temps de lecture : 2 minutes 

![Quantmetry.com : La segmentation Bayésienne appliquée aux IRM cérébraux](https://www.quantmetry.com/wp-content/uploads/2022/06/image-mise-en-avant-e1654085882658.jpg)

Le traitement des tumeurs cérébrales les plus agressives, appelées gliomes de haut grade, vise à prolonger la vie des patients de quelques mois tout en préservant au maximum leur qualité de vie. Il consiste en une ablation de la tumeur suivie d’une radiothérapie ciblée sur les pourtours de la zone opérée. Cette radiothérapie a des effets secondaires conséquents, dont l’atrophie cérébrale et la leucoencéphalopathie qui est une dégradation de la substance blanche résidant à l’intérieur du cerveau. A ce jour, la balance bénéfice-risque ne fait pas l’objet d’un consensus médical. 

#  EpiBrainRad, une étude d’envergure 

[ L’Institut de radioprotection et de sûreté nucléaire (IRSN) ](https://www.irsn.fr/FR/Pages/Home.aspx) mène une étude dose-réponse dans le cadre du [ projet EpiBrainRad ](https://www.irsn.fr/FR/Larecherche/Organisation/equipes/radioprotection-homme/Lepid/Pages/Lepid-EPIBRAINRAD.aspx#.Ypk1x5NByEs) qui a suivi pendant 3 ans une cohorte de 135 patients volontaires traités pour des tumeurs cérébrales à l’Hôpital de la Pitié Salpêtrière (Paris) et à l’Institut Paul Strauss (Strasbourg). Il s’agit entre autres de quantifier l’évolution de deux biomarqueurs au fil des examens espacés d’un ou deux mois : le volume cérébral et le volume affecté par la leucoencephalopathie. Le traitement automatisé des IRM cérébrales apparaît comme une nécessité pour une telle étude, car le traitement humain des IRM 2D requiert typiquement à la fois une forte disponibilité des médecins (radiologues, neurologues…) et la construction d’une représentation 3D des réponses apparaît comme une tâche impossible pour un humain. 

#  Une solution IA basée sur des techniques Bayésiennes 

Quantmetry a apporté son expertise computer vision à l’IRSN en proposant des algorithmes de segmentation non supervisés 3D basés sur des techniques Bayésiennes. Plus précisément, nous avons conçu un data pipeline estimant l’évolution temporelle des deux biomarqueurs pour chaque patient, associée à des intervalles de confiance. La solution développée inclut une extraction du cerveau et la segmentation des différents tissus constituant ce dernier à l’aide d’un modèle de champ de Markov caché. Ce modèle se base sur les IRM de type FLAIR, auxquelles on adjoint les IRM de type T1 pour gagner en contraste dans le cas où elles sont disponibles. 

##### 

#####  👉👉 [ En savoir plus sur le développement du data pipeline ](https://medium.com/@julien.oroussel/a-bayesian-approach-to-unsupervised-segmentation-a922efcb7b10) 👈👈 

#####  [ ![](https://www.quantmetry.com/wp-content/uploads/2022/06/logo-expertise-computer-vision-300x177.png) ](https://www.quantmetry.com/experts/#computervision)

Les membres de l’expertise Computer Vision adressent des thématiques couvrant l’ensemble du cycle de valorisation des images : de la constitution du jeu de données à l’implémentation du modèle sur des dispositifs embarqués. 

#### 

![](https://www.quantmetry.com/wp-content/uploads/2022/06/separation.png)

####  ![](https://www.quantmetry.com/wp-content/uploads/2022/06/photo-r-jro-150x150.png)

[ **Julien ROUSSEL** ](https://www.linkedin.com/in/julien-roussel-b626104a)   
Data Scientist chez Quantmetry 

Docteur en mathématiques appliquées à la physique statistiques, j’aborde aujourd’hui les problématiques de data science sous les angles scientifiques, techniques et métiers. J’ai un faible pour les modèles Bayésiens, les séries temporelles et l’IA de confiance ! 
