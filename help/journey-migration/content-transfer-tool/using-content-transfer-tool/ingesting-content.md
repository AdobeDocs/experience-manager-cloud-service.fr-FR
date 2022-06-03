---
title: Ingestion de contenu dans Target
description: Ingestion de contenu dans Target
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: 05765bdaa681502b60fc5a7c943e2265c09764ec
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 40%

---

# Ingestion de contenu dans Target {#ingesting-content}

## Processus d’ingestion dans l’outil de transfert de contenu {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Ingestion de contenu"
>abstract="L’ingestion désigne l’ingestion de contenu à partir du jeu de migration dans l’instance Cloud Service cible. L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=fr#top-up-ingestion-process" text="Ingestion de complément"

Pour ingérer le jeu de migration obtenu à l’aide de l’outil de transfert de contenu, procédez comme suit :
>[!NOTE]
>Vous pouvez exécuter l’étape de précopie facultative pour accélérer considérablement la phase d’ingestion. L’étape de précopie est la plus efficace pour la première extraction et ingestion complètes. Pour plus d’informations, voir [Ingestion avec AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).

1. Accédez à Cloud Acceleration Manager. Cliquez sur la carte de votre projet, puis sur la carte Transfert de contenu . Accédez à **Tâches d’ingestion** et cliquez sur **Nouvelle ingestion**

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Fournissez les informations requises pour créer une ingestion.

   * Sélectionnez le jeu de migration que vous venez d’extraire en tant que source.
   * Sélectionnez l’environnement de destination. C’est là que le contenu du jeu de migration sera ingéré. Sélectionnez le niveau. (Auteur/Publication).

   >[!NOTE]
   >
   >Si la source était Auteur, il est recommandé de l’ingérer dans le niveau Auteur sur la cible. De même, si la source était Publier, la cible doit également être Publier.

   >[!NOTE]
   >
   >Vous pouvez exécuter l’étape de précopie facultative pour accélérer considérablement la phase d’ingestion. Pour plus d’informations, voir [Ingestion avec AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).
   > 
   >Si l’ingestion avec une précopie est utilisée (pour S3 ou Azure Data Store), il est recommandé d’exécuter l’ingestion d’auteur en premier, seule. Cela permet d’accélérer l’ingestion de publication lorsqu’elle est exécutée ultérieurement.

   >[!IMPORTANT]
   >
   >Vous ne pourrez déclencher une ingestion dans l’environnement de destination que si vous appartenez au **Administrateurs AEM** dans l’instance de Cloud Service où vous transférez du contenu. Si vous n’appartenez pas au groupe d’administrateurs AEM, une erreur s’affiche, comme illustré ci-dessous lorsque vous essayez de démarrer une ingestion.
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam21.png)

   >[!IMPORTANT]
   >
   >Si le paramètre **Wipe** est activé avant l’ingestion, il supprime l’intégralité du référentiel existant et crée un nouveau référentiel dans lequel ingérer du contenu. Cela signifie que tous les paramètres sont réinitialisés, y compris les autorisations relatives à l’instance Cloud Service cible. C’est également vrai pour un utilisateur administrateur ajouté au groupe **administrateurs**. Vous devez être de nouveau ajouté au groupe administrateurs pour démarrer une ingestion.

1. Cliquez sur **Ingérer**

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Vous pouvez ensuite surveiller la phase d’ingestion en mode Liste des tâches d’ingestion .

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Une fois l’ingestion terminée, cliquez sur le bouton (i) dans le coin supérieur droit de l’écran pour obtenir plus d’informations sur la tâche d’ingestion.

<!-- Alexandru: hiding temporarily, until it's reviewed 

1. The **Migration Set ingestion** dialog box displays. Content can be ingested to either Author instance or Publish instance at a time. Select the instance to ingest content to. Click on **Ingest** to start the ingestion phase. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >If ingesting with pre-copy is used (for S3 or Azure Data Store), it is recommended to run Author ingestion first alone. This will speed up the Publish ingestion when it is run later. 

   >[!IMPORTANT]
   >When the **Wipe existing content on Cloud instance before ingestion** option is enabled, it deletes the entire existing repository and creates a new repository to ingest content into. This means that it resets all settings including permissions on the target Cloud Service instance. This is also true for an admin user added to the **administrators** group.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-03.png)

   Additionally, click on **Customer Care** to log a ticket, as shown in the figure below. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-04.png)
   
   Also, refer to [Important Considerations for Using Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#important-considerations) to learn more.

1. Once the ingestion is complete, the status under **Author ingestion** updates to **FINISHED**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png) -->

## Ingestion de complément {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup" title="Top Up Ingestion"
>abstract="Utilisez la fonction de complément pour déplacer le contenu modifié depuis l’activité de transfert de contenu précédente. Une fois l’ingestion terminée, recherchez dans les journaux les erreurs/avertissements. Toutes les erreurs doivent être corrigées immédiatement en traitant les problèmes signalés ou en contactant l’assistance clientèle d’Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en" text="Affichage des journaux"

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un *complément* de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service. Si vous avez utilisé l’étape de précopie pour la première ingestion complète, vous pouvez ignorer la précopie pour les assimilations de complément suivantes (si la taille du jeu de migration de complément est inférieure à 200 Go), car cela peut ajouter du temps à l’ensemble du processus.

Une fois le processus d’ingestion terminé, vous devrez exécuter une [Extraction de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) puis utiliser la méthode d’ingestion de complément.

Pour ce faire, créez une tâche d’ingestion et assurez-vous que **Wipe** est désactivé pendant la phase d’ingestion, comme illustré ci-dessous :

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)



## Prochaines étapes {#whats-next}

Une fois que vous avez appris à ingérer du contenu dans Target grâce à l’outil de transfert de contenu, vous pouvez afficher les journaux à la fin de chaque étape (extraction et ingestion) et rechercher les erreurs. Consultez la section [Affichage des journaux d’un jeu de migration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=fr) pour en savoir plus.
