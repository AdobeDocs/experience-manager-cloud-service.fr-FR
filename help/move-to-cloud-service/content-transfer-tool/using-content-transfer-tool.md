---
title: Utilisation de l’outil de transfert de contenu
description: Utilisation de l’outil de transfert de contenu
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: dbca0404c310bc0fa9372347bb7b37649adf8b94
workflow-type: tm+mt
source-wordcount: '3193'
ht-degree: 81%

---

# Utilisation de l’outil de transfert de contenu {#using-content-transfer-tool}

## Points importants concernant l’utilisation de l’outil de transfert de contenu {#pre-reqs}

Consultez la section ci-dessous afin de comprendre les points importants à prendre en compte pour l’exécution de l’outil de transfert de contenu :

* La configuration minimale requise pour l’outil de transfert de contenu est AEM 6.3+ et JAVA 8. Si vous utilisez une version antérieure d’AEM, vous devez mettre à niveau votre référentiel de contenu à la version AEM 6.5 pour utiliser l’outil de transfert de contenu.

* Java doit être configuré dans l’environnement AEM, de sorte que la commande `java` puisse être exécutée par l’utilisateur démarrant AEM.

* Il est recommandé de désinstaller les anciennes versions de l’outil de transfert de contenu lors de l’installation de la version 1.3.0, car l’outil a subi un changement d’architecture majeur. Avec la version 1.3.0, vous devez également créer des jeux de migration et réexécuter l’extraction et l’ingestion sur les nouveaux jeux de migration.

* L’outil de transfert de contenu peut être utilisé avec les types de magasin de données suivants : File Data Store, S3 Data Store, Shared S3 Data Store et Azure Blob Store Data Store.

* Si vous utilisez un *environnement sandbox*, assurez-vous que celui-ci est à jour et mis à niveau vers la dernière version. Si vous utilisez un *environnement de production*, il est automatiquement mis à jour.

* Pour utiliser l’outil de transfert de contenu, vous devez être un utilisateur administrateur sur votre instance source et appartenir au groupe d’**administrateurs** AEM local dans l’instance Cloud Service vers laquelle vous transférez du contenu. Les utilisateurs non privilégiés ne pourront pas récupérer le jeton d’accès pour utiliser l’outil de transfert de contenu.

* Lorsque l’option **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est activée, elle supprime l’intégralité du référentiel existant et crée un référentiel dans lequel ingérer du contenu. Cela signifie que tous les paramètres sont réinitialisés, y compris les autorisations relatives à l’instance Cloud Service cible. C’est également vrai pour un utilisateur administrateur ajouté au groupe **administrateurs**. L’utilisateur devra être ajouté une nouvelle fois au groupe **administrateurs** pour récupérer le jeton d’accès à l’outil de transfert de contenu (CTT).

* Le jeton d’accès peut expirer périodiquement, soit après une période spécifique, soit après la mise à niveau de l’environnement Cloud Service. Si le jeton d’accès a expiré, vous ne pourrez pas vous connecter à l’instance de Cloud Service et vous devrez récupérer le nouveau jeton d’accès. L’icône d’état associée à un jeu de migration existant prend l’aspect d’un nuage rouge et affiche un message si vous le survolez.

* L’outil de transfert de contenu (CTT) n’effectue aucune analyse avant de transférer le contenu de l’instance source vers l’instance cible. Par exemple, le CTT ne fait pas de distinction entre le contenu publié et le contenu non publié lors de l’ingestion de contenu dans un environnement de publication. Quel que soit le contenu spécifié dans le jeu de migration, il sera ingéré dans l’instance cible choisie. L’utilisateur peut ingérer un jeu de migration dans une instance d’auteur ou de publication, ou les deux. Il est recommandé, tout en déplaçant le contenu vers une instance de production, d’installer le CTT sur l’instance d’auteur source afin de déplacer le contenu vers l’instance d’auteur cible. De même, il est recommandé d’installer le CTT dans l’instance de publication source pour déplacer le contenu vers l’instance de publication cible. Pour plus d’informations, voir [Exécution de l’outil de transfert de contenu sur une instance de publication](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-ctt-on-publish) .

