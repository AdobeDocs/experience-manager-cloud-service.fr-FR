---
title: Prise en main de l’outil de transfert de contenu
description: Découvrez comment commencer à utiliser l’outil de transfert de contenu
exl-id: c0cecf65-f419-484b-9d55-3cbd561e8dcd
feature: Migration
role: Admin
source-git-commit: d8730109f5cd7dab44f535b1de008ae09811f221
workflow-type: tm+mt
source-wordcount: '1362'
ht-degree: 76%

---


# Prise en main de l’outil de transfert de contenu {#getting-started-content-transfer-tool}


## Disponibilité {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Télécharger"
>abstract="Il est possible de télécharger l’outil de transfert de contenu dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le package par le biais du gestionnaire de packages sur votre instance source Adobe Experience Manager (AEM). Veillez à télécharger la dernière version."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html?lang=fr" text="Notes de mise à jour"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Portail de distribution de logiciels"

Il est possible de télécharger l’outil de transfert de contenu dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le package par le biais de [Package Manager](/help/implementing/developing/tools/package-manager.md) sur votre instance Adobe Experience Manager (AEM) source. Veillez à télécharger la dernière version. Pour plus de détails sur la dernière version, voir [Notes de mise à jour](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html?lang=fr).

Seules les versions 2.0.0 et ultérieures seront prises en charge. Il est conseillé d’utiliser la version la plus récente.

>[!NOTE]
>Téléchargez l’outil de transfert de contenu depuis le portail de [distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?lang=fr).

## Connectivité de l’environnement source {#source-environment-connectivity}

>[!NOTE]
>
>Une erreur de connexion peut également se produire si un jeu de migration a été supprimé de Cloud Acceleration Manager.

L’instance d’AEM source peut se trouver derrière un pare-feu d’où elle ne peut atteindre que certains hôtes qui ont été ajoutés à une liste autorisée. Pour réussir l’exécution d’une extraction, les points de terminaison suivants doivent être accessibles à partir de l’instance AEM :

* Le service de stockage d’objets blob Azure : `casstorageprod.blob.core.windows.net`

>[!NOTE]
>Si l’extraction échoue en raison de l’erreur suivante : &quot;javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target&quot;, cela peut être résolu en important le certificat d’autorité de certification approprié.

### Activation de la journalisation SSL {#enable-ssl-logging}

Comprendre les problèmes de connexion SSL/TLS peut parfois être difficile. Pour résoudre les problèmes de connexion lors d’un processus d’extraction, vous pouvez activer la journalisation SSL via la console système de l’environnement AEM source en procédant comme suit :

1. Accédez à la console web Adobe Experience Manager sur votre instance source, en accédant à **Outils > Opérations > Console web** ou directement à l’URL à l’adresse *https://serveraddress:serverport/system/console/configMgr*
1. Recherchez **Configuration du service d’extraction de l’outil de transfert de contenu**
1. Utilisez le bouton représentant un crayon pour modifier ses valeurs de configuration.
1. Activez la variable **Activation de la journalisation SSL pour l’extraction** , puis appuyez sur **Enregistrer**:

   ![image](/help/journey-migration/content-transfer-tool/assets/enable_ssl_logging.png)

>[!NOTE]
>Cet indicateur est uniquement destiné au débogage des problèmes SSL. Assurez-vous que l’indicateur est désactivé avant d’exécuter l’extraction, car cela peut nécessiter un grand volume d’espace disque. Cela peut potentiellement remplir la capacité du lecteur et entraîner l’échec du processus d’extraction.

## Exécution de l’outil de transfert de contenu {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Exécution de l’outil de transfert de contenu"
>abstract="Découvrez comment utiliser l’outil de transfert de contenu pour effectuer une migration du contenu vers AEM as a Cloud Service (auteur/publication) à l’aide de l’outil de transfert de contenu."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on&amp;captions=fre_fr" text=" Voir Démonstration"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=fr#migration" text="Tutoriel – Utilisation de l’outil de transfert de contenu"

La section suivante s’applique à la nouvelle version de l’outil de transfert de contenu. Consultez cette section pour effectuer une migration du contenu vers AEM as a Cloud Service à l’aide de l’outil de transfert de contenu :

### Phase de configuration de l’extraction {#extraction-setup-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction_setup"
>title="Phase de configuration de l’extraction"
>abstract="Découvrez comment créer et gérer un jeu de migration et comment copier la clé d’extraction."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=fr#migration" text="Tutoriel – Utilisation de l’outil de transfert de contenu"

<!-- Contextualhelp id "aemcloud_ctt_extraction_setup" must be added here -->

1. Connectez-vous à Cloud Acceleration Manager (CAM) et cliquez sur le projet CAM que vous avez créé précédemment afin d’évaluer votre préparation au passage à AEM as a Cloud Service. Si vous n’avez pas créé de projet CAM, reportez-vous à la section Création et gestion d’un projet dans CAM.

1. Cliquez sur la carte **Transfert de contenu** pour ouvrir la vue Liste des jeux de migration.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam1.png)

