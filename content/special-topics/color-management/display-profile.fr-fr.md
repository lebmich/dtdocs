---
author: people
draft: 'false'
id: display-profile
title: "profil d'affichage"
weight: 20
---

 Pour que darktable rende fidèlement les couleurs à l'écran, il doit trouver le profil d'affichage correct pour votre moniteur. En général, cela nécessite que votre moniteur soit correctement calibré et profilé, et il a besoin que le profil soit correctement installé sur votre système. darktable interroge le xatom de votre serveur d'affichage X ainsi que le service colord du système (si disponible) pour le bon profil. Si nécessaire, vous pouvez appliquer une méthode spécifique dans [préférences>divers](../../preferences-settings/miscellaneous.md).

Pour examiner la configuration de votre profil d'affichage, vous pouvez exécuter le binaire [darktable-cmstest](../program-invocation/darktable-cmstest.md) (Linux uniquement) qui affiche des informations utiles (par exemple le nom du profil par moniteur) et vous indique si le système est correctement configuré.

Dans de rares cas, vous devrez peut-être sélectionner manuellement le profil d'affichage. Ceci est possible à partir de l'[épreuvage écran](../../module-reference/utility-modules/darkroom/soft-proof.md) et de la [vérification de gamut](../../module-reference/utility-modules/darkroom/gamut.md) dans la vue chambre noire et dans la boîte de dialogue de profil d'affichage dans la vue table lumineuse.

Gardez à l'esprit que les écrans grand public de haut niveau n'ont pas besoin d'un profil d'affichage personnalisé, sauf si vous devez effectuer un épreuvage écran avec des attentes professionnelles, car ils sont correctement calibrés en usine pour sRGB.

Un profil d'affichage mal conçu sera plus nocif que de s'en tenir au profil sRGB par défaut, car la valeur par défaut peut être légèrement inexacte mais sera au moins fiable. Il est conseillé aux utilisateurs avancés et professionnels de procéder à la production de profils d'affichage personnalisés uniquement s'ils ont la formation nécessaire pour évaluer la qualité du profil résultant et la compréhension des options de profilage.
