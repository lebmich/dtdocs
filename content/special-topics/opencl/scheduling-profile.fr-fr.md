---
author: people
draft: 'false'
id: scheduling-profile
title: 'profil de planification'
weight: 80
---

darktable peut utiliser le CPU ainsi qu'un ou plusieurs GPUs supportant OpenCL. En fonction des performances relatives de ces périphériques, les utilisateurs peuvent choisir parmi différents profils de planifications pour optimiser les performances. Ceci est fait par le paramètre de configuration [préférences > cpu/gpu/memory >profil de planification OpenCL](../../preferences-settings/cpu-gpu-memory.md) qui offre les choix suivants  :

default
: If an OpenCL capable GPU is found darktable uses it for processing the center image view while the [navigation preview window](../../module-reference/utility-modules/darkroom/navigation.md) is processed on the CPU in parallel. This is the preferred setting for systems with a reasonably fast CPU and a moderately fast GPU. The exact allocation of devices to the various pixelpipe types can be finetuned with the “opencl\_device\_priority” configuration parameter (see [multiple devices](./multiple-devices.md)).

GPU très rapide
: Avec ce profil de planification darktable traite séquentiellement sur le GPU le panneau central contenant l'image et la fenêtre de prévisualisation. Ceci est le réglage préférable pour les systèmes qui ont un GPU surpassant fortement le CPU.

multiple GPUs
: This setting addresses systems with multiple GPUs whose relative performance does not differ significantly. Whenever a processing job is started darktable uses any currently idle GPU but not the CPU. Users of systems with a variety of GPUs will need better control on their relative priority. They would be better off selecting the “default” profile and fine-tuning their system with the “opencl\_device\_priority” configuration parameter (see [multiple devices](./multiple-devices.md)).

Au premier démarrage ou après détection d'une modification de la configuration du GPU de votre système, darktable essaie d'identifier le profil qui vous convient le mieux. Vous pouvez changer ceci à tout moment dans l'onglet [préférences > cpu/gpu/mémoire](../../preferences-settings/cpu-gpu-memory.md) avec effet immédiat .
