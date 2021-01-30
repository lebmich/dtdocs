---
title: copies locales
id: local-copies
weight: 30
draft: false
author: "traducteur : Michel Leblond"
---

Assez souvent les utilisateurs ont d'énormes collections d’images qu'ils stockent sur des disques durs supplémentaires de leur ordinateur de bureau ou sur un support externe comme un NAS en RAID, etc.

Ils souhaitent fréquemment développer des images lors d’un voyage en utilisant un ordinateur portable et les synchroniser plus tard vers leur stockage externe. Mais copier les fichiers manuellement du stockage principal vers l’ordinateur portable et inversement est fastidieux et source d’erreurs.

La fonctionnalité de « copies locales » de darktable a été conçue pour prendre en charge ces cas d’utilisation.

Vous pouvez créer sur le disque local de votre ordinateur une copie locale des images sélectionnées dans la table lumineuse. Cette copie locale est toujours utilisée quand elle est présente, donnant accès aux images lorsque le stockage externe n'est plus connecté. Ultérieurement, lorsque votre support de stockage principal est de nouveau connecté, vous pouvez synchroniser les fichiers xmp liés et supprimer la copie locale de vos images d'entrée. Ces opérations se trouvent sur le panneau images sélectionnées (voir Section 2.3.8, « Images sélectionnées »).

Ces opérations se trouvent sur le panneau [images sélectionnées](../../module-reference/utility-modules/lighttable/selected-image.md) de la table lumi module in the lighttable.

Pour des raisons de sécurité, s’il existe des copies locales et que le stockage externe est disponible, alors les fichiers liés xmp locaux seront automatiquement synchronisés au démarrage.

Les copies locales sont enregistrées dans le répertoire `HOME/.cache/darktable` et s’appellent `img-<SIGNATURE>.<EXT>` (où `SIGNATURE` est une signature de hachage (MD5) du chemin complet et `EXT` est l'extension du fichier d'origine.

Une copie locale est identifiée dans la vue table lumineuse par une marque blanche dans le coin supérieur droit de la miniature. De plus toutes les copies locales possèdent le mot-clé `darktable|local-copy` pour pouvoir être sélectionnées rapidement.
