---
title: Ingestion de contenu dans Cloud Service
description: Découvrez comment utiliser Cloud Acceleration Manager pour ingérer du contenu à partir de votre jeu de migration vers une instance de Cloud Service de destination.
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: 382d1ed93e9545127ebb54641657db365886503d
workflow-type: tm+mt
source-wordcount: '1954'
ht-degree: 40%

---

# Ingestion de contenu dans Cloud Service {#ingesting-content}

## Processus d’ingestion dans l’outil de transfert de contenu {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Ingestion de contenu"
>abstract="L’ingestion fait référence à l’ingestion de contenu à partir du jeu de migration vers l’instance de Cloud Service de destination. L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr" text="Ingestion complémentaire"

Suivez les étapes ci-dessous pour ingérer votre jeu de migration à l’aide de Cloud Acceleration Manager :

>[!NOTE]
>Avez-vous pensé à soumettre un ticket d’assistance pour cette ingestion ? Pour cela et afin d’obtenir de l’aide pour réussir l’ingestion, consultez les [Points importants avant d’utiliser l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=fr#important-considerations).

1. Présentation de Cloud Acceleration Manager. Cliquez sur la carte de votre projet, puis sur la carte Transfert de contenu . Accédez à **Tâches d’ingestion** et cliquez sur **Nouvelle ingestion**

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Consultez la liste de contrôle d’ingestion et assurez-vous que toutes les étapes sont terminées. Ces étapes sont nécessaires pour garantir la réussite de l’ingestion. Passez à la **Suivant** étape uniquement si la liste de contrôle est terminée.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Fournissez les informations requises pour créer une ingestion.

   * Sélectionnez le jeu de migration contenant les données extraites en tant que source.
      * Les jeux de migration expirent après une longue période d’inactivité. Il est donc probable que l’ingestion se produise peu de temps après l’exécution de l’extraction. Consultez [Expiration du jeu de migration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) pour plus d’informations.
   * Sélectionnez l’environnement de destination. C’est dans cet environnement que le contenu du jeu de migration est ingéré. Sélectionnez le niveau. (Création/Publication). Les environnements de développement rapide ne sont pas pris en charge.

   >[!NOTE]
   >Les remarques suivantes s’appliquent à l’ingestion de contenu :
   > Si la source était en Auteur, il est recommandé de l’ingérer dans le niveau Auteur sur la cible. De même, si la source était en Publication, la cible doit également être en Publication.
   > Si le niveau cible est `Author`, l’instance d’auteur est arrêtée pendant la durée de l’ingestion et devient indisponible pour les utilisateurs (par exemple, les auteurs ou toute personne effectuant la maintenance). La raison est de protéger le système et d’empêcher toute modification qui pourrait être perdue ou provoquer un conflit d’ingestion. Assurez-vous que votre équipe est au courant de ce fait. Notez également que l’environnement apparaît en veille pendant l’ingestion par l’auteur.
   > Vous pouvez exécuter l’étape de précopie facultative pour accélérer considérablement la phase d’ingestion. Voir [Ingestion avec AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy) pour plus d’informations.
   > Si l’ingestion avec une précopie est utilisée (pour S3 ou Azure Data Store), il est recommandé d’exécuter l’ingestion d’auteur en premier, seule. Cela permet d’accélérer l’ingestion de publication lorsqu’elle est exécutée ultérieurement.
   > Les intuitions ne prennent pas en charge une destination RDE (Rapid Development Environment) et n’apparaissent pas comme un choix de destination possible, même si l’utilisateur y a accès.

   >[!IMPORTANT]
   > Les remarques importantes suivantes s’appliquent à l’ingestion de contenu :
   > Vous ne pouvez lancer une ingestion vers l’environnement de destination que si vous appartenez au **Administrateurs AEM** groupe sur le service de création du Cloud Service de destination. Si vous ne parvenez pas à démarrer une ingestion, reportez-vous à la section [Impossible de démarrer l’ingestion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) pour plus d’informations.
   > Si le paramètre **Wipe** est activé avant l’ingestion, il supprime l’intégralité du référentiel existant et crée un référentiel dans lequel vous pouvez ingérer du contenu. Ce workflow réinitialise tous les paramètres dont les autorisations sur l’instance Cloud Service cible. Cette réinitialisation est également vraie pour un utilisateur administrateur ajouté à la variable **administrateurs** groupe. Vous devez être lu par le groupe administrateurs pour commencer une ingestion.

1. Cliquez sur **Ingérer**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Vous pouvez ensuite surveiller la phase d’ingestion dans la vue Liste des Tâches d’ingestion. Vous pouvez également utiliser le menu Action de l’ingestion pour consulter le journal consignant la progression de l’ingestion.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Cliquez sur le bouton **(i)** sur la ligne pour plus d’informations sur la tâche d’ingestion. Vous pouvez voir la durée de chaque étape de l’ingestion lorsqu’elle est en cours d’exécution ou terminée en cliquant sur **..**, puis cliquez sur **Afficher les durées**. Les informations de l’extraction sont également affichées pour réaliser ce qui est ingéré.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23b.png)

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

   Also, see [Important Considerations for Using Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html#important-considerations) to learn more.

1. Once the ingestion is complete, the status under **Author ingestion** updates to **FINISHED**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png) -->

