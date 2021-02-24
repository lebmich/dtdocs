---
title: table lumineuse
id: lighttable
weight: 40
draft: false
author: "traducteur : Michel Leblond"
---

Les options suivantes contrôlent les fonctionnalités de la vue [table lumineuse](../lighttable/_index.md).

# général

nombre de niveaux de dossiers à afficher
: Le nombre de niveaux de dossier à afficher dans les noms de pellicule, en partant de la droite (par défaut 1).

trier les pellicules par
: Trier les pellicules par "dossier" (chemin) ou "numéro" (à peu près équivalent à la date à laquelle les pellicules ont été importées pour la première fois) dans le module [filtres de collection](../module-reference/utility-modules/shared/collect-images.md) module (par défaut "numéro").

trier les collections de la plus récente à la plus ancienne
: Lors de la sélection des dossiers et des dates/heures dans le module [filtres de collection](../module-reference/utility-modules/shared/collect-images.md), trier les éléments des plus récents aux plus anciens (par défaut activé).

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

ne pas utiliser les JPEG intégrés aux images, toujours utiliser les RAW réduits
: Si activé, darktable traitera les données RAW de l'image pour générer toutes les images de la table lumineuse. Si désactivé, darktable utilisera l'aperçu JPEG intégré dans le fichier RAW jusqu'à ce que l'image ait été traitée dans la chambre noire (désactivé par défaut).

miniatures de haute qualité à partir de la taille
: Si la taille de la miniature est plus grande que cette valeur, elle sera crée en utilisant le développement de haute qualité (meilleur mais plus lent) (par défaut 720p)

séparateurs de catégories des tailles
: Les catégories de taille permettent d'afficher différentes superpositions des miniatures en fonction de la taille des miniatures. Un ensemble de valeurs délimitées par  une barre verticale définit à quelles tailles d'image les catégories changent. La valeur par défaut "120|400" signifie qu'il y aura trois catégories de miniatures : 0-120px, 120-400px et> 400px.

patron pour les surimpressions des miniatures
: Si l'utilisateur a choisi de superposer aux miniatures le texte étendu, ce paramètre lui permet de définir les informations à afficher. Ce patron peut utiliser n'importe laquelle des variables définies dans la section [substitution de variable](../special-topics/variables.md).

patron pour les infos bulles des miniatures (vide pour désactiver)
: Définit les informations affichées dans l'info-bulle lorsque la souris survole les miniatures d'image. Ce patron peut utiliser n'importe laquelle des variables définies dans la section [substitution de variable](../special-topics/variables.md).
