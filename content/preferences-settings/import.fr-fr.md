---
draft: 'false'
id: import
title: importer
weight: 30
---

Cet onglet contient un certain nombre de paramètres par défaut pour le module importer de la table lumineuse [importer](../module-reference/utility-modules/lighttable/import.md).

# options de session

Ces options définissent un modèle de nommage pour organiser les images sur le disque lors de l'importation à partir d'un appareil photo connecté et lors de la prise de photos dans la vue [capture](../tethering/_index.md).

Le modèle de nommage se compose de trois parties : une partie de base définissant le dossier parent, une partie session définissant un sous-répertoire (qui est spécifique à la session d'importation individuelle) et une partie nom de fichier définissant la structure de nom de fichier pour chaque image importée.

Plusieurs variables prédéfinies peuvent être utilisées dans le modèle comme variables de substitution :

```
$(HOME)              the home folder as defined by the system
$(PICTURES_FOLDER)   the pictures folder as defined by the system (usually “$HOME/Pictures”)
$(DESKTOP)           the desktop folder as defined by the system (usually “$HOME/Desktop”)
$(USERNAME)          your user account name on the system
$(FILE_NAME)         basename of the imported image
$(FILE_EXTENSION)    extension of the imported image
$(JOBCODE)           unique identifier of the import job
$(SEQUENCE)          a sequence number within the import job
$(MAX_WIDTH)         maximum image width to limit within export session
$(MAX_HEIGHT)        maximum image height to limit within export session
$(ID)                unique identification number of the image in darktable's database
$(YEAR)              year at the date of import
$(MONTH)             month at the date of import
$(DAY)               day at the date of import
$(HOUR)              hour at the time of import
$(MINUTE)            minute at the time of import
$(SECOND)            second at the time of import
$(EXIF_YEAR)         year the photo was taken (from Exif data)
$(EXIF_MONTH)        month the photo was taken (from Exif data)
$(EXIF_DAY)          day the photo was taken (from Exif data)
$(EXIF_HOUR)         hour the photo was taken (from Exif data)
$(EXIF_MINUTE)       minute the photo was taken (from Exif data)
$(EXIF_SECOND)       seconds the photo was taken (from Exif data)
$(EXIF_ISO)          ISO value of the photo (from Exif data)
```

nommage du répertoire de base
: La partie répertoire de base du modèle de nommage (par défaut `$(PICTURES_FOLDER)/Darktable`).

nommage du sous répertoire
: La partie sous-répertoire du modèle de nommage (par défaut `$(YEAR)$(MONTH)$(DAY)_$(JOBCODE)`).

garder le nom d'origine
: Cochez cette case pour conserver le nom de fichier d'origine au lieu d'utiliser le modèle ci-dessous lors de l'importation depuis un appareil photo ou une carte (désactivé par défaut).

nommage des fichiers
: La partie nom de fichier du modèle de nommage (par défaut `$(YEAR)$(MONTH)$(DAY)_$(SEQUENCE).$(FILE_EXTENSION`).
