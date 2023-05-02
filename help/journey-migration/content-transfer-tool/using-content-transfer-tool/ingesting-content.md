---
title: Ingestion de contenu dans Target
description: Ingestion de contenu dans Target
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: 79f5133e681261fa8f7604f1fc9c3fbf5c6a5f59
workflow-type: tm+mt
source-wordcount: '1722'
ht-degree: 86%

---

# Ingestion de contenu dans Target {#ingesting-content}

## Processus d’ingestion dans l’outil de transfert de contenu {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Ingestion de contenu"
>abstract="L’ingestion désigne l’ingestion de contenu à partir du jeu de migration dans l’instance Cloud Service cible. L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html#top-up-ingestion-process" text="Ingestion de complément"

Pour ingérer le jeu de migration obtenu à l’aide de l’outil de transfert de contenu, procédez comme suit :

>[!NOTE]
>Avez-vous pensé à soumettre un ticket d’assistance pour cette ingestion ? Pour cela et afin d’obtenir de l’aide pour réussir l’ingestion, consultez les [Points importants avant d’utiliser l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=fr#important-considerations).

1. Présentation de Cloud Acceleration Manager. Cliquez sur la carte de votre projet, puis sur la carte Transfert de contenu. Accédez aux **Tâches d’ingestion** et cliquez sur **Nouvelle ingestion**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Consultez la liste de contrôle d’ingestion et assurez-vous que toutes les étapes ont été effectuées. Ces étapes constituent un préalable indispensable à la réussite de l’ingestion. Vous devez d’abord terminer la liste de contrôle avant de pouvoir passer à l’étape **suivante**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Fournissez les informations requises pour créer une ingestion.

   * Sélectionnez le jeu de migration contenant les données extraites comme Source.
      * Les jeux de migration expirent après une longue période d’inactivité. Il est donc prévu que l’ingestion se produise relativement peu de temps après l’exécution de l’extraction. Réviser [Expiration du jeu de migration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) pour plus d’informations.
   * Sélectionnez l’environnement de destination. C’est à ce moment que le contenu du jeu de migration sera ingéré. Sélectionnez le niveau. (Auteur/Publication). Les environnements de développement rapide ne sont pas pris en charge.

   >[!NOTE]
   >Les remarques suivantes s’appliquent à l’ingestion de contenu :
   > Si la source était en Auteur, il est recommandé de l’ingérer dans le niveau Auteur sur la cible. De même, si la source était en Publication, la cible doit également être en Publication.
   > Si le niveau cible est `Author`, l’instance de création sera arrêtée pendant la durée de l’ingestion et ne sera pas disponible pour les utilisateurs et utilisatrices (par exemple, les auteurs ou autrices ou toute personne effectuant la maintenance, etc.). Cela permet de protéger le système et d’empêcher toute modification qui pourrait être perdue ou entraîner un conflit d’ingestion. Assurez-vous d’en informer votre équipe. Notez également que l’environnement apparaîtra en veille pendant l’ingestion de l’instance de création.
   > Vous pouvez exécuter l’étape de précopie facultative pour accélérer considérablement la phase d’ingestion. Pour plus d’informations, voir [Ingestion avec AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).
   > Si l’ingestion avec une précopie est utilisée (pour S3 ou Azure Data Store), il est recommandé d’exécuter l’ingestion d’auteur en premier, seule. Cela permet d’accélérer l’ingestion de publication lorsqu’elle est exécutée ultérieurement.
   > Les intuitions ne prennent pas en charge une destination RDE (Rapid Development Environment). Ils n’apparaîtront pas comme choix de destination possible, même si l’utilisateur y a accès.

   >[!IMPORTANT]
   > Les remarques importantes suivantes s’appliquent à l’ingestion de contenu :
   > Vous ne pourrez lancer une ingestion dans l’environnement de destination que si vous appartenez à l’environnement local. **Administrateurs AEM** groupe sur le service de création du Cloud Service de destination. Si vous ne parvenez pas à démarrer une ingestion, reportez-vous à la section [Impossible de démarrer l’ingestion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) pour plus d’informations.
   > Si le paramètre **Effacer** est activé avant l’ingestion, il supprime l’intégralité du référentiel existant et crée un nouveau référentiel dans lequel ingérer du contenu. Cela signifie que tous les paramètres sont réinitialisés, y compris les autorisations relatives à l’instance Cloud Service cible. C’est également vrai pour un utilisateur administrateur ajouté au groupe **administrateurs**. Vous devez être de nouveau ajouté au groupe d’administrateurs pour démarrer une ingestion.

1. Cliquez sur **Ingérer**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Vous pouvez ensuite surveiller la phase d’ingestion dans la vue Liste des Tâches d’ingestion. Vous pouvez également utiliser le menu Action de l’ingestion pour consulter le journal consignant la progression de l’ingestion.

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
   
   Also, refer to [Important Considerations for Using Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html#important-considerations) to learn more.

1. Once the ingestion is complete, the status under **Author ingestion** updates to **FINISHED**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png) -->

## Ingestion de complément {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="Ingestion de complément"
>abstract="Utilisez la fonction de complément pour déplacer le contenu modifié depuis l’activité de transfert de contenu précédente. Une fois l’ingestion terminée, recherchez dans les journaux les erreurs/avertissements éventuels. Toute erreur doit être corrigée immédiatement, soit en traitant les problèmes signalés, soit en contactant l’assistance clientèle d’Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html" text="Affichage des journaux"

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

Vous ne pourrez lancer une ingestion dans l’environnement de destination que si vous appartenez à l’environnement local. **Administrateurs AEM** groupe sur le service de création du Cloud Service de destination. Si vous n’appartenez pas au groupe d’administrateurs AEM, une erreur s’affiche lorsque vous essayez de démarrer une ingestion, comme illustré ci-dessous. Vous pouvez demander à votre administrateur de vous ajouter au groupe local **Administrateurs AEM** ou demander directement le jeton, que vous pouvez ensuite coller dans le champ **Entrée du jeton de migration**.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### Impossible d’atteindre le service de migration {#unable-to-reach-migration-service}

Une fois l’ingestion demandée, un message comme celui-ci peut être présenté à l’utilisateur ou l’utilisatrice : « Le service de migration sur l’environnement de destination est actuellement inatteignable. Veuillez réessayer ultérieurement ou contacter l’assistance Adobe. »

![image](/help/journey-migration/content-transfer-tool/assets-ctt/error_cannot_reach_migser.png)

Cela indique que Cloud Acceleration Manager n’a pas pu atteindre le service de migration de l’environnement cible pour démarrer l’ingestion. Cela peut se produire pour plusieurs raisons.

>[!NOTE]
> 
> Le champ « Jeton de migration » s’affiche, car dans certains cas, la récupération de ce jeton est ce qui est en fait interdit. En autorisant sa mise à disposition manuelle, cela peut permettre à l’utilisateur ou l’utilisatrice de démarrer rapidement l’ingestion, sans aide supplémentaire. Si le jeton est fourni et que le message s’affiche toujours, ce n’est pas la récupération du jeton qui a posé problème.

* AEM as a Cloud Service conserve l’état de l’environnement et peut parfois devoir redémarrer le service de migration pour plusieurs raisons normales. Si ce service redémarre, il ne peut pas être atteint, mais sera rapidement disponible.
* Il est possible qu’un autre processus soit en cours d’exécution sur l’instance. Si, par exemple, l’application d’une mise à jour est lancée par Release Orchestration, le système peut être occupé et le service de migration régulièrement indisponible. C’est pour cette raison, ainsi qu’en raison du risque de corruption de l’instance d’évaluation ou de production, il est fortement recommandé de suspendre les mises à jour lors d’une ingestion.
* Si une [liste autorisée d’adresses IP a été appliquée](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) via Cloud Manager, cela empêche Cloud Acceleration Manager d’accéder au service de migration. Une adresse IP ne peut pas être ajoutée pour les ingestions, car leur adresse est très dynamique. Actuellement, la seule solution consiste à désactiver la liste autorisée d’adresses IP pendant l’exécution de l’ingestion.
* D’autres raisons peuvent nécessiter un examen. Si l’ingestion continue d’échouer, veuillez contacter l’assistance clientèle Adobe.

### Les mises à jour automatiques par l’intermédiaire de l’orchestrateur de versions sont toujours activées.

L’orchestrateur de versions applique les mises à jour automatiquement, ce qui permet de maintenir les environnements à jour. Si la mise à jour est déclenchée lors de l’ingestion, elle peut entraîner des résultats imprévisibles, y compris la corruption de l’environnement. C’est l’une des raisons pour lesquelles un ticket d’assistance doit être soumis avant de commencer une ingestion (voir la « Remarque » ci-dessus), de sorte que la désactivation temporaire de l’orchestrateur de versions puisse être planifiée.

Si l’orchestrateur de versions est toujours en cours d’exécution au moment où une ingestion commence, l’interface utilisateur affichera ce message. Vous pouvez choisir de continuer tout de même, en acceptant le risque, en cochant le champ et en appuyant à nouveau sur le bouton.

>[!NOTE]
>
> Le déploiement d’Release Orchestration sur les environnements de développement est en cours. Il est donc conseillé de suspendre les mises à jour de ces environnements.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_ingestion.png)

