---
title: formats de fichier supportés
id: supported-file-formats
draft: false
weight: 20
author: "people"
---

darktable prend en charge un grand nombre de formats de divers fabricants d’appareils. De plus, il peut lire des images de petite plage dynamique et de grande plage
dynamique – principalement pour des échanges de données avec d’autres logiciels.

Pour que darktable puisse importer un fichier, il doit avoir l’une des extensions suivantes (la casse n’a pas d’importance) : `3FR, ARI, ARW, BAY, BMQ, CAP, CINE, CR2, CRW, CS1, DC2, DCR, DNG, GPR, ERF, FFF, EXR, IA, IIQ, JPEG, JPG, K25, KC2, KDC, MDC, MEF, MOS, MRW, NEF, NRW, ORF, PEF, PFM, PNG, PXN, QTK, RAF, RAW, RDC, RW1, RW2, SR2, SRF, SRW, STI, TIF, TIFF, X3F`

Si darktable a été compilé avec la prise en charge de JPEG2000, les extensions suivantes
sont aussi reconnues : `J2C, J2K, JP2, JPC`.

En plus de celles qui sont standard, les extensions suivantes sont reconnues si darktable
a été compilé avec la prise en charge de GraphicsMagick : `BMP, DCM, GIF, JNG, JPC, JP2, MIFF, MNG, PBM, PGM, PNM, PPM`.

# fichier RAW de l'appareil

darktable lit les fichiers RAW en utilisant la bibliothèque open source [RawSpeed](https://github.com/darktable-org/rawspeed), originellement développée par Klaus Post
et maintenue à présent dans le projet darktable lui-même. Le nombre d’appareils et de formats de fichier pris en charge est en constante augmentation.

La plupart des appareils modernes sont pris en charge et la tendance est d'ajouter les nouveaux très rapidement. En donner la liste exhaustive dépasse le cadre de ce manuel.

À l'exception des appareils Fujifilm X-Trans, darktable ne décode pas les images provenant d'appareils n'ayant pas un capteur Bayer (ex. les appareils Sigma avec le capteur Foveon X3).

# autres fichiers image

darktable lit de manière native les images « ordinaires » dans les formats JPEG, PNG 8-bit/16-bit et TIFF 8-bit/16-bit, aussi bien que dans les formats TIFF en nombres à virgule flottante 16-bit/23-bit. Le format JPEG2000 est aussi pris en charge si les bibliothèques nécessaires sont présentes lors de la compilation. De la même manière, si darktable a été compilé avec la prise en charge de GraphicsMagick, un certain nombre de formats d’importation supplémentaires sont disponibles, comme GIF, Dicom DCM , des formats TIFF exotiques et certains formats de la famille « portable xyz-map » de Sun.

darktable lit les images à grande plage dynamique dans les formats OpenEXR, RVBE et PFM.

