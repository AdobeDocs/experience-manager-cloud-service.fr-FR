---
title: Ingestion de contenu dans Cloud Service
description: Découvrez comment utiliser Cloud Acceleration Manager pour ingérer du contenu à partir de votre jeu de migration vers une instance de Cloud Service de destination.
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
feature: Migration
role: Admin
source-git-commit: 1add389e1bba181757229ca73252f1fcaa9d049a
workflow-type: tm+mt
source-wordcount: '3187'
ht-degree: 38%

---

# Ingestion de contenu dans Cloud Service {#ingesting-content}

## Processus d’ingestion dans Cloud Acceleration Manager {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Ingestion de contenu"
>abstract="L’ingestion désigne l’ingestion de contenu à partir du jeu de migration dans l’instance Cloud Service cible. L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content#top-up-extraction-process" text="Extraction de complément"

Pour ingérer votre jeu de migration à l’aide de Cloud Acceleration Manager, procédez comme suit :

1. Accédez à Cloud Acceleration Manager. Cliquez sur votre carte de projet puis sur la carte de transfert de contenu. Accédez aux **Tâches d’ingestion** et cliquez sur **Nouvelle ingestion**

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Consultez la liste de contrôle d’ingestion et assurez-vous que toutes les étapes sont effectuées. Ces étapes sont nécessaires à la réussite de l’ingestion. Vous devez terminer la liste de contrôle avant de pouvoir passer à l’étape **suivante**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Fournissez les informations requises pour créer une ingestion.

   * **Jeu de migration :** Sélectionnez le jeu de migration contenant les données extraites sous la forme Source.
      * Les jeux de migration expirent après une longue période d’inactivité. Il est donc probable que l’ingestion se produise peu de temps après l’exécution de l’extraction. Consultez [Expiration du jeu de migration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) pour plus d’informations.

   >[!TIP]
   > Si l’extraction est en cours d’exécution, la boîte de dialogue l’indique. Une fois l’extraction terminée, l’ingestion démarre automatiquement. Si l’extraction échoue ou est arrêtée, la tâche d’ingestion est annulée.

   * **Destination :** Sélectionnez l’environnement de destination. C’est dans cet environnement que le contenu du jeu de migration est ingéré.
      * Les ingestion ne prennent pas en charge les destinations de type Environnement de développement rapide (RDE) ou Aperçu, et elles n’apparaissent pas comme un choix de destination possible, même si l’utilisateur y a accès.
      * Bien qu’un jeu de migration puisse être ingéré simultanément dans plusieurs destinations, une destination peut être la cible d’une seule ingestion en cours d’exécution ou en attente à la fois.

   * **Niveau :** Sélectionnez le niveau. (Auteur/Publication).
      * Si la source était `Author`, il est recommandé de l’ingérer dans le niveau `Author` sur la cible. De même, si la source était `Publish`, la cible doit également être `Publish`.

   >[!NOTE]
   > Si le niveau cible est `Author`, l’instance de création est arrêtée pendant la durée de l’ingestion et n’est pas disponible pour les utilisateurs et utilisatrices (par exemple, les auteurs ou autrices ou toute personne effectuant la maintenance). La raison est de protéger le système et d’empêcher toute modification qui pourrait être perdue ou provoquer un conflit d’ingestion. Assurez-vous d’en informer votre équipe. Notez également que l’environnement apparaît en veille pendant l’ingestion de l’instance de création.

   * **Wipe:** Sélectionnez la valeur `Wipe`
      * L’option **Wipe** définit le point de départ de la destination de l’ingestion. Si **Wipe** est activé, la destination, y compris tout son contenu, est réinitialisée à la version de l’AEM spécifiée dans Cloud Manager. Si elle n’est pas activée, la destination conserve son contenu actuel comme point de départ.
      * Cette option n’affecte **PAS** la manière dont l’ingestion du contenu sera effectuée. L’ingestion utilise toujours une stratégie de remplacement de contenu et _non_ une stratégie de fusion de contenu. Ainsi, dans les cas **Wipe** et **Non-Wipe**, l’ingestion d’un jeu de migration remplacera le contenu dans le même chemin d’accès sur la destination. Par exemple, si le jeu de migration contient `/content/page1` et que la destination contient déjà `/content/page1/product1`, l’ingestion supprime l’intégralité du chemin d’accès `page1` et ses sous-pages, y compris `product1`, et le remplace par le contenu du jeu de migration. Cela signifie qu’une planification minutieuse doit être effectuée lors de l’ingestion **non effacée** vers une destination qui contient tout contenu qui doit être conservé.
      * Les assimilations non effacées sont spécialement conçues pour le cas d’utilisation de l’ingestion de complément. Ces assimilations sont destinées à disposer d’une quantité incrémentielle de nouveau contenu qui a changé depuis la dernière ingestion dans un jeu de migration existant. L’exécution d’ingérations non effacées en dehors de ce cas d’utilisation peut entraîner des temps d’ingestion très longs.

   >[!IMPORTANT]
   > Si le paramètre **Wipe** est activé pour l’ingestion, il réinitialise l’ensemble du référentiel existant, y compris les autorisations utilisateur sur l’instance du Cloud Service cible. Cette réinitialisation est également vraie pour un utilisateur administrateur ajouté au groupe **administrateurs** et cet utilisateur doit être ajouté à nouveau au groupe administrateurs pour démarrer une ingestion.

   * **Pré-copie :** Sélectionnez la valeur `Pre-copy`
      * Vous pouvez exécuter l’étape de précopie facultative pour accélérer considérablement l’ingestion. Pour plus d’informations, veuillez consulter la section [Ingestion avec AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).
      * Si l’ingestion avec une précopie est utilisée (pour S3 ou Azure Data Store), il est recommandé d’exécuter l’ingestion `Author` en premier lieu seul. Cela permet d’accélérer l’ingestion `Publish` lorsqu’elle est exécutée ultérieurement.

   >[!IMPORTANT]
   > Vous pouvez déclencher une ingestion vers un environnement de destination seulement si vous appartenez au groupe local **Administrateurs et administratrices d’AEM** sur le service de création Cloud Service de destination. Si vous ne parvenez pas à démarrer une ingestion, reportez-vous à la section [Impossible de démarrer l’ingestion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) pour plus d’informations.

