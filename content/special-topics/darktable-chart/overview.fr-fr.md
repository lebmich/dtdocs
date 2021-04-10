---
author: people
draft: 'false'
id: overview
title: présentation
weight: 10
---

`darktable-chart` est un outil pour extraire les valeurs de clarté et de couleurs d'une image. Ces valeurs sont prises dans des cartes de référence couleur comme les chartes IT8.7 / 1. Le but principal de ce module est de comparer une image source (typiquement une image RAW non traitée) à une image cible (typiquement une image JPEG créée par le boîtier) et de créer un style darktable capable de convertir les valeurs de clarté et de couleur de l'image source pour produire l'image cible. Ce style utilise pour cela les modules [_courbe des tonalités_](../../module-reference/processing-modules/tone-curve.md), [_profil couleur d'entrée_](../../module-reference/processing-modules/input-color-profile.md) et [_table correspondance couleurs_](../../module-reference/processing-modules/color-look-up-table.md).

Certains boîtiers mettent à votre disposition divers modes de simulation de film. Avec l'aide du module `darktable-chart` et des modules sous-jacents, vous pouvez maintenant créer des styles qui reproduisent ces simulations de film.
