---
title: stockage
id: storage
weight: 100
draft: false
author: "traducteur : Michel Leblond"
---

Les options suivantes sont relatives à la base de données de darktable et aux [fichiers liés XMP](../overview/sidecar-files/_index.md).

# base de données

vérifier pour la maintenance de la base de données
:  Indique quand darktable doit vérifier la fragmentation de la base de données et effectuer la maintenance. Les options sont "jamais", "au démarrage", "à la fermeture", et "au deux". Chacun de ceux-ci est également disponible avec une option supplémentaire "(sans confirmation)" pour effectuer les vérifications automatiquement et sans invite (par défaut "à la fermeture").

seuil de fragmentation de la base de données
: Taux de fragmentation (en pourcentage) au-dessus duquel la maintenance de la base de données doit être effectuée (sous réserve de la sélection effectuée dans l'option ci-dessus) (par défaut 25).

faire une sauvegarde de la base de données
: Spécifie la fréquence des sauvegardes de la base de données. Les options sont «jamais», «une fois par mois», «une fois par semaine», «une fois par jour» et «à la fermeture» (par défaut «une fois par semaine»)

nombre de sauvegarde à conserver
: Nombre de sauvegardes à conserver après la création d'une nouvelle sauvegarde, sans compter les sauvegardes de base de données effectuées lors du passage d'une version de darktable à une autre. Entrez "-1" pour stocker un nombre illimité de sauvegardes. (par défaut 10)

# xmp

écrire un fichier XMP redondant pour chaque image
: Les fichiers XMP fournissent une méthode redondante pour enregistrer les modifications que vous avez apportées à une image, indépendamment de la base de données de darktable. Les fichiers XMP peuvent être réimportés ultérieurement dans une autre base de données, en préservant les modifications apportées à l'image. Il est fortement recommandé de laisser cette option activée afin de ne pas perdre de données si votre base de données est corrompue. La sauvegarde de votre fichier RAW et du fichier XMP qui l'accompagne vous permettra de restaurer complètement votre travail (activé par défaut).

enregistre les mots-clés xmp avec un format compressé
: Les données des mots-clés XMP peuvent devenir assez volumineuses et peuvent dépasser l'espace disponible pour stocker l'historique de développement dans des fichiers lors de l'exportation. Cette option permet de compresser les mots-clés XMP binaires afin d'économiser de l'espace. Les options disponibles sont «jamais», «toujours» et «seulement les grands» (par défaut).

vérifie au démarrage les fichiers xmp modifiés
: Analyser tous les fichiers XMP au démarrage et vérifier s'ils ont été modifiés entre-temps par un autre logiciel. Si des fichiers XMP modifiés sont trouvés, un menu s'ouvre pour que l'utilisateur choisisse les fichiers XMP qu'il faut recharger (en remplaçant les entrées de la base de données de darktable par le contenu du fichier XMP) et ceux qu'il faut écraser à partir de la base de données de darktable. L'activation de cette option amène également darktable à rechercher les fichiers liés XMP qui ont été ajoutés après l'importation - voir [préférences > table lumineuse > overlay txt sidecar over zoomed images](./lighttable.md) (désactivé par défaut).
