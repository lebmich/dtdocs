---
draft: 'false'
id: module-header
title: "entête d'un module"
weight: 10
---

En haut de chaque module de traitement se trouve l'_entête du module_. 

![entête d'un module](./module-header/module-header.png#w33)

Cliquez sur le nom du module pour développer le module et afficher les paramètres qui contrôlent son fonctionnement.

Par défaut, darktable n'autorisera qu'un seul module de traitement à être déplié à la fois -- si vous cliquez sur l'entête d'un autre module, le module précédemment ouvert sera replié. Si vous souhaitez déplier plus d'un module, vous pouvez le faire en Shift+cliquant sur les entêtes d'autres modules et tous ceux qui ont été précédemment dépliés le resteront. Ce comportement peut être inversé via un paramètre dans les [préférences > chambre noire](../../../preferences-settings/darkroom.md).

---

**Remarque :** Déplier un module ne provoque pas son activation. Voir ci-dessous pour savoir comment activer les modules.

---

L'entête d'un module contient les contrôles suivants dans l'ordre de gauche à droite :

bouton marche/arrêt
: Cliquer pour activer ou désactiver le module. Certains modules sont essentiels pour le traitement d'image et ne peuvent pas être désactivés (bien que leurs paramètres puissent être modifiés). De même, certains modules ne sont pas applicables à certains types d'images et ne peuvent pas être activés.

: Ctrl+clic sur le bouton marche/arrêt pour donner ou non le focus au module. Donner le focus est généralement utilisé pour activer les superpositions qu'un module place sur l'image pour contrôler ses fonctionnalités. Par exemple, le module [_recadrer et pivoter_](../../../module-reference/processing-modules/crop-rotate.md) affiche les lignes de recadrage et la grille du guide de recadrage uniquement s'il a le focus. 

nom du module
: Le nom du module se compose d'une description de l'opération qu'il réalise (ce nom ne peut pas être modifié) suivi du nom de l'instance du module (qui peut être modifié). Par défaut, la première instance d'un module a un nom d'instance vide. Si vous créez des instances supplémentaires, le nom de chaque nouvelle instance sera indexé avec un entier unique. Par exemple, la deuxième instance créée du module exposition sera automatiquement nommée _exposition 1_.

: Ctrl+clic sur le nom d'un module pour modifier manuellement son nom d'instance. 

mask toggle
: This icon will appear in the header whenever a [mask](../masking-and-blending/masks/_index.md) is active on a module. Hover over the icon to see what type of mask is enabled. Click it to display the current mask as a yellow overlay over a black-and-white version of the image. Solid yellow indicates an opacity of 100%; a fully visible gray background image (without yellow overlay) indicates an opacity of 0%. This toggle button can be disabled in [preferences > darkroom > show mask indicator in module headers](../../preferences-settings/darkroom.md#modules). 

multiple instance menu
: This drop-down menu allows you to create, delete, move and rename module instances. Right-click on this icon to directly create a new instance of the module. See the [multiple instances](./multiple-instances.md) section for more information.

réinitialiser les paramètres
: Cliquez pour réinitialiser tous les paramètres du module à leurs valeurs par défaut. Ctrl+clic pour réappliquer les [préréglages](./presets.md) automatiques pour le module -- si aucun préréglage automatique n'est applicable pour ce module, Ctrl+clic réinitialisera simplement les valeurs par défaut (comme pour un clic).

menu des préréglages
: Ce menu vous permet d'appliquer, de créer et de modifier les préréglages du module. Voir la section [préréglages](./presets.md) pour plus d'informations.

The visibility of the three icons to the right of the module name can be controlled through [preferences > darkroom > show right-side buttons in darkroom module headers](../../preferences-settings/darkroom.md#modules).
