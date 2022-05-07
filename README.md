# <div align = center> Projet-Optimisation-1A </div>
Ce projet constitue le premier projet d'optimisation de la première année de Mines de Paris. Il consiste en reconstitué, dans un référentiel absolu, la trajectoire d'un robot dont on connait les déplacements relatifs.

## Quelques remarques sur les différentes questions abordées.

### QUESTION 4 : 
&ensp; $\longrightarrow$ Dans un premier temps, nous avons voulu ajouter les contraintes sur thêta dans le problème d'optimisation. Cependant, il semble plus judicieux, en plus de la contrainte (que l'on laisse par sécurité) de s'assurer artificiellement que thêta reste bien entre -pi et pi.  
Pour réaliser cela, nous voudrions utiliser la fonction remainder de numpy. Cependant cette fonction n'est pas compatible avec du code <code>casadi</code>. Nous programmons donc à côté une fonction qui permet de réaliser ceci : échec ! Cela ne fonctionne pas. En effet les matrices sous casadi présente un type particulier : pour les plus générales, le type est <code>MX</code>. Chaque matrice est associé à une représentation symbolique et non à des valeurs numériques. L'ordinateur enregistre les opérations que l'on applique et non pas les valeurs prises par les coefficients de la matrice. Ceci empêche la fonction <code>remainder</code> de fonctionner parce qu'elle implique un test booléen qui ne peut être réalisé sur une matrice qui ne contient pas de valeures numériques.  
&ensp; Pour ne pas perdre tout le travail effectué avec le module casadi, nous optimisons notre fonction sans les contraintes selon $\theta$, ce qui n'est pas absurde parce que pour minimiser notre fonction, les $\theta$ vont "naturellement" s'accorder sur un intervalle de longueur $2\pi$.  

&ensp; Nous réalisons cependant cette question avec le module Pytorch aussi pour avoir plus de flexibilité et avancer dans notre projet.

