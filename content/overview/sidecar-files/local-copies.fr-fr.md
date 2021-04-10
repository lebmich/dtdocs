---
author: people
draft: 'false'
id: local-copies
title: 'copies locales'
weight: 30
---

Assez souvent les utilisateurs ont d'énormes collections d’images qu'ils stockent sur des disques durs supplémentaires de leur ordinateur de bureau ou sur un support externe comme un NAS en RAID, etc.

It is a common requirement to be able to develop a number of images while travelling using a laptop and then later synchronize them back to the original storage medium. However, copying images manually from the main storage to the laptop and back is cumbersome and prone to errors. The “local copies” feature of darktable has been designed to directly support these use cases. 

Vous pouvez créer sur le disque local de votre ordinateur une copie locale des images sélectionnées dans la table lumineuse. Cette copie locale est toujours utilisée quand elle est présente, donnant accès aux images lorsque le stockage externe n'est plus connecté. Ultérieurement, lorsque votre support de stockage principal est de nouveau connecté, vous pouvez synchroniser les fichiers XMP liés et supprimer la copie locale de vos images d'entrée. Ces opérations se trouvent dans le panneau [images sélectionnées](../../module-reference/utility-modules/lighttable/selected-image.md) de la table lumineuse.

Pour des raisons de sécurité, s’il existe des copies locales et que le stockage externe est disponible, alors les fichiers liés XMP locaux seront automatiquement synchronisés au démarrage.

Les copies locales sont enregistrées dans le répertoire `HOME/.cache/darktable` et s’appellent `img-<SIGNATURE>.<EXT>` (où `SIGNATURE` est une signature de hachage (MD5) du chemin complet et `EXT` est l'extension du fichier d'origine.

Une copie locale est identifiée dans la vue table lumineuse par une marque blanche dans le coin supérieur droit de la miniature. De plus toutes les copies locales possèdent le mot-clé `darktable|local-copy` pour pouvoir être sélectionnées rapidement.
