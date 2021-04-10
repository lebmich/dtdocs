---
draft: 'false'
id: the-pixelpipe-and-module-order
title: "le pipeline graphique & l'ordre des modules"
weight: 20
---

La séquence ordonnée des [modules de traitement](../../module-reference/processing-modules/_index.md) opérant sur un fichier d'entrée pour générer une image de sortie est connue sous le nom de _pipeline graphique_. 

L'ordre des modules du pipeline graphique est représenté graphiquement par l'ordre dans lequel les modules sont présentés dans l'interface utilisateur -- le pipeline graphique commence par une image raw en bas de la liste, et applique les modules de traitement un par un, en empilant une à une les couches de traitement de bas en haut, jusqu'à ce qu'il atteigne le haut de la liste, où il produit l'image entièrement traitée.

---

**Remarque :** L'ordre d'exécution des modules de traitement correspond exactement à l'ordre dans lequel les modules apparaissent dans l'interface utilisateur de darktable. **La modification de cet ordre dans l'interface utilisateur changera la façon dont votre image sera traitée.**

---

# ordre des modules et flux de travail

L'ordre dans lequel les modules sont exécutés dans le pipeline graphique a été soigneusement choisi pour donner la meilleure qualité de sortie. Dans les versions précédentes de darktable, il n'était pas possible de modifier l'ordre des modules. Cependant, il existe un certain nombre de cas d'utilisation très spécifiques où le déplacement de certains modules dans le pipeline graphique est conseillé.

L'une des principales raisons de changer l'ordre des modules est venue avec la version 3.0 de darktable, qui a introduit la nouvelle méthode de travail _relative à la scène_. La version 3.2 a officialisé cela en introduisant les flux de travail _relatif à l'affichage_ et _relatif à la scène_, qui sont contrôlés par le réglage des [préférences > traitement > flux de travail par défaut](../../../preferences-settings/processing.md).

La principale différence entre ces deux flux de travail est que _relatif à l'affichage_ fonctionne principalement dans la plage dynamique basse de l'écran de l'utilisateur, tandis que _relatif à la scène_ fonctionne dans la plage dynamique élevée du fichier raw d'origine. La transition entre _relatif à la scène_ et _relatif à l'affichage_ est généralement effectuée par un module de _mappage des tonalités_ qui prend en entrée la plage dynamique élevée du boîtier et la compresse pour l'adapter à la plage dynamique du support de sortie.

## flux de travail relatif à l'affichage

Avant la version 3.0, le flux de travail de darktable était _relatif à l'affichage_ (dans les préférences globales l'option flux de travail par défaut = _relatif à l'affichage_) et ceci est toujours fourni comme flux de travail par défaut dans la version actuelle. Dans ce flux de travail, la [_courbe de base_](../../../module-reference/processing-modules/base-curve.md) ou le module [_filmique rvb_](../../../module-reference/processing-modules/filmic-rgb.md) effectue un mappage des tonalités au début du pipeline graphique et la plupart des autres modules de darktable opèrent sur les données d'image dans l'espace compressé _relatif à l'affichage_.

Ce flux de travail utilise l'ordre originel (d'avant darktable 3.0) des modules. Il active automatiquement le module [courbe de base](../../../module-reference/processing-modules/base-curve.md) pour les nouvelles images.

Les données des pixels dans l'espace _relatif à l'affichage_ ne sont pas linéaires et ne sont pas une représentation physiquement réaliste de la scène originale. Cela peut conduire à divers artefacts avec certains modules, d'où la création du flux de travail _relatif à la scène_ (maintenant recommandé).

## flux de travail relatif à la scène

Le nouveau flux de travail _relatif à la scène_ (dans les préférences globales l'option flux de travail par défaut = _relatif à la scène_) a été introduit dans le cadre de darktable 3.0. L'ordre des modules a été entièrement réorganisé pour laisser le module [_filmique rvb _](../../../module-reference/processing-modules/filmic-rgb.md) et la [_courbe de base_](../../../module-reference/processing-modules/base-curve.md) effectuer le mappage des tonalités beaucoup plus tard dans le pipeline graphique. Cela signifie que la plupart des opérations sur les pixels fonctionnent désormais dans l'espace _linéaire rvb_ avec seulement quelques modules restants dans l'espace non linéaire _relatif à l'affichage_. Dans ce flux de travail, il est maintenant recommandé que la majorité du traitement d'image ait lieu en utilisant les modules qui, dans la liste ordonée des modules, sont situés avant [_filmique rvb_](../../../module-reference/processing-modules/filmic-rgb.md) (compris). Les opérations de cette section du pipeline graphique, étant vraiment linéaires, sont beaucoup plus réalistes physiquement et produisent moins d'artefacts.

Ce flux de travail utilise le nouvel ordre des modules (darktable 3.0 et suivant). Il active automatiquement les modules [_exposition_](../../../module-reference/processing-modules/exposure.md) (../../../ module-reference / processing-modules / exposition.md) et [_filmique rvb_](../../../module-reference/processing-modules/filmic-rgb.md) avec quelques préréglages conçus pour servir de point de départ raisonnable au traitement d'images _relativement à la scène_.

# changer l'ordre des modules

Il reste fortement recommandé aux utilisateurs de ne pas modifier l'ordre des modules dans le pipeline graphique pour un certain nombre de raisons :

- La séquence des modules a été choisie avec le plus grand soin afin d'obtenir la plus grande qualité de sortie. En général, les modifications apportées à la séquence feraient pire que mieux.

- Certains modules de traitement d'image n'ont tout simplement pas de sens s'ils sont déplacés dans le pipeline graphique. Par exemple, la [reconstruction des hautes lumières](../../../module-reference/processing-modules/highlight-reconstruction.md) doit être effectuée sur les données raw avant le [dématriçage](../../../module-reference/processing-modules/demosaic.md), qui lui même doit être réalisé avant qu'un quelconque [profil de couleur d'entrée](../../../module-reference/processing-modules/input-color-profile.md) ne soit appliqué.

- La plupart des modules de darktable ont été conçus pour travailler dans un modèle de couleur spécifique (voir [gestion de la couleur](../../../special-topics/color-management/_index.md) pour plus de détails). Une flexibilité totale exigerait des modules supportant différents algorithmes parallèles en fonction de l'espace colorimétrique dans lequel ils travaillent, ceci augmenterait considérablement la complexité.


Malgré la recommandation générale de laisser tel quel l'ordre des modules du pipeline graphique, il est possible de déplacer un module. Pour ce faire, il suffit de maintenir enfoncé Ctrl+Shift tout en faisant un glisser-déposer du module souhaité à son nouvel emplacement. Cela ne doit être fait que par des utilisateurs expérimentés qui comprennent l'impact que cela aura sur l'image.

L'ordre _3.0_ ou l'ordre _originel_ des modules peut être choisi manuellement à l'aide du module [ordre des modules](../../../module-reference/utility-modules/darkroom/module-order.md). Ce module peut également être utilisé pour définir vos propres préréglages de l'ordre des modules.
