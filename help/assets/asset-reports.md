---
title: Rapports sur l’utilisation et le partage
description: Des rapports sur vos ressources dans  [!DNL Adobe Experience Manager Assets]  vous permettent de comprendre l’utilisation, l’activité et le partage de vos ressources numériques.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 3ee2e53268ea77949057ac18fcb4a8f8b1e01cb2
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 96%

---


# Rapports de ressources  {#asset-reports}

Les rapports de ressources vous permettent d’évaluer l’utilité de votre déploiement [!DNL Adobe Experience Manager Assets]. Avec [!DNL Assets], vous pouvez générer divers rapports pour vos ressources numériques. Les rapports fournissent des informations utiles concernant votre utilisation du système, la façon dont les utilisateurs interagissent avec les ressources et la façon dont les ressources sont téléchargées et partagées.

Utilisez les informations figurant dans les rapports de manière à obtenir des mesures de succès essentielles pour évaluer l’adoption d’[!DNL Assets] au sein de votre entreprise et par les clients.

Le framework de création de rapports [!DNL Assets] exploite des tâches [!DNL Sling] de façon à traiter de manière asynchrone les demandes de rapports en respectant l’ordre. Il est extensible pour les référentiels de grande taille. Le traitement asynchrone des rapports permet de générer des rapports de manière plus efficace et rapide.

L’interface de gestion de rapports est intuitive et inclut des options et des commandes précises pour accéder aux rapports archivés, ainsi qu’afficher les états d’exécution des rapports (réussite, échec et en file d’attente).

Lorsqu’un rapport est généré, vous êtes averti par <!-- through an email (optional) and --> une notification de boîte de réception. Vous pouvez afficher, télécharger ou supprimer un rapport de la page de liste des rapports, où tous les rapports précédemment générés sont affichés.

## Génération de rapports {#generate-reports}

[!DNL Experience Manager Assets] génère les rapports standard suivants :

* Chargement
* Téléchargement
* Expiration
* Modification
* Publication
* Publier sur [!DNL Brand Portal]
* Utilisation du disque
* Fichiers
* Partage de liens

Les administrateurs d’[!DNL Adobe Experience Manager] peuvent facilement générer et personnaliser ces rapports pour votre implémentation. Un administrateur peut procéder comme suit pour générer un rapport :

1. Dans l’interface [!DNL Experience Manager], cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Rapports]**.

   ![Page Outils pour parcourir le rapport des ressources](assets/navigation.png)

1. Sur la page [!UICONTROL Rapports de ressources], cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.
1. Sur la page **[!UICONTROL Créer un rapport]**, sélectionnez le rapport que vous souhaitez créer, puis cliquez sur **[!UICONTROL Suivant]**.

   ![Sélectionner le type de rapport](assets/choose_report.png)

<!-- TBD: How do enable this in CS now? Is it done using some OSGi config now?
   >[!NOTE]
   >
   >Before you can generate an **[!UICONTROL Asset Downloaded]** report, ensure that the Asset Download service is enabled. From the web console (`https://[aem_server]:[port]/system/console/configMgr`), open the **[!UICONTROL Day CQ DAM Event Recorder]** configuration, and select the **[!UICONTROL Asset Downloaded (DOWNLOADED)]** option in Event Types if not already selected.
-->

>[!NOTE]
>
>Par défaut, les fragments de contenu et les partages de lien sont inclus dans le rapport [!UICONTROL Ressource téléchargée]. Sélectionnez l’option appropriée pour créer un rapport de partages de lien ou pour exclure les fragments de contenu du rapport de téléchargement.

>[!NOTE]
>
>Le rapport [!UICONTROL Téléchargement] affiche uniquement les détails des ressources téléchargées après sélection individuelle ou téléchargées à l’aide de l’action rapide. Cependant, il n’inclut pas les détails des ressources figurant dans un dossier téléchargé.

1. Configurez les détails du rapport, tels que le titre, la description, la miniature et le chemin du dossier dans le référentiel CRX où le rapport est stocké. Par défaut, le chemin du dossier est `/content/dam`. Vous pouvez spécifier un autre chemin.

   ![Page d’ajout de détails de rapport](assets/report_configuration.png)

   Sélectionnez la période de votre rapport.

   Vous pouvez choisir de générer le rapport maintenant ou à une date et une heure ultérieures.

   >[!NOTE]
   >
   >Si vous choisissez de planifier le rapport à une date ultérieure, veillez à spécifier la date et l’heure dans les champs Date et Heure. Si vous ne spécifiez aucune valeur, le moteur de création de rapports traite le rapport comme devant être généré immédiatement.

   Les champs de configuration peuvent varier en fonction du type de rapport que vous créez. Par exemple, le rapport **[!UICONTROL Utilisation du disque]** fournit des options pour inclure les rendus de ressources lors du calcul de l’espace disque utilisé par les ressources. Vous pouvez choisir d’inclure ou d’exclure les ressources figurant dans les sous-dossiers pour le calcul de l’utilisation du disque.

   >[!NOTE]
   >
   >Le rapport **[!UICONTROL Utilisation du disque]** n’inclut pas les champs de période, car il indique uniquement l’utilisation actuelle de l’espace disque.

   ![Page Détails du rapport Utilisation du disque](assets/disk_usage_configuration.png)

   Lorsque vous créez le rapport **[!UICONTROL Fichiers]**, vous pouvez inclure/exclure les sous-dossiers. Cependant, vous ne pouvez pas inclure les rendus de ressources dans ce rapport.

   ![Page Détails du rapport Fichiers](assets/files_report.png)

   Le rapport **[!UICONTROL Partage de liens]** affiche les URL des ressources qui sont partagées avec des utilisateurs externes à partir d’[!DNL Assets]. <!-- It includes email ids of the user who shared the assets, emails ids of users with which the assets are shared, share date, and expiration date for the link. --> Les colonnes ne sont pas personnalisables.

   Le rapport **[!UICONTROL Partage de liens]** n’inclut pas d’options pour les sous-dossiers et les rendus, car il ne publie que les URL partagées qui apparaissent sous `/var/dam/share`.

   ![Page Détails du rapport Partage de liens](assets/link_share.png)

