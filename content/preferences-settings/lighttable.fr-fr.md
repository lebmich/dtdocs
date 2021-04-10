---
draft: 'false'
id: lighttable
title: 'table lumineuse'
weight: 40
---

Les options suivantes contrôlent les fonctionnalités de la vue et des modules de la [table lumineuse](../lighttable/_index.md).

# général

cacher les préréglages internes des modules utilitaires
: Si cette option est activée, seuls les préréglages définis par l'utilisateur seront affichés dans le menu des préréglages des modules utilitaires -- les préréglages intégrés seront masqués (par défaut désactivé).

utiliser un seul clic pour les collections
: Activer le mode "simple clic" dans le module [filtres de collection](../module-reference/utility-modules/shared/collect-images.md). Cela permet aussi de sélectionner des plages de dates et de valeurs numériques (désactivée par défaut).

déplier un seul module utilitaire de la table lumineuse à la fois
: Contrôle la façon dont les modules utilitaires sont dépliés. Si cette option est activée, déplier un module en cliquant dessus replie tout autre module actuellement déplié. Si vous souhaitez déplier un module sans replier les autres, vous pouvez le faire avec Maj+clic. La désactivation de cette option inverse la signification de Clic et de Maj+clic (désactivé par défaut).

positionne les modules utilitaires lorsqu'ils sont dépliés/repliés
: Lorsque cette option est activée darktable essaiera de positionner le module pour qu'il soit entièrement visible (désactivée par défaut).

appliquer une étoile deux fois à une image ne supprimera pas l'étoile
: Appliquer une étoile deux fois à une image ne positionnera aucune étoile (par défaut désactivé).

afficher les barres de défilement pour la zone centrale
: Si activé les barres de défilement seront affichées dans la zone centrale de la table lumineuse (activé par défaut).

# miniatures

miniatures avec gestion de la couleur
: Si activé, darktable génère les miniatures dans un espace colorimétrique général (AdobeRGB) afin de les rendre indépendamment du moniteur utilisé. La conversion vers l'espace colorimétrique du moniteur est effectuée au moment de l'affichage. Si cette option n'est pas activée, les miniatures sont stockées directement dans un espace colorimétrique spécifique au moniteur au moment de la génération et sont ensuite affichées sans autre correction (activé par défaut).

use raw file instead of embedded JPEG from size
: When generating thumbnails for images that have not yet been processed in the darkroom, if the thumbnail size is greater than this value, generate it by processing the raw image data. If the thumbnail is below this size, use the JPEG preview image embedded in the raw file. Once an image has been processed in the darkroom, thumbnails will always be generated from raw data (you can revert back to the JPEG preview by discarding history). To render thumbnails with the best quality choose "always".

high quality processing from size
: If the thumbnail size is greater than this value and is being generated from raw data, it will be processed using the full quality rendering path, which is better but slower (default 720p). To render thumbnails with the best quality, choose "always".

séparateurs de catégories des tailles
: Les catégories de taille permettent d'afficher différentes superpositions des miniatures en fonction de la taille des miniatures. Un ensemble de valeurs délimitées par une barre verticale définit à quelles tailles d'image les catégories changent. La valeur par défaut "120|400" signifie qu'il y aura trois catégories de miniatures : 0-120px, 120-400px et> 400px.

patron pour les surimpressions des miniatures
: Si l'utilisateur a choisi de superposer aux miniatures le texte étendu, ce paramètre lui permet de définir les informations à afficher. Ce patron peut utiliser n'importe laquelle des variables définies dans la section [substitution de variable](../special-topics/variables.md).

patron pour les infos bulles des miniatures (vide pour désactiver)
: Définit les informations affichées dans l'info-bulle lorsque la souris survole les miniatures d'image. Ce patron peut utiliser n'importe laquelle des variables définies dans la section [substitution de variable](../special-topics/variables.md).
