---
title: Ingestion de contenu dans Target dans l’outil de transfert de contenu
description: Ingestion de contenu dans Target dans l’outil de transfert de contenu
source-git-commit: d638fe0f4711bd152bd9c4be99a68662f12072e6
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 63%

---


# Ingestion de contenu dans Target dans l’outil de transfert de contenu {#ingesting-content}

## Processus d’ingestion dans l’outil de transfert de contenu {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Ingestion de contenu"
>abstract="L’ingestion désigne l’ingestion de contenu à partir du jeu de migration dans l’instance Cloud Service cible. L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-ingestion-process" text="Ingestion de complément"

Pour ingérer le jeu de migration obtenu à l’aide de l’outil de transfert de contenu, procédez comme suit :
>[!NOTE]
>Si Amazon S3 ou Azure Data Store est utilisé comme type d’entrepôt de données, vous pouvez exécuter l’étape facultative de précopie afin d’accélérer considérablement la phase d’ingestion. Pour plus d’informations, voir [Ingestion avec AzCopy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#ingesting-azcopy) .

1. Sélectionnez un jeu de migration à partir de la page **Content Transfer** et cliquez sur **Ingest** pour commencer l’ingestion.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-01.png)

1. La boîte de dialogue **Migration Set ingestion** (Ingestion du jeu de migration) s’affiche. Le contenu peut être ingéré simultanément sur l’instance d’auteur ou l’instance de publication. Sélectionnez l’instance à laquelle ingérer le contenu. Cliquez sur **Ingest** pour démarrer la phase d’ingestion.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >Si l’ingestion avec une précopie est utilisée (pour S3 ou Azure Data Store), il est recommandé d’exécuter l’ingestion par l’auteur en premier seul. Cela permettra d’accélérer l’ingestion de publication lorsqu’elle est exécutée ultérieurement.

   >[!IMPORTANT]
   >Lorsque l’option **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est activée, elle supprime l’intégralité du référentiel existant et crée un référentiel dans lequel intégrer du contenu. Cela signifie que tous les paramètres sont réinitialisés, y compris les autorisations relatives à l’instance Cloud Service cible. C’est également vrai pour un utilisateur administrateur ajouté au groupe **administrateurs**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-03.png)

   Cliquez également sur **Assistance clientèle** pour enregistrer un ticket, comme illustré dans la figure ci-dessous.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-04.png)

   Consultez également [Points importants concernant l’utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#important-considerations) pour en savoir plus.

1. Une fois l’ingestion terminée, l’état sous **Ingestion de l’auteur** est mis à jour vers **FINISHED**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/15-ingestion-complete.png)

## Ingestion de complément {#top-up-ingestion-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un *complément* de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.

Une fois le processus d’ingestion terminé, vous pouvez utiliser le contenu différentiel à l’aide de la méthode d’ingestion de complément. Suivez les étapes ci-dessous :

1. Accédez à la page *Overview* et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’ingestion de complément. Cliquez sur **Ingest** pour démarrer l’extraction de complément. La boîte de dialogue **Migration Set ingestion** (Ingestion du jeu de migration) s’affiche.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-02.png)

   >[!IMPORTANT]
   >Vous devez désactiver l’option **Effacer le contenu existant sur l’instance cloud avant l’ingestion** pour empêcher la suppression du contenu existant de l’activité d’ingestion précédente. De plus, cliquez sur **Assistance clientèle** pour enregistrer un ticket, comme le montre la figure précédente.
