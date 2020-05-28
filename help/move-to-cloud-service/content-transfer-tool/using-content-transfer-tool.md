---
title: Utilisation de l’outil de transfert de contenu
description: Utilisation de l’outil de transfert de contenu
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '1412'
ht-degree: 3%

---


# Utilisation de l’outil de transfert de contenu {#using-content-transfer-tool}

## Considérations importantes concernant l’utilisation de l’outil de transfert de contenu {#pre-reqs}

Suivez la section ci-dessous pour comprendre les points importants à prendre en compte lors de l’exécution de l’outil de transfert de contenu :

* La configuration minimale requise pour l’outil de transfert de contenu est AEM 6.3 + et JAVA 8. Si vous utilisez une version AEM inférieure, vous devrez mettre à niveau votre référentiel de contenu vers AEM 6.5 pour utiliser l’outil de transfert de contenu.

* Si vous utilisez un Environnement ** Sandbox, veillez à ce que votre environnement soit mis à niveau vers la version du 29 mai 2020 ou une version ultérieure. Si vous utilisez un Environnement *de* production, il est automatiquement mis à jour.

* Pendant la phase d’extraction, l’outil de transfert de contenu est exécuté sur une instance source AEM active.

* La phase ** d&#39;importation pour l&#39;auteur réduira le déploiement de l&#39;auteur dans son ensemble. Cela signifie que l’auteur AEM ne sera pas disponible pendant l’ensemble du processus d’assimilation.

## Disponibilité {#availability}

L&#39;outil de transfert de contenu peut être téléchargé dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le package via Package Manager sur votre instance source Adobe Experience Manager (AEM).

>[!NOTE]
>Consultez [Accès à AEM en tant que SDK](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html#accessing-the-aem-as-a-cloud-service-sdk) de service Cloud pour plus d’informations.

## Exécution de l’outil de transfert de contenu {#running-tool}

Suivez cette section pour savoir comment utiliser l’outil de transfert de contenu pour migrer le contenu vers AEM as a Cloud Service (Auteur/Publier) :

1. Sélectionnez Adobe Experience Manager et accédez aux outils -> **Opérations** -> Transfert **de** contenu.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content1.png)

1. Cliquez sur **Créer un jeu** de migration pour créer un jeu de migration. Les détails **du jeu de** migrations de contenu s’affichent.

   >[!NOTE]
   >Vous allez vue les jeux de migration existants sur cet écran avec leur état actuel.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

