---
title: Extraction de contenu à partir de la source
description: Découvrez comment extraire du contenu d’une instance source Adobe Experience Manager (AEM) pour le transférer ultérieurement vers une instance Cloud Service AEM.
exl-id: c5c08c4e-d5c3-4a66-873e-96986e094fd3
feature: Migration
role: Admin
source-git-commit: d568619bd8ebb42a6914211401df680352c921ab
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 39%

---

# Extraction de contenu à partir de la source {#extracting-content}

## Processus d’extraction dans l’outil de transfert de contenu {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Extraction de contenu"
>abstract="L’extraction fait référence à l’extraction de contenu de l’instance Adobe Experience Manager (AEM) source dans une zone temporaire appelée ensemble de migration. Un ensemble de migration est un espace de stockage cloud fourni par Adobe pour stocker temporairement le contenu transféré entre l’instance AEM source et l’instance AEM Cloud Service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=fr#top-up-extraction-process" text="Extraction de complément"


Pour extraire votre ensemble de migration à partir de l’outil de transfert de contenu, procédez comme suit :

>[!NOTE]
>Si Amazon S3, Azure Data Store ou File Data Store est utilisé comme type d’entrepôt de données, vous pouvez exécuter l’étape facultative de précopie pour augmenter la vitesse de la phase d’extraction. L’étape de précopie est la plus efficace pour la première extraction et ingestion complète. Pour plus d’informations, consultez [Gestion des référentiels de contenu volumineux](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md).

1. Sélectionnez un jeu de migration dans l’assistant **Transfert de contenu** et cliquez sur **Extraire** pour démarrer l’extraction.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam12.png)

   >[!TIP]
   >Une ingestion peut désormais être planifiée pour démarrer automatiquement immédiatement après le succès d’une extraction. Voir [ Ingestion de contenu dans Target](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) pour plus d’informations.

   >[!IMPORTANT]
   >
   >Assurez-vous que la clé d’extraction est valide et n’est pas proche de son expiration. Si sa date d’expiration est proche, vous pouvez renouveler la clé d’extraction en sélectionnant le jeu de migration et en cliquant sur Propriétés. Cliquez sur **Renouveler**. Vous accédez alors au Cloud Acceleration Manager dans lequel vous pouvez cliquer sur **Copier la clé d’extraction**. Chaque fois que vous cliquez sur **Copier la clé d’extraction**, une nouvelle clé d’extraction est générée, valable 14 jours à compter de la création.
   >![Image](/help/journey-migration/content-transfer-tool/assets-ctt/migrationSetDetails.png)

1. La boîte de dialogue Extraction s’affiche. Cliquez sur **Extraire** pour démarrer la phase d’extraction.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/migrationSetExtraction.png)

   >[!NOTE]
   >Vous pouvez éventuellement remplacer le conteneur d’évaluation pendant la phase d’extraction. Si l’option **Remplacer le conteneur d’évaluation** est désactivée, elle peut accélérer les extractions pour les migrations ultérieures où les chemins d’accès au contenu ou les paramètres des versions n’ont pas changé. Cependant, si les chemins d’accès au contenu ou les paramètres des versions ont changé, alors l’option **Remplacer le conteneur d’évaluation** doit être activée.

1. Le champ **Extraction** affiche désormais le statut **RUNNING** pour indiquer que l’extraction est en cours d’exécution.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam15.png)

   Vous pouvez cliquer sur **Afficher la progression** pour obtenir une vue granulaire de l’extraction en cours.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/viewProgress.png)

   Vous pouvez également surveiller la progression de la phase d’extraction à partir de Cloud Acceleration Manager en consultant la page Transfert de contenu et consulter celle-ci en détail en cliquant sur **...** > **Afficher les détails**.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam17.png)

1. Une fois l’extraction terminée, passez en revue les autres colonnes telles que **Source** et **Chemins** pour plus d’informations sur le jeu de migration que vous avez renseigné. Cliquez sur **...** > **Afficher les détails** pour afficher les détails, y compris la durée de chaque étape de l’extraction. Affichez cette boîte de dialogue pendant l’extraction afin de voir comment les étapes progressent.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam18b.png)


## Extraction de complément {#top-up-extraction-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service. Si vous avez utilisé l’étape de précopie pour la première extraction complète, vous pouvez ignorer la précopie pour les extractions de compléments suivantes (si la taille du jeu de migration de complément est inférieure à 200 Go). En effet, cela peut rallonger l’ensemble du processus.
>&#x200B;>En outre, il est essentiel que la structure de contenu du contenu existant ne soit pas modifiée du moment où l’extraction initiale est prise au moment de l’exécution de l’extraction de complément. Les compléments peuvent pas être exécutés sur du contenu dont la structure a été modifiée depuis l’extraction initiale. Veillez à limiter cette opération pendant le processus de migration.

>[!NOTE]
>Une fois que les chemins d’accès au contenu ont été migrés vers le conteneur d’évaluation, ces chemins ou les sous-chemins qu’ils contiennent ne peuvent pas être supprimés ou exclus des migrations complémentaires suivantes.
>&#x200B;>Exemple : migration initiale : content/dam/weRetail,
>&#x200B;>Prochaine tentative d’exclusion du complément : content/dam/weRetail/ab.
>&#x200B;>Dans ce scénario, l’exclusion de content/dam/weRetail/ab n’est pas possible, car les données ont déjà été migrées vers le conteneur d’évaluation.

Une fois le processus d’extraction terminé, vous pouvez transférer le contenu différentiel à l’aide de la méthode d’extraction de complément.

Suivez les étapes ci-dessous :

1. Accédez à l’assistant de **transfert de contenu** et sélectionnez l’ensemble de migration pour lequel vous souhaitez effectuer l’extraction de complément. Cliquez sur **Extraire** pour démarrer l’extraction de complément.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam19.png)

1. La boîte de dialogue **Extraction de l’ensemble de migration** s’ouvre. Cliquez sur **Extraire**.

   >[!IMPORTANT]
   >Il est préférable de désactiver l’option **Overwrite staging container during extraction** (Remplacer le conteneur d’évaluation pendant l’extraction).
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/overwriteStagingContainer.png)


## Prochaines étapes {#whats-next}

Maintenant que vous avez appris à extraire du contenu de Source dans l’outil de transfert de contenu, vous êtes prêt à apprendre comment fonctionne le processus d’ingestion dans l’outil de transfert de contenu. Voir [Ingestion de contenu dans Target](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) où vous pouvez apprendre à ingérer votre jeu de migration à partir de l’outil de transfert de contenu.
