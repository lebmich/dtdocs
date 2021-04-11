---
draft: 'false'
id: presets
title: préréglages
weight: 30
---

Les préréglages vous permettent de stocker pour une utilisation future les paramètres d'un module couramment utilisé. Certains modules sont déjà livrés avec des préréglages prédéfinis et vous pouvez également définir les vôtres. Les préréglages internes et définis par l'utilisateur peuvent être affichés en cliquant sur le _menu des préréglages_ dans [entête du module](./ module-header.md).

Most of the functionality described here applies to processing modules only. However, presets can also be used with some utility modules. When used with utility modules, the functionality to auto-apply or auto-show presets based on image Exif data is not available.

# le menu des préréglages

The presets menu will contain one or more of the following entries depending on what presets are defined or selected for the current module:

preset list
: A list of the presets available for the current module. The currently selected preset (if any) is shown in **bold**.

edit this preset
: If a preset has been selected, click to edit that preset (see below)

delete this preset
: If a preset has been selected, delete that preset.

update preset \[name\]
: Update the named preset to match the module's current parameters.

store new preset
: Create a new preset using the module's current parameters.

Left-click on a preset name to apply the preset to the current instance of the module.  Right-click on a preset name to create a new instance of the module and apply the selected preset to it.  You can also apply a preset at any time while you are in the darkroom by pressing the shortcut key that has been assigned to it (see [preferences > shortcuts](../../preferences-settings/shortcuts.md)).

# créer et modifier des préréglages

Lors de la création ou de la modification des préréglages, la boîte de dialogue suivante s'affiche :

![nouveau préréglage](./presets/new_preset.png#w33)

The following options can be set:

name
: The name of the preset

description
: A searchable description for the preset (optional)

auto apply this preset to matching images _(processing modules only)_
: Check this box to automatically apply this preset to matching images when they are opened in the darkroom for the first time (you can reapply such automatic presets by Ctrl+clicking on the _reset_ button in the [module header](./module-header.md)). Additional controls will appear to allow you to define which images the preset will be applied to based on image Exif data (see below).

: For example, if you want a preset to be applied to all images from a specific camera leave all fields at default values except for the model field. Leave all fields unchanged to auto-apply a preset to all images.

: The example dialog above sets up following rules: if the lens name matches, the aperture is greater than or equal to f/8 and the focal length is between 24 and 35mm the preset will be automatically applied. 

: _The [image information](../../module-reference/utility-modules/shared/image-information.md) module displays the camera model and lens name for each image. Use this to ensure you have the correct spelling._

only show this preset for matching images _(processing modules only)_
: Check this box to automatically show the preset in the preset menu, using the same set of filters.

# filter criteria

Les critères suivants peuvent être utilisés pour appliquer ou afficher automatiquement les préréglages des modules de traitement.

model
: A pattern to be matched against the Exif field that describes your camera model; use % as wildcard.

maker
: A pattern to be matched against the Exif field that describes the maker of your camera; use % as wildcard.

lens
: A pattern to be matched against the Exif field that describes your lens; use % as wildcard.

ISO
: Only apply the preset if the ISO value of your image lies within the given range.

exposure
: Only apply the preset if the exposure time of your image lies within the given range; set + as the upper value to match arbitrarily long exposures.

aperture
: Only apply the preset if the aperture of your image lies within the given range; set f/0 as the lower value to match arbitrarily open apertures; set f/+ as the upper value to match arbitrarily closed apertures.

focal length
: Only apply the preset if the focal length of your image lies within the given range (from 0 to 1000). 

format
: Only apply the preset to certain types of image. Choose from "normal images", "raw", "HDR", "monochrome" and "color".

# gérer les préréglages

Les préréglages créés par l'utilisateur et les préréglages prédéfinis peuvent être visualisés et gérés à partir de [préférences > préréglages](../../../preferences-settings/presets.md).

---

**Note:** If you create a user-defined preset with the same name as a built-in preset, your preset will override the built-in version, which will no longer be accessible.

If you delete a preset that has the same name as one of the built-in presets, then your user preset will be deleted, and that preset name will no longer appear in the preset menu at all. The next time you start darktable, the corresponding built-in preset will once again become visible.

---

