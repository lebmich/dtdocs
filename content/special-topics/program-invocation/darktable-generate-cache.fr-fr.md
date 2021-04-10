---
author: people
draft: 'false'
id: darktable-generate-cache
title: darktable-generate-cache
weight: 30
---

L'exécutable `darktable-generate-cache` met à jour le cache des miniatures. Vous pouvez lancer ce programme, en arrière-plan quand votre ordinateur est inactif, pour générer toutes les miniatures manquantes .

`darktable-generate-cache` est appelé avec les paramètres suivants de la ligne de commande :

```
darktable-generate-cache
              [-h, --help]
              [--version]
              [--min-mip <0-7>] [-m, --max-mip <0 - 7>]
              [--min-imgid <N>] [--max-imgid <N>]
              [--core <darktable options>]
```

Tous les paramètres sont optionnels. S'il est démarré sans paramètre `darktable-generate-cache` utilise des valeurs par défaut raisonnables.

`-h, --help`
: Donne des informations d'utilisation et s'arrête.

`--version`
: Donne des informations de version et de copyright et s'arrête.

`--min-mip <0 - 7>, -m, --max-mip <0 - 7>`
: darktable peut gérer et stocker, pour chaque image, des miniatures ayant jusqu'à huit niveaux différents de résolution. Ces paramètres définissent la résolution maximale qui doit être générée (valeur par défaut dans une plage de 0 à 2). Il n'est normalement pas nécessaire de générer ici toutes les résolutions possibles ; celles qui manquent seront générées automatiquement par darktable au moment où elles seront nécessaires. Quand on demande la génération de plusieurs résolutions à la fois, les images de plus basse résolution sont rapidement sous-échantillonnées à partir de l'image de la plus haute résolution.

`--min-imgid <N>, --max-imgid <N>`
: Spécifie la plage d'IDs des images de la base de données sur laquelle il faut travailler. Si aucune plage n'est donnée, `darktable-generate-cache` générera le cache de toutes les images de la collection.

`--core <darktable options>`
: Tous les paramètres de la ligne de commande suivant `--core` sont passés au noyau de darktable et manipulés comme des paramètres standards. Voir la section [Exécutable darktable](./darktable.md) pour une description détaillée.

