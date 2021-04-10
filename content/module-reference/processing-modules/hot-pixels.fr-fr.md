---
applicable-version: 3.2.1
id: hot-pixels
masking: 'true'
tags: ~
title: 'hot pixels'
view: darkroom
working-color-space: 'Not Applicable (RAW)'
---

Automatically detect and eliminate hot pixels. 

Hot pixels are pixels which have failed to record a light level correctly. Detected hot pixels are replaced by an average of their neighbors.

# les contrôles du module

threshold
: How strong a pixel's value needs to deviate from that of its neighbors to be regarded as a hot pixel.

strength
: The blending strength of the hot pixels with their surrounding.

detect by 3 neighbours
: Extend the detection of hot pixels -- regard a pixel as hot if a minimum of only three (instead of four) neighbor pixels deviate by more than the threshold level.

mark fixed pixels
: Visually mark the corrected pixels on the image and display a count of hot pixels that have been fixed
