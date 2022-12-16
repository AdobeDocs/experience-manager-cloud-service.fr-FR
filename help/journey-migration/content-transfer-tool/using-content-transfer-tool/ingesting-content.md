---
title: Ingestion de contenu dans Target
description: Ingestion de contenu dans Target
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: 20e54ff697c0dc7ab9faa504d9f9e0e6ee585464
workflow-type: tm+mt
source-wordcount: '1181'
ht-degree: 74%

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
>Vous pouvez exécuter l’étape de précopie facultative pour accélérer considérablement la phase d’ingestion. L’étape de précopie est la plus efficace pour la première occurrence complète d’extraction et d’ingestion. Pour plus d’informations, consultez la section [Ingestion avec AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).

>[!NOTE]
>Vous souvenez-vous d’enregistrer un ticket d’assistance pour cette ingestion ? Voir [Points importants avant l’utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html#important-considerations) pour cela et pour d’autres considérations afin de contribuer à la réussite de l’ingestion.

1. Présentation de Cloud Acceleration Manager. Cliquez sur la carte de votre projet, puis sur la carte Transfert de contenu. Accédez aux **Tâches d’ingestion** et cliquez sur **Nouvelle ingestion**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)


1. Consultez la liste de contrôle d’ingestion et assurez-vous que toutes les étapes ont été effectuées. Il s’agit des étapes nécessaires pour garantir la réussite de l’ingestion. Vous pourrez accéder à la variable **Suivant** étape uniquement si la liste de contrôle est terminée.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Fournissez les informations requises pour créer une ingestion.

   * Sélectionnez le jeu de migration que vous venez d’extraire en tant que source.
   * Sélectionnez l’environnement de destination. C’est à ce moment que le contenu du jeu de migration sera ingéré. Sélectionnez le niveau. (Auteur/Publication).

   >[!NOTE]
   >
   >Si la source était en Auteur, il est recommandé de l’ingérer dans le niveau Auteur sur la cible. De même, si la source était en Publication, la cible doit également être en Publication.

   >[!NOTE]
   >
   >Si le niveau cible est `Author`, l’instance d’auteur sera arrêtée pendant la durée de l’ingestion et ne sera pas disponible pour les utilisateurs (par exemple, les auteurs ou toute personne effectuant la maintenance, etc.). Il s’agit de protéger le système et d’empêcher toute modification qui pourrait être perdue ou provoquer un conflit d’ingestion. Assurez-vous que votre équipe est au courant de ce fait. Notez également que l’environnement apparaîtra en veille pendant l’ingestion par l’auteur.

   >[!NOTE]
   >
   >Vous pouvez exécuter l’étape de précopie facultative pour accélérer considérablement la phase d’ingestion. Pour plus d’informations, voir [Ingestion avec AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).
   > 
   >Si l’ingestion avec une précopie est utilisée (pour S3 ou Azure Data Store), il est recommandé d’exécuter l’ingestion d’auteur en premier, seule. Cela permet d’accélérer l’ingestion de publication lorsqu’elle est exécutée ultérieurement.

   >[!IMPORTANT]
   >
   >Vous ne pourrez déclencher une ingestion dans l’environnement de destination que si vous appartenez au groupe local **Administrateurs AEM** du service de création Cloud Service de destination. Si vous ne parvenez pas à démarrer une ingestion, reportez-vous à la section [Impossible de démarrer l’ingestion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) pour plus d’informations.

   >[!IMPORTANT]
   >
   >Si le paramètre **Effacer** est activé avant l’ingestion, il supprime l’intégralité du référentiel existant et crée un nouveau référentiel dans lequel ingérer du contenu. Cela signifie que tous les paramètres sont réinitialisés, y compris les autorisations relatives à l’instance Cloud Service cible. C’est également vrai pour un utilisateur administrateur ajouté au groupe **administrateurs**. Vous devez être de nouveau ajouté au groupe d’administrateurs pour démarrer une ingestion.

