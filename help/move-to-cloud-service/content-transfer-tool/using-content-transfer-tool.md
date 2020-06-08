---
title: Utilisation de l’outil de transfert de contenu
description: Utilisation de l’outil de transfert de contenu
translation-type: tm+mt
source-git-commit: f154ffacbeeee1993a9cc3bd3bd274be33dca7a7
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 91%

---


# Utilisation de l’outil de transfert de contenu {#using-content-transfer-tool}

## Points importants concernant l’utilisation de l’outil de transfert de contenu {#pre-reqs}

Consultez la section ci-dessous pour comprendre les points importants à prendre en compte pour l’exécution de l’outil de transfert de contenu :

* La configuration minimale requise pour l’outil de transfert de contenu est AEM 6.3 + et JAVA 8. Si vous utilisez une version antérieure d’AEM, vous devrez mettre à niveau votre référentiel de contenu à la version AEM 6.5 pour utiliser l’outil de transfert de contenu.

* Si vous utilisez un *environnement Sandbox*, veillez à ce qu’il soit mis à niveau à la version du 29 mai 2020, ou à une version postérieure. Si vous utilisez un *environnement de production*, il est automatiquement mis à jour.

* Pour utiliser l’outil de transfert de contenu, vous devez être un utilisateur administrateur sur votre instance source et appartenir au groupe d’administration dans l’instance de service Cloud à laquelle vous transférez du contenu. Les utilisateurs non privilégiés ne pourront pas récupérer le jeton d&#39;accès pour utiliser l’outil de transfert de contenu.

* Pendant la phase d’extraction, l’outil de transfert de contenu est exécuté sur une instance source AEM active.

* La *phase d’assimilation* de l’auteur réduira l’ensemble du déploiement de l’auteur. L’auteur AEM ne sera donc pas disponible pendant la totalité du processus d’assimilation.

## Disponibilité {#availability}

Il est possible de télécharger l’outil de transfert de contenu dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais de Package Manager sur votre instance source Adobe Experience Manager (AEM).

>[!NOTE]
>Téléchargez l’outil de transfert de contenu depuis [Adobe Experience Cloud](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## Exécution de l’outil de transfert de contenu {#running-tool}

Consultez cette section pour effectuer une migration du contenu vers AEM as a Cloud Service (création/publication) à l’aide de l’outil de transfert de contenu :

1. Sélectionnez Adobe Experience Manager et accédez aux outils -> **Opérations** -> **Transfert de contenu**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content1.png)

1. Cliquez sur **Créer un jeu de migration** pour créer un jeu de migration. L’écran **Détails du jeu de migration de contenu** s’affiche.

   >[!NOTE]
   >Vous voyez s’afficher dans cet écran les jeux de migration existants, avec leur état actuel.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

