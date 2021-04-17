---
draft: 'false'
id: presets
title: préréglages
weight: 30
---

Les préréglages vous permettent de stocker pour une utilisation future les paramètres d'un module couramment utilisé. Certains modules sont déjà livrés avec des préréglages prédéfinis et vous pouvez également définir les vôtres. Les préréglages internes et définis par l'utilisateur peuvent être affichés en cliquant sur le _menu des préréglages_ dans [entête du module](./ module-header.md).

Most of the functionality described here applies to processing modules only. However, presets can also be used with some utility modules. When used with utility modules, the functionality to auto-apply or auto-show presets based on image Exif data is not available.

Please note that, for processing modules, the saved preset also includes the active state of the module. You can use this to create your own default settings, which you can activate on-demand. Simply set your desired defaults, disable the module, and save the preset.

# le menu des préréglages

Le menu des préréglages contiendra une ou plusieurs des entrées suivantes en fonction des préréglages définis ou sélectionnés pour le module actuel :

liste des préréglages
: Une liste des préréglages disponibles pour le module actuel. Le préréglage actuellement sélectionné (le cas échéant) est affiché en **gras**.

modifier ce préréglage
: Si un préréglage a été sélectionné, cliquez pour modifier ce préréglage (voir ci-dessous)

supprimer ce préréglage
: Si un préréglage a été sélectionné, supprimer ce préréglage.

mettre à jour le préréglage \[nom\]
: Mettre à jour le préréglage nommé pour qu'il corresponde aux paramètres actuels du module.

stocker un nouveau préréglage
: Créer un nouveau préréglage en utilisant les paramètres actuels du module.

Left-click on a preset name to apply the preset to the current instance of the module.  Right-click on a preset name to create a new instance of the module and apply the selected preset to it.  You can also apply a preset at any time while you are in the darkroom by pressing the shortcut key that has been assigned to it (see [preferences > shortcuts](../../preferences-settings/shortcuts.md)).

# créer et modifier des préréglages

Lors de la création ou de la modification des préréglages, la boîte de dialogue suivante s'affiche :

![nouveau préréglage](./presets/new_preset.png#w33)

Les options suivantes peuvent être définies :

nom
: Le nom du préréglage

description
: Une description consultable pour le préréglage (facultatif)

auto apply this preset to matching images _(processing modules only)_
: Check this box to automatically apply this preset to matching images when they are opened in the darkroom for the first time (you can reapply such automatic presets by Ctrl+clicking on the _reset_ button in the [module header](./module-header.md)). Additional controls will appear to allow you to define which images the preset will be applied to based on image Exif data (see below).

: Par exemple, si vous souhaitez qu'un préréglage soit appliqué à toutes les images d'un boîtier spécifique, laissez tous les champs aux valeurs par défaut, à l'exception du champ de modèle. Laissez tous les champs inchangés pour appliquer automatiquement un préréglage à toutes les images.

: L'exemple de boîte de dialogue ci-dessus définit les règles suivantes : si le nom de l'objectif correspond, si l'ouverture est supérieure ou égale à f/8 et si la distance focale est comprise entre 24 et 35 mm, le préréglage sera automatiquement appliqué. 

: Le module [_informations de l'image_](../../module-reference/utility-modules/shared/image-information.md) affiche le modèle de boîtier et le nom de l'objectif pour chaque image. Utilisez ceci pour vous assurer que vous avez l'orthographe correcte.

only show this preset for matching images _(processing modules only)_
: Check this box to automatically show the preset in the preset menu, using the same set of filters.

# filter criteria

The following criteria can be used to auto-apply or auto-show presets for processing modules.

patron
: Un motif à comparer avec le champ Exif qui décrit votre modèle d'appareil photo ; utilisez % comme joker.

fabricant
: Un motif à faire correspondre avec le champ Exif qui décrit le fabricant de votre appareil photo ; utilisez % comme joker.

objectif
: Un motif à comparer avec le champ Exif qui décrit votre objectif ; Utilisez % comme joker.

ISO
: N'appliquer le préréglage que si la valeur ISO de votre image se situe dans la plage donnée.

exposition
: N'appliquer le préréglage que si le temps d'exposition de votre image se situe dans la plage donnée ; définir + comme valeur supérieure pour correspondre à des expositions arbitrairement longues.

ouverture
: N'appliquer le préréglage que si l'ouverture de votre image se situe dans la plage donnée ; mettez f/0 comme valeur la plus faible, elle correspondra aux valeurs d'ouverture arbitrairement grandes ; mettez f/+ comme valeur supérieure, elle correspondra aux valeurs d'ouverture arbitrairement petites.

distance focale
: N'appliquer le préréglage que si la distance focale de votre image se situe dans la plage donnée (de 0 à 1000). 

format
: N'appliquer le préréglage qu'à certains types d'images. Choisissez parmi «images normales», «raw», «HDR», «monochrome» et «couleur».

# gérer les préréglages

Les préréglages créés par l'utilisateur et les préréglages prédéfinis peuvent être visualisés et gérés à partir de [préférences > préréglages](../../../preferences-settings/presets.md).

---

**Remarque :** Si vous créez un préréglage défini par l'utilisateur avec le même nom qu'un préréglage intégré, votre préréglage remplacera la version intégrée, qui ne sera plus accessible.

Si vous supprimez un préréglage qui porte le même nom que l'un des préréglages intégrés, votre préréglage utilisateur sera supprimé et ce nom de préréglage n'apparaîtra plus du tout dans le menu des préréglages. La prochaine fois que vous démarrez darktable, le préréglage intégré correspondant redeviendra visible.

---

