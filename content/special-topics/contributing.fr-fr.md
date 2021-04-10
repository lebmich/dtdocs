---
author: people
draft: 'false'
id: contributing
title: 'contribuer à dtdocs'
weight: 90
---

Cette page définit le guide de style pour dtdocs et donne des informations sur la manière de contribuer au projet.

La page est incluse dans le manuel de l'utilisateur afin que vous puissiez voir comment elle est écrite et rendue. Veuillez aller sur [GitHub](https://raw.githubusercontent.com/darktable-org/dtdocs/master/content/special-topics/contributing.md) pour voir la source de cette page.

La structure et le contenu du manuel ont été soigneusement étudiés en fonction des critères suivants :
1. Le manuel doit être complet -- il doit décrire toutes les fonctionnalités disponibles dans darktable
2. Il doit avoir une structure cohérente et logique et chaque élément de fonctionnalité doit avoir sa propre place logique dans cette structure
3. Il devrait être aussi long que nécessaire mais aussi court que possible - la brièveté est un must
4. Il doit être objectif
5. La fonctionnalité doit être expliquée une et une seule fois (à l'exception des directives de base des flux de travail dans la section présentation)
6. Les images ne devraient être incluses que lorsque cela est nécessaire pour améliorer la compréhension des principes clés et ne devraient pas contenir de texte à moins que cela ne soit inévitable

Nous ne sommes généralement **pas** intéressés par :
1. Une restructurer du manuel
2. Un changement du langage de balisage
3. Des didacticiels détaillés sur le flux de travail (bien que nous souhaitons les publier sur les blogs de darktable.org ou de pixls.us)

Nous **sommes** intéressés par :
1. Les corrections orthographiques et grammaticales
2. La clarification du texte
3. La documentation des nouvelles fonctionnalités

Nous sommes toujours extrêmement intéressés de savoir quelles sections du manuel n'ont pas de sens pour vous et *pourquoi*, afin que nous puissions améliorer la documentation.

En général, si vous souhaitez apporter un changement majeur, veuillez ouvrir une "issue" et discutez-en d'abord avec les responsables. Cela pour éviter de faire un travail qui ne serait pas accepté.

# format

Ce site Web est créé en pur markdown, en utilisant certaines extensions. Il est initialement conçu pour fonctionner avec Hugo SSG, mais conçu pour être suffisamment portable pour pouvoir être facilement rendu avec une autre application si nécessaire.

Le fichier doit être rendu en UTF-8 et ne doit pas inclure de retour à la ligne automatique.

# structure

Ce qui suit montre la structure d'un exemple de chapitre principal avec des sous-sections sur le site Web dtdocs.

```
example-chapter/
   _index.md
   section1-with-subsections/
      subsection1/
         image.png
      _index.md
      subsection1.md
      subsection2.md
   section2.md
   section3.md
```

Quelques notes sur la structure ci-dessus :

- Les fichiers `_index.md` ne contiennent aucun contenu (ils contiennent uniquement des métadonnées) et sont utilisés pour rendre les en-têtes de section et les entrées de la table des matières. Dans l'exemple ci-dessus, `example-chapter/_index.md` définit le titre de l'exemple de chapitre et l'ordre dans lequel il apparaît dans la table des matières principale. De même, `example-chapter/section1-with-subsections/_index.md` définit les métadonnées pour la première section du chapitre.

- Les fichiers multimédias doivent être contenus dans un répertoire portant le même nom que la page à laquelle ils se rapportent. Dans cet exemple, `example-chapter/section1-with-subsections/subsection1` contient un média lié à la page `subsection1.md`.


# métadonnées

Les métadonnées des fichiers markdown sont présentées en tête de page à l'aide de yaml. Toutes les métadonnées peuvent être définies - les sections de référence du module contiennent beaucoup de métadonnées spécifiques - cependant ce qui suit définit quelques métadonnées minimales pour la page d'exemple `example-chapter/section1-with-subsections/subsection1.md`.

```
---
title: Sub Section 1 Title
id: subsection1
weight: 10
---
```

title
: Cela doit contenir le titre rendu de votre page. Pour inclure un deux-points dans un titre, placez le titre entre guillemets.

id
: C'est l'identifiant utilisé pour identifier la page par Hugo. Il doit généralement avoir le même nom que le fichier (pour les fichiers de contenu) ou le répertoire parent (pour les fichiers `_index.md`).

weight
: Il s'agit d'un champ de métadonnées facultatif utilisé pour définir l'ordre dans lequel les sections sont présentées dans la table des matières. Si le champ _weight_ n'est pas inclus, les pages seront rendues dans l'ordre alphabétique par défaut. Par exemple, pour définir les sections et sous-sections de l'exemple ci-dessus dans l'ordre inverse, les métadonnées suivantes doivent être définies :

```
   example-chapter/
      section1-with-subsections/
         _index.md               # weight : 30 (place la page section1 à la fin de example-chapter)
         subsection1.md             # weight : 20 (place la  page subsection1 à la fin de la section1)
         subsection2.md             # weight : 10 (place la page subsection2 à la fin de la section1)
      section2.md                # weight : 20 (place la section2 au milieu de example-chapter)
      section3.md                # weight : 10 (place la section3 au début de example-chapter)
```

# contenu

## conseils généraux de style

- Tout le contenu doit être rédigé en clair sans code abrégé et le HTML doit être réduit au minimum absolu, s'il est utilisé.

- Le minimalisme est un must absolu. Le moins de mots possible est préféré

- Les fichiers Markdown doivent être aussi courts que possible

- Suivez les normes de dénomination et de capitalisation présentes dans l'interface graphique de l'application - à savoir que tous les en-têtes et titres sont en minuscules, à l'exception des noms de chapitre de très haut niveau

- Les en-têtes dans un fichier ne doivent pas dépasser le niveau trois (###)

- La langue de création principale est l'anglais

- Supposez que le lecteur a ouvert l'application lors de la lecture du manuel d'utilisation et n'incluez que des images où elles contribuent à l'explication de fonctionnalités complexes

- Utilisez des références si vous avez besoin d'annoter une image (c.-à-d. Marquez des parties de l'image avec une lettre ou un chiffre, puis expliquez la signification dans un texte suivant l'image). Ne placez pas de mots directement dans l'image pour les annotations, car cela rend la localisation difficile. Voir [cette page](../darkroom/pixelpipe/the-anatomy-of-a-module.md) pour un exemple.

- Les modifications du contenu doivent être proposées via une pull request ou un mécanisme similaire

- Vos soumissions seront modifiées, ne le prenez pas mal


## listes de définitions

La méthode standard de présentation des informations concernant les contrôles des modules de darktable consiste à utiliser des listes de définitions.

nom d'un contrôle de l'interface graphique
: Une déclaration de ce que fait le contrôle. Par exemple "Réglez l'exposition en unités EV"

: Vous pouvez inclure autant de paragraphes que vous le souhaitez, mais essayez de limiter leur nombre à 2 ou 3 si possible.

![active-icon](./contributing/active-icon.png#icon) un contrôle accessible via un bouton avec une icône
: Lorsqu'un contrôle est activé à l'aide d'une icône, prenez une capture d'écran de l'icône en utilisant le thème standard de darktable et ajoutez-le avant le nom du contrôle

nom de la zone de liste déroulante de l'interface
: Les les zones de liste déroulante ont souvent plusieurs options qui doivent toutes être affichées avec des définitions séparées. Utilisez des listes à puces avec _italiques_ pour les valeurs de la zone de liste déroulante.
: - _la première valeur_ : ce que signifie la première valeur
: - _la seconde valeur_ : ce que signifie la seconde valeur

Les listes de définitions sont également utilisées dans tout le document, partout où une fonctionnalité nommée doit être définie. Voir, par exemple, [darktable-cli](./program-invocation/darktable-cli.md).

## Remarques

Si vous souhaitez présenter une remarque importante à l'utilisateur, utilisez le format suivant :

---

**Remarque** : Ceci est une remarque importante.

---

## polices à largeur fixe et blocs de code

Les polices à largeur fixe (utilisant le caractère \`) ne doivent normalement être utilisées que pour les blocs de code et lors du référencement des noms de fichiers et des paramètres de la ligne de commande.

## liens

Les liens internes doivent être relatifs au fichier actuel et doivent pointer vers un fichier markdown (.md) valide. Commencez les liens avec soit `./` Pour représenter le répertoire courant ou `../` pour représenter le répertoire parent.

- Les liens vers un module de traitement doivent être en italique, par ex. [_exposition_](../module-reference/processing-modules/exposure.md)

- Les liens vers un module utilitaire doivent être en texte brut, par exemple [historique](../module-reference/utility-modules/darkroom/history-stack.md)

- Lien vers une section de niveau supérieur en référençant le fichier `_index.md`, par ex. [référence des modules](../module-reference/_index.md)

- Lien vers un onglet dans la boîte de dialogue des préférences : [préférences > général](../preferences-settings/general.md)

- Lien vers un paramètre spécifique des préférences : [préférences > général > langue pour l'interface](../preferences-settings/general.md)

- Chaque en-tête d'une page peut être lié directement avec un lien d'ancrage : [contribution/remarques](./contributing.md#notes)


## images

Lorsque vous prenez des captures d'écran de l'application darktable elle-même, utilisez le thème darktable par défaut.

Plusieurs suffixes de nom de fichier peuvent être utilisés pour contrôler la façon dont une imagList are not e est rendue.

icône
: Pour insérer une image sous forme d'icône, incluez `#icon` après le nom de l'image dans le lien. Le markdown `![squirrel icon](./contributing/contributing.png#icon)` affiche ce qui suit : ![squirrel icon](./contributing/squirrel.png#icon)

largeur de l'image
: Vous pouvez définir la largeur de l'image à 25, 33, 50, 66, 75 ou 100% de la largeur de la page rendue en incluant `#wxx` après le nom de l'image dans le lien, où `xx` est la largeur souhaitée. Par exemple :
: `![squirrel](./contributing/squirrel.png#w25)` affiche
: ![squirrel](./contributing/squirrel.png#w25)
: `![squirrel](./contributing/squirrel.png#w75)` affiche
: ![squirrel](./contributing/squirrel.png#w75)

en ligne
: À l'exception des icônes, les images sont incluses en tant qu'éléments de bloc par défaut. Vous pouvez remplacer cela en incluant `#inline` après le nom de l'image. Cela peut être combiné avec le paramètre de largeur comme suit.
: `![squirrel](./contributing/squirrel.png#w25#inline)` affiche ![squirrel](./contributing/squirrel.png#w25#inline)

défaut
: Par défaut, les images sont présentées sous forme d'éléments de bloc avec une largeur de 100%. Donc `![squirrel](./contribution/squirrel.png#w100)` et `![squirrel](./contribution/squirrel.png)` sont équivalents et les deux produisent ce qui suit :
: ![squirrel](./contributing/squirrel.png)
