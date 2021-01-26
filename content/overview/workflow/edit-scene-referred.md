---
title: "développer une image : flux de travail relatif à la scène"
id: edit-scene-referred
draft: false
weight: 30
author: "traduction : Michel Leblond"
---

Le flux de travail _relatif à la scène_ met l'accent sur l'exécution, par pipeline graphique, du traitement d'image dans la partie linéaire relative à la scène. Cela permet de réduire les artefacts et les décalages de couleur qui peuvent résulter du traitement des valeurs non linéaires des pixels. En découplant le traitement d'image des caractéristiques d'un écran spécifique, il sera plus facile d'adapter ultérieurement votre travail à de nouveaux supports d'affichage, tels que les affichages à plage dynamique élevée.

Ceci étant la méthode recommandée pour traiter les images dans les versions 3.0 et supérieures, cette section fournira un aperçu beaucoup plus complet que la section suivante sur le flux de travail _relatif à l'affichage_.

# étapes basiques
Le traitement de base d'une image dans le flux de travail relatif à la scène demande, au minimum, de prendre en compte les étapes suivantes pour rendre à l'écran une image correcte :

prendre une photo
: Utilisez votre appareil photo pour prendre une photo correctement exposée. Normalement, vous pouvez compter sur les fonctions de mesure et d'exposition automatiques du boîtier. Cependant, pour certaines scènes, vous devrez peut-être utiliser la molette de compensation d'exposition du boîtier ou les réglages manuels pour obtenir une exposition optimale. En général, vous souhaitez rendre l'exposition de l'appareil photo aussi lumineuse que possible sans tronquer les hautes lumières. Ceci est connu sous le nom d '«exposition à droite» (ETTR) et vous permet de tirer le meilleur parti de la plage dynamique du capteur. De nombreux appareils photo ont des fonctionnalités telles que "zébrures" ou "clignotements" pour vous avertir lorsque vous êtes en danger d'écrêtage.