1. Renseignez les champs de l’écran **Détails du jeu de migration de contenu**, comme décrit ci-dessous.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content-3.png)


   1. **Nom** : renseignez le nom du jeu de migration.
      >[!NOTE]
      >Aucun caractère spécial n’est autorisé pour la saisie de ce nom.

   1. **Configuration du service cloud** : renseignez l’URL de destination d’auteur AEM as a Cloud Service.

      >[!NOTE]
      >Vous pouvez créer et gérer un maximum de quatre jeux de migration à la fois pendant l’activité de transfert de contenu.
      >En outre, vous devez créer une migration distincte pour chacun des environnements spécifiques - *Évaluation*, *Développement* ou *Production*.

   1. **Jeton d’accès** : renseignez le jeton d’accès.

      >[!NOTE]
      >Vous pouvez récupérer le jeton d’accès de l’instance d’auteur en accédant à `/libs/granite/migration/token.json`.

   1. **Paramètres** : sélectionnez les paramètres suivants pour créer le jeu de migration :

      1. **Inclure la version** : sélectionnez les options requises.

      1. **Chemins à inclure** : utilisez le navigateur de chemins pour sélectionner les chemins objets de la migration.

         >[!IMPORTANT]
         >Les chemins suivants sont restreints lors de la création d’un jeu de migration :
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc`


1. Cliquez sur **Enregistrer** après avoir complété tous les champs de l’écran **Détails du jeu de migration de contenu**.

1. Vous voyez alors le jeu de migration défini dans la page *Aperçu*.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

   Tous les jeux de migration existants de cet écran s’affichent sur la page *Aperçu* avec leurs informations d’état et d’état actuel.

   * Un *nuage de couleur rouge* indique que vous ne pouvez pas terminer le processus d’extraction.
   * Un *nuage de couleur verte* indique que vous pouvez terminer le processus d’extraction.
   * Une *icône de couleur jaune* indique que vous n’avez pas créé le jeu de migration existant et que celui ainsi indiqué a été créé par un autre utilisateur de la même instance.

1. Sélectionnez un jeu de migration dans la page d’aperçu, puis cliquez sur **Propriétés** pour voir ou modifier les propriétés du jeu de migration.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img6.png)

### Processus d’extraction au cours du transfert de contenu {#extraction-process}

Pour extraire votre jeu de migration de l’outil de transfert de contenu, procédez comme suit :

1. Pour démarrer l’extraction, sélectionnez un jeu de migration dans la page *Aperçu*, puis cliquez sur **Extraire**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. La boîte de dialogue **Extraction du jeu de migration** s’affiche. Cliquez sur **Extraire** pour terminer la phase d’extraction.

   >[!NOTE]
   >Vous avez la possibilité de remplacer le conteneur d’évaluation pendant la phase d’extraction.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-2.png)

1. Le champ **EXTRACTION** affiche l’état **EN COURS** pour le processus d’extraction en cours.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-3.png)

   Une fois l’extraction terminée, l’état du jeu de migration est mis à jour sur **TERMINÉ** et une icône représentant un nuage *vert uni* s’affiche sous le champ **INFO**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-4.png)

   >[!NOTE]
   >Vous devrez actualiser la page pour voir l’état après mise à jour.
   >Lorsque la phase d’extraction est lancée, un verrou d’écriture est créé et libéré après *60 secondes*. Donc, si une extraction est arrêtée, vous devez attendre une minute pour que le verrou soit relâché avant de recommencer l&#39;extraction.

#### Extraction de complément {#top-up-extraction-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur le service cloud.

Une fois le processus d’extraction terminé, vous pouvez transférer le contenu différentiel à l’aide de la méthode d’extraction de complément. Suivez les étapes ci-dessous :

1. Accédez à la page *Aperçu* et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’extraction de complément.

1. Cliquez sur **Extraire** pour démarrer l’extraction de complément.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. La boîte de dialogue **Extraction du jeu de migration** s’affiche.

   >[!IMPORTANT]
   >Il est préférable de désactiver l’option **Remplacer le conteneur d’évaluation pendant l’extraction**.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-topup-1.png)

### Processus d’assimilation au cours du transfert de contenu {#ingestion-process}

Pour assimiler le jeu de migration obtenu à l’aide de l’outil de transfert de contenu, procédez comme suit :

1. Pour démarrer l’extraction, sélectionnez un jeu de migration dans la page *Aperçu*, puis cliquez sur **Assimiler**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. La boîte de dialogue **Assimilation du jeu de migration** s’affiche.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-2.png)

   Pour une démonstration, l’option **Assimiler du contenu avec l’instance d’auteur** est désactivée. Il est possible d’assimiler en même temps du contenu avec l’instance d’auteur et de publication.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-3.png)

   Cliquez sur **Assimiler** pour terminer la phase d’assimilation.

1. Une fois l’assimilation terminée, l’état du champ **ASSIMILATION AVEC L’AUTEUR** est mis à jour sur **TERMINÉ** et une icône en forme de nuage vert uni s’affiche sous la mention **INFO**.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-4.png)

   >[!NOTE]
   > Vous devrez actualiser la page pour voir l’état après mise à jour.

#### Assimilation de complément {#top-up-ingestion-process}

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un *complément* de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur le service cloud.

Une fois le processus d’assimilation terminé, vous pouvez utiliser le contenu différentiel à l’aide de la méthode d’assimilation de complément. Suivez les étapes ci-dessous :

1. Accédez à la page *Aperçu* et sélectionnez le jeu de migration pour lequel vous souhaitez effectuer l’assimilation de complément.

1. Cliquez sur **Assimiler** pour démarrer l’extraction de complément.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. La boîte de dialogue **Assimilation du jeu de migration** s’affiche.

   >[!NOTE]
   >Désactivez l’option *Effacer* pour éviter la suppression du contenu existant de l’activité d’assimilation précédente.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-topup-1.png)

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
> `--verbose` (indicateur) est nécessaire pour signaler les chemins d’accès aux nœuds permettant de référencer les objets blob.

**Pour les référentiels AEM 6.5 (Oak 1.8 et versions antérieures)**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Pour les référentiels dotés de Oak > 1.10**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

Pour plus d’informations, voir la section [Fichier jar exécutable Oak](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run).

Les fichiers créés dans *OUT_DIR*, spécifiés ci-dessus pour assurer la cohérence, peuvent ensuite être vérifiés pour détecter les chemins manquants de binaires et les actions appropriées mises en œuvre (restauration à partir d’une sauvegarde, suppression des chemins, réindexation, etc.).

### Comportement de l’interface utilisateur {#ui-behavior}

En tant qu’utilisateur, il est possible que vous constatiez les changements de comportement suivants dans l’interface utilisateur de l’outil de transfert de contenu :

* L’utilisateur crée un jeu de migration pour une URL d’auteur (Développement/Évaluation/Production) et effectue avec succès l’extraction et l’assimilation.

* L’utilisateur crée ensuite un jeu de migration pour la même URL d’auteur et effectue l’extraction et l’assimilation sur le nouveau jeu de migration. L’interface utilisateur indique que l’état d’assimilation du premier jeu de migration devient **ÉCHEC** et qu’aucun journal n’est disponible.

* Cela ne signifie pas que l’assimilation du premier jeu de migration a échoué. Ce comportement apparaît car lorsqu’une nouvelle tâche d’assimilation est lancée, elle supprime la tâche d’assimilation précédente. L’état des modifications du premier jeu de migration doit donc être ignoré.

* Les icônes de l’interface utilisateur de l’outil de transfert de contenu peuvent sembler différentes des captures d’écran affichées dans ce guide ou ne s’affichent pas du tout selon la version de l’instance AEM source.


