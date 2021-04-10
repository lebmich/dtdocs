---
draft: 'false'
id: cpu-gpu-memory
title: cpu/gpu/mémoire
weight: 90
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

activate [OpenCL](../special-topics/opencl/_index.md) support
: _darktable_ can use your GPU to significantly speed up processing. The OpenCL interface requires suitable hardware and matching OpenCL drivers on your system. If one of those is not found the option is grayed out. Can be switched on and off at any time and takes immediate effect (default on).

profile de planification OpenCL
: Définit comment l'image complète et la prévisualisation sont traitées sur les systèmes avec support OpenCL :
: - _défaut_ : le GPU est utilisé pour le rendu de l'image complète ; le CPU pour la prévisualisation,
: - _GPUs multiples_ : l'image complète et la prévisualisation sont traitées en parallèle sur des GPUs différents,
: - _GPU très rapide_ : l'image complète et la prévisualisation sont traitées séquentiellement sur le GPU. 
