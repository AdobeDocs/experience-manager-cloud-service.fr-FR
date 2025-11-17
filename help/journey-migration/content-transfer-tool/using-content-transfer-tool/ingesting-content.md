---
title: Ingestion de contenu dans Cloud Service
description: Découvrez comment utiliser Cloud Acceleration Manager pour ingérer du contenu à partir de votre jeu de migration vers une instance Cloud Service de destination.
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
feature: Migration
role: Admin
source-git-commit: 7c0703d746601742a28c3c98f35e69de70f25e05
workflow-type: tm+mt
source-wordcount: '3647'
ht-degree: 34%

---

# Ingestion de contenu dans Cloud Service {#ingesting-content}

## Processus d’ingestion dans Cloud Acceleration Manager {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Ingestion de contenu"
>abstract="L’ingestion désigne l’ingestion de contenu à partir de l’ensemble de migration dans l’instance Cloud Service cible. L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content#top-up-extraction-process" text="Extraction de complément"

Pour ingérer votre jeu de migration à l’aide de Cloud Acceleration Manager, procédez comme suit :

1. Accédez à Cloud Acceleration Manager. Cliquez sur votre carte de projet puis sur la carte de transfert de contenu. Accédez aux **Tâches d’ingestion** et cliquez sur **Nouvelle ingestion**

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Consultez la liste de contrôle d’ingestion et assurez-vous que toutes les étapes sont effectuées. Ces étapes sont nécessaires à la réussite de l’ingestion. Vous devez terminer la liste de contrôle avant de pouvoir passer à l’étape **suivante**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Fournissez les informations requises pour créer une ingestion.

   * **Jeu de migration :** sélectionnez le jeu de migration contenant les données extraites comme Source.
      * Les ensembles de migration expirent après une longue période d’inactivité. Il est donc probable que l’ingestion se produise peu de temps après l’exécution de l’extraction. Consultez [Expiration de l’ensemble de migration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) pour plus d’informations.

   >[!TIP]
   > Si l’extraction est en cours d’exécution, la boîte de dialogue l’indique. Une fois l’extraction terminée avec succès, l’ingestion commence automatiquement. Si l’extraction échoue ou est arrêtée, la tâche d’ingestion est annulée.

   * **Destination :** sélectionnez l’environnement de destination. C’est dans cet environnement que le contenu du jeu de migration est ingéré.
      * Les ingestions ne prennent pas en charge les destinations de type Environnement de développement rapide (RDE) ou Aperçu et elles n’apparaissent pas comme un choix de destination possible, même si l’utilisateur ou l’utilisatrice y a accès.
      * Bien qu’un jeu de migration puisse être ingéré simultanément dans plusieurs destinations, une destination ne peut être la cible que d’une seule ingestion en cours ou en attente à la fois.

   * **Niveau :** sélectionnez le niveau. (Auteur/Publication).
      * Si la source a été `Author`, il est recommandé de l’ingérer dans le niveau `Author` sur la cible. De même, si la source a été `Publish`, la cible doit également être `Publish`.

   >[!NOTE]
   > Si le niveau cible est `Author`, l’instance de création est arrêtée pendant la durée de l’ingestion et n’est pas disponible pour les utilisateurs et utilisatrices (par exemple, les auteurs ou autrices ou toute personne effectuant la maintenance). La raison est de protéger le système et d’empêcher toute modification qui pourrait être perdue ou entraîner un conflit d’ingestion. Assurez-vous d’en informer votre équipe. Notez également que l’environnement apparaît en veille pendant l’ingestion de l’instance de création.

   >[!NOTE]
   > Si le niveau cible est `Publish`, l’instance de publication reste en cours d’exécution lors de l’ingestion.  Cependant, si le processus de compression est en cours d’exécution lors de l’ingestion, un conflit entre les deux processus est susceptible de se produire.  Pour cette raison, le processus d’ingestion 1) désactive le script minuté de compression afin que la compression ne démarre pas pendant l’ingestion, et 2) vérifie si la compression est en cours d’exécution et, si c’est le cas, attend qu’elle se termine avant de poursuivre l’ingestion.  Si l’ingestion de publication dure plus longtemps que prévu, recherchez les instructions de journal associées dans les journaux d’ingestion.

   * **Effacer :** sélectionnez la valeur `Wipe`
      * L’option **Effacer** définit le point de départ de l’ingestion vers la destination. Si l’option **Effacer** est activée, la destination, y compris tout son contenu, est réinitialisée à la version d’AEM spécifiée dans Cloud Manager. Si cette option n’est pas activée, la destination conserve son contenu actuel comme point de départ.
      * Cette option n’affecte **PAS** la manière dont l’ingestion de contenu sera effectuée. L’ingestion utilise toujours une stratégie de remplacement de contenu et _pas_ une stratégie de fusion de contenu. Par conséquent, dans les cas **Effacer** et **Non-Effacer**, l’ingestion d’un jeu de migration remplacera le contenu du même chemin d’accès sur la destination. Par exemple, si le jeu de migration contient `/content/page1` et que la destination contient déjà `/content/page1/product1`, l’ingestion supprime l’intégralité du chemin d’accès au `page1` et ses sous-pages, y compris `product1`, et le remplace par le contenu du jeu de migration. Cela signifie qu’une planification attentive doit être effectuée lors d’une ingestion **Non effacer** vers une destination qui contient tout contenu devant être conservé.
      * Les ingestions sans effacement sont spécifiquement conçues pour le cas d’utilisation d’ingestion de complément. Ces ingestions sont conçues pour avoir une quantité incrémentielle de nouveau contenu qui a changé depuis la dernière ingestion dans un jeu de migration existant. L’exécution d’ingestions sans effacement en dehors de ce cas d’utilisation peut entraîner des temps d’ingestion très longs.

   >[!IMPORTANT]
   > Si le paramètre **Effacer** est activé pour l’ingestion, il réinitialise l’ensemble du référentiel existant, y compris les autorisations utilisateur sur l’instance Cloud Service cible. Cette réinitialisation est également vraie pour un utilisateur administrateur ajouté au groupe **administrateurs** et cet utilisateur doit être ajouté à nouveau au groupe administrateurs pour démarrer une ingestion.

   * **Pré-copie :** sélectionnez la valeur `Pre-copy`
      * Vous pouvez exécuter l’étape facultative de précopie pour accélérer considérablement l’ingestion. Pour plus d’informations, veuillez consulter la section [Ingestion avec AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).
      * Si l’ingestion avec une pré-copie est utilisée (pour S3 ou Azure Data Store), il est recommandé d’exécuter `Author`’ingestion seule en premier. Cela permet d’accélérer l’ingestion `Publish` lorsqu’elle est exécutée ultérieurement.

   >[!IMPORTANT]
   > Vous pouvez déclencher une ingestion vers un environnement de destination seulement si vous appartenez au groupe local **Administrateurs et administratrices d’AEM** sur le service de création Cloud Service de destination. Si vous ne parvenez pas à démarrer une ingestion, reportez-vous à la section [Impossible de démarrer l’ingestion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) pour plus d’informations.

