---
author: people
draft: 'false'
id: export-metadata-upload
title: "exportation et téléchargement d'images avec métadonnées"
weight: 50
---

Les modifications apportées à une image ne sont pas enregistrées directement dans le fichier image contrairement à un éditeur d'image classique. Au contraire, darktable est un éditeur non destructif, ce qui signifie que toutes les modifications sont enregistrées dans la base de données de la bibliothèque de darktable et que l'image d'origine reste intacte. Par conséquent, vous devez exporter des images afin de sauvegarder vos options de traitement et les modifications de métadonnées dans un fichier de sortie qui peut être distribué en dehors de darktable.

Les images sont exportées à partir de la vue table lumineuse, en utilisant l'onglet [exporter sélection](../../module-reference/utility-modules/lighttable/export-selected.md) du panneau droit. Ce module offre de nombreuses options, mais l'utilisation de loin la plus courante est "sauvegarder mon image raw développée au format JPEG".

Dans darktable, lors de l'exportation d'images, vous devez répondre à deux questions fondamentales :

- _Où dois-je envoyer les images exportées?_ Le plus souvent, vous choisirez d'écrire les fichiers dans un dossier de votre disque local, mais d'autres options incluent leur écriture dans un modèle de livre photo LaTeX ou leur envoi vers un autre programme tel que [Hugin](http://hugin.sourceforge.net/) (pour l'assemblage panoramique) ou [GIMP](https://www.gimp.org/) (pour un développement ultérieur).


- _Dans quel format dois-je enregistrer les images exportées?_ Cela couvre non seulement le format du fichier image (JPEG, PNG, TIFF, OpenEXR etc.) mais également la qualité, la compression, la résolution, les paramètres de profil d'image et quelles métadonnées intégrer dans l'image exportée.


Les étapes les plus courantes seraient donc :

1.  Sélectionnez une ou plusieurs images dans la vue table lumineuse


2.  Choisissez le stockage cible et le format de fichier


3.  Définissez les dimensions limites de l'image en largeur et en hauteur. Laissez les limites de largeur et de hauteur à zéro pour exporter en pleine résolution.


Par défaut, une image sera enregistrée sur le disque local en tant que JPEG de haute qualité à pleine résolution. Pour plus d'informations sur toutes les options d'exportation disponibles, veuillez consulter la référence [exporter sélection](../../module-reference/utility-modules/lighttable/export-selected.md)
