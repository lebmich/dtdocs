---
author: people
draft: 'false'
id: color-artifacts
title: 'artefacts de couleur possibles'
weight: 70
---

Il existe quelques situations rares qui peuvent encore conduire à des résultats problématiques à moins que l'utilisateur ne prenne des mesures. Pour certains modules de l'espace colorimétrique Lab, comme [_niveaux_](../../module-reference/processing-modules/levels.md) et [_monochrome_](../../module-reference/processing-modules/monochrome.md), il faut tenir compte du fait que les canaux L transportent toutes les informations de clarté, les canaux a et b représentant, quant à eux, purement la chrominance et la teinte. Les couleurs non bornées avec des valeurs L négatives sont particulièrement problématiques pour ces modules et peuvent conduire à des artefacts de pixels noirs.

On a constaté que des sources de lumière bleue hautement saturées dans l'image sont des candidats probables pour des pixels ayant des valeurs de L négatives. Si vous êtes engagé dans la photographie de spectacle, vous devez prêter une attention particulière à ces lumières apparaissant dans les images.

Afin d'atténuer ce problème, le module [_profil de couleur d'entrée_](../../module-reference/processing-modules/input-color-profile.md) a une option d'écrêtage du gamut. Cette option est désactivée par défaut mais peut être activée si des artefacts sont observés. En fonction des paramètres, les couleurs seront limitées à l'un des gamuts RVB disponibles. En effet, les artefacts de pixels noirs sont évités au prix d'un rétrécissement de la plage des couleurs.
