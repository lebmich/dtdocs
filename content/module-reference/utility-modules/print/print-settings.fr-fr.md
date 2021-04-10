---
applicable-version: 3.2.1
id: print-settings
tags: ~
title: "paramètres d'impression"
view: print
---

Gérer les paramètre de la [vue impression](../../../print/_index.md) et lancer l'impression.

# les contrôles du module

## imprimante

imprimante
: Sélectionner l'une des imprimantes installées.

type de papier
: le type de papier de l'imprimante (papier ordinaire, papier photo lustré, etc.).

profile
: Le profil ICC de l'imprimante pour le papier chargé. C'est le profil spécifique à l'imprimante et au papier de l'imprimante. Ce profil est la dernière transformation d'espace colorimétrique faite à l'image dont le but est de créer une impression de haute qualité.

intent
: The print rendering intent (“perceptual”, “relative colorimetric”, “saturation” or “absolute colorimetric”). See [rendering intent](../../../special-topics/color-management/rendering-intent.md) for more details.

black point compensation
: Whether to adjust the black point of the output profile, which is often lighter than the input profile. This should be “on” when the _intent_ is set to “relative colorimetric”. 

## page

taille papier
: La taille du papier pour l'impression.

orientation
: Portrait ou paysage (notez que darktable choisit par défaut la meilleure solution).

units
: The unit to use for setting the margins: “mm”, “cm”, or “inch”.

margins
: Set each margin separately, or all together by clicking on the middle “lock” button.

largeur/hauteur image
: Ce champ d'informations affiche les largeur et hauteur réelle de l'image sur le papier (données avec les unités sélectionnées).

facteur d’agrandissement
: Ce champ d'informations affiche le facteur d'agrandissement de l'image nécessaire à son ajustement à la taille du papier. Si cette valeur est inférieure à 1 l'image est réduite sinon elle est agrandie. C'est un important facteur à surveiller – une trop grande valeur (agrandissement) peut produire une impression de qualité médiocre. Le dpi (nombre de points par pouce ; dots per inch en anglais) est aussi affiché.

alignement
: Cette option vous permet de sélectionner l'alignement de l'image sur le papier.

## paramètres d'impression

profil
: Ceci vous permet de sélectionner le profil d'exportation à utiliser. Ce profil est le point d'entrée utilisé par la prochaine transformation utilisant le profil d'imprimante ICC ci-dessus. Habituellement il est préférable d'utiliser un profil avec un grand gamut comme AdobeRVB plutôt qu'un profil avec un gamut plus petit comme sRVB.

rendu
: Cette option fixe l'intention de rendu à utiliser pour l'exportation de l'image. Pour plus de d'informations voir [intention de rendu](../../../special-topics/color-management/rendering-intent.md).

style
: Choose a style to apply when exporting the image -- defaults to “none”. See the [export](../shared/export.md) module for a more detailed discussion of applying a style during export.

mode
: Indique si le style sera ajouté à l'historique existant ou s'il le remplacera complètement. Voir [exportation](../shared/export.md) pour plus de détails.

## bouton d'impression

Quand il est cliqué l'image est exportée en utilisant les options sélectionnées et envoyée à l'imprimante.
