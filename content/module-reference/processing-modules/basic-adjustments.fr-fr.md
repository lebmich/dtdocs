---
applicable-version: 3.6
id: basic-adjustments
masking: ~
tags: ~
title: 'basic adjustments (deprecated)'
view: darkroom
working-color-space: ~
---

---

**Please note that this module is deprecated in darktable 3.6 and should no longer be used for new edits. Please use the [quick access panel](../../darkroom/organization/quick-access-panel.md) instead.**

---

A convenience module that combines controls from [_exposure_](./exposure.md), [_highlight reconstruction_](./highlight-reconstruction.md), [_color balance_](./color-balance.md) and [_vibrance_](./vibrance.md) into a single module. 

While this module can provide a quick and convenient way to make simple adjustments to an image, it must be used with care. Normally exposure adjustments should come before [input color profile](./input-color-profile.md) in the pixelpipe, and color adjustments should come after. Because the _basic adjustments_ module combines all of these functions into a single operation in the pixelpipe, it may not play nicely with other modules. Therefore, if you plan to use _basic adjustments_ with other modules, please instead consider using the [_exposure_](exposure.md) + [_base curve_](base-curve.md) / [_tone curve_](tone-curve.md) / [filmic rgb](filmic-rgb.md) + [_color balance_](color-balance.md) modules so that these operations occur in the correct places in the pixelpipe.

# les contrôles du module

black level correction
: Equivalent to black level correction in the [_exposure_](exposure.md) module, this slider defines the threshold at which dark gray values are cut off to pure black. Reducing this can bring some dark colors back into gamut. Increasing this slider may appear to increase the contrast and pop of an image, but it can push dark colors out of gamut, and clipped data cannot be recovered further down the pixel pipe. To control the contrast in the shadows, it is better to use other modules such as [_tone curve_](tone-curve.md) or [_levels_](levels.md), which mitigate these negative impacts further down the pixel pipeline.

exposure
: Adjust exposure compensation. Adding 1 EV of exposure compensation is equivalent to doubling the exposure time in camera, opening the aperture by 1 stop, or doubling the ISO. 

: Positive exposure corrections will make the image brighter. As a side effect noise level is increased. Depending on the basic noise level of your camera and the ISO value of your image, positive exposure compensations with up to 1EV or 2EV should still give reasonable results.

: Negative exposure corrections will make the image darker. Given the nature of digital images this can not correct for fully blown out highlights but allows you to reconstruct data if only some of the RGB channels are clipped (see the [_highlight reconstruction_](highlight-reconstruction.md) module for information on how to deal with clipped pixels).

highlight compression
: Compress the highlights of the image in order to recover detail.

contrast
: Equivalent to the _contrast_ slider in the [_color balance_](color-balance.md) module, this is used to increase the separation of luminance values around a fulcrum point, in effect making the tone curve steeper. The _middle gray_ slider sets the fulcrum point for the contrast, and any pixels whose luminance matches this middle gray point will be unaffected. Pixels brighter than the middle gray point will become even brighter, and pixels darker darker than the middle gray point will become even darker.

préserver les couleurs
: Si une courbe de tonalité non linéaire est appliquée à chacun des canaux rvb individuellement, alors la quantité de réglage de ton appliqué à chaque canal de couleur peut être différente, ce qui peut provoquer des changements de teinte. Par conséquent, le menu _préserver les couleurs_ fournit différentes méthodes de calcul du "niveau de luminance" d'un pixel. La quantité de réglage de la tonalité est calculée en fonction de cette valeur de luminance, puis ce même réglage est appliqué aux trois canaux rvb. Différents estimateurs de luminance peuvent affecter le contraste dans différentes parties de l'image, en fonction des caractéristiques spécifiques de cette image. L'utilisateur peut donc choisir un estimateur particulier qui fournit les meilleurs résultats pour l'image donnée.

middle gray
: Set the fulcrum point for the _contrast_ slider. This is equivalent to the _contrast fulcrum_ slider on the [_color balance_](color-balance.md) module. If the contrast slider is set to 0 this slider will not have any effect.

brightness
: Equivalent to increasing the _gamma factor_ slider in the [_color balance_](color-balance.md) module. Moving the slider to the right will increase the brightness of the image, with an emphasis on the mid-tones.

saturation
: Equivalent to the _output saturation_ slider on the [_color balance_](color-balance.md) module, this slider affects the saturation, or brilliance and intensity of the colors. Moving the slider to the right will increase the amount of color in the image; moving the slider to the left will reduce the amount of color in the image.

vibrance
: Accentuate the colors of the image without adding unnatural colors, as it's often the case with the _saturation_ slider. It works by reducing the lightness of already saturated pixels to make the colors more vivid. You can also achieve some interesting effects by combining it with the saturation slider to target more or less saturated areas of the image.

auto
: Automatically adjust the exposure, taking into account the entire image, or use the color picker to select a rectangular area of the image -- the exposure will be automatically adjusted based on the selected region. This allows you to prioritise which parts of the image should be well-exposed.

clip
: This affects the number of pixels that will be clipped to black or white during the auto-exposure calculation. Moving this slider to the right will allow more pixels to be clipped and increase the contrast; moving this slider to the left will compress the image more and lower the contrast.

