---
author: people
draft: 'false'
id: edit-scene-referred
title: 'développer une image : flux de travail relatif à la scène'
weight: 30
---

Le flux de travail _relatif à la scène_ met l'accent sur l'exécution du traitement d'image dans la partie linéaire relative à la scène du pipeline graphique. Cela permet de réduire les artefacts et les décalages de couleur qui peuvent résulter du traitement des valeurs non linéaires des pixels. En découplant le traitement d'image des caractéristiques d'un écran spécifique, il sera plus facile d'adapter ultérieurement votre travail à de nouveaux supports d'affichage, tels que les affichages à plage dynamique élevée.

Ceci étant la méthode recommandée pour traiter les images dans les versions 3.0 et supérieures, cette section fournira un aperçu beaucoup plus complet que la section suivante sur le flux de travail _relatif à l'affichage_.

# étapes basiques
Le traitement de base d'une image dans le flux de travail relatif à la scène demande, au minimum, de prendre en compte les étapes suivantes pour rendre à l'écran une image correcte :

1. Prenez une photo


   Utilisez votre appareil photo pour prendre une photo correctement exposée. Normalement, vous pouvez compter sur les fonctions de mesure et d'exposition automatiques du boîtier. Cependant, pour certaines scènes, vous devrez peut-être utiliser la molette de compensation d'exposition du boîtier ou les réglages manuels pour obtenir une exposition optimale. En général, vous souhaitez rendre l'exposition de l'appareil photo aussi lumineuse que possible sans tronquer les hautes lumières. Ceci est connu sous le nom d '"exposition à droite" (ETTR) et vous permet de tirer le meilleur parti de la plage dynamique du capteur. De nombreux appareils photo ont des fonctionnalités telles que "zébrures" ou "clignotements" pour vous avertir lorsque vous êtes en danger d'écrêtage.

2. Ajustez les tons-moyens en utilisant le module [_exposition_](../../module-reference/processing-modules/exposure.md)


   Utilisez le curseur exposition pour régler les tons-moyens de l'image à un niveau de luminosité approprié. À ce stade, ne vous inquiétez pas des hautes lumières et des ombres - elles seront traitées plus tard.

   Le module _exposition_ est activé par défaut. Il inclura une augmentation d'exposition initiale de +0,5&nbsp;IL pour imiter le traitement standard de la plupart des boîtiers fournissant des JPEG intégrés. Les systèmes de mesure des boîtiers varient et certains modèles peuvent nécessiter une augmentation d'exposition légèrement plus importante (par exemple +0,8&nbsp;IL à +1,5&nbsp;IL), auquel cas vous pouvez créer un  [préréglage](../../darkroom/interacting-with-modules/presets.md) automatique adéquat. Le module _exposition_ détectera si la molette de compensation d'exposition du boîtier a été utilisée (voir les remarques ci-dessus sur l'ETTR) et réajustera l'exposition en conséquence.

   Vous _pouvez_ modifier le niveau de noir dans le module _exposition_ pour fournir plus de contraste, mais vous devez faire très attention en faisant cela car vous pouvez vous retrouver avec des valeurs RVB négatives, ce qui peut entraîner un dysfonctionnement du module _filmique rvb_.

3. Ajustez la [_balance des blancs_](../../module-reference/processing-modules/white-balance.md)


   It is important that the white balance is set correctly to form a solid basis for subsequent processing. The camera will normally store the selected white balance setting inside the raw file's metadata, and darktable will use this as a starting point. To get a more accurate white balance, you can either use the color picker to select a neutral gray tone in the image, or you can switch to a different white balance preset from your camera, where available. Fine adjustments to the global white balance are made using the _temperature_ slider and, less often, the _tint_ slider. Moving the _temperature_ slider to the left makes the image cooler (more blue), and moving it to the right makes it warmer (more orange).

   Le module _balance des blancs_ ne peut effectuer que des réglages _globaux_ de la balance des blancs de l'image. Le module [_balance couleur_](../../module-reference/processing-modules/color-balance.md), entre autres, vous donne plus de contrôle dans les cas où une scène a été éclairée par plusieurs sources de lumière avec différentes températures de couleur.

