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

- Vous souhaiterez peut-être gérer indépendamment les bruits de luminance et de chrominance. Cela peut être accompli en générant deux instances du module de réduction du bruit que vous avez choisi et en utilisant la première uniquement pour luminance (en sélectionnant le [mode de fusion](../masking-and-blending/blend-modes.md) clarté) et la seconde uniquement pour la chrominance (en sélectionnant le mode de fusion couleur).


---

**Remarque :** Chaque instance augmente la charge de travail de votre pipeline graphique. Générer trop d'instances, en particulier celles des modules les plus exigeants, entraînera un ralentissement notable.

---

# gérer les instances multiples

_Cliquez_ sur le _menu instances multiples_ dans [l'entête du module](./module-header.md) pour afficher un menu déroulant, avec les options suivantes.

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
