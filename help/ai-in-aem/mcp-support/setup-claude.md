---
title: Configuration d’Anthropic Claude avec AEM MCP
description: Découvrez comment configurer Anthropic Claude pour qu’il se connecte aux serveurs MCP AEM
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 2b90b2b2-cdd0-4f1e-890f-2f58f578face
source-git-commit: fede808fcd8b082a71273bf9ffceb48b5332f45d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Configuration d’Anthropic Claude avec AEM MCP {#setup-claude}

Pour connecter Anthropic Claude aux serveurs MCP AEM, procédez comme suit.

* Dans la configuration MCP de Claude, enregistrez une ou plusieurs URL de serveur MCP AEM.
* Terminez le flux de connexion à Adobe.
* Vous pouvez éventuellement activer la confirmation automatique pour certains outils dans la zone de configuration. Cette option est recommandée pour les opérations de recherche ou de lecture seule.
* Assurez-vous que le serveur MCP est sélectionné avant de commencer votre conversation.
* Demandez à Claude d’effectuer des tâches liées à AEM. Claude sélectionne les outils AEM exposés par le serveur MCP en fonction de votre invite.

Pour configurer Claude pour AEM MCP, procédez comme suit :

>[!NOTE]
>
>L’interface utilisateur de Claude peut faire l’objet de modifications et n’est pas définitive. Ces instructions sont fournies à titre d’illustration.

1. Ouvrez le menu Compte dans le coin inférieur gauche de l’application web Claude et choisissez **Paramètres** pour ouvrir la zone Paramètres .

   ![Menu Compte dans Claude avec les paramètres sélectionnés.](assets/claude-1.png)

1. Dans la barre latérale Paramètres, sélectionnez **Connecteurs**. Sur la page Connecteurs, choisissez **Ajouter un connecteur personnalisé** pour enregistrer un point d’entrée MCP personnalisé.

   ![Page Connecteurs dans Paramètres avec Ajouter un connecteur personnalisé.](assets/claude-2.png)

1. Dans la boîte de dialogue **Ajouter un connecteur personnalisé**, saisissez un nom d’affichage (par exemple, **Service AEM Content MCP**) et l’URL de votre serveur AEM MCP, puis choisissez **Ajouter**. Utilisez **Paramètres avancés** uniquement lorsque votre déploiement nécessite des options supplémentaires.

   ![Ajout d’une boîte de dialogue de connecteur personnalisé avec le nom et l’URL MCP.](assets/claude-3.png)

1. Dans la liste Connecteurs, recherchez votre entrée de connecteur personnalisée (elle affiche un libellé **CUSTOM**) et choisissez **Connect** pour vous connecter et lier le connecteur à votre compte Claude.

   ![Liste des connecteurs avec l’option Connexion sélectionnée pour le service AEM Content MCP.](assets/claude-4.png)

1. Lorsque le connecteur apparaît dans la liste avec son URL, choisissez **Configurer** en regard de **Service AEM Content MCP** pour afficher les détails du connecteur et poursuivre la configuration.

   ![Liste des connecteurs avec l’option Configurer sélectionnée pour le service AEM Content MCP.](assets/claude-5.png)

1. Sur la page **Autorisations des outils**, vérifiez les valeurs par défaut (par exemple, **Approbation requise**), puis définissez chaque outil AEM sur **Toujours autoriser**, **Demander l’autorisation** ou **Jamais autoriser** conformément à votre politique de sécurité.

   ![Autorisations d’outil pour le service AEM Content MCP.](assets/claude-6.png)

1. Ouvrez une conversation. Sélectionnez les outils et le menu de modèle (icône curseurs) à gauche du champ de message, activez **Service AEM Content MCP** sous Connecteurs, puis saisissez votre invite afin que Claude puisse utiliser les outils MCP pour cette conversation.

   ![Compositeur de conversation avec le service AEM Content MCP activé dans le menu des outils.](assets/claude-7.png)

## Connecteur Adobe Experience Manager Claude {#aem-claude-connector}

Pour installer le **connecteur Claude**, ouvrez **Paramètres** > **Connecteurs** dans Claude. Vous pouvez également ouvrir la page Connecteurs directement sur [&#128279;](https://claude.ai/settings/connectors). Le connecteur enregistre un serveur MCP qui expose un ensemble croissant d’outils pour les workflows AEM.

![Installation du connecteur Adobe Experience Manager Claude à partir du répertoire des connecteurs.](assets/claude-connector.png)