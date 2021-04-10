---
author: people
draft: 'false'
id: darktable-cli
title: darktable-cli
weight: 20
---

L'exécutable `darktable-cli` lance la variante en ligne de commande de l’interface de darktable qui permet l’exportation d’images.

This variant does not open any display -- it works in pure console mode without launching a GUI. This mode is particularly useful for servers running background jobs.

`darktable-cli` peut être appelé avec les paramètres suivants de la ligne de commande :

```
darktable-cli [<input file or folder>]
              [<xmp file>]
              <output file or folder>
              [--width <max width>]
              [--height <max height>]
              [--bpp <bpp>]
              [--hq <0|1|true|false>]
              [--upscale <0|1|true|false>]
              [--style <style name>]
              [--style-overwrite]
              [--apply-custom-presets <0|1|false|true>]
              [--out-ext <extension>]
              [--import <file or dir>]
              [--icc-type <type>]
              [--icc-file <file>]
              [--icc-intent <intent>]
              [--verbose]
              [--help [option]]
              [--core <darktable options>]
```

L’utilisateur doit fournir un nom de fichier d’entrée et un nom de fichier de sortie. Tous les autres paramètres sont optionnels.

`<input file or folder>`
: le nom du fichier en entrée ou du répertoire (contenant des images) à exporter. Si vous souhaitez développer plusieurs images ou plusieurs répertoires utilisez plutôt l'option `--import`.

`<xmp file>`
: Nom optionnel d’un fichier lié XMP qui contient les données de l’historique de développement qui sera appliqué lors de l’exportation. Si cette option n’est pas donnée, darktable recherchera un fichier XMP appartenant au(x) fichier(s) d’entrée indiqué(s).

`<output file or folder>`
: Le nom du fichier de sortie ou le répertoire de destination. Le format du fichier de sortie est dérivé de son extension ou de l'option `--out-ext` . Vous pouvez aussi utiliser des [variables de substitution](../variables.md) dans le nom du fichier de sortie. Pour des raisons évidentes ceci est obligatoire si vous utilisez le programme pour un répertoire contenant de nombreuses images. Si vous spécifiez le répertoire de sortie, il est recommandé de spécifier également le format de fichier avec `--out-ext`.

`--width <max width>`
: Ce paramètre permet de limiter la largeur de l’image exportée au nombre de pixels indiqué.

`--height <max height>`
: Ce paramètre permet de limiter la hauteur de l’image exportée au nombre de pixels indiqué.

`--bpp <bpp>`
: Ce paramètre définit la profondeur de bits de l’image exportée. Les valeurs autorisées dépendent du format de fichier. 

---

**Remarque ** Actuellement, cette option n’est pas encore fonctionnelle. Si vous devez définir la profondeur de bits, vous devez utiliser la solution suivante :

```
    --core
    --conf plugins/imageio/format/<FORMAT>/bpp=<VALUE>
```
où`<FORMAT>` est le nom du format de sortie sélectionné.

---

`--hq <0|1|true|false>`
: Indicateur définissant s’il faut utiliser un ré-échantillonnage de haute qualité lors de l’exportation (voir le module [exporter sélection](../../module-reference/utility-modules/shared/export.md) pour plus de détails). Vrai par défaut.

`--upscale <0|1|true|false>`
: Indicateur définissant s’il faut utiliser un ré-échantillonnage de haute qualité lors de l’exportation Faux par défaut.

`--style <style name>`
: Spécifiez le nom d'un style à appliquer lors de l'exportation. Si un style est spécifié, le chemin d'accès au répertoire de configuration darktable doit également être spécifié (c'est-à-dire `--core --configdir ~/.config/darktable`). Par défaut, aucun style n'est spécifié.

`--style-overwrite`
: Le style spécifié remplace l'historique au lieu d'y être ajouté.

`--apply-custom-presets <0|1|false|true>`
: S'il faut charger `data.db` qui contient des préréglages et des styles. Désactiver cette option vous permet de lancer plusieurs instances de `darktable-cli` au prix de ne pas pouvoir utiliser l'option `--style`. La valeur par défaut est vrai.

`--out-ext <extension>`
: Définissez l'extension de sortie à utiliser. Si elle est spécifiée, elle est prioritaire sur celle du `<fichier de sortie>`. Par défaut, elle est extraite du nom du `<fichier de sortie>`. La valeur par défaut est `jpg` si un ` <répertoire de sortie> `est spécifié.

`--import <file or dir>`
: Spécifiez le fichier ou le répertoire d'entrée, peut être utilisé plusieurs fois. Cette option ne peut pas être combinée avec `<input file or folder>`.

`--icc-type <type>`
: Spécifiez le type de profil ICC, ce qui revient à spécifier le `profil de sortie` dans le module `profil de couleur de sortie`. La valeur par défaut est "image spécifiée". Utilisez`--help icc-type` pour obtenir une liste des types pris en charge. Voir [profil couleur de sortie](../../module-reference/processing-modules/output-color-profile) pour une description plus détaillée des options disponibles.

`--icc-file <file>` 
: Spécifiez le nom de fichier du profil ICC. Par défaut, un nom de fichier vide.

`--icc-intent <intent>` 
: Spécifiez l'intention de rendu. Utilisez `--help icc-intent` pour obtenir une liste des modes de rendu pris en charge. Voir [intention de rendu](../../special-topics/color-management/rendering-intent) pour une description plus détaillée des options disponibles.

`--verbose`
: Activer la sortie verbeuse.

`--help [option]`
: Donne les paramètres d'usage et quitte. Si `option` est spécifié, donne en plus les paramètres de l'option donnée.

`--core <darktable options>`
: Tous les paramètres de la ligne de commande suivant `--core` sont passés au noyau de darktable et manipulés comme des paramètres standards. Voir la section [Exécutable darktable](./darktable.md) pour une description détaillée.



