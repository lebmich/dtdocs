---
author: people
draft: 'false'
id: variables
title: variables
weight: 60
---

darktable prend en charge la substitution de variables dans un certain nombre de modules et dans les préférences. Par exemple :

- Définition des noms de fichiers dans le module [exporter sélection](../module-reference/utility-modules/shared/export.md)

- Affichage des informations de l'image dans la [ligne d'informations de l'image](../module-reference/utility-modules/darkroom/image-info-line.md) de la chambre noire

- Affichage des informations de l'image dans les superpositions et les info-bulles de la table lumineuse (voir [préférences > table lumineuse](../preferences-settings/lighttable.md))

- Placement de texte sur une image dans le module [_filigrane_](../module-reference/processing-modules/watermark.md).


# variables disponibles

Les variables suivantes sont disponibles, bien qu'elles ne le soient pas dans certains contextes.

```
$(ROLL_NAME)               pellicule de l’image en entrée
$(FILE_FOLDER)             répertoire contenant l’image en entrée
$(FILE_NAME)               nom de base de l’image en entrée
$(FILE_EXTENSION)          extension du fichier de l’image en entrée
$(ID)                      id de l’image
$(VERSION)                 numéro de version de l'image clonée
$(VERSION_IF_MULTI)        identique à $(VERSION) mais chaîne vide si une seule version existe
$(VERSION_NAME)            nom de version des métadonnées
$(SEQUENCE)                nombre séquentiel dans la tâche d’exportation
$(MAX_WIDTH)               largeur maximale d'une image lors de la session d'exportation
$(MAX_HEIGHT)              hauteur maximale d'une image lors de la session d'exportation
$(YEAR)                    année de la date d’exportation
$(MONTH)                   mois de la date d’exportation
$(DAY)                     jour de la date d’exportation
$(HOUR)                    heure de la date d’exportation
$(MINUTE)                  minutes de l’heure d’exportation
$(SECOND)                  secondes de l’heure d’exportation
$(EXIF_YEAR)               année Exif
$(EXIF_MONTH)              mois Exif
$(EXIF_DAY)                jour Exif
$(EXIF_HOUR)               heure Exif
$(EXIF_MINUTE)             minute Exif
$(EXIF_SECOND)             seconde Exif
$(EXIF_ISO)                valeur ISO
$(EXIF_EXPOSURE)           exposition Exif
$(EXIF_EXPOSURE_BIAS)      biais d'exposition Exif
$(EXIF_APERTURE)           ouverture Exif
$(EXIF_FOCAL_LENGTH)       longueur focale Exif
$(EXIF_FOCUS_DISTANCE)     distance focale Exif
$(LONGITUDE)               longitude
$(LATITUDE)                latitude
$(ELEVATION)               élévation
$(STARS)                   évaluation par étoiles (nombre)
$(RATING_ICONS)            évaluation par étoiles avec des caractères étoiles
$(LABELS)                  étiquettes de couleur (texte seulement)
$(LABELS_ICONS)            étiquettes de couleur (puces caractères colorés)
$(LABELS_COLORICONS)       étiquettes de couleur (icônes colorées)
$(MAKER)                   fabricant du boîtier
$(MODEL)                   modèle du boîtier
$(LENS)                    objectif
$(TITLE)                   titre d'après les métadonnées
$(DESCRIPTION)             description d'après les métadonnées
$(CREATOR)                 créateur d'après les métadonnées
$(PUBLISHER)               éditeur d'après les métadonnées
$(RIGHTS)                  droits d'après les métadonnées
$(TAGS)                    liste de mots-clés (Xmp.dc.Subject)
$(CATEGORYn(category))     nom du mot-clé de niveau n [0,9] de la catégorie sélectionnée (ou mot-clé)
$(SIDECAR_TEXT)            contenu texte du fichier lié s'il existe
$(PICTURES_FOLDER)         répertoire des images
$(HOME)                    répertoire de l'utilisateur
$(DESKTOP)                 répertoire du bureau
$(OPENCL_ACTIVATED)        si OpenCL est activé
$(USERNAME)                nom de l'utilisateur défini par le système
$(NL)                      caractère nouvelle ligne
$(JOBCODE)                 code interne du travail courant
```

# substitution de varaible

Toutes les variables supportent la substitution de chaîne de base inspirée de bash, bien que certains détails diffèrent. 

Tous les modèles sont traités comme de simples comparaisons de chaînes de caractères. Il n'y a pas de support des expressions régulières. 

Les fonctions suivantes de remplacement de chaînes sont fournies, où `var` est l'une des variables répertoriées ci-dessus :

```
$(var-default)                   Si var est vide, renvoie "défaut"
$(var+alt_value)                 Si var est défini, renvoie "alt_value" sinon renvoie une chaîne vide
$(var:offset)                    Renvoie la partie de var commençant à offset 
                                 Si offset est négatif on compte à partir de la fin de la chaîne
$(var:offset:length)             À partir de offset, renvoie au plus lenght caractères de var
                                 Si offset est négatif lenght est compté à partir de la fin de var
                                 Si length est négatif,  il indique la fin du résultat, 
                                 compté à partir de la fin de var et non une longueur réelle
$(var#pattern)                   Supprime "pattern" au début de var 
$(var%pattern)                   Supprime "pattern" à la fin de var 
$(var/pattern/replacement)       Remplace par "replacement", la première occurrence de "pattern" dans var
                                 Si "replacement" est vide alors "pattern" sera supprimé. 
$(var//pattern/replacement)      Remplace par "replacement", toutes les occurrences de "pattern" dans var
                                 Si "replacement" est vide alors "pattern" sera supprimé
$(var/#pattern/replacement)      Si var commence par "pattern" alors "pattern" est remplacé par "replacement"
$(var/%pattern/replacement)      Si var se termine par "pattern" alors "pattern" est remplacé par "replacement"
$(var^)                          Met en majuscule le premier caractère de var
$(var^^)                         Met en majuscule tous les caractères de var
$(var,)                          Met en minuscule le premier caractère de var
$(var,,)                         Met en minuscule tous les caractères de var
```
