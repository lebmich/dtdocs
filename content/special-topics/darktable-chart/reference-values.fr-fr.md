---
author: people
draft: 'false'
id: reference-values
title: 'valeurs de références'
weight: 40
---

The “reference values” tab determines the target values to which the source image must to be modified by the resulting style. You can either supply reference values in the form of measured data of your color reference card (mode “cie/it8 file”), or you can supply a photographic image (mode “color chart image”) much in the same way as described above. This second image must also be supplied in Lab Portable Float Map format. There is no need to supply the chart file again as `darktable-chart` takes the same one as defined under “source image”. You only need to again align the layout grid and the image and potentially adjust the “size” slider.

Dans un cas typique d'utilisation la seconde image sera basée sur le fichier JPEG produit par le boîtier. De cette façon vous pouvez créer dans darktable un style qui simule le processus du boîtier.

Dans le cadre inférieur de sortie texte vous voyez les valeurs couleur extraites des données disponibles pour chaque pastille couleur. La première colonne donne le nom de la pastille, les deuxième et troisième colonnes montrent respectivement les valeurs couleur de l'image source en format RVB et Lab. La quatrième colonne contient la valeur Lab provenant de la référence (ou du fichier graphique si aucune image référence n'a été donnée). Finalement, les cinquième et sixième colonnes indiquent à quel point les valeurs source et référence dévient en termes de valeurs delta E.
