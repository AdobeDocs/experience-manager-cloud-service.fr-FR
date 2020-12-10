---
title: Utilisation de l’outil de transfert de contenu
description: Utilisation de l’outil de transfert de contenu
translation-type: tm+mt
source-git-commit: f3a4fdf57dc84bba9811530fccb2fe6a4404376f
workflow-type: tm+mt
source-wordcount: '1902'
ht-degree: 89%

---


# Utilisation de l’outil de transfert de contenu {#using-content-transfer-tool}

## Points importants concernant l’utilisation de l’outil de transfert de contenu {#pre-reqs}

Consultez la section ci-dessous afin de comprendre les points importants à prendre en compte pour l’exécution de l’outil de transfert de contenu :

* La configuration minimale requise pour l’outil de transfert de contenu est AEM 6.3+ et JAVA 8. Si vous utilisez une version antérieure d’AEM, vous devrez mettre à niveau votre référentiel de contenu à la version AEM 6.5 pour utiliser l’outil de transfert de contenu.

* Java doit être configuré dans l’environnement AEM, de sorte que la commande `java` puisse être exécutée par l’utilisateur démarrant AEM.

* L’outil de transfert de contenu peut être utilisé avec les types de magasin de données suivants : File Data Store, S3 Data Store, Shared S3 Data Store et Azure Blob Store Data Store.

* Si vous utilisez un *environnement sandbox*, assurez-vous que celui-ci est à jour et mis à niveau vers la dernière version. Si vous utilisez un *environnement de production*, il est automatiquement mis à jour.

* Pour utiliser l’outil de transfert de contenu, vous devez être un utilisateur administrateur sur votre instance source et appartenir au groupe d’administrateurs AEM local dans l’instance Cloud Service vers laquelle vous transférez du contenu. Les utilisateurs non privilégiés ne pourront pas récupérer le jeton d’accès pour utiliser l’outil de transfert de contenu.

* Actuellement, la taille par défaut de MongoDB pour une instance AEM as a Cloud Service est de 32 Go. Pour une taille de banque de segments supérieure à 20 Go, envoyez un ticket d’assistance demandant à augmenter la taille de MongoDB.

* Les utilisateurs et groupes transférés par l’outil de transfert de contenu sont uniquement ceux qui sont requis par le contenu pour satisfaire aux autorisations. Le processus *Extraction* copie l&#39;ensemble `/home` dans le jeu de migration et le processus *Ingestion* copie tous les utilisateurs et groupes référencés dans les listes de contrôle d&#39;accès du contenu migré.

* Pendant la phase d’extraction, l’outil de transfert de contenu est exécuté sur une instance source AEM active.

* Après avoir terminé la phase *Extraction* du processus de transfert de contenu et avant de commencer la phase *d&#39;importation* pour ingérer du contenu dans votre AEM en tant que Cloud Service *Stage* ou *Production*, vous devez enregistrer un ticket d&#39;assistance pour informer l&#39;Adobe de votre intention d&#39;exécuter *Production gestion* afin que l&#39;Adobe puisse s&#39;assurer qu&#39;aucune interruption ne se produit pendant le processus *Ingestion*. Vous devrez consigner le ticket de support 1 semaine avant la date *d&#39;importation* prévue. Une fois que vous avez soumis le ticket d&#39;assistance, l&#39;équipe d&#39;assistance vous donnera des conseils sur les étapes suivantes.
   * Enregistrez un ticket d&#39;assistance avec les détails suivants :
      * Date exacte et heure estimée (avec votre fuseau horaire) lorsque vous prévoyez de début de la phase *Ingestion*.
      * Type d’Environnement (Phase ou Production) dans lequel vous prévoyez d’importer des données.
      * ID de programme.

* La *phase d’ingestion* de l’auteur réduira l’ensemble du déploiement de l’auteur. L’auteur AEM ne sera donc pas disponible pendant la totalité du processus d’ingestion. Assurez-vous également qu’aucun pipeline Cloud Manager n’est exécuté pendant que vous exécutez la phase *Ingestion*.


## Disponibilité {#availability}

Il est possible de télécharger l’outil de transfert de contenu dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais de Package Manager sur votre instance source Adobe Experience Manager (AEM). Veillez à télécharger la dernière version. Pour plus d’informations sur la dernière version, consultez les [Notes de mise à jour](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

>[!NOTE]
>Téléchargez l’outil de transfert de contenu depuis le portail de [distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## Exécution de l’outil de transfert de contenu {#running-tool}

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


Consultez cette section pour effectuer une migration du contenu vers AEM as a Cloud Service (auteur/publication) à l’aide de l’outil de transfert de contenu :

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Content Transfer** (Transfert de contenu).

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content1.png)

1. La console ci-dessous s’affiche lorsque vous créez le premier jeu de migration. Cliquez sur **Create Migration Set** (Créer un jeu de migration) pour créer un jeu de migration.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/01-migration-set-overview.png)

   >[!NOTE]
   >Si vous disposez de jeux de migration, la console affiche la liste de ces jeux avec leur état actuel.

