---
draft: 'false'
id: miscellaneous
title: divers
weight: 110
---

# interface

trier les préréglages internes en premier
: Choisir comment le menu des préréglages est trié. Si cette option est activée, les préréglages internes sont montrés en premier. Si cette option est désactivée, les préréglages de l'utilisateur sont montrés en premier (activée par défaut).

déplacement des panneaux latéraux avec la molette
: Lorsqu'elle est activée, par défaut, la molette de la souris fait défiler les panneaux latéraux et Ctrl+Alt+molette fait défiler les champs de saisie de données. Lorsqu'elle est désactivée, ce comportement est inversé (désactivée par défaut) 

toujours montrer les ascenseurs des panneaux
: Définit si les barres de défilement du panneau doivent être toujours visibles ou activées uniquement en fonction du contenu du panneau (activé par défaut). (nécessite un redémarrage) 

method to use for getting the display profile
: This option allows the user to force darktable to use a specific method to obtain the current display profile for [color management](../special-topics/color-management/_index.md). In the default setting “all”, darktable will choose to query the X display server's xatom or the colord system service. You can set this option to “xatom” or “colord” to enforce a specific method if the two methods give different results. You can run the [darktable-cmstest](../special-topics/program-invocation/darktable-cmstest.md) binary to examine your color management subsystem.

# mots clés

ignorer la hiérarchie des mots-clés
: Lors de l'exportation d'images, les mots-clés hiérarchiques sont également ajoutés sous la forme d'une simple liste de mots-clés non hiérarchiques pour les rendre visibles par d'autres programmes. Lorsque cette option est cochée, darktable n'inclura que la dernière partie de la hiérarchie et ignorera le reste. Donc `foo | bar | baz` ajoutera seulement` baz` 

désactiver l'auto-complétion
: l'auto-complétion est utile pour ceux qui saisissent des mots-clés uniquement au clavier. Pour les autres, l'auto-complétion peut être embarrassante (désactivée par défaut). (nécessite un redémarrage) 

# raccourcis clavier avec instances multiples

Il est possible de créer plusieurs instances de nombreux modules de traitement. Dans ce scénario, il n'est pas toujours évident de savoir quelle instance doit être contrôlée par des opérations de raccourci clavier. Les options suivantes contrôlent les règles qui sont appliquées (dans l'ordre) pour décider à quelle instance les raccourcis clavier doivent être appliqués.

Ces règles sont également utilisées lorsque, pour modifier l'exposition, vous cliquez et faites glisser sur l'histogramme.

préférence aux instances développées
: si des instances du module sont dépliées, ignore les instances repliées (désactivée par défaut).

préférence aux instances actives
: Après avoir appliqué la règle ci-dessus, si les instances restantes du module sont actives, ignorez les instances inactives (désactivée par défaut).

préférence aux instances visibles
: Après avoir appliqué les règles ci-dessus, si les instances restantes du module sont visibles, ignorez les instances cachées (désactivée par défaut).

ordre de sélection
: Après avoir appliqué les règles ci-dessus, appliquez le raccourci à la première ou à la dernière instance restante ("dernière instance" par défaut).

# autre

ne pas afficher le jeu du 1er avril
: Ne pas afficher de jeu lors de l'ouverture de darktable le 1er avril (activé par défaut). 

password storage backend to use
: The backend to use for password storage. Options: “auto” (default), “none”, “libsecret”, “kwallet”. 

executable for playing audio files
: Define an external program which is used in the lighttable view to play audio files that some cameras record to keep notes for images (default “aplay”). 
