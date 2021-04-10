---
author: people
draft: 'false'
id: screen-layout
title: "disposition de l'affichage"
weight: 20
---

La disposition de l'affichage est la même pour toutes les vues. Elle consiste en une zone centrale bordée par des panneaux : 

![disposition de l' affichage](./screen-layout/screen-layout.png#w100)

1. zone centrale
: Contient des informations et la fonctionnalité spécifique de la vue actuelle.

2. panneau gauche
: Contient des modules principalement utilisés pour fournir des informations.

3. panneau droit
 : Contient des modules principalement utilisés pour le traitement d'image.

4. bannière supérieure
: Contient des informations sur la version actuelle de darktable et vous permet de basculer entre les vues. Également utilisé par certains modules pour afficher des conseils et des messages.

5. [panneau supérieur](./top-panel.md)
: Fournit l'accès aux paramètres globaux et aux raccourcis.

6. panneau inférieur
 : Permet d'accéder aux paramètres et raccourcis spécifiques à la vue.

7. panneau [pellicule](../../module-reference/utility-modules/shared/filmstrip.md)/[chronologie](../../module-reference/utility-modules/lighttable/timeline.md)
: Un panneau facultatif qui peut être activé en bas de l'écran pour afficher une chronologie (dans la vue table lumineuse) ou une pellicule (dans d'autres vues) des images de la collection actuelle.

# taille d'un panneau et sa visibilité

Les panneaux gauche, droit et pellicule/chronologie peuvent être redimensionnés en faisant glisser leurs bordures intérieures. 

Chacun de ces panneaux peut être affiché ou masqué en appuyant sur un triangle situé sur le bord extérieur du panneau. La visibilité du panneau peut également être ajustée à l'aide de raccourcis clavier, comme suit :

```
TAB             Étendre temporairement la vue centrale pour remplir toute la fenêtre.
                Appuyez à nouveau pour revenir à la vue précédente
F11             Basculer en mode plein écran
Shift+Ctrl+t    Afficher/masquer le panneau supérieur (entre l'image et la bannière du haut)
Shift+Ctrl+b    Afficher/masquer le panneau inférieur (entre l'image et le panneau pellicule / chronologie s'il est affiché)
Shift+Ctrl+l    Afficher/masquer le panneau gauche
Shift+Ctrl+r    Afficher/masquer le panneau droit
Ctrl+f          Afficher/masquer le panneau pellicule / chronologie
Ctrl+h          Afficher/masquer la bannière supérieure
b               Afficher/masquer tous les bords et les contrôles de réduction des panneaux
```
---

**Remarque :** La taille et la visibilité des panneaux sont stockées indépendamment pour chaque vue.

---
