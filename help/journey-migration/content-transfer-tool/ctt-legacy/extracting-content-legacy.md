---
title: Extraction de contenu à partir de la source  (hérité)
description: Extraction de contenu à partir de la source
hide: true
hidefromtoc: true
exl-id: 9f43356c-ba51-48bc-97f5-f1f5db81e7f3
source-git-commit: 3c8035e4db5729f58bae29136a32a0b9944d6a2f
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 70%

---

# Extraction de contenu à partir de la source  (hérité) {#extracting-content}

## Processus d’extraction dans l’outil de transfert de contenu {#extraction-process}

Pour extraire votre jeu de migration à partir de l’outil de transfert de contenu, procédez comme suit :
>[!NOTE]
>Si Amazon S3 ou Azure Data Store est utilisé comme type d’entrepôt de données, vous pouvez exécuter l’étape facultative de précopie afin d’accélérer considérablement la phase d’extraction. Pour ce faire, vous devez configurer une `azcopy.config` avant d’exécuter l’extraction. Pour plus d’informations, consultez [Gestion des référentiels de contenu volumineux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en).

>[!IMPORTANT]
>Vous devez exécuter l’outil de mappage des utilisateurs avant d’extraire du contenu de la source. Consultez [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html?lang=en) pour plus d’informations.

1. Pour démarrer l’extraction, sélectionnez un jeu de migration dans l’assistant **Transfert de contenu** et cliquez sur **Extraire**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-01.png)

1. La boîte de dialogue **Extraction du jeu de migration** (Extraction du jeu de migration) s’affiche. Cliquez sur **Extraire** pour démarrer la phase d’extraction.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-02.png)

   >[!NOTE]
   >Vous pouvez éventuellement remplacer le conteneur d’évaluation pendant la phase d’extraction.

   >[!IMPORTANT]
   >Si le mappage utilisateur n’a pas été exécuté sur ce jeu de migration avant d’extraire du contenu de la source, un avertissement s’affiche indiquant que l’étape de mappage utilisateur est en attente, comme illustré dans la figure ci-dessous. Sélectionner **Mappage des utilisateurs** pour exécuter l’outil de mappage des utilisateurs.
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/user-mapping-extract.png)

1. Le champ **Extraction** affiche désormais le statut **RUNNING** pour indiquer que l’extraction est en cours d’exécution.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-03.png)

   Une fois l’extraction terminée, l’état du jeu de migration est mis à jour sur **FINISHED** (TERMINÉ) et une icône représentant un nuage *vert uni* s’affiche sous le champ **INFO**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-04.png)

   >[!IMPORTANT]
   >L’interface utilisateur dispose d’une fonction de rechargement automatique qui recharge l’assistant de **transfert de contenu** toutes les 30 secondes.
   >Lorsque la phase d’extraction est lancée, un verrou d’écriture est créé et libéré au-delà de *60 secondes*. Si une extraction est arrêtée, vous devez donc attendre une minute pour que le verrou soit libéré avant de recommencer.

## Extraction de complément {#top-up-extraction-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.
>Veillez également à ce que la structure de contenu du contenu existant ne soit pas modifiée au moment de l’extraction initiale au moment de l’exécution de l’extraction de complément. Les cumuls ne peuvent pas être exécutés sur du contenu dont la structure a été modifiée depuis l’extraction initiale. Veillez à limiter cette opération pendant le processus de migration.

Une fois le processus d’extraction terminé, vous pouvez transférer le contenu différentiel à l’aide de la méthode d’extraction de complément.

Suivez les étapes ci-dessous :

1. Accédez à l’assistant de **transfert de contenu** et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’extraction de complément. Cliquez sur **Extraire** pour démarrer l’extraction de complément.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-05.png)

1. La boîte de dialogue **Migration Set extraction** (Extraction du jeu de migration) s’affiche. Cliquez sur **Extract** (Extraire).

   >[!IMPORTANT]
   >Il est préférable de désactiver l’option **Overwrite staging container during extraction** (Remplacer le conteneur d’évaluation pendant l’extraction).
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-06.png)


## Prochaines étapes {#whats-next}

Une fois que vous avez appris à propos de l’extraction de contenu de la source dans l’outil de transfert de contenu, vous êtes prêt à apprendre le processus d’ingestion dans l’outil de transfert de contenu. Voir [Ingestion de contenu dans la cible](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) pour savoir comment ingérer votre jeu de migration à partir de l’outil de transfert de contenu.
