---
author: people
draft: 'false'
id: background
title: 'le contexte'
weight: 10
---

Le traitement d’images en haute résolution est une tâche exigeante qui nécessite un ordinateur moderne. Que ce soit en termes de ressources mémoire et en termes de puissance du processeur CPU. Tirer le meilleur partie d’une image typique de 15, 20 ou 25 mégapixels peut rapidement pousser votre ordinateur à ses limites.

darktable's requirements are no exception. All calculations are performed on 4 x 32bit floating point numbers. This is slower than “ordinary” 8 or 16 bit integer algebra, but eliminates all problems of tonal breaks or loss of information.

A great deal of optimization has been undertaken to make darktable as fast as possible. If you run a current version of darktable on a modern computer, you might not notice any “slowness”. However, there are conditions and certain modules where you will feel (or hear from the howling of your CPU fan) how much your poor multi-core processor has to struggle.

C'est ici qu’OpenCL arrive. OpenCL nous permet de tirer avantage de l’énorme puissance des cartes graphiques modernes. Dans les jeux de tir modernes la demande des joueurs en mondes 3D très détaillés a favorisé le développement des GPU. Afin de répondre à cette demande, ATI, NVIDIA et Co ont mis une énorme puissance de traitement dans leurs GPU. On obtient ainsi des cartes graphiques modernes avec des GPU hautement parallélisées permettant de calculer rapidement, avec des fréquences d’images élevées, les surfaces et les textures.

Vous n'êtes pas un joueur et vous ne tirez pas parti de cette puissance ? Et bien vous pouvez l’utiliser au moins dans darktable ! Pour les tâches demandant des calculs fortement parallélisés en virgule flottante, les GPU modernes sont bien plus rapides que les CPU. Ceci est particulièrement vrai lorsque vous souhaitez répéter les mêmes étapes de traitement sur des millions d’éléments. Cas typique d’utilisation : traitement d’images comportant des millions de pixels.
