---
title: Création d’un dossier de ressources - Configuration découplée
description: Utilisez des modèles de fragment de contenu AEM pour définir la structure des fragments de contenu, à la base de votre contenu découplé.
exl-id: 9a156a17-8403-40fc-9bd0-dd82fb7b2235
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 38a4bf89e099432163163e90e08aa0f47407724f
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 81%

---

# Création d’un dossier de ressources - Configuration découplée {#creating-an-assets-folder}

Utilisez des modèles de fragment de contenu AEM pour définir la structure des fragments de contenu, à la base de votre contenu découplé. Ces fragments sont ensuite stockés dans des dossiers de ressources.

## Qu’est-ce qu’un dossier de ressources ?  {#what-is-an-assets-folder}

[Maintenant que vous avez créé des modèles de fragments de contenu](create-content-model.md) qui définissent la structure souhaitée pour vos futurs fragments de contenu, vous êtes probablement enthousiaste à l’idée d’en créer.

Cependant, vous devez d’abord créer un dossier de ressources pour les stocker.

Les dossiers de ressources sont utilisés pour [organiser des ressources de contenu traditionnelles](/help/assets/manage-digital-assets.md) tels que des images et des vidéos, ainsi que des fragments de contenu.

## Création et configuration d’un dossier Assets {#create-and-configure-an-assets-folder}

Un administrateur n’a besoin de créer des dossiers qu’occasionnellement pour organiser le contenu au fur et à mesure de sa création. Utilisez la console Assets pour créer votre dossier.

Une fois créée, vous devez appliquer votre [configuration](/help/headless/setup/create-configuration.md) au dossier. Pour plus d’informations, consultez [Application de la configuration à votre dossier](/help/sites-cloud/administering/content-fragments/setup.md#apply-the-configuration-to-your-folder).

Vous pouvez créer des sous-dossiers supplémentaires dans le dossier que vous venez de créer. Les sous-dossiers hériteront de la **configuration du cloud** du dossier parent. Vous pouvez toutefois le remplacer si vous souhaitez utiliser des modèles d’une autre configuration.

Si vous utilisez une structure de site localisée, vous pouvez [créer une racine de langue](/help/assets/translate-assets.md) sous votre nouveau dossier.

## Étapes suivantes {#next-steps}

Maintenant que vous avez créé un dossier pour vos fragments de contenu, vous pouvez passer à la quatrième partie du guide de prise en main et [créer des fragments de contenu](create-content-fragment.md).

>[!TIP]
>
>Pour plus d’informations sur la gestion des fragments de contenu, voir la [documentation sur les fragments de contenu](/help/sites-cloud/administering/content-fragments/overview.md).
