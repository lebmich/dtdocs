---
draft: 'false'
id: shortcuts
title: raccourcis
weight: 120
---

Une grande partie des fonctionnalités de darktable est accessible via des raccourcis utilisant le clavier ou des combinaisons clavier/souris. Ces raccourcis sont configurables par l'utilisateur via l'onglet raccourcis des préférences. 

De nombreuses actions de raccourci importantes sont fournies avec des combinaisons de touches par défaut, mais la plupart doivent être configurées manuellement par l'utilisateur. N'importe quelle touche peut être utilisée pour un raccourci clavier et peut être combinée avec les touches de modification Shift, Control ou Alt (ou toute combinaison de celles-ci)

Lorsque vous ouvrez l'onglet _raccourcis_, une liste hiérarchique de toutes les actions pouvant être appliquées avec un raccourci clavier s'affiche initialement. Au sommet de cette hiérarchie se trouve une courte liste de _catégories_ clés qui sont définies ci-dessous.

# ajouter ou modifier un raccourci

Pour ajouter ou modifier un raccourci, accédez d'abord à l'action que vous souhaitez modifier et double-cliquez dessus. Vous serez invité à appuyer sur la nouvelle combinaison de touches à associer à l'action sélectionnée. 

Si un conflit est détecté, vous aurez la possibilité de conserver le raccourci existant ou de le remplacer. Selon le contexte, il est possible d'utiliser le même raccourci clavier pour plusieurs actions. Par exemple, la même combinaison de touches peut être utilisée pour une action dans la vue table lumineuse et une autre dans la vue chambre noire.

# supprimer un raccourci

Pour supprimer un raccourci clavier, cliquez une fois sur l'action que vous souhaitez supprimer et appuyez sur la touche de retour arrière.

# rechercher

Un champ de recherche s'affiche en bas de l'onglet des _raccourcis_. Entrez le texte que vous souhaitez rechercher et appuyez sur Entrée ou cliquez sur le bouton de _rechercher_. Appuyez plusieurs fois sur Entrée ou _rechercher_ pour parcourir toutes les actions correspondantes.

# afficher les raccourcis actuellement attribués

Appuyez sur la touche H dans n'importe quelle vue de darktable pour afficher une liste de tous les raccourcis affectés à la vue actuelle.

# importer, exporter, réinitialiser

Vous pouvez importer vos mappages de raccourcis ou les exporter vers un fichier.

Appuyez sur _défaut_ pour réinitialiser tous les raccourcis à leur état par défaut. _Faites attention lorsque vous utilisez cette option, car il n'est pas possible de restaurer un état antérieur à moins que vous n'ayez d'abord exporté les raccourcis existants vers un fichier ou fait une sauvegarde de votre répertoire de configuration._

# catégories de raccourci

Keyboard shortcuts are categorized within a hierarchical list so that they can easily be found. The following sections summarize these categories and list some common options.

## global

Shortcut actions in this section are applicable to all darktable views.

If you have created any user-defined styles, these will be available as actions within a "styles" sub-section.

## vues

A single section is provided for each darktable view. Shortcut actions are only applicable to the selected view.

## modules de traitement

Shortcut actions for the [processing modules](../module-reference/processing-modules/_index.md) in the darktable view. A section is provided for each processing module.

In addition, a separate "blending" section allows you to control the [masking and blending](../darkroom/masking-and-blending/_index.md) options for the last module that you interacted with.

### common shortcuts

Every processing module provides the following shortcut actions by default

enable module
: Enable or disable the module, regardless of whether it is currently visible

show module
: Expand or collapse the module. If the module is not currently displayed on the screen, darktable will switch to an appropriate module group (if applicable) before displaying it

focus module
: Cause the module to receive or lose focus.

reset module parameters
: Reset the module to its default state

afficher le menu des préréglages
: Afficher le menu des préréglages du module

presets
: An expandable category which lists all currently-defined presets for the module as possible actions.  It will not be shown if there are no presets.

For comboboxes and sliders, some standard shortcut actions are provided, as described in the following sections.

In addition, other module-specific controls will be provided with their own shortcut actions.

### curseurs

All sliders in processing modules can be adjusted via keyboard shortcuts, regardless of whether the module is currently shown or enabled. The following shortcut actions are provided as standard for each slider:

increase/decrease
: Separate shortcuts which allow you to increase or decrease the slider's value by a single step.

dynamic
: A single shortcut that can be used in combination with the mouse scroll wheel to increase and decrease slider values.

edit
: A shortcut to bring up the slider's edit dialog within which you may key a value directly or modify the slider with the mouse.

reset
: Reset the slider to its default value.

In addition, you can modify the precision of the increase/decrease operations with a keyboard shortcut (_shortcuts > views > darkroom > change keyboard shortcut slider precision_), choosing between fine, normal and coarse. See [module controls](../darkroom/processing-modules/module-controls.md) for more details.

When performing increase/decrease and dynamic operations on sliders a toast message will appear at the top of the image to indicate the current value of the slider.

### boîtes déroulantes

As with sliders, all comboboxes in processing modules can be adjusted via keyboard shortcuts. The following shortcut actions are provided as standard for each combobox:

next/previous
: Separate shortcuts which allow you to change to the next or previous entry in the combobox

dynamic
: A single shortcut that can be used in combination with the mouse scroll wheel to change to the next/previous entry in the combobox

If the end of a combobox list is reached, these shortcuts will cycle back to the beginning of the list. Similarly, if the beginning of the list is reached the shortcuts will cycle to the end. 

### multiple module instances

It is possible to create [multiple instances](../darkroom/processing-modules/multiple-instances.md) of many processing modules. In this scenario it is not always obvious which instance should be controlled by keyboard shortcut operations.

See [preferences > miscellaneous](./miscellaneous.md) for some additional settings that allow you to control how keyboard shortcuts are handled when multiple instances of a processing module are present.

## modules techniques

Shortcut actions for the [utility modules](../module-reference/utility-modules/_index.md). These are modules that are not used for image processing and may appear on any panel. Some utility modules can be used in multiple views.

As with processing modules, some shortcut actions are provided by default for each module:

show module
: Expand or collapse the module.

reset module parameters
: Reset the module to its default state.

afficher le menu des préréglages
: Afficher le menu des préréglages du module.

Some of the above actions may not be available for all utility modules.
