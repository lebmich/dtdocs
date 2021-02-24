---
title: général
id: general
weight: 20
draft: false
author: "traducteur : Michel Leblond"
---

Les préférences de cet onglet contrôlent l'aspect général de darktable.

langue pour l'interface
: Définissez la langue de l'interface utilisateur. La valeur par défaut du système est marquée d'un * (nécessite un redémarrage)

thème
: Définissez le thème de l'interface utilisateur. Indépendamment de toute considération esthétique, la couleur d'interface recommandée pour l'évaluation des couleurs est le gris moyen. En effet, la perception visuelle est affectée par la luminosité ambiante, et une faible luminosité de l'interface provoque toutes sortes d'illusions. Utiliser une interface sombre pour retoucher les photos peut donc conduire à des retouches excessives (abus de contraste et de saturation) et à une photo trop sombre une fois imprimée. Il est donc fortement recommandé d'utiliser l'un des thèmes "gris" pour les travaux de retouche car ils sont conçus pour que l'interface utilisateur se rapproche du gris moyen ("darktable" par défaut).

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
