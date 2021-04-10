---
draft: 'false'
id: history-stack
title: "l'historique"
weight: 30
---

L'_historique_ stocke l'intégralité de l'historique de développement pour une image donnée, dans l'ordre dans lequel les modifications ont été appliquées. Il est enregistré dans la base de données de la bibliothèque de darktable et dans le fichier lié XMP de l'image et persiste entre les sessions d'édition.

Chaque fois qu'un module de traitement est activé, désactivé, déplacé ou modifié, une nouvelle entrée est ajoutée en haut de l'_historique_. 

L’historique peut être consulté et modifié dans le module [historique](../../../module-reference/utility-modules/darkroom/history-stack.md) de la chambre noire.

---

**Remarque :** L'historique n'est pas une représentation de l'ordre dans lequel les modules sont **exécutés** mais une représentation de l'ordre dans lequel ils ont été **activés**. L'ordre d'exécution est représenté par l'ordre des modules dans le panneau de droite.

---
