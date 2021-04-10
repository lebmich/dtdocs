---
draft: 'false'
id: general
title: général
weight: 20
---

Les préférences de cet onglet contrôlent l'aspect général de darktable.

langue pour l'interface
: Définissez la langue de l'interface utilisateur. La valeur par défaut du système est marquée d'un * (nécessite un redémarrage)

theme
: Set the theme for the user interface. Apart from any aesthetic considerations, the recommended interface color for color evaluation is middle gray. Indeed, visual perception is affected by ambient brightness, and a low brightness of the interface causes all kinds of illusions. Using a dark interface to retouch photos can therefore lead to excessive retouching (abuse of contrast and saturation) and to a photo that is too dark once printed. It is therefore highly recommended that you use one of the "gray" themes for retouching work as these are designed so that the user interface approximates middle gray (default "darktable").

favoriser la performance à la qualité
: Activez cette option pour afficher les miniatures et les aperçus avec une qualité inférieure. Cela augmente la vitesse de rendu d'un facteur 4, et est utile lorsque vous travaillez sur des ordinateurs plus lents (désactivé par défaut). Cela améliore également les performances du rendu d'image du diaporama.

utiliser la taille de la police système
: Sélectionnez cette option pour utiliser la taille de police définie par votre système. Si elle n'est pas cochée, vous pouvez saisir une taille de police personnalisée dans la case ci-dessous (activée par défaut).

taille de la police en points
: Si l'option «utiliser la taille de la police système» est désactivée, entrez une taille de police (en points) que darktable doit utiliser. La taille de la police sera modifiée immédiatement.

contrôles et texte DPI
: Ajustez la résolution globale de l'interface graphique pour redimensionner les contrôles, les boutons, les étiquettes, etc. Augmentez pour une interface graphique agrandie, diminuez pour ajuster plus de contenu dans la fenêtre. Défini sur -1 pour utiliser la résolution globale définie par le système. La valeur par défaut est 96 PPP sur la plupart des systèmes. (nécessite un redémarrage)

# modifier le thème via les ajustements CSS ci-dessous

En plus de sélectionner un thème pré-construit vous pouvez également appliquer vos propres personnalisations CSS pour modifier l'aspect général de darktable. Une zone de saisie de texte est prévue à cet effet.

Lorsque vous avez terminé de saisir vos modifications CSS, cliquez sur le bouton «sauvegarder et appliquer». Cela enregistrera votre CSS dans un fichier (`$HOME/.config/darktable/user.css`) et l'appliquera immédiatement à la session actuelle de darktable.

Si vos modifications posent des problèmes, vous pouvez décocher la case "modifier le thème via les ajustements CSS ci-dessous". Cela restaurera immédiatement le thème de base, mais laissera vos réglages dans l'éditeur afin que vous puissiez rééditer et réessayer. Appuyez simplement sur "sauvegarder et appliquer" à nouveau lorsque vous êtes prêt à réessayer. Cela revérifiera automatiquement la case à cocher "modifier le thème via les ajustements CSS ci-dessous" et appliquera le nouveau CSS.

Si vous rencontrez des problèmes avec darktable, veuillez réessayer avec cette option décochée pour être certain qu'ils n'ont été causés par l'une de vos modifications.
