---
draft: 'false'
id: storage
title: stockage
weight: 100
---

Les options suivantes sont relatives à la base de données de darktable et aux [fichiers liés XMP](../overview/sidecar-files/_index.md).

# base de données

vérifier pour la maintenance de la base de données
: Indique quand darktable doit vérifier la fragmentation de la base de données et effectuer la maintenance. Les options sont "jamais", "au démarrage", "à la fermeture", et "au deux". Chacun de ceux-ci est également disponible avec une option supplémentaire "(sans confirmation)" pour effectuer les vérifications automatiquement et sans invite (par défaut "à la fermeture").

seuil de fragmentation de la base de données
: Taux de fragmentation (en pourcentage) au-dessus duquel la maintenance de la base de données doit être effectuée (sous réserve de la sélection effectuée dans l'option ci-dessus) (par défaut 25).

faire une sauvegarde de la base de données
: Spécifie la fréquence des sauvegardes de la base de données. Les options sont «jamais», «une fois par mois», «une fois par semaine», «une fois par jour» et «à la fermeture» (par défaut «une fois par semaine»)

nombre de sauvegarde à conserver
: Nombre de sauvegardes à conserver après la création d'une nouvelle sauvegarde, sans compter les sauvegardes de base de données effectuées lors du passage d'une version de darktable à une autre. Entrez "-1" pour stocker un nombre illimité de sauvegardes. (par défaut 10)

# xmp

écrire un fichier XMP redondant pour chaque image
: Les fichiers XMP fournissent une méthode redondante pour enregistrer les modifications que vous avez apportées à une image, indépendamment de la base de données de darktable. Les fichiers XMP peuvent être réimportés ultérieurement dans une autre base de données, en préservant les modifications apportées à l'image. Il est fortement recommandé de laisser cette option activée afin de ne pas perdre de données si votre base de données est corrompue. La sauvegarde de votre fichier RAW et du fichier XMP qui l'accompagne vous permettra de restaurer complètement votre travail (activé par défaut).

store xmp tags in compressed format
: Entries in XMP tags can get rather large and may exceed the available space to store the history stack in some output files on export. This option allows binary XMP tags to be compressed in order to save space. Available options are “never”, “always”, and “only large entries” (default).

look for updated xmp files on startup
: Scan all XMP files on startup and check if any have been updated in the meantime by some other software. If updated XMP files are found, a menu is opened for the user to choose which of the XMP files to reload (replacing darktable's database entries by the XMP file contents) and which of the XMP to overwrite from darktable's database. Activating this option also causes darktable to check for text sidecar files that have been added after import time – see [preferences > lighttable > overlay txt sidecar over zoomed images](./lighttable.md) (default off). 
