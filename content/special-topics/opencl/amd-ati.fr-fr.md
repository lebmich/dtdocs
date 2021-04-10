---
author: people
draft: 'false'
id: amd-ati
title: 'périphériques amd/ati'
weight: 60
---

Alors que les cartes NVIDIA et la plupart des cartes AMD/ATI modernes fonctionnent immédiatement la plupart du temps, il y a un peu plus de travail à faire pour les cartes graphiques AMD/ATI plus anciennes, c’est-à-dire celles avant les séries HD7xxx. Ceci commence avec le fait que ces cartes ne reportent à darktable qu’une partie de la mémoire totale du GPU. Pour un système possédant 1GB de mémoire, ceci donne typiquement une valeur de 512MB, une valeur que darktable refuse dans sa configuration standard parce qu'elle est insuffisante pour exécuter ses tâches. En conséquence le GPU ne sera pas utilisé.

Sur le web, vous trouverez peut-être une astuce indiquant de fixer la valeur de la variable d’environnement `GPU_MAX_HEAP_SIZE` à 100 dans ce cas. Bien entendu cela fera que le pilote AMD/ATI va signaler toute la mémoire installée à darktable. Cependant, il y a un problème. Sur de nombreuses (toutes ?) cartes, ceci va entraîner l’allocation des tampons sur votre ordinateur (hôte) et non sur la carte vidéo ! Dans ce cas, les accès mémoire auront besoin de passer par le bus PCI qui est lent. Ceci va vous coûter un facteur 10 ou davantage dans les performances et rendra OpenCL inutile pour vous, particulièrement lors de l’exportation de fichiers.

Une autre variable d’environnement qui modifie le comportement du pilote est `GPU_MAX_ALLOC_PERCENT`. Vous pourriez la mettre à 100 de manière à autoriser des allocations mémoire aussi importantes que 1 Go sur votre carte AMD/ATI. Le problème est que cela tend à faire planter darktable tôt ou tard.

Notre recommandation est de laisser ces paramètres inchangés. Souvent, votre carte sera reconnue avec 512 Mo de mémoire et une taille maximum d’allocation de 128 Mo. Il existe trois paramètres de configuration que vous pouvez assigner dans le fichier `$HOME/.config/darktable/darktablerc`afin que les choses fonctionnent. En voici les détails :

opencl\_memory\_requirement
: Définissez ce paramètre à 500 de manière à ce que darktable accepte les 512 Mo de mémoire graphique comme étant une quantité de mémoire suffisante.

opencl\_memory\_headroom
: Ce paramètre contrôle la quantité de mémoire graphique (parmi celle qui est reportée par votre carte) que darktable doit laisser libre pour les pilotes et l’écran. Comme pour les systèmes AMD/ATI nous n'avons, de toutes manières, que la moitié de la mémoire RAM disponible, on peut mettre cette valeur à 0. De cette manière, les 512 Mo pourront être utilisés par darktable.

opencl\_avoid\_atomics
: Les opérations atomiques d’OpenCL sont une manière particulière d’effectuer la synchronisation de données. Elles ne sont utilisées qu’avec certains noyaux. Malheureusement, certains (la plupart ?) dispositifs AMD/ATI sont extrêmement lents dans les opérations atomiques. Il est préférable de traiter les modules concernés par la CPU plutôt que d’accepter un code GPU très lent. Définissez ce paramètre à TRUE si vous rencontrez un traitement lent de modules comme [_ombres et hautes lumières_](../../module-reference/processing-modules/shadows-and-highlights.md), [_monochrome_](../../module-reference/processing-modules/monochrome.md), [_contraste local_](../../module-reference/processing-modules/local-contrast), ou [_mappage global des tonalités (déprécié)_](../../module-reference/processing-modules/global-tonemap) ou encore si vous avez des blocages intermittents du système.

Ces recommandations ne s’appliquent pas aux cartes Radeon plus récentes des séries HD7xxx avec l’architecture GCN. En plus d’être très rapides en termes de calcul GPU, elles fonctionnent normalement directement. Vous ne devrez vous intéresser qu’à quelques options d’optimisation qui sont décrites dans la section suivante.
