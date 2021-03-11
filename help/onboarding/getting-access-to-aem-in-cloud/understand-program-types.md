---
title: Présentation des types de Programme et de Programme
description: Présentation des types de Programme et de Programme - Cloud Services
translation-type: tm+mt
source-git-commit: 5a4353cb31337882a1c13b0ed830ea64f617181a
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 3%

---


# Présentation des programmes et des types de programmes {#understanding-programs}

Dans Cloud Manager, l’entité locataire se trouve tout en haut de l’écran et peut comporter plusieurs Programmes. Chaque Programme ne peut pas contenir plus d’un environnement de production et plusieurs environnements non productifs.

Le diagramme suivant présente la hiérarchie des entités dans Cloud Manager.

![image](assets/program-types1.png)

## Types de programme {#program-types}

Un utilisateur peut créer un programme **Sandbox** ou **Production**.

* Un *Programme de production* est créé pour activer le trafic actif au moment approprié dans le futur.
Voir [Introduction aux Programmes de production](/help/onboarding/getting-access-to-aem-in-cloud/introduction-production-programs.md) pour plus de détails.


* Un *Programme Sandbox* est généralement créé pour servir à la formation, à l’exécution de démonstrations, à l’activation, aux points de vue ou à la documentation. Il n&#39;est pas destiné à transporter du trafic réel et aura des restrictions qu&#39;un programme de production ne fera pas. Il comprendra des sites et des ressources et sera livré automatiquement avec une branche Git comprenant un exemple de code, un environnement Dev et un pipeline non productif.
Voir [Introduction aux Programmes Sandbox](/help/onboarding/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) pour plus de détails.

