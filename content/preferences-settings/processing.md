---
title: traitement
id: processing
weight: 70
draft: false
author: "traducteur : Michel Leblond"
---

Les options suivantes contrôlent le traitement des images.

toujours utiliser LittleCMS 2 pour le profile couleur de sortie
: Si cette option est activée, darktable utilisera la bibliothèque système LittleCMS 2 pour appliquer le profil couleur de sortie au lieu de ses propres routines internes. Ceci est nettement plus lent que la valeur par défaut, mais peut donner des résultats plus précis dans certains cas.
: Si l'ICC donné est basé sur une LUT ou contient à la fois une LUT et une matrice, darktable utilisera LittleCMS 2 pour rendre les couleurs quelle que soit la valeur de ce paramètre de configuration (désactivé par défaut).

algorithme d'interpolation
: L'algorithme utilisé pour la rotation, la correction des objectifs, l'augmentation et la réduction d'échelle. Les options sont “bilinéaire”, “bicubique”, “lanczos2”, “lanczos3” (par défaut).

répertoire 3D lut racine
: Définir le répertoire racine (et les sous-répertoires) contenant les fichiers Lut utilisés par le module [_lut 3D_](../module-reference/processing-modules/lut-3D.md).

appliquer l'adaptation chromatique par défaut
: Choisissez le module chargé d'effectuer les ajustements de balance des blancs (adaptation chromatique) par défaut. Sélectionnez "originel" (par défaut) pour effectuer une adaptation chromatique de base en utilisant uniquement le module [_balance des blancs_](../module-reference/processing-modules/white-balance.md). Sélectionnez "moderne" pour utiliser une combinaison des modules _balance des blancs_ et [_calibration des couleurs_](../module-reference/processing-modules/color-calibration.md) pour effectuer une adaptation chromatique moderne avec une science des couleurs améliorée. Ces paramètres sont appliqués par défaut aux nouveaux développements et n'auront aucun impact sur les anciens.

flux de travail par défaut appliqué automatiquement
: Choisissez les modules et l'ordre des modules à appliquer par défaut aux nouvelles images :

- _relatif à la scène_ est le flux de travail basé sur des modules RVB linéaires. Sélectionner cette option activera automatiquement les modules [_filmique rvb_](../module-reference/processing-modules/filmic-rgb.md) et [_exposition_](../module-reference/processing-modules/exposure.md). L'ordre d'application des modules sera alors celui qui a été défini pour darktable à partir de la version 3.0.

  Le module _exposition_ ajoutera automatiquement +0,5 IL à l'exposition pour que le gris moyen corresponde à celui de la majorité des appareils photo SLR. Cet ajout peut être remplacé par un préréglage appliqué automatiquement si cette valeur par défaut produit constamment des images sombres pour votre appareil.

  Enfin, ce paramètre active automatiquement l'option «compenser exposition boîtier» dans le module _exposition_ pour ajuster la luminosité globale de manière appropriée quand la molette de compensation d'exposition du boîtier a été utilisée pour protéger les hautes lumières de l'image ou quand l'option "Exposez à droite (ETTR)" a été sélectionnée lors de la prise de vue pour utiliser de façon optimale la plage dynamique du capteur.

- _relatif à l'affichage_ (par défaut) est le flux de travail basé sur des modules Lab. C’est le flux de travail originel de darktable jusqu'à la version 2.6. Sélectionner cette option activera automatiquement le module [_courbe de base_](../module-reference/processing-modules/base-curve.md). L'ordre d'application des modules dans le pipeline graphique sera alors celui qui était utilisé par défaut jusqu'à la version 2.6.

- _aucun_ n'activera aucun module par défaut et l'ordre d'application des modules dans le pipeline graphique sera celui défini pour darktable à partir de la version 3.0 (relatif à la scène).

applique le préréglage de la courbe de base pour le boîtier
: Applique la courbe de base spécifique au boîtier à la place de celle, générique à la marque, si elle est disponible. Cela ne doit être utilisé qu'en conjonction avec le flux de travail _relatif à l'affichage_ défini ci-dessus (désactivé par défaut).

applique automatiquement de la netteté
: Appliquer automatiquement le module netteté aux nouvelles images. Cette option n'est pas recommandée pour les boîtiers n'ayant pas de filtre passe-bas. (activé par défaut, nécessite un redémarrage si modifié).

détecter les miniatures monochromes
: Activez cette option pour analyser les images lors de l'importation et les étiqueter avec le mot-clé `chambre noire|mode|monochrome` si elles sont monochromes. L'analyse est basée sur l'aperçu intégré dans le fichier importé. Cela permet un flux de travail plus pratique lorsque vous travaillez avec des images monochromes, mais cela ralentit l'importation, ce paramètre est donc désactivé par défaut.
