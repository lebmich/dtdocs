---
author: people
draft: 'false'
id: sidecar
title: 'fichiers liés'
weight: 10
---

darktable est un éditeur d’images non destructif. Il ouvre les images en lecture seule. Toutes les donnés créées dans darktable (métadonnées, mots-clés et étapes du traitement d'image) sont enregistrées dans un fichier séparé `.XMP` appelé _fichier lié_. Ces fichiers permettent à darktable de stocker des informations concernant les images ainsi que l'historique complet de développement sans toucher aux fichiers raw originaux. Lorsque vous importez une image pour la première fois dans darktable, un fichier lié XMP est automatiquement créé en utilisant des paramètres par défaut. La génération automatique de ces fichiers liés XMP peut être désactivée dans [préférences > stockage](../../preferences-settings/storage.md) mais ceci n'est pas recommandé dans un usage normal.

For a given source image, multiple editing versions, called _duplicates_, can co-exist, sharing the same input (raw) data but each having their own metadata, tags and processing steps. Each duplicate is represented by a separate XMP sidecar file (with a filename constructed in the form `<basename>_nn.<extension>.xmp`, where `nn` represents the version number of that edit). Information for the initial edit – the “duplicate” with version number zero  – is stored in the sidecar file `<basename>.<extension>.xmp`. The version number of each duplicate is displayed in the [image information](../../module-reference/utility-modules/shared/image-information.md) module in each of darktable's views.

Sidecar files are automatically synchronized with your work without the need to press a “save” button. When backing up your data, make sure you also retain the XMP files, as these are needed to fully reconstruct your work in case of a disaster.

Pour un accès rapide, en plus des fichiers liés, darktable conserve les données associées à toutes les images dans une base de données. Une image ne peut être affichée et modifiée dans darktable que si ses données ont été chargées dans cette base de données. Ceci se fait automatiquement lorsque vous importez une image pour la première fois (voir [importer](../../module-reference/utility-modules/lighttable/import.md)). Si une image est ultérieurement réimportée, la base de données sera mise à jour à partir des données du fichier XMP.

Dès qu'une image a été importée dans darktable, les entrées de la base de données ont priorité sur le fichier XMP. Les modifications ultérieures apportées à un fichier XMP par tout autre logiciel ne sont pas visibles par darktable -- ces modifications seront écrasées la prochaine fois que darktable synchronisera ce fichier. Sur demande, darktable peut être configuré pour, au démarrage, rechercher les fichiers XMP mis à jour, offrant le choix de mettre à jour la base de données ou d'écraser le fichier XMP là où des modifications seront identifiées. Cette configuration peut également être modifiée dans [préférences > stockage](../../preferences-settings/storage.md).