1. Une fois les choix d’ingestion sélectionnés, une estimation de sa durée peut s’afficher. Il s’agit d’une estimation du meilleur effort basée sur les données historiques d’ingestions similaires.

   * Cette estimation n’est ni calculée ni affichée pour les ingestions **sans effacement**, car CAM ne connaît pas la quantité de contenu sur le système cible dans ce cas.
   * Cette estimation n’est calculée et affichée que si les valeurs « Check Size » (Vérifier la taille) de l’extraction ont été collectées et sont disponibles.
   * Cette valeur est une estimation et, bien qu’elle soit calculée intelligemment, elle ne doit pas être considérée comme exacte. Divers facteurs peuvent modifier la durée réelle.
   * Pendant l’exécution de l’ingestion, cette valeur est également disponible dans la boîte de dialogue des durées, accessible via l’action « **Afficher les durées** » de l’ingestion.

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_estimate"
>title="Estimation de la durée d’ingestion"
>abstract="Une durée approximative d’une ingestion spécifique peut être affichée pour donner une idée générale de la durée de cette ingestion. Sa précision a toutefois des limites."

![Image](/help/journey-migration/content-transfer-tool/assets/estimate.png)

1. Cliquez sur **Ingérer**.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Vous pouvez ensuite surveiller l’ingestion à partir de la vue Liste des Tâches d’ingestion et utiliser le menu d’actions de l’ingestion pour afficher les durées et consigner la progression de l’ingestion.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Cliquez sur le bouton **(i)** sur la ligne pour plus d’informations sur la tâche d’ingestion. Vous pouvez voir la durée de chaque étape de l’ingestion lorsqu’elle est en cours d’exécution ou terminée en cliquant sur **…**, puis sur **Afficher les durées**. Les informations de l’extraction sont également affichées pour réaliser ce qui est ingéré.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23b.png)