1. Créez un jeu de migration en cliquant sur **Créer un jeu de migration**.

   >[!NOTE]
   >
   >Dans Cloud Acceleration Manager, il est possible de créer un maximum de 10 jeux de migration, y compris les jeux expirés, par projet.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam2.png)

   La boîte de dialogue suivante s’affiche. Notez qu’un jeu de migration expire après une longue période d’inactivité. Une fois les avertissements affichés sur la carte du projet et les lignes du tableau des tâches de migration pour une période donnée, le jeu de migration expire et ses données ne sont plus disponibles. Consultez [Expiration du jeu de migration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) pour plus d’informations.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam3.png)

   >[!NOTE]
   >
   >Le nom doit respecter les mêmes conventions qu’un nœud AEM. Il ne peut donc pas contenir les caractères suivants : . / : [ ] | *

1. Votre liste de migration doit maintenant apparaître dans la vue Liste. Sélectionnez le symbole des trois points (**...**) pour ouvrir la liste déroulante et sélectionnez **Copier la clé d’extraction**. Vous avez besoin de cette clé pendant la phase d’extraction. Copiez cette clé d’extraction.

   >[!NOTE]
   >
   >La clé d’extraction permet à votre environnement AEM source de se connecter en toute sécurité au jeu de migration. Traitez cette clé avec le même soin que vous le feriez avec un mot de passe et ne la partagez jamais sur un support non sécurisé comme un e-mail.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam4.png)

### Renseignement du jeu de migration {#populating-the-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_populate_migrationset"
>title="Renseigner le jeu de migrations"
>abstract="Lorsque vous avez créé un jeu de migration, celui-ci doit être renseigné avec le contenu de l’instance source qui doit être déplacée vers l’environnement AEM as a Cloud Service. Pour ce faire, l’outil de transfert de contenu doit être installé sur l’instance source."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html?lang=fr" text="Extraction de contenu"

Pour renseigner le jeu de migration que vous avez créé dans Cloud Acceleration Manager, installez la dernière version de l’outil de transfert de contenu sur votre instance Adobe Experience Manager (AEM) source. Pour savoir comment renseigner le jeu de migration, suivez cette section.

1. Après avoir installé la dernière version de l’outil de transfert de contenu sur votre instance Adobe Experience Manager source, accédez à **Opérations - Migration de contenu**.

1. Cliquez sur **Créer un jeu de migration**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam5.png)

1. Collez la clé d’extraction qui a été copiée à partir de l’instance CAM plus tôt dans le champ d’entrée Clé d’extraction du formulaire **Créer un jeu de migration**. Une fois que vous avez effectué cette opération, les champs Nom du jeu de migration et Nom du projet de Cloud Acceleration Manager (CAM) sont automatiquement renseignés. Ils doivent correspondre au nom du jeu de migration dans CAM et au nom du projet CAM que vous avez créé. Vous pouvez maintenant ajouter des chemins de contenu. Après avoir ajouté des chemins de contenu, enregistrez le jeu de migration. Vous pouvez exécuter l’extraction en incluant ou en excluant les versions.

   >[!NOTE]
   >
   >Assurez-vous que la clé d&#39;extraction est valide et qu&#39;elle n&#39;est pas proche de son expiration. Vous pouvez obtenir ces informations dans la boîte de dialogue **Créer un jeu de migration** après avoir collé la clé d’extraction. Si vous obtenez une erreur de connexion, reportez-vous à [Connectivité de l’environnement source](#source-environment-connectivity) pour plus d’informations.

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

1. Select a migration set and click **Properties** to view or edit the migration set properties. While editing properties, it is not possible to change the **Migration Set name** or the **Service URL**. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt06.png) -->

### Vérification de la taille du jeu de migration {#migration-set-size}

Après la création d’un jeu de migration, il est vivement recommandé d’exécuter une vérification de taille sur le jeu de migration avant de lancer un processus d’extraction.
En effectuant une vérification de taille sur le jeu de migration, vous pouvez :

* déterminer s’il y a suffisamment d’espace disque dans le sous-référentiel `crx-quickstart` pour terminer l’extraction ;
* déterminer si la taille du jeu de migration est conforme aux restrictions concernant les produits pris en charge et éviter les échecs d’ingestion de contenu.

Pour exécuter une vérification de taille, procédez comme suit :

1. Sélectionnez un jeu de migration et cliquez sur **Vérifier la taille**.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam8.png)

1. Cela ouvre la boîte de dialogue **Vérifier la taille**.

   ![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam9.png)

1. Cliquez sur **Vérifier la taille** pour lancer le processus. Vous revenez alors à la vue Liste jeu de migration et un message vous indique que **Vérifier la taille** est en cours d’exécution.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam10.png)

1. Une fois que le processus **Vérifier la taille** est terminé, le statut passe à **TERMINÉ**. Sélectionnez le même jeu de migration et cliquez sur **Vérifier la taille** pour afficher les résultats. Voici ci-dessous un exemple de résultats de **Check Size** (Vérifier la taille) sans avertissement.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam11.png)

1. Si les résultats du processus **Vérifier la taille** indiquent qu’il n’y a pas suffisamment d’espace disque et/ou que le jeu de migration dépasse les limites du produit, le statut **AVERTISSEMENT** s’affiche.

<!--   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)
   
   Below is an example of **Check Size** results with warnings.
 
   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png) -->


## Prochaines étapes {#whats-next}

Maintenant que vous avez appris à créer un jeu de migration, vous êtes prêt à en apprendre plus sur les processus d’extraction et d’ingestion dans l’outil de transfert de contenu. Avant d’apprendre ces processus, vous devez consulter [Gestion de référentiels de contenu volumineux](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) pour accélérer considérablement les phases d’extraction et d’ingestion de l’activité de transfert de contenu afin de déplacer le contenu vers AEM as a Cloud Service.
