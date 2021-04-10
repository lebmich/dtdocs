---
author: people
draft: 'false'
id: translating
title: 'traduire dtdocs'
weight: 100
---

Traduire la documentation de darktable se fait via notre [instance de Weblate](https://weblate.pixls.us/projects/darktable/).

Vous pouvez soit utiliser l'interface utilisateur Web de Weblate pour traduire la documentation, soit télécharger la traduction de Weblate sur votre ordinateur, la modifier, puis téléverser les modifications.

Veuillez effectuer tous les travaux de traduction via Weblate. Nous n'accepterons pas les pull resquests directement sur github pour mettre à jour les fichiers PO.


# Créer une nouvelle branche dans git
1. Créez une nouvelle branche avec git pour y travailler.
   Par exemple :
   `git checkout -b fr-translation-init`


# Ajouter une nouvelle langue à Hugo

1. Dans les fichiers `config.yaml` et `config-pdf.yaml`, localisez la ligne `languages:`.

2. Ajoutez la langue que vous souhaitez traduire. Par exemple, l'anglais ressemble à ceci :

   ```
     en-us:
       title: darktable 3.4 user manual
       weight: 1
   ```

3. Enregistrez les fichiers.


# Générer un fichier PO

Effectuez les étapes suivantes si vous souhaitez mettre à jour les fichiers POT et PO à partir de la source markdown.

1. Créez un fichier PO vide pour votre langue dans le répertoire `po` avec le nom de fichier `content.<langue>.po`.
   Par exemple :
   `touch po/content.fr-fr.po`

2. Exécutez le script pour remplir le fichier PO :
   `cd tools/ && ./generate-translations.sh --no-translations`


# Générer des fichiers traduits

Suivez les étapes suivantes pour générer les fichiers du site Web à partir d'une traduction.

1. Générer les fichiers traduits :
   `cd tools/ && ./generate-translations.sh --no-update`.

2. Vérifiez la traduction en démarrant le serveur interne de Hugo :
   `hugo server`

3. Ouvrez un navigateur Web et vérifiez les modifications. L'URL est dans la sortie de la commande `hugo server`.

4. Supprimez les fichiers traduits, car nous ne les archivons jamais dans git :
   `cd tools/ && ./generate-translations.sh --rm-translations`.


# Traduction du site Web et des chaînes en PDF

Il existe deux thèmes pour la documentation de darktable : un pour le site Web HTML et un pour le PDF. Vous devrez traduire les chaînes pour les deux.

1. Allez dans `themes/hugo-darktable-docs-themes/i18n`.

2. Copiez le contenu du fichier `en.yaml` et nommez le nouveau fichier `<votre langue>.yaml`.

3. Traduisez le contenu du nouveau fichier yaml.

4. Vérifiez le fichier PO traduit dans git, poussez-le vers github et ouvrez une pull request pour que vos modifications soient acceptées.

5. Répétez les quatre dernières étapes pour l'autre thème, `themes/hugo-darktable-docs-pdf-theme`.

