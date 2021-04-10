---
author: people
draft: 'false'
id: memory
title: memory
weight: 20
---

darktable's memory requirements are high. A simple calculation makes this clear. If you have a 20MPx image then, for precision reasons, darktable will store this internally as a 4 x 32-bit floating point cell for each pixel. Each full image of this size will therefore need about 300MB of memory. As we want to process the image, we will at least need two buffers for each module  – one for input and one for output. If we have a more complex module, its algorithm might additionally require several intermediate buffers of the same size. Without further optimization, anything between 600MB and 3GB would be needed merely to store and process image data. On top of that we have darktable's code segment, the code and data of all dynamically linked system libraries, and not to forget, further buffers where darktable stores intermediate images for quick access during interactive work (mip map cache). 

Dans l'ensemble, darktable a besoin d'un minimum d'environ 4 Go de mémoire pour fonctionner correctement.

# mémoire total du système

D'après l'analyse ci-dessus, il est évident que votre ordinateur a besoin d'une configuration de mémoire raisonnable pour exécuter correctement darktable. Nous vous suggérons de disposer d'au moins 4 Go de RAM physique et de 4 à 8 Go d'espace d'échange supplémentaire. 

Theoretically, you could run darktable with lower amounts of physical RAM and balance this with enough swap space. However, you this could cause your system to “thrash”, as it reads or writes data pages to and from the hard disk. We have positive reports that this functions well for several users, but it still might get extremely slow for others. A solid-state drive can ease the pain slightly.

# espace d'adressage disponible

Outre la quantité totale de mémoire système, il existe un autre facteur limitant : l'espace d'adressage disponible de votre architecture matérielle. La quantité de mémoire pouvant être adressée par un processus dépend du nombre de bits d'adresse offerts par votre CPU. Pour une CPU avec des registres d'adresses 32 bits, c'est 2^32 octets, ce qui fait un total de 4 Go. C'est la limite supérieure absolue de mémoire qui peut être utilisée par un processus et cela met darktable dans une situation difficile comme nous l'avons vu ci-dessus.

La porte de sortie de darktable s'appelle le tuilage. Pour chaque module de traitement, au lieu de traiter une image en un seul gros morceau, darktable la divise en parties plus petites (des tuiles). Cela nécessite encore un tampon d'entrée et de sortie, mais ces tampons intermédiaires peuvent être suffisamment petits pour tout faire rentrer dans les limites du matériel.

# fragmentation de la mémoire

Malheureusement, ce n’est pas encore la fin de l’histoire. Un effet appelé fragmentation de la mémoire peut toucher et touchera les logiciels qui doivent réaliser une gestion étendue de la mémoire. Si un tel programme alloue 5 fois 300 Mo à la fois et ensuite les libère, cette mémoire devrait normalement être disponible pour une grande allocation ultérieure de 1,5 Go. Cependant ce n'est pas souvent le cas. L'allocateur de mémoire du système peut ne plus voir cette zone comme un bloc contigu de 1,5 Go mais comme une rangée de blocs séparés de 300 Mo. S'il n'y a pas d'autre zone libre de 1,5 Go disponible, une allocation ultérieure échouera. Pendant l'exécution d'un programme, ce mécanisme enlèvera de plus en plus de blocs de mémoire plus gros au profit de blocs plus petits. Le cache mip map de darktable alloue plusieurs petits blocs de mémoire par miniature, ce problème est donc encore plus important. Pour cette raison, à partir de darktable 2.0, la prise en charge des systèmes 32 bits est obsolète.

# autres limitations

As if this were not challenging enough, there are further things that might limit darktable's access to memory. On some older boards you need to activate the "memory mapping" BIOS option in order to have all physically installed memory enabled. In addition if you are on a 32-bit OS you will probably need a kernel version that has “Physical Address Extension” (PAE) enabled. This is often but not always the case for Linux. Many distributions deliver different kernels, some with and some without PAE activated; you need to choose the right one. To check if the system is setup correctly, use the command “free” in a terminal and examine the output. If the output reports less RAM than you have installed, you have an issue needing correction; for example you have 4GB on your board, but your kernel is only seeing 3GB or less. You should consult your BIOS manual and the information about your Linux variant for further help.

# Configurer darktable sur un système 32 bits

Comme nous l'avons vu, les systèmes 32 bits sont des environnements difficiles pour darktable. Certains les utilisent encore pour exécuter darktable, quand les exigences de base en termes de mémoire système totale et les sujets mentionnés dans les paragraphes ci-dessus sont traités correctement.

There are several parameters that require adjustment in order to get it running. If you install fresh, darktable will detect your system and set conservative values by default. However, if you upgrade darktable from an older version, chances are you have unfavorable settings in your preferences. The consequences might be darktable aborting due to allocation failures or – very typically – darktable not being able to properly import a new film roll. As a frequent symptom you get skulls displayed instead of thumbnails for many of your pictures.

