---
title: Configuration de Microsoft Copilot Studio avec AEM MCP
description: Découvrez comment configurer Microsoft Copilot Studio pour qu’il se connecte aux serveurs MCP AEM
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: c8e96fe6-1a05-47c0-8215-0c28705e5e48
source-git-commit: f7a5c43a4a4dd6629225f3628a7c592056d6d144
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Configuration de Microsoft Copilot Studio avec AEM MCP {#setup-microsoft-copilot-studio}

Pour connecter Microsoft Copilot Studio aux serveurs MCP AEM, procédez comme suit.

>[!NOTE]
>
>L’interface utilisateur de Microsoft Copilot Studio peut changer et n’est pas définitive. Ces instructions sont fournies à titre d’illustration.

1. Dans **Agents**, démarrez le flux pour ajouter un agent qui utilisera les outils AEM MCP.

   * Créez un agent.

   ![Panneau Agents dans Microsoft Copilot Studio.](assets/copilot-1.png)

1. Ouvrez la zone des outils de cet agent afin de pouvoir enregistrer la manière dont il appelle les fonctionnalités externes.

   * Accédez à la section Outil et cliquez sur **Ajouter un outil**.

   ![Boîte de dialogue Ajouter un outil dans Microsoft Copilot Studio.](assets/copilot-2.png)

1. Décidez de réutiliser une intégration existante ou de définir un nouvel outil pris en charge par MCP.

   * Sélectionnez un outil existant ou créez-en un.

   ![Sélection du protocole de contexte de modèle comme type d’outil.](assets/copilot-3.png)

1. Lorsque vous créez un outil MCP, passez à l’étape du serveur **Model Context Protocol**, y compris le mode Aperçu lorsqu’il apparaît.

   * Configurez un nouvel outil MCP pointant vers un ou plusieurs serveurs MCP AEM **URL**.

   ![Ajout d’un serveur Model Context Protocol en mode d’aperçu.](assets/copilot-4.png)

1. Définissez comment ce point d’entrée MCP est atteint par l’agent, y compris si l’accès est partagé ou dédié.

   * Établissez une connexion qui peut être **partagée** ou **dédiée** entre les agents.

   ![Boîte de dialogue permettant de créer une connexion.](assets/copilot-5.png)

1. Dans **Ajouter et configurer**, fournissez ou confirmez les détails de l’outil MCP afin que l’agent puisse atteindre votre environnement AEM.

   ![Panneau Ajouter et configurer de l’outil MCP.](assets/copilot-6.png)

1. Champs de fin du formulaire de l’outil MCP (par exemple, URL de serveur **URL** et options liées à l’authentification).

   * Vous pouvez éventuellement activer le **mode de confirmation automatique** ou exiger **confirmation de l’utilisateur final** pour toutes les interactions de l’outil.

   ![Formulaire de configuration de l’outil MCP.](assets/copilot-7.png)

1. Validez la connectivité avec le serveur MCP ; connectez-vous avec votre navigateur lorsque Copilot Studio vous redirige.

   * Connectez-vous à l’aide de votre **** après redirection.

   ![Test de la connexion au serveur MCP AEM.](assets/copilot-8.png)

1. Avant d’exécuter un test, ouvrez **Gérer les connexions** (ou le **gestionnaire de connexions**) et attribuez la connexion appropriée à votre session.

   * Lors du test de l’agent, ouvrez d’abord le **gestionnaire de connexions** pour attribuer une connexion à votre session.

   ![Le panneau Gérer les connexions affiche les connexions disponibles.](assets/copilot-9.png)

1. Dans l’expérience de test, exécutez l’agent sur votre connexion AEM MCP.

   * Lors du test de l’agent, appuyez sur **Réessayer** après avoir attribué une connexion dans le **gestionnaire de connexions**.

   ![Test de l’agent avec la connexion AEM MCP.](assets/copilot-10.png)
