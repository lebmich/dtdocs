---
draft: 'false'
id: overview
title: présentation
weight: 10
---

Par défaut, un module reçoit son entrée du module le précédant dans le pipeline graphique, il effectue ses calculs et envoie sa sortie au module le suivant dans le pipeline graphique. 

Les données de sortie d'un module peuvent optionnellement être retraitée (combinées) avec son entrée avant que le résultat soit passé au module suivant. Ce traitement supplémentaire est appelé _fusion_. Entrée et sortie peuvent être traitées avec différents algorithmes, appelés opérateurs de fusion ou [modes de fusion](./blend-modes.md).

Chaque mode de fusion est en outre contrôlé par un paramètre appelé _opacité_ qui peut avoir une valeur comprise entre 0% et 100% et qui définit la manière dont les images d’entrée et de sortie contribuent au résultat final. Typiquement, une valeur d’opacité égale à 0% produit une image identique à l’image d’entrée -- le module n’a pas d’effet. Une valeur d’opacité égale à 100% délivre le maximum de l’effet du module pour le mode de fusion choisi.

L'opacité peut être la même pour chaque pixel de l'image (en combinant simplement un mode de fusion avec le curseur d'opacité unique) -- dans ce cas, la fusion agit de manière uniforme sur toute l'image. Les valeurs d'opacité peuvent également varier en fonction des propriétés ou de l'emplacement de chaque pixel. Cette modification locale de l'opacité est appelée un _masque_. Les masques fournissent à l'utilisateur un contrôle précis sur les parties d'une image qui sont affectées par un module et dans quelle mesure. Vous pouvez choisir d'activer un [masque dessiné](./masks/drawn.md), un [masque paramétrique](./masks/parametric.md) ou une [combinaison des deux](./masks/drawn-and-parametric.md). 

La fonctionnalité de fusion et de masquage est contrôlée via un groupe d'icônes situé au bas de chaque module où elle est applicable. 

![options de masquage et de fusion](./overview/mask-blend-options.png#w33)

Ces icônes activent les options de masquage et de fusion suivantes, de gauche à droite :

désactivé
: La sortie du module est transmise au module suivant dans le pipeline graphique sans retraitement supplémentaire. Aucun autre contrôle n'est affiché. 

uniformly
: Input and output images are reprocessed to the same extent for all pixels with the extent of the blending controlled by a single opacity slider. Additional controls to choose the blend mode and opacity are displayed. The default blend mode is “normal” with an opacity of 100%.

[masque dessiné](./masks/drawn.md)
: Le retraitement a lieu avec le mode de fusion et l'opacité choisis en fonction de l'emplacement des pixels dans un masque dessiné. Des contrôles supplémentaires s'affichent pour vous permettre de dessiner un masque en utilisant une ou plusieurs formes. Si aucun élément de masque n'est dessiné, tous les pixels ont la même opacité, celle que définit le curseur d'opacité.

[masque paramétrique](./masks/parametric.md)
: Le retraitement a lieu en fonction des propriétés de chacun des pixels en utilisant le mode de fusion et l'opacité choisis. Des contrôles supplémentaires s'affichent pour vous permettre d'ajuster l'opacité, pixel par pixel, en fonction des valeurs des pixels.

[drawn & parametric mask](./masks/drawn-and-parametric.md)
: Reprocessing takes place with the chosen blend mode and opacity based on a combination of a drawn mask parametric mask.

[raster mask](./masks/raster.md)
: Reprocessing takes place with the chosen blend mode and opacity based on a mask that was generated within a different module

blending options
: Choose which color space to use when calculating the blending mask, and specify whether or not to allow a mask to be generated based on the module's output channels (normally a parametric mask is generated based on the input channels coming into the module). The following options are available:
: - _reset to default blend colorspace_: Use the default color space for the module to specify the parametric mask.
: - _Lab_: Use the Lab color space (where available) when specifying the parametric mask.
: - _RGB (display)_: Use the display-referred RGB/HSL color space to specify the parametric mask.
: - _RGB (scene)_: Use the scene-referred RGB/J<sub>z</sub>C<sub>z</sub>h<sub>z</sub> color space to specify the parametric mask.
: - _show output channels_: Show the [parametric mask](./masks/parametric.md) output channel controls, so that the parametric mask can be defined in terms of the module's output channels.

---

**Note:** Not all of these blend options are available for every module.

---