Si tel est le cas, prenez une minute pour optimiser vos paramètres de préférence. Vous les trouverez dans [préférences > cpu / gpu / mémoire](../preferences-settings/cpu-gpu-memory.md). 

Voici une brève explication des paramètres pertinents et de leurs réglages proposés :

nombre de fils d'exécution
: Ce paramètre définit le nombre maximum de fils d'exécution autorisés à s'exécuter en parallèle pour l'importation de pellicules ou pour d'autres tâches d'arrière-plan. Pour des raisons évidentes sur les systèmes 32 bits, vous ne pouvez avoir qu'un seul fil d'exécution consommant des ressources à la fois. Vous devez donc définir ce paramètre sur 1 ; toute valeur supérieure provoquera un plantage.

mémoire limite (en Mo) pour le tuilage
: Ce paramètre indique à darktable la quantité de mémoire (en Mo) qu'il doit supposer disponible pour stocker les tampons d'image pendant les opérations du module. Si une image ne peut pas être traitée dans ces limites en un seul bloc, le tuilage prendra le relais et traitera l'image en plusieurs parties, l'une après l'autre. Fixez ce paramètre à la valeur la plus faible possible, avec 500 comme point de départ. Vous pourrez par la suite tester si vous pouvez l’augmenter un peu de manière à réduire la surcharge due au tuilage.

quantité minimale de mémoire (en Mo) pour la mémoire-tampon d'une tuile
: c'est le second paramètre qui contrôle le tuilage. Il définit une limite basse pour la taille, en mégaoctets, des tampons intermédiaires. Le paramètre est nécessaire pour éviter un tuilage excessif dans certains cas (pour certains modules). Fixez ce paramètre à la faible valeur de 8. Vous pourrez tenter de l’augmenter à 16 par la suite.

mémoire en mégaoctets à utiliser pour le cache des miniatures
: Ceci contrôle combien de miniatures (ou mip maps) peuvent être stockées à la fois en mémoire. Comme point de départ fixez ce nombre à quelque chose comme 256 MB. Depuis darktable 2.0, le cache doit allouer de petits buffers pour chaque miniature, causant ainsi une significative fragmentation de la mémoire. Comme expliqué auparavant, ceci pose problème aux systèmes 32-bits. Pour cette raison, à partir de darktable 2.0, le support du 32-bits est déconseillé.

# darktable sur les systèmes 64-bits

Il n'y a plus grand chose à dire ici. Bien sûr, les systèmes 64 bits ont besoin d’une certaine quantité de mémoire principale, donc la recommandation de 4 Go plus le swap reste vraie. D’un autre côté, l’architecture 64 bits ne souffre pas des limitations spécifiques au 32 bits comme l’espace adressable réduit et le problème de la fragmentation.

Most modern Intel or AMD 64-bit CPUs will have available address space in the range of several Terabytes. The word “modern” is relative in this context: all AMD and Intel CPUs introduced since 2003 and 2004, respectively, offer a 64-bit mode. Linux 64-bit has been available for many years.

Toutes les distributions de Linux concernées vous donnent le choix d’installer une version 32 bits ou une version 64 bits. Vous pouvez même faire tourner des binaires 32 bits sous une version 64 bits de Linux. La seule chose pour laquelle vous devrez passer un peu de temps sera la migration. Nous recommandons finalement de passer à une version 64 bits de Linux. Il n'y a vraiment aucune raison de ne pas le faire.

On a 64-bit system you can safely leave the tiling related configuration parameters at their defaults: “host memory limit (in MB) for tiling” should have a value of 1500 and “minimum amount of memory (in MB) for a single buffer in tiling” should be set to 16. If you are migrating from a 32-bit to a 64-bit system you will need to check these settings and manually change them if needed in darktable's preference dialog.

Typically there is no need to restrict oneself in the number of background threads on a 64-bit system. On a multi-processor system a number of two to eight threads can speed up thumbnail generation considerably versus only one thread. The reason is not so much taking maximum advantage of all your CPU cores – darktable's pixelpipe uses all of them in parallel anyway – but hiding I/O latency.

Une exception vaut la peine d'être mentionnée. Si vous utilisez darktable pour traiter des vues panoramiques par assemblage (par exemple des TIFFs générés par le logiciel Hugin) alors ces images peuvent atteindre des tailles considérables. Chaque fil d'exécution a besoin d'allouer suffisamment de mémoire pour garder dans ses tampons une image complète, des intermédiaires et l'image de sortie. Ceci peut rapidement conduire à un dépassement de mémoire même avec un système 64 bits bien équipé. Dans ce cas réduisez à un le nombre de fils d'exécution.

