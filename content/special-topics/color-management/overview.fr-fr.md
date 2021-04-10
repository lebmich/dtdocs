---
author: people
draft: 'false'
id: overview
title: présentation
weight: 10
---

 darktable utilise un flux de travail entièrement géré par la couleur :

- Les spécifications de couleur d'entrée proviennent de profils ICC intégrés ou fournis par l'utilisateur ou, dans le cas de fichiers raw, d'une bibliothèque de matrices de couleurs spécifiques à l'appareil photo.


- darktable lit automatiquement le profil d'affichage de votre moniteur (s'il est correctement configuré) pour un rendu précis des couleurs à l'écran. Les configurations multi-écrans sont entièrement prises en charge tant qu'un service système tel que colord est en place et correctement configuré pour informer darktable du profil correct des moniteurs.


- Les fichiers de sortie peuvent être encodés dans l'un des profils intégrés de darktable, y compris sRVB et Adobe RVB, ou dans un espace colorimétrique fourni par l'utilisateur en tant que profil ICC.

