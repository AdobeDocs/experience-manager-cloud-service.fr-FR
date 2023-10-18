---
title: Extraction de contenu à partir de la source
description: Découvrez comment extraire du contenu d’une instance Adobe Experience Manager (AEM) source pour le transférer ultérieurement vers une instance AEM Cloud Service.
exl-id: c5c08c4e-d5c3-4a66-873e-96986e094fd3
source-git-commit: 031ddfa2da0fc5ecc92267eae1f9dcaac394573d
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 44%

---

# Extraction de contenu à partir de la source {#extracting-content}

## Processus d’extraction dans l’outil de transfert de contenu {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Extraction de contenu"
>abstract="L’extraction fait référence à l’extraction de contenu de l’instance Adobe Experience Manager (AEM) source dans une zone temporaire appelée jeu de migration. Un jeu de migration est un espace de stockage cloud fourni par Adobe pour stocker temporairement le contenu transféré entre l’instance AEM source et l’instance AEM Cloud Service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html#top-up-extraction-process?lang=fr" text="Extraction de complément"


Pour extraire votre jeu de migration à partir de l’outil de transfert de contenu, procédez comme suit :

>[!NOTE]
>Si Amazon S3, Azure Data Store ou File Data Store sont utilisés comme type de magasin de données, vous pouvez exécuter l’étape de précopie facultative pour augmenter la vitesse de la phase d’extraction. L’étape de précopie est la plus efficace pour la première extraction et ingestion complète. Pour plus d’informations, consultez [Gestion des référentiels de contenu volumineux](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md).

1. Sélectionnez un jeu de migration dans le **Transfert de contenu** assistant et cliquez sur **Extract** pour démarrer l’extraction.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam12.png)

   >[!IMPORTANT]
   >
   >Assurez-vous que la clé Extraction est valide et qu’elle n’est pas proche de son expiration. Si la date d&#39;expiration est proche, vous pouvez renouveler la clé Extraction en sélectionnant le jeu de migration et en cliquant sur Propriétés. Cliquez sur **Renouveler**. Vous accédez alors au Cloud Acceleration Manager où vous pouvez cliquer sur **Copier la clé d’extraction**. Chaque fois que vous cliquez **Copier la clé d’extraction**, une nouvelle clé d’extraction est générée, valable 14 jours à compter de la création.
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam13.png)

1. Cela ouvre la boîte de dialogue Extraction . Cliquez sur **Extract** pour démarrer la phase d&#39;extraction.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam14b.png)

   >[!NOTE]
   >Vous pouvez éventuellement remplacer le conteneur intermédiaire lors de la phase d’extraction. If **Remplacement du conteneur d’évaluation** est désactivé, il peut accélérer les extractions pour les migrations suivantes où les chemins d’accès au contenu ou les paramètres des versions d’inclusion n’ont pas changé. Cependant, si les chemins d’accès au contenu ou les paramètres des versions ont changé, alors l’option **Remplacer le conteneur d’évaluation** doit être activée.

1. Le champ **Extraction** affiche désormais le statut **RUNNING** pour indiquer que l’extraction est en cours d’exécution.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam15.png)

   Cliquez sur **Afficher la progression** pour obtenir une vue granulaire de l’extraction en cours.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam16.png)

   Vous pouvez également surveiller la progression de la phase d’extraction à partir de Cloud Acceleration Manager en consultant la page du transfert de contenu, puis en cliquant sur **..** > **Afficher les détails**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam17.png)

1. Une fois l’extraction terminée, passez en revue les autres colonnes comme **Source** et **Chemins** pour plus d’informations sur le jeu de migration que vous avez renseigné. Cliquer **..** > **Afficher les détails** pour afficher les détails, y compris la durée de chaque étape de l’extraction. Affichez cette boîte de dialogue pendant l’extraction afin de voir comment les étapes progressent.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam18b.png)


## Extraction de complément {#top-up-extraction-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service. Si vous avez utilisé l’étape de précopie pour la première extraction complète, vous pouvez ignorer la précopie pour les extractions de complément suivantes (si la taille du jeu de migration de complément est inférieure à 200 Go). En effet, cela peut rallonger l’ensemble du processus.
>En outre, il est essentiel que la structure de contenu du contenu existant ne soit pas modifiée du moment où l’extraction initiale est prise au moment de l’exécution de l’extraction de complément. Les compléments peuvent pas être exécutés sur du contenu dont la structure a été modifiée depuis l’extraction initiale. Veillez à limiter cette opération pendant le processus de migration.

Une fois le processus d’extraction terminé, vous pouvez transférer le contenu différentiel à l’aide de la méthode d’extraction de complément.

Suivez les étapes ci-dessous :

1. Accédez à l’assistant de **transfert de contenu** et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’extraction de complément. Cliquez sur **Extraire** pour démarrer l’extraction de complément.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam19.png)

1. La boîte de dialogue **Migration Set extraction** (Extraction du jeu de migration) s’affiche. Cliquez sur **Extract**.

   >[!IMPORTANT]
   >Il est préférable de désactiver l’option **Overwrite staging container during extraction** (Remplacer le conteneur d’évaluation pendant l’extraction).
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam20.png)


## Prochaines étapes {#whats-next}

Après avoir appris à extraire du contenu de la source dans l’outil de transfert de contenu, vous êtes prêt à apprendre le processus d’ingestion dans l’outil de transfert de contenu. Voir [Ingestion de contenu dans Target](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) où vous pouvez apprendre à ingérer votre jeu de migration à partir de l’outil de transfert de contenu.
