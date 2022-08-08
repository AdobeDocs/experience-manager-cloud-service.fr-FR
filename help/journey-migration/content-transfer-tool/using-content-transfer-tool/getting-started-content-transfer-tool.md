---
title: Prise en main de l’outil de transfert de contenu
description: Prise en main de l’outil de transfert de contenu
exl-id: c0cecf65-f419-484b-9d55-3cbd561e8dcd
source-git-commit: 7bebdff5095786005d5c4c91b7b699d71f9813a7
workflow-type: tm+mt
source-wordcount: '1341'
ht-degree: 96%

---

# Prise en main de l’outil de transfert de contenu {#getting-started-content-transfer-tool}


## Disponibilité {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Télécharger"
>abstract="Il est possible de télécharger l’outil de transfert de contenu dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM). Veillez à télécharger la dernière version."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html" text="Notes de mise à jour"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Portail de distribution de logiciels"

Il est possible de télécharger l’outil de transfert de contenu dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du [Gestionnaire de modules](/help/implementing/developing/tools/package-manager.md) sur votre instance source Adobe Experience Manager (AEM). Veillez à télécharger la dernière version. Pour plus d’informations sur la dernière version, consultez les [Notes de mise à jour](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

>[!NOTE]
>Téléchargez l’outil de transfert de contenu depuis le portail de [distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## Connectivité de l’environnement source {#source-environment-connectivity}

>[!NOTE]
>
>Une erreur de connexion peut également se produire si un jeu de migration a été supprimé de Cloud Acceleration Manager.

L’instance d’AEM source peut se trouver derrière un pare-feu d’où elle ne peut atteindre que certains hôtes qui ont été ajoutés à une liste autorisée. Pour réussir l’exécution d’une extraction, les points d’entrée suivants doivent être accessibles à partir de l’instance AEM en cours d’exécution :

* L’environnement AEM as a Cloud Service cible : `author-p<program_id>-e<env_id>.adobeaemcloud.com`
* Le service d’enregistrement blob Azure : `*.blob.core.windows.net`
* Le point d’entrée de l’IO de mappage des utilisateurs : `usermanagement.adobe.io`

Pour tester la connectivité à l’environnement AEM as a Cloud Service cible, lancez la commande cURL suivante à partir du shell de l’instance source (remplacez `program_id`, `environment_id` et `migration_token`) :

`curl -i https://author-p<program_id>-e<environment_id>.adobeaemcloud.com/api/migration/migrationSet -H "Authorization: Bearer <migration_token>"`

>[!NOTE]
>Si vous recevez un `HTTP/2 200`, la connexion à AEM as a Cloud Service a réussi.

### Activation de la journalisation SSL {#enable-ssl-logging}

Comprendre les problèmes de connexion SSL/TLS peut parfois être difficile. Pour résoudre les problèmes de connexion lors d’un processus d’extraction, vous pouvez activer la journalisation SSL via la console système de l’environnement d’AEM source en procédant comme suit :

1. Accédez à la console web Adobe Experience Manager sur votre instance source en accédant à **Outils - Opérations - Console web** ou directement à l’URL à l’adresse *https://serveraddress:serverport/system/console/configMgr*
1. Recherchez **Configuration du service d’extraction de l’outil de transfert de contenu**
1. Utilisez le bouton représentant un crayon pour modifier ses valeurs de configuration.
1. Activez la variable **Activation de la journalisation SSL pour l’extraction** , puis appuyez sur **Enregistrer**:

   ![image](/help/journey-migration/content-transfer-tool/assets/enable_ssl_logging.png)


## Exécution de l’outil de transfert de contenu {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Exécution de l’outil de transfert de contenu"
>abstract="Découvrez comment utiliser l’outil de transfert de contenu pour effectuer une migration du contenu vers AEM as a Cloud Service (auteur/publication) à l’aide de l’outil de transfert de contenu."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on&amp;captions=fre_fr" text=" Voir Démonstration"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=fr#migration" text="Tutoriel – Utilisation de l’outil de transfert de contenu"

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)
<!-- Need to remove the video -->

La section suivante s’applique à la nouvelle version de l’outil de transfert de contenu. Consultez cette section pour effectuer une migration du contenu vers AEM as a Cloud Service à l’aide de l’outil de transfert de contenu :

### Phase de configuration de l’extraction {#extraction-setup-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction_setup"
>title="Phase de configuration de l’extraction"
>abstract="Découvrez comment créer un jeu de migration et copier la clé d’extraction."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration" text="Tutoriel – Utilisation de l’outil de transfert de contenu"

<!-- Contextualhelp id "aemcloud_ctt_extraction_setup" needs to be added here -->

1. Connectez-vous à Cloud Acceleration Manager (CAM) et cliquez sur le projet CAM que vous avez créé précédemment pour évaluer votre préparation à AEM as a Cloud Service. Si vous n’avez pas créé de projet CAM, reportez-vous à la section Création et gestion d’un projet dans CAM.

1. Cliquez sur la carte **Transfert de contenu**. Vous accédez alors à la vue Liste des jeux de migration.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam1.png)

