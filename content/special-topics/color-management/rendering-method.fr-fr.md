---
author: people
draft: 'false'
id: rendering-method
title: 'méthode de rendu'
weight: 30
---

darktable peut rendre les couleurs soit avec ses algorithmes internes, soit en utilisant la bibliothèque externe LittleCMS2. La méthode interne de darktable est plus rapide, d'un ordre de grandeur, que la méthode externe. L'option externe vous donne le choix de l'intention rendu et peut offrir une précision légèrement supérieure dans certains cas.

Vous pouvez changer la méthode par défaut dans [préférences> traitement>toujours utiliser LittleCMS 2 pour le profil de couleur de sortie](../../preferences-settings/processing.md)

---

** Remarque : ** Si l'ICC donné est basé sur une LUT ou contient à la fois une LUT et une matrice, darktable utilisera LittleCMS2 pour rendre les couleurs quelle que soit la valeur du paramètre de configuration.

---
