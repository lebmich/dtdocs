---
author: people
draft: 'false'
id: color-spaces
title: 'espaces colorimétriques de darktable'
weight: 50
---

darktable's input images are either RGB files (like JPEGs or TIFFs) or camera RAWs. Both store visual information as a combination of primary colors (such as red, green and blue) which together describe a light emission to be later recreated by a display.

L'image suivante illustre ce concept.

![Décomposition spectrale d'une émission lumineuse en 3 intensités RVB](./color-spaces/spectral-decomposition.png#w100)

Sur le côté gauche de l'image se trouve une lumière colorée que nous devons représenter numériquement. En utilisant trois filtres de couleur idéaux, nous pouvons décomposer cette lumière en trois lumières de couleur primaire à différentes intensités. Afin de recréer la lumière colorée d'origine à partir de notre décomposition idéale, comme illustré au centre de l'image, nous devons simplement recombiner ces trois lumières de couleur primaire par addition.

Il devrait être possible de reproduire cette lumière originale en prenant une combinaison de lumières blanches aux intensités correctes et en projetant cette lumière à travers des filtres de couleur appropriée. Cette expérience peut être réalisée à la maison en utilisant des gels et des ampoules blanches à intensité variable. C'est à peu près ce que faisaient les anciens écrans CRT couleur et c'est encore comment fonctionnent les vidéoprojecteurs.

En photographie, l'étape de décomposition initiale est effectuée par le réseau de filtres couleur qui se trouve au-dessus du capteur de votre appareil photo. Cette décomposition n'est pas idéale, il n'est donc pas possible de recréer l'émission d'origine directement par une simple addition. Au lieu de cela, nous devons fournir une mise à l'échelle intermédiaire pour ajuster les trois intensités. 

On screens, the LED bulbs are dimmed proportionally to each intensity, and the emissions of the three lights physically added to reconstruct the original emission. Digital images store the intensities of these primary lights as a set of 3 numbers for each pixel, depicted on the right of the above image as shades of gray.

Alors qu'un ensemble d'intensités d'affichage peut être facilement combiné pour recréer une lumière originale sur un écran (par exemple, si nous avons créé une image de synthèse avec l'ordinateur), l'ensemble des intensités capturées par un capteur nécessite une mise à l'échelle pour que l'addition de ces intensités à l'écran reproduise raisonnablement l'émission lumineuse d'origine. Cela signifie que chaque ensemble d'intensités, exprimé sous la forme d'un ensemble de valeurs RVB, doit être lié à un ensemble de filtres (ou de couleurs primaires de LED) définissant un _espace colorimétrique_ -- tout ensemble RVB n'a de sens qu'en référence à un espace colorimétrique. 

Nous devons donc adapter les intensités capturées pour les rendre à nouveau sommables. Mais si nous devons aussi recomposer la lumière d'origine sur un écran qui n'a pas les mêmes filtres colorés ou primaires que l'espace auquel notre ensemble de valeurs RVB appartient, alors, ces intensités doivent être mises à l'échelle pour prendre en compte les filtres différents de l'écran. Le mécanisme de cette mise à l'échelle est décrit dans les _ profils de couleur_, généralement stockés dans des fichiers .icc.

---

** Remarque ** : La couleur n'est pas une propriété physique de la lumière. Elle n'existe que dans le cerveau humain. Elle résulte de la décomposition d'une émission de lumière par les cellules coniques de la rétine. Le principe de cette décomposition est très similaire à celui du filtrage de l'exemple précédent. Une valeur «RVB» doit être comprise comme «une émission lumineuse codée par trois canaux connectés à trois primaires». Mais les primaires elles-mêmes peuvent être différentes de ce que les humains appellent «rouge», «vert» ou «bleu».

---

Pour résumer, les filtres décrits ici sont des filtres passe-bande qui se chevauchent. Puisqu'ils se chevauchent, additionner leurs valeurs ne préserverait pas l'énergie du spectre d'origine. Donc, pour faire court, nous devons recomposer ces valeurs en prenant en compte la réponse des cônes de la rétine.

Most of darktable's actual image processing takes place in a large RGB "working profile" space, with some (mostly older) modules internally working in the CIELab 1976 color space (often just called “Lab”). The final output of the image processing pipeline is once again in an RGB space shaped for either the monitor display or the output file.

Ce processus implique que le pipeline graphique comporte deux étapes fixes de conversion de couleur : [_profil de couleur d'entrée_](../../module-reference/processing-modules/input-color-profile.md) et [_profil de couleur de sortie_](../../module-reference/processing-modules/output-color-profile.md). De plus, il y a l'étape [_dématriçage_](../../module-reference/processing-modules/demosaic.md) pour les images raw, où les couleurs de chaque pixel sont reconstruites par interpolation.

Chaque module a une position dans le pipeline graphique qui vous indique dans quel espace colorimétrique le module travaille :

- jusqu'à [_dématriçage_](../../module-reference/processing-modules/demosaic.md)
: Les informations d'image raw ne constituent pas encore une "image" mais simplement des "données" concernant la lumière capturée par le boîtier. Chaque pixel porte une intensité pour chaque couleur primaire, et les couleurs primaires du boîtier sont très différentes de celles utilisées dans les modèles de vision humaine. Gardez à l'esprit que certains des modules de cette partie du pipeline peuvent également agir sur des images d'entrée non raw au format RVB ayant des informations complètes sur les trois canaux de couleur.

- entre [_dématriçage _](../../module-reference/processing-modules/demosaic.md) et [_profil de couleur d'entrée_](../../module-reference/processing-modules/input-color-profile.md)
: L'image est au format RVB dans l'espace colorimétrique du boîtier ou du fichier d'entrée spécifique.

- entre [_profil de couleur d'entrée_](../../module-reference/processing-modules/input-color-profile.md) et [_profil de couleur de sortie_](../../module-reference/processing-modules/output-color-profile.md)
: L'image se trouve dans l'espace défini par le profil de travail sélectionné (linéaire Rec2020 RVB par défaut). Comme darktable traite les images dans des tampons à virgule flottante 4x32 bits, nous pouvons gérer de grands espaces colorimétriques de travail sans risquer des bandes ou des coupures tonales.


- après [_profil de couleur de sortie_](../../module-reference/processing-modules/output-color-profile.md)
: L'image est au format RVB tel que défini par l'affichage sélectionné ou le profil ICC de sortie.
