---
title: importation, évaluation et labels de couleur
id: import-rate-tag
draft: false
weight: 10
author: "people"
---

Quand vous souhaitez développer de nouvelles images dans darktable, la première étape est de les [importer](../../module-reference/utility-modules/lighttable/import.md). Ceci créera des entrées pour les nouvelles images importées dans la base de données de darktable. Il pourra ainsi suivre les modifications que vous leurs apporterez. Il existe deux méthodes principales pour importer des images : 

importer des images depuis le système de fichiers
: Vous pouvez importer depuis le système de fichier une seule image ou un dossier contenant des images (optionnellement importer les dossiers récursivement). Quand il importe des images, darktable lit les métadonnées qu'elles contiennent et tous les [fichiers liés xmp](../../overview/sidecar-files/_index.md) qui, éventuellement, les accompagnent. Si une image a déjà été importée, elle sera ignorée (bien que toute mise à jour du fichier lié sera chargée). L'emplacement de chaque image est enregistré dans la base de données, mais darktable ne copiera ni ne déplacera les fichiers. Si vous souhaitez un programme qui copie des fichiers dans un dossier spécifique, vous pouvez utiliser un programme comme [rapid photo downloader](https://damonlynch.net/rapid/) pour faire cela.

importer des images depuis un boîtier
: To import images from a camera, first connect the camera to your system with a USB cable. If your system tries to automount the camera's files, you should choose to abort the mount operation, otherwise the camera cannot be accessed from within darktable. If you don't see your camera listed in the import module, press the "scan for devices" button. Once your camera is detected the import module should offer the ability to _import_ images or _tether_ your camera while shooting. Unlike when importing of images from the filesystem, darktable will physically copy files imported from the camera into a specified directory following the file naming pattern defined in [preferences > import](../../preferences-settings/import.md).

Once images are imported, they will appear in the lighttable view. By default, the images will all be given a one-star rating.

There are many different ways to manage a set of newly imported photos, such as giving them tags and adjusting their ratings. Please refer to the [lighttable](../../lighttable/_index.md) section of this guide for a full list of _digital asset management_ features.

One example workflow might be:
1. Set the lighttable view to show photos with exactly a 1 star rating.
2. Perform a quick first-level screening of your photos. If any photos are badly out-of-focus or otherwise useless, _reject_ them with the R key, or give them a 0-star rating. If a photo looks reasonable and should pass to the next phase, press 2 to give it a 2 star rating. Any photos that no longer have a 1 star rating will automatically disappear from view. Continue in this manner until you have completed the first level of assessment.
3. Now set the lighttable view to show only photos with exactly a 2 star rating. Go through these photos more carefully, and decide whether to promote them to a 3 star rating, or put them back down to a 1 star or rejected rating.
4. You can now spend some time performing a quick edit on your 3 star photos, to see if they are worth keeping. If you are happy with the results, you can create a tag for the photo, and promote it to a 4 or even 5 star rating.
5. Go through your 4 and 5 star photos, perform any final edits on them, print them out, publish on your portfolio site, etc. and bask in the copious amounts of critical acclaim you will receive! 
6. If space is at a premium you might want to consider permanently deleting your rejected or 0-star images. Select these images in the lighttable and use the 'trash' option in the [selected images](../../module-reference/utility-modules/lighttable/selected-image.md) module. You should probably only do this on photos you are certain you will never need again (badly focussed, significantly overexposed etc.).