1. Renseignez les champs de l’écran Détails **du jeu de** migration de contenu, comme décrit ci-dessous.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content-3.png)


   1. **Nom**: Entrez le nom du jeu de migration.
      >[!NOTE]
      >Aucun caractère spécial n’est autorisé pour le nom du jeu de migration.

   1. **Configuration** du service cloud : Saisissez la destination AEM en tant qu’URL d’auteur du service Cloud.

      >[!NOTE]
      >Vous pouvez créer et gérer un maximum de quatre jeux de migration à la fois pendant l’activité de transfert de contenu.
      >En outre, vous devez créer une migration distincte pour chacun des environnements spécifiques - *Phase*, *Développement* ou *Production*.

   1. **Jeton d&#39;accès**: Entrez le jeton d&#39;accès.

      >[!NOTE]
      >Vous pouvez récupérer le jeton d&#39;accès de l’instance d’auteur en accédant à `/libs/granite/migration/token.json`.

   1. **Paramètres**: Sélectionnez les paramètres suivants pour créer le jeu de migration :

      1. **Inclure la version**: Sélectionnez les options requises.

      1. **Chemins à inclure**: Utilisez le navigateur de chemins pour sélectionner les chemins à migrer.

         >[!IMPORTANT]
         >Les chemins suivants sont restreints lors de la création d’un jeu de migration :
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc`


1. Cliquez sur **Enregistrer** une fois que vous avez rempli tous les champs de l’écran Détails **de la visionneuse de migrations de** contenu.

1. Vous allez vue votre jeu de migration dans la page *Aperçu* .

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

   Tous les jeux de migration existants sur cet écran s’affichent sur la page *Aperçu* avec leurs informations d’état et d’état actuelles.

   * Un nuage ** rouge indique que vous ne pouvez pas terminer le processus d’extraction.
   * Un nuage ** vert indique que vous pouvez terminer la procédure d’extraction.
   * Une icône ** jaune indique que vous n’avez pas créé le jeu de migration existant et que celui-ci est créé par un autre utilisateur de la même instance.

1. Sélectionnez un jeu de migration dans la page d’aperçu et cliquez sur **Propriétés** pour vue ou modifier les propriétés du jeu de migration.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img6.png)

### Processus d’Extraction dans le transfert de contenu {#extraction-process}

Pour extraire votre jeu de migration de l’outil de transfert de contenu, procédez comme suit :

1. Sélectionnez un jeu de migration dans la page *Aperçu* et cliquez sur **Extraire** vers l’extraction d’début.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. La boîte de dialogue extraction **du jeu de** migration s’affiche et cliquez sur **Extraction** pour terminer la phase d’extraction.

   >[!NOTE]
   >Vous avez la possibilité de remplacer le conteneur d’évaluation pendant la phase d’extraction.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-2.png)

1. Le champ **EXTRACTION** affiche désormais l’état **EN COURS** pour le processus d’extraction en cours.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-3.png)

   Une fois l’extraction terminée, l’état du jeu de migration se met à jour sur **FINI** et une icône de nuage vert ** plein s’affiche sous le champ **INFO** .

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-4.png)

   >[!NOTE]
   > Vous devrez actualiser la page pour mettre en vue l’état mis à jour.

#### Extraction supérieure {#top-up-extraction-process}

L’outil de transfert de contenu comporte une fonctionnalité qui prend en charge le supplément de contenu différentiel où il est possible de transférer uniquement les modifications effectuées depuis l’activité précédente de transfert de contenu.

>[!NOTE]
>Après le transfert initial de contenu, il est recommandé d’effectuer de fréquents ajouts différentiels de contenu afin de raccourcir la période de gel de contenu pour le transfert différentiel final de contenu avant de passer en ligne sur le service Cloud.

Une fois le processus d’extraction terminé, vous pouvez transférer le contenu delta à l’aide de la méthode d’extraction de transfert. Suivez les étapes ci-dessous :

1. Accédez à la page *Aperçu* et sélectionnez l’ensemble de migration pour lequel vous souhaitez effectuer l’extraction supérieure.

1. Cliquez sur **Extraction** pour début de l’extraction supérieure.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. La boîte de dialogue extraction **du jeu de** migration s’affiche.

   >[!IMPORTANT]
   >Désactivez l’option **Remplacer le conteneur d’évaluation pendant l’extraction** .
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-topup-1.png)

### Processus d&#39;importation dans le transfert de contenu {#ingestion-process}

Suivez les étapes ci-dessous pour assimiler votre jeu de migration à partir de l’outil de transfert de contenu :

1. Sélectionnez un jeu de migration dans la page *Aperçu* , puis cliquez sur **Assimiler** à l’extraction d’début.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. La boîte de dialogue d’assimilation **d’une visionneuse de** migration s’affiche.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-2.png)

   À des fins de démonstration, l’option **Envoi de contenu à l’instance** d’auteur est désactivée. Il est possible d’assimiler du contenu à l’auteur et à la publication en même temps.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-3.png)

   Cliquez sur **Récupérer** pour terminer la phase d&#39;assimilation.

1. Une fois l&#39;assimilation terminée, le statut du champ INGESTION **** AUTEUR est mis à jour pour **FINI** et une icône de nuage vert plein s&#39;affiche sous l&#39; **INFO**.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-4.png)

   >[!NOTE]
   > Vous devrez actualiser la page pour mettre en vue l’état mis à jour.

#### Ingestion globale {#top-up-ingestion-process}

L’outil de transfert de contenu est doté d’une fonctionnalité qui prend en charge le *supplément* de contenu différentiel, où il est possible de transférer uniquement les modifications effectuées depuis l’activité précédente de transfert de contenu.

>[!NOTE]
>Après le transfert initial de contenu, il est recommandé d’effectuer de fréquents ajouts différentiels de contenu afin de raccourcir la période de gel de contenu pour le transfert différentiel final de contenu avant de passer en ligne sur le service Cloud.

Une fois le processus d’assimilation terminé, vous pouvez utiliser le contenu delta, en utilisant la méthode d’assimilation supérieure. Suivez les étapes ci-dessous :

1. Accédez à la page *Aperçu* et sélectionnez le jeu de migration pour lequel vous souhaitez exécuter l’assimilation de la partie supérieure.

1. Cliquez sur **Inviter** pour début de l’extraction supérieure.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. La boîte de dialogue **Migration Set Ingestion** (Ingestion de la visionneuse de migration) s&#39;affiche.

   >[!NOTE]
   >Désactivez l’option *Balayer* pour empêcher la suppression du contenu existant de l’activité d’assimilation précédente.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-topup-1.png)

### Affichage des journaux d’une visionneuse de migration {#viewing-logs-migration-set}

Vous pouvez vue des journaux pour un jeu de migration existant à partir de la page *Aperçu* .
Suivez les étapes ci-dessous :

1. Accédez à la page *Aperçu* et sélectionnez le jeu de migration à supprimer, puis cliquez sur Journal **des** Vues dans la barre d’actions.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log1.png)

1. La boîte de dialogue **Journaux** s&#39;affiche. Cliquez sur Journaux **** d’Extraction pour vue les journaux dans un nouvel onglet.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log2.png)Or,

   Vous pouvez également vue les journaux de votre jeu de migration depuis l’écran *Aperçu* . Sélectionnez le jeu de migration et cliquez sur l’état sous le champ **EXTRACTION** . Dans ce cas, cliquez sur **TERMINÉ** pour accéder aux journaux de vue dans un nouvel onglet.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log3.png)

### Suppression d’une visionneuse de migration {#deleting-migration-set}

Vous pouvez supprimer le jeu de migration de la page *Aperçu* .
Suivez les étapes ci-dessous :

1. Accédez à la page *Aperçu* et sélectionnez le jeu de migration à supprimer, puis cliquez sur **Supprimer** dans la barre d’actions.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/delete-1.png)

1. Cliquez sur **Supprimer** de la boîte de dialogue **Supprimer le jeu** de migration pour confirmer la suppression.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/delete-3.png)

## Résolution des incidents {#troubleshooting}

### ID d’objet blob manquants {#missing-blobs}

S’il manque des identifiants blob signalés, comme indiqué ci-dessous, il est nécessaire d’exécuter une vérification de cohérence dans le référentiel existant et de restaurer les lobs manquants.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

La commande suivante est exécutée :

>[!NOTE]
> `--verbose` est requis pour signaler les chemins d’accès aux noeuds à partir desquels les objets blob sont référencés.

**Pour les référentiels AEM 6.5 (Oak 1.8 et versions antérieures)**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Pour les référentiels dotés de Oak > 1.10**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

Pour plus d&#39;informations, reportez-vous à [Oak Runnable Jar](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run) .

Les fichiers créés dans *OUT_DIR* spécifiés ci-dessus pour assurer la cohérence peuvent ensuite être vérifiés pour détecter les chemins manquants de binaires et les actions appropriées prises comme la restauration à partir d&#39;une sauvegarde, la suppression des chemins, la réindexation, etc.

### Comportement de l’interface utilisateur {#ui-behavior}

En tant qu’utilisateur, vous pouvez constater les changements de comportement suivants dans l’interface utilisateur de l’outil de transfert de contenu :

1. L’utilisateur crée un jeu de migration pour une URL d’auteur (Développement/Etape/Production) et effectue correctement l’extraction et l’assimilation.

1. L’utilisateur crée ensuite un jeu de migration pour la même URL d’auteur et effectue l’extraction et l’assimilation sur le nouveau jeu de migration. L’interface utilisateur indique que l’état d’assimilation du premier jeu de migration devient **ÉCHOUÉ** et qu’aucun journal n’est disponible.

1. Cela ne signifie pas que l’assimilation du premier jeu de migration a échoué. Ce comportement est visible car lorsqu’une nouvelle tâche d’assimilation est lancée, elle supprime la tâche d’assimilation précédente. Par conséquent, l’état des modifications sur le premier jeu de migration doit être ignoré.


