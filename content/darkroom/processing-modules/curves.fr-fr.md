---
draft: 'false'
id: curves
title: courbes
weight: 50
---

Trois modules de traitement ([courbe de base](../../module-reference/processing-modules/base-curve.md), [courbes des tonalités](../../module-reference/processing-modules/tone-curve.md) et [courbe rvb](../../module-reference/processing-modules/rgb-curve.md)) utilisent des courbes pour contrôler les tons de l'image. Ces modules ont des caractéristiques communes qui méritent une discussion séparée.

![courbe](./curves/curve.png#w33)

# nœuds

Dans leur état par défaut, les courbes sont des lignes droites, définies par deux nœuds d'ancrage en haut à droite et en bas à gauche du graphique de la courbe. Vous pouvez déplacer les nœuds pour modifier la courbe ou générer de nouveaux nœuds en cliquant sur la courbe. Ctrl+clic pour générer un nouveau nœud à l'emplacement x du pointeur de la souris et l'emplacement y correspondant de la courbe actuelle - cela ajoute un nœud sans risque de modifier accidentellement la courbe. Jusqu'à 20 nœuds peuvent être définis par courbe. Pour supprimer un nœud, cliquez dessus et faites-le glisser hors de la zone des widgets.

# contrôles de la courbe

Les commandes suivantes sont communes à deux ou plusieurs des modules de traitement ci-dessus et sont donc décrites séparément ici. Veuillez consulter la documentation de chaque module pour une discussion sur les commandes supplémentaires spécifiques au module.

méthode d'interpolation
: _modules courbe des tonalités et courbe rvb uniquement_

: L'interpolation est le processus par lequel une courbe continue est dérivée de quelques nœuds. Comme ce processus n'est jamais parfait, plusieurs méthodes sont proposées qui peuvent atténuer certains des problèmes que vous pourriez rencontrer.

: - Arguably, the most visually pleasing method is the “cubic spline” -- since it gives smooth curves, the contrast in the image is better enhanced. However, this method is very sensitive to the nodes' position, and can produce cusps and oscillations when the nodes are too close to each other, or when there are too many of them. This method works best when there are only 4 to 5 nodes, evenly spaced.

: - The “centripetal spline” method is designed specifically to avoid cusps and oscillations, but as a drawback it will follow the nodes more loosely. It is very robust, no matter the number of nodes and their spacing, but will produce a more faded and dull contrast.

: - The “monotonic spline” method is designed specifically to give a monotonic interpolation, meaning that there will be none of the oscillations the cubic spline may produce. This method is most suitable when you are trying to build an analytical function from a node interpolation (for example: exponential, logarithm, power, etc.). Such functions are provided as presets. It is a good trade-off between the two aforementioned methods.

préserver couleur
: Si une courbe de tonalité non linéaire est appliquée à chacun des canaux rvb individuellement, alors la quantité de réglage de ton appliqué à chaque canal de couleur peut être différente, ce qui peut provoquer des changements de teinte. Par conséquent, la zone de liste déroulante _préserver couleur_ fournit différentes méthodes de calcul du "niveau de luminance" d'un pixel. La quantité de réglage de la tonalité est calculée en fonction de cette valeur de luminance, puis ce même réglage est appliqué aux trois canaux rvb. Différents estimateurs de luminance peuvent affecter le contraste dans différentes parties de l'image, en fonction des caractéristiques spécifiques de cette image. L'utilisateur peut donc choisir un estimateur particulier qui fournit les meilleurs résultats pour l'image donnée. Certaines de ces méthodes sont décrites en détail dans le contrôle **préserver couleur** du module [_filmique rvb_](../../module-reference/processing-modules/filmic-rgb.md) . Les options suivantes sont disponibles :

: - _non_
: - _luminance Y_
: - _max rvb_
: - _moyenne rvb_
: - _somme rvb_
: - _norme rvb_
: - _puissance de base_

échelle du graphe
: _modules courbe des tonalités et courbe de base uniquement_

: La mise à l'échelle vous permet de déformer l'affichage du graphique afin que certaines propriétés graphiques apparaissent pour vous aider à dessiner des courbes plus utiles. Notez que l'option de mise à l'échelle n'affecte que l'affichage de la courbe, pas les paramètres réels stockés par le module.

: By default, a “linear” scale is used (defined by a scale factor of 0). This scale uses evenly spaced abscissa and ordinates axes.

: Une échelle logarithmique compressera les valeurs élevées et dilatera les valeurs basses, à la fois sur l'axe des abscisses et sur l'axe des ordonnées. Ainsi les nœuds, dans les basses lumières, obtiendront plus d'espace sur le graphique et pourront être contrôlés plus facilement.

: Augmentez le curseur `échelle du graphe` pour définir la base du logarithme utilisé pour la mise à l'échelle des axes. Cela vous permet de contrôler la quantité de compression/dilatation opérée par la mise à l'échelle. Si vous dessinez des fonctions purement exponentielles ou logarithmiques à partir de la fonction identité, la définition de cette valeur définit la base de ces fonctions.
