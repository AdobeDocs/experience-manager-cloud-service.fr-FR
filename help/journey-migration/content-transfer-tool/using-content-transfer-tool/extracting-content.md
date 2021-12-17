---
title: Extraction de contenu de la source
description: Extraction de contenu de la source
source-git-commit: bcbf4e4ba1330bef9f2c8c473419903e40ac0e58
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 64%

---


# Extraction de contenu de la source {#extracting-content}

## Processus d’extraction dans l’outil de transfert de contenu {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Extraction de contenu"
>abstract="L’extraction fait référence à l’extraction de contenu de l’instance AEM source dans une zone temporaire appelée jeu de migration. Un jeu de migration est un espace de stockage cloud fourni par Adobe pour stocker temporairement le contenu transféré entre l’instance AEM source et l’instance AEM Cloud Service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=fr#top-up-extraction-process" text="Extraction de complément"


Pour extraire votre jeu de migration à partir de l’outil de transfert de contenu, procédez comme suit :
>[!NOTE]
>Si Amazon S3 ou Azure Data Store est utilisé comme type d’entrepôt de données, vous pouvez exécuter l’étape facultative de précopie afin d’accélérer considérablement la phase d’extraction. Pour ce faire, vous devez configurer un fichier `azcopy.config` avant d’exécuter l’extraction. Voir [Gestion des référentiels de contenu volumineux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr) pour plus d’informations.

>[!IMPORTANT]
>Vous devez exécuter l’outil de mappage des utilisateurs avant d’extraire du contenu de la source. Voir [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html?lang=en) pour plus d’informations.

1. Sélectionner un jeu de migration à partir de **Transfert de contenu** assistant et cliquez sur **Extract** pour démarrer l’extraction.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-01.png)

1. La boîte de dialogue **Migration Set extraction** (Extraction du jeu de migration) s’affiche. Cliquez sur **Extract** pour démarrer la phase d’extraction.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-02.png)

   >[!NOTE]
   >Vous avez la possibilité de remplacer le conteneur d’évaluation pendant la phase d’extraction.

   >[!IMPORTANT]
   >Si le mappage utilisateur n’a pas été exécuté sur ce jeu de migration avant d’extraire le contenu de la source, un avertissement s’affiche indiquant que l’étape de mappage utilisateur est en attente, comme illustré dans la figure ci-dessous. Cliquez sur **Mappage des utilisateurs** pour exécuter l’outil de mappage des utilisateurs.
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/user-mapping-extract.png)

1. Le **Extraction** affiche maintenant le champ **EN COURS** état pour indiquer que l&#39;extraction est en cours.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-03.png)

   Une fois l’extraction terminée, l’état du jeu de migration est mis à jour sur **FINISHED** (TERMINÉ) et une icône représentant un nuage *vert uni* s’affiche sous le champ **INFO**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-04.png)

   >[!IMPORTANT]
   >L’interface utilisateur dispose d’une fonction de rechargement automatique qui recharge la fonction **Transfert de contenu** toutes les 30 secondes.
   >Lorsque la phase d’extraction est lancée, un verrou d’écriture est créé et libéré au-delà de *60 secondes*. Si une extraction est arrêtée, vous devez donc attendre une minute pour que le verrou soit libéré avant de recommencer.

## Extraction de complément {#top-up-extraction-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.
>En outre, il est essentiel que la structure de contenu du contenu existant ne soit pas modifiée du moment où l’extraction initiale est prise au moment de l’exécution de l’extraction de complément. Les compléments peuvent pas être exécutés sur du contenu dont la structure a été modifiée depuis l’extraction initiale. Veillez à limiter cette opération pendant le processus de migration.

Une fois le processus d’extraction terminé, vous pouvez transférer le contenu différentiel à l’aide de la méthode d’extraction de complément.

Suivez les étapes ci-dessous :

1. Accédez au **Transfert de contenu** et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l&#39;extraction de complément. Cliquez sur **Extraire** pour démarrer l’extraction de complément.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-05.png)

1. La boîte de dialogue **Migration Set extraction** (Extraction du jeu de migration) s’affiche. Cliquez sur **Extract**.

   >[!IMPORTANT]
   >Il est préférable de désactiver l’option **Overwrite staging container during extraction** (Remplacer le conteneur d’évaluation pendant l’extraction).
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-06.png)


## Et après ? {#whats-next}

Une fois que vous avez appris à extraire du contenu de la source dans l’outil de transfert de contenu, vous êtes prêt à apprendre le processus d’ingestion dans l’outil de transfert de contenu. Voir [Ingestion de contenu dans Target](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) pour savoir comment ingérer votre jeu de migration à partir de l’outil de transfert de contenu.
