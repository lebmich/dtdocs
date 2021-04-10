---
author: people
draft: 'false'
id: problems-solutions
title: 'problèmes possibles et solutions'
weight: 50
---

darktable détecte automatiquement les problèmes d’OpenCL en cours de fonctionnement. Il effectuera alors le traitement sur le CPU ; seule la vitesse est affectée et le résutat final ne sera pas impacté.

Il y a de nombreuses raison qui font qu’OpenCL peut échouer lors de sa phase d’initialisation. OpenCL dépend des exigences matérielles et de la présence de certains pilotes et bibliothèques. De plus tout ceci doit correspondre en termes de modèle et de numéro de version. Si quelque chose ne correspond pas (par exemple si votre pilote graphique -- chargé en tant que module du noyau -- ne correspond pas à la version de votre `libOpenCL.so`) le support d’OpenCL ne sera probablement pas disponible.

Dans ce cas, la meilleure chose à faire est de démarrer darktable depuis une console par `darktable -d opencl`.

Ceci va donner des informations de débogage supplémentaires concernant l’initialisation et l’utilisation d’OpenCL. Regardez d’abord si vous voyez une ligne qui commence par `[opencl_init] FINALLY ...`. Ceci doit vous indiquer si la prise en charge d’OpenCL est disponible pour vous ou pas. S’il y a un échec de l’initialisation, regardez dans les messages au-dessus s’il y a quelque chose qui ressemble à `could not be detected` ou `could not be created`. Regardez s’il y a une indication de l’endroit où l’échec a eu lieu.

Voici un certain nombre de cas observés dans le passé :

- darktable peut vous indiquer qu’aucune carte graphique prenant en charge OpenCL n'a été détectée ou que la mémoire disponible sur votre GPU est trop faible et que la carte ne sera pas utilisée. Dans ce cas, il vous faudra acheter une nouvelle carte si vous désirez la prise en charge d’OpenCL.


- darktable pourrait trouver votre `libOpenCL.so` mais vous dire ensuite qu'il ne peut obtenir de plate-forme. Les pilotes NVIDIA donnent souvent un code d’erreur -1001 dans ce cas. Ceci arrive parce que `libOpenCL.so` n'est qu'un encapsuleur de bibliothèque. Pour le travail réel, d'autres bibliothèques spécifiques au fournisseur doivent être chargées. Ceci a échoué pour une raison quelconque. Il y a une structure de fichiers dans`/etc/OpenCL` sur votre système que `libOpenCL.so` consulte pour rechercher ces bibliothèques. Vérifiez que vous n'avez pas quelque chose de louche par là et essayez de le corriger. Souvent, les bibliothèques ne peuvent pas être trouvées par le chargeur dynamique de votre système. Donner les noms de chemin complet peut aider.


- darktable peut aussi vous indiquer qu'un contexte ne peut être créé. Ceci indique souvent qu'il y a une incompatibilité de version entre le pilote graphique chargé et libOpenCL. Vérifiez que vous n'avez pas laissé de modules du noyau ou de bibliothèques graphiques provenant d’une installation plus ancienne et prenez les mesures appropriées. En cas de doute, faites une réinstallation propre de votre pilote graphique. Quelquefois, immédiatement après une mise à jour de pilote, le module du noyau ne correspond pas aux bibliothèques nouvellement installées. Dans ce cas, redémarrez votre système.


- Il arrive, dans quelques rares cas, que darktable se plante durant le démarrage. Ceci peut se produire si votre configuration OpenCL est complètement cassée ou si un pilote ou une bibliothèque comporte un bogue sévère. Si vous n'arrivez pas à le corriger, vous pouvez toujours utiliser l’option de lancement de darktable `--disable-opencl`, qui sautera alors l’ensemble de la phase d’initialisation d’OpenCL.


- darktable peut échouer à compiler ses fichiers source OpenCL lors de l’exécution. Dans ce cas, vous obtiendrez de nombreux messages d’erreur semblables à des erreurs typiques de compilateur. Ceci peut indiquer une incompatibilité entre votre implémentation d’OpenCL et l'interprétation des normes par darktable. Dans ce cas, prenez contact avec les développeurs sur IRC dans `#darktable`sur FreeNode ou sur la liste darktable-dev@lists.darktable.org et signalez le problème. Il y a de bonnes chances que nous puissions vous aider. Veuillez aussi signaler si vous constatez des différences significatives entre le traitement CPU et le traitement GPU d’une image.


Il existe aussi quelques implémentation d’OpenCL sur le CPU, disponibles sous la forme de pilotes fournis par INTEL ou AMD. Nous avons remarqué qu'ils n’apportaient aucun gain en vitesse comparé à notre code CPU optimisé à la main. Par conséquent, darktable, par défaut, rejette tout simplement ces périphériques. Ce comportement peut être modifié en définissant à VRAI la variable de configuration `opencl_use_cpu_devices` (dans`$HOME/.config/darktablerc`).
