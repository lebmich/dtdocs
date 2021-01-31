---
title: importer
id: import
weight: 30
draft: false
author: "traducteur Michel Leblond"
---

Cet onglet contient un certain nombre de paramètres par défaut pour le module importer de la table lumineuse [importer](../module-reference/utility-modules/lighttable/import.md).

# importer

ignorer les fichiers JPEG lors de l'importation d'un dossier
: Lorsque vous avez des images RAW + JPEG dans un même répertoire, il n'est généralement pas logique d'importer les deux. Définissez cet indicateur pour ignorer tous les fichiers JPEG lors de l'importation d'images (désactivé par défaut).

importer les dossiers de manière récursive
: Lors de l'importation d'images à partir d'un dossier, importe également de manière récursive des images depuis ses sous-dossiers. (désactivé par défaut).

auteur par défaut lors de l'importation
: Si elle est fournie, ajoute automatiquement cette chaîne dans les métadonnées en tant que balise créateur lors de l'importation d'images (aucune par défaut).

diffuseur par défaut lors de l'importation
: Si elle est fournie, ajoute automatiquement cette chaîne dans les métadonnées en tant que balise diffuseur lors de l'importation d'images (aucune par défaut).

droits par défaut lors de l'importation
: Si elle est fournie, ajoute automatiquement cette chaîne dans les métadonnées en tant que balise droits lors de l'importation d'images (aucune par défaut).

mots-clés séparés par des virgules à appliquer à l'importation
: Si vous souhaitez ajouter d'autres balises par défaut lors de l'importation d'images, vous pouvez les fournir ici sous forme de liste, séparées par des virgules (aucune par défaut).

étoile(s) à l'importation
: Évaluation initiale par étoiles (de 0 à 5), pour toutes les images, lors de l'importation (par défaut 1).

# options de session

Ces options définissent un modèle de nommage pour organiser les images sur le disque lors de l'importation à partir d'un appareil photo connecté et lors de la prise de photos dans la vue [capture](../tethering/_index.md).

Le modèle de nommage se compose de trois parties : une partie de base définissant le dossier parent, une partie session définissant un sous-répertoire (qui est spécifique à la session d'importation individuelle) et une partie nom de fichier définissant la structure de nom de fichier pour chaque image importée.

Plusieurs variables prédéfinies peuvent être utilisées dans le modèle comme variables de substitution :

```
$(HOME)              le dossier personnel de l'utilisateur tel que défini par le système
$(PICTURES_FOLDER)   le dossier d'images tel que défini par le système (généralement «$HOME/Images»)
$(DESKTOP)           le dossier bureau tel que défini par le système (généralement «$HOME/Bureau»)
$(USERNAME)          votre nom de compte utilisateur sur le système
$(FILE_NAME)         nom de base de l'image importée
$(FILE_EXTENSION)    extension de l'image importée
$(JOBCODE)           identifiant unique de la tâche d'importation
$(SEQUENCE)          nombre séquentiel dans la tâche d’importation
$(MAX_WIDTH)         largeur maximale d'une image lors de la session d'exportation
$(MAX_HEIGHT)        hauteur maximale d'une image lors de la session d'exportation
$(ID)                identifiant numérique unique de l’image dans la base de données
$(YEAR)              année de la date d’importation
$(MONTH)             mois de la date d’importation
$(DAY)               jour de la date d’importation
$(HOUR)              heure de la date d’importation
$(MINUTE)            minute de la date d’importation
$(SECOND)            seconde de la date d’importation
$(EXIF_YEAR)         année de prise de la photo (à partir des données EXIF)
$(EXIF_MONTH)        mois de prise de la photo (à partir des données EXIF)
$(EXIF_DAY)          jour de prise de la photo (à partir des données EXIF)
$(EXIF_HOUR)         heure de prise de la photo (à partir des données EXIF)
$(EXIF_MINUTE)       minute prise de la photo (à partir des données EXIF)
$(EXIF_SECOND)       seconde de prise de la photo (à partir des données EXIF)
$(EXIF_ISO)          sensibilité ISO de la photo (à partir des données EXIF)
```

nommage du répertoire de base
: La partie répertoire de base du modèle de nommage (par défaut
  `$(PICTURES_FOLDER)/Darktable`).

nommage du sous répertoire
: La partie sous-répertoire du modèle de nommage (par défaut
  `$(YEAR)$(MONTH)$(DAY)_$(JOBCODE)`).

garder le nom d'origine
: Cochez cette case pour conserver le nom de fichier d'origine au lieu d'utiliser le modèle ci-dessous lors de l'importation depuis un appareil photo ou une carte (désactivé par défaut).

nommage des fichiers
: La partie nom de fichier du modèle de nommage (par défaut
  `$(YEAR)$(MONTH)$(DAY)_$(SEQUENCE).$(FILE_EXTENSION`).