## Ingestion complémentaire {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="Ingestion de complément"
>abstract="Utilisez la fonction de complément pour déplacer le contenu modifié depuis la précédente activité de transfert de contenu. Une fois l’ingestion terminée, recherchez les erreurs/avertissements éventuels dans les journaux. Toute erreur doit être corrigée immédiatement, soit en traitant les problèmes signalés, soit en contactant l’assistance clientèle d’Adobe."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs" text="Affichage des journaux"

L’outil de transfert de contenu comporte une fonctionnalité permettant d’extraire du contenu différentiel en effectuant un *complément* du jeu de migration. Cela permet de modifier le jeu de migration pour inclure uniquement le contenu qui a été modifié depuis l’extraction précédente sans avoir à extraire à nouveau tout le contenu.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service. Si vous avez utilisé l’étape de précopie pour la première ingestion, vous pouvez ignorer la précopie pour les ingestions de compléments suivantes (si la taille du jeu de migration de complément est inférieure à 200 Go). La raison en est que cela peut ajouter du temps à tout le processus.

Pour ingérer du contenu différentiel une fois certaines ingestions terminées, vous devez exécuter une [Extraction de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process), puis utiliser la méthode d’ingestion avec l’option **Effacer** **désactivée**. Veillez à lire l’explication **Effacer** ci-dessus pour éviter de perdre du contenu déjà présent dans la destination.