### Échec de l’ingestion complémentaire

Les conflits entre identifiants de nœud sont une cause courante de l’échec de l’[Ingestion complémentaire](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process). Pour identifier cette erreur, téléchargez le journal d’ingestion à l’aide de l’interface utilisateur de Cloud Acceleration Manager et recherchez une entrée du type suivant :

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: Uniqueness constraint violated property [jcr:uuid] having value a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5e5: /some/path/jcr:content, /some/other/path/jcr:content

Chaque nœud d’AEM doit disposer d’un UUID unique. Cette erreur indique qu’un nœud en cours d’ingestion présente un uuid qui existe déjà au niveau d’un autre chemin d’accès sur l’instance cible.
Cela peut se produire si un nœud est déplacé sur la source entre une extraction et une [extraction complémentaire](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) suivante.
Cela peut également se produire si un nœud de la cible est déplacé entre une ingestion et une ingestion complémentaire suivante.

Ce conflit doit être résolu manuellement. Une personne qui connait le contenu doit décider lequel des deux nœuds doit être supprimé, sans oublier tout autre contenu qui y fait référence. La solution peut nécessiter que l’extraction complémentaire soit effectuée à nouveau sans le nœud fautif.

## Prochaines étapes {#whats-next}

Une fois que vous avez terminé l’ingestion de contenu dans Target, vous pouvez consulter les journaux de chaque étape (extraction et ingestion) et rechercher les erreurs. Consultez la section [Affichage des journaux d’un jeu de migration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html) pour en savoir plus.
