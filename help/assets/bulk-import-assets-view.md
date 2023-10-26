---
title: Importer des ressources en bloc à l’aide de la vue Assets
description: Découvrez comment importer des ressources en bloc à l’aide de la nouvelle interface utilisateur d’Assets (vue Assets). Elle permet aux administrateurs et administratrices d’importer un grand nombre de ressources d’une source de données vers AEM Assets.
exl-id: 10f9d679-7579-4650-9379-bc8287cb2ff1
source-git-commit: 88198e9333a7f706fc99e487d8cde84647fa111f
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 53%

---

# Importer des ressources en bloc à l’aide de la vue Assets  {#bulk-import-assets-view}

L’import en bloc dans la vue AEM Assets permet aux administrateurs et administratrices d’importer un grand nombre de ressources d’une source de données vers AEM Assets. Les administrateurs et administratrices n’ont plus besoin de charger des ressources ou des dossiers individuels vers AEM Assets.

>[!NOTE]
>
>L’importateur en masse d’affichage des ressources utilise le même serveur principal que celui de l’importateur en masse d’affichage administrateur. Cependant, il offre davantage de sources de données à importer et une expérience utilisateur plus simplifiée.

Vous pouvez importer des ressources à partir des sources de données suivantes :

* Azure
* AWS
* Google Cloud
* Dropbox
* OneDrive

## Conditions préalables requises {#prerequisites}

| Source de données | Conditions préalables requises |
|-----|------|
| Azure | <ul> <li>Compte de stockage Azure </li> <li> Conteneur d’objets blob Azure <li> Clé d’accès Azure ou jeton SAS en fonction du mode d’authentification </li></ul> |
| AWS | <ul> <li>Région AWS </li> <li> Compartiment AWS <li> Clé d’accès AWS </li><li> Secret d’accès AWS </li></ul> |
| Google Cloud | <ul> <li>Compartiment GCP </li> <li> Adresse e-mail du compte de service GCP <li> Clé privée du compte de service GCP</li></ul> |
| Dropbox | <ul> <li>ID client Dropbox (Clé de l’application) </li> <li> Secret client Dropbox (secret d’application)</li></ul> |
| OneDrive | <ul> <li>Identifiant du tenant OneDrive  </li> <li> Identifiant du client OneDrive</li><li> Secret client OneDrive</li></ul> |

Outre ces conditions préalables en fonction de la source de données, vous devez connaître le nom du dossier source disponible dans votre source de données, qui contient toutes les ressources à importer dans AEM Assets.

## Configuration de l’application de développement de Dropbox {#dropbox-developer-application}

Avant d’importer des ressources de votre compte de Dropbox vers AEM Assets, créez et configurez l’application de développement de Dropbox.

Procédez comme suit :

