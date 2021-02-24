---
title: importation, évaluation et labels de couleur
id: import-rate-tag
draft: false
weight: 10
author: "traducteur : Michel Leblond"
---

Quand vous souhaitez développer de nouvelles images dans darktable, la première étape est de les [importer](../../module-reference/utility-modules/lighttable/import.md). Ceci créera des entrées pour les nouvelles images importées dans la base de données de darktable. Il pourra ainsi suivre les modifications que vous leurs apporterez. Il existe deux méthodes principales pour importer des images :

importer des images depuis le système de fichiers
: Vous pouvez importer depuis le système de fichier une seule image ou un dossier contenant des images (optionnellement importer les dossiers récursivement). Quand il importe des images, darktable lit les métadonnées qu'elles contiennent et tous les [fichiers liés xmp](../../overview/sidecar-files/_index.md) qui, éventuellement, les accompagnent. Si une image a déjà été importée, elle sera ignorée (bien que toute mise à jour du fichier lié sera chargée). L'emplacement de chaque image est enregistré dans la base de données, mais darktable ne copiera ni ne déplacera les fichiers. Si vous souhaitez un programme qui copie des fichiers dans un dossier spécifique, vous pouvez utiliser un programme comme [rapid photo downloader](https://damonlynch.net/rapid/) pour faire cela.

importer des images depuis un boîtier
: Pour importer des images depuis un boîtier, connectez tout d'abord votre boîtier à votre système avec un câble USB. Si votre système essaie de monter automatiquement les fichiers du boîtier, vous devez interrompre cette opération, sinon le boîtier ne sera pas accessible depuis darktable. Si votre boîtier n'apparaît pas dans la liste du module importation, presser le bouton "chercher un appareil". Une fois votre appareil photo détecté, le module d'importation devrait offrir la possibilité d'_importer_ des images ou de _capturer_ votre appareil photo pendant la prise de vue. Contrairement à l'importation d'images à partir du système de fichiers, darktable copiera physiquement les fichiers importés du boîtier dans un répertoire spécifié en suivant le modèle de dénomination de fichier défini dans [préférences > importer](../../preferences-settings/import.md).

Une fois les images importées, elles apparaîtront dans la vue table lumineuse. Par défaut, les images recevront toutes une note d'une étoile.

Il existe de nombreuses façons de gérer un ensemble de photos récemment importées, par exemple en leur attribuant des labels et en ajustant leurs évaluations. Veuillez vous référer à la section [lighttable](../../lighttable/_index.md) de ce guide pour une liste exhaustive des fonctionnalités de _gestion des acquisitions numériques_.

Un exemple de flux de travail pourrait être :
1. Réglez la vue table lumineuse pour afficher les photos avec exactement une note de 1 étoile.
2. Effectuez une première visualisation rapide de vos photos. Si des photos sont très floues ou inutiles, rejetez-les avec la touche R ou attribuez-leur une note de 0 étoile. Si une photo semble raisonnable et doit passer à la phase suivante, appuyez sur 2 pour lui attribuer une note de 2 étoiles. Toutes les photos qui ne sont plus classées 1 étoile disparaîtront automatiquement de la vue. Continuez de cette manière jusqu'à ce que vous ayez terminé le premier niveau d'évaluation.
3. Réglez maintenant la vue de la table lumineuse pour n'afficher que les photos avec exactement une note de 2 étoiles. Parcourez ces photos plus attentivement et décidez si vous souhaitez les promouvoir avec une note de 3 étoiles, ou leur redonner une note de 1 étoile ou les rejeter.
4. Vous pouvez maintenant passer du temps à effectuer un développement rapide de vos photos 3 étoiles, pour voir si elles valent la peine d'être conservées. Si vous êtes satisfait des résultats pour une photo, vous pouvez créer un label pour elle et la promouvoir avec une note de 4 ou même 5 étoiles.
5. Parcourez vos photos 4 et 5 étoiles, effectuez les derniers développements. Imprimez-les, publiez-les sur le site de votre portfolio, etc. et appréciez les nombreuses acclamations critiques que vous recevrez !
6. Si votre espace disque est limité, vous envisagerez peut-être de supprimer définitivement vos images rejetées ou notées 0 étoiles. Sélectionnez ces images dans la vue table lumineuse et utilisez l'option «corbeille» dans l'onglet [images sélectionnées](../../module-reference/utility-modules/lighttable/selected-image.md). Vous ne devriez probablement le faire que pour des photos dont vous êtes certain de ne plus jamais avoir besoin (mal mises au point, significativement surexposées, etc.).
