---
title: darktable-cli
id: darktable-cli
weight: 20
draft: false
author: "people"
---

The `darktable-cli` binary starts the command line interface variant of darktable which allows images to be exported.

This variant does not open any display, so it will work in pure console mode without launching a GUI. This mode is particularly useful for servers running background jobs.

`darktable-cli` can be called with the following command line parameters:

```
darktable-cli <input file>|<image folder>
              [<xmp file>]
              <output file>
              [--width <max width>]
              [--height <max height>]
              [--bpp <bpp>]
              [--hq <0|1|true|false>]
              [--upscale <0|1|true|false>]
              [--style <style name>]
              [--style-overwrite]
              [--verbose]
              [--core <darktable options>]
```

The user must supply an input filename and an output filename. All other parameters are optional.

`<input file>`
: The name of the input file or folder (containing images) to be exported.

`<xmp file>`
: The optional name of an XMP sidecar file containing the history stack data to be applied during export. If this option is not provided darktable will search for an XMP file that belongs to the given input file(s).

`<output file>`
: The name of the output file. The export file format is derived from the file extension. You can also use a number of [variables](../variables.md) in the output filename. For obvious reasons this parameter is mandatory if you use the program on an image folder containing multiple images.

`--width <max width>`
: Limit the width of the exported image to the given number of pixels.

`--height <max height>`
: Limit the height of the exported image to the given number of pixels.

`--bpp <bpp>`
: Define the bit depth of the exported image. Permitted values depend on the output file format. 

_Note: This option is not currently functional. If you need to define the bit depth you need to use the following workaround:_

```
    --core
    --conf plugins/imageio/format/<FORMAT>/bpp=<VALUE>
```
_where `<FORMAT>` is the name of the selected output format.__

`--hq <0|1|true|false>`
: Define whether to use high quality resampling during export (see the [export](../../module-reference/utility-modules/lighttable/export-selected.md) module for more details). Defaults to true.

`--upscale <0|1|true|false>`
: Define whether allow upscaling during export. Defaults to false.

`--style <style name>`
: Specify the name of a style to be applied during export. If a style is specified, the path to the darktable configuration directory must also be specified (i.e. `--core --configdir ~/.config/darktable`). Defaults to no style specified.

`--style-overwrite`
: The specified style overwrites the history stack instead of being appended to it.

`--verbose`
: Enables verbose output.

`--core <darktable options>`
: All command line parameters following `--core` are passed to the darktable core and handled as standard parameters. See the [darktable binary](./darktable.md) section for a detailed description.


