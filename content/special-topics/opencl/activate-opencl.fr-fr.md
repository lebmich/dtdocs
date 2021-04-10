---
author: people
draft: 'false'
id: activate-opencl
title: 'activer OpenCL dans darktable'
weight: 30
---

L’utilisation d’OpenCL dans darktable nécessite que votre PC soit équipé d’une carte graphique adaptée et que les bibliothèques requises soient installées. Les cartes graphiques modernes de NVIDIA et d'ATI prennent en charge complètement OpenCL. Le compilateur OpenCL fait normalement partie du pilote graphique propriétaire ; il est utilisé sous la forme d'une bibliothèque dynamique appelée `libOpenCL.so`. Cette bibliothèque doit se trouver dans un répertoire qui puisse être trouvé par l’éditeur dynamique de liens de votre système.

Quand darktable démarre, il va d’abord essayer de trouver et de charger libOpenCL.so et, en cas de succès, vérifier que la carte graphique disponible prend en charge OpenCL. Une quantité de mémoire graphique suffisante (1 Go+) doit être disponible afin de tirer parti du GPU. Si ce contrôle réussit, darktable va essayer de configurer son environnement OpenCL : un contexte de traitement doit être initialisé, un pipeline de calcul doit être démarré. Les fichiers du code source d’OpenCL (d’extension .cl) doivent être lus et compilés et les routines incluses (appelées noyaux d’OpenCL) doivent être préparées pour les modules de darktable. Une fois tout ceci effectué, la préparation est terminée.

By default OpenCL support is activated in darktable if all the above steps were successful. If you want to de-activate it you can do so in [preferences > cpu/gpu/memory](../../preferences-settings/cpu-gpu-memory.md). This configuration parameter is grayed out if the OpenCL initialization failed.

Vous pouvez à tout moment activer ou désactiver la prise en charge d’OpenCL, ce qui aura un effet immédiat. Selon le type des modules que vous utilisez, vous en remarquerez l’effet comme une accélération générale lors du travail interactif et lors de l’exportation. La plupart des modules de darktable peuvent profiter d’OpenCL mais tous ne sont pas suffisamment consommateurs de ressources pour que la différence puisse être remarquée. Afin de ressentir une vraie différence, prenez un module comme [_ombres et hautes lumières_](../../module-reference/processing-modules/shadows-and-highlights.md), [_renforcer la netteté_](../../module-reference/processing-modules/sharpen.md), [_filtre passe-bas_](../../module-reference/processing-modules/lowpass.md), [_filtre passe-haut_](../../module-reference/processing-modules/highpass.md) ou encore plus extrême [_contrast equalizer_](../../module-reference/processing-modules/contrast-equalizer.md) et [_réduction bruit (profil)_](../../module-reference/processing-modules/denoise-profiled.md).

Si vous êtes intéressé par les valeurs de profilage, vous pouvez lancer darktable avec les paramètres de la ligne de commande `-d opencl -d perf`. Après chaque exécution du pipeline graphique, vous allez obtenir l’allocation détaillée du temps d’exécution de chaque module avec un profil encore plus fin pour tous les noyaux OpenCL utilisés.

En dehors de l’accélération, vous ne devriez voir aucune différence de résultats entre le traitement CPU et le traitement GPU. À l’exception des erreurs d’arrondis, les résultats sont prévus pour être équivalents. Si, pour une raison quelconque, darktable échoue à terminer proprement un calcul GPU, il va normalement s’en apercevoir et automatiquement (et de manière transparente), se replier vers un traitement CPU. 