4. Ajustez le point blanc et le point noir en utilisant le module [_filmique rvb_](../../module-reference/processing-modules/filmic-rgb.md)


   This module performs tone mapping compression from the high-dynamic-range of the captured image, to the lower dynamic range of the display medium. The mid-gray tone level has already been set (above) with the _exposure_ module. Filmic will propose, on its _scene_ tab, an appropriate white point and black point for the image -- you may need to adjust these for a particular scene. On the _look_ tab you can adjust the midtone contrast and saturation settings if required.


# autres modules recommandés
En plus des modules de base décrits ci-dessus, vous pouvez envisager d'utiliser les modules suivants pour rendre votre image encore plus jolie. Ces modules sont connus pour fonctionner correctement avec le flux de travail relatif à la scène :

[_recadrer et pivoter_](../../module-reference/processing-modules/crop-rotate.md) / [_correction de perspective_](../../module-reference/processing-modules/perspective-correction.md)
: Très souvent, vous souhaitez afficher uniquement une partie de la scène capturée dans votre image, par exemple pour enlever des détails dérangeants près de son pourtour. Dans d'autres cas, l'horizon de l'image peut nécessiter une mise à niveau ou il peut y avoir des distorsions de perspective. Tout cela peut être corrigé avec un contrôle manuel complet dans le module _recadrer et pivoter_. Pour une correction entièrement automatique des distorsions de perspective, vous pouvez également visiter le module _correction de perspective_.

[_retouche_](../../module-reference/processing-modules/retouch.md) / [_correction des taches_](../../module-reference/processing-modules/spot-removal.md) / [_pixels chauds_](../../module-reference/processing-modules/hot-pixels.md)
: Parfois, vous devrez supprimer les taches causées par les poussières du capteur. Le nouveau module _retouche_ et l'ancien module _correction des taches_ sont faits pour cela et peuvent également corriger d'autres éléments perturbants comme les imperfections cutanées. Si votre appareil photo a des pixels défectueux ou a tendance à produire des pixels chauds à des valeurs ISO élevées ou pour des temps d'exposition plus longs, jetez un œil au module _pixels chauds_ pour une correction automatique.

[_balance couleur_](../../module-reference/processing-modules/color-balance.md)
: Il s'agit d'un module polyvalent qui peut être utilisé pour ajuster davantage le contraste et la saturation d'une image. Il peut également être utilisé pour effectuer un étalonnage des couleurs (par exemple, émuler l'étalonnage "orange et bleu sarcelle" (Orange&Teal) utilisé dans les films hollywoodiens, supprimer les rougeurs dans les tons de peau, régler une balance des couleurs inégale dans les ombres/demi-tons/hautes lumières, etc.). Le module [_zone de couleurs_](../../module-reference/processing-modules/color-zones.md) peut également être utile dans les cas où vous ne pouvez pas obtenir l'effet souhaité en utilisant le module _balance couleur_.

[_égaliseur de ton_](../../module-reference/processing-modules/tone-equalizer.md)
: Utilisez ce module pour effectuer des opérations «éclaircir et assombrir» (dodging and burning) et récupérer des détails dans les ombres et les hautes lumières. Ce module génère un masque pour faire la moyenne de la luminance dans différentes parties de l'image, et l'égaliseur vous permet d'augmenter et de diminuer sélectivement les niveaux de luminance à l'aide de ce masque. Il est recommandé de vérifier d'abord que le masque est correctement configuré, puis vous pouvez utiliser les curseurs ou la courbe spline pour ajuster les différents niveaux de luminosité. Vous pouvez également placer le curseur de la souris sur différentes parties de l'image pour voir le niveau IL du masque à ce point, puis utiliser la molette de la souris pour ajuster la luminosité de ce niveau IL en conséquence.

[_contraste local_](../../module-reference/processing-modules/local-contrast.md)
: Ce module peut mettre l'accent sur les détails et améliorer la clarté, et constitue un bon moyen d'améliorer la netteté générale d'une image. Il est recommandé d'utiliser ce module en mode _filtre laplacien local_.

: Une technique plus polyvalente mais aussi plus complexe consiste à utiliser le module [_contrast equalizer_](../../module-reference/processing-modules/contrast-equalizer.md) . Il est très utile pour faire des ajustements où la dimension spatiale joue un rôle. Il a un certain nombre de préréglages qui peuvent être utiles comme point de départ pour comprendre ce module.

