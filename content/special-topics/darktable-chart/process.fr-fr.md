---
author: people
draft: 'false'
id: process
title: processus
weight: 50
---

If all of the required settings in the “source image” and “reference values” tabs are ready you can move on to the “process” tab.

![processus](./process/darktable-chart-process.png#w75)

First, you need to tell `darktable-chart` which of the patches represents the gray ramp. In the screenshot displayed above, the gray ramp is positioned in the lower part of the color reference chart, denoted as “GS00...GS23”.

The “number of final patches” input defines how many editable color patches the resulting style will use within the [_color look up table_](../../module-reference/processing-modules/color-look-up-table.md) module.

Click the “process” button to start the calculation.

La qualité du résultat (en termes de delta E moyen et de delta E maximum) est affichée sous le bouton. Ces données montrent à quel point le style résultant appliqué à l'image source sera en mesure de correspondre aux valeurs de référence -- plus ils sont faibles, mieux c'est.

Once you are happy with the result you can click on “export” to save the generated style.

Vous fournissez un nom de style et une description du style sous lesquels le style apparaîtra ultérieurement dans darktable. `darktable-chart` sauvegarde le style dans un fichier ayant l'extension .dtstyle qui peut être importé dans darktable et peut être partagé avec d'autres. Voir [styles](../../module-reference/utility-modules/lighttable/styles.md).

The “export raw data as csv” button allows you to save the extracted raw data as a CSV file for debugging purposes or later use. `darktable-chart` offers a command line option to produce a style with the desired number of final patches from a supplied CSV file (see [`darktable-chart`](../program-invocation/darktable-chart.md)).
