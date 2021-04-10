---
author: people
draft: 'false'
id: unbounded-colors
title: 'couleurs non bornées'
weight: 60
---

Screens and most image file formats can only encode RGB intensities confined within a certain range. For example, images encoded on 8 bits can only contain values from 0 to 255, images on 10 bits from 0 to 1023, and so on… Graphic standards postulate that the maximum of that range, no matter its actual value, will always represent the maximum brightness that the display medium is able to render, usually between 100 and 160 Cd/m² (or nits) depending on the actual standard. We generally call this maximum "100 % display-referred". The minimum of the range, encoded 0 no matter the bit-depth used, becomes then "0 % display-referred". 100 % encodes pure white, 0 % encodes pure black.

Il s'agit d'une limitation pour les applications de traitement d'image, car cela signifie que tout pixel situé en dehors de cette plage sera tronqué à la limite la plus proche, entraînant une perte non récupérable de données (couleurs et/ou textures).

Pendant très longtemps, les logiciels de traitement d'image ont également été assujettis à cette limitation pour des raisons techniques. Certains le sont encore, mais maintenant c'est par choix lors de leur conception. En conséquence, ils tronqueront les intensités RVB à 100 % relatif à l'affichage lors des opérations sur l'image.

darktable utilise l'arithmétique à virgule flottante dans son pipeline graphique. Il peut donc gérer en interne n'importe quelle valeur RVB, même si elle ne se trouve pas dans la plage relative à l'affichage, pourvu qu'elle soit strictement positive. Ce n'est qu'à la toute fin du pipeline graphique, avant que l'image ne soit enregistrée dans un fichier ou envoyée à l'affichage, que les valeurs RVB sont tronquées si cela est nécessaire.

Pixels that can take values outside of the display range are said to have “unbounded colors”. One could choose to clamp (i.e. confine) those values to the allowed range at every processing step or choose to carry on with them, and clamp them only at the last step in the pipeline. However, it has been found that processing is less prone to artifacts if the unbounded colors are not clamped but treated just like any other color data.

À la fin du pipeline graphique, des modules comme [_filmique_](../../module-reference/processing-modules/filmic-rgb.md) peuvent vous aider à mapper les valeurs RVB dans la plage relative à l'affichage tout en maximisant la préservation des données, évitant ainsi l'écrêtage dur qui n'est généralement pas agréable visuellement.

Cependant, à tout moment dans le pipeline graphique, vous devez vous assurer de ne pas créer de valeurs RVB négatives. Les intensités RVB codent les émissions lumineuses et la lumière négative n'existe pas. Les modules qui, pour traiter les pixels, reposent sur une interprétation physique de la lumière échoueront s'ils rencontrent une émission de lumière non physique. Par prévention, les valeurs RVB négatives sont toujours écrêtées chaque fois qu'elles peuvent faire échouer les algorithmes, mais le résultat visuel peut sembler dégradé. Des valeurs négatives peuvent être produites en abusant du _correction du niveau de noir_ dans le module [_exposition_](../../module-reference/processing-modules/exposure.md) ou d'_offset_ dans le module [_balance couleur_](../../module-reference/processing-modules/color-balance.md). Des précautions doivent donc être prises lors de l'utilisation de ces modules.
