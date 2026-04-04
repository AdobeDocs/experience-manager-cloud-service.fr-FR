---
title: Configuration de JetBrains avec GitHub Copilot et AEM MCP
description: Découvrez comment configurer le Copilote GitHub dans les IDE JetBrains pour vous connecter aux serveurs MCP AEM
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: e153da42-51e0-49ea-8457-10bb5e77e2de
source-git-commit: 81f85045212ca6fd92f2b665aeceaa0d4b92318c
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 1%

---

# Configuration de JetBrains avec GitHub Copilot et AEM MCP {#setup-jetbrains-copilot}

Suivez ces étapes pour connecter GitHub Copilot dans un IDE JetBrains (tel que IntelliJ IDEA, WebStorm ou PyCharm) aux serveurs MCP d’AEM.

1. Ouvrez GitHub Copilot Chat dans votre IDE JetBrains en cliquant sur l’icône **GitHub Copilot Chat** sur le côté droit de l’éditeur.

   ![L’IDE JetBrains avec le Module de conversation Copilote GitHub ouvert.](assets/jetbrains-copilot-1.png)

1. Cliquez sur l’icône **paramètres** dans le panneau Copilot Chat pour ouvrir la configuration MCP.

   ![Le panneau de conversation du copilote GitHub avec l’icône des paramètres en surbrillance.](assets/jetbrains-copilot-2.png)

1. Dans **Paramètres**, accédez à **Outils > Copilote GitHub > Modèle de protocole contextuel (MCP)** puis cliquez sur **Configurer** pour ouvrir le fichier de configuration `mcp.json`.

   ![Boîte de dialogue Paramètres JetBrains présentant la configuration du protocole MCP (Model Context Protocol) sous Copilote GitHub.](assets/jetbrains-copilot-3.png)

1. Ajoutez une ou plusieurs URL de serveur AEM MCP au fichier `mcp.json`. Par exemple :

   ```json
   {
     "servers": {
       "aem": {
         "url": "https://mcp.adobeaemcloud.com/adobe/mcp/content"
       }
     }
   }
   ```


   ![Le fichier de configuration mcp.json avec l’URL du serveur MCP AEM.](assets/jetbrains-copilot-4.png)


1. Enregistrez le fichier. Le copilote GitHub détecte automatiquement la nouvelle configuration de serveur et affiche une action **Start**.

   ![Fichier mcp.json affichant le serveur AEM configuré avec les outils détectés.](assets/jetbrains-copilot-5.png)

1. Cliquez sur l’action **Démarrer** et lorsque vous y êtes invité, connectez-vous avec votre Adobe ID pour terminer le flux d’authentification.

1. Vous pouvez vérifier et gérer les outils découverts en cliquant sur l’indicateur **tools** qui s’affiche dans le panneau Copilot Chat. Vous pouvez éventuellement activer ou désactiver des outils individuels.


   ![Boîte de dialogue Configurer les outils affichant les outils AEM MCP disponibles.](assets/jetbrains-copilot-6.png)

1. Utilisez le Module de conversation GitHub Copilot pour appeler les outils AEM dans le cadre de vos workflows de développement ou de contenu.