Commencez par créer une tâche d’ingestion et assurez-vous que l’option **Effacer** est désactivée pendant l’ingestion, comme illustré ci-dessous :

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Résolution des problèmes {#troubleshooting}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_troubleshooting"
>title="Dépannage pour l’ingestion de contenu"
>abstract="Reportez-vous aux journaux d’ingestion et à la documentation afin de trouver des solutions aux raisons courantes de l’échec d’une ingestion ainsi que le moyen de résoudre le problème. Une fois corrigée, l’ingestion peut être exécutée à nouveau."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers" text="Validation des transferts de contenu "

### Impossible pour CAM de récupérer le jeton de migration {#cam-unable-to-retrieve-the-migration-token}

La récupération automatique du jeton de migration peut échouer pour différentes raisons, y compris la [configuration d’une liste autorisée d’adresses IP via Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) dans l’environnement Cloud Service cible. Dans ce cas de figure, la boîte de dialogue suivante s’affiche lorsque vous tentez de démarrer une ingestion :

![image](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

Récupérez manuellement le jeton de migration en cliquant sur le lien « Obtenir le jeton » dans la boîte de dialogue. Un autre onglet qui affiche le jeton s’ouvre. Vous pouvez ensuite copier le jeton et le coller dans le champ **Entrée du jeton de migration**. À présent, vous devriez être en mesure de commencer l’ingestion.

>[!NOTE]
>
>Le jeton sera disponible pour les utilisateurs et utilisatrices qui appartiennent au groupe local **Administrateurs AEM** sur le service de création Cloud Service de destination.

### Impossible de démarrer l’ingestion {#unable-to-start-ingestion}

Vous pouvez déclencher une ingestion vers un environnement de destination seulement si vous appartenez au groupe local **Administrateurs AEM** sur le service de création Cloud Service de destination. Si vous n’appartenez pas au groupe d’administrateurs AEM, une erreur s’affiche lorsque vous essayez de démarrer une ingestion, comme illustré ci-dessous. Vous pouvez demander à votre administrateur de vous ajouter au groupe local **Administrateurs AEM** ou demander directement le jeton, que vous pouvez ensuite coller dans le champ **Entrée du jeton de migration**.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### Impossible d’atteindre le service de migration {#unable-to-reach-migration-service}

Une fois l’ingestion demandée, un message comme celui-ci peut être présenté à l’utilisateur ou l’utilisatrice : « Le service de migration sur l’environnement de destination est inatteignable. Réessayez ultérieurement ou contactez l’assistance Adobe. »

![image](/help/journey-migration/content-transfer-tool/assets-ctt/error_cannot_reach_migser.png)

Ce message indique que Cloud Acceleration Manager n’a pas pu atteindre le service de migration de l’environnement cible pour démarrer l’ingestion. Cette situation peut se produire pour diverses raisons.

>[!NOTE]
> 
> Le champ « Jeton de migration » s’affiche, car dans certains cas, la récupération de ce jeton est ce qui est en fait interdit. En autorisant sa mise à disposition manuelle, cela peut permettre à l’utilisateur ou l’utilisatrice de démarrer rapidement l’ingestion, sans aide supplémentaire. Si le jeton est fourni et que le message s’affiche toujours, ce n’est donc pas la récupération du jeton qui a posé problème.

* AEM as a Cloud Service conserve l’état de l’environnement et peut parfois devoir redémarrer le service de migration pour plusieurs raisons normales. Si ce service redémarre, il ne peut pas être atteint, mais il finit par être disponible.
* Il est possible qu’un autre processus soit en cours d’exécution sur l’instance. Par exemple, si [Mises à jour de la version d’AEM](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates) applique une mise à jour, le système peut être occupé et le service de migration régulièrement indisponible. Une fois ce processus terminé, le début de l’ingestion peut être réessayé.
* Si une [liste autorisée d’adresses IP a été appliquée](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) via Cloud Manager, cela empêche Cloud Acceleration Manager d’accéder au service de migration. Une adresse IP ne peut pas être ajoutée pour les ingestions, car leur adresse est dynamique. Actuellement, la seule solution consiste à désactiver le place sur la liste autorisée IP pendant le processus d’ingestion et d’indexation en ajoutant temporairement du 0.0.0.0/0 à la place sur la liste autorisée pendant l’exécution du processus d’ingestion et d’indexation.
* D’autres raisons peuvent nécessiter un examen. Si l’ingestion ou l’indexation continue d’échouer, contactez l’Assistance clientèle d’Adobe.

### Mises à jour et assimilations de version AEM {#aem-version-updates-and-ingestions}

Les [mises à jour de la version d’AEM](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates) sont automatiquement appliquées aux environnements pour les tenir à jour avec la version d’AEM as a Cloud Service la plus récente. Si la mise à jour est déclenchée lors d’une ingestion, elle peut entraîner des résultats imprévisibles, notamment la corruption de l’environnement.

Si la fonction « Mises à jour de la version d’AEM » est intégrée au programme de destination, le processus d’ingestion tente de désactiver sa file d’attente avant son démarrage. Une fois l’ingestion terminée, l’état de la mise à jour de version est rétabli à ce qu’il était avant le début des ingestions.

>[!NOTE]
>
> Il n’est plus nécessaire de consigner un ticket d’assistance pour désactiver les « Mises à jour de la version AEM ».

Si l’option « Mises à jour de la version d’AEM » est active (c’est-à-dire, si des mises à jour sont en cours d’exécution ou sont mises en file d’attente pour être exécutées), l’ingestion ne commence pas et l’interface utilisateur affiche le message suivant. Une fois les mises à jour terminées, l’ingestion peut commencer. Cloud Manager peut être utilisé pour afficher l’état actuel des pipelines du programme.

>[!NOTE]
>
> « Mises à jour de la version d’AEM » est exécuté dans le pipeline de l’environnement et attend que le pipeline soit vide. Si les mises à jour sont mises en file d’attente plus longtemps que prévu, assurez-vous qu’un workflow personnalisé ne comporte pas de pipeline verrouillé involontairement.

![Image](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_active.png)

### Échec de l’ingestion en raison d’un environnement cloud non opérationnel {#ingestion-failure-due-to-cloud-environment-not-in-ready-state}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_cloud_environment_not_in_ready_state"
>title="Environnement cloud non opérationnel"
>abstract="Dans de rares cas, l’environnement cloud cible peut rencontrer des problèmes inattendus, ce qui entraîne l’échec de l’ingestion."

Dans de rares cas, l’environnement Cloud Service cible de l’ingestion peut rencontrer des problèmes inattendus. Par conséquent, l’ingestion échoue, car l’environnement n’est pas dans l’état prêt attendu. Consultez le journal d’ingestion pour afficher plus de détails sur l’état d’erreur rencontré.

Assurez-vous que l’environnement de création est disponible et patientez quelques minutes avant de réessayer l’ingestion. Si le problème persiste, contactez le service clientèle en indiquant l’état d’erreur rencontré.

### Échec de l’ingestion de complément dû à une violation de contrainte d’unicité {#top-up-ingestion-failure-due-to-uniqueness-constraint-violation}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_uuid"
>title="Violation de contrainte d’unicité"
>abstract="Les conflits entre identifiants de nœud sont une cause courante de l’échec de l’ingestion hors balayage. Un seul des nœuds en conflit peut exister."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content#top-up-ingestion-process" text="Ingestion de complément"

Les conflits entre identifiants de nœud sont une cause courante de l’échec de l’[Ingestion complémentaire](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process). Pour identifier cette erreur, téléchargez le journal d’ingestion à l’aide de l’interface utilisateur de Cloud Acceleration Manager et recherchez une entrée du type suivant :

>java.lang.RuntimeException : org.apache.jackrabbit.oak.api.CommitFailedException : OakConstraint0030 : la contrainte d’unicité a violé la propriété [jcr:uuid] avec la valeur a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5 : /some/path/jcr:content, /some/other/path/jcr:content

Chaque nœud d’AEM doit disposer d’un UUID unique. Cette erreur indique qu’un nœud en cours d’ingestion présente le même uuid qu’un nœud existant à un chemin d’accès différent sur l’instance de destination. Cette situation peut se produire pour deux raisons :

* Un nœud est déplacé sur la source entre une extraction et une [Extraction complémentaire](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) suivante
   * _À RETENIR_ : pour les extractions de complément, le nœud existe toujours dans le jeu de migration, même s’il n’existe plus sur la source.
* Un nœud de la destination est déplacé entre une ingestion et une ingestion complémentaire suivante.

Ce conflit doit être résolu manuellement. Une personne qui connait le contenu doit décider lequel des deux nœuds doit être supprimé, sans oublier tout autre contenu qui y fait référence. La solution peut nécessiter que l’extraction complémentaire soit effectuée à nouveau sans le nœud fautif.

### Échec de l’ingestion de complément dû à l’impossibilité de supprimer le nœud référencé {#top-up-ingestion-failure-due-to-unable-to-delete-referenced-node}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_referenced_node"
>title="Impossible de supprimer le nœud référencé"
>abstract="Les conflits entre versions pour un nœud particulier sur l’instance de destination sont une cause courante de l’échec d’ingestion hors balayage. Les versions du nœud doivent être corrigées."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content#top-up-ingestion-process" text="Ingestion de complément"

Un conflit de version pour un nœud particulier sur l’instance de destination est une autre cause courante de l’échec de l’[ Ingestion complémentaire ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process). Pour identifier cette erreur, téléchargez le journal d’ingestion à l’aide de l’interface utilisateur de Cloud Acceleration Manager et recherchez une entrée du type suivant :

>java.lang.RuntimeException : org.apache.jackrabbit.oak.api.CommitFailedException : OakIntegrity0001 : impossible de supprimer le nœud référencé : 8a2289f4-b904-4bd0-8410-15e41e0976a8

Cela peut se produire si un nœud de la destination est modifié entre une ingestion et une ingestion **Non effacer** ultérieure, de sorte qu’une nouvelle version a été créée. Si le jeu de migration a été extrait avec les « versions incluses » activées, un conflit peut se produire, car la destination dispose désormais d’une version plus récente référencée par l’historique des versions et d’autres contenus. Le processus d’ingestion ne peut pas supprimer le nœud de version incriminé en raison de son référencement.

La solution peut nécessiter que l’extraction complémentaire soit effectuée à nouveau sans le nœud fautif. Vous pouvez également créer un petit jeu de migration du nœud fautif, mais avec les « versions d’inclusion » désactivées.

Les bonnes pratiques indiquent que si une ingestion **Non effacée** doit être exécutée à l’aide d’un jeu de migration comprenant des versions, il est essentiel que le contenu de la destination soit modifié le moins possible, jusqu’à ce que le parcours de migration soit terminé. Dans le cas contraire, ces conflits peuvent se produire.

### Échec de l’ingestion dû à des valeurs élevées de propriété de nœud {#ingestion-failure-due-to-large-node-property-values}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_bson"
>title="Propriété de nœud élevée"
>abstract="Le dépassement de la taille maximale des valeurs de propriété de nœud est une cause courante de l’échec de l’ingestion. Consultez la documentation, y compris celle relative au rapport BPA, pour remédier à cette situation."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool" text="Conditions préalables à la migration"

La valeur des propriétés de nœud stockées dans MongoDB ne doit pas dépasser 16 Mo. Si la valeur d’un nœud dépasse la taille prise en charge, l’ingestion échoue et le journal contient :

* une erreur `BSONObjectTooLarge` et indiquez quel nœud a dépassé le maximum, ou
* une erreur `BsonMaximumSizeExceededException`, qui indique qu’il existe un nœud contenant probablement des caractères unicode qui dépasse la taille maximale **

Il s’agit d’une restriction MongoDB.

Pour plus d’informations et pour obtenir un lien vers un outil Oak qui pourrait vous aider à trouver tous les nœuds volumineux, consultez la note de `Node property value in MongoDB` dans la section [Conditions préalables pour l’outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md). Une fois tous les nœuds de grande taille résolus, exécutez à nouveau l’extraction et l’ingestion.

Pour éviter cette restriction, exécutez l’[analyseur de bonnes pratiques](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md) sur l’instance AEM source et passez en revue les résultats qu’il présente, notamment le modèle [ « Structure de référentiel non prise en charge » (URS)](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/urs).

>[!NOTE]
>
>[Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md) version 2.1.50+ génère des rapports sur les nœuds volumineux contenant des caractères Unicode qui dépassent la taille maximale. Vérifiez que vous exécutez la dernière version. Les versions de BPA antérieures à la version 2.1.50 n’identifient pas et ne génèrent pas de rapports sur ces nœuds volumineux et doivent être découvertes séparément à l’aide de l’outil Oak requis mentionné ci-dessus.

### Échec de l’ingestion en raison d’erreurs intermittentes inattendues {#ingestion-failure-due-to-unexpected-intermittent-errors}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_intermittent_errors"
>title="Erreurs intermittentes inattendues"
>abstract="Parfois, des erreurs de service intermittentes inattendues peuvent se produire en aval. Malheureusement, le seul recours consiste à simplement relancer l’ingestion."

Parfois, des problèmes intermittents inattendus peuvent se produire lors d’échecs d’ingestion, où malheureusement le seul recours est de relancer l’ingestion. Vérifiez le journal d’ingestion pour identifier la cause de l’échec et voir s’il correspond à l’une des erreurs répertoriées ci-dessous, où une nouvelle tentative doit être effectuée.

#### Problèmes liés à MongoDB {#mongo-db-issues}

* `Atlas prescale timeout error` - La phase d’ingestion tente de prédéfinir la base de données cloud cible à une taille appropriée qui correspond à la taille du contenu du jeu de migration en cours d’ingestion. Dans de rares cas, cette opération ne se termine pas dans le délai prévu.
* `Exhausted mongo restore retries` - Les tentatives de restauration d’une image mémoire locale du contenu du jeu de migration ingéré dans la base de données cloud sont épuisées. Cela indique un problème d’intégrité global/de réseau avec MongoDB, qui guérit souvent spontanément en quelques minutes.
* `Mongo network error` - Parfois, l’établissement d’une connexion à MongoDB peut échouer, ce qui entraîne la sortie précoce du processus d’ingestion et le signalement comme un échec. Une simple reprise de l’ingestion doit être tentée.
* `Mongo server selection error` - Il s’agit d’une rare erreur de délai d’expiration côté client mongo qui peut se produire pour plusieurs raisons sous-jacentes. Il est probable qu’une nouvelle tentative corrigera le problème.
* `Mongo took too long to start` - Dans de très rares cas, la base de données MongoDB locale utilisée dans le workflow d’ingestion peut ne pas démarrer. Il est probable qu’une nouvelle tentative corrigera le problème.

#### Problèmes AZCopy {#azcopy-issues}

* `AZCopy critical failure` - Dans de rares cas, l’outil AZCopy utilisé pour effectuer l’étape de précopie de l’ingestion peut échouer de manière inattendue. Une nouvelle tentative d’ingestion doit être tentée dans ce cas.

### Ingestion annulée {#ingestion-rescinded}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_rescinded"
>title="Ingestion annulée"
>abstract="L’extraction que l’ingestion attendait ne s’est pas terminée correctement. L’ingestion a été annulée, car elle n’a pas pu être exécutée."

Une ingestion créée avec une extraction en cours d’exécution en tant que jeu de migration source attend patiemment que cette extraction réussisse et commence normalement à ce stade. Si l’extraction échoue ou est arrêtée, l’ingestion et sa tâche d’indexation ne commencent pas, mais sont annulées. Dans ce cas, vérifiez l’extraction pour déterminer pourquoi elle a échoué, corrigez le problème et recommencez l’extraction. Une fois l’extraction fixe en cours d’exécution, une nouvelle ingestion peut être planifiée.

### Échec du démarrage de l’ingestion en attente {#waiting-ingestion-not-started}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_waiting_ingestion_not_started"
>title="Ingestion en attente non démarrée"
>abstract="L’ingestion n’a pas pu démarrer après avoir attendu la fin d’une extraction."

Une ingestion créée avec une extraction en cours d’exécution en tant que jeu de migration source attend que cette extraction réussisse. À ce stade, l’ingestion tente de démarrer normalement. Si l’ingestion ne démarre pas, elle est marquée comme ayant échoué. Les raisons possibles de ne pas démarrer sont les suivantes : une Liste autorisée IP est configurée sur l’environnement de création cible ; l’environnement cible n’est pas disponible pour une autre raison.  Dans ce cas, vérifiez pourquoi l’ingestion n’a pas démarré, corrigez le problème, puis redémarrez l’ingestion (il n’est pas nécessaire de réexécuter l’extraction).

### Ressource supprimée absente après la réexécution de l’ingestion

En règle générale, il n’est pas recommandé de modifier les données de l’environnement cloud entre les ingestions.

Lorsqu’une ressource est supprimée de la destination Cloud Service à l’aide de l’interface utilisateur tactile d’Assets, les données de nœud sont supprimées, mais l’objet Blob de ressource avec l’image n’est pas immédiatement supprimé. Il est marqué pour suppression afin de ne plus apparaître dans l’interface utilisateur. Cependant, il reste dans le magasin de données jusqu’à ce que le nettoyage soit effectué et que l’objet Blob soit supprimé.

Dans le scénario où une ressource précédemment migrée est supprimée et où l’ingestion suivante est exécutée avant que le garbage collector n’ait terminé la suppression de la ressource, l’ingestion du même jeu de migration ne restaurera pas la ressource supprimée. Lorsque l’ingestion vérifie la ressource dans l’environnement cloud d’, il n’existe aucune donnée de nœud ; par conséquent, l’ingestion copie les données de nœud dans l’environnement cloud. Cependant, lorsqu’il vérifie la banque d’objets blob, il constate que l’objet blob est présent et ignore la copie de l’objet blob. C’est pourquoi les métadonnées sont présentes après l’ingestion lorsque vous examinez la ressource à partir de l’interface utilisateur tactile, mais pas l’image. N’oubliez pas que les jeux de migration et l’ingestion de contenu n’ont pas été conçus pour gérer ce cas. Ils visent à ajouter du nouveau contenu à l’environnement cloud et à ne pas restaurer le contenu précédemment migré.

## Prochaines étapes {#whats-next}

Une fois l’ingestion réussie, l’indexation AEM démarre automatiquement. Pour plus d’informations, consultez [Indexation après la migration ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/indexing-content.md) contenu .

Une fois l’ingestion de contenu dans Cloud Service terminée, vous pouvez afficher les journaux de chaque étape (extraction et ingestion) et rechercher les erreurs. Consultez la section [Affichage des journaux d’un ensemble de migration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/viewing-logs.md) pour en savoir plus.