[_denoise (profiled)_](../../module-reference/processing-modules/denoise-profiled.md)
: The _denoise (profiled)_ module is usually your best option for reducing noise in an image. This module offers an almost “single-click” solution to remove noise. From a user perspective the effect only depends on camera type and ISO value, both derived from Exif data. All other settings are taken from a database of noise profiles that the darktable team has collected -- now covering well above 300 popular camera models. The simplest way to use this module is _non-local means (auto)_ mode. The wavelet feature of this module is also quite effective against color noise. It is recommended that you use this module at 100% zoom so that you can accurately see the effects of your changes.

: D'autres modules qui permettent le débruitage d'image incluent [_réduction du bruit raw_](../../module-reference/processing-modules/raw-denoise.mf), [_flou de surface_](../../module-reference/processing-modules/surface-blur.md), [_réduction du bruit photo astro_](../../module-reference/processing-modules/astrophoto-denoise.md), et le module [_égaliseur de contraste_](../../module-reference/processing-modules/contrast-equalizer.md), qui est basé sur les ondelettes. Si votre boîtier n'est pas encore pris en charge par le module _réduction du bruit (profil)_, alors le module _réduction du bruit photo astro_ est probablement l'alternative la plus pratique, car elle vous permet de traiter séparément le bruit de couleur et de luminance.

[_suppression de la brume_](../../module-reference/processing-modules/haze-removal.md)
: Ce module fait exactement ce que son nom indique -- il élimine la brume atmosphérique.

[_calibration des couleurs_](../../module-reference/processing-modules/color-calibration.md)
: Ce module propose une gamme de préréglages pour créer des images noir et blanc imitant un film classique. Il peut également être utilisé pour modifier vos matrices de profils de couleurs, par exemple, pour résoudre les problèmes de gamut.

[_correction des objectifs_](../../module-reference/processing-modules/lens-correction.md)
: Si votre combinaison boîtier/objectif est prise en charge, utilisez ce module pour corriger les distorsions d'objectif standard, lorsque les corrections n'ont pas déjà été effectuées par le boîtier. Les modules [_recadrer et pivoter_](../../module-reference/processing-modules/crop-rotate.md) et [_correction de perspective_](../../module-reference/processing-modules/perspective-correction.md) peuvent également être utilisés pour simuler les effets d'un objectif à bascule et décentrement.

# modules à utiliser avec précaution

Il y a certains modules pour lesquels il n'existe pas encore d'alternative bien adaptée au flux de travail relatif à la scène. Si nécessaire, ces modules doivent être utilisés avec parcimonie et prudence.

[_vibrance_](../../module-reference/processing-modules/vibrance.md)
: A tendance à assombrir les couleurs. Pour plus de contrôle, pensez à utiliser le module [_zones de couleurs_](../../module-reference/processing-modules/color-zones.md) avec un masque paramétrique de saturation.

[_zones de couleurs_](../../module-reference/processing-modules/color-zones.md)
: Les transitions peuvent ne pas être gracieuses. Une alternative peut être d'utiliser le module [_balance couleur_](../../module-reference/processing-modules/color-balance.md) avec un masque paramétrique.

[_vignetage_](../../module-reference/processing-modules/vignetting.md)
: Ce module peut produire des résultats d'apparence non naturelle avec une décroissance trop brutale. Vous feriez peut-être mieux d'utiliser le module [_exposition_](../../module-reference/processing-modules/exposure.md) avec un masque elliptique ayant une grande zone de transition, et peut-être en activant en plus le module [_balance couleur_](../../module-reference/processing-modules/color-balance.md) avec le même masque pour réduire la saturation sur les bords.

---

**Remarque :** En utilisant les [modes de fusion](../../darkroom/masking-and-blending/blend-modes.md) sur n'importe quel module, vous devez savoir que de nombreux modes de fusion sont optimisés pour l'espace relatif à l'affichage et supposent une valeur de gris moyen de 50%. Pour l'espace linéaire relatif à la scène, respectez les modes de fusion basés sur des opérations arithmétiques (addition, multiplication, division, soustraction, moyenne), sur des comparaisons maximum/minimum (écran) ou sur des séparations de canaux (teinte, couleur, chroma, etc.).

---

# autres modules à effets artistiques

Il existe également un certain nombre de modules d'effets artistiques disponibles dans darktable. Pour en nommer quelques uns :

- Utilisez le module [_filigrane_](../../module-reference/processing-modules/watermark.md) pour ajouter un filigrane à votre image.

- Utilisez le module [_grain_](../../module-reference/processing-modules/grain.md) pour simuler le bruit typique des photos analogiques.

