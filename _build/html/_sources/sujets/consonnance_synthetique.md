# Consonance synthétique

Création d'une interface graphique permettant d'ajuster l'intervalle séparant deux ondes sonores.
La manipulation s'effectue à la souris et les sons sont ajustés en temps réels, de même que la représentation graphique de l'onde.

![interface](./interface_consonance.png)


## Modules utilisés
- [tkinter](https://docs.python.org/3/library/tkinter.html) (_after_, _mouse event_)
- [pygame](https://www.pygame.org/docs/)

## Paramètres d'entrée
- sélection de la fréquence fondamentale $f_1$ de l'onde de référence
- sélection de la fréquence $f_2$ de la seconde onde (temps réel)

## Fonctionnalités
- représentation graphique du rapport des fréquences dans l'intervalle $[1, 2]$, en échelle logarithmique
- représentation graphique des deux ondes sinusoïdales en échelle de couleur dans des cadres rectangulaires
- production simultanée des sons associés aux deux ondes représentées
- contrôle de la seconde onde par compression/étirement de la représentation graphique de la forme d'onde au moyen de la souris
- ajustement graphique et sonore en temps réel de la fréquence de la seconde onde modifié
