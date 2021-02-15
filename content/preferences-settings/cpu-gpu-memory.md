---
title: cpu/gpu/mémoire
id: cpu-gpu-memory
weight: 90
draft: false
author: "traducteur : Michel Leblond"
---

Cet onglet des préférences contient principalement des paramètres liés aux performances :

mémoire en mégaoctets à utiliser pour le cache des miniatures
: Afin d'accélérer l'affichage des pellicules, darktable stocke les miniatures dans un fichier cache sur le disque (cache principal) et le charge en mémoire au démarrage. Ce paramètre contrôle la taille du cache en mégaoctets. Un redémarrage est nécessaire en cas de modification (256 Mo par défaut).

utilisation du disque dur pour le cache des miniatures
: Si activé, darktable stocke toutes les miniatures sur le disque dur en tant que cache secondaire, et les garde ainsi accessibles si elles sont supprimées du cache principal. Cela nécessite plus d'espace disque mais accélère la vue [lighttable](../lighttable/_index.md) car cela évite le retraitement des miniatures (activé par défaut).

utilisation du disque dur pour le cache des images 100%
: Si activé, darktable écrit les images de prévisualisation complètes sur le disque (`.cache/darktable/`) lorsqu'elles sont supprimées du cache mémoire. Notez que cela peut prendre beaucoup de stockage (plusieurs gigaoctets pour 20000 images) et darktable ne supprimera jamais les images mises en cache. Vous pouvez les supprimer manuellement si vous le souhaitez. L'activation de cette option améliorera considérablement les performances de la table lumineuse lors du zoom sur une image en mode d'aperçu complet (désactivé par défaut).

nombre de fils d'exécution
: C'est le nombre de fils d'exécution en parallèle utilisés pour créer des miniatures lors de l'importation. Nécessite un redémarrage en cas de modification (par défaut 2).

mémoire limite (en mégaoctets) pour le tuilage
: Afin de gérer de grandes images sur des systèmes avec une mémoire limitée, darktable effectue un traitement par tuiles. Cette variable contrôle la quantité maximale de mémoire (en Mo) qu'un module peut utiliser pendant le développement. Des petites valeurs forceront les modules gourmands en mémoire à utiliser de nombreuses tuiles. Mettre cette variable à 0 pour une infinité de tuiles. Les valeurs inférieures à 500 seront traitées comme 500. Nécessite un redémarrage en cas de modification (par défaut 1500).

quantité minimale de mémoire (en Mo) pour la mémoire tampon d'une tuile
: Une valeur strictement positive définit la quantité de mémoire minimale (en Mo) que darktable doit utiliser pour une tuile. Nécessite un redémarrage en cas de modification (par défaut 16).

activer le support d'[OpenCL](../special-topics/opencl/_index.md)
: _darktable_ peut utiliser votre GPU pour accélérer considérablement le développement. L'interface OpenCL nécessite un matériel approprié et les pilotes OpenCL correspondants sur votre système. Si l'un de ceux-ci n'est pas trouvé, l'option est grisée. Peut être activé et désactivé à tout moment et prend effet immédiatement (activé par défaut).

profile de planification OpenCL
: Defines how preview and full pixelpipe tasks are scheduled on OpenCL enabled systems:
: - _default_: the GPU processes the center view pixelpipe; the CPU processes the preview pipe;
: - _multiple GPUs_: both pixelpipes are processed in parallel on two different GPUs;
: - _very fast GPU_: both pixelpipes are processed sequentially on the GPU.
