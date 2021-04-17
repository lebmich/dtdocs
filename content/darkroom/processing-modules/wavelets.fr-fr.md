---
draft: 'false'
id: wavelets
title: ondelettes
weight: 55
---

Les ondelettes sont une technique utilisée dans le traitement d'image pour séparer (ou décomposer) une image en un certain nombre de couches distinctes, chacune contenant un niveau de détail différent. Après avoir décomposé une image de cette manière, un module peut limiter son traitement à une ou plusieurs de ces couches de détail, puis reconstituer les couches à la fin pour former son image de sortie. Cela nous permet d'avoir une précision chirurgicale sur les caractéristiques de l'image que nous souhaitons impacter lorsque nous travaillons avec un module. 

Certaines des opérations que darktable peut effectuer de cette manière sont :

- réduction du bruit (dans les modules [_réduction bruit (profil)_](../../module-reference/processing-modules/denoise-profiled.md), [_réduction du bruit raw_](../../module-reference/processing-modules/raw-denoise.md) et [_égaliseur de contraste_](../../module-reference/processing-modules/contrast-equalizer.md)) 

- ajustement du contraste (dans le module [_égaliseur de contraste_](../../module-reference/processing-modules/contrast-equalizer.md))

- flou ou suppression de détails indésirables (dans le module [_retouche_](../../module-reference/processing-modules/retouch.md))


# théorie

Une ondelette est une fonction mathématique qui commence à zéro, oscille de haut en bas, puis revient à zéro. Le diagramme suivant montre quelques ondelettes simples de différentes tailles.

![présentation-ondelettes](./wavelets/wavelets-overview.png#w50) 

Ces fonctions d'ondelettes sont utilisées pour parcourir l'image en utilisant une opération mathématique appelée _convolution_. Ceci sélectionne les détails de l'image qui sont à une échelle similaire à la taille d'une ondelette donnée et crée un certain nombre de couches de détails correspondant chacune à une échelle d'ondelettes différente.

Vous trouverez ci-dessous un exemple où des couches de détails ont été extraites de l'image ci-dessus. Dans ce cas, les images ont été produites en utilisant le module [_retouche_](../../module-reference/processing-modules/retouch.md), en divisant l'image en huit couches différentes et en utilisant les contrôles du module pour visualiser le détails présents à chacune de ces échelles d'ondelettes :

![ondelettes-retouche-gui](./wavelets/clean-retouch.png#w33)

The bars in the _wavelet decompose_ section indicate the layers that have been extracted at different wavelet scales. The darkest rectangle at the left represents the entire image (before decomposition) and the gray boxes represent each of the decomposed layers. Clicking on the staircase icon below the bar graph enables the layer visualisation overlay so that you can see what the currently selected layer looks like. 

Jetons un coup d'œil à certaines des couches générées pour l'image ci-dessus.

À l'échelle n°2, l'image ne contient que des détails très fins, dont les sourcils, les cils et les pores de la peau du mannequin. Elle n'inclut pas les détails plus grossiers de l'image, car ces détails ont été extraits vers d'autres couches :

![couche-ondelettes-échelle-2](./wavelets/wavelets-layer-scale-2.png#w50)

Aux échelles n°5 et n°6, nous commençons à voir des détails de plus en plus grands :

![couches-ondelettes-échelle-5](./wavelets/wavelets-layer-scale-5.png#w50) 

![couche-ondelettes-échelle-6](./wavelets/wavelets-layer-scale-6.png#w50)

À l'échelle n°8, nous ne voyons que des détails de très haut niveau du modèle tels que la forme générale du nez, des yeux et de la joue :

![couche-ondelettes-échelle-8](./wavelets/wavelets-layer-scale-8.png#w50)

# pourquoi utiliser des ondelettes ?

Supposons, dans l'exemple ci-dessus, que nous voulions lisser une partie des taches sur la peau du modèle, sans rien perdre de la texture de peau sous-jacente. Avec la décomposition en ondelettes ceci est une opération triviale -- nous pouvons simplement utiliser le module retouche pour appliquer un flou gaussien uniquement au(x) couche(s) "tachée(s)", laissant toutes les autres couches non modifiées. Une fois l'ajustement terminé, le module retouche recombine simplement la ou les couches modifiées avec les couches non modifiées pour produire l'image finale.

La séquence d'images ci-dessous montre (1) L'image originale ; (2) La couche (échelle 5) que l'on souhaite flouter ; et (3) L'image finale après que la couche à l'échelle 5 a été floutée et que les différentes couches ont été recombinées :

![ondelettes-original](./wavelets/wavelets-original.png#w50) 

![couches-ondelettes-échelle-5](./wavelets/wavelets-layer-scale-5.png#w50) 

![ondelettes-flou-couche](./wavelets/wavelets-blur-layered.png#w50)

Comme vous pouvez le voir, les taches cutanées à grande échelle ont été supprimées, mais les détails à plus petite échelle ont été conservés.

# interagir avec les échelles d'ondelettes

Les modules de traitement vous permettent de modifier leur fonctionnement à l'aide d'échelles d'ondelettes en utilisant deux méthodes.

## la décomposition en ondelettes

Comme indiqué ci-dessus, le module _retouche_ vous permet de choisir le nombre de niveaux de détails dans lesquels diviser votre image. Il décompose l'image en couches séparées et vous permet d'effectuer des opérations de manière sélective sur chaque couche ou sur l'image dans son ensemble :

![ondelettes-retouche-gui](./wavelets/clean-retouch.png#w33)

Voir la documentation du module [_retouche_](../../../module-reference/processing-modules/retouch.md) pour plus de détails.

## les contrôles de spline

The [_denoise (profiled)_](../../module-reference/processing-modules/denoise-profiled.md), [_raw denoise_](../../module-reference/processing-modules/raw-denoise.md) and [_contrast equalizer_](../../module-reference/processing-modules/contrast-equalizer.md) modules allow their effects to be applied more or less to different wavelet scales using _splines_.

![spline](./wavelets/clean-spline.png#w33)

Here, each node in the graph represents a different level of detail in the image, from coarse detail on the left to fine detail on the right. You can raise or lower each of these nodes with your mouse to increase or decrease the module's effect, respectively, on that wavelet scale. 

To modify the curve, click slightly above or below the line near to a node and drag up or down. You can change the width of your modification by scrolling with your mouse wheel, which increases or reduces the size of the circle displayed under your mouse pointer. A small circle indicates that the effect of dragging the curve up or down will be isolated mostly to the node being adjusted. A larger circle indicates that the effect will be more broad and will increasingly impact adjacent nodes. When you hover your mouse over the graph, shaded areas indicate the parts of the spline that will be impacted when you attempt to modify the curve.
