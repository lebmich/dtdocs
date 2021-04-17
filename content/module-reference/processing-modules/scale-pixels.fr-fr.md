---
applicable-version: 3.2.1
id: scale-pixels
masking: 'false'
tags: ~
title: "mise à l'échelle des pixels"
view: darkroom
working-color-space: RGB
---

Some cameras (such as the Nikon D1X) have rectangular instead of the usual square sensor cells. Without correction this would lead to distorted images. This module applies the required scaling.

darktable detects images that need correction using their Exif data and automatically activates this module where required. For other images the module always remains disabled. 

The module has no controls.
