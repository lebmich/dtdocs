---
author: people
draft: 'false'
id: making-input-images
title: "Faire une image d'entrée pour darktable-chart"
weight: 60
---

To start with, you need a suitable photo of your color reference card in RAW+JPEG format. It goes beyond the scope of this manual to explain the details of how to take this photo, but in a nutshell you need to make the shot on a sunny day around midday with the light source (the sun) shining at an angle onto the card. You need to avoid any glare in the image. The neutral white color patch in the gray ramp (G00) should end up at the L value specified in the description of your card. Often this is L=92 and requires you to overexpose the shot by about 1/3 EV. Ideally you will make several shots with slightly different exposures and later select the right one in darktable. Make sure that the chart fills up most of the frame. Use a lens with a “normal” focal length (e.g. 50mm equivalent) and stop down a bit to avoid vignetting.

You then open the raw file in darktable and disable most modules, especially [_base curve_](../../module-reference/processing-modules/base-curve.md). Select the standard input matrix in the [_input color profile module_](../../module-reference/processing-modules/input-color-profile.md) and disable gamut clipping. Select “camera white balance” in the [_white balance_](../../module-reference/processing-modules/white-balance.md) module.

Il y a une situation particulière quand votre boîtier applique automatiquement au fichier JPEG résultant des corrections d'objectif, à savoir des corrections de vignettage. Dans ce cas vous devez activer le module [_correction des objectifs_](../../module-reference/processing-modules/lens-correction.md) de darktable afin que le traitement RAW corresponde au JPEG. Cependant, étant donné que la correction de vignetage de darktable peut ne pas correspondre exactement à la correction intégrée à l'appareil photo, il est préférable de désactiver cette correction si possible.

Pour sortir votre image allez dans le module [exporter](../../module-reference/utility-modules/shared/export.md) de la table lumineuse.

You will need to select “Lab” as the output color profile. This color space is not visible in the combobox by default. You first need to enable it by setting `allow_lab_output` to `TRUE` in `$HOME/.config/darktable/darktablerc`. Alternatively, you can start darktable with:

```
darktable --conf allow_lab_output=true
```

Then select “PFM (float)” as the output format and press “export” to generate the source image file.

You can prodce the corresponding reference (target) image from the JPEG in a similar way. This time you will need to disable all modules and export with the “Lab” output color profile in “PFM (float)” format.
