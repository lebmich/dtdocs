---
author: people
draft: 'false'
id: setting-up
title: 'configurer opencl'
weight: 40
---

La grande diversité des systèmes, les différences marquées entre les vendeurs OpenCL et les versions de pilotes, ne permettent pas de donner une vue d'ensemble de la manière de configurer OpenCL. Nous ne pouvons que vous donner un exemple pour la version du pilote NVIDIA 331.89 sur Ubuntu 14.04. Nous espérons que cela va vous servir pour une première impression et vous aidera à résoudre les problèmes éventuels de votre configuration spécifique.

Le principe de fonctionnement d'OpenCL ressemble à ceci :

`darktable > libOpenCL.so > libnvidia-opencl.so.1 > kernel driver module(s) > GPU`

- darktable charge dynamiquement `libOpenCL.so`, une bibliothèque système qui doit être accessible au chargeur dynamique du système (`ld.so`).


- `libOpenCL.so`lira le fichier d'informations spécifique au vendeur (`/etc/OpenCL/vendors/nvidia.icd`) pour trouver la bibliothèque qui contient l’implémentation OpenCL spécifique au vendeur.


- L'implémentation OpenCL spécifique au vendeur est fournie sous forme d'une bibliothèque `libnvidia-opencl.so.1` qui dans notre cas est un lien symbolique vers `libnvidia-opencl.so.331.89`).


- `libnvidia-opencl.so.1` a besoin de communiquer avec les modules du noyau spécifiques au vendeur `nvidia` et `nvidia_uvm` via des fichiers spéciaux de périphériques `/dev/nvidia0`, `/dev/nvidiactl`, et `/dev/nvidia-uvm`.


Au démarrage du système les fichiers spéciaux de périphériques requis (`/dev/nvidia*`) doivent être créés. Si cela ne se produit pas par défaut sur votre système, le moyen le plus simple pour les définir et pour être sûr que tous les modules seront chargés est d'installer le paquet `nvidia-modprobe`.

A user account which needs to make use of OpenCL from within darktable must have read-write access to NVIDIA's device special files. On some systems these files allow world read-write access by default, which avoids permission issues but might be debatable in terms of system security. Other systems restrict the access to a user group, e.g. “video”. In this case your user account has to be member of that group.

En résumé, les paquets qui doivent être installés dans ce cas particulier sont :

```
nvidia-331 (331.89-0ubuntu1~xedgers14.04.2)
nvidia-331-dev (331.89-0ubuntu1~xedgers14.04.2)
nvidia-331-uvm (331.89-0ubuntu1~xedgers14.04.2)
nvidia-libopencl1-331 (331.89-0ubuntu1~xedgers14.04.2)
nvidia-modprobe (340.24-1)
nvidia-opencl-dev:amd64 (5.5.22-3ubuntu1)
nvidia-opencl-icd-331 (331.89-0ubuntu1~xedgers14.04.2)
nvidia-settings (340.24-0ubuntu1~xedgers14.04.1)
nvidia-settings-304 (340.24-0ubuntu1~xedgers14.04.1)
nvidia-libopencl1-331 (331.89-0ubuntu1~xedgers14.04.2)
nvidia-opencl-dev:amd64 (5.5.22-3ubuntu1)
nvidia-opencl-icd-331 (331.89-0ubuntu1~xedgers14.04.2)
opencl-headers (1.2-2013.10.23-1)
```

La liste des modules du noyau concernant NVIDIA affichée par la commande lsmod est :

```
nvidia
nvidia_uvm
```

La liste des fichiers spéciaux de périphériques liés à NVIDIA (obtenue par la commande `ls -l /dev/nvidia*`) devrait ressembler à ceci :

```
crw-rw-rw- 1 root root 195,   0 Jul 28 21:13 /dev/nvidia0
crw-rw-rw- 1 root root 195, 255 Jul 28 21:13 /dev/nvidiactl
crw-rw-rw- 1 root root 250,   0 Jul 28 21:13 /dev/nvidia-uvm
```

Méfiez-vous que les numéros majeurs/mineurs (par exemple `250/0` pour `/dev/nvidia-uvm` dans cet exemple) peuvent varier en fonction de votre système. 
