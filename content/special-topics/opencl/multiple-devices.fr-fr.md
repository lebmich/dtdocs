---
author: people
draft: 'false'
id: multiple-devices
title: 'multiples périphériques'
weight: 90
---

The scheduling of OpenCL devices on most systems can be optimized using the “OpenCL scheduling profile” settings. However, if your system is equipped with more than one GPU you might want to set the relative device priority manually. To do this you need to select the “default” scheduling profile and change the settings in the “opencl\_device\_priority” configuration parameter.

It is important to understand how darktable uses OpenCL devices. Each processing sequence of an image – to convert an input to the final output using a history stack – is run in a pixelpipe. There are four different types of pixelpipe in darktable. One type is responsible for processing the center image view (or full view) in darkroom mode, another pixelpipe processes the preview image (navigation window). There can be one of each of these two pixelpipes running at any one time – with the full and preview pixelpipes running in parallel. In addition there can be multiple parallel pixelpipes performing file exports as well as multiple parallel pixelpipes generating thumbnails. If an OpenCL device is available darktable dynamically allocates it to one specific pixelpipe for one run and releases it afterwards.

La demande en calcul dépend beaucoup du type de pipeline. Image de prévisualisation et miniature ont une basse résolution et peuvent être traitées rapidement. L'image du panneau central est plus gourmande. Le pipeline réalisant l'exportation complète l'est encore plus.

The configuration parameter “opencl\_device\_priority” holds a string with the following structure: `a,b,c.../k,l,m.../o,p,q.../x,y,z...`. Each letter represents one specific OpenCL device. There are four fields in the parameter string separated by a slash, each representing one type of pixelpipe. `a,b,c...` defines the devices that are allowed to process the center image (full) pixelpipe. Likewise devices `k,l,m...` can process the preview pixelpipe, devices `o,p,q...` the export pixelpipes and finally devices `x,y,z...` the thumbnail pixelpipes. An empty field means that no OpenCL device may serve this type of pixelpipe.

darktable possède un système de numérotation interne, où le premier périphérique OpenCL disponible recevra le numéro « 0 ». Les périphériques suivants seront numérotés consécutivement. Ce numéro, utilisé conjointement avec le nom du périphérique, est affiché lorsque vous démarrez darktable avec `darktable -d opencl`. Vous pouvez indiquer un dispositif soit par son numéro, soit par son nom (la casse et les espaces ne sont pas pris en compte). Si vous avez plus d’un dispositif ayant le même nom vous devrez utiliser les numéros de périphérique afin de les différencier.

Un indicateur de périphérique peut être précédé d’un point d’exclamation `!`, dans ce cas, le périphérique ne pourra pas exécuter ce pipeline graphique. Vous pouvez aussi utiliser un astérisque`*` comme joker, qui représentera tous les périphériques non encore mentionnés explicitement dans ce groupe.

L’ordre dans un groupe a une importance -- darktable va lire la liste de la gauche vers la droite et lorsqu’il cherche à allouer un périphérique OpenCL à un pipeline graphique, il va balayer les périphériques dans cet ordre et prendra le premier périphérique libre qu'il trouvera

Si un pipeline est sur le point d'être lancé et si tous les GPUs du groupe correspondant sont occupés, darktable, par défaut, traite automatiquement l'image sur le CPU. Vous pouvez forcer le traitement sur GPU en préfixant la liste des GPUs autorisés par un signe plus `+`. darktable n'utilisera pas le CPU mais suspendra le traitement jusqu'à ce que le premier périphérique OpenCL soit disponible.

darktable's default setting for “opencl\_device\_priority” is `*/!0,*/*/*`.

Tout périphérique OpenCL détecté est autorisé à traiter l'image du panneau central. Le premier périphérique OpenCL (0) n'est pas autorisé à traiter le pipeline graphique de prévisualisation. En conséquence, s’il n'y a qu'un seul GPU sur votre système, le pipeline graphique de prévisualisation sera toujours traité par le CPU, réservant exclusivement votre unique GPU au panneau central contenant l’image qui demande davantage de ressources. Ceci est un paramétrage raisonnable pour la plupart des systèmes. Aucune restriction de ce type ne s’applique au pipeline de l’exportation et au pipeline des miniatures.

La valeur par défaut est un bon choix si vous n’avez qu'une carte. Si vous en avez plusieurs, cela reste un bon point de départ. Cependant, comme vos cartes peuvent avoir un niveau de puissance de calcul assez différent, cela vaut le coup de passer un peu de temps à optimiser votre liste de priorités.

Voici un exemple. Supposons que nous ayons un système avec deux périphériques, une Radeon HD7950 rapide et une GeForce GTS450 plus ancienne et plus lente. darktable (démarré avec `darktable -d opencl`) signalera les appareils suivants :

```
[opencl_init] successfully initialized.
[opencl_init] here are the internal numbers and names of
                          OpenCL devices available to darktable:
[opencl_init]           0       'GeForce GTS 450'
[opencl_init]           1       'Tahiti'
[opencl_init] FINALLY: opencl is AVAILABLE on this system.
```

Ici, la GeForce GTS 450 est détectée comme le premier périphérique ; la Radeon HD7950 («Tahiti») comme le second. Cet ordre ne changera normalement pas à moins que la configuration du matériel ou du pilote ne soit modifiée, mais il est préférable d'utiliser des noms de périphériques plutôt que des numéros pour être en sécurité.

Comme la GTS450 est plus lente que la HD7950, un "opencl_device_priority" optimisé devrait ressembler à : `!GeForce GTS450,*/!Tahiti,*/Tahiti,*/Tahiti,*`.

The GTS450 is explicitly excluded from processing the center image pixelpipe; this is reserved to “all” other devices (i.e. the HD7950/Tahiti). Conversely, for the preview pixelpipe, the Tahiti is excluded, so that only the GTS450 is permitted to do the work.

Nous souhaitons que l’exportation des fichiers et la génération des miniatures se fassent sans toucher à rien. Cependant, darktable va d’abord vérifier que le dispositif Tahiti est libre parce qu'il est le plus rapide. Si cela n'est pas le cas, il va vérifier tous les autres périphériques – en fait, uniquement la GTS450.
