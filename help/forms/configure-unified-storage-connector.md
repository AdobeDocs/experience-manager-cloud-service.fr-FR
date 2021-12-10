---
title: Comment configurer le connecteur de stockage unifié pour AEM Forms ?
description: Découvrez comment gérer le connecteur de stockage unifié pour AEM Forms. Utilisez le connecteur de stockage unifié pour connecter AEM Forms à des stockages de données externes.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 100%

---


# Gestion du connecteur de stockage unifié pour AEM Forms {#manage-unified-storage-connector}

Vous pouvez utiliser le connecteur de stockage unifié pour connecter AEM Forms à des stockages de données externes.

Par exemple, vous pouvez remplir les valeurs des champs d’un formulaire adaptatif et les envoyer à un workflow AEM. Vous pouvez configurer des workflows AEM pour stocker des données dans un stockage externe, tel que le serveur de stockage Microsoft Azure. Utilisez le connecteur de stockage unifié pour créer une connexion entre les workflows AEM et le stockage externe.

## Connexion de workflows AEM à un serveur de stockage Microsoft Azure {#connect-workflows-with-azure}

Créez une configuration de stockage Azure et référez-vous à cette configuration à l’aide du connecteur de stockage unifié. Vous pouvez ensuite configurer les modèles de workflow AEM pour externaliser l’enregistrement des données afin de les connecter à un serveur de stockage Azure.

### Créer une configuration de stockage [!DNL Azure] {#create-azure-storage-configuration}

Avant d’exécuter ces étapes, vérifiez que vous disposez d’un compte de stockage [!DNL Azure] et d’une clé d’accès pour autoriser l’accès au compte de stockage [!DNL Azure].

Pour créer une configuration de stockage [!DNL Azure], procédez comme suit :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Stockage Azure]**.
1. Sélectionnez un dossier pour créer la configuration et appuyez sur **[!UICONTROL Créer]**.
1. Indiquez un titre pour la configuration dans le champ **[!UICONTROL Titre]**.
1. Indiquez le nom du compte de stockage [!DNL Azure] dans le champ **[!UICONTROL Compte de stockage Azure]**.
1. Indiquez la clé pour accéder au compte de stockage Azure dans le champ **[!UICONTROL Clé d’accès Azure]** et appuyez sur **[!UICONTROL Enregistrer]**.

### Configuration du connecteur de stockage unifié pour les workflows AEM {#configure-unified-storage-connector-workflows}

Suivez les étapes suivantes pour configurer le connecteur de stockage unifié pour les workflows AEM :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Connecteur de stockage unifié]**.

1. Dans la section **[!UICONTROL Workflow]**, sélectionnez **[!UICONTROL Azure]** dans la liste déroulante Stockage.
1. Spécifiez le [chemin de configuration pour la configuration de stockage Azure](#create-azure-storage-configuration) dans le champ **[!UICONTROL Chemin de configuration de stockage]**.
1. Appuyez sur **[!UICONTROL Publier]**, puis sur **[!UICONTROL Enregistrer]** pour enregistrer la configuration.

### Configuration d’un modèle de workflow AEM pour le stockage de données externe {#configure-workflow-external-data-storage}

Suivez les étapes suivantes pour configurer un modèle de workflow AEM pour un stockage de données externe :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Workflows]** > **[!UICONTROL Modèles]**.
1. Sélectionnez un nom de modèle et appuyez sur **[!UICONTROL Modifier]**.
1. Appuyez sur l’icône Informations sur la page et appuyez sur **[!UICONTROL Ouvrir les propriétés]**.
1. Sélectionnez **[!UICONTROL Externaliser le stockage des données de workflow]**.
1. Appuyez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer les propriétés.

>[!NOTE]
>
>Les options permettant d’enregistrer l’étape Affecter une tâche en tant que brouillon et de récupérer l’historique de l’étape Affecter une tâche ne sont pas disponibles lorsque vous configurez un modèle de workflow AEM pour le stockage de données externe.

### Recommandations pour les workflows d’AEM pour le stockage de données externes {#guidelines-workflows-external-data-storage}

Voici nos recommandations concernant l’utilisation des workflows AEM et le stockage de données externes tels que le serveur de stockage Microsoft Azure :

* Utilisez des variables pour stocker des données lors de la définition de fichiers de données d’entrée et de sortie et de pièces jointes dans les étapes du modèle de workflow. Ne sélectionnez pas les options **[!UICONTROL Relatif à la charge]** et **[!UICONTROL Disponible sur un chemin absolu]**. Les options **[!UICONTROL Relatif à la charge]** et **Disponible sur un chemin absolu** ne s’affichent pas automatiquement lorsque vous [configurez un modèle de workflow AEM pour le stockage de données externes](#configure-workflow-external-data-storage).

* Utilisez des variables pour stocker le fichier de données et les pièces jointes lors de l’envoi d’un formulaire adaptatif à un workflow AEM. Ne sélectionnez pas l’option **[!UICONTROL Relatif à la charge]** lors de l’envoi d’un formulaire adaptatif à un workflow AEM. L’option **[!UICONTROL Relatif à la charge]** ne s’affiche pas automatiquement une fois que vous avez [configuré un modèle de workflow AEM pour le stockage des données externes](#configure-workflow-external-data-storage).

* N’utilisez pas d’étape de workflow AEM personnalisée dans un modèle de workflow pour stocker des données dans le référentiel CRX DE.

* Lorsque vous [configurez un modèle de workflow AEM pour le stockage des données externes](#configure-workflow-external-data-storage), ne créez pas de colonnes personnalisées dans la boîte de réception AEM en fonction des données d’un workflow.
