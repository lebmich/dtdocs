---
title: curves
id: curves
weight: 50
draft: false
---

Trois modules de traitement d'images([courbe de base](../../module-reference/processing-modules/base-curve.md), [tone curve](../../module-reference/processing-modules/tone-curve.md) et [courbe rvb](../../module-reference/processing-modules/rgb-curve.md)) utilisent des courbes pour contrôler les tonalités d'une image. Ces modules ont des caractéristiques communes qui méritent une discussion séparée.

![courbe](./curves/curve.png#w33)

# nœuds

Dans leur état par défaut, les courbes sont des lignes droites, définies par deux nœuds d'ancrage en haut à droite et en bas à gauche du graphique de courbes. Vous pouvez déplacer les nœuds pour modifier la courbe ou générer de nouveaux nœuds en cliquant sur la courbe. Ctrl + clic pour générer un nouveau nœud à l'emplacement x du pointeur de la souris et l'emplacement y correspondant de la courbe actuelle - cela ajoute un nœud sans risque de modifier accidentellement la courbe. Jusqu'à 20 nœuds peuvent être définis par courbe. Pour supprimer un nœud, cliquez dessus et faites-le glisser hors de la zone du widget.

# contrôles de la courbe

Les contrôles suivants sont communs à deux ou plusieurs des modules de traitement d'image ci-dessus et sont donc décrits séparément ici. Veuillez consulter la documentation d'un module particulier pour une discussion sur les contrôles supplémentaires spécifiques au module.

méthode d'interpolation 
: _modules courbe des tonalités et courbe rvb seulement_

: L'interpolation est le processus qui dérive une courbe continue à partir de quelques nœuds. Comme ce processus n'est jamais parfait, plusieurs méthodes sont proposées qui peuvent atténuer certains des problèmes que vous pourriez rencontrer.

: - On peut soutenir que la méthode la plus agréable visuellement est la «spline cubique» - puisqu'elle donne des courbes lisses, le contraste de l'image est mieux amélioré. Cependant, cette méthode est très sensible à la position des nœuds, et peut produire des cuspides et des oscillations lorsque les nœuds sont trop proches les uns des autres, ou lorsqu'il y en a trop. Cette méthode fonctionne mieux lorsqu'il n'y a que 4 à 5 nœuds, régulièrement espacés.

: - La méthode “spline centripète” est conçue spécifiquement pour éviter les cuspides et les oscillations, mais comme inconvénient, elle suivra les nœuds de manière plus lâche. Elle est très robuste, quel que soit le nombre de nœuds et leur espacement, mais produira un contraste plus fané et terne.

: - La méthode «spline monotone» est conçue spécifiquement pour donner une interpolation monotone, ce qui signifie qu'il n'y aura aucune des oscillations que la spline cubique peut produire. Cette méthode est la plus appropriée lorsque vous essayez de créer une fonction analytique à partir d'une interpolation de nœuds (par exemple: exponentielle, logarithme, puissance, etc.). Ces fonctions sont fournies sous forme de préréglages. C'est un bon compromis entre les deux méthodes susmentionnées.

préservation des couleurs
: Si une courbe des tonalités non linéaire est appliquée à chacun des canaux RVB individuellement, alors la quantité de réglage de ton appliqué à chaque canal de couleur peut être différente, ce qui peut provoquer des changements de teinte. Par conséquent, la zone de liste déroulante _préserver couleur_ fournit différentes méthodes de calcul du "niveau de luminance" d'un pixel. La quantité de réglage de la tonalité est calculée en fonction de cette valeur de luminance, puis ce même réglage est appliqué aux trois canaux RVB. Différents estimateurs de luminance peuvent affecter le contraste dans différentes parties de l'image, en fonction des caractéristiques spécifiques de cette image. L'utilisateur peut donc choisir un estimateur particulier qui fournit les meilleurs résultats pour l'image donnée. Certaines de ces méthodes sont décrites en détails dans la commande **préserver la chrominance** du module [_filmique RVB_] (../../ module-reference / processing-modules / filmic-rgb.md). Les options suivantes sont disponibles :

: - _non_
: - _luminance Y_
: - _max RVB_
: - _moyenne RVB_
: - _somme RVB_
: - _norme RGB_
: - _puissance de base_

échelle graphique 
: _modules courbe des tonalités et courbe de base seulement_

: L'échelle vous permet de déformer l'affichage du graphique afin que certaines propriétés graphiques émergent pour vous aider à dessiner des courbes plus utiles. Notez que l'option de mise à l'échelle affecte uniquement l'affichage de la courbe, pas les paramètres réels stockés par le module.

: Par défaut, une échelle «linéaire» est utilisée (définie par un facteur d'échelle à 0). Cette échelle utilise des abscisses et des ordonnées régulièrement espacées.

: Une échelle logarithmique compressera les valeurs élevées et dilatera les valeurs basses, à la fois sur les axes des abcisses et des ordonnées. Ainsi les nœuds dans les basses lumières seront plus espacés sur le graphique et pourront être contrôlés plus clairement.

: Augmentez le curseur «échelle graphique» pour définir la base du logarithme utilisé pour mettre les axes à l'échelle. Cela vous permet de contrôler la quantité de compression / dilatation opérée par l'échelle. Si vous dessinez des fonctions purement exponentielles ou logarithmiques à partir de la fonction identité, cette valeur définit la base de ces fonctions.