1. Cliquez sur **[!UICONTROL Suivant]** dans la barre d’outils.

1. Sur la page **[!UICONTROL Configurer les colonnes]**, certaines colonnes sont sélectionnées pour apparaître dans le rapport par défaut. Vous pouvez sélectionner plus de colonnes. Désélectionnez une colonne sélectionnée pour l’exclure du rapport.

   ![Sélectionner ou désélectionner des colonnes de rapports](assets/configure_columns.png)

   Pour afficher un chemin de propriété ou un nom de colonne personnalisé, configurez les propriétés du binaire de ressource sous le nœud `jcr:content` dans CRX. Vous pouvez également l’ajouter dans le sélecteur de chemin de propriété.

   ![Sélectionner ou désélectionner des colonnes de rapports](assets/custom_columns.png)

1. Cliquez sur **[!UICONTROL Créer]** dans la barre d’outils. Un message indique que la génération du rapport a été lancée.
1. Sur la page [!UICONTROL Rapports de ressources], l’état de la génération des rapports repose sur l’état actuel de la tâche de rapport ; par exemple [!UICONTROL Réussite], [!UICONTROL Échec], [!UICONTROL En file d’attente] ou [!UICONTROL Planifié]. Le même état s’affiche dans la boîte de réception des notifications. Pour afficher la page du rapport, cliquez sur le lien du rapport. Vous pouvez également sélectionner le rapport et cliquer sur **[!UICONTROL Afficher]** dans la barre d’outils.

   ![Un rapport généré](assets/report_page.png)

   Cliquez sur **[!UICONTROL Télécharger]** dans la barre d’outils pour télécharger le rapport au format CSV.

## Ajout de colonnes personnalisées  {#add-custom-columns}

Vous pouvez ajouter des colonnes personnalisées aux rapports suivants pour afficher davantage de données en fonction de vos besoins :

* Chargement
* Téléchargement
* Expiration
* Modification
* Publication
* Publier sur [!DNL Brand Portal]
* Fichiers

Pour ajouter des colonnes personnalisées à ces rapports, procédez comme suit :

1. Dans le [!DNL Manager interface], cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Rapports]**.
1. Sur la page [!UICONTROL Rapports de ressources], cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.

1. Sur la page **[!UICONTROL Créer un rapport]**, sélectionnez le rapport que vous souhaitez créer, puis cliquez sur **[!UICONTROL Suivant]**.
1. Configurez les détails du rapport, tels que le titre, la description, la miniature, le chemin du dossier et la période, le cas échéant.

1. Pour afficher une colonne personnalisée, spécifiez son nom sous **[!UICONTROL Colonnes personnalisées]**.

   ![Spécifier le nom de la colonne personnalisée du rapport](assets/custom_columns-1.png)

1. Ajoutez le chemin de la propriété sous le nœud `jcr:content` dans CRXDE à l’aide du sélecteur de chemin de propriété. Vous pouvez également saisir le chemin d’accès dans le champ de chemin d’accès à la propriété.

   ![Faites correspondre le chemin de la propriété des chemins dans jcr:content](assets/property_picker.png)

   Pour ajouter d’autres colonnes personnalisées, cliquez sur **[!UICONTROL Ajouter]** et répétez les étapes 5 et 6.

1. Cliquez sur **[!UICONTROL Créer]** dans la barre d’outils. Un message indique que la génération du rapport a été lancée.

<!-- TBD: How to configure purge now? Is it using OSGi configurations?

## Configure purging service {#configure-purging-service}

To remove reports that you no longer require, configure the DAM Report Purge service from the web console to purge existing reports based on their quantity and age.

1. Access the web console (configuration manager) from `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL DAM Report Purge Service]** configuration.
1. Specify the frequency (time interval) for the purging service in the `scheduler.expression.name` field. You can also configure the age and the quantity threshold for reports.
1. Save the changes.
-->

## Informations, conseils et limites de dépannage {#best-practices-and-limitations}

* Si le rapport d&#39;utilisation des disques n&#39;est pas généré et que vous utilisez [!DNL Dynamic Media], assurez-vous que toutes les ressources sont correctement traitées. Pour résoudre ce problème, retraitez les ressources, puis générez de nouveau le rapport.
