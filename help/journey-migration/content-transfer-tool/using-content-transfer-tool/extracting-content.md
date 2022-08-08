---
title: Extraction de contenu à partir de la source
description: Extraction de contenu à partir de la source
exl-id: c5c08c4e-d5c3-4a66-873e-96986e094fd3
source-git-commit: 5075482f48bf9aaf2c7386af74c14a50b4469840
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 100%

---

# Extraction de contenu à partir de la source {#extracting-content}

## Processus d’extraction dans l’outil de transfert de contenu {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Extraction de contenu"
>abstract="L’extraction fait référence à l’extraction de contenu de l’instance AEM source dans une zone temporaire appelée jeu de migration. Un jeu de migration est un espace de stockage cloud fourni par Adobe pour stocker temporairement le contenu transféré entre l’instance AEM source et l’instance AEM Cloud Service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=fr#top-up-extraction-process" text="Extraction de complément"


Pour extraire votre jeu de migration à partir de l’outil de transfert de contenu, procédez comme suit :

>[!NOTE]
>Si Amazon S3, Azure Data Store ou File Data Store est utilisé comme type d’entrepôt de données, vous pouvez exécuter l’étape facultative de précopie afin d’accélérer considérablement la phase d’extraction. L’étape de précopie est la plus efficace pour la première occurrence complète d’extraction et d’ingestion. Pour ce faire, vous devez configurer un fichier `azcopy.config` avant d’exécuter l’extraction. Pour plus d’informations, consultez [Gestion des référentiels de contenu volumineux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr).

>[!IMPORTANT]
>Vous devez exécuter l’outil de mappage des utilisateurs avant d’extraire du contenu de la source. Consultez [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html?lang=fr) pour plus d’informations.

1. Pour démarrer l’extraction, sélectionnez un jeu de migration dans l’assistant **Transfert de contenu** et cliquez sur **Extraire**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam12.png)

   >!![IMPORTANT]
   Assurez-vous que la clé d’extraction est valide et n’est pas proche de son expiration. Si sa date d’expiration est proche, vous pouvez renouveler la clé d’extraction en sélectionnant le jeu de migration et en cliquant sur Propriétés. Cliquez sur **Renouveler**. Vous accédez alors au Cloud Acceleration Manager dans lequel vous pouvez cliquer sur **Copier la clé d’extraction**. Chaque fois que vous cliquez sur **Copier la clé d’extraction**, une nouvelle clé d’extraction est générée, valable 14 jours à compter de la création.
   [!image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam13.png)

1. La boîte de dialogue Extraction ’affiche. Cliquez sur **Extraire** pour démarrer la phase d’extraction.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam14.png)

   >[!NOTE]
Vous avez la possibilité de remplacer le conteneur d’évaluation pendant la phase d’extraction. Si l’option **Remplacer le conteneur d’évaluation** est désactivée, cela permet d’accélérer les extractions pour les migrations suivantes où les chemins d’accès au contenu ou les paramètres des versions d’inclusion n’ont pas été modifiés. Cependant, si les chemins d’accès au contenu ou les paramètres des versions ont changé, alors l’option **Remplacer le conteneur d’évaluation** doit être activée.

   >[!IMPORTANT]
Si le mappage des utilisateurs n’a pas été exécuté sur ce jeu de migration avant d’extraire le contenu de la source, un avertissement s’affiche indiquant que l’étape de mappage des utilisateurs est en attente, comme illustré dans la figure ci-dessus. Cliquez sur **Mappage des utilisateurs** pour exécuter l’outil de mappage des utilisateurs.

1. Le champ **Extraction** affiche désormais le statut **RUNNING** pour indiquer que l’extraction est en cours d’exécution.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam15.png)

   Vous pouvez cliquer sur **Afficher la progression** pour obtenir une vue granulaire de l’extraction en cours.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam16.png)

   Vous pouvez également surveiller la progression de la phase d’extraction à partir de Cloud Acceleration Manager en consultant la page du transfert de contenu.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam17.png)

1. Une fois l’extraction terminée, passez en revue les autres colonnes telles que **Source** et **Chemins** pour obtenir plus d’informations sur le jeu de migration que vous avez renseigné, en cliquant sur **...** puis sur **Afficher les détails**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam18.png)


## Extraction de complément {#top-up-extraction-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service. Si vous avez utilisé l’étape de précopie pour la première extraction complète, vous pouvez ignorer la précopie pour les extraction de compléments suivantes (si la taille du jeu de migration de complément est inférieure à 200 Go), car elle est susceptible de rallonger l’ensemble du processus.
En outre, il est essentiel que la structure de contenu du contenu existant ne soit pas modifiée du moment où l’extraction initiale est prise au moment de l’exécution de l’extraction de complément. Les compléments peuvent pas être exécutés sur du contenu dont la structure a été modifiée depuis l’extraction initiale. Veillez à limiter cette opération pendant le processus de migration.

Une fois le processus d’extraction terminé, vous pouvez transférer le contenu différentiel à l’aide de la méthode d’extraction de complément.

Suivez les étapes ci-dessous :

1. Accédez à l’assistant de **transfert de contenu** et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’extraction de complément. Cliquez sur **Extraire** pour démarrer l’extraction de complément.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam19.png)

1. La boîte de dialogue **Migration Set extraction** (Extraction du jeu de migration) s’affiche. Cliquez sur **Extract** (Extraire).

   >[!IMPORTANT]
Il est préférable de désactiver l’option **Remplacer le conteneur d’évaluation pendant l’extraction**.
   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam20.png)


## Prochaines étapes {#whats-next}

Une fois que vous avez appris à extraire du contenu de la source dans l’outil de transfert de contenu, vous êtes prêt à apprendre comment fonctionne le processus d’ingestion dans l’outil de transfert de contenu. Voir [Ingestion de contenu dans la cible](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) pour savoir comment ingérer votre jeu de migration à partir de l’outil de transfert de contenu.