- Utilisez le module [_mappage des couleurs_](../../module-reference/processing-modules/color-mapping.md) pour transférer l'apparence d'une image couleur sur une autre.

- Utilisez le module [_faible lumière_](../../module-reference/processing-modules/lowlight-vision.md) pour simuler la vision de nuit humaine en rapprochant de la réalité les images en basse lumière.

- Utilisez le module [_filtre dégradé_](../../module-reference/processing-modules/graduated-density.md) pour ajouter un dégradé neutre ou coloré à votre image pour corriger l'exposition et les couleurs.


Veuillez consulter [la référence des modules de traitement](../../module-reference/processing-modules/_index.md) pour une liste des modules disponibles.

# modules à éviter

Il existe un certain nombre de modules qui ne sont plus recommandés pour une utilisation dans un flux de travail relatif à la scène. Cela ne signifie pas qu'ils ne peuvent pas être utilisés, mais ils peuvent produire des effets indésirables lorsque leurs curseurs sont poussés trop loin, et il existe de meilleures alternatives. Dans chaque cas, le module alternatif préférable est répertorié avec une brève explication.

[_mappage local des tonalités (déprécié)_](../../module-reference/processing-modules/tone-mapping.md)
: _préférez [égaliseur de ton](../../module-reference/processing-modules/tone-equalizer.md)_

: Ce module applique un flou bilatéral sur un mappage non linéaire (log) qui peut provoquer des halos et des franges. C'est un problème courant pour les modules exécutant des flous et des occlusions qui opèrent sur un codage non linéaire.

[_mappage global des tonalités (déprécié)_](../../module-reference/processing-modules/global-tonemap.md)
: _préférez [filmique rvb](../../module-reference/processing-modules/filmic-rgb.md)_

: Ce module tente de traiter les images HDR en utilisant l'espace colorimétrique Lab, qui n'est pas bien adapté aux grandes plages dynamiques. Le module _filmique rvb_ fonctionne dans un espace linéaire et peut facilement traiter une large plage de valeurs d'entrée provenant de la scène et les adapter aux plages dynamiques moins grandes exigées par les dispositifs d'affichage et d'impression.

[_ombres et hautes lumières_](../../module-reference/processing-modules/shadows-and-highlights.md)
: _préférez [égaliseur de ton](../../module-reference/processing-modules/tone-equalizer.md)_

: Ce module utilise des flous dans l'espace colorimétrique Lab, ce qui entraîne des problèmes tels que des halos, un contraste local élevé dans les hautes lumières et des décalages de teinte vers le bleu dans les ombres.

[_filtre passe-bas_](../../module-reference/processing-modules/lowpass.md)
: _préférez [égaliseur de contraste](../../module-reference/processing-modules/contrast-equalizer.md) ou [égaliseur de ton](../../module-reference/processing-modules/tone-equalizer.md)_

: Un autre module faisant des flous dans l'espace Lab. Préférez l'_égaliseur de contraste_ pour le flou, ou l'_égaliseur de ton_ si la compression de la plage dynamique locale est nécessaire.

[_filtre passe-haut_](../../module-reference/processing-modules/highpass.md)
: _préférez [égaliseur de contraste](../../module-reference/processing-modules/contrast-equalizer.md) ou [contraste local](../../module-reference/processing-modules/local-contrast.md)_

: Ce module utilise un flou qu'il réalise dans l'espace colorimétrique Lab. Il en résulte les mêmes problèmes qu'avec le module [_filtre passe-bas_](../../module-reference/processing-modules/lowpass.md). Utilisez _égaliseur de contraste_ pour une netteté fine, ou _contraste local_ pour une netteté générale.

[_renforcer la netteté_](../../module-reference/processing-modules/sharpen.md)
: _préférez [égaliseur de contraste](../../module-reference/processing-modules/contrast-equalizer.md) ou [contraste local](../../module-reference/processing-modules/local-contrast.md)_

: L'algorithme USM (UnSharp Mask) utilisé dans le module _renforcer la netteté_ souffre des mêmes problèmes que le module _filtre passe-haut_, et peut facilement provoquer des artefacts. Utilisez les préréglages fournis par le module _égaliseur de contraste_ pour atténuer le flou, ou _contraste local_ pour une netteté générale.