1. Connectez-vous à [Compte Dropbox](https://www.dropbox.com/developers) et cliquez sur **[!UICONTROL Création d’applications]**.

1. Dans le **[!UICONTROL Choix d’une API]** , sélectionnez le seul bouton radio disponible.

1. Dans le **[!UICONTROL Choisissez le type d&#39;accès dont vous avez besoin]** , sélectionnez l’une des options suivantes :

   * Sélectionner **[!UICONTROL Dossier de l’application]**, si vous avez besoin d’accéder à un seul dossier créé dans votre application dans votre compte de Dropbox.

   * Sélectionner **[!UICONTROL Dropbox complet]**, si vous devez accéder à tous les fichiers et dossiers de votre compte de Dropbox.

1. Indiquez un nom pour votre application, puis cliquez sur **[!UICONTROL Créer une application]**.

1. Dans le **[!UICONTROL Paramètres]** dans l’onglet de votre application, ajoutez ce qui suit au **[!UICONTROL URI de redirection]** section :

   * https://exc-unifiedcontent.experience.adobe.net

   * https://exc-unifiedcontent.experience-stage.adobe.net (valide uniquement pour les environnements intermédiaires)

1. Copiez les valeurs de la variable **[!UICONTROL Clé de l’application]** et **[!UICONTROL Secret de l’application]** des champs. Les valeurs sont requises lors de la configuration de l’outil d’importation en bloc dans AEM Assets.

1. Sur le **[!UICONTROL Autorisations]** , ajoutez les autorisations suivantes dans la **[!UICONTROL Portées individuelles]** .

   * account_info.read

   * files.metadata.read

   * files.content.read

   * files.content.write

1. Cliquez sur **[!UICONTROL Envoyer]** pour enregistrer les modifications.

## Configuration de l’application de développement OneDrive {#onedrive-developer-application}

Avant d’importer des ressources de votre compte OneDrive vers AEM Assets, créez et configurez l’application de développement OneDrive.

Procédez comme suit :

1. Connectez-vous à [Compte OneDrive](https://portal.azure.com/#view/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) et cliquez sur **[!UICONTROL Nouvelle inscription]**.

1. Indiquez un nom pour l’application, puis sélectionnez **[!UICONTROL Comptes dans cet annuaire organisationnel uniquement (Adobe uniquement - client unique)]** de **[!UICONTROL Types de compte pris en charge]**, puis cliquez sur **[!UICONTROL Enregistrer]**. L’application est créée avec succès.

1. Copiez les valeurs des champs ID client de l’application et ID client. Les valeurs sont requises lors de la configuration de l’outil d’importation en bloc dans AEM Assets.

1. Pour ajouter un certificat, procédez comme suit :
   1. Sur la page d’aperçu de l’application, cliquez sur **[!UICONTROL Ajouter un certificat ou un secret]** puis cliquez sur **[!UICONTROL Nouveau secret client]**.
   1. Indiquez la description et l’expiration du secret client, puis cliquez sur **[!UICONTROL Ajouter]**.
   1. Après avoir créé le secret client, copiez la variable **[!UICONTROL Valeur]** (Ne copiez pas le champ Identifiant secret ). Elle est requise lors de la configuration de l’importation en bloc dans AEM Assets.

1. Exécutez les étapes suivantes pour ajouter des URI de redirection :
   1. Sur la page d’aperçu de l’application, cliquez sur **[!UICONTROL Ajout d’un URI de redirection]** > **[!UICONTROL Ajouter une plate-forme]** > **[!UICONTROL Web]**.
   1. Ajoutez ce qui suit au **[!UICONTROL URI de redirection]** section :

      * https://exc-unifiedcontent.experience.adobe.net

      * https://exc-unifiedcontent.experience-stage.adobe.net (valide uniquement pour les environnements intermédiaires)

      Ajoutez le premier URI et cliquez sur **[!UICONTROL Configurer]** pour l’ajouter. Vous pouvez en ajouter d’autres en cliquant sur **[!UICONTROL Ajouter un URI]** , disponible dans la variable **[!UICONTROL Web]** de la section **[!UICONTROL Authentification]** page.

1. Pour ajouter des autorisations d’API à l’application, procédez comme suit :
   1. Cliquez sur **[!UICONTROL Autorisations d’API]** dans le volet de gauche, puis cliquez sur **[!UICONTROL Ajouter une autorisation]**.
   1. Cliquez sur **[!UICONTROL Graphique Microsoft]** > **[!UICONTROL Autorisations déléguées]**. La variable **[!UICONTROL Sélectionner l’autorisation]** affiche les autorisations disponibles.
   1. Sélectionner `offline_access` autorisation de `OpenId permissions` et `Files.ReadWrite.All` autorisation de `Files`.
   1. Cliquez sur **[!UICONTROL Ajout d’autorisations]** pour enregistrer les mises à jour.




## Créer une configuration d’import en bloc {#create-bulk-import-configuration}

Pour créer une configuration d’import en bloc, procédez comme suit :

1. Accédez à **[!UICONTROL Paramètres]** > **[!UICONTROL Import en bloc]** et cliquez sur **[!UICONTROL Créer un import]**.
1. Sélectionnez la source de données. Les options disponibles comprennent Azure, AWS, Google Cloud et Dropbox.
1. Indiquez un nom pour la configuration de lʼimport en bloc dans le champ **[!UICONTROL Nom]**.
1. Indiquez les informations d’identification spécifiques à la source de données, comme mentionné dans les [conditions préalables](#prerequisites).
1. Indiquez le nom du dossier contenant les ressources dans la source de données dans la variable **[!UICONTROL Dossier source]** champ .

   >[!NOTE]
   >
   >Si vous utilisez Dropbox comme source de données, spécifiez le chemin du dossier source en fonction des règles suivantes :
   >* Si vous sélectionnez **Dropbox complet** lors de la création de l’application de Dropbox et le dossier contenant les ressources existe à l’adresse `https://www.dropbox.com/home/bulkimport-assets`, puis spécifiez `bulkimport-assets` dans le **[!UICONTROL Dossier source]** champ .
   >* Si vous sélectionnez **Dossier de l’application** lors de la création de l’application de Dropbox et le dossier contenant les ressources existe à l’adresse `https://www.dropbox.com/home/Apps/BulkImportAppFolderScope/bulkimport-assets`, puis spécifiez `bulkimport-assets` dans le **[!UICONTROL Dossier source]** champ, où `BulkImportAppFolderScope` fait référence au nom de l’application. `Apps` est automatiquement ajouté après `home` dans ce cas.

1. (Facultatif) Sélectionnez lʼoption **[!UICONTROL Supprimer le fichier source après lʼimport]** afin de supprimer les fichiers originaux du magasin de données source après lʼimport des fichiers dans Experience Manager Assets.
1. Sélectionnez le **[!UICONTROL Mode d’importation]**. Les modes suivants sont disponibles : **[!UICONTROL Ignorer]**, **[!UICONTROL Remplacer]** ou **[!UICONTROL Créer une version]**. Le mode par défaut est Ignorer. Dans ce mode, l’outil d’ingestion ignore l’import d’une ressource si elle existe déjà.
   ![Import des détails de la source.](/help/assets/assets/bulk-import-source-details.png)

1. (Facultatif) Indiquez le fichier de métadonnées à importer, fourni au format CSV, dans le champ Fichier de métadonnées, puis cliquez sur **[!UICONTROL Suivant]** pour accéder à **[!UICONTROL Emplacement et filtres]**.
1. Pour définir un emplacement dans la gestion des ressources numériques (DAM) où les ressources doivent être importées à l’aide du champ **[!UICONTROL Dossier cible des ressources]**, indiquez un chemin d’accès. Par exemple, `/content/dam/imported_assets`.
1. (Facultatif) Dans la section **[!UICONTROL Choisir des filtres]**, indiquez la taille de fichier minimale des ressources en Mo à inclure dans le processus d’ingestion dans le champ **[!UICONTROL Filtrer par taille minimale]**.
1. (Facultatif) Indiquez la taille de fichier maximale des ressources en Mo à inclure dans le processus d’ingestion dans le champ **[!UICONTROL Filtrer par taille maximale]**.
1. (Facultatif) Sélectionnez les types MIME à inclure dans le processus d’ingestion à l’aide du champ **[!UICONTROL Inclure le type MIME]**. Vous pouvez sélectionner plusieurs types MIME dans ce champ. Si vous ne définissez pas de valeur, tous les types MIME sont inclus dans le processus d’ingestion.

1. (Facultatif) Sélectionnez les types MIME à exclure dans le processus d’ingestion à l’aide du champ **[!UICONTROL Exclure le type MIME]**. Vous pouvez sélectionner plusieurs types MIME dans ce champ. Si vous ne définissez pas de valeur, tous les types MIME sont inclus dans le processus d’ingestion.

   ![Filtres d’import en bloc.](assets/bulk-import-location.png)

1. Cliquez sur **[!UICONTROL Suivant]**. Sélectionnez **[!UICONTROL Enregistrer et exécuter l’import]** pour enregistrer la configuration et exécuter l’import en bloc. Sélectionnez **[!UICONTROL Enregistrer l’import]** pour enregistrer la configuration afin de pouvoir l’exécuter ultérieurement.

   ![Exécution de l’import en bloc.](assets/bulk-import-run.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour exécuter l’option sélectionnée.

### Gestion des noms de fichier lors de l’importation en bloc {#filename-handling-bulkimport-assets-view}

Lorsque vous importez des ressources ou des dossiers en bloc, [!DNL Experience Manager Assets] importe toute la structure de ce qui existe dans la source d’import. [!DNL Experience Manager] suit les règles intégrées pour les caractères spéciaux dans les noms de ressources et de dossiers ; par conséquent, ces noms de fichier doivent être assainis. Pour les noms de dossier et de ressource, le titre défini par l’utilisateur reste inchangé et est stocké dans `jcr:title`.

Lors de l’importation en bloc, [!DNL Experience Manager] recherche les dossiers existants pour éviter de réimporter les ressources et les dossiers et vérifie également les règles d’assainissement appliquées dans le dossier parent où l’importation a lieu. Si les règles d’assainissement sont appliquées dans le dossier parent, les mêmes règles sont appliquées à la source d’importation. Pour une nouvelle importation, les règles d’assainissement suivantes sont appliquées pour gérer les noms de fichiers des ressources et dossiers.

Pour plus d’informations sur les noms interdits, la gestion des noms de ressources et la gestion des noms de dossiers lors de l’importation en bloc, voir [Gestion des noms de fichier lors de l’importation en bloc dans la vue d’administration](add-assets.md##filename-handling-bulkimport).

## Afficher les configurations d’import en bloc existantes {#view-import-configuration}

Si vous choisissez d’enregistrer la configuration après sa création, celle-ci s’affiche dans l’onglet **[!UICONTROL Imports enregistrés]**.

![Enregistrement de la configuration d’import en bloc.](assets/bulk-import-save.png)

Si vous choisissez d’enregistrer et d’exécuter l’import, la configuration de celui-ci s’affiche dans l’onglet **[!UICONTROL Imports exécutés]**.

![Enregistrement de la configuration d’import en bloc.](assets/bulk-import-executed.png)

Si vous planifiez un import, il s’affiche dans l’onglet **[!UICONTROL Imports planifiés]**.

## Modifier la configuration d’import en bloc {#edit-import-configuration}

Pour modifier les détails de configuration, cliquez sur Plus d’options (...) correspondant au nom de la configuration, puis cliquez sur **[!UICONTROL Modifier]**. Notez que certains éléments ne sont pas modifiables, tels que le titre de la configuration et la source de données d’import. Vous pouvez modifier la configuration à l’aide des onglets Imports exécutés, planifiés ou enregistrés.

![Modification de la configuration d’import en bloc.](assets/bulk-import-edit.png)

## Planifier des imports ponctuels ou récurrents {#schedule-imports}

Pour planifier un import en bloc ponctuel ou récurrent, procédez comme suit :

1. Cliquez sur Plus d’options (...) correspondant au nom de configuration disponible dans la **[!UICONTROL Imports exécutés]** ou **[!UICONTROL Imports enregistrés]** et cliquez sur **[!UICONTROL Planification]**. Vous pouvez également replanifier un import planifié existant en accédant à l’onglet **[!UICONTROL Imports planifiés]** et en cliquant sur **[!UICONTROL Planifier]**.

1. Définissez une ingestion ponctuelle ou planifiez une planification horaire, quotidienne ou hebdomadaire. Cliquez sur **[!UICONTROL Envoyer]**.

   ![Planification de la configuration d’import en bloc.](assets/bulk-import-schedule.png)

## Exécuter un contrôle de l’intégrité de l’import {#import-health-check}

Pour valider la connexion à la source de données, cliquez sur Autres options (...) correspondant au nom de la configuration, puis cliquez sur **[!UICONTROL Vérifier]**. Si la connexion est établie, Experience Manager Assets affiche le message suivant :

![Vérification de l’intégrité de l’import en bloc.](assets/bulk-import-health-check.png)

## Effectuer un essai avant l’exécution d’un import {#dry-run-bulk-import}

Cliquez sur Autres options (...) correspondant au nom de la configuration, puis cliquez sur **[!UICONTROL Exécution d’essai]** pour appeler une exécution de test pour la tâche d’importation en bloc. Experience Manager Assets affiche les informations suivantes sur la tâche d’import en bloc :

![Vérification de l’intégrité de l’import en bloc.](assets/bulk-import-dry-run.png)

## Exécuter un import en bloc {#run-bulk-import}

Si vous avez enregistré l’importation lors de la création de la configuration, vous pouvez accéder à l’onglet Imports enregistrés , cliquer sur Plus d’options (...) correspondant à la configuration et cliquer sur **[!UICONTROL Exécuter]**.

De même, si vous devez exécuter un import déjà exécuté, accédez à l&#39;onglet Imports exécutés , cliquez sur Plus d&#39;options (...) correspondant au nom de la configuration et cliquez sur **[!UICONTROL Exécuter]**.

## Arrêter ou planifier un import en cours {#schedule-stop-ongoing-report}

Vous pouvez planifier ou arrêter un import en bloc en cours à l’aide de la boîte de dialogue de statut d’import en bloc qui s’affiche sur la page d’accueil de l’import en bloc au cours d’un import.

![Import en cours.](assets/bulk-import-progress.png)

Vous pouvez également afficher les ressources importées dans le dossier cible en cliquant sur **[!UICONTROL Afficher les ressources]**.


## Supprimer une configuration d’import en bloc {#delete-bulk-import-configuration}

Cliquez sur Autres options (...) correspondant au nom de configuration existant dans **[!UICONTROL Imports exécutés]**, **[!UICONTROL Imports planifiés]**, ou **[!UICONTROL Imports enregistrés]** onglets et clic **[!UICONTROL Supprimer]** pour supprimer la configuration Import en bloc .

## Accéder aux ressources après l’exécution de l’import en bloc {#view-assets-after-bulk-import}

Pour afficher l’emplacement cible Ressources où les ressources sont importées après l’exécution de la tâche d’importation en bloc, cliquez sur Autres options (...) correspondant au nom de la configuration, puis cliquez sur **[!UICONTROL Affichage des ressources]**.