1. Créez un jeu de migration en cliquant sur **Créer un jeu de migration**.

   >[!NOTE]
   >
   >Vous pouvez créer au maximum cinq jeux de migration par projet dans Cloud Acceleration Manager.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam2.png)

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam3.png)

1. Votre liste de migration doit maintenant apparaître dans la vue Liste. Cliquez sur le symbole des trois petits points (**...**) pour ouvrir la liste déroulante, puis cliquez sur **Copier la clé d’extraction**. Vous aurez besoin de cette clé pendant la phase d’extraction. Copiez cette clé d’extraction.

   >[!NOTE]
   >
   >La clé d’extraction permet à votre environnement AEM source de se connecter en toute sécurité au jeu de migration. Traitez cette clé avec le même soin que vous le feriez avec un mot de passe et ne la partagez jamais sur un support non sécurisé comme un e-mail.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam4.png)

### Renseignement du jeu de migration {#populating-the-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_populate_migrationset"
>title="Renseignez le jeu de migration « abstract= ». Lorsque vous avez créé un jeu de migration, celui-ci doit être renseigné avec le contenu de l’instance source qui doit être déplacée vers l’environnement AEM as a Cloud Service. Pour ce faire, l’outil de transfert de contenu doit être installé sur l’instance source."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html?lang=fr" text="Extraction de contenu"

Pour renseigner le jeu de migration que vous avez créé dans Cloud Acceleration Manager, vous devez installer la dernière version de l’outil de transfert de contenu sur votre instance source Adobe Experience Manager (AEM). Consultez cette section pour savoir comment renseigner le jeu de migration.

1. Après avoir installé la dernière version (v2.0.10) de l’outil de transfert de contenu sur votre instance Adobe Experience Manager source, accédez à **Opérations - Migration de contenu**.

1. Cliquez sur **Créer un jeu de migration**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam5.png)

1. Collez la clé d’extraction qui a été copiée à partir de l’instance CAM plus tôt dans le champ d’entrée Clé d’extraction du formulaire **Créer un jeu de migration**. Une fois que vous avez effectué cette opération, les champs Nom du jeu de migration et Nom du projet (CAM) de Cloud Acceleration Manager sont automatiquement renseignés. Ils doivent correspondre au nom du jeu de migration dans CAM et au nom du projet CAM que vous avez créé. Vous pouvez maintenant ajouter des chemins de contenu. Une fois que vous avez ajouté des chemins de contenu, vous pouvez enregistrer le jeu de migration. Vous pouvez exécuter l’extraction en incluant ou en excluant les versions.

   >[!NOTE]
   >
   >Assurez-vous que la clé d’extraction est valide et n’est pas proche de son expiration. Vous pouvez obtenir ces informations dans la boîte de dialogue **Créer un jeu de migration** après avoir collé la clé d’extraction. Si vous obtenez une erreur de connexion, reportez-vous à [Connectivité de l’environnement source](#source-environment-connectivity) pour plus d’informations.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam6.png)

1. Sélectionnez ensuite les paramètres suivants pour créer un jeu de migration :

   1. **Inclure les versions** : sélectionnez les options requises. Lorsque différentes versions sont incluses, le chemin d’accès `/var/audit` est automatiquement inclus pour migrer les événements de contrôle.

      ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam7.png)

      >[!NOTE]
      >Si vous envisagez d’inclure différentes versions dans un jeu de migration et effectuez des compléments avec `wipe=false`, vous devez désactiver la purge des versions en raison d’une restriction actuelle de l’outil de transfert de contenu. Si vous préférez conserver la purge de version activée et effectuer des compléments dans un jeu de migration, vous devez effectuer l’ingestion sous la forme `wipe=true`.


   1. **Chemins à inclure** : utilisez le navigateur de chemins pour sélectionner les chemins objets de la migration. Le sélecteur de chemin accepte les entrées effectuées par saisie ou par sélection.

      >[!IMPORTANT]
      >Les chemins suivants sont restreints lors de la création d’un jeu de migration :
      >* `/apps`
      >* `/libs`
      >* `/home`
      >* `/etc` (il est possible de sélectionner certains chemins `/etc` dans le CTT)


