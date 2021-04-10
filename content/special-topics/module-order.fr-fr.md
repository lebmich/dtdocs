---
author: people
draft: 'false'
id: module-order
title: 'ordre des modules par défaut'
weight: 70
---

Les sections suivantes décrivent l'ordre des modules par défaut dans le nouveau flux de travail relatif à la scène et le flux de travail originel relatif à l'affichage. Notez que dans les sections suivantes, l'ordre des modules va du haut (fichier d'entrée) au bas (image de sortie).

# ordre des modules relatif à la scène

L'ordre par défaut des modules lors de l'utilisation du nouveau flux de travail relatif à la scène est le suivant :

1. [**point noir/blanc raw**](../module-reference/processing-modules/raw-black-white-point.md)

2. [inverser (déprécié)](../module-reference/processing-modules/invert.md)

2. [**balance des blancs**](../module-reference/processing-modules/white-balance.md)

2. [**reconstruire hautes lumières**](../module-reference/processing-modules/highlight-reconstruction.md)

2. [aberrations chromatiques](../module-reference/processing-modules/chromatic-aberrations.md)

2. [pixels chauds](../module-reference/processing-modules/hot-pixels.md)

2. [_réduction du bruit raw_](../module-reference/processing-modules/raw-denoise.md)

2. [dématriçage](../module-reference/processing-modules/demosaic.md)

2. [réduction du bruit (profil)](../module-reference/processing-modules/denoise-profiled.md)

2. [_flou de surface_](../module-reference/processing-modules/surface-blur.md)

2. [_rotation des pixels_](../module-reference/processing-modules/rotate-pixels.md)