* Les utilisateurs et les groupes transférés par l’outil de transfert de contenu sont uniquement ceux requis en fonction du contenu pour respecter les autorisations. Le processus d’*extraction* copie l’intégralité de `/home` dans le jeu de migration et le processus d’*ingestion* copie tous les utilisateurs et groupes référencés dans les listes de contrôle d’accès du contenu migré. Pour mapper automatiquement les utilisateurs et les groupes existants avec leurs ID IMS, reportez-vous à la section [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr#cloud-migration).

* Pendant la phase d’extraction, l’outil de transfert de contenu est exécuté sur une instance source AEM active.

* Après avoir terminé la phase d’*extraction* du processus de transfert de contenu et avant de commencer la phase d’*ingestion* pour ingérer du contenu dans vos instances d’*évaluation* ou de *production* AEM as a Cloud Service, vous devez enregistrer un ticket d’assistance pour informer Adobe de votre intention d’exécuter *Ingestion* afin qu’Adobe puisse s’assurer qu’aucune interruption ne se produise pendant le processus d’*ingestion*. Vous devrez consigner le ticket de support une semaine avant la date d’*Ingestion* prévue. Une fois que vous aurez soumis le ticket d’assistance, l’équipe d’assistance vous donnera des conseils sur les étapes suivantes. Vous pouvez enregistrer un ticket d’assistance avec les détails suivants :

   * Date exacte et heure estimée (avec votre fuseau horaire) lorsque vous prévoyez de lancer la phase d’*ingestion*.
   * Type d’environnement (évaluation ou production) dans lequel vous prévoyez d’importer des données.
   * ID de programme.

* La *phase d’ingestion* de l’auteur réduit l’ensemble du déploiement de l’auteur. L’auteur AEM ne sera donc pas disponible pendant la totalité du processus d’ingestion. Assurez-vous également qu’aucun pipeline Cloud Manager n’est exécuté pendant que vous exécutez la phase d’*ingestion*.

* Si vous utilisez `Amazon S3` ou `Azure` comme entrepôt de données sur le système AEM source, cet entrepôt doit être configuré de sorte que les objets blob stockés ne puissent pas être supprimés (nettoyage de la mémoire). Cela garantit l’intégrité des données d’index et un échec de ce type de configuration peut entraîner des échecs d’extraction en raison d’un manque d’intégrité de ces données d’index.

* Si vous utilisez des index personnalisés, vous devez veiller à les configurer avec le nœud `tika` avant d’exécuter l’outil de transfert de contenu. Pour plus d’informations, voir la section [Préparation de la nouvelle définition d’index](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=fr#preparing-the-new-index-definition).

* Si vous avez l’intention d’effectuer des ajouts, il est essentiel que la structure de contenu du contenu existant ne soit pas modifiée du moment où l’extraction initiale est prise au moment de l’exécution de l’extraction de complément. Les cumuls ne peuvent pas être exécutés sur du contenu dont la structure a été modifiée depuis l’extraction initiale. Veillez à limiter cette opération pendant le processus de migration.

* Si vous envisagez d’inclure des versions dans un jeu de migration et que vous effectuez des compléments avec `wipe=false`, vous devez désactiver la purge de version en raison d’une limitation actuelle de l’outil de transfert de contenu. Si vous préférez conserver la purge de version activée et effectuer des compléments dans un jeu de migration, vous devez effectuer l’ingestion sous la forme `wipe=true`.

## Disponibilité {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Télécharger"
>abstract="Il est possible de télécharger l’outil de transfert de contenu dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM). Veillez à télécharger la dernière version."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html" text="Notes de mise à jour"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Portail de distribution de logiciels"

Il est possible de télécharger l’outil de transfert de contenu dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM). Veillez à télécharger la dernière version. Pour plus d’informations sur la dernière version, consultez les [Notes de mise à jour](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

>[!NOTE]
>Téléchargez l’outil de transfert de contenu depuis le portail de [distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## Exécution de l’outil de transfert de contenu {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Exécution de l’outil de transfert de contenu"
>abstract="Découvrez comment utiliser l’outil de transfert de contenu pour effectuer une migration du contenu vers AEM as a Cloud Service (auteur/publication) à l’aide de l’outil de transfert de contenu."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" Voir Démonstration"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=fr#migration" text="Tutoriel – Utilisation de l’outil de transfert de contenu"

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


Consultez cette section pour effectuer une migration du contenu vers AEM as a Cloud Service (auteur/publication) à l’aide de l’outil de transfert de contenu :

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Migration de contenu**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt01.png)

1. Sélectionnez l’option **Transfert de contenu** dans l’assistant **Migration de contenu**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt02.png)


1. La console ci-dessous s’affiche lorsque vous créez le premier jeu de migration. Cliquez sur **Create Migration Set** (Créer un jeu de migration) pour créer un jeu de migration.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt03.png)

   >[!NOTE]
   >Si vous disposez de jeux de migration, la console affiche la liste de ces jeux avec leur état actuel.


