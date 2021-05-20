---
title: Présentation des types de programme et de programme
description: Présentation des types de programme et de programme - Cloud Services
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 13%

---

# Présentation des programmes et des types de programmes {#understanding-programs}

Dans Cloud Manager, l’entité Tenant se trouve en haut de l’écran et peut comporter plusieurs programmes. Chaque programme ne peut pas contenir plus d’un environnement de production et plusieurs environnements hors production.

Le diagramme suivant présente la hiérarchie des entités dans Cloud Manager.

![image](assets/program-types1.png)

## Référentiel de code source {#source-code-repository}

Le programme Cloud Manager est fourni avec son propre référentiel Git.

Pour qu’un utilisateur puisse accéder au référentiel Git de Cloud Manager, il doit utiliser un client Git avec un outil de ligne de commande, un client Git visuel autonome ou l’IDE de l’utilisateur tel qu’Eclipse, IntelliJ, NetBeans.

Une fois qu’un client Git est configuré, vous pouvez gérer votre référentiel Git à partir de l’interface utilisateur de Cloud Manager. Pour en savoir plus sur la gestion de Git à l’aide de l’interface utilisateur de Cloud Manager, voir [Accès à Git](/help/implementing/cloud-manager/accessing-git.md).

Pour commencer à développer l’application AEM Cloud, une copie locale du code de l’application doit être effectuée en l’extrayant du référentiel Cloud Manager vers un emplacement sur l’ordinateur local où il souhaite créer son référentiel.

```java
$ git clone {URL}
```

>[!NOTE]
>Un utilisateur peut extraire une copie de son code et effectuer des modifications dans le référentiel de code local. Une fois prêt, l’utilisateur peut valider les modifications de code dans le référentiel de code distant dans Cloud Manager.

## Types de programme {#program-types}

Un utilisateur peut créer un programme **Sandbox** ou **Production**.

* Un *programme de production* est créé pour activer le trafic en direct au moment approprié à l’avenir.
Pour plus d’informations, voir [Présentation des programmes de production](/help/onboarding/getting-access-to-aem-in-cloud/introduction-production-programs.md).


* Un *programme Sandbox* est généralement créé à des fins de formation, d’exécution de démonstration, d’activation, de preuves de concept ou de documentation. Il n’est pas destiné à transporter du trafic en direct et aura des restrictions qu’un programme de production ne mettra pas en place. Elle comprend les sites et les ressources et est automatiquement renseignée avec une branche Git qui inclut un exemple de code, un environnement de développement et un pipeline hors production.
Pour plus d’informations, voir [Présentation des programmes Sandbox](/help/onboarding/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) .