1. Une fois les choix d’ingestion sélectionnés, une estimation de sa durée s’affiche. Il s’agit d’une estimation du meilleur effort basée sur des données historiques d’assimilations similaires.

   * Cette estimation n&#39;est calculée et affichée que si les valeurs &quot;Vérifier la taille&quot; de l&#39;extraction ont été collectées et sont disponibles.
   * Cette valeur est une estimation qui, bien qu’elle soit calculée intelligemment, ne doit pas être considérée comme exacte. Plusieurs facteurs peuvent modifier la durée réelle.
   * Pendant l’ingestion, cette valeur sera également disponible dans la boîte de dialogue des durées, accessible via l’action &quot;**Afficher les durées**&quot; de l’ingestion.

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_estimate"
>title="Estimation de la durée d’ingestion"
>abstract="Une durée approximative d’une ingestion spécifique peut être affichée pour donner une idée générale de la durée de cette ingestion. Sa précision a toutefois des limites."

![Image](/help/journey-migration/content-transfer-tool/assets/estimate.png)

1. Cliquez sur **Ingérer**.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Vous pouvez ensuite surveiller l’ingestion dans la vue de liste Tâches d’ingestion et utiliser le menu d’action de l’ingestion pour afficher les durées et le journal au fur et à mesure de l’ingestion.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Cliquez sur le bouton **(i)** sur la ligne pour plus d’informations sur la tâche d’ingestion. Vous pouvez voir la durée de chaque étape de l’ingestion lorsqu’elle est en cours d’exécution ou terminée en cliquant sur **…**, puis sur **Afficher les durées**. Les informations de l’extraction sont également affichées pour réaliser ce qui est ingéré.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23b.png)

## Ingestion complémentaire {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="Ingestion de complément"
>abstract="Utilisez la fonction de complément pour déplacer le contenu modifié depuis la précédente activité de transfert de contenu. Une fois l’ingestion terminée, recherchez les erreurs/avertissements éventuels dans les journaux. Toute erreur doit être corrigée immédiatement, soit en traitant les problèmes signalés, soit en contactant l’assistance clientèle d’Adobe."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs" text="Affichage des journaux"

L’outil de transfert de contenu dispose d’une fonctionnalité qui permet d’extraire du contenu différentiel en effectuant un *complément* du jeu de migration. Cela permet de modifier le jeu de migration pour inclure uniquement le contenu qui a changé depuis l’extraction précédente sans avoir à extraire à nouveau tout le contenu.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service. Si vous avez utilisé l’étape de précopie pour la première ingestion, vous pouvez ignorer la précopie pour les prochaines assimilations de complément (si la taille du jeu de migration de complément est inférieure à 200 Go). La raison est qu’il peut ajouter du temps à l’ensemble du processus.

