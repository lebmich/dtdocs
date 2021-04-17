---
draft: 'false'
id: overview
title: présentation
weight: 10
---

Par défaut, un module reçoit son entrée du module le précédant dans le pipeline graphique, il effectue ses calculs et envoie sa sortie au module le suivant dans le pipeline graphique. 

Les données de sortie d'un module peuvent optionnellement être retraitée (combinées) avec son entrée avant que le résultat soit passé au module suivant. Ce traitement supplémentaire est appelé _fusion_. Entrée et sortie peuvent être traitées avec différents algorithmes, appelés opérateurs de fusion ou [modes de fusion](./blend-modes.md).

Chaque mode de fusion est en outre contrôlé par un paramètre appelé _opacité_ qui peut avoir une valeur comprise entre 0% et 100% et qui définit la manière dont les images d’entrée et de sortie contribuent au résultat final. Typiquement, une valeur d’opacité égale à 0% produit une image identique à l’image d’entrée -- le module n’a pas d’effet. Une valeur d’opacité égale à 100% délivre le maximum de l’effet du module pour le mode de fusion choisi.

L'opacité peut être la même pour chaque pixel de l'image (en combinant simplement un mode de fusion avec le curseur d'opacité unique) -- dans ce cas, la fusion agit de manière uniforme sur toute l'image. Les valeurs d'opacité peuvent également varier en fonction des propriétés ou de l'emplacement de chaque pixel. Cette modification locale de l'opacité est appelée un _masque_. Les masques fournissent à l'utilisateur un contrôle précis sur les parties d'une image qui sont affectées par un module et dans quelle mesure. Vous pouvez choisir d'activer un [masque dessiné](./masks/drawn.md), un [masque paramétrique](./masks/parametric.md) ou une [combinaison des deux](./masks/drawn-and-parametric.md). 

La fonctionnalité de fusion et de masquage est contrôlée via un groupe d'icônes situé au bas de chaque module où elle est applicable. 

![options de masquage et de fusion](./overview/mask-blend-options.png#w33)

Ces icônes activent les options de masquage et de fusion suivantes, de gauche à droite :

désactivé
: La sortie du module est transmise au module suivant dans le pipeline graphique sans retraitement supplémentaire. Aucun autre contrôle n'est affiché. 

uniformly
: Input and output images are reprocessed to the same extent for all pixels with the extent of the blending controlled by a single opacity slider. Additional controls to choose the blend mode and opacity are displayed. The default blend mode is “normal” with an opacity of 100%.

[masque dessiné](./masks/drawn.md)
: Le retraitement a lieu avec le mode de fusion et l'opacité choisie en fonction de l'emplacement des pixels dans un masque dessiné. Des contrôles supplémentaires s'affichent pour vous permettre de dessiner un masque en utilisant une ou plusieurs formes. Si aucun élément de masque n'est dessiné, tous les pixels ont la même opacité, celle que définit le curseur d'opacité.

[masque paramétrique](./masks/parametric.md)
: Le retraitement a lieu avec le mode de fusion et l'opacité choisie en fonction de l'emplacement des pixels dans un masque paramétrique. Des contrôles supplémentaires s'affichent pour vous permettre de définir un masque paramétrique à l'aide de propriétés des pixels.

[masque dessiné et paramétrique](./masks/drawn-and-parametric.md)
: Le retraitement a lieu avec le mode de fusion et l'opacité choisie en fonction d'une combinaison d'un masque paramétrique et d'un masque dessiné.

[masque raster](./masks/raster.md)
: Le retraitement a lieu avec le mode de fusion et l'opacité choisie en fonction d'un masque qui a été généré dans un module différent

options de fusion
: Choisissez l'espace colorimétrique à utiliser lors du calcul du masque de fusion et spécifiez si vous souhaitez autoriser ou non la génération d'un masque en fonction des canaux de sortie du module (normalement, un masque paramétrique est généré en fonction des canaux d'entrée entrant dans le module). Les options suivantes sont disponibles :
: - _réinitialiser à par défaut l'espace de couleurs de fusion_ : Utiliser l'espace de couleurs par défaut du module pour spécifier le masque paramétrique.
: - _Lab_ : utiliser l'espace colorimétrique Lab (s'il est disponible) lors de la spécification du masque paramétrique.
: - _RVB (affichage)_ : utiliser l'espace colorimétrique RVB/TSL relatif à l'affichage pour spécifier le masque paramétrique.
: - _RVB (scène)_ : utiliser l'espace colorimétrique RVB / J <sub> z </sub> C <sub> z </sub> h <sub> z </sub> relatif à la scène pour spécifier le masque paramétrique.
: - _afficher les canaux de sortie_ : Afficher les contrôles des canaux de sortie afin que le [masque paramétrique](./masks/parametric.md) puisse être défini en fonction des canaux de sortie du module.

---

**Remarque :** Toutes ces options de fusion ne sont pas disponibles pour chaque module.

---

