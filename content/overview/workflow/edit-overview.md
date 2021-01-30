---
title: "développer une image: aperçu d'un flux de travail"
id: workflow-overview
draft: false
weight: 20
author: "traducteur : Michel Leblond"
---

Cette section va vous guider à travers les bases du développement d'une image dans la vue [chambre noire](../../darkroom/_index.md), où un arsenal de modules est à votre disposition pour vous aider à atteindre vos objectifs créatifs.

Pour commencer, ouvrez une image dans la chambre noire en double-cliquant sur la miniature d'une image dans la vue [table lumineuse](../../lighttable/_index.md).

Chaque modification que vous apportez à l'image de la chambre noire est transformée en un élément de l'historique. L'historique est stocké dans une base de données et dans un fichier lié xmp pour cette image. Toutes les modifications sont sauvegardées automatiquement lorsque vous changez d'images ou passez d'une vue de darktable à une autre. Vous pouvez quitter le mode chambre noire en toute sécurité ou quitter darktable à tout moment et revenir plus tard pour continuer votre travail. Pour cette raison, darktable n'a pas besoin d'un bouton «enregistrer» et il n'en a pas.

En mode chambre noire, sur le panneau de gauche se trouve l'[historique](../../module-reference/utility-modules/darkroom/history-stack.md). Il liste les modifications que vous avez apportées, en commençant par le bas -- chaque modification ajoute un nouvel élément au sommet de l'historique.  À des fins de comparaison entre les modifications, vous pouvez sélectionner, en cliquant dessus, un point quelconque de cet historique pour voir à quoi ressemblait l'image en ce point. L'historique peut être compressé pour supprimer les points intermédiaires redondants dans votre développement. Lorsque vous êtes satisfait de ce que vous avez fait, compressez simplement l'historique. Notez que lors de la compression de l'historique, sont définitivement supprimées toutes les modifications situées au-dessus de l'entrée d'historique sélectionnée.

Un grand nombre de [modules de traitement](../../module-reference/processing-modules/_index.md) sont fournis avec darktable. Ils sont organisés en [groupes de modules](../../darkroom/interacting-with-modules/search-and-group.md). Ces groupes sont accessibles via les boutons-bascule en haut du panneau de droite, juste en dessous de l'[histogramme](../../module-reference/utility-modules/shared/histogram.md).

# choisir un flux de travail

Lors du traitement d'une image, nous appliquons une séquence de modules, connue sous le nom de [pipeline graphique](../../darkroom/processing-modules-and-pixelpipe/_index.md).

![edit-overview](./edit-overview/edit-overview.png#w100)

1. Les modules _relatif à la scène_  sont destinés à traiter des valeurs de pixels proportionnelles à la quantité de lumière collectée par le boîtier dans la scène. La plage dynamique d'une image dans la section _relative à la scène_ du pipeline graphique est souvent plus grande que celle du support d'affichage.

2. À un moment donné dans le pipeline graphique, ces valeurs de pixels sont compressées par un module de mappage des tonalités dans une plage dynamique plus petite mieux appropriée à l'affichage sur un moniteur ou une impression papier.

3. Les modules restants opèrent dans la section _relative à l'affichage_, non-linéaire pour produire l'image de sortie finale.

Il existe deux flux de travail standard proposés dans darktable (ceci peut être modifié dans [préférences > traitement > flux de travail par défaut](../../preferences-settings/processing.md)) :
* [_flux de travail relatif à la scène_](edit-scene-referred.md) : Ici, l'accent est mis sur la réalisation, autant que possible, du traitement dans la partie du pipeline graphique _relative à la scène_, et la réalisation, le plus tard possible, de la compression de la plage dynamique vers l'espace _relatif à l'affichage_. Il s'agit du flux de travail recommandé. Il utilise le module [_filmique rvb_](../../module-reference/processing-modules/filmic-rgb.md) pour effectuer le mappage de compression des tonalités.

* [_le flux de travail relatif à l'affichage_](edit-display-referred.md) : Il s'agit du flux de travail originel. C'est toujours le paramètre par défaut lors de la première installation de darktable. Il effectue le mappage de compression des tonalités beaucoup plus tôt dans le pipeline graphique. De nombreux modules fonctionnent donc dans l'espace _relatif à l'affichage_.  Il utilise le module [_courbe de base_](../../module-reference/processing-modules/base-curve.md) pour effectuer le mappage de compression des tonalités.

Une troisième option consiste à définir l'option de préréglages du flux de travail par défaut sur _aucun_. Dans ce cas, l'ordre des modules du flux de travail _relatif à la scène_ sera utilisé par défaut mais aucun des modules ci-dessus ne sera automatiquement appliqué. Il appartient à l'utilisateur d'organiser un mappage des tonalités approprié et de réorganiser les modules si nécessaire.

---

**Remarque :** lors d'une modification du flux de travail par défaut dans les préférences de darktable, le nouveau paramètre ne s'appliquera qu'aux images nouvellement importées. Si vous avez déjà importé une image en utilisant un paramètre de flux de travail différent, accédez à l'[_historique_](../../module-reference/utility-modules/darkroom/history-stack.md) dans la vue chambre noire, sélectionnez  "original", et cliquez "compresser l'historique". Cela supprimera toutes les modifications et réinitialisera le flux de travail pour cette image.

---
