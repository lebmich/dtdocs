---
author: people
draft: 'false'
id: overview
title: présentation
weight: 10
---

Cette vue concerne l'impression. Parce qu'imprimer n'est pas aisé, de nombreux aspects techniques doivent être pris en compte.

Après avoir sélectionné une image dans la [table lumineuse](../lighttable/_index.md) on peut entrer dans le module [paramètres d'impression](../module-reference/utility-modules/print/print-settings.md) pour ajuster les paramètres d'impression et lancer l'impression.

Ce module prend en charge le profil ICC de l'imprimante, ce qui est quelque peu obligatoire si vous souhaitez obtenir une impression de haute qualité proche de l'image affichée à l'écran.

Il est important de noter que les profils ICC fournis par les fabricants de papier et/ou d'imprimante ne peuvent pas être utilisés sous GNU/Linux car ils dépendent des pilotes d'imprimante. Le module impression de darktable utilise CUPS et il n'y a pas de profils ICC prêts à l'emploi pour ce pilote.
