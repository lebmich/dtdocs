---
title: fichiers liés
id: sidecar
weight: 10
draft: false
author: "people"
---

darktable est un éditeur d’images non destructif. Il ouvre les images en lecture seule. Toutes les donnés créées dans darktable (métadonnées, mots-clés et étapes du traitement d'image) sont enregistrées dans un fichier séparé `.xmp` appelé _fichier lié_. Ces fichiers permettent à darktable de stocker des informations concernant les images ainsi que l'historique complet de développement sans toucher aux fichiers RAW originaux. Lorsque vous importez une image pour la première fois dans darktable, un fichier lié xmp est automatiquement créé en utilisant des paramètres par défaut. La génération automatiqe de ces fichiers liés xmp peut être désactivée dans [préférences > stockage](../../preferences-settings/storage.md) mais ceci n'est pas recommandé dans un usage normal.

Pour une image source donnée, plusieurs versions d'édition, appelées _clones_, peuvent coexister, partageant les mêmes données d'entrée (RAW) mais chacune ayant ses propres métadonnées, mots-clés et étapes de traitement. Chaque clone est représenté par un fichier lié xmp distinct. Son nom est construit sous la forme `<basename>_nn.<extension>.xmp`, où `nn` représente le numéro de version de cette modification. Les informations du  premier traitement de l'image - le "clone" avec le numéro de version zéro - sont stockées dans le fichier lié `<basename>.<extension>.xmp`. Le numéro de version de chaque duplicata est affiché dans la liste déroulante [informations de l'image](../../module-reference/utility-modules/shared/image-information.md) dans chacune des vues de darktable.

Les fichiers liés sont synchronisés automatiquement avec votre travail sans passer par un bouton "enregistrer". Quand vous effectuez une copie de sauvegarde de vos données, assurez-vous que vous sauvegarder aussi les fichiers xmp, car ils sont nécessaires pour reconstruire entièrement votre travail en cas de catastrophe.

Pour un accès rapide, en plus des fichiers liés, darktable conserve les données associées à toutes les images dans une base de données. Une image ne peut être affichée et modifiée dans darktable que si ses données ont été chargées dans cette base de données. Ceci se fait automatiquement lorsque vous importez une image pour la première fois (voir [importer](../../module-reference/utility-modules/lighttable/import.md)). Si une image est ultérieurement réimportée, la base de données sera mise à jour à partir des données du fichier xmp.

Dès qu'une image a été importée dans darktable, les entrées de la base de données ont priorité sur le fichier xmp. Les modifications ultérieures apportées à un fichier xmp par tout autre logiciel ne sont pas visibles par darktable -- ces modifications seront écrasées la prochaine fois que darktable synchronisera ce fichier. Sur demande, darktable peut être configuré pour, au démarrage, rechercher les fichiers xmp mis à jour, offrant le choix de mettre à jour la base de données ou d'écraser le fichier xmp là où des modifications seront identifiées. Cette configuration peut également être modifiée dans [préférences > stockage](../../preferences-settings/storage.md).
