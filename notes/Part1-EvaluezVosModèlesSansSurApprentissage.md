## 1. Comprenez ce qui fait un bon modèle d'apprentissage
### Généralisation
Un **bon modèle de machine learning**, c’est un modèle qui généralise.

### Sur-apprentissage et compromis biais-variance
Un modèle qui **sur-apprend** est un modèle qui est **trop complexe** par rapport à la réalité qu’il essaie de représenter. Nous avons tendance à préférer des modèles simples ; c’est le principe du **rasoir d’Ockham** (ou Occam), selon lequel les hypothèses suffisantes les plus simples sont les plus vraisemblables. Par ailleurs, coller de trop près aux données est une mauvaise idée car elles sont inévitablement bruitées :
- Par des erreurs de mesure (les appareils que nous utilisons pour mesurer les variables qui représentent nos données peuvent faire des erreurs techniques) ;
- Par des erreurs d’étiquetage (l’erreur est humaine, et il se peut que certaines des étiquettes ne soient pas les bonnes) ;
- Parce que nous n’avons pas mesuré les variables les plus pertinentes, soit parce qu'on ne les connaît pas, soit parce qu'elles sont très compliquées à mesurer

"**Sous-apprentissage**" - Les modèles **trop simples**

**Compromis biais-variance** 
![Compromis biais-variance](https://github.com/ywsyws/OpenClassRooms_EvaluezLesPerformancesdUnModeleDeML/blob/master/image/compromisBiaisVariance.png)

:information_source: La complexité d’un modèle peut être mesurée de différentes façons. L’une d’entre elles est le nombre de paramètres utilisés par ce modèle : plus il y a de paramètres, plus le modèle est complexe.  


### Les problèmes mal posés
En fait, toutes nos difficultés viennent du fait que les problèmes d'apprentissage sont des problèmes **mal posés** (*ill-posed* en anglais). Nous n'arrivons pas à les formuler de sorte à avoir une solution unique. Les données que nous observons ne sont pas suffisantes pour modéliser correctement le phénomène que nous cherchons à comprendre pour répondre à notre problématique, et nous devons rajouter des hypothèses (par exemple, que la frontière séparant les points bleus des points orange est un cercle) pour finalement arriver à un bon modèle. Ces hypothèses forment ce que l’on appelle le **biais d’induction** (*inductive* bias en anglais).  

### Ressources informatiques
Trade off between time and accuracy of a model.  

### En résumé
- En apprentissage supervisé, le but est de produire des modèles qui **généralisent**, c’est-à-dire qui sont capables de faire de bonnes prédictions sur de nouvelles données.  
- De bonnes performances sur le jeu d’entraînement **ne garantissent pas** que le modèle sera capable de généraliser !  
- On cherche à développer un modèle qui soit suffisamment complexe pour bien capturer la nature des données (et éviter ainsi le **sous-apprentissage**), mais suffisamment simple pour éviter le sur-apprentissage.  
- Attention aux **contraintes de temps de calcul** et aux **ressources en mémoire** !  
<br>

## 2. Mettez en place un cadre de validation croisée
### Jeux d’entraînement et de test

### Validation croisée
:information_source:
Dans scikit-learn, la méthode **<ins>model_selection</ins>**.KFold permet de créer les folds d’une validation croisée.  

### Stratification
:information_source:
Dans scikit-learn, la méthode **<ins>model_selection.StratifiedKFold</ins>** permet de créer les folds d’une validation croisée stratifiée.  

:information_source:
Au moment de l'*apprentissage* (et non pas de l'évaluation), on peut compenser le déséquilibre entre les classes dans le jeu d'entraînement en utilisant une méthode de ré-échantillonnage : on tire  aléatoirement parmi la classe majoritaire autant d'observations que dans la classe minoritaire, ce qui crée un jeu équilibré, opération que l'on répète de nombreuses fois. On crée ainsi plusieurs modèles, que l'on peut ensuite combiner en moyennant leurs scores ou en choisissant l'étiquette la plus fréquemment prédite.

### Leave-one-out
(k-1)n/k
n est la taille du jeu complet
**Leave-one-out**: on ne laisse de côté qu’un seul exemple pour chaque jeu d’entraînement

Ça a l’air bien ! Sauf que…

- on augmente fortement le temps de calcul. Imaginez ça sur une base de données de 100 000 images ! Il faudrait entraîner 100 000 modèles sur 99 999 images chacun.  
- on forme ainsi des jeux d’entraînements très similaires entre eux, et des jeux de test très différents les uns des autres. On va avoir quasiment le même modèle sur chaque fold, et la qualité de ses prédictions risque de beaucoup varier. Il sera difficile de tirer des conclusions.

:information_source: 
En pratique, on choisit le plus souvent k=5 ou k=10.  
<br>

## 3. TP – Sélectionnez le nombre de voisins dans un kNN
### Sélection de modèle
Pour faire ça correctement, il faut séparer les données en trois parties : un **jeu d’entraînement**, un **jeu de validation** et un **jeu de test**. Le jeu d’entraînement sert à entraîner divers modèles. Le jeu de validation sert à *sélectionner* un modèle : on choisit celui qui a la meilleure performance sur ce jeu. Enfin, le jeu de test sert à *estimer la performance* en généralisation du modèle.  

Alternativement, au lieu de créer un jeu d’entraînement et un jeu de validation, on peut séparer les données uniquement en deux parties : un jeu d’entraînement et un jeu de test. On fera ensuite une *validation croisée* sur le jeu d’entraînement. Cela nous permet de choisir un modèle (celui qui a la meilleure performance), que l’on va ensuite entraîner sur la totalité du jeu d’entraînement, puis tester sur le jeu de test. C’est cette performance finale qui est la meilleure approximation de la performance que le modèle pourra atteindre sur de nouvelles données.  

![Train Valid Test](https://github.com/ywsyws/OpenClassRooms_EvaluezLesPerformancesdUnModeleDeML/blob/master/image/trainValidTest.png)

:information_source: On peut appliquer le même raisonnement qui nous a conduit à faire une validation croisée plutôt qu’une simple séparation entraînement / test et répéter cette procédure au sein d’une autre validation croisée. On parle alors de **validation croisées imbriquées** (« *nested cross-validation* » en anglais). Le défaut de ce type d’approche, en pratique, et qu’elle peut sélectionner des modèles différents sur chaque fold…  


### Recherche sur grille (grid search)

### Sélectionnez le nombre de voisins dans un kNN sur un jeu de données

### Les données

### Sélection de modèle

### Alternatives à la recherche exhaustive

### Résumé