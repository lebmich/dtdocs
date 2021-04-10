---
author: people
draft: 'false'
id: color-pipeline
title: 'pipeline graphique de darktable'
weight: 80
---

La plupart des applications de traitement d'image proviennent des années 90 et/ou héritent d'un flux de travail des années 90. Ces applications traitaient des images codées avec des entiers non signés de 8 bits car c'était plus efficace en termes de mémoire et de calcul. Cependant, en raison de l'utilisation d'un format entier (qui implique des erreurs d'arrondi), elles ont dû appliquer un "gamma" (essentiellement une fonction de transfert appliquant une puissance 1/2,2 ou 1/2,4 pour encoder les valeurs RVB). Elles ont aussi dû augmenter la profondeur de bit afin de réduire les erreurs d'arrondi dans les basses lumières (les humains sont très sensibles aux détails de faible luminosité). Les formats d'entiers 8 bits sont également techniquement limités à la plage 0-255. Toute valeur qui ne se trouve pas dans cette plage est tronquée.

These workflows, using bounded RGB representations and possibly non-linear transforms to encode RGB signals, are called "display-referred". They rely on the assumption that the image has been prepared for display at an early stage in the processing pipeline, and embed hard-coded assumptions about the RGB values of black, middle-gray and white. Most of the image-processing algorithms used in these workflows have been tuned around these assumptions. For example, the darken and lighten blending modes expect a middle-gray encoded at 50% (or 128 in integer encoding).

Malheureusement, la mise à l'échelle non linéaire, qui est obligatoire pour faire fonctionner le codage entier, rompt les relations naturelles entre les valeurs de pixel. La teinte et la saturation changent de manière imprévisible, et les relations de valeur entre les pixels voisins sont dilatées ou compressées de sorte que les dégradés sont également modifiés de manière imprévisible.

Les pipelines graphiques relatifs à l'affichage cassent donc l'effet des filtres optiques (flou ou correction du flou d'un objectif), la simulation de transparence (qui repose sur des définitions optiques et géométriques de l'occultation), les couleurs et les dégradés (relations locales entre chrominance et luminance des pixels). Ils ne s'adaptent pas bien non plus aux images HDR, ce qui a conduit au développement de nombreuses méthodes discutables de mappage local et global des tonalités et au fameux «look HDR» des années 2010.

Les ordinateurs modernes ne sont pas assujettis aux mêmes limitations de calcul que ceux des années 1990 et peuvent travailler sur des pixels aux valeurs illimitées (de 0 à + infini) et encodées en nombres réels (en utilisant des formats à virgule flottante). Ces possibilités permettent ce que nous appelons un flux de travail "relatif à la scène", dans lequel les pixels peuvent conserver leurs relations radiométriques d'origine presque tout le long du pipeline graphique. Dans le flux de travail relatif à la scène, les pixels sont préparés pour l'affichage uniquement à la dernière étape du pipeline, dans la transformation d'affichage. Cela signifie que les valeurs RVB des pixels sont maintenues proportionnelles à l'intensité de l'émission de lumière enregistrée par la caméra dans la scène, permettant une simulation de transparence précise et des émulations de filtre optique, tout en s'adaptant à n'importe quelle plage dynamique via le même algorithme (SDR aussi bien que HDR).

However, scene-referred pipelines lose the convenient fixed values of white, middle-gray and black which characterised display-referred pipelines, and setting these values, according to the scene and to the conditions of shooting, now becomes the responsibility of the user. This requires a more complex user interface.

De plus, comme les valeurs relatives à la scène sont supposées avoir une signification physique, les pixels ne peuvent pas avoir une intensité nulle. Cela signifierait qu'ils n'ont pas de lumière du tout et que l'existence d'une lumière nulle casse de nombreux algorithmes physiquement précis. En fait, le blanc et le noir ne signifient rien par rapport à la scène originale, qui n'est qu'un ensemble de luminances à des intensités variables. Le flux de travail relatif à la scène vise simplement à mapper certaines luminances arbitraires de la scène sur ce qui apparaîtra en blanc ou en noir sur le support de sortie.

