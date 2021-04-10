---
draft: 'false'
id: mutiple-instances
title: 'instances multiples'
weight: 20
---

De nombreux modules de darktable peuvent être appliqués plus d'une fois dans le pipeline graphique. Chaque instance d'un module se comporte de manière indépendante, obtenant son entrée du module qui le précède dans le pipeline graphique et délivrant sa sortie au module qui le suit.

Comme pour l'instance de base d'un module, toutes les instances peuvent être déplacées indépendamment dans le pipeline graphique soit en maintenant Ctrl+Maj pendant le glisser-déposer, soit en choisissant _monter_ ou _descendre_ dans le menu déroulant _multiples instances_.

Les instances peuvent être renommées en faisant un Ctrl+clic sur l'entête du module.

# cas typiques d’utilisation

Il y a de nombreuses occasions où il est judicieux de faire appliquer un module plus d'une fois dans le pipeline graphique. Voici quelques cas d'utilisation typiques.

 - Le module [_exposition_](../../../module-reference/processing-modules/exposure.md) peut être utilisé en combinaison avec des [masques](../masking-and-blending/masks/_index.md) pour éclaircir ou assombrir certaines parties d'une image. Une instance distincte peut être créée pour modifier chaque partie de l'image.

- You may wish to handle luma and chroma noise independently. This can be accomplished by generating two instances of your chosen denoising module and using the first one only on luma (by selecting [blend mode](../masking-and-blending/blend-modes.md) “lightness”) and the second one only on chroma (by selecting blend mode “color”).


---

**Note:** Each instance also adds to the workload of your pixelpipe. Generating too many instances – especially of the more demanding modules – will cause noticeable slow-down.

---

# gérer les instances multiples

Click on the _multiple instance menu_ in the [module header](./module-header.md) to display a drop-down menu, with the following options. Right-click on the menu icon to create a new instance directly (same action as clicking on the "new instance" option of the menu).

nouvelle instance
: Créez une nouvelle instance du module actuel avec tous ses paramètres réinitialisés par défaut. Un numéro est ajouté au nom de base du module pour la distinguer.

cloner l'instance
: Crée une nouvelle instance du module actuel avec tous ses paramètres hérités de son parent. Un numéro est ajouté au nom de base du module pour la distinguer.

monter/descendre
: monter ou descendre l'instance dans le pipeline graphique

supprimer
: Supprimer l'instance actuelle. Cette option n'est pas disponible si une seule instance est présente.

renommer
: Renommez l'instance actuelle. Voir la section [historique](../../../module-reference/utility-modules/lighttable/history-stack.md) pour plus de détails sur l'impact du nom de l'instance sur la copie et le collage des historiques.
