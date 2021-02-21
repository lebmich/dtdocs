---
title: stockage
id: storage
weight: 100
draft: false
author: "traducteur : Michel Leblond"
---

The following options are related to darktable's library database and [XMP sidecar files](../overview/sidecar-files/_index.md).

# base de données

vérifier pour la maintenance de la base de données
: Indicates when darktable should check for database fragmentation and perform maintenance. Options are "never", "on startup", "on close" and "on both". Each of these is also available with an additional "(don't ask)" option to perform the checks automatically without prompting (default "on close").

seuil de fragmentation de la base de données
: Fragmentation ratio (in per cent) above which database maintenance should be performed (subject to the selection made in the option above) (default 25).

faire une sauvegarde de la base de données
: Specifies how often darktable should create database snapshots. Options are "never", "once a month", "once a week", "once a day" and "on close" (default "once a week")

nombre de sauvegarde à conserver
: Number of snapshots to keep after creating a new snapshot, not counting database backups taken when moving between darktable versions. Enter "-1" to store an unlimited number of snapshots. (default 10)

# xmp

écrire un fichier xmp redondant pour chaque image
: XMP files provide a redundant method of saving the changes you have made to an image, independently of darktable's database. XMP files can later be re-imported into a different database, preserving your changes to the image. It's strongly recommended that you leave this option activated so that you don't lose data if your database becomes corrupted. Backing up your raw file plus the accompanying XMP file will allow you to fully restore your work (default on).

enregistre les mots-clés xmp avec un format compressé
: Entries in XMP tags can get rather large and may exceed the available space to store the history stack in some output files on export. This option allows binary XMP tags to be compressed in order to save space. Available options are “never”, “always”, and “only large entries” (default).

vérifie au démarrage les fichiers xmp modifiés
: Scan all XMP files on startup and check if any have been updated in the meantime by some other software. If updated XMP files are found, a menu is opened for the user to choose which of the XMP files to reload (replacing darktable's database entries by the XMP file contents) and which of the XMP to overwrite from darktable's database. Activating this option also causes darktable to check for text sidecar files that have been added after import time – see [preferences > lighttable > overlay txt sidecar over zoomed images](./lighttable.md) (default off).
