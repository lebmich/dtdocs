---
author: people
draft: 'false'
id: source-image
title: 'image source'
weight: 30
---

In the “source image” tab you set your source image, which requires two elements. The first element is an input file in Lab Portable Float Map format (extension `.pfm`). The source file represents the largely unmodified data as the camera sees it. Information about how to take photos of a color reference card and produce a `.pfm` output file are described below. The second element is a chart file that contains a formal description of the underlying color reference card's layout (extension `.cht`). Chart files are usually shipped with your color reference card or can be downloaded from the internet.

![source](./source-image/darktable-chart-source.png#w75)

Dans la réalité la photo prise de la carte de références couleurs montrera quelques distorsions de perspective par rapport à la disposition définie dans le fichier graphique. Pour cette raison la disposition est affichée en tant que grille superposée à l'image et peut être modifiée.

Vous pouvez déplacer les coins de la grille en utilisant la souris pour obtenir le meilleur alignement de la grille et de l'image.

A rectangular frame is displayed for each patch and defines the area from which `darktable-chart` will sample the required input data. You may need to modify the size of these rectangles so that the sampling area is big enough but does not overlap with neighboring patches. Use the “size” slider in the upper right part of the GUI. Higher values lead to smaller sizes.
