---
title: Ingestion de contenu dans Target (Legacy)
description: Ingestion de contenu dans Target
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 97%

---

# Ingestion de contenu dans Target (Hérité) {#ingesting-content}

## Processus d’ingestion dans l’outil de transfert de contenu {#ingestion-process}

Pour ingérer le jeu de migration obtenu à l’aide de l’outil de transfert de contenu, procédez comme suit :
>[!NOTE]
>Vous pouvez exécuter l’étape de précopie facultative pour accélérer considérablement la phase d’ingestion. Pour plus d’informations, voir [Ingestion avec AzCopy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr#ingesting-azcopy).

1. Sélectionnez un jeu de migration dans la page **Transfert de contenu**, puis cliquez sur **Ingérer** pour démarrer l’ingestion.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. La boîte de dialogue **Ingestion du jeu de migration** (Ingestion du jeu de migration) s’affiche. Le contenu peut être ingéré simultanément sur l’instance d’auteur ou l’instance de publication. Sélectionnez l’instance cible d’ingestion du contenu. Cliquez sur **Ingérer** pour démarrer la phase d’ingestion.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >Si l’ingestion avec une précopie est utilisée (pour S3 ou Azure Data Store), il est recommandé d’exécuter l’ingestion d’auteur en premier, seule. Cela permet d’accélérer l’ingestion de publication lorsqu’elle est exécutée ultérieurement.

   >[!IMPORTANT]
   >Lorsque l’option **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est activée, elle supprime l’intégralité du référentiel existant et crée un référentiel dans lequel intégrer du contenu. Cela signifie que tous les paramètres sont réinitialisés, y compris les autorisations relatives à l’instance Cloud Service cible. C’est également vrai pour un utilisateur administrateur ajouté au groupe **administrateurs**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-03.png)

   De plus, cliquez sur **Assistance clientèle** pour enregistrer un ticket, comme le montre la figure ci-dessous.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-04.png)

   Consultez également [Points importants concernant l’utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=fr#important-considerations) pour en savoir plus.

1. Une fois l’ingestion terminée, le statut du champ **Ingestion Auteur** passe sur **TERMINÉ**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png)

## Ingestion de complément {#top-up-ingestion-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un *complément* de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.

Une fois le processus d’ingestion terminé, vous pouvez utiliser le contenu différentiel à l’aide de la méthode d’ingestion de complément. Suivez les étapes ci-dessous :

1. Accédez à l’assistant **Transfert de contenu** et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’ingestion de complément. Cliquez sur **Ingérer** pour démarrer l’extraction de complément.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest1.png)


1. La boîte de dialogue **Ingestion du jeu de migration** s’affiche.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest2.png)

   >[!IMPORTANT]
   >Vous devez désactiver l’option **Effacer le contenu existant sur l’instance cloud avant l’ingestion** pour empêcher la suppression du contenu existant de l’activité d’ingestion précédente. De plus, cliquez sur **Assistance clientèle** pour enregistrer un ticket, comme le montre la figure précédente.

## Prochaines étapes {#whats-next}

Une fois que vous avez appris à ingérer du contenu dans Target grâce à l’outil de transfert de contenu, vous pouvez afficher les journaux à la fin de chaque étape (extraction et ingestion) et rechercher les erreurs. Consultez la section [Affichage des journaux d’un jeu de migration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=fr) pour en savoir plus.
