---
title: importer des fichiers liés générés par d'autres applications
id: sidecar-import
weight: 20
draft: false
author: "people"
---

Lorsqu'il importe une image, darktable teste automatiquement s'il est accompagné d'un fichier lié. En plus de rechercher les fichiers nommés `<basename>.<extension>.xmp` et `<basename>_nn.<extension>.xmp` (les formats de dénomination des fichiers xmp de darktable), il vérifie également la présence d'un fichier sous la forme `<basename> .xmp` (le format de dénomination des fichiers lié xmp de Lighroom). Les fichiers avec ce dernier format de dénomination seront lus par darktable mais il n'y écrira pas. Une fois l'image importée, darktable générera un fichier xmp supplémentaire en utilisant sa propre convention de dénomination.

À ce jour, pendant la phase d'importation, à partir de fichiers liés générés par Lightroom, darktable est capable de traiter les métadonnées suivantes :

- mots-clés (y compris les mots-clés hiérarchiques)
- les labels de couleurs
- les évaluations
- les informations GPS

De plus, darktable a été conçu pour faciliter la migration d'opérations de développement des images provenant de certaines applications. L'objectif n’est pas de faire de darktable un remplaçant direct de tout autre logiciel ; il s'agit plutôt de vous aider à récupérer une partie du travail investi dans votre image si vous décidez de migrer vers darktable. Il est important de comprendre que ce processus d’importation ne donnera jamais des résultats identiques. Les moteurs de développement sous-jacents sont très différents d’une application à l’autre et dépendent en outre beaucoup de l’image concernée. Dans certains cas les résultats obtenus seront probablement proches mais dans d’autres le développement nécessitera un ajustement manuel dans darktable.

La migration est automatique lorsqu’on entre dans la vue chambre noire à condition qu’un fichier lié xmp soit trouvé.

À ce jour, darktable est capable de prendre en charge les étapes de développement suivantes des fichiers xmp générés par Lightroom (module correspondant de darktable entre parenthèses) :


- recadrer et pivoter ([_recadrer et pivoter_](../../module-reference/processing-modules/crop-rotate.md))
- niveau de noir ([_exposition_](../../module-reference/processing-modules/exposure.md))
- exposition ([_exposition_](../../module-reference/processing-modules/exposure.md))
- vignettage ([_vignettage_](../../module-reference/processing-modules/vignetting.md))
- clarté ([_contraste local_](../../module-reference/processing-modules/local-contrast.md))
- courbes des tonalités ([_courbe des tonalités_](../../module-reference/processing-modules/tone-curve.md))
- TSL ([_zones de couleur_](../../module-reference/processing-modules/color-zones.md))
- virage partiel ([_virage partiel_](../../module-reference/processing-modules/split-toning.md))
- grain ([_grain_](../../module-reference/processing-modules/grain.md))
- correction des taches ([_correction des taches_](../../module-reference/processing-modules/spot-removal.md))
