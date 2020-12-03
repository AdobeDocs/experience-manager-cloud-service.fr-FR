---
title: Rapports sur l’utilisation et le partage
description: Rapports sur vos ressources dans  [!DNL Adobe Experience Manager Assets] qui vous aident à comprendre l’utilisation, l’activité et le partage de vos ressources numériques.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 3ee2e53268ea77949057ac18fcb4a8f8b1e01cb2
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 42%

---


# Rapports de ressources   {#asset-reports}

Le rapports des ressources vous permet d’évaluer l’utilité de votre déploiement [!DNL Adobe Experience Manager Assets]. [!DNL Assets] permet de générer divers rapports pour vos ressources numériques. Les rapports fournissent des informations utiles concernant votre utilisation du système, la façon dont les utilisateurs interagissent avec les ressources et la façon dont les ressources sont téléchargées et partagées.

Utilisez les informations des rapports pour dériver des mesures de réussite clés afin de mesurer l&#39;adoption de [!DNL Assets] dans votre entreprise et par les clients.

La structure de rapports [!DNL Assets] utilise les tâches [!DNL Sling] pour traiter les demandes de rapports de manière asynchrone et ordonnée. Elle est extensible pour les référentiels de grande taille. Le traitement asynchrone des rapports permet de générer des rapports de manière plus efficace et rapide.

L’interface de gestion de rapports est intuitive et inclut des options et des commandes précises pour accéder aux rapports archivés, ainsi qu’afficher les états d’exécution des rapports (réussite, échec et en file d’attente).

Lorsqu’un rapport est généré, vous êtes averti par <!-- through an email (optional) and --> une notification de boîte de réception. Vous pouvez afficher, télécharger ou supprimer un rapport de la page de liste des rapports, où tous les rapports précédemment générés sont affichés.

## Génération de rapports {#generate-reports}

[!DNL Experience Manager Assets] génère les rapports standard suivants pour vous :

* Charger
* Téléchargement
* Expiration
* Modification
* Publier
* [!DNL Brand Portal] publish
* Utilisation du disque
* Fichiers
* Partage de liens

[!DNL Adobe Experience Manager] les administrateurs peuvent facilement générer et personnaliser ces rapports pour votre mise en oeuvre. Un administrateur peut procéder comme suit pour générer un rapport :

1. Dans l&#39;interface [!DNL Experience Manager], cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Rapports]**.

   ![Page Outils pour parcourir le rapport des ressources](assets/navigation.png)

1. Sur la page [!UICONTROL Rapports sur les ressources], cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.
1. Sur la page **[!UICONTROL Créer un rapport]**, sélectionnez le rapport à créer, puis cliquez sur **[!UICONTROL Suivant]**.

   ![Sélectionner le type de rapport](assets/choose_report.png)

<!-- TBD: How do enable this in CS now? Is it done using some OSGi config now?
   >[!NOTE]
   >
   >Before you can generate an **[!UICONTROL Asset Downloaded]** report, ensure that the Asset Download service is enabled. From the web console (`https://[aem_server]:[port]/system/console/configMgr`), open the **[!UICONTROL Day CQ DAM Event Recorder]** configuration, and select the **[!UICONTROL Asset Downloaded (DOWNLOADED)]** option in Event Types if not already selected.
-->

>[!NOTE]
>
>Par défaut, les fragments de contenu et les partages de liens sont inclus dans le rapport Ressources [!UICONTROL Télécharger]. Sélectionnez l’option appropriée pour créer un rapport de partages de lien ou pour exclure les fragments de contenu du rapport de téléchargement.

>[!NOTE]
>
>Le rapport [!UICONTROL Télécharger] affiche uniquement les détails des ressources téléchargées après sélection individuelle ou téléchargées à l’aide de l’action rapide. Toutefois, il n’inclut pas les détails des ressources se trouvant dans un dossier téléchargé.

