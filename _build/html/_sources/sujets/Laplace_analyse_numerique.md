# Problème de Laplace

Ce projet s'inscrit dans l'analyse des résultats d'expérience de mesures  électriques à l'échelle nanométrique (_conductive AFM_) menées au laboratoire GEMaC. 

![](cAFM_configuration_small.png)

La géométrie de la mesure impose une distribution inhomogène du champ électrique induit par la différence de potentiel appliquée entre les électrodes. De ce fait, la relation entre la résistance mesurée et la résistivité intrinsèque du matériau dépend non seulement des dimensions de l'échantillon mais également du détail de la configuration de mesure qui détermine la distribution de champ électrique.

Le but de ce projet est de déterminer numériquement la distribution de champ électrique dans un matériau isolant en présence d'électrodes métalliques imposant localement un potentiel. 
Le champ électrique dans le matériau est calculé à partir de la distribution de potentiel vérifiant l'équation de Laplace.

![](Potential_distribution.png)





1. position du problème et traitement analytique des cas accessibles
2. différences finies : analyse numérique du schéma (convergence, stabilité, robustesse, complexité)
3. différences finies : implémentation du schéma numérique 2D et 3D
4. éléments finis : implémentation par sfepy comme boite noire 



	Projet de 4 personnes 

	Coordination avec projet "dipôle magnétique"

Représentation graphique du champ magnétique créé par une spire, un solénoïde, ...


## Modules utilisés
- [matplotlib](https://matplotlib.org/)
- [numpy](https://numpy.org/)

## Paramètres d'entrée
- pas du maillage 3D (décomposition élémentaire de la distribution)
- pas du maillage de représentation (origine des vecteurs affichés)
- distribution de charge (élément de courant et position)

## Fonctionnalités
- Calcul direct du champ magnétique créé par une spire idéale dans tout l'espace
- Calcul par superposition du champ créé partout dans l'espace par un solénoïde fini
- Représentations graphiques du champ magnétique
- Vérification sur des distributions pour lesquelles une solution analytique simple existe pour le solénoïde
- Extractions de coupe (distributions 3D) et de profils (distributions 2D) de champ et de potentiel
- Simulation du champ créé par une association de solénoïdes 
	+ [Bobines de Helmholtz](https://fr.wikipedia.org/wiki/Bobines_de_Helmholtz)
	+ [Cage de Helmhlotz](https://uccubecats.github.io/HelmholtzCage.html)
	+ [Bobine de Maxwell](https://fr.wikipedia.org/wiki/Bobines_de_Maxwell)