1. Cliquez sur **Enregistrer** après avoir rempli tous les champs de l’écran **Créer un jeu de migration**.

<!-- 1. You will view your migration set in the **Content Transfer** wizard, as shown in the figure below.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt07.png)

   All the existing migration sets are displayed on the **Content Transfer** wizard with their current status and status information. You may see some of these icons described below.

   * A *red cloud* indicates that you cannot complete the extraction process.
   * A *green cloud* indicates that you can complete the extraction process.
   * A *yellow icon* indicates that you did not create the existing migration set and the specific one is created by some other user in the same instance.

1. Select a migration set and click on **Properties** to view or edit the migration set properties. While editing properties, it is not possible to change the **Migration Set name** or the **Service URL**. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt06.png) -->

### Vérification de la taille du jeu de migration {#migration-set-size}

Après la création d’un jeu de migration, il est vivement recommandé d’exécuter une vérification de taille sur le jeu de migration avant de lancer un processus d’extraction.
En effectuant une vérification de taille sur le jeu de migration, vous pourrez :
* déterminer s’il y a suffisamment d’espace disque dans le sous-référentiel `crx-quickstart` pour terminer l’extraction ;
* déterminer si la taille du jeu de migration est conforme aux restrictions concernant les produits pris en charge et éviter les échecs d’ingestion de contenu.

Pour exécuter une vérification de taille, procédez comme suit :

1. Sélectionnez un jeu de migration et cliquez sur **Check Size** (Vérifier la taille).

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam8.png)

1. Cela ouvrira la boîte de dialogue **Check Size** (Vérifier la taille).

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam9.png)

1. Cliquez sur **Check Size** (Vérifier la taille) pour démarrer le processus. Vous revenez alors à la vue Liste des jeux de migration et un message vous indique que **Check Size** (Vérifier la taille) est en cours d’exécution.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam10.png)

1. Une fois que le processus **Vérifier la taille** est terminé, le statut passe sur **TERMINÉ**. Sélectionnez le même jeu de migration et cliquez sur **Vérifier la taille** pour afficher les résultats. Voici ci-dessous un exemple de résultats de **Check Size** (Vérifier la taille) sans avertissement.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam11.png)

1. Si les résultats de **Check Size** (Vérifier la taille) indiquent qu’il n’y a pas suffisamment d’espace disque ou que le jeu de migration dépasse les limites du produit, le statut **WARNING** (AVERTISSEMENT) s’affiche.

<!--   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)
   
   Below is an example of **Check Size** results with warnings.
 
   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png) -->


## Prochaines étapes {#whats-next}

Maintenant que vous avez appris à créer un jeu de migration, vous êtes prêt à en apprendre plus sur les processus d’extraction et d’ingestion dans l’outil de transfert de contenu. Avant d’en apprendre plus sur ces processus, vous devez consulter la section [Gestion des référentiels de contenu volumineux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr) pour accélérer considérablement les phases d’extraction et d’ingestion de l’activité de transfert de contenu afin de déplacer le contenu vers AEM as a Cloud Service.
