---
author: people
draft: 'false'
id: still-doesnt-work
title: 'opencl ne fonctionne toujours pas pour moi'
weight: 100
---

Comme nous l’avons dit précédemment, les systèmes OpenCL possèdent une énorme variété de configurations : différents fabricants de GPU, différents modèles de GPU, une quantité de mémoire variable pour le GPU, différents pilotes, différentes distributions, etc. 

Beaucoup des problèmes potentiels n'apparaîtront qu'avec une combinaison spécifique de ces facteurs. Comme les développeurs de darktable ont seulement accès à un nombre limité de ces variantes, comprenez que nous pouvons ne pas être à même de résoudre votre problème spécifique. Nous ne pouvons pas y faire grand chose s’il n'y a aucun moyen pour nous de le reproduire.

Si rien d’autre ne peut aider, la meilleure option est de démarrer darktable par

`darktable --disable-opencl`

Enfin, il n'y a rien dans darktable qui ne tourne que sur un GPU. Ne laissez pas OpenCL vous décourager -- le code CPU de darktable est fortement optimisé pour les performances !
