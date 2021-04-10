---
applicable-version: 3.2.1
id: raw-black-white-point
masking: 'false'
tags: ~
title: 'raw black/white point'
view: darkroom
working-color-space: 'Not Applicable (RAW)'
---

Define camera-specific black and white points. 

This module is activated automatically for all raw images. Default settings are applied for all supported cameras. Changes to the defaults are normally not required.

# les contrôles du module

black level 0-3
: The camera-specific black level of the four pixels in the RGGB Bayer pattern. Pixels with values lower than the defined level are considered not to contain valid data.

white point
: The camera-specific white level. All pixels with values above this are likely to be clipped and will be handled accordingly in the [_highlight reconstruction_](./highlight-reconstruction.md) module.
