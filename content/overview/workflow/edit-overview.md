---
title: "développer une image: aperçu d'un flux de travail"
id: workflow-overview
draft: false
weight: 20
author: "people"
---

Cette section va vous guider à travers les bases du développement d'une image dans la vue [chambre noire](../../darkroom/_index.md), où un arsenal de modules est à votre disposition pour vous aider à atteindre vos objectifs créatifs.

Pour commencer, ouvrez une image dans la chambre noire en double-cliquant sur la miniature d'une image dans la vue [table lumineuse](../../lighttable/_index.md).

Chaque modification que vous apportez à l'image de la chambre noire est transformée en un élément de l'historique. L'historique est stocké dans une base de données et dans un fichier lié XMP pour cette image. Toutes les modifications sont sauvegardées automatiquement lorsque vous changez d'images ou passez d'une vue de darktable à une autre. Vous pouvez quitter le mode chambre noire en toute sécurité ou quitter darktable à tout moment et revenir plus tard pour continuer votre travail. Pour cette raison, darktable n'a pas besoin d'un bouton «enregistrer» et il n'en a pas.

En mode chambre noire, sur le panneau de gauche se trouve l'[historique](../../module-reference/utility-modules/darkroom/history-stack.md). Il liste les modifications que vous avez apportées, en commençant par le bas -- chaque modification ajoute un nouvel élément au sommet de l'historique.  À des fins de comparaison entre les modifications, vous pouvez sélectionner, en cliquant dessus, un point quelconque de cet historique pour voir à quoi ressemblait l'image en ce point. L'historique peut être compressé pour supprimer les points intermédiaires redondants dans votre développement. Lorsque vous êtes satisfait de ce que vous avez fait, compressez simplement l'historique. Notez que lors de la compression de l'historique, sont définitivement supprimées toutes les modifications situées au-dessus de l'entrée d'historique sélectionnée.

Un grand nombre de [modules de traitement](../../module-reference/processing-modules/_index.md) sont fournis avec darktable. Ils sont organisés en [groupes de modules](../../darkroom/interacting-with-modules/search-and-group.md). Ces groupes sont accessibles via les boutons-bascule en haut du panneau de droite, juste en dessous de l'[histogramme](../../module-reference/utility-modules/shared/histogram.md).

# choisir un flux de travail

When processing an image, we apply a sequence of modules, known as the [pixelpipe](../../darkroom/processing-modules-and-pixelpipe/_index.md). 

![edit-overview](./edit-overview/edit-overview.png#w100)

1. The _scene-referred_ modules are intended to process pixel values that are proportional to the amount of light collected by the camera at the scene. The dynamic range of an image in the scene-referred section of the pixelpipe is often larger than that of the display medium. 

2. At some point in the pixelpipe, these pixel values are compressed by a tone mapping module into a smaller dynamic range more suitable for display on a monitor or hardcopy print.

3. The remaining modules operate in this non-linear _display-referred_ section of the pixelpipe to produce the final output image.

There are two standard workflows offered in darktable (these can be changed in [preferences > processing > auto-apply pixel workflow defaults](../../preferences-settings/processing.md)):
* [_scene-referred workflow_](edit-scene-referred.md): Here the emphasis is on doing as much processing as possible in the scene-referred part of the pipeline, and performing dynamic range compression to display-referred space as late as possible. This is the preferred workflow for darktable. It uses the [_filmic rgb_](../../module-reference/processing-modules/filmic-rgb.md) module to perform the tone mapping compression.
* [_display-referred workflow_](edit-display-referred.md): This is the legacy workflow and is still the default setting when darktable is first installed. It performs the tone mapping compression much earlier in the pixelpipe, and many of the modules therefore operate in display-referred space. It uses the [_base curve_](../../module-reference/processing-modules/base-curve.md) module to perform the tone mapping compression.

A third option is to set the workflow presets option to _none_. In this case, the scene-referred workflow module order will be used by default but none of the above modules will be automatically applied. It is up to the user to arrange for appropriate tone mapping and reorder the modules where required.

---

**Note:** when changing the preferences between scene-referred and display-referred workflow, the new setting will only apply for newly imported images. If you have already imported an image using a different workflow setting, go to the [_history stack_](../../module-reference/utility-modules/darkroom/history-stack.md) module in the darkroom view, select "original image", and click "compress history stack". This will discard any previous edits and reset the workflow for that image.

---
