---
author: people
draft: 'false'
id: rendering-intent
title: 'intention de rendu'
weight: 40
---

Si le rendu avec LittleCMS2 est activé (voir [méthode de rendu](./rendering-method.md)), vous pouvez définir comment les couleurs hors gamut sont gérées lors de la conversion entre les espaces colorimétriques. Une boîte de sélection dans le module [exporter]((../../module-reference/utility-modules/shared/export.md)), le module [_profil de couleur de sortie_](../../module-reference/processing-modules/output-color-profile.md) et le module [épreuvage écran](../../module-reference/utility-modules/darkroom/soft-proof.md) vous donnent le choix entre les intentions de rendu suivants :

perceptif
: Convient aux photographies car il maintient la position relative des couleurs. C'est généralement le meilleur choix.

colorimétrique relative
: Les couleurs hors gamut sont converties en couleurs ayant la même clarté, mais une saturation différente. Les autres couleurs restent inchangées.

saturation
: La saturation est conservée mais la luminosité est légèrement modifiée.

colorimétrique absolue
: Garder le point blanc. 
