---
draft: 'false'
id: the-anatomy-of-a-module
title: "l'anatomie d'un module de traitement"
weight: 10
---

Les éléments de base du traitement d'image dans darktable sont les [modules de traitement](../../module-reference/processing-modules/). Afin de traiter une image raw, un certain nombre de ces modules agissent en séquence sur l'image d'entrée, chacun effectuant une _opération_ différente sur les données de l'image. Pour ceux qui sont familiers avec Adobe Photoshop, le concept d'un _module de traitement_ dans darktable est analogue à celui d'un _calque d'ajustement_ car tous les deux effectuent un ajustement incrémentiel de l'image, en s'appuyant sur les ajustements précédents.

darktable fournit également des [modules utilitaires](../../module-reference/utility-modules/), cependant ceux-ci ne sont pas directement impliqués dans le traitement d'image, mais ils fournissent à la place une interface graphique qui vous permet de gérer vos images, de les étiqueter, de les exporter et ainsi de suite.

Chaque module de traitement s'exécute indépendamment de la même manière :

![anatomie d'un module](./the-anatomy-of-a-module/module-anatomy.png#w100)

1. Il reçoit son _entrée_ en provenance du dernier module exécuté et effectue dessus une _opération_ pour produire la _sortie traitée_. Cette _opération_ est différente pour chaque [module de traitement](../../module-reference/processing-modules/_index.md).


2. Il combine l '_entrée du module_ et la _sortie traitée_ à l'aide d'un [opérateur de fusion](../masking-and-blending/blend-modes.md) pour produire la _sortie fusionnée_. Si aucune fusion n'est effectuée, la sortie de cette étape est la même que la _sortie traitée_.


3. Il génére un _masque_, qui définit une _opacité_ pour chaque pixel de l'image. L'_opacité_ est utilisée plus tard pour contrôler la force avec laquelle l'action du module est appliquée à chaque partie de l'image. 


   Vous pouvez définir votre propre masque en dessinant des formes sur l'image ou en utilisant les propriétés des pixels provenant de l'_entrée du module_ ou de la _sortie traitée_ (voir [masques](../masking-and-blending/masks/_index.md) pour plus de détails). Ce masque peut être encore modifié avec un paramètre d'opacité globale, qui affecte chaque pixel de la même manière. 

   Si aucun masque dessiné/paramétrique n'est utilisé, la sortie de cette étape est un masque où chaque pixel a la même opacité (régie par le paramètre d'opacité globale). Si aucune opacité n'est définie (aucun mélange n'est effectué), une opacité globale de 1,0 (ou 100%) est supposée.

4. Il combine l'_entrée du module_ et la _sortie fusionnée_ pixel par pixel en utilisant le _masque_ comme opérateur de mixage, pour produire la _sortie finale_. Lorsque l'opacité du masque est de 100%, la _sortie finale_ est la _sortie fusionnée_ pour ce pixel. Lorsque l'opacité du masque est égale à 0, la sortie finale est l'_entrée du module_ pour ce pixel. Pour une opacité intermédiaire du masque, la _sortie fusionnée_ et l'_entrée du module_ sont combinées proportionnellement à cette opacité pour donner la _sortie finale_ de ce pixel. La _sortie finale_ est transmise au module suivant pour un traitement ultérieur.


Les étapes 2 et 3 sont facultatives et ne sont pas prises en charge par tous les modules. Par exemple, le module [dématriçage](../../../module-reference/processing-modules/demosaic.md) doit être appliqué à l'ensemble du fichier raw afin de produire une belle image, il est donc inutile de masquer ou de fusionner sa sortie.

Chacune des étapes ci-dessus est définie plus en détail dans les sections suivantes.