2. [_mise à l'échelle des pixels_](../module-reference/processing-modules/scale-pixels.md)

2. [correction des objectifs](../module-reference/processing-modules/lens-correction.md)

2. [suppression de la brume](../module-reference/processing-modules/haze-removal.md)

2. [correction de perspective](../module-reference/processing-modules/perspective-correction.md)

2. [**orientation**](../module-reference/processing-modules/orientation.md)

2. [recadrer et pivoter](../module-reference/processing-modules/crop-rotate.md)

2. [liquéfier](../module-reference/processing-modules/liquify.md)

2. [correction des taches](../module-reference/processing-modules/spot-removal.md)

2. [retouche](../module-reference/processing-modules/retouch.md)

2. [**exposition**](../module-reference/processing-modules/exposure.md)

2. [mappage des tonalités (déprécié)](../module-reference/processing-modules/tone-mapping.md)

2. [égaliseur de ton](../module-reference/processing-modules/tone-equalizer.md)

2. [filtre dégradé](../module-reference/processing-modules/graduated-density.md)

2. [correction du profil d'entrée](../module-reference/processing-modules/unbreak-input-profile.md)

2. _égaliseur originel_

2. [**profil de couleur d'entrée**](../module-reference/processing-modules/input-color-profile.md)

2. [docteur néga](../module-reference/processing-modules/negadoctor.md)

2. [_réduction du bruit photo astro_](../module-reference/processing-modules/astrophoto-denoise.md)

2. [table correspondance couleurs](../module-reference/processing-modules/color-look-up-table.md)

2. [suppression des franges](../module-reference/processing-modules/defringe.md)

2. [égaliseur de contraste](../module-reference/processing-modules/contrast-equalizer.md)

2. [filtre passe-bas](../module-reference/processing-modules/lowpass.md)

2. [filtre passe-haut](../module-reference/processing-modules/highpass.md)

2. [renforcer la netteté](../module-reference/processing-modules/sharpen.md)

2. [3D lut](../module-reference/processing-modules/lut-3D.md)

2. [mappage des couleurs](../module-reference/processing-modules/color-mapping.md)

2. [mixeur de canaux (déprécié)](../module-reference/processing-modules/channel-mixer.md)

2. [ajustement de base](../module-reference/processing-modules/basic-adjustments.md)

2. [balance couleur](../module-reference/processing-modules/color-balance.md)

2. [_courbe rvb_](../module-reference/processing-modules/rgb-curve.md)

2. [_niveaux rvb_](../module-reference/processing-modules/rgb-levels.md)

2. [_courbe de base_](../module-reference/processing-modules/base-curve.md)

2. _filmique (originel)_

2. [**filmique rvb**](../module-reference/processing-modules/filmic-rgb.md) -- passage de l'espace relatif à la scène à l'espace relatif à l'affichage

2. [_contraste lum. saturation_](../module-reference/processing-modules/contrast-brightness-saturation.md)

2. [_courbe des tonalités_](../module-reference/processing-modules/tone-curve.md)

2. [_niveaux_](../module-reference/processing-modules/levels.md)

2. [_ombres et hautes lumières_](../module-reference/processing-modules/shadows-and-highlights.md)

2. [_zones (déprécié)_](../module-reference/processing-modules/zone-system.md)

2. [_mappage global des tonalités (deprecated)_](../module-reference/processing-modules/global-tonemap.md)

2. [_lumière d'appoint (déprécié)_](../module-reference/processing-modules/fill-light.md)

2. [contraste local](../module-reference/processing-modules/local-contrast.md)

2. [_correction des couleurs_](../module-reference/processing-modules/color-correction.md)

2. [_contraste de couleur_](../module-reference/processing-modules/color-contrast.md)

2. [velvia](../module-reference/processing-modules/velvia.md)

2. [vibrance](../module-reference/processing-modules/vibrance.md)

2. [zones de couleurs](../module-reference/processing-modules/color-zones.md)

2. [_lumière d'arrière-plan_](../module-reference/processing-modules/bloom.md)

2. [coloriser](../module-reference/processing-modules/colorize.md)

2. [faible lumière](../module-reference/processing-modules/lowlight-vision.md)

2. [_monochrome_](../module-reference/processing-modules/monochrome.md)

2. [grain](../module-reference/processing-modules/grain.md)

2. [effet Orton (adoucir)](../module-reference/processing-modules/soften.md)

2. [virage partiel](../module-reference/processing-modules/split-toning.md)

2. [vignetage](../module-reference/processing-modules/vignetting.md)

2. [reconstruction des couleurs](../module-reference/processing-modules/color-reconstruction.md)

2. [**profil de couleur de sortie**](../module-reference/processing-modules/output-color-profile.md)

2. [ homogénéisation](../module-reference/processing-modules/dithering.md)

2. [cadre décoratif](../module-reference/processing-modules/framing.md)

2. [filigrane](../module-reference/processing-modules/watermark.md)


**key :**
* _italic_ : non recommandé pour le flux de travail relatif à la scène
* **bold** : module activé par défaut

# ordre des modules originel/relatif à l'affichage

L'ordre par défaut des modules lors de l'utilisation de l'ancien flux de travail relatif à l'affichage est le suivant :

1. [**point noir/blanc raw**](../module-reference/processing-modules/raw-black-white-point.md)

2. [inverser (déprécié)](../module-reference/processing-modules/invert.md)

2. [**balance des blancs**](../module-reference/processing-modules/white-balance.md)

2. [**reconstruire hautes lumières**](../module-reference/processing-modules/highlight-reconstruction.md)

2. [aberrations chromatiques](../module-reference/processing-modules/chromatic-aberrations.md)

2. [pixels chauds](../module-reference/processing-modules/hot-pixels.md)

2. [réduction du bruit raw](../module-reference/processing-modules/raw-denoise.md)

2. [dématriçage](../module-reference/processing-modules/demosaic.md)

2. [réduction du bruit (profil)](../module-reference/processing-modules/denoise-profiled.md)

2. [mappage des tonalités (déprécié)](../module-reference/processing-modules/tone-mapping.md)

2. [exposition](../module-reference/processing-modules/exposure.md)

2. [correction des taches](../module-reference/processing-modules/spot-removal.md)

2. [retouche](../module-reference/processing-modules/retouch.md)

2. [correction des objectifs](../module-reference/processing-modules/lens-correction.md)

2. [correction de perspective](../module-reference/processing-modules/perspective-correction.md)

2. [liquéfier](../module-reference/processing-modules/liquify.md)

2. [rotation des pixels](../module-reference/processing-modules/rotate-pixels.md)

2. [mise à l'échelle des pixels](../module-reference/processing-modules/scale-pixels.md)

2. [orientation](../module-reference/processing-modules/orientation.md)

2. [recadrer et pivoter](../module-reference/processing-modules/crop-rotate.md)

2. [égaliseur de ton](../module-reference/processing-modules/tone-equalizer.md)

2. [filtre dégradé](../module-reference/processing-modules/graduated-density.md)

2. [**courbe de base**](../module-reference/processing-modules/base-curve.md)  -- transition par défaut entre l'espace relatif à la scène et l'espace relatif à l'affichage

2. [flou de surface](../module-reference/processing-modules/surface-blur.md)

2. [correction du profil d'entrée](../module-reference/processing-modules/unbreak-input-profile.md)

2. [suppression de la brume](../module-reference/processing-modules/haze-removal.md)

2. [**profil de couleur d'entrée**](../module-reference/processing-modules/input-color-profile.md)

2. [docteur néga](../module-reference/processing-modules/negadoctor.md)

2. [ajustement de base](../module-reference/processing-modules/basic-adjustments.md)

2. [reconstruction des couleurs](../module-reference/processing-modules/color-reconstruction.md)

2. [table correspondance couleurs](../module-reference/processing-modules/color-look-up-table.md)

2. [suppression des franges](../module-reference/processing-modules/defringe.md)

2. égaliseur originel

2. [vibrance](../module-reference/processing-modules/vibrance.md)

2. [balance couleur](../module-reference/processing-modules/color-balance.md)

2. [coloriser](../module-reference/processing-modules/colorize.md)

2. [mappage des couleurs](../module-reference/processing-modules/color-mapping.md)

2. [lumière d'arrière-plan](../module-reference/processing-modules/bloom.md)

2. [réduction du bruit photo astro ](../module-reference/processing-modules/astrophoto-denoise.md)

2. [mappage global des tonalités (déprécié)](../module-reference/processing-modules/global-tonemap.md)

2. [ombre et hautes lumières](../module-reference/processing-modules/shadows-and-highlights.md)

2. [égaliseur de contraste](../module-reference/processing-modules/contrast-equalizer.md)

2. [contraste local](../module-reference/processing-modules/local-contrast.md)

2. [zones de couleurs](../module-reference/processing-modules/color-zones.md)

2. [faible lumière](../module-reference/processing-modules/lowlight-vision.md)

2. [monochrome](../module-reference/processing-modules/monochrome.md)

2. filmique (originel)

2. [filmique rvb](../module-reference/processing-modules/filmic-rgb.md)

2. [contraste lum. saturation](../module-reference/processing-modules/contrast-brightness-saturation.md)

2. [zones (déprécié)](../module-reference/processing-modules/zone-system.md)

2. [courbe des tonalités](../module-reference/processing-modules/tone-curve.md)

2. [niveaux](../module-reference/processing-modules/levels.md)

2. [niveaux rvb](../module-reference/processing-modules/rgb-levels.md)

2. [courbe rvb](../module-reference/processing-modules/rgb-curve.md)

2. [lumière d'appoint (déprécié)](../module-reference/processing-modules/fill-light.md)

2. [correction des couleurs](../module-reference/processing-modules/color-correction.md)

2. [**renforcer la netteté**](../module-reference/processing-modules/sharpen.md)

2. [filtre passe-bas](../module-reference/processing-modules/lowpass.md)

2. [filtre passe-haut](../module-reference/processing-modules/highpass.md)

2. [grain](../module-reference/processing-modules/grain.md)

2. [3D lut](../module-reference/processing-modules/lut-3D.md)

2. [contraste de couleur](../module-reference/processing-modules/color-contrast.md)

2. [**profil de couleur de sortie**](../module-reference/processing-modules/output-color-profile.md)

2. [mixeur de canaux (déprécié)](../module-reference/processing-modules/channel-mixer.md)

2. [effet Orton (adoucir)](../module-reference/processing-modules/soften.md)

2. [vignetage](../module-reference/processing-modules/vignetting.md)

2. [virage partiel](../module-reference/processing-modules/split-toning.md)

2. [velvia](../module-reference/processing-modules/velvia.md)

2. [ homogénéisation](../module-reference/processing-modules/dithering.md)

2. [cadre décoratif](../module-reference/processing-modules/framing.md)

2. [filigrane](../module-reference/processing-modules/watermark.md)

