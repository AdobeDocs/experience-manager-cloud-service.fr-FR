---
title: Création de modèles de fragment de contenu - Configuration découplée
description: Définissez la structure du contenu que vous allez créer et diffuser à l’aide des fonctionnalités découplées AEM à l’aide des modèles de fragment de contenu.
exl-id: 8e3e4d00-34d3-4d4f-bc3a-43b8a322b986
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 91%

---

# Création de modèles de fragment de contenu - Configuration découplée {#creating-content-fragment-models}

Définissez la structure du contenu que vous allez créer et diffuser à l’aide des fonctionnalités découplées AEM à l’aide des modèles de fragment de contenu.

## Que sont les modèles de fragments de contenu ? {#what-are-content-fragment-models}

[Maintenant que vous avez créé une configuration,](create-configuration.md) vous pouvez l’utiliser pour créer des modèles de fragments de contenu.

Les modèles de fragments de contenu définissent la structure des données et du contenu que vous allez créer et gérer dans AEM. Il s’agit en quelque sorte du squelette de votre contenu. Lorsque vous choisissez de créer du contenu, vos auteurs choisissent parmi les modèles de fragment de contenu que vous définissez, ce qui les guide dans la création de contenu.

## Création d’un modèle de fragment de contenu {#how-to-create-a-content-fragment-model}

Un architecte de l’information ne réaliserait ces tâches qu’occasionnellement, lorsque de nouveaux modèles sont nécessaires. Pour les besoins de ce guide de prise en main, nous n’avons besoin de créer qu’un modèle.

1. Connectez-vous à AEM as a Cloud Service et, dans le menu principal, sélectionnez **Outils**, **Général**, **Modèles de fragments de contenu**.
1. Appuyez ou cliquez sur le dossier créé lors de la configuration.

   ![Le dossier de modèles](../assets/models-folder.png)
1. Appuyez ou cliquez sur **Créer**.
1. Définissez le **Titre du modèle**, les **Balises** et la **Description**. Vous pouvez également sélectionner/désélectionner l’option **Activer le modèle** pour contrôler si le modèle est immédiatement activé lors de sa création.

   ![Création d’un modèle](../assets/models-create.png)
1. Dans la fenêtre de confirmation, appuyez ou cliquez sur **Ouvrir** pour configurer votre modèle.

   ![Fenêtre de confirmation](../assets/models-confirmation.png)
1. Utilisez l’**Éditeur de modèles de fragment de contenu** pour créer votre modèle de fragment de contenu en faisant glisser des champs depuis la colonne **Types de données**.

   ![Glisser-déposer des champs](../assets/models-drag-and-drop.png)

1. Une fois que vous avez placé un champ, vous devez configurer ses propriétés. L’éditeur bascule automatiquement sur l’onglet **Propriétés** pour le champ ajouté où vous pouvez fournir les champs obligatoires.

   ![Configuration des propriétés](../assets/models-configure-properties.png)

1. Lorsque vous avez fini de créer votre modèle, appuyez ou cliquez sur **Enregistrer**.

1. Le mode du modèle que vous venez de créer varie selon que vous avez sélectionné ou non **Activer le modèle** lors de la création du modèle :
   * sélectionné - le nouveau modèle sera déjà **Activé**.
   * non sélectionné : le nouveau modèle est créé dans **Version préliminaire** mode

1. Si elle n’est pas déjà activée, le modèle doit être **Activé** pour l’utiliser.
   1. Sélectionnez le modèle que vous venez de créer, puis appuyez ou cliquez sur **Activer**.

      ![Activation du modèle](../assets/models-enable.png)
   1. Confirmez l’activation du modèle en appuyant ou en cliquant sur **Activer** dans la boîte de dialogue de confirmation.

      ![Activation de la boîte de dialogue de confirmation](../assets/models-enabling.png)
1. Le modèle est désormais activé et prêt à l’emploi.

   ![Modèle activé](../assets/models-enabled.png)

L’**Éditeur de modèles de fragment de contenu** prend en charge de nombreux types de données différents, tels que des champs de texte simples, des références à des ressources, des références à d’autres modèles, ainsi que des données JSON.

Vous pouvez créer plusieurs modèles. Les modèles peuvent faire référence à d’autres fragments de contenu. Utilisez [configurations](create-configuration.md) pour organiser vos modèles.

## Étapes suivantes {#next-steps}

Maintenant que vous avez défini les structures de vos fragments de contenu en créant des modèles, vous pouvez passer à la troisième partie du guide de prise en main et [créer des dossiers dans lesquels vous stockerez les fragments.](create-assets-folder.md)

>[!TIP]
>
>Pour plus d’informations sur les modèles de fragments de contenu, voir la [documentation sur les modèles de fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-models.md).
