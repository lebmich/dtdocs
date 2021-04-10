---
author: people
draft: 'false'
id: how-opencl-works
title: 'comment travaille opencl'
weight: 20
---

Comme vous pouvez l’imaginer, les architectures matérielles des GPU peuvent être très différentes. Il y a différents fabricants, et même, pour le même fabricant, différentes générations de GPU peuvent être différentes. Dans le même temps, les fabricants de GPU ne rendent pas public tous les détails matériels de leurs produits. Une des conséquences connues est la nécessité d’utiliser sous Linux des pilotes propriétaires si vous désirez tirer le maximum de votre carte graphique.

Fortunately an industry consortium lead by The Khronos Group has developed an open, standardized interface called OpenCL. It allows your GPU to be used as a numerical processing device. OpenCL offers a C99-like programming language with a strong focus on parallel computing. An application that wants to use OpenCL will need OpenCL source code that it hands over to a hardware specific compiler at run-time. This way the application can use OpenCL on different GPU architectures (even at the same time). All of the hardware “secrets” are hidden in this compiler and are normally not visible to the user (or the application). The compiled OpenCL code is loaded onto your GPU and – with certain API calls – it is ready to perform calculations for you. 
