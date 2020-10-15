---
title: Utilisation de l’outil de transfert de contenu
description: Utilisation de l’outil de transfert de contenu
translation-type: tm+mt
source-git-commit: e96ffc15849baa306fae8839476fa453ace69ef5
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 78%

---


# Utilisation de l’outil de transfert de contenu {#using-content-transfer-tool}

## Points importants concernant l’utilisation de l’outil de transfert de contenu {#pre-reqs}

Consultez la section ci-dessous afin de comprendre les points importants à prendre en compte pour l’exécution de l’outil de transfert de contenu :

* La configuration minimale requise pour l’outil de transfert de contenu est AEM 6.3+ et JAVA 8. Si vous utilisez une version antérieure d’AEM, vous devrez mettre à niveau votre référentiel de contenu à la version AEM 6.5 pour utiliser l’outil de transfert de contenu.

* Java doit être configuré sur l’environnement AEM, de sorte que la `java` commande puisse être exécutée par l’utilisateur qui a début AEM.

* L’outil de transfert de contenu peut être utilisé avec les types de stockage de données suivants : File Data Store, S3 Data Store, Shared S3 Data Store et Azure Blob Store Data Store.

* Si vous utilisez un Environnement ** Sandbox, assurez-vous que votre environnement est à jour et mis à niveau vers la dernière version. Si vous utilisez un *environnement de production*, il est automatiquement mis à jour.

* Pour utiliser l’outil de transfert de contenu, vous devez être un utilisateur administrateur sur votre instance source et appartenir au groupe d’administrateurs AEM locaux dans l’instance de Cloud Service à laquelle vous transférez du contenu. Les utilisateurs non privilégiés ne pourront pas récupérer le jeton d’accès pour utiliser l’outil de transfert de contenu.

* Pendant la phase d’extraction, l’outil de transfert de contenu est exécuté sur une instance source AEM active.

* La *phase d’ingestion* de l’auteur réduira l’ensemble du déploiement de l’auteur. L’auteur AEM ne sera donc pas disponible pendant la totalité du processus d’ingestion.

* Actuellement, la taille de MongoDB par défaut pour un AEM en tant qu’instance d’auteur Cloud Service est de 32 Go. Pour une taille de stockage de segments supérieure à 20 Go, il est recommandé d’envoyer un ticket d’assistance afin d’augmenter la taille de MongoDB.

## Disponibilité {#availability}

L&#39;outil de transfert de contenu peut être téléchargé dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM). Veillez à télécharger la dernière version. Pour plus d’informations sur la dernière version, consultez les Notes [de](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html)mise à jour.

>[!NOTE]
>Téléchargez l’outil de transfert de contenu depuis le portail de [distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## Exécution de l’outil de transfert de contenu {#running-tool}

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)

Consultez cette section pour effectuer une migration du contenu vers AEM as a Cloud Service (auteur/publication) à l’aide de l’outil de transfert de contenu :

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Transfert de contenu**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content1.png)

1. La console ci-dessous s’affiche lorsque vous créez le premier jeu de migration. Cliquez sur **Créer un jeu de migration** pour créer un jeu de migration.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/01-migration-set-overview.png)

   >[!NOTE]
   >Si vous avez des jeux de migration existants, la console affiche la liste des jeux de migration existants avec leur état actuel.

