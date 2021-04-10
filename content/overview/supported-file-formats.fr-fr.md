---
author: people
draft: 'false'
id: supported-file-formats
title: 'formats de fichier supportés'
weight: 20
---

darktable supports a huge number of file formats from various camera manufacturers. In addition darktable can read specific low dynamic range and high dynamic range images -- mainly for data exchange between darktable and other software.

Pour que darktable puisse importer un fichier, il doit avoir l’une des extensions suivantes (la casse n’a pas d’importance) : `3FR, ARI, ARW, BAY, BMQ, CAP, CINE, CR2, CRW, CS1, DC2, DCR, DNG, GPR, ERF, FFF, EXR, IA, IIQ, JPEG, JPG, K25, KC2, KDC, MDC, MEF, MOS, MRW, NEF, NRW, ORF, PEF, PFM, PNG, PXN, QTK, RAF, RAW, RDC, RW1, RW2, SR2, SRF, SRW, STI, TIF, TIFF, X3F`

Si darktable a été compilé avec la prise en charge de JPEG2000, les extensions suivantes sont aussi reconnues : `J2C, J2K, JP2, JPC`.

En plus de celles qui sont standard, les extensions suivantes sont reconnues si darktable a été compilé avec la prise en charge de GraphicsMagick : `BMP, DCM, GIF, JNG, JPC, JP2, MIFF, MNG, PBM, PGM, PNM, PPM`.

# fichier RAW de l'appareil

darktable lit les fichiers RAW en utilisant la bibliothèque open source [RawSpeed](https://github.com/darktable-org/rawspeed), originellement développée par Klaus Post et maintenue à présent dans le projet darktable lui-même. Le nombre d’appareils et de formats de fichier pris en charge est en constante augmentation. La plupart des appareils modernes sont pris en charge et la tendance est d'ajouter les nouveaux très rapidement. En donner la liste exhaustive dépasse le cadre de ce manuel.

À l'exception des appareils Fujifilm X-Trans, darktable ne décode pas les images provenant d'appareils n'ayant pas un capteur Bayer (ex. les appareils Sigma avec le capteur Foveon X3).

# autres fichiers image

darktable natively reads “ordinary” images in JPEG, 8-bit/16-bit PNG and 8-bit/16-bit TIFF format, as well as 16-bit/32-bit floating point TIFF formats. JPEG2000 is also supported if the required libraries are present at compile time. Similarly, if darktable was compiled with GraphicsMagick support, there are further supported formats, such as GIF, Dicom DCM, additional "exotic" TIFF formats, and some of Sun's “portable xyz-map” family.

darktable lit aussi les images à grande plage dynamique dans les formats OpenEXR, RVBE et PFM.

