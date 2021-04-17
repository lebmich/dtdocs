---
applicable-version: 3.2.1
id: filmstrip
tags: ~
title: pellicule
view: 'lighttable, darkroom, tethering, map, print'
---

La pellicule peut être utilisée pour basculer rapidement entre les images dans n'importe quelle vue de darktable. Les images dont les miniatures sont affichées dans la pellicules sont les mêmes que celles qui sont affichées dans la vue table lumineuse et sont définies par la collection actuellement sélectionnée.

![pellicule](./filmstrip/filmstrip.png)

La pellicule peut être activée et désactivée à l'aide du raccourci Ctrl+F. La hauteur du panneau de la pellicule peut être modifiée en cliquant et en faisant glisser sa bordure supérieure.

Parcourez rapidement les miniatures de la pellicule en faisant défiler avec la souris. Dans la chambre noire, vous pouvez changer de photo en cours de traitement en cliquant sur une autre miniature de la pellicule.

Dans la vue chambre noire, la miniature de l'image en cours de traitement est sélectionnée et mise en surbrillance. Survolez la pellicule avec la souris pour sélectionner une autre miniature (afin d'agir sur l'image correspondante à l'aide d'un raccourci clavier) sans changer l'image en cours de traitement.

Si vous souhaitez sélectionner plusieurs miniatures dans la pellicule, utilisez Alt+clic pour sélectionner la première, puis Ctrl+clic pour ajouter ou supprimer de la sélection d'autres miniatures ou Maj+clic pour sélectionner une plage de miniatures.

Les raccourcis suivants sont disponibles pour sélectionner des miniatures dans la pellicule ou pour effectuer des actions sur les images correspondant aux miniatures sélectionnées :

```
Ctrl+A         select all images in the filmstrip
Ctrl+Shift+A   deselect all images
Ctrl+I         invert the current selection

F1 – F5        toggle color label (red, yellow, green, blue, purple)
0 – 5          set/change image rating
R              reject image
Ctrl+D         duplicate image
Ctrl+C         copy the full history stack
Ctrl+V         paste all of the copied history stack
Alt+Ctrl+C     selectively copy the history stack
Alt+Ctrl+V     selectively paste from the copied history stack
```

Voir la documentation de l'[historique](../lighttable/history-stack.md) pour plus de détails sur les fonctionnalités du copier-coller.
