---
applicable-version: 3.4
id: tone-mapping
masking: 'true'
tags: ~
title: 'tone mapping (deprecated)'
view: darkroom
working-color-space: RGB
---

---

**Please note that this module is deprecated in darktable 3.4 and should no longer be used for new edits. Please use the [_tone equalizer_](./tone-equalizer.md) module instead.**

---

Compress the tonal range of HDR images so that they fit into the limits of an LDR image, using Durand's 2002 algorithm. 

The underlying algorithm uses a bilateral filter to decompose an image into a coarse base layer and a detail layer. The contrast of the base layer is compressed, while the detail layer is preserved, then both layers are re-combined.

# les contrôles du module

contrast compression
: The contrast compression level of the base layer. A higher compression will make the image fit a lower dynamic range.

spatial extent
: The spatial extent of the bilateral filter. Lower values cause the contrast compression to have stronger effects on image details.