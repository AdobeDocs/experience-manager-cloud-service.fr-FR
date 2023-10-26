---
title: Indexation après migration de contenu
description: Découvrez comment le processus de migration va indexer le contenu ingéré sur l’instance du Cloud Service de destination.
exl-id: a13d5df4-b351-410a-9336-1b34a8af21b6
source-git-commit: 0109cea1be85e647fb6c04dde4714b162bdc75a5
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 8%

---

# Indexation après migration de contenu {#Indexing-content}

## Indexation {#aem-indexing-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_indexing"
>title="Indexation de contenu"
>abstract="L’Indexation AEM fait référence à l’indexation du contenu sur l’instance de Cloud Service après la migration du contenu vers celle-ci. L’indexation est nécessaire pour prendre en charge la recherche de contenu sur cette instance."

Une fois que Cloud Acceleration Manager a terminé l’ingestion de contenu dans votre instance de Cloud Service, il est prêt à être utilisé. Au départ, le contenu n’est pas indexé, ce qui entraîne probablement un environnement instable dans lequel des problèmes tels que le contenu non indexable et les performances dégradées peuvent être attendus.
Pour des performances optimales sur l&#39;instance, le processus de migration démarre automatiquement l&#39;indexation du contenu. Il n&#39;y a rien à faire, à part surveiller la progression de l&#39;indexation.

> Pour plus d’informations sur le démarrage d’une ingestion, voir [Ingestion de contenu dans Cloud Service](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md).

Les étapes suivantes indiquent le flux général que vous pouvez prévoir dans l’interface utilisateur lors de l’indexation. Certains libellés fournissent un contexte utile dans les info-bulles. Par conséquent, veillez à pointer sur les éléments pour en savoir plus sur l’état d’indexation actuel.

Pour commencer, accédez à Cloud Acceleration Manager. Cliquez sur la carte de votre projet, puis sur la carte Transfert de contenu . Accédez à **Tâches d’ingestion**
et voir les tâches répertoriées.

>[!NOTE]
>Vous pouvez afficher ou télécharger les journaux d’indexation à l’aide des actions de la tâche d’ingestion, à l’aide de la liste déroulante ... Les journaux seront disponibles dans la variable
> section Actions du journal d’indexation, une fois la tâche d’indexation terminée

### En attente

Voici comment la ligne de la tâche d’ingestion apparaîtra lorsque l’ingestion est en cours d’exécution, avant que la tâche d’indexation n’ait été lancée. L’utilisateur ne doit effectuer aucune action. Si l’ingestion échoue pour une raison quelconque, la file d’attente de la tâche d’index sera annulée et ne sera pas lancée.

![image](/help/journey-migration/content-transfer-tool/assets-indexing/pending.png)

### Exécution en cours

Lorsque l’ingestion réussit, la tâche d’indexation est lancée automatiquement. La ligne de tâche d’ingestion affiche une icône de progression pour l’état d’indexation AEM. Vous pouvez ouvrir la boîte de dialogue Durée pour afficher la progression de la tâche.

![image](/help/journey-migration/content-transfer-tool/assets-indexing/running.png)

### Terminé

Lorsque la tâche d’indexation réussit, l’instance est prête à être utilisée à des performances optimales. À ce stade, les journaux des tâches d’indexation seront disponibles pour affichage ou téléchargement afin de les inspecter.

![image](/help/journey-migration/content-transfer-tool/assets-indexing/complete.png)

### Erreurs

L’indexation de l’instance du Cloud Service de destination réussira très probablement. Dans certains cas, il peut échouer et la ligne de tâche d’ingestion apparaîtra comme suit. Dans tous les cas, vous pouvez trouver des détails sur l’échec en pointant la souris sur l’état de l’échec et il peut fournir plus d’informations pour vous aider à déterminer les prochaines étapes. À ce stade, les journaux des tâches d’indexation seront disponibles pour affichage ou téléchargement afin de vous aider à découvrir la source de l’échec. Si l’étape suivante n’est pas claire, contactez le support Adobe avec les détails de l’ingestion et du journal d’indexation.

![image](/help/journey-migration/content-transfer-tool/assets-indexing/failed.png)

## Prochaines étapes {#whats-next}

Une fois que l’instance de service cloud de destination a été indexée, vous pouvez afficher les journaux des tâches d’indexation et rechercher des détails et des erreurs.

La migration est terminée. Le test et la validation de l’instance de service cloud de destination peuvent commencer.