[_monochrome_](../../module-reference/processing-modules/monochrome.md)
: _préférez [calibration des couleurs](../../module-reference/processing-modules/color-calibration.md) (ou [balance couleur](../../module-reference/processing-modules/color-balance.md))_

: Le module _monochrome_ peut être assez compliqué à utiliser. Les préréglages du module _calibration des couleurs_ émulent mieux ce qui se passe physiquement avec un film. Vous pouvez aussi définir à 0 le curseur _saturation en sortie_ du module _balance couleur_ pour une approche plus perceptuelle.

[_lumière d'appoint (déprécié)_](../../module-reference/processing-modules/fill-light.md)
: _préférez [égaliseur de ton](../../module-reference/processing-modules/tone-equalizer.md) (ou [exposition](../../module-reference/processing-modules/exposure.md))_

: Utilisé pour ajouter de la lumière à une scène, ce module utilise à nouveau des flous dans l'espace Lab. L'_égaliseur de ton_ lui fonctionne dans un espace linéaire. Vous pouvez également obtenir un effet similaire en utilisant le module _exposition_ avec un [masque dessiné](../../darkroom/masking-and-blending/masks/drawn.md).

[_lumière d'arrière plan_](../../module-reference/processing-modules/bloom.md)
: _préférez [égaliseur de ton](../../module-reference/processing-modules/tone-equalizer.md) (ou [exposure](../../module-reference/processing-modules/exposure.md))_

: Encore une fois, ce module utilise des flous dans l'espace Lab. Utilisez soit le module _égaliseur de ton_, soit le module _exposition_ avec un [masque paramétrique](../../darkroom/masking-and-blending/masks/parametric.md). Ces deux modules fonctionnent avec des encodages linéaires.

[_zones (déprécié)_](../../module-reference/processing-modules/zone-system.md)
: _préférez [égaliseur de ton](../../module-reference/processing-modules/tone-equalizer.md) (ou [exposition](../../module-reference/processing-modules/exposure.md))_

: Ce module fonctionne à nouveau dans l'espace Lab, et devient problématique si vous le poussez trop loin. Il est préférable d'utiliser l '_égaliseur de ton_ ou plusieurs instances du module _exposition_ avec des masques paramétriques pour définir une zone.

[_correction des couleurs_](../../module-reference/processing-modules/color-correction.md)
: _préférez [balance couleur](../../module-reference/processing-modules/color-balance.md)_

: Préférez le module _balance couleur_, qui fonctionne dans l'espace colorimétrique RVB et permet un réglage facile de la balance des blancs dans les ombres (_offset_), les demi-tons (_power_) et les hautes lumières (_slope_). Notez que les paramètres _offset_, _power_ et _slope_ que nous utilisons normalement dans les espaces linéaires correspondent à peu près aux paramètres _lift_, _gamma_ et _gain_ utilisés dans les espaces non linéaires à encodage gamma.

[_velvia_](../../module-reference/processing-modules/velvia.md)
: _préférez [balance couleur](../../module-reference/processing-modules/color-balance.md)_

: Le curseur _saturation en sortie_ du module _balance couleur_ utilise une logique similaire à celle du module _velvia_, mais sans les décalages de teinte et de luminosité qui peuvent être difficile à gérer.

[_niveaux_](../../module-reference/processing-modules/levels.md)/[niveaux rvb](../../module-reference/processing-modules/rgb-levels.md)
: _préférez [balance couleur](../../module-reference/processing-modules/color-balance.md)_

: Ces modules implémentent essentiellement un sous-ensemble des fonctions du module _balance couleur_, ce qui les rend à peu près redondants.

[_courbe des tonalités_](../../module-reference/processing-modules/tone-curve.md)/[courbe rvb](../../module-reference/processing-modules/rgb-curve.md)
: _préférez [balance couleur](../../module-reference/processing-modules/color-balance.md)_

: These modules are normally used to adjust contrast. Their user interface assumes the mid-gray level is around 50%, but in linear scene-referred space mid-gray is much lower at around 18%. It is better to adjust the contrast in _color balance_ module, where the mid-gray reference point can be set with the _contrast fulcrum_ slider.

[_contraste luminosité saturation_](../../module-reference/processing-modules/contrast-brightness-saturation.md)
: _préférez [balance couleur](../../module-reference/processing-modules/color-balance.md)_

: Ce module fonctionne dans l'espace colorimétrique Lab (avec les limitations que cela implique) et duplique essentiellement les fonctions déjà fournies par le module _color balance_.
