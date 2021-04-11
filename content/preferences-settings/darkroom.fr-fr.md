---
draft: 'false'
id: darkroom
title: 'chambre noire'
weight: 50
---

Les options suivantes contrôlent les fonctionnalités de la vue [chambre noire](../darkroom/_index.md) et des modules associés.

# général

pen pressure control for brush masks
: Controls how the pressure reading of a graphics tablet impacts newly generated [drawn mask](../darkroom/masking-and-blending/masks/drawn.md) brush strokes. You can control the brush width, hardness and opacity. “Absolute” control means that the pressure reading directly defines the attribute with a value between 0% and 100%. “Relative” means that the pressure reading adjusts the attribute between zero and the pre-defined default value (default off).

lissage du pinceau
: Définit le niveau de lissage des traits de pinceau du [masque dessiné](../darkroom/masking-and-blending/masks/drawn.md). Un lissage plus fort entraîne moins de nœuds et une édition plus facile au détriment d'une précision moindre.

format de la ligne d'information sur l'image
: Définit les informations à afficher dans [ligne d'information de l'image](../module-reference/utility-modules/darkroom/image-info-line.md). Vous pouvez utiliser toute variable définie dans la section [substitution de variable](../special-topics/variables.md) ainsi que `$(NL)` pour une nouvelle ligne.

position of the image information line
: Choose the darkroom panel in which the [image information line](../module-reference/utility-modules/darkroom/image-info-line.md) is displayed. Choose between “top left” “top right” “top center” “bottom” and “hidden” (default "bottom").

bordure autour de l'image dans la vue chambre noire
: Traiter l'image centrale en mode chambre noire avec une bordure du nombre de pixels donné (par défaut 20). 

affiche les barres de défilement de la zone centrale
: Définit si les barres de défilement doivent être affichées dans la vue centrale de la chambre noire (désactivé par défaut).

méthode de dématriçage pour la vue chambre noire
: Choisir la méthode pour dématricer les images de la vue chambre noire qui ne sont pas affichées à l'échelle de zoom 1:1
: - _toujours bilinéaire (rapide)_ est la plus rapide, mais donne des résultats peu netste
: - _au mieux PPG (raisonnable)_ utilise PPG plus les modes d'interpolation
: - _full (possibly slow)_ utilise exactement les paramètres définis pour l'exportation en taille réelle
: (par défaut "_au mieux PPG (raisonnable)_"). 

réduire la résolution de la pré-visualisation
: Réduire la résolution de l'image de [prévisualisation dans la navigation](../module-reference/utility-modules/darkroom/navigation.md) (choisir la taille entre "original", "1/2", "1/3" ou "1/4"). Cela peut améliorer la vitesse du rendu, mais attention car cela peut également gêner la sélection précise des couleurs et le masquage ("original" par défaut).

affichage des boutons sur la droite des modules de développement
: Choisissez d'afficher les trois boutons (instances multiples, réinitialiser, préréglages) sur le côté droit [de l'entête](../darkroom/interacting-with-modules/module-header.md) des modules de traitement. Ces boutons apparaîtront toujours lorsque la souris survolera le module. D'autres fois, ils seront affichés ou masqués selon le choix fait entre :
: - _toujours_ : toujours afficher tous les boutons,
: - _actif_ : n'afficher les boutons que lorsque la souris est au-dessus du module,
: - _atténué_ : les boutons sont grisés lorsque la souris est éloignée,
: - _auto_ : masquer les boutons lorsque le panneau est étroit,
: - _estompé_ : atténuer tous les boutons quand le panneau est étroit,
: - _ajusté_ : masquer tous les boutons si le nom du module n'a pas assez de place,
: - _doux_ : atténuer tous les boutons d'un module simultanément,
: - _glisser_ : cacher progressivement les boutons lorsque nécessaire.
: (par défault _toujours_).

show loading screen between images
: Show gray loading screen when navigating between images in the darkroom. Switch this option off to just show a simple toast message and leave the previous image in place until the next image is loaded. Note that switching this option off can be very useful to quickly compare duplicate images, however, there might be issues with long loading times (leading you to think the next image has already loaded) and you may observe visual artifacts while the next image is loading (default on).

# modules

display of individual color channels
: Controls how individual color channels are displayed when activated in the [parametric masks](../darkroom/masking-and-blending/masks/parametric.md) feature. You can choose between “false color” and “gray scale” (default "false color").

cacher les préréglages internes des modules de développement
: Si cette option est activée, seuls les préréglages définis par l'utilisateur seront affichés dans le menu des préréglages pour le traitement des modules -- les préréglages intégrés seront masqués (désactivée par défaut).

déplier un seul module de développement à la fois
: Contrôle comment sont dépliés les [modules de développement](../module-reference/processing-modules) dans la chambre noire. Si cette option est activée, développer un module en cliquant dessus replie tout module actuellement déplié. Si vous souhaitez déplier un module sans replier les autres, vous pouvez le faire avec Maj+clic. La désactivation de cette option inverse la signification de Clic et Maj+clic (activé par défaut).

replier les modules du groupe actuel seulement
: Lorsque vous choisissez de déplier un seul module de développement à la fois (en utilisant la logique définie dans le paramètre précédent), ne replie que les autres modules apparaissant dans le groupe visible actuel. Désactivez cette option pour vous assurer que les modules des groupes non visibles sont également repliés (activé par défaut).

déplier le module quand il est activé, et le replier quand il est désactivé
: Sélectionnez cette option pour que darktable déplie ou replie automatiquement [les modules de développemnt](../module-reference/processing-modules) selon qu'ils sont activés ou désactivés (désactivée par défaut)

positionne les modules de développement lorsqu'ils sont dépliés/repliés
: Lorsque cette option est activée darktable essaiera de positionner un [module de développement](../module-reference/processing-modules) pour qu'il soit entièrement visible (activée par défaut).

couleurs du curseur de balance des blancs
: Contrôle l'apparence des curseurs dans le module [balance des blancs](../module-reference/processing-modules/white-balance.md).
: - _sans couleur_ : l'arrière-plan des curseurs n'est pas du tout coloré,
: - _couleur de l'illuminant_ : les couleurs du curseur représentent la couleur de la source lumineuse, c'est-à-dire la couleur que vous ajustez pour obtenir un blanc neutre,
: - _effet d'émulation_ : les couleurs du curseur représentent l'effet que l'ajustement aurait eu sur la scène. C'est ainsi que la plupart des autres processeurs de fichiers raw affichent les couleurs des curseurs de température/teinte.
: (_sans couleur_ par défaut)

disposition des contrôles du module balance couleur
: Contrôle l'apparence des sections ombres/tons moyens/hautes lumières dans le module [balance couleur](../module-reference/processing-modules/color-balance.md).
: - _liste_ : tous les curseurs sont affichés dans une longue liste (avec en-têtes),
: - _onglets_ : utiliser les onglets pour basculer entre les blocs de curseurs,
: - _colonnes_ : les blocs de curseurs sont affichés les uns à côté des autres (dans des colonnes étroites).
: (_liste_ par défaut)

show mask indicator in module headers
: If enabled, an icon will be shown in the header of any processing modules that have a [mask](../darkroom/masking-and-blending/masks/_index.md) applied (default on).
