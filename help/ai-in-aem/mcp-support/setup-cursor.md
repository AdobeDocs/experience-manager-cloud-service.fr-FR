---
title: Configuration du curseur avec AEM MCP
description: Découvrez comment configurer Cursor pour vous connecter aux serveurs MCP AEM
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: f0897898-cb1d-4af6-859c-f5a1c0ec6168
source-git-commit: f7a5c43a4a4dd6629225f3628a7c592056d6d144
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Configuration du curseur avec AEM MCP {#setup-cursor}

Pour connecter Cursor aux serveurs MCP AEM, procédez comme suit.

* Dans les paramètres MCP du curseur, créez une entrée de serveur MCP avec une ou plusieurs URL MCP AEM.
* Authentifiez-vous avec votre Adobe ID lorsque vous y êtes invité.
* Vous pouvez éventuellement activer ou désactiver des outils individuels en cliquant sur leur nom. Tous les outils sont activés par défaut.
* Utilisez l’éditeur du curseur ou la conversation pour appeler les outils AEM dans le cadre des workflows de développement ou de contenu.

>[!NOTE]
>
>L’interface utilisateur du curseur peut changer et n’est pas définitive. Ces instructions sont fournies à titre d’illustration.

1. Ouvrez **Cursor Settings** pour configurer la manière dont Cursor se connecte aux serveurs MCP.

   ![Boîte de dialogue Paramètres du curseur.](assets/cursor-1.png)

1. Ouvrez **Outils et MCP**, puis choisissez **Ajouter un MCP personnalisé** pour démarrer une entrée de serveur MCP personnalisé.

   ![Le panneau Outils et MCP avec la possibilité d’ajouter un serveur MCP personnalisé.](assets/cursor-2.png)

1. Dans le formulaire du serveur de MCP personnalisé, saisissez le **Nom**, votre **URL** (ou vos URL) AEM MCP et tout autre champ obligatoire, puis **Enregistrer**.

   ![Formulaire des paramètres du serveur MCP personnalisé dans Cursor.](assets/cursor-3.png)

1. Lorsque la boîte de dialogue de connexion s’affiche, terminez la connexion en appuyant sur **Connect** afin que le nouveau serveur MCP soit autorisé.

   ![Boîte de dialogue de connexion du nouveau serveur MCP dans Cursor.](assets/cursor-4.png)

1. Dans **Chat** ou dans l’éditeur, écrivez des invites qui appellent **les outils AEM** afin que le serveur MCP configuré participe à votre workflow.

   ![Invitation du curseur à utiliser le nouveau service AEM MCP.](assets/cursor-5.png)