1. Renseignez les champs de l’écran **Content Migrations Set details** (Détails du jeu de migration de contenu), comme décrit ci-dessous.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/02-migration-set-creation.png)


   1. **Name** : renseignez le nom du jeu de migration.
      >[!NOTE]
      >Aucun caractère spécial n’est autorisé dans ce nom.

   1. **Cloud Service Configuration** : renseignez l’URL de destination d’auteur AEM as a Cloud Service.

      >[!NOTE]
      >Vous pouvez créer et gérer un maximum de quatre jeux de migration à la fois pendant l’activité de transfert de contenu.
      >En outre, vous devez créer une migration distincte pour chacun des environnements spécifiques : *Stage* (Évaluation), *Development* (Développement) ou *Production*.

   1. **Access Token** : renseignez le jeton d’accès.

      >[!NOTE]
      >Vous pouvez récupérer le jeton d’accès à l’aide du bouton **Open access token** (Ouvrir le jeton d’accès). Vous devez vous assurer que vous appartenez au groupe d’administrateurs AEM dans l’instance Cloud Service cible.

   1. **Parameters** : sélectionnez les paramètres suivants pour créer le jeu de migration :

      1. **Include version** : sélectionnez les options requises.

      1. **Paths to be included** : utilisez le navigateur de chemins pour sélectionner les chemins objets de la migration. Le sélecteur de chemin accepte les entrées effectuées par saisie ou par sélection.

         >[!IMPORTANT]
         >Les chemins suivants sont restreints lors de la création d’un jeu de migration :
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc`


1. Cliquez sur **Save** après avoir rempli tous les champs de l’écran **Content Migrations Set details**.

1. Vous voyez alors le jeu de migration défini dans la page *Overview* (Aperçu).

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/04-item-selection-and-quick-actions.png)

   Tous les jeux de migration existants de cet écran s’affichent sur la page *Overview* avec leur état actuel et les informations correspondantes. Certaines des icônes décrites ci-dessous peuvent apparaître.

   * Un *nuage de couleur rouge* indique que vous ne pouvez pas terminer le processus d’extraction.
   * Un *nuage de couleur verte* indique que vous pouvez terminer le processus d’extraction.
   * Une *icône de couleur jaune* indique que vous n’avez pas créé le jeu de migration existant et que celui ainsi indiqué a été créé par un autre utilisateur de la même instance.

1. Sélectionnez un jeu de migration dans la page d’aperçu, puis cliquez sur **Properties** pour voir ou modifier les propriétés du jeu de migration. Lors de la modification des propriétés, il n’est pas possible de changer le nom du conteneur ou l’URL du service.



### Processus d’extraction au cours du transfert de contenu {#extraction-process}

Pour extraire votre jeu de migration à partir de l’outil de transfert de contenu, procédez comme suit :

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

Une fois le processus d’extraction terminé, vous pouvez transférer le contenu différentiel à l’aide de la méthode d’extraction de complément. Suivez les étapes ci-dessous :

1. Accédez à la page *Overview* et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’extraction de complément. Cliquez sur **Extract** pour démarrer l’extraction de complément. La boîte de dialogue **Migration Set extraction** (Extraction du jeu de migration) s’affiche.

   >[!IMPORTANT]
   >
   >Il est préférable de désactiver l’option **Overwrite staging container during extraction** (Remplacer le conteneur d’évaluation pendant l’extraction).
   >
   >![image](/help/move-to-cloud-service/content-transfer-tool/assets/11-topup-extraction.png)

### Processus d’ingestion au cours du transfert de contenu {#ingestion-process}

Pour ingérer le jeu de migration obtenu à l’aide de l’outil de transfert de contenu, procédez comme suit :

1. Pour démarrer l’extraction, sélectionnez un jeu de migration dans la page *Overview*, puis cliquez sur **Ingest** (Ingérer). La boîte de dialogue **Migration Set ingestion** (Ingestion du jeu de migration) s’affiche. Cliquez sur **Ingest** pour démarrer la phase d’ingestion. Pour une démonstration, l’option **Ingest content to Author instance** (Ingérer du contenu vers l’instance d’auteur) est désactivée. Il est possible d’ingérer en même temps du contenu vers les instances d’auteur et de publication.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/12-content-ingestion.png)

1. Une fois l’ingestion terminée, l’état du champ **PUBLISH INGESTION** passe à **FINISHED**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/15-ingestion-complete.png)

#### Ingestion de complément {#top-up-ingestion-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un *complément* de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.

Une fois le processus d’ingestion terminé, vous pouvez utiliser le contenu différentiel à l’aide de la méthode d’ingestion de complément. Suivez les étapes ci-dessous :

1. Accédez à la page *Overview* et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’ingestion de complément. Cliquez sur **Ingest** pour démarrer l’extraction de complément. La boîte de dialogue **Migration Set ingestion** (Ingestion du jeu de migration) s’affiche.

   >[!IMPORTANT]
   >
   >Vous devez désactiver l’option **Wipe existing content on Cloud instance before ingestion** (Effacer le contenu existant sur l’instance cloud avant l’ingestion) pour empêcher la suppression du contenu existant de l’activité d’ingestion précédente.
   >
   >![image](/help/move-to-cloud-service/content-transfer-tool/assets/16-topup-ingestion.png)

### Affichage des journaux d’un jeu de migration {#viewing-logs-migration-set}

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

## Résolution des incidents {#troubleshooting}

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

* L’utilisateur crée un jeu de migration pour une URL d’auteur (Développement/Évaluation/Production) et effectue avec succès l’extraction et l’ingestion.

* L’utilisateur crée ensuite un jeu de migration pour la même URL d’auteur et effectue l’extraction et l’ingestion sur le nouveau jeu de migration. L’interface utilisateur indique que l’état d’ingestion du premier jeu de migration devient **ÉCHEC** et qu’aucun journal n’est disponible.

* Cela ne signifie pas que l’ingestion du premier jeu de migration a échoué. Ce comportement apparaît, car lorsqu’une nouvelle tâche d’ingestion est lancée, elle supprime la tâche d’ingestion précédente. L’état des modifications du premier jeu de migration doit donc être ignoré.

* Selon la version de l’instance AEM source, les icônes de l’interface utilisateur de l’outil de transfert de contenu peuvent apparaître sous des formes différentes des captures d’écran de ce guide ou ne pas apparaître du tout.


