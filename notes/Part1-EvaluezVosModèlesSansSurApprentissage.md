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