1. Renseignez les champs de l’écran **Créer un jeu de migration** comme décrit ci-dessous.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt04.png)

   1. **Name** : renseignez le nom du jeu de migration.
      >[!NOTE]
      >Aucun caractère spécial n’est autorisé dans ce nom.

   1. **Cloud Service Configuration** : renseignez l’URL de destination d’auteur AEM as a Cloud Service.

      >[!NOTE]
      >Vous pouvez créer et gérer un maximum de dix jeux de migration à la fois pendant l’activité de transfert de contenu.
      >En outre, vous devez créer une migration distincte pour chacun des environnements spécifiques : *Stage* (Évaluation), *Development* (Développement) ou *Production*.

   1. **Access Token** : renseignez le jeton d’accès.

      >[!NOTE]
      >Vous pouvez récupérer le jeton d’accès à l’aide du bouton **Open access token** (Ouvrir le jeton d’accès). Vous devez vous assurer que vous appartenez au groupe d’administrateurs AEM dans l’instance Cloud Service cible.

   1. **Parameters** : sélectionnez les paramètres suivants pour créer le jeu de migration :

      1. **Include version** : sélectionnez les options requises. Lorsque des versions sont incluses, le chemin `/var/audit` est automatiquement inclus pour migrer les événements de contrôle.

      ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt05.png)

      >[!NOTE]
      >Si vous envisagez d’inclure des versions dans un jeu de migration et que vous effectuez des compléments avec `wipe=false`, vous devez désactiver la purge de version en raison d’une limitation actuelle de l’outil de transfert de contenu. Si vous préférez conserver la purge de version activée et effectuer des compléments dans un jeu de migration, vous devez effectuer l’ingestion sous la forme `wipe=true`.

      1. **Inclure le mappage des utilisateurs à partir des utilisateurs et groupes IMS** : sélectionnez l’option permettant d’inclure le mappage à partir des utilisateurs et groupes IMS.
