---
draft: 'false'
id: module-controls
title: 'les contrôles du module'
weight: 40
---

# curseurs

Les curseurs proposent cinq méthodes d'interaction différentes, en fonction du niveau de contrôle dont vous avez besoin.

clic gauche
: Cliquez n'importe où dans la zone du curseur pour définir la valeur. Vous pouvez également cliquer et faire glisser pour le modifier. Vous n'avez pas à viser le triangle ou même la ligne -- vous pouvez cliquer n'importe où sur toute la hauteur du curseur, y compris le label.

molette de la souris
: Survolez le curseur avec votre souris, puis utilisez la molette de votre souris pour ajuster la valeur.

keyboard arrow keys
: When the slider has focus you can hover over the slider with your mouse, then use your keyboard's arrow keys (←/↓ and →/↑) to adjust the value. In order to give focus to the widget without changing the current value you can right-click, then right-click again.

clic-droit
: Lorsque votre souris est sur un curseur, un clic droit active sous le curseur une fenêtre contextuelle multifonctionnelle pour un contrôle précis avec votre souris ou une entrée numérique à l'aide du clavier.

: ![bauhaus](./module-controls/bauhaus.png#w33)

: Une ligne courbe partant du marqueur triangulaire se déplace avec votre souris. Plus le pointeur de votre souris est proche du marqueur triangulaire, plus le contrôle que vous avez sur la valeur est grossier ; plus vous êtes éloigné du marqueur triangulaire, plus votre contrôle est fin. Cliquez avec le bouton gauche de la souris pour accepter la nouvelle valeur et masquer la fenêtre contextuelle.

: Alternatively you can type in a new value using your keyboard and commit by hitting the enter key. You may even supply the new value in the form of an arithmetic expression which darktable will calculate for you – the previous value is referenced as “x”.

double-clic
: Vous pouvez double-cliquer sur un curseur ou son label pour réinitialiser sa valeur par défaut.

De plus, la précision des réglages de la molette de la souris et des touches flèches peut être modifiée :

 - maintenez la touche Maj enfoncée tout en ajustant pour _augmenter_ la taille du pas d'un facteur 10. 

 - maintenez la touche Ctrl enfoncée tout en ajustant pour _diminuer_ la taille du pas d'un facteur 10.


Ces deux multiplicateurs peuvent être modifiés dans le fichier `$HOME/.config/darktablerc` :

```
darkroom/ui/scale_rough_step_multiplier=10.0
darkroom/ui/scale_precise_step_multiplier=0.1
```

# boîtes déroulantes

Click on a combobox to open a list of available options which you can click to select. Occasionally the selection list will open close to the bottom or top of the screen meaning that only some of the items are visible -- simply scroll with your mouse wheel to bring up the full list. Alternatively, you can also use the mouse wheel and keyboard arrow keys to select an option, or start typing to filter the combobox entries.

# pipettes à couleurs

Un certain nombre de modules permettent de définir des paramètres à l'aide de pipettes à couleurs (identifiés par l'icône ![pipette à couleurs](./module-controls/color-picker.png#icon)). Celles-ci utilisent une interface standard et la plupart peuvent fonctionner en mode point ou en mode zone. Le mode point peut être activé en cliquant sur l'icône de la pipette à couleur. Ctrl+clic sur l'icône pour activer le mode zone.

# raccourcis clavier

Les paramètres du module peuvent également être modifiés avec des raccourcis clavier. Voir [préférences > raccourcis](../../preferences-settings/shortcuts.md) pour plus d'informations.