[_exposition_](../../module-reference/processing-modules/exposure.md)
: Ce module est activé par défaut. Il inclura une augmentation d'exposition initiale de +0,5&nbsp;IL pour imiter le traitement standard de la plupart des boîtiers fournissant des JPEG intégrés. Les systèmes de mesure des boîtiers varient et certains modèles peuvent nécessiter une augmentation d'exposition légèrement plus importante (par exemple +0,8&nbsp;IL à +1,5&nbsp;IL), auquel cas vous pouvez créer un  [préréglage](../../darkroom/interacting-with-modules/presets.md) automatique adéquat. Le module d'exposition détectera si la molette de compensation d'exposition du boîtier a été utilisée (voir les remarques ci-dessus sur l'ETTR) et réajustera l'exposition en conséquence.

: Utilisez le curseur d'exposition pour régler les demi-tons de l'image à un niveau de luminosité approprié. À ce stade, ne vous inquiétez pas des hautes lumières et des ombres - elles seront traitées plus tard.

: Vous pouvez également cliquer et faire glisser sur l'histogramme pour modifier l'exposition, mais cela donne moins de contrôle que d'utiliser le curseur du module _exposition_. Bien que vous puissiez utiliser le module _exposition_ pour ajuster le niveau de noir pour fournir plus de contraste, vous devez faire très attention en faisant cela car vous pouvez vous retrouver avec des valeurs RVB négatives.

[_balance des blancs_](../../module-reference/processing-modules/white-balance.md)
: Il est important que la balance des blancs soit correctement réglée pour former une base solide pour le traitement ultérieur. Le boîtier stockera normalement dans les métadonnées du fichier Raw, le réglage de la balance des blancs sélectionnée et darktable l'utilisera comme point de départ. Pour obtenir une balance des blancs plus précise, vous pouvez soit utiliser la pipette à couleurs pour sélectionner dans l'image un ton de gris neutre, soit, le cas échéant, passer à un autre préréglage de la balance des blancs de votre boîtier. Des ajustements fins de la balance des blancs globale sont effectués à l'aide du curseur _température_ et, moins souvent, du curseur _teinte_. Déplacer le curseur _température_ vers la gauche rend l'image plus froide (plus bleue), et le déplacer vers la droite la rend plus chaude (plus orange).

: Le module _balance des blancs_ ne peut effectuer que des réglages _globaux_ de la balance des blancs de l'image. Le module [_balance couleur_](../../module-reference/processing-modules/color-balance.md), entre autres, vous donne plus de contrôle dans les cas où une scène a été éclairée par plusieurs sources de lumière avec différentes températures de couleur.

[_filmique rvb_](../../module-reference/processing-modules/filmic-rgb.md)
: Ce module effectue un mappage avec compression des tonalités de la plage dynamique élevée de l'image capturée vers la plage dynamique moins élevée du support d'affichage. Le niveau de ton gris moyen a déjà été réglé (ci-dessus) avec le module _exposition_. Filmique proposera, sur son onglet _scène_, un point blanc et un point noir appropriés pour l'image - vous devrez peut-être les ajuster pour une scène particulière. Sur l'onglet _look_, vous pouvez ajuster les paramètres de contraste et de saturation des tons moyens si nécessaire.

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

[_égaliseur de contraste_](../../module-reference/processing-modules/contrast-equalizer.md)
: Une technique plus polyvalente mais aussi plus complexe consiste à utiliser ce module. Il est très utile pour faire des ajustements où la dimension spatiale joue un rôle. Il a un certain nombre de préréglages qui peuvent être utiles comme point de départ pour comprendre ce module.

[_réduction du bruit (profil)_](../../module-reference/processing-modules/denoise-profiled.md)
: Le module _réduction du bruit(profil)_ est généralement votre meilleure option pour réduire le bruit dans une image. Ce module offre une solution quasiment «en un seul clic» pour supprimer le bruit. Du point de vue de l'utilisateur, l'effet dépend uniquement du type de boîtier et de la valeur ISO, tous deux dérivés des données Exif. Tous les autres paramètres sont extraits d'une base de données de profils de bruit que l'équipe de darktable a collectée - couvrant désormais bien plus de 300 modèles d'appareils photo populaires. La manière la plus simple d'utiliser ce module est le mode _moyennes non-locales auto_. Le mode _ondelettes_ de ce module est également assez efficace contre le bruit de couleur. Il est recommandé d'utiliser ce module avec un zoom de 100% afin de pouvoir voir avec précision les effets de vos modifications.

: D'autres modules qui permettent le débruitage d'image incluent [_réduction du bruit RAW_](../../module-reference/processing-modules/raw-denoise.mf), [_flou de surface_](../../module-reference/processing-modules/surface-blur.md), [_réduction du bruit photo astro_](../../module-reference/processing-modules/astrophoto-denoise.md), et le module [_égaliseur de contraste_](../../module-reference/processing-modules/contrast-equalizer.md), qui est basé sur les ondelettes. Si votre boîtier n'est pas encore pris en charge par le module _réduction du bruit (profil)_, alors le module _réduction du bruit photo astro_ est probablement l'alternative la plus pratique, car elle vous permet de traiter séparément le bruit de couleur et de luminance.

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

**Note:** En utilisant les [modes de fusion](../../darkroom/masking-and-blending/blend-modes.md) sur n'importe quel module, vous devez savoir que de nombreux modes de fusion sont optimisés pour l'espace relatif à l'affichage et supposent une valeur de gris moyen de 50%. Pour l'espace linéaire relatif à la scène, respectez les modes de fusion basés sur des opérations arithmétiques (addition, multiplication, division, soustraction, moyenne), sur des comparaisons maximum/minimum (écran) ou sur des séparations de canaux (teinte, couleur, chroma, etc.).

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

There are a number of modules which are no longer recommended for use within a scene-referred workflow. This doesn't mean they can't be used, but they can produce undesirable effects when their sliders are pushed too far, and there are better alternatives. In each case, the preferred alternative module is listed along with a brief explanation.

[_local tone mapping (deprecated)_](../../module-reference/processing-modules/tone-mapping.md)
: _prefer [tone equalizer](../../module-reference/processing-modules/tone-equalizer.md)_

: This module applies a bilateral blur over a non-linear (log) mapping that can provoke halos and fringing. This is common issue for modules performing blurs and occlusions that operate over a non-linear encoding.

[_global tonemap (deprecated)_](../../module-reference/processing-modules/global-tonemap.md)
: _prefer [filmic rgb](../../module-reference/processing-modules/filmic-rgb.md)_

: This module tries to deal with HDR images using the Lab color space, which is not well suited for high dyanamic ranges. The _filmic rgb_ module operates in a linear space and can easily scale over a wide range of input values from the scene and fit them into the narrower dynamic range demanded by display and printing devices.

[_shadows and highlights_](../../module-reference/processing-modules/shadows-and-highlights.md)
: _prefer [tone equalizer](../../module-reference/processing-modules/tone-equalizer.md)_

: This module works with blurs in Lab color space, resulting in problems including halos, high local contrast in highlights and hue shifts towards blue in the shadows.

[_lowpass_](../../module-reference/processing-modules/lowpass.md)
: _prefer [contrast equalizer](../../module-reference/processing-modules/contrast-equalizer.md) or [tone equalizer](../../module-reference/processing-modules/tone-equalizer.md)_

: Another module doing blurs in Lab space. Prefer the _contrast equalizer_ for blurring, or the _tone equalizer_ if local dynamic range compression is needed.

[_highpass_](../../module-reference/processing-modules/highpass.md)
: _prefer [contrast equalizer](../../module-reference/processing-modules/contrast-equalizer.md) or [local contrast](../../module-reference/processing-modules/local-contrast.md)_

: Uses a blur performed in Lab space, so has the same problems as with the [_lowpass_](../../module-reference/processing-modules/lowpass.md) module. Use _contrast equalizer_ for fine sharpness, or _local contrast_ for general sharpness.

[_sharpen_](../../module-reference/processing-modules/sharpen.md)
: _prefer [contrast equalizer](../../module-reference/processing-modules/contrast-equalizer.md) or [local contrast](../../module-reference/processing-modules/local-contrast.md)_

: The USM algorithm used in the _sharpen_ module suffers from same issues as the _highpass_ module, and can easily cause artifacts. Use the presets offered by the _contrast equalizer_ for de-blurring, or _local contrast_ for general sharpness.

[_monochrome_](../../module-reference/processing-modules/monochrome.md)
: _prefer [color calibration](../../module-reference/processing-modules/color-calibration.md) (or [color balance](../../module-reference/processing-modules/color-balance.md))_

: The _monochrome_ module can be quite fiddly to use. The _color calibration_ presets better emulate what physically happens with film, or you can set the _output saturation_ slider in the _color balance_ module to 0% for a more perceptual approach.

[_fill light (deprecated)_](../../module-reference/processing-modules/fill-light.md)
: _prefer [tone equalizer](../../module-reference/processing-modules/tone-equalizer.md) (or [exposure](../../module-reference/processing-modules/exposure.md))_

: Used to add light to a scene, this module again uses blurs in Lab space. The _tone equalizer_ works in linear space, or you can also achieve a similar effect by using the _exposure_ module with a [drawn mask](../../darkroom/masking-and-blending/masks/drawn.md).

[_bloom_](../../module-reference/processing-modules/bloom.md)
: _prefer [tone equalizer](../../module-reference/processing-modules/tone-equalizer.md) (or [exposure](../../module-reference/processing-modules/exposure.md))_

: Again, this module uses blurs in Lab space. Either use the _tone equalizer_ module or the _exposure_ module with a [parametric mask](../../darkroom/masking-and-blending/masks/parametric.md), both of which operate with linear encodings.

[_zone system (deprecated)_](../../module-reference/processing-modules/zone-system.md)
: _prefer [tone equalizer](../../module-reference/processing-modules/tone-equalizer.md) (or [exposure](../../module-reference/processing-modules/exposure.md))_

: This module again operates in Lab space, and becomes problematic if you push it too far. It is better to use the _tone equalizer_ or multiple instances of the _exposure_ module with parametric masks to narrow down on a zone.

[_color correction_](../../module-reference/processing-modules/color-correction.md)
: _prefer [color balance](../../module-reference/processing-modules/color-balance.md)_

: Prefer the _color balance_ module, which works in RGB color space and allows easy adjustment of the white balance in shadows (_offset_), midtones (_power_) and highlights (_slope_). Note the _offset_, _power_ and _slope_ that we normally use in linear spaces roughly correspond to the _lift_, _gamma_ and _gain_ parameters used in non-linear gamma-encoded spaces.

[_velvia_](../../module-reference/processing-modules/velvia.md)
: _prefer [color balance](../../module-reference/processing-modules/color-balance.md)_

: The _output saturation_ slider of the _color balance_ module uses similar logic as the _velvia_ module, but without the hue and brightness shifts, which can be difficult to manage.

[_levels_](../../module-reference/processing-modules/levels.md)/[rgb levels](../../module-reference/processing-modules/rgb-levels.md)
: _prefer [color balance](../../module-reference/processing-modules/color-balance.md)_

: These modules basically implement a subset of the functions of the _color balance_ module, which pretty much makes them redundant.

[_tone curve_](../../module-reference/processing-modules/tone-curve.md)/[rgb curve](../../module-reference/processing-modules/rgb-curve.md)
: _prefer [color balance](../../module-reference/processing-modules/color-balance.md)_

: These modules are normally used to adjust contrast. Their user interface assumes the mid-grey level is around 50%, but in linear scene-referred space mid-grey is much lower at around 18%. It is better to adjust the contrast in _color balance_ module, where the mid-grey reference point can be set with the _contrast fulcrum_ slider.

[_contrast brightness saturation_](../../module-reference/processing-modules/contrast-brightness-saturation.md)
: _prefer [color balance](../../module-reference/processing-modules/color-balance.md)_

: This module works in Lab color space (with the limitations that implies) and basically duplicates functions already provided by _color balance_.