Versions of darktable prior to 2.6 had a non-linear display-referred pipeline, assuming that a non-linear transform took place early in the pipe and middle-gray was thereafter encoded as 50%. However, not all modules and filters clipped pixel values above 100%, leaving open the possibility of recovering those values later in the pipe.

The _filmic_ module's view transform, introduced in darktable 2.6, was the first step toward a scene-referred pipeline, and deferred the mandatory, non-linear, display preparation to the end of the pipe, along with the ability to set custom black, gray and white values. The _color balance_ module then introduced a way to deal with a variable definition of middle-gray.

À partir de darktable 3.2, les utilisateurs pouvaient choisir entre deux flux de travail qui définissaient des paramètres par défaut cohérents, un choix de modules et leur ordre dans le pipeline graphique, à la fois, pour le traitement _relatif à l'affichage_ et pour le traitement _relatif à la scène_.

Dans darktable 3.4, une option complète de masquage et de fusion relative à la scène a été introduite, permettant de définir des masques pour des valeurs de pixel supérieures à 100% et utilisant uniquement des opérateurs de fusion non bornés.

Switching to _scene-referred_ is a cognitive leap for most experienced users, who are used thinking in display-referred ways. In a display-referred workflow, it is customary to anchor the white value and let tone adjustments revolve around that point, trying to maximize brightness while avoiding clipping. In a scene-referred workflow, white and black values are fluid and adapted to the output medium. It is advised that users anchor middle-gray (which will be preserved as-is for any output medium) and let the view transform (_filmic_) dilate or contract the dynamic range around that point. Because 10 bit HDR white is 4 times as bright as 8 bit SDR white, any rigid definition of "white" becomes irrelevant. But anchoring for middle-gray is actually more convenient, since it keeps the average brightness of the picture unchanged through the view transform.

Certains modules (_niveaux_, _niveaux rvb_, _courbe des tonalités_, _courbe rvb_) sont intrinsèquement incompatibles avec un flux de travail _relatif à la scène_, car leur interface graphique suggère implicitement des valeurs RVB limitées dans la plage de 0 à 100%. Les opérations sur les pixels qu'ils exécutent sont non bornées en interne et peuvent être utilisées dans des flux de travail _relatif à la scène_ ou _relatif à l'affichage_. Mais leur interface de contrôle ne permet pas que des pixels soient sélectionnés en dehors de la plage de 0 à 100%.

De même, les modes de fusion tels que superposer, lumière linéaire, lumière douce, lumière dure, assombrir, éclaircir, etc. ont tous des seuils codés en dur qui attendent en interne un codage non linéaire _relatif à l'affichage_.

Dans darktable 3.4, le fait de placer le curseur sur un en-tête de module affiche une info-bulle détaillant les espaces colorimétriques, les plages et les encodages que le module attend, utilise et produit. Voici les définitions des termes utilisés :

linéaire
: Les valeurs de pixel sont proportionnelles à l'émission radiométrique de la scène, de manière à permettre une émulation précise des filtres physiques.

non-linear
: Pixel values are re-scaled such that low-lights are given a larger encoding range, usually to remap the 18.45% reference middle-gray to a value between 46 and 50%.

relatif à l'affichage
: Les valeurs de pixel sont censées se situer entre 0 et 100% de la plage d'affichage, où 100% est considéré comme la luminance d'une surface blanche réfléchissante à 20% (la pastille blanche d'un Color Checker) et 0% est compris comme densité maximale du support de sortie (encre noire saturée ou rétroéclairage minimum du panneau LED).

relatif à la scène
: Les valeurs de pixel doivent être strictement supérieures à zéro et aller jusqu'à + infini. La signification des valeurs spécifiques des pixels doit être définie par l'utilisateur lors de l'exécution. Les valeurs relatives à la scène n'impliquent pas automatiquement un codage linéaire, mis à l'échelle dans le cadre de la radiométrie.