1. Renseignez les champs de l’écran **Détails du jeu de migration de contenu**, comme décrit ci-dessous.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/02-migration-set-creation.png)


   1. **Nom** : renseignez le nom du jeu de migration.
      >[!NOTE]
      >Aucun caractère spécial n’est autorisé dans ce nom.

   1. **Configuration du service cloud** : renseignez l’URL de destination d’auteur AEM as a Cloud Service.

      >[!NOTE]
      >Vous pouvez créer et gérer un maximum de quatre jeux de migration à la fois pendant l’activité de transfert de contenu.
      >En outre, vous devez créer une migration distincte pour chacun des environnements spécifiques : *Évaluation*, *Développement* ou *Production*.

   1. **Jeton d’accès** : renseignez le jeton d’accès.

      >[!NOTE]
      >Vous pouvez récupérer le jeton d&#39;accès à l’aide du bouton **Ouvrir le jeton d&#39;accès** . Vous devez vous assurer que vous appartenez au groupe d’administrateurs AEM dans l’instance de Cloud Service de cible.

   1. **Paramètres** : sélectionnez les paramètres suivants pour créer le jeu de migration :

      1. **Inclure la version** : sélectionnez les options requises.

      1. **Chemins à inclure** : utilisez le navigateur de chemins pour sélectionner les chemins objets de la migration. Le sélecteur de chemins accepte les entrées en saisissant ou en sélectionnant.

         >[!IMPORTANT]
         >Les chemins suivants sont restreints lors de la création d’un jeu de migration :
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc`


1. Cliquez sur **Enregistrer** après avoir rempli tous les champs de l’écran **Détails du jeu de migration de contenu**.

1. Vous voyez alors le jeu de migration défini dans la page *Aperçu*.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/04-item-selection-and-quick-actions.png)

   Tous les jeux de migration existants de cet écran s’affichent sur la page *Aperçu* avec leur état actuel et les informations correspondantes. Vous pouvez voir certaines de ces icônes décrites ci-dessous.

   * Un *nuage de couleur rouge* indique que vous ne pouvez pas terminer le processus d’extraction.
   * Un *nuage de couleur verte* indique que vous pouvez terminer le processus d’extraction.
   * Une *icône de couleur jaune* indique que vous n’avez pas créé le jeu de migration existant et que celui ainsi indiqué a été créé par un autre utilisateur de la même instance.

1. Sélectionnez un jeu de migration dans la page d’aperçu, puis cliquez sur **Propriétés** pour voir ou modifier les propriétés du jeu de migration. Lors de la modification des propriétés, il n’est pas possible de modifier le nom du conteneur ou l’URL du service.



### Processus d’extraction au cours du transfert de contenu {#extraction-process}

Pour extraire votre jeu de migration à partir de l’outil de transfert de contenu, procédez comme suit :

1. Pour démarrer l’extraction, sélectionnez un jeu de migration dans la page *Aperçu*, puis cliquez sur **Extraire.** The **Migration Set extraction** dialog box displays and click on **Extract** to start the extraction phase.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/06-content-extraction.png)

   >[!NOTE]
   >Vous avez la possibilité de remplacer le conteneur d’évaluation pendant la phase d’extraction.


1. Le champ **EXTRACTION** affiche désormais l’état **EN COURS** pour indiquer que l’extraction est en cours d’exécution.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/07-extraction-job-running.png)

   Une fois l’extraction terminée, l’état du jeu de migration est mis à jour sur **TERMINÉ** et une icône représentant un nuage *vert uni* s’affiche sous le champ **INFO**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/10-extraction-complete.png)

   >[!NOTE]
   >L’interface utilisateur dispose d’une fonction de rechargement automatique qui recharge la page d’aperçu toutes les 30 secondes.
   >Lorsque la phase d’extraction est lancée, un verrou d’écriture est créé et libéré au-delà de *60 secondes*. Si une extraction est arrêtée, vous devez donc attendre une minute pour que le verrou soit libéré avant de recommencer.

#### Extraction de complément {#top-up-extraction-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.

Une fois le processus d’extraction terminé, vous pouvez transférer le contenu différentiel à l’aide de la méthode d’extraction de complément. Suivez les étapes ci-dessous :

1. Accédez à la page *Aperçu* et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’extraction de complément. Cliquez sur **Extraire** pour démarrer l’extraction de complément. La boîte de dialogue **Extraction du jeu de migration** s’affiche.

   >[!IMPORTANT]
   >
   >Il est préférable de désactiver l’option **Remplacer le conteneur d’évaluation pendant l’extraction**.
   >
   >![image](/help/move-to-cloud-service/content-transfer-tool/assets/11-topup-extraction.png)

### Processus d’ingestion au cours du transfert de contenu {#ingestion-process}

Pour ingérer le jeu de migration obtenu à l’aide de l’outil de transfert de contenu, procédez comme suit :

1. Pour démarrer l’extraction, sélectionnez un jeu de migration dans la page *Aperçu*, puis cliquez sur **Ingérer.** La boîte de dialogue **Ingestion du jeu de migration** s’affiche. Click on **Ingest** to start the ingestion phase. Pour une démonstration, l’option **Ingérer du contenu avec l’instance d’auteur** est désactivée. Il est possible d’ingérer en même temps du contenu avec l’instance d’auteur et de publication.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/12-content-ingestion.png)

1. Une fois l’assimilation terminée, l’état du champ **PUBLIER L’INGESTION** se met à jour pour **TERMINER**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/15-ingestion-complete.png)

#### Ingestion de complément {#top-up-ingestion-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un *complément* de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.

Une fois le processus d’ingestion terminé, vous pouvez utiliser le contenu différentiel à l’aide de la méthode d’ingestion de complément. Suivez les étapes ci-dessous :

1. Accédez à la page *Aperçu* et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’ingestion de complément. Cliquez sur **Ingérer** pour démarrer l’extraction de complément. La boîte de dialogue **Ingestion du jeu de migration** s’affiche.

   >[!IMPORTANT]
   >
   >Vous devez désactiver l’option **Balayer le contenu existant sur l’instance Cloud avant l’assimilation** , afin d’empêcher la suppression du contenu existant de l’activité d’assimilation précédente.
   >
   >![image](/help/move-to-cloud-service/content-transfer-tool/assets/16-topup-ingestion.png)

### Affichage des journaux d’un jeu de migration {#viewing-logs-migration-set}

Vous pouvez afficher les journaux d’un jeu de migration existant à l’aide de la page *Aperçu*.
Suivez les étapes ci-dessous :

1. Accédez à la page *Aperçu*, sélectionnez le jeu de migration à supprimer, puis cliquez sur l’option **Afficher le journal** dans la barre d’actions.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log1.png)

1. La boîte de dialogue **Journaux** s’affiche. Cliquez sur **Journaux d’extraction** pour voir les journaux dans un nouvel onglet.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log2.png)
ou,

   Vous pouvez également voir les journaux de votre jeu de migration à l’aide de l’écran *Aperçu*. Sélectionnez le jeu de migration et cliquez sur l’état sous le champ **EXTRACTION**. Dans ce cas, cliquez sur **TERMINÉ** pour voir les journaux dans un nouvel onglet.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log3.png)

1. Pour consulter les dernières lignes des journaux sans utiliser l’interface utilisateur, vous pouvez vous connecter à votre environnement AEM source via SSH et exécuter la commande tail sur le fichier `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`.

### Suppression d’un jeu de migration {#deleting-migration-set}

Vous pouvez supprimer le jeu de migration de la page *Aperçu*.
Suivez les étapes ci-dessous :

1. Accédez à la page *Aperçu*, sélectionnez le jeu de migration à supprimer, puis cliquez sur **Supprimer** dans la barre d’actions.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/delete-1.png)

1. Cliquez sur **Supprimer** dans la boîte de dialogue **Supprimer le jeu de migration** pour confirmer la suppression.

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