## Ingestion complémentaire {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="Ingestion de complément"
>abstract="Utilisez la fonction de complément pour déplacer le contenu modifié depuis l&#39;activité de transfert de contenu précédente. Une fois l’ingestion terminée, recherchez dans les journaux les erreurs/avertissements éventuels. Toute erreur doit être corrigée immédiatement, soit en traitant les problèmes signalés, soit en contactant l’assistance clientèle d’Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html?lang=fr" text="Affichage des journaux"

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un *complément* de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service. Si vous avez utilisé l’étape de précopie pour la première ingestion complète, vous pouvez ignorer la précopie pour les assimilations de complément suivantes (si la taille du jeu de migration de complément est inférieure à 200 Go). La raison est qu’il peut ajouter du temps à l’ensemble du processus.

Une fois le processus d’ingestion terminé, vous devez exécuter une [Extraction de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process), puis utiliser la méthode d’ingestion de complément.

Commencez par créer une tâche d’ingestion et assurez-vous que **Wipe** est désactivé pendant la phase d’ingestion, comme illustré ci-dessous :

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Résolution des problèmes {#troubleshooting}

### Impossible pour CAM de récupérer le jeton de migration {#cam-unable-to-retrieve-the-migration-token}

La récupération automatique du jeton de migration peut échouer pour différentes raisons, y compris la [configuration d’une liste autorisée d’adresses IP via Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) dans l’environnement Cloud Service cible. Dans ce cas de figure, la boîte de dialogue suivante s’affiche lorsque vous tentez de démarrer une ingestion :

![image](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

Récupérez manuellement le jeton de migration en cliquant sur le lien &quot;Obtenir le jeton&quot; dans la boîte de dialogue. Un autre onglet qui affiche le jeton s’ouvre. Vous pouvez ensuite copier le jeton et le coller dans le champ **Entrée du jeton de migration**. À présent, vous devriez être en mesure de commencer l’ingestion.

>[!NOTE]
>
>Le jeton est disponible pour les utilisateurs qui appartiennent au **Administrateurs AEM** groupe sur le service de création du Cloud Service de destination.

### Impossible de démarrer l’ingestion {#unable-to-start-ingestion}

Vous ne pouvez lancer une ingestion vers l’environnement de destination que si vous appartenez au **Administrateurs AEM** groupe sur le service de création du Cloud Service de destination. Si vous n’appartenez pas au groupe d’administrateurs d’AEM, une erreur s’affiche, comme illustré ci-dessous lorsque vous essayez de démarrer une ingestion. Vous pouvez demander à votre administrateur de vous ajouter au groupe local **Administrateurs AEM** ou demander directement le jeton, que vous pouvez ensuite coller dans le champ **Entrée du jeton de migration**.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### Impossible d’atteindre le service de migration {#unable-to-reach-migration-service}

Une fois l’ingestion demandée, un message du type suivant peut être présenté à l’utilisateur : &quot;Le service de migration sur l’environnement de destination est inaccessible. Si tel est le cas, réessayez plus tard ou contactez l’assistance Adobe.&quot;

![image](/help/journey-migration/content-transfer-tool/assets-ctt/error_cannot_reach_migser.png)

Ce message indique que Cloud Acceleration Manager n’a pas pu atteindre le service de migration de l’environnement cible pour démarrer l’ingestion. Cette situation peut se produire pour diverses raisons.

>[!NOTE]
> 
> Le champ « Jeton de migration » s’affiche, car dans certains cas, la récupération de ce jeton est ce qui est en fait interdit. En autorisant sa mise à disposition manuelle, cela peut permettre à l’utilisateur ou l’utilisatrice de démarrer rapidement l’ingestion, sans aide supplémentaire. Si le jeton est fourni et que le message s’affiche toujours, la récupération du jeton n’est pas le problème.

* AEM as a Cloud Service conserve l’état de l’environnement et doit parfois redémarrer le service de migration pour diverses raisons normales. Si ce service redémarre, il ne peut pas être atteint, mais il est disponible à terme.
* Il est possible qu’un autre processus soit en cours d’exécution sur l’instance. Si, par exemple, l&#39;application d&#39;une mise à jour est lancée par Release Orchestration, le système peut être occupé et le service de migration régulièrement indisponible. C’est pourquoi il est vivement recommandé de suspendre les mises à jour lors d’une ingestion, ainsi que la possibilité de corrompre l’instance d’évaluation ou de production.
* Si [LISTE AUTORISÉE IP appliquée](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) Cloud Manager empêche Cloud Acceleration Manager d’accéder au service de migration. Il n’est pas possible d’ajouter une adresse IP pour les assimilations, car celle-ci est dynamique. Actuellement, la seule solution consiste à désactiver la liste autorisée d’adresses IP pendant l’exécution de l’ingestion.
* D’autres raisons peuvent nécessiter un examen. Si l’ingestion continue d’échouer, contactez l’assistance clientèle Adobe.

### Les mises à jour automatiques par l’intermédiaire de l’orchestrateur de versions sont toujours activées.

L’orchestrateur de versions applique les mises à jour automatiquement, ce qui permet de maintenir les environnements à jour. Si la mise à jour est déclenchée lorsqu’une ingestion est effectuée, elle peut entraîner des résultats imprévisibles, y compris la corruption de l’environnement. Une bonne raison de consigner un ticket d’assistance clientèle avant de commencer une ingestion (voir la &quot;Remarque&quot; ci-dessus), de sorte que la désactivation temporaire de Release Orchestration puisse être planifiée.

Si l’ingestion est toujours en cours d’exécution, l’interface utilisateur présente ce message. Vous pouvez choisir de continuer tout de même, en acceptant le risque, en cochant le champ et en appuyant à nouveau sur le bouton.

>[!NOTE]
>
> Le déploiement d’Release Orchestration sur les environnements de développement est en cours. Il est donc conseillé de suspendre les mises à jour de ces environnements.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_ingestion.png)

### Échec de l’ingestion complémentaire En raison d’une violation de contrainte d’unicité

Les conflits entre identifiants de nœud sont une cause courante de l’échec de l’[Ingestion complémentaire](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process). Pour identifier cette erreur, téléchargez le journal d’ingestion à l’aide de l’interface utilisateur de Cloud Acceleration Manager et recherchez une entrée du type suivant :

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: Uniqueness constraint violated property [jcr:uuid] having value a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5e5: /some/path/jcr:content, /some/other/path/jcr:content

Chaque nœud d’AEM doit disposer d’un UUID unique. Cette erreur indique qu’un noeud en cours d’ingestion possède le même uuid que celui qui existe ailleurs à un autre chemin sur l’instance cible.
Cette situation peut se produire si un noeud est déplacé sur la source entre une extraction et une [Extraction de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process).
Cela peut également se produire si un nœud de la cible est déplacé entre une ingestion et une ingestion complémentaire suivante.

Ce conflit doit être résolu manuellement. Une personne qui connait le contenu doit décider lequel des deux nœuds doit être supprimé, sans oublier tout autre contenu qui y fait référence. La solution peut nécessiter que l’extraction complémentaire soit effectuée à nouveau sans le nœud fautif.

### Échec de l’ingestion de complément en raison de l’impossibilité de supprimer le noeud référencé

Une autre cause commune d&#39;une [Ingestion de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) failure est un conflit de version pour un noeud particulier sur l’instance cible. Pour identifier cette erreur, téléchargez le journal d’ingestion à l’aide de l’interface utilisateur de Cloud Acceleration Manager et recherchez une entrée du type suivant :
>java.lang.RuntimeException : org.apache.jackrabbit.oak.api.CommitFailedException : OakIntegrity0001 : impossible de supprimer le noeud référencé : 8a289f4-b904-4bd0-8410-15e41e0976a8

Cela peut se produire si un noeud de la cible est modifié entre une ingestion et une ingestion de complément ultérieure de sorte qu’une nouvelle version ait été créée. Si les &quot;versions d’inclusion&quot; sont activées pour l’ingestion, un conflit peut se produire, dans la mesure où la cible dispose désormais d’une version plus récente référencée par l’historique des versions et d’autres contenus. Le processus d’ingestion ne pourra pas supprimer le noeud de version offensante car il est référencé.

La solution peut nécessiter que l’extraction complémentaire soit effectuée à nouveau sans le nœud fautif. Vous pouvez également créer un petit jeu de migration du noeud incriminé, mais en désactivant l’option &quot;Versions d’inclusion&quot;.

Les bonnes pratiques indiquent que si une ingestion doit être exécutée avec wipe=false et &quot;include versions&quot;=true, il est essentiel que le contenu de la cible soit modifié le moins possible, jusqu’à ce que le parcours de migration soit terminé. Sinon, ces conflits peuvent se produire.


## Prochaines étapes {#whats-next}

Une fois l’ingestion terminée, AEM indexation démarre automatiquement. Voir [Indexation après migration de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/indexing-content.md) pour plus d’informations.

Une fois l’ingestion de contenu dans Cloud Service terminée, vous pouvez afficher les journaux de chaque étape (extraction et ingestion) et rechercher les erreurs. Consultez la section [Affichage des journaux d’un jeu de migration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/viewing-logs.md) pour en savoir plus.