Pour plus d’informations, consultez [Outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr).

      1. **Paths to be included** : utilisez le navigateur de chemins pour sélectionner les chemins objets de la migration. Le sélecteur de chemin accepte les entrées effectuées par saisie ou par sélection.

         >[!IMPORTANT]
         >Les chemins suivants sont restreints lors de la création d’un jeu de migration :
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc` (il est possible de sélectionner certains chemins `/etc` dans le CTT)




1. Cliquez sur **Enregistrer** après avoir rempli tous les champs de l’écran **Créer un jeu de migration**.

1. Vous voyez alors le jeu de migration défini dans la page *Overview* (Aperçu).

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/04-item-selection-and-quick-actions.png)

   Tous les jeux de migration existants de cet écran s’affichent sur la page *Aperçu* avec leur état actuel et les informations correspondantes. Certaines des icônes décrites ci-dessous peuvent apparaître.

   * Un *nuage de couleur rouge* indique que vous ne pouvez pas terminer le processus d’extraction.
   * Un *nuage de couleur verte* indique que vous pouvez terminer le processus d’extraction.
   * Une *icône de couleur jaune* indique que vous n’avez pas créé le jeu de migration existant et que celui ainsi indiqué a été créé par un autre utilisateur de la même instance.

1. Sélectionnez un jeu de migration dans la page d’aperçu, puis cliquez sur **Properties** pour voir ou modifier les propriétés du jeu de migration. Lors de la modification des propriétés, il n’est pas possible de changer le nom du conteneur ou l’URL du service.


### Processus d’extraction au cours du transfert de contenu {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Extraction de contenu"
>abstract="L’extraction fait référence à l’extraction de contenu de l’instance AEM source dans une zone temporaire appelée jeu de migration. Un jeu de migration est un espace de stockage cloud fourni par Adobe pour stocker temporairement le contenu transféré entre l’instance AEM source et l’instance AEM Cloud Service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-extraction-process" text="Extraction de complément"

Pour extraire votre jeu de migration à partir de l’outil de transfert de contenu, procédez comme suit :
>[!NOTE]
>Si Amazon S3 ou Azure Data Store est utilisé comme type d’entrepôt de données, vous pouvez exécuter l’étape facultative de précopie afin d’accélérer considérablement la phase d’extraction. Pour ce faire, vous devez configurer un fichier `azcopy.config` avant d’exécuter l’extraction. Pour plus d’informations, voir [Gestion des référentiels de contenu volumineux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) .

1. Pour démarrer l’extraction, sélectionnez un jeu de migration dans la page *Overview*, puis cliquez sur **Extract**. La boîte de dialogue **Migration Set extraction** (Extraction du jeu de migration) s’affiche. Cliquez sur **Extract** pour démarrer la phase d’extraction.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/06-content-extraction.png)

   >[!NOTE]
   >Vous avez la possibilité de remplacer le conteneur d’évaluation pendant la phase d’extraction.


1. Le champ **EXTRACTION** affiche désormais l’état **RUNNING** pour indiquer que l’extraction est en cours d’exécution.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/07-extraction-job-running.png)

   Une fois l’extraction terminée, l’état du jeu de migration est mis à jour sur **FINISHED** (TERMINÉ) et une icône représentant un nuage *vert uni* s’affiche sous le champ **INFO**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/10-extraction-complete.png)

   >[!NOTE]
   >L’IU dispose d’une fonction de rechargement automatique qui recharge la page d’aperçu toutes les 30 secondes.
   >Lorsque la phase d’extraction est lancée, un verrou d’écriture est créé et libéré au-delà de *60 secondes*. Si une extraction est arrêtée, vous devez donc attendre une minute pour que le verrou soit libéré avant de recommencer.

#### Extraction de complément {#top-up-extraction-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.
>En outre, il est essentiel que la structure de contenu du contenu existant ne soit pas modifiée du moment où l’extraction initiale est prise au moment de l’exécution de l’extraction de complément. Les cumuls ne peuvent pas être exécutés sur du contenu dont la structure a été modifiée depuis l’extraction initiale. Veillez à limiter cette opération pendant le processus de migration.

Une fois le processus d’extraction terminé, vous pouvez transférer le contenu différentiel à l’aide de la méthode d’extraction de complément. Suivez les étapes ci-dessous :

1. Accédez à la page *Overview* et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’extraction de complément. Cliquez sur **Extract** pour démarrer l’extraction de complément. La boîte de dialogue **Migration Set extraction** (Extraction du jeu de migration) s’affiche.

   >[!IMPORTANT]
   >
   >Il est préférable de désactiver l’option **Overwrite staging container during extraction** (Remplacer le conteneur d’évaluation pendant l’extraction).
   >
   >![image](/help/move-to-cloud-service/content-transfer-tool/assets/11-topup-extraction.png)

### Processus d’ingestion au cours du transfert de contenu {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Ingestion de contenu"
>abstract="L’ingestion désigne l’ingestion de contenu à partir du jeu de migration dans l’instance Cloud Service cible. L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-ingestion-process" text="Ingestion de complément"

Pour ingérer le jeu de migration obtenu à l’aide de l’outil de transfert de contenu, procédez comme suit :
>[!NOTE]
>Si Amazon S3 ou Azure Data Store est utilisé comme type d’entrepôt de données, vous pouvez exécuter l’étape facultative de précopie afin d’accélérer considérablement la phase d’ingestion. Pour plus d’informations, voir [Ingestion avec AzCopy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#ingesting-azcopy) .

1. Sélectionnez un jeu de migration à partir de la page *Overview* et cliquez sur **Ingest** pour commencer l’ingestion. La boîte de dialogue **Migration Set ingestion** (Ingestion du jeu de migration) s’affiche. Le contenu peut être ingéré simultanément sur l’instance d’auteur ou l’instance de publication. Sélectionnez l’instance à laquelle ingérer le contenu. Cliquez sur **Ingest** pour démarrer la phase d’ingestion.

   >[!IMPORTANT]
   >Si l’ingestion avec une précopie est utilisée (pour S3 ou Azure Data Store), il est recommandé d’exécuter l’ingestion par l’auteur en premier seul. Cela permettra d’accélérer l’ingestion de publication lorsqu’elle est exécutée ultérieurement.

   >[!IMPORTANT]
   >Lorsque l’option **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est activée, elle supprime l’intégralité du référentiel existant et crée un référentiel dans lequel intégrer du contenu. Cela signifie que tous les paramètres sont réinitialisés, y compris les autorisations relatives à l’instance Cloud Service cible. C’est également vrai pour un utilisateur administrateur ajouté au groupe **administrateurs**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-03.png)

   De plus, cliquez sur **Assistance clientèle** pour enregistrer un ticket, comme le montre la figure ci-dessus. Consultez également [Points importants concernant l’utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs) pour en savoir plus.

1. Une fois l’ingestion terminée, l’état est mis à jour vers **FINISHED**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/15-ingestion-complete.png)

#### Ingestion de complément {#top-up-ingestion-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un *complément* de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.

Une fois le processus d’ingestion terminé, vous pouvez utiliser le contenu différentiel à l’aide de la méthode d’ingestion de complément. Suivez les étapes ci-dessous :

1. Accédez à la page *Overview* et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’ingestion de complément. Cliquez sur **Ingest** pour démarrer l’extraction de complément. La boîte de dialogue **Migration Set ingestion** (Ingestion du jeu de migration) s’affiche.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-02.png)

   >[!IMPORTANT]
   >Vous devez désactiver l’option **Effacer le contenu existant sur l’instance cloud avant l’ingestion** pour empêcher la suppression du contenu existant de l’activité d’ingestion précédente. De plus, cliquez sur **Assistance clientèle** pour enregistrer un ticket, comme le montre la figure précédente.


### Affichage des journaux d’un jeu de migration {#viewing-logs-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="Affichage des journaux"
>abstract="Une fois l’extraction de l’ingestion terminée, recherchez dans les journaux les erreurs/avertissements éventuels. Toute erreur doit être corrigée immédiatement soit en traitant les problèmes signalés, soit en contactant l’assistance d’Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#troubleshooting" text="Résolution des problèmes"
>additional-url="https://helpx.adobe.com/fr/enterprise/admin-guide.html/fr/enterprise/using/support-for-experience-cloud.ug.html" text="Contacter le support technique d’Adobe"

Une fois chaque étape terminée (extraction et ingestion), vérifiez les journaux et recherchez les erreurs.  Toute erreur doit être corrigée immédiatement soit en traitant les problèmes signalés, soit en contactant l’assistance d’Adobe.

Vous pouvez afficher les journaux d’un jeu de migration existant à l’aide de la page *Overview*.
Suivez les étapes ci-dessous :

1. Accédez à la page *Overview*, sélectionnez le jeu de migration à supprimer, puis cliquez sur l’option **View Log** (Afficher le journal) dans la barre d’actions.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log1.png)

1. La boîte de dialogue **Logs** (Journaux) s’affiche. Cliquez sur **Extraction Logs** (Journaux d’extraction) pour voir les journaux dans un nouvel onglet.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log2.png)
ou,

   Vous pouvez également voir les journaux de votre jeu de migration à l’aide de l’écran *Overview*. Sélectionnez le jeu de migration et cliquez sur l’état sous le champ **EXTRACTION**. Dans ce cas, cliquez sur **FINISHED** (TERMINÉ) pour voir les journaux dans un nouvel onglet.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log3.png)

1. Pour consulter les dernières lignes des journaux sans utiliser l’interface utilisateur, vous pouvez vous connecter à votre environnement AEM source via SSH et exécuter la commande tail sur le fichier `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`.

### Suppression d’un jeu de migration {#deleting-migration-set}

Vous pouvez supprimer le jeu de migration de la page *Overview*.
Suivez les étapes ci-dessous :

1. Accédez à la page *Overview*, sélectionnez le jeu de migration à supprimer, puis cliquez sur **Delete** dans la barre d’actions.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/delete-1.png)

1. Cliquez sur **Delete** dans la boîte de dialogue **Delete Migration Set** pour confirmer la suppression.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/delete-3.png)


## Exécution de l’outil de transfert de contenu sur une instance de publication {#running-ctt-on-publish}

Il est recommandé que lors du déplacement du contenu vers une instance de publication, CTT soit installé sur l’instance de publication source pour déplacer le contenu vers l’instance de publication cible. Suivez l’approche recommandée, comme décrit ci-dessous :

* Utilisez la même version du CTT que celle utilisée sur l’instance d’auteur.

* Un seul noeud de publication doit être migré. Il doit être supprimé de l’équilibreur de charge avant de commencer l’extraction.

* Lors de la création du jeu de migration, utilisez l’URL de l’environnement AEMaaCS de création.

* Lors de l’ingestion pour la publication, le niveau de publication ne sera PAS réduit (contrairement à l’auteur). Par mesure de précaution, évitez les opérations d’écriture initiées par l’utilisateur, telles que :

   * Distribution de contenu de l’auteur AEMaaCS à la publication dans cet environnement
   * Synchronisation des utilisateurs entre les instances de publication


## Résolution des problèmes {#troubleshooting}

### ID d’objets blob manquants {#missing-blobs}

Si l’absence d’ID d’objets blob est signalée, comme indiqué ci-dessous, il est nécessaire d’exécuter une vérification de cohérence du référentiel existant et de restaurer les blobs manquants.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

La commande suivante est exécutée

>[!NOTE]
>
>`--verbose`(indicateur) est nécessaire pour signaler les chemins d’accès aux nœuds permettant de référencer les objets blob.

**Pour les référentiels AEM 6.5 (Oak 1.8 et versions antérieures)**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Pour les référentiels dotés d’Oak > 1.10**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

Pour plus d’informations, voir [Fichier jar exécutable Oak](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run).

Les fichiers créés dans *OUT_DIR*, spécifiés ci-dessus pour assurer la cohérence, peuvent ensuite être vérifiés pour détecter les chemins manquants de binaires et les actions appropriées mises en œuvre (restauration à partir d’une sauvegarde, suppression des chemins, réindexation, etc.).


### Comportement de l’interface utilisateur {#ui-behavior}

En tant qu’utilisateur, il est possible que vous constatiez les changements de comportement suivants dans l’interface utilisateur de l’outil de transfert de contenu :

* Selon la version de l’instance AEM source, les icônes de l’interface utilisateur de l’outil de transfert de contenu peuvent apparaître sous des formes différentes des captures d’écran de ce guide ou ne pas apparaître du tout.