1. Configurez les détails du rapport, tels que le titre, la description, la miniature et le chemin du dossier dans le référentiel CRX où le rapport est stocké. Par défaut, le chemin d’accès au dossier est `/content/dam`. Vous pouvez spécifier un autre chemin.

   ![Page pour ajouter des détails sur le rapport](assets/report_configuration.png)

   Sélectionnez la période de votre rapport.

   Vous pouvez choisir de générer le rapport maintenant ou à une date et une heure ultérieures.

   >[!NOTE]
   >
   >Si vous choisissez de planifier le rapport ultérieurement, veillez à spécifier la date et l’heure dans les champs Date et heure. Si vous ne spécifiez aucune valeur, le moteur de création de rapports traite le rapport comme devant être généré immédiatement.

   Les champs de configuration peuvent varier en fonction du type de rapport que vous créez. Par exemple, le rapport **[!UICONTROL Utilisation du disque]** fournit des options pour inclure les rendus de ressources lors du calcul de l’espace disque utilisé par les ressources. Vous pouvez choisir d’inclure ou d’exclure des fichiers dans des sous-dossiers pour le calcul de l’utilisation du disque.

   >[!NOTE]
   >
   >Le rapport **[!UICONTROL Utilisation du disque]** n’inclut pas les champs de période, car il indique uniquement l’utilisation actuelle de l’espace disque.

   ![Page Détails du rapport d&#39;utilisation des disques](assets/disk_usage_configuration.png)

   Lorsque vous créez le rapport **[!UICONTROL Fichiers]**, vous pouvez inclure/exclure des sous-dossiers. Cependant, vous ne pouvez pas inclure les rendus de ressources dans ce rapport.

   ![Page Détails du rapport Fichiers](assets/files_report.png)

   Le rapport **[!UICONTROL Lier le partage]** affiche les URL des ressources partagées avec des utilisateurs externes depuis [!DNL Assets]. <!-- It includes email ids of the user who shared the assets, emails ids of users with which the assets are shared, share date, and expiration date for the link. --> Les colonnes ne sont pas personnalisables.

   Le rapport **[!UICONTROL Partage de liens]** n’inclut pas d’options pour les sous-dossiers et les rendus, car il publie simplement les URL partagées qui apparaissent sous `/var/dam/share`.

   ![Page de détails du rapport Partage de liens](assets/link_share.png)

1. Cliquez sur **[!UICONTROL Suivant]** dans la barre d’outils.

1. Sur la page **[!UICONTROL Configurer les colonnes]**, certaines colonnes sont sélectionnées pour apparaître dans le rapport par défaut. Vous pouvez sélectionner d’autres colonnes. Désélectionnez une colonne sélectionnée pour l’exclure du rapport.

   ![Sélectionner ou désélectionner des colonnes de rapports](assets/configure_columns.png)

   Pour afficher un nom de colonne personnalisé ou un chemin de propriété, configurez les propriétés du fichier binaire sous le noeud `jcr:content` dans CRX. Vous pouvez également l’ajouter dans le sélecteur de chemin de propriété.

   ![Sélectionner ou désélectionner des colonnes de rapports](assets/custom_columns.png)

1. Cliquez sur **[!UICONTROL Créer]** dans la barre d’outils. Un message indique que la génération du rapport a été lancée.
1. Sur la page [!UICONTROL Rapports sur les ressources], l’état de génération du rapport est basé sur l’état actuel de la tâche de rapport, par exemple [!UICONTROL Succès], [!UICONTROL Échec], [!UICONTROL En file d’attente] ou [!UICONTROL Programmé]. Le même état s&#39;affiche dans la boîte de réception des notifications. Pour vue à la page du rapport, cliquez sur le lien du rapport. Vous pouvez également sélectionner le rapport, puis cliquer sur **[!UICONTROL Vue]** dans la barre d’outils.

   ![Un rapport généré](assets/report_page.png)

   Cliquez sur **[!UICONTROL Télécharger]** dans la barre d’outils pour télécharger le rapport au format CSV.

## Ajout de colonnes personnalisées   {#add-custom-columns}

Vous pouvez ajouter des colonnes personnalisées aux rapports suivants pour afficher davantage de données en fonction de vos besoins :

* Charger
* Téléchargement
* Expiration
* Modification
* Publier
* [!DNL Brand Portal] publier
* Fichiers

Pour ajouter des colonnes personnalisées à ces rapports, procédez comme suit :

1. Dans [!DNL Manager interface], cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Rapports]**.
1. Sur la page [!UICONTROL Rapports sur les ressources], cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.

1. Sur la page **[!UICONTROL Créer un rapport]**, sélectionnez le rapport à créer, puis cliquez sur **[!UICONTROL Suivant]**.
1. Configurez les détails du rapport, tels que le titre, la description, la miniature, le chemin d’accès au dossier et la plage de dates, le cas échéant.

1. Pour afficher une colonne personnalisée, spécifiez son nom sous **[!UICONTROL Colonnes personnalisées]**.

   ![Spécifier le nom de la colonne personnalisée du rapport](assets/custom_columns-1.png)

1. Ajoutez le chemin de la propriété sous le nœud `jcr:content` dans CRXDE à l’aide du sélecteur de chemin de propriété. Vous pouvez également saisir le chemin d’accès dans le champ de chemin d’accès à la propriété.

   ![Faites correspondre le chemin d’accès à la propriété des chemins dans jcr:content](assets/property_picker.png)

   Pour ajouter d’autres colonnes personnalisées, cliquez sur **[!UICONTROL Ajouter]** et répétez les étapes 5 et 6.

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
