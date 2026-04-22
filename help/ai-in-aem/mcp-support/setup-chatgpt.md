---
title: Configuration de OpenAI ChatGPT avec AEM MCP
description: Découvrez comment configurer OpenAI ChatGPT pour qu’il se connecte aux serveurs MCP AEM
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 1f116225-168b-483c-9df6-c752a573b57b
source-git-commit: f7a5c43a4a4dd6629225f3628a7c592056d6d144
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Configuration de OpenAI ChatGPT avec AEM MCP {#setup-chatgpt}

Pour connecter OpenAI ChatGPT aux serveurs MCP AEM, procédez comme suit.

* Ajoutez une ou plusieurs URL de serveur MCP AEM dans la zone où les connexions ou outils MCP sont configurés.
* Déclenchez la connexion et connectez-vous avec votre Adobe ID en cas de redirection.
* Dans une conversation, référencez les outils AEM configurés dans vos invites, par exemple :

  ```
  "Using the configured AEM MCP tools, list all sites in the author environment."
  ```

>[!NOTE]
>
>L’interface utilisateur de OpenAI ChatGPT peut changer et n’est pas définitive. Ces instructions sont fournies à titre d’illustration.

1. Ouvrez **Paramètres** pour accéder à la zone où les connexions ou outils MCP sont configurés.

   ![Boîte de dialogue Paramètres ChatGPT.](assets/chatgpt-1.png)

1. Dans **Applications et connecteurs**, ouvrez **Paramètres avancés** pour gérer les options de connecteur et les options liées au MCP.

   ![Panneau Paramètres avancés des applications et des connecteurs dans ChatGPT.](assets/chatgpt-2.png)

1. Activez le **mode Développeur** dans **Applications et connecteurs** afin de pouvoir ajouter et configurer des applications ou des connecteurs personnalisés.

   ![Activation du mode Développeur dans la section Applications et connecteurs.](assets/chatgpt-3.png)

1. Démarrez **Créer une application** (ou un contrôle équivalent) pour ajouter une entrée d’application pour votre serveur MCP AEM.

   ![Boîte de dialogue pour la création d’une application dans ChatGPT.](assets/chatgpt-4.png)

1. Remplissez le formulaire **Nouvelle application** par exemple, nommez l’application et saisissez l’URL de votre serveur AEM MCP et tout autre champ obligatoire, puis **Enregistrez**.

   ![Formulaire de configuration de la nouvelle application dans ChatGPT.](assets/chatgpt-5.png)

1. Confirmez que le service **AEM Content MCP** (ou votre application configurée) apparaît dans **Applications et connecteurs** pour que ChatGPT puisse l’utiliser.

   ![Service AEM Content MCP répertorié dans Applications et connecteurs.](assets/chatgpt-6.png)

1. Dans une conversation, écrivez une invite qui indique à ChatGPT d’utiliser les **outils AEM configurés** (par exemple, pour interroger du contenu ou des sites de création).

   ![Inviter ChatGPT à utiliser le service AEM Content MCP.](assets/chatgpt-7.png)
