---
author: people
draft: 'false'
id: darktable
title: darktable
weight: 10
---

Le binaire `darktable` démarre darktable avec son interface graphique et ses fonctionnalités complètes. C'est la manière standard d'utiliser darktable.

`darktable` peut être appelé avec les paramètres de ligne de commande suivants :

```
darktable [-d {all,cache,camctl,camsupport,control,dev,
               fswatch,input,lighttable,lua,masks,memory,nan,
               opencl,perf,pwstorage,print,sql,ioporder,
               imageio,undo,signal}]
          [<input file>|<image folder>]
          [--version]
          [--disable-opencl]
          [--library <library file>]
          [--datadir <data directory>]
          [--moduledir <module directory>]
          [--tmpdir <tmp directory>]
          [--configdir <user config directory>]
          [--cachedir <user cache directory>]
          [--localedir <locale directory>]
          [--luacmd <lua command>]
          [--noiseprofiles <noiseprofiles json file>]
          [--d-signal <signal>]
          [--d-signal-act <all,raise,connect,disconnect,print-trace>]
          [--conf <key>=<value>]
          [-t <num openmp threads>]
```

Tous les paramètres sont optionnels. Dans la plupart des cas, les utilisateurs lanceront darktable sans paramètres supplémentaires. Dans ce cas, darktable utilise les valeurs par défaut adaptées.

`-d {all,cache,camctl,camsupport,control,dev,fswatch,input,lighttable,lua,masks,memory,nan,opencl,perf,pwstorage,print,sqlioporder,imageio,undo,signal}`
: Cette option active la sortie de débogage vers le terminal. Il y a plusieurs sous-systèmes dans darktable et le débogage de chacun d’eux peut être activé séparément. Vous pouvez utiliser cette option plusieurs fois si vous désirez déboguer la sortie de plus d’un sous-système.

`<input file>|<image folder>`
: Optionnellement vous pouvez indiquer le nom de fichier d’une image ou le nom d’un dossier contenant des fichiers d’images. Si un nom de fichier est donné darktable démarre en mode chambre noire avec ce fichier ouvert. Si un nom de dossier est donné darktable démarre en mode table lumineuse avec le contenu de ce dossier comme collection courante.

`--version`
: Avec cette option darktable affiche son numéro de version, un avis de droits d'auteur, quelques autres informations utiles et ensuite s'arrête.

`--disable-opencl`
: Cette option empêche darktable d'initialiser le sous-système OpenCL. Utilisez cette option dans le cas de plantage de darktable au démarrage en raison d’une implémentation défectueuse d’OpenCL.

`--library <library file>`
: darktable keeps image information in an sqlite database for fast access. The default location of that database file is `$HOME/.config/darktable/library.db`. Use this option to provide an alternative location, e.g. if you want to do some experiments without compromising your original `library.db`. If the database file does not exist, darktable creates it for you. You may also provide `:memory:` as the library file, in which case the database is kept in system memory – all changes are discarded when darktable terminates.
: Whenever darktable starts, it will lock the library to the current user. It does this by writing the current process identifier (PID) into a lock file `<library file>.lock` next to the library specified. If darktable finds an existing lock file for the library, it will terminate immediately.

`--datadir <data directory>`
: Cette option définit le répertoire où darktable recherche ses données d'exécution. L’emplacement par défaut dépend de votre installation. Des emplacements typiques sont`/opt/darktable/share/darktable/` et `/usr/share/darktable/`.

`--moduledir <module directory>`
: darktable a une structure modulaire et organise ses modules sous forme de bibliothèques partagées à charger lors de l'exécution. Avec cette option, vous indiquez à darktable où il doit les rechercher. L’emplacement par défaut dépend de votre installation. Des emplacements typiques sont `/opt/darktable/lib64/darktable/` et `/usr/lib64/darktable/`.

`--tmpdir <tmp directory>`
: Emplacement où darktable enregistre ses fichiers temporaires. Si cette option n’est pas fournie, darktable utilise la valeur par défaut du système.

`--configdir <config directory>`
: Cette option définit le répertoire où darktable enregistre la configuration propre à l’utilisateur. L’emplacement par défaut est `$HOME/.config/darktable/`.

`--cachedir <cache directory>`
: darktable keeps a cache of image thumbnails for fast image preview and of precompiled OpenCL binaries for fast startup. By default the cache is located in `$HOME/.cache/darktable/`. Multiple thumbnail caches may exist in parallel – one for each library file.

`--localedir <locale directory>`
: Emplacement où darktable recherche ses chaînes de texte propres aux différentes langues. L’emplacement par défaut dépend de votre installation. Des emplacements typiques sont `/opt/darktable/share/locale/` et `/usr/share/locale/`.

`--luacmd <lua command>`
: A string containing lua commands to execute after lua initialization. These commands will be run after your “luarc” file.
: If lua is not compiled in, this option will be accepted but won't do anything.

`--noiseprofiles <noiseprofiles json file>`
: Le fichier json qui contient les profils de bruit spécifiques aux boîtiers. L'emplacement par défaut dépend de votre installation. Les emplacements typiques sont `/opt/darktable/share/darktable/noiseprofile.json` et `/usr/share/darktable/noiseprofile.json`.

`--d-signal <signal>`
: Si `-d signal` ou`-d all` est spécifié, spécifiez le signal à déboguer en utilisant cette option. Spécifiez `ALL` pour déboguer tous les signaux ou spécifiez le signal en utilisant son nom complet. Peut être utilisé plusieurs fois.

`--d-signal-act <all,raise,connect,disconnect,print-trace>`
: Si `-d signal` ou`-d all` est spécifié, spécifiez le signal à déboguer en utilisant cette option.

`--conf <key>=<value>`
: darktable supports a rich set of configuration parameters which the user defines in `$HOME/.config/darktable/darktablerc`. You may temporarily overwrite individual settings on the command line with this option – however, these settings will not be stored in “darktablerc” on exit.

`-t <num openmp threads>`
: nombre maximum de fils openmp à utiliser dans les sections parallèles openmp.
