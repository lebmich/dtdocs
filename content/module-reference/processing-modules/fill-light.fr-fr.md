---
applicable-version: 3.4
id: fill-light
masking: 'false'
tags: ~
title: 'fill light (deprecated)'
view: darkroom
working-color-space: Lab
---

---

**Please note that this module is deprecated in darktable 3.4 and should no longer be used for new edits. Please use the [_tone equalizer_](./tone-equalizer.md) module or the [_exposure_](./exposure.md) module with a [drawn mask](../../darkroom/masking-and-blending/masks/drawn.md).**

---

Locally modify exposure based on pixel lightness.

This module pushes exposure by increasing lightness with a Gaussian curve of a specified width, centered on a given lightness.

# les contrôles du module

exposure
: The fill-light exposure (EV)

center
: The median lightness impacted by the fill-light. The lightness must be set manually but a color picker can be used to provide a guide based on a sample from the image. The lightness of the selected point/area is displayed in the gradient bar.

width
: The width of the Gaussian curve. This number is expressed in zones, with the full range being 10 zones.