1. Cliquez sur **Ingérer**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Vous pouvez ensuite surveiller la phase d’ingestion en mode liste des Tâches d’ingestion. et utilisez le menu d’action de l’ingestion pour afficher le journal au fur et à mesure de l’ingestion.

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
>id="aemcloud_ctt_ingestion_topup"
>title="Ingestion de complément"
>abstract="Utilisez la fonction de complément pour déplacer le contenu modifié depuis l’activité de transfert de contenu précédente. Une fois l’ingestion terminée, recherchez dans les journaux les erreurs/avertissements éventuels. Toute erreur doit être corrigée immédiatement, soit en traitant les problèmes signalés, soit en contactant l’assistance clientèle d’Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html?lang=fr" text="Affichage des journaux"

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un *complément* de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service. Si vous avez utilisé l’étape de précopie pour la première ingestion complète, vous pouvez ignorer la précopie pour les ingestions de compléments suivantes (si la taille du jeu de migration de complément est inférieure à 200 Go), car elle est susceptible de rallonger l’ensemble du processus.

Une fois le processus d’ingestion terminé, vous devrez exécuter une [Extraction de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) pour ingérer le contenu manquant puis utiliser la méthode d’ingestion de complément.

Pour ce faire, créez une tâche d’ingestion et assurez-vous que l’option **Effacer** est désactivé pendant la phase d’ingestion, comme illustré ci-dessous :

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Résolution des problèmes {#troubleshooting}

### Impossible pour CAM de récupérer le jeton de migration {#cam-unable-to-retrieve-the-migration-token}

La récupération automatique du jeton de migration peut échouer pour différentes raisons, y compris la [configuration d’une liste autorisée d’adresses IP via Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) dans l’environnement Cloud Service cible. Dans ce cas de figure, la boîte de dialogue suivante s’affiche lorsque vous tentez de démarrer une ingestion :

![image](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

Vous devez récupérer manuellement le jeton de migration en cliquant sur le lien « Obtenir le jeton » dans la boîte de dialogue. Cette action a pour effet d’ouvrir un autre onglet affichant le jeton. Vous pouvez ensuite copier le jeton et le coller dans le champ **Entrée du jeton de migration**. À présent, vous devriez être en mesure de commencer l’ingestion.

>[!NOTE]
>
>Le jeton sera disponible pour les utilisateurs qui appartiennent au groupe local **Administrateurs AEM** sur le service de création Cloud Service de destination.

### Impossible de démarrer l’ingestion {#unable-to-start-ingestion}

Vous pourrez déclencher une ingestion vers un environnement de destination seulement si vous appartenez au groupe local **Administrateurs AEM** sur le service de création Cloud Service de destination. Si vous n’appartenez pas au groupe d’administrateurs AEM, une erreur s’affiche lorsque vous essayez de démarrer une ingestion, comme illustré ci-dessous. Vous pouvez demander à votre administrateur de vous ajouter au groupe local **Administrateurs AEM** ou demander directement le jeton, que vous pouvez ensuite coller dans le champ **Entrée du jeton de migration**.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### Les mises à jour automatiques par l’intermédiaire de la fonction Release Explorer sont toujours activées.

L&#39;application automatique des mises à jour permet de tenir automatiquement les environnements à jour. Si la mise à jour est déclenchée lors d’une ingestion, elle peut entraîner des résultats imprévisibles, y compris la corruption de l’environnement. C’est l’une des raisons pour lesquelles un ticket d’assistance doit être consigné avant de commencer une ingestion (voir la &quot;Remarque&quot; ci-dessus), de sorte que la désactivation temporaire de Release Orchestration puisse être planifiée.

Si l’exécution de Release Orchestration est toujours en cours de démarrage, l’interface utilisateur affiche ce message d’erreur. Vous pouvez choisir de continuer de toute façon, en acceptant le risque, en cochant le champ et en appuyant de nouveau sur le bouton.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_ingestion.png)

## Prochaines étapes {#whats-next}

Une fois que vous avez terminé l’ingestion de contenu dans Target, vous pouvez afficher les journaux de chaque étape (extraction et ingestion) et rechercher les erreurs. Consultez la section [Affichage des journaux d’un jeu de migration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=fr) pour en savoir plus.