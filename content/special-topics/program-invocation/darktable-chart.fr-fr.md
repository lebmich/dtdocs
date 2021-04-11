---
author: people
draft: 'false'
id: darktable-chart
title: darktable-chart
weight: 40
---

Cet exécutable est un utilitaire dédié à la création de styles à partir de paires d'images telles que raw+JPEG fournies par le boîtier. Des détails de son utilisation peuvent être trouvés dans la section [utiliser darktable-chart](../darktable-chart/_index.md)

`darktable-chart` soit démarre une interface graphique soit est utilisé comme programme en ligne de commande.

```
darktable-chart
              [--help]
              [<input Lab pfm file>]
              [<cht file>]
              [<reference cgats/it8 or Lab pfm file>]
```

Tous les paramètres sont optionnels, cependant, si vous voulez fournir le deuxième nom de fichier vous devez aussi fournir le premier, etc. Démarrer darktable-chart de cette manière ouvre une interface graphique spéciale (des détails peuvent être trouvés dans la section [utiliser darktable-chart](../darktable-chart/_index.md)).

`--help`
: Donne des informations d'utilisation et s'arrête.

`<input Lab pfm file>`
: Ouvre l'utilitaire avec le fichier donné comme image source. Le fichier en entrée doit être au format Lab Portable Float Map.

`<cht file>`
: Spécifie un fichier décrivant la disposition du diagramme de références couleur.

`<reference cgats/it8 or Lab pfm file>`
: Spécifie les valeurs de référence, soit comme valeurs mesurées en fonction du standard CGATS, soit comme image de référence dans le format Lab Portable Float Map.

Alternativement `darktable-chart` peut être utilisé comme un programme en ligne de commande pour générer des fichiers de style à partir de fichiers CVS précédemment sauvegardés.

```
darktable-chart
              --csv
              <csv file>
              <number patches>
              <output dtstyle file>
```

Tous les paramètres sont obligatoires.

`<csv file>`
: Un fichier CSV précédemment sauvegardé avec darktable-chart.

`<number patches>`
: Le nombre de pastilles de couleur à utiliser dans le paramétrage de la table correspondance couleurs du style créé.

`<output dtstyle file>`
: Nom du fichier de style qui doit être créé.