Pour ingérer un contenu différentiel une fois certaines assimilations terminées, vous devez exécuter une [extraction de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process), puis utiliser la méthode d’ingestion avec l’option **Effacer** **désactivée**. Veillez à lire l’explication **Wipe** ci-dessus pour éviter de perdre du contenu déjà sur la destination.

Commencez par créer une tâche d’ingestion et assurez-vous que l’option **Effacer** est désactivée pendant l’ingestion, comme illustré ci-dessous :

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Résolution des problèmes {#troubleshooting}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_troubleshooting"
>title="Dépannage pour l’ingestion de contenu"
>abstract="Reportez-vous aux journaux d’ingestion et à la documentation afin de trouver des solutions aux raisons courantes de l’échec d’une ingestion ainsi que le moyen de résoudre le problème. Une fois corrigée, l’ingestion peut être exécutée à nouveau."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers" text="Validation des transferts de contenu "

### Impossible pour CAM de récupérer le jeton de migration {#cam-unable-to-retrieve-the-migration-token}

La récupération automatique du jeton de migration peut échouer pour différentes raisons, y compris la [configuration d’une liste autorisée d’adresses IP via Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) dans l’environnement Cloud Service cible. Dans ce cas de figure, la boîte de dialogue suivante s’affiche lorsque vous tentez de démarrer une ingestion :

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
* Il est possible qu’un autre processus soit en cours d’exécution sur l’instance. Par exemple, si [AEM mises à jour de version](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates) applique une mise à jour, le système peut être occupé et le service de migration est régulièrement indisponible. Une fois ce processus terminé, le début de l’ingestion peut à nouveau être tenté.
* Si une [liste autorisée d’adresses IP a été appliquée](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) via Cloud Manager, cela empêche Cloud Acceleration Manager d’accéder au service de migration. Une adresse IP ne peut pas être ajoutée pour les ingestions, car leur adresse est dynamique. Actuellement, la seule solution est de désactiver la liste autorisée IP pendant le processus d’ingestion et d’indexation.
* D’autres raisons peuvent nécessiter un examen. Si l’ingestion ou l’indexation continue d’échouer, contactez l’assistance clientèle d’Adobe.

### AEM des mises à jour et des ingérations de version {#aem-version-updates-and-ingestions}

[AEM les mises à jour de version](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates) sont automatiquement appliquées aux environnements pour les tenir à jour avec la version la plus récente d’AEM as a Cloud Service. Si la mise à jour est déclenchée lorsqu’une ingestion est effectuée, elle peut entraîner des résultats imprévisibles, y compris la corruption de l’environnement.

Si les &quot;Mises à jour de version AEM&quot; sont intégrées dans le programme de destination, le processus d’ingestion tente de désactiver sa file d’attente avant de commencer. Une fois l’ingestion terminée, l’état du mise à jour de version est renvoyé à son état avant le début des ingérations.

>[!NOTE]
>
> Il n’est plus nécessaire de consigner un ticket d’assistance pour que &quot;AEM mises à jour de version&quot; soit désactivé.

Si &quot;AEM mises à jour de version&quot; est actif (c’est-à-dire que les mises à jour sont en cours d’exécution ou sont placées en file d’attente pour être exécutées), l’ingestion ne démarre pas et l’interface utilisateur présente le message suivant. Une fois les mises à jour terminées, l’ingestion peut être lancée. Cloud Manager peut être utilisé pour afficher l’état actuel des pipelines du programme.

>[!NOTE]
>
> &quot;AEM les mises à jour de version&quot; est exécuté dans le pipeline de l’environnement et attend que le pipeline soit clair. Si les mises à jour sont mises en file d’attente plus longtemps que prévu, assurez-vous qu’un workflow personnalisé ne verrouille pas involontairement le pipeline.

![Image](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_active.png)

### Échec de l’ingestion de complément dû à une violation de contrainte d’unicité {#top-up-ingestion-failure-due-to-uniqueness-constraint-violation}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_uuid"
>title="Violation de contrainte d’unicité"
>abstract="Les conflits entre identifiants de nœud sont une cause courante de l’échec de l’ingestion hors balayage. Un seul des nœuds en conflit peut exister."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content#top-up-ingestion-process" text="Ingestion de complément"

Les conflits entre identifiants de nœud sont une cause courante de l’échec de l’[Ingestion complémentaire](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process). Pour identifier cette erreur, téléchargez le journal d’ingestion à l’aide de l’interface utilisateur de Cloud Acceleration Manager et recherchez une entrée du type suivant :

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: Uniqueness constraint violated property [jcr:uuid] having value a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5e5: /some/path/jcr:content, /some/other/path/jcr:content

Chaque nœud d’AEM doit disposer d’un UUID unique. Cette erreur indique qu’un noeud en cours d’ingestion possède le même uuid que celui qui existe à un autre chemin sur l’instance de destination. Cette situation peut se produire pour deux raisons :

* Un noeud est déplacé sur la source entre une extraction et une [extraction de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) ultérieure.
   * _RAPPEL_ : pour les extractions de complément, le noeud existera toujours dans le jeu de migration, même s’il n’existe plus sur la source.
* Un noeud sur la destination est déplacé entre une ingestion et une ingestion de complément ultérieure.

Ce conflit doit être résolu manuellement. Une personne qui connait le contenu doit décider lequel des deux nœuds doit être supprimé, sans oublier tout autre contenu qui y fait référence. La solution peut nécessiter que l’extraction complémentaire soit effectuée à nouveau sans le nœud fautif.

### Échec de l’ingestion de complément dû à l’impossibilité de supprimer le nœud référencé {#top-up-ingestion-failure-due-to-unable-to-delete-referenced-node}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_referenced_node"
>title="Impossible de supprimer le nœud référencé"
>abstract="Les conflits entre versions pour un nœud particulier sur l’instance de destination sont une cause courante de l’échec d’ingestion hors balayage. Les versions du nœud doivent être corrigées."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content#top-up-ingestion-process" text="Ingestion de complément"

Une autre cause courante de l’échec d’une [ingestion de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) est un conflit de version pour un noeud particulier sur l’instance de destination. Pour identifier cette erreur, téléchargez le journal d’ingestion à l’aide de l’interface utilisateur de Cloud Acceleration Manager et recherchez une entrée du type suivant :

>java.lang.RuntimeException : org.apache.jackrabbit.oak.api.CommitFailedException : OakIntegrity0001 : impossible de supprimer le noeud référencé : 8a289f4-b904-4bd0-8410-15e41e0976a8

Cela peut se produire si un noeud de la destination est modifié entre une ingestion et une ingestion **Non-Wipe** ultérieure de sorte qu’une nouvelle version ait été créée. Si le jeu de migration a été extrait avec l’option &quot;Inclure les versions&quot; activée, un conflit peut se produire, car la destination possède désormais une version plus récente qui est référencée par l’historique des versions et d’autres contenus. Le processus d’ingestion ne parvient pas à supprimer le noeud de version offensante, car il est référencé.

La solution peut nécessiter que l’extraction de complément soit effectuée à nouveau sans le noeud offensif. Vous pouvez également créer un petit jeu de migration du noeud incriminé, mais en désactivant l’option &quot;Versions d’inclusion&quot;.

Les bonnes pratiques indiquent que si une ingestion **non effacée** doit être exécutée à l’aide d’un jeu de migration qui inclut des versions, il est essentiel que le contenu de la destination soit modifié le moins possible, jusqu’à ce que le parcours de migration soit terminé. Sinon, ces conflits peuvent se produire.

### Échec de l’ingestion dû à des valeurs élevées de propriété de nœud {#ingestion-failure-due-to-large-node-property-values}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_bson"
>title="Propriété de nœud élevée"
>abstract="Le dépassement de la taille maximale des valeurs de propriété de nœud est une cause courante de l’échec de l’ingestion. Consultez la documentation, y compris celle relative au rapport BPA, pour remédier à cette situation."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool" text="Conditions préalables à la migration"

La valeur des propriétés de nœud stockées dans MongoDB ne doit pas dépasser 16 Mo. Si une valeur de noeud dépasse la taille prise en charge, l’ingestion échoue et le journal contient l’une des options suivantes :

* une erreur `BSONObjectTooLarge` et spécifiez le noeud qui a dépassé le maximum, ou
* une erreur `BsonMaximumSizeExceededException` qui indique qu’il existe un noeud susceptible de contenir des caractères Unicode dépassant la taille maximale **

Il s’agit d’une restriction MongoDB.

Pour plus d’informations et consulter un lien vers un outil Oak qui peut vous aider à trouver tous les noeuds volumineux, reportez-vous à la note `Node property value in MongoDB` de la section [ Conditions préalables requises pour l’outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md) . Une fois tous les noeuds de grande taille corrigés, exécutez à nouveau l’extraction et l’ingestion.

Pour éviter toute restriction, exécutez l’[analyseur des bonnes pratiques](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md) sur l’instance d’AEM source et examinez les résultats qu’il présente, en particulier le modèle [&quot;Unsupported Repository Structure&quot; (URS)](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/urs).

>[!NOTE]
>
>[Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md) version 2.1.50+ : effectue un rapport sur les noeuds volumineux contenant des caractères Unicode supérieurs à la taille maximale. Vérifiez que vous exécutez la dernière version. Les versions BPA antérieures à la version 2.1.50 n’identifieront pas et ne signaleront pas ces noeuds volumineux ; elles devront être découvertes séparément à l’aide de l’outil Oak prérequis mentionné ci-dessus.

### Échec de l’ingestion en raison d’erreurs intermittentes inattendues {#ingestion-failure-due-to-unexpected-intermittent-errors}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_intermittent_errors"
>title="Erreurs intermittentes inattendues"
>abstract="Parfois, des erreurs de service intermittentes inattendues peuvent se produire en aval. Malheureusement, le seul recours consiste à simplement relancer l’ingestion."

Parfois, des problèmes intermittents inattendus peuvent se prêter à des ingérations qui ont échoué et, malheureusement, le seul recours est de relancer l&#39;ingestion. Examinez le journal d’ingestion pour découvrir la cause de l’échec et voir s’il s’aligne sur l’une des erreurs répertoriées ci-dessous, où une nouvelle tentative doit être effectuée.

## Problèmes de MongoDB {#mongo-db-issues}

* `Atlas prescale timeout error` - La phase d’ingestion tentera de présenter la base de données cloud cible à une taille appropriée qui s’aligne sur la taille du contenu du jeu de migration en cours d’ingestion. Très rarement, cette opération ne se termine pas dans le délai prévu.
* `Exhausted mongo restore retries` - Les tentatives de restauration d’un vidage local du contenu du jeu de migration ingéré vers la base de données cloud ont été épuisées. Cela indique un problème de réseau/d’intégrité global avec MongoDB, qui se soigne souvent après quelques minutes.

### Ingestion annulée {#ingestion-rescinded}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_rescinded"
>title="Ingestion annulée"
>abstract="L’extraction que l’ingestion attendait ne s’est pas terminée correctement. L’ingestion a été annulée, car elle n’a pas pu être exécutée."

Une ingestion créée avec une extraction en cours d’exécution comme jeu de migration source attend patiemment jusqu’à ce que cette extraction réussisse, et démarre normalement à ce moment. Si l’extraction échoue ou est arrêtée, l’ingestion et sa tâche d’indexation ne démarrent pas, mais sont annulées. Dans ce cas, vérifiez l’extraction pour déterminer pourquoi elle a échoué, corrigez le problème et recommencez à extraire. Une fois l’extraction fixe en cours d’exécution, une nouvelle ingestion peut être planifiée.

### Ressource supprimée non présente après la réexécution de l’ingestion

En règle générale, il n’est pas recommandé de modifier les données de l’environnement cloud entre les ingestion.

Lorsqu’une ressource est supprimée de la destination du Cloud Service à l’aide de l’interface utilisateur tactile d’Assets, les données de noeud sont supprimées, mais l’objet Blob de la ressource avec l’image n’est pas immédiatement supprimé. Il est marqué pour suppression de sorte qu’il n’apparaisse plus dans l’interface utilisateur. Cependant, il reste dans l’entrepôt de données jusqu’à ce que le nettoyage de la mémoire se produise et que l’objet blob soit supprimé.

Dans le cas où une ressource précédemment migrée est supprimée et que l’ingestion suivante est exécutée avant que le garbage collector n’ait terminé la suppression de la ressource, l’ingestion du même jeu de migration ne restaurera pas la ressource supprimée. Lorsque l’ingestion recherche la ressource dans l’environnement cloud, il n’existe aucune donnée de noeud. Par conséquent, l’ingestion copie les données de noeud dans l’environnement cloud. Cependant, lorsqu’il vérifie l’objet blob, il constate que l’objet blob est présent et ignore la copie de l’objet blob. C’est pourquoi les métadonnées sont présentes après l’ingestion lorsque vous examinez la ressource à partir de l’interface utilisateur tactile, mais pas l’image. N’oubliez pas que les jeux de migration et l’ingestion de contenu n’ont pas été conçus pour gérer ce cas. Ils visent à ajouter du nouveau contenu à l’environnement cloud et à ne pas restaurer le contenu précédemment migré.

## Prochaines étapes {#whats-next}

Une fois l’ingestion terminée, AEM indexation démarre automatiquement. Pour plus d’informations, voir [Indexation après migration de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/indexing-content.md) .

Une fois l’ingestion de contenu dans Cloud Service terminée, vous pouvez afficher les journaux de chaque étape (extraction et ingestion) et rechercher les erreurs. Consultez la section [Affichage des journaux d’un jeu de migration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/viewing-logs.md) pour en savoir plus.
