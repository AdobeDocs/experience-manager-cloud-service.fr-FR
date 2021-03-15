---
title: Guide de démarrage rapide sur la création de modèles de fragments de contenu découplés
description: Les modèles de fragments de contenu définissent la structure du contenu que vous allez créer et diffuser à l’aide des fonctionnalités de découplage d’AEM.
translation-type: tm+mt
source-git-commit: d37342feb794b9f1385bb5edd38b2d9bb6e7dff9
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 100%

---


# Guide de démarrage rapide sur la création de modèles de fragments de contenu découplés {#creating-content-fragment-models}

Les modèles de fragments de contenu définissent la structure du contenu que vous allez créer et diffuser à l’aide des fonctionnalités de découplage d’AEM.

## Que sont les modèles de fragments de contenu ? {#what-are-content-fragment-models}

[Maintenant que vous avez créé une configuration,](create-configuration.md) vous pouvez l’utiliser pour créer des modèles de fragments de contenu.

Les modèles de fragments de contenu définissent la structure des données et du contenu que vous allez créer et gérer dans AEM. Il s’agit en quelque sorte du squelette de votre contenu. Lorsque vous choisissez de créer du contenu, vos auteurs choisissent parmi les modèles de fragment de contenu que vous définissez, ce qui les guide dans la création de contenu.

## Création d’un modèle de fragment de contenu {#how-to-create-a-content-fragment-model}

Un architecte de l’information ne réaliserait ces tâches qu’occasionnellement, lorsque de nouveaux modèles sont nécessaires. Pour les besoins de ce guide de prise en main, nous n’avons besoin de créer qu’un modèle.

1. Connectez-vous à AEM as a Cloud Service et, dans le menu principal, sélectionnez **Outils > Ressources > Modèles de fragments de contenu**.
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
1. Lorsque vous avez fini de créer votre modèle, appuyez ou cliquez sur **Enregistrer**. Le modèle que vous venez de créer est enregistré en mode **Brouillon**.

   ![Modèle en mode Brouillon](../assets/models-draft.png)
1. Le modèle doit être activé pour pouvoir l’utiliser (s’il ne l’est pas déjà). Sélectionnez le modèle que vous venez de créer, puis appuyez ou cliquez sur **Activer**.

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
>Pour plus d’informations sur les modèles de fragments de contenu, voir la [documentation sur les modèles de fragments de contenu](/help/assets/content-fragments/content-fragments-models.md).
