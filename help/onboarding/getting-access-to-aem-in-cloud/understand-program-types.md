---
title: Présentation des types de Programme et de Programme
description: Présentation des types de Programme et de Programme - Cloud Services
translation-type: tm+mt
source-git-commit: 6e8cf08ec3f85437a8472a45895f3818e473e98c
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 13%

---


# Présentation des programmes et des types de programmes {#understanding-programs}

Dans Cloud Manager, l’entité locataire se trouve tout en haut de l’écran et peut comporter plusieurs Programmes. Chaque Programme ne peut pas contenir plus d’un environnement de production et plusieurs environnements non productifs.

Le diagramme suivant présente la hiérarchie des entités dans Cloud Manager.

![image](assets/program-types1.png)

## Référentiel de code source {#source-code-repository}

Le programme Cloud Manager est fourni avec son propre référentiel git.

Pour qu’un utilisateur puisse accéder au référentiel Git de Cloud Manager, il doit utiliser un client Git avec un outil de ligne de commande, un client Git visuel autonome ou l’IDE de l’utilisateur tel qu’Eclipse, IntelliJ, NetBeans.

Une fois un client Git configuré, vous pouvez gérer votre référentiel Git à partir de l’interface utilisateur de Cloud Manager. Pour savoir comment gérer Git à l’aide de l’interface utilisateur de Cloud Manager, voir [Accès à Git](/help/implementing/cloud-manager/accessing-git.md).

Pour commencer à développer l’application AEM Cloud, une copie locale du code de l’application doit être effectuée en l’extrayant du référentiel Cloud Manager vers un emplacement sur leur ordinateur local où ils souhaitent créer leur référentiel.

```java
$ git clone {URL}
```

>[!NOTE]
>Un utilisateur peut extraire une copie de son code et effectuer des modifications dans le référentiel de code local. Une fois prêt, l’utilisateur peut valider les modifications de code dans le référentiel de code distant dans Cloud Manager.

## Types de programme {#program-types}

Un utilisateur peut créer un programme **Sandbox** ou **Production**.

* Un *Programme de production* est créé pour activer le trafic actif au moment approprié dans le futur.
Voir [Introduction aux Programmes de production](/help/onboarding/getting-access-to-aem-in-cloud/introduction-production-programs.md) pour plus de détails.


* Un *Programme Sandbox* est généralement créé pour servir à la formation, à l’exécution de démonstrations, à l’activation, aux points de vue ou à la documentation. Il n&#39;est pas destiné à transporter du trafic réel et aura des restrictions qu&#39;un programme de production ne fera pas. Il comprendra des sites et des ressources et sera livré automatiquement avec une branche Git comprenant un exemple de code, un environnement Dev et un pipeline non productif.
Voir [Introduction aux Programmes Sandbox](/help/onboarding/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) pour plus de détails.

