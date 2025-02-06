---
title: Création de fragments de contenu - Configuration découplée
description: Découvrez comment utiliser les fragments de contenu AEM pour concevoir, créer, organiser et utiliser du contenu indépendant des pages pour une diffusion découplée.
exl-id: a227ae2c-f710-4968-8a00-bfe48aa66145
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 72%

---

# Création de fragments de contenu - Configuration découplée {#creating-content-fragments}

Découvrez comment utiliser les fragments de contenu AEM pour concevoir, créer, organiser et utiliser du contenu indépendant des pages pour une diffusion découplée.

## Que sont les fragments de contenu ?  {#what-are-content-fragments}

[Maintenant que vous avez créé un dossier de ressources](create-assets-folder.md) dans lequel vous pouvez stocker vos fragments de contenu, vous pouvez créer les fragments.

Les fragments de contenu permettent de concevoir, créer, organiser et publier du contenu indépendant des pages. Ils permettent de préparer le contenu prêt à être utilisé dans des emplacements multiples et sur plusieurs canaux.

Les fragments de contenu contiennent du contenu structuré et peuvent être diffusés au format JSON.

## Création d’un fragment de contenu {#how-to-create-a-content-fragment}

Les auteurs et autrices de contenu créeront n’importe quel nombre de fragments de contenu pour représenter le contenu créé. Il s’agit-là de leur principale tâche dans AEM. Pour les besoins de ce guide de prise en main, nous n’aurons besoin d’en créer qu’un.

1. Connectez-vous à AEM as a Cloud Service et dans le menu principal, sélectionnez **Navigation** > **Fragments de contenu**.

1. Sélectionnez le [dossier créé précédemment](create-assets-folder.md).
1. Sélectionnez **Créer**.
1. La création d’un fragment de contenu est présentée sous la forme d’une boîte de dialogue.
Sélectionnez l’emplacement et le modèle à utiliser pour créer votre fragment de contenu.

   * Les modèles disponibles dépendent de la [**configuration cloud** que vous avez définie pour le dossier de ressources](create-assets-folder.md) dans lequel vous créez le fragment de contenu.
   * Si votre modèle n’est pas disponible, vérifiez la configuration de votre dossier de ressources.

   Ajoutez le titre, le nom et, si nécessaire, la description.

   ![Boîte de dialogue Créer un fragment de contenu](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

1. Sélectionnez **Créer** ou **Créer et ouvrir**.

Les fragments de contenu peuvent faire référence à d’autres fragments de contenu, ce qui permet d’obtenir une structure de contenu imbriquée si nécessaire.

Les fragments de contenu peuvent également faire référence à d’autres ressources dans AEM. [Ces ressources doivent être stockées dans AEM](/help/assets/manage-digital-assets.md) avant de créer un fragment de contenu de référence.

## Étapes suivantes {#next-steps}

Maintenant que vous avez créé un fragment de contenu, vous pouvez passer à la dernière partie du guide de prise en main et [créer des demandes d’API pour accéder aux fragments de contenu et les diffuser](create-api-request.md).

>[!TIP]
>
>Pour plus d’informations sur la gestion des fragments de contenu, consultez la [documentation sur les fragments de contenu](/help/sites-cloud/administering/content-fragments/overview.md).
