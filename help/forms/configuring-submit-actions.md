---
title: Comment configurer une action Envoyer pour un formulaire adaptatif ?
description: Un formulaire adaptatif fournit plusieurs actions Envoyer. Une action Envoyer définit le mode de traitement d’un formulaire adaptatif après l’envoi. Vous pouvez utiliser des actions Envoyer intégrées ou créer les vôtres.
feature: Adaptive Forms, Foundation Components
exl-id: a4ebedeb-920a-4ed4-98b3-2c4aad8e5f78
role: User, Developer
source-git-commit: db0487ab11f48690cb36b410b895324e0d4cf684
workflow-type: tm+mt
source-wordcount: '3929'
ht-degree: 84%

---

# Action Envoyer pour formulaire adaptatif {#configuring-the-submit-action}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html) |
| AEM as a Cloud Service (composants principaux) | [Cliquez ici](/help/forms/configure-submit-actions-core-components.md) |
| AEM as a Cloud Service (composants de base) | Cet article |

**S’applique à** : ✔️ Composants de base de formulaire adaptatif. ❌ [Composants principaux de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md). Adobe recommande d’utiliser les composants principaux pour [ajouter Forms adaptatif à une page AEM Sites](create-or-add-an-adaptive-form-to-aem-sites-page.md) ou [créer une Forms adaptatif autonome](creating-adaptive-form-core-components.md).

Une action d’envoi est déclenchée lorsqu’un utilisateur clique sur le bouton **[!UICONTROL Envoyer]** d’un formulaire adaptatif. Forms as a Cloud Service fournit les actions d’envoi suivantes prêtes à l’emploi.

* [Envoyer vers le point d’entrée REST](#submit-to-rest-endpoint)
* [Envoyer un e-mail](#send-email)
* [Envoyer en mode de données de formulaire (FDM) l](#submit-using-form-data-model)
* [Appeler un workflow AEM](#invoke-an-aem-workflow)
* [Envoyer à SharePoint](#submit-to-sharedrive)
* [Envoyer à OneDrive](#submit-to-onedrive)
* [Envoyer au stockage Blob Azure](#azure-blob-storage)
* [Envoyer à Power Automate](#microsoft-power-automate)
* [Envoyer vers Workfront Fusion](#workfront-fusion)
* [Envoyer à Marketo Engage](/help/forms/integrate-form-to-marketo-engage.md)

Vous pouvez également [étendre les actions d’envoi par défaut](custom-submit-action-form.md) pour créer votre propre action d’envoi.

Vous pouvez configurer une action d’envoi dans la section **[!UICONTROL Envoi]** des propriétés du conteneur de formulaire adaptatif, dans la barre latérale.

![Configuration de l’action d’envoi](assets/submission.png)


<!-- [!NOTE]
>
>Send PDF via Email Submit Action is applicable only to Adaptive Forms that use XFA template as form model. 

>[!NOTE]
>
>Ensure that the [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder
>exists. The directory is required to temporarily store attachments. If the directory does not exist, create it. -->

<!--

>[!CAUTION]
>
>If you  [prefill](prepopulate-adaptive-form-fields.md) a form template,  a Form Data Model or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema , form template, or form data model) that is data does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost. 

>[!CAUTION]
>
>If you [prefill](prepopulate-adaptive-form-fields.md) a form template, a Form Data Model or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema, or form data model) that does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost.
-->

## Envoyer vers le point d’entrée REST {#submit-to-rest-endpoint}

Utilisez l’action **[!UICONTROL Envoyer vers le point d’entrée REST]** pour transmettre les données envoyées à l’URL REST. L’URL peut être celle d’un serveur interne (le serveur sur lequel le formulaire est rendu) ou externe.

Pour publier des données sur un serveur interne, indiquez le chemin de la ressource. Les données sont publiées avec le chemin de la ressource. Par exemple, /content/restEndPoint. Pour ces requêtes de publication, les informations d’authentification de la requête d’envoi sont utilisées.

Pour publier des données sur un serveur externe, indiquez une URL. Le format d’URL est le suivant : `https://host:port/path_to_rest_end_point`. Assurez-vous de configurer le chemin pour que la requête POST soit traitée anonymement.

![Mappage pour la transmission des valeurs de champs sous forme de paramètres de page de remerciement](assets/post-enabled-actionconfig.png)

Dans l’exemple ci-dessus, les informations saisies par l’utilisateur dans `textbox` sont capturées au moyen du paramètre `param1`. La syntaxe permettant de publier les données capturées au moyen de `param1` est :

`String data=request.getParameter("param1");`

De même, les paramètres que vous utilisez pour publier des données XML et des pièces jointes sont `dataXml` et `attachments`.

Par exemple, vous utilisez ces deux paramètres dans votre script pour analyser les données à un point d’entrée REST. Vous utilisez la syntaxe suivante pour stocker et analyser les données :

`String data=request.getParameter("dataXml");`
`String att=request.getParameter("attachments");`

Dans cet exemple, `data` contient les données XML et `att` les données des pièces jointes.

L’option d’envoi **[!UICONTROL Envoyer vers le point d’entrée REST]** transmet les données renseignées dans le formulaire à une page de confirmation configurée dans le cadre de la requête HTTP GET. Vous pouvez ajouter le nom des champs à demander. Le format de la requête est :

`{fieldName}={request parameter name}`

Comme illustré ci-dessous, `param1` et `param2` sont transmis en tant que paramètres avec des valeurs copiées à partir des champs **textbox** et **numericbox** pour la prochaine action.

![Configuration de l’action Envoyer vers le point d’entrée REST](assets/action-config.png)

Vous pouvez également **[!UICONTROL Activer la requête POST]** et fournir une URL pour la publication de la requête. Pour envoyer des données au serveur AEM qui héberge le formulaire, utilisez un chemin d’accès relatif correspondant au chemin racine du serveur AEM. Par exemple, `/content/forms/af/SampleForm.html`. Pour envoyer des données vers un autre serveur, utilisez un chemin d’accès absolu.

>[!NOTE]
>
>Pour transmettre les champs en tant que paramètres dans une URL REST, tous les champs doivent avoir des noms d’éléments différents, même s’ils sont placés sur différents panneaux.

## Envoyer un e-mail {#send-email}

Vous pouvez utiliser l’action d’envoi **[!UICONTROL Envoyer un e-mail]** pour envoyer un e-mail à un ou à plusieurs destinataires lors de l’envoi réussi du formulaire. Le message généré peut contenir des données de formulaire dans un format prédéfini. Par exemple, dans le modèle suivant, le nom du client, l’adresse d’expédition, le nom de l’État et le code postal sont récupérés à partir des données de formulaire envoyées.

    &quot;
    
    Hi ${customer_Name},
    
    Les paramètres suivants sont définis comme votre adresse de livraison par défaut :
    ${customer_Name},
    ${customer_Shipping_Address},
    ${customer_State},
    ${customer_ZIPCode}
    
    Regards,
    WKND
    
    &quot;

>[!NOTE]
>
> * Tous les champs de formulaire doivent avoir des noms d’élément différents, même si les champs sont placés sur différents panneaux d’un formulaire adaptatif.
> * AEM as a Cloud Service exige que le e-mails sortants soient chiffrés. Par défaut, les e-mails sortants sont désactivés. Pour les désactiver, envoyez un ticket d’assistance à [Demande d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#sending-email).

Vous pouvez également inclure des pièces jointes et un document d’enregistrement (DE) à l’e-mail. Pour activer l’option **[!UICONTROL Joindre le document d’enregistrement]**, configurez le formulaire adaptatif pour générer un document d’enregistrement (DE). Vous pouvez activer cette option pour générer un document d’enregistrement à partir des propriétés de formulaire adaptatif.



<!-- ## Send PDF via Email {#send-pdf-via-email}

The **Send PDF via Email** Submit Action sends an email with a PDF containing form data, to one or more recipients on successful submission of the form.

>[!NOTE]
>
>This Submit Action is available for XFA-based Adaptive Forms and XSD-based adaption forms that have the Document of Record template. -->

<!-- ## Invoke a forms workflow {#invoke-a-forms-workflow}

The **Submit to Forms workflow** submit option sends a data xml and file attachments (if any) to an existing Adobe LiveCycle or [!DNL AEM Forms] on JEE process.

For information about how to configure the Submit to forms workflow Submit Action, see [Submitting and processing your form data using forms workflows](submit-form-data-livecycle-process.md). -->

## Envoyer à l’aide du modèle de données de formulaire (FDM) {#submit-using-form-data-model}

L’action d’envoi **[!UICONTROL Envoyer à l’aide du modèle de données de formulaire]** écrit les données de formulaire adaptatif envoyées pour l’objet de modèle de données spécifié dans un modèle de données de formulaire (FDM) dans sa source de données. Lors de la configuration de l’action d’envoi, vous pouvez sélectionner un objet de modèle de données dont vous souhaitez écrire les données envoyées dans sa source de données.

En outre, vous pouvez envoyer une pièce jointe de formulaire à l’aide d’un modèle de données de formulaire (FDM) et d’un document d’enregistrement (DoR) à la source de données. Pour plus d’informations sur le modèle de données de formulaire (FDM), voir [[!DNL AEM Forms] Intégration de données](data-integration.md).

<!--
## Forms Portal Submit Action {#forms-portal-submit-action}

The **Forms Portal Submit Action** option makes form data available through an [!DNL AEM Forms] portal.

For more information about the Forms Portal and Submit Action, see [Drafts and submissions component](draft-submission-component.md). -->

## Appeler un processus AEM {#invoke-an-aem-workflow}

L’action d’envoi **[!UICONTROL Appeler un processus AEM]** associe un formulaire adaptatif à un [processus AEM](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr#extending-aem). Lorsqu’un formulaire est envoyé, le processus associé commence automatiquement sur l’instance de création. Vous pouvez enregistrer le fichier de données, les pièces jointes et le document d’enregistrement à l’emplacement de la payload du workflow ou dans une variable. Si le processus est marqué pour le stockage de données externe et configuré pour un stockage de données externe, seule l’option variable est disponible. Vous pouvez choisir dans la liste des variables disponibles pour le modèle de workflow. Si le processus est marqué pour le stockage des données externes à une étape ultérieure et non au moment de la création du processus, assurez-vous que les configurations de variable requises sont en place.

L’action Envoyer place les éléments suivants à l’emplacement de la payload du workflow, ou de la variable si le workflow est marqué pour le stockage de données externe :

* **Fichier de données** : Il contient les données envoyées au formulaire adaptatif. Vous pouvez utiliser l’option **[!UICONTROL Chemin d’accès au fichier de données]** pour spécifier le nom du fichier et le chemin d’accès du fichier par rapport à la charge utile. Par exemple, le chemin d’accès `/addresschange/data.xml` crée un dossier nommé `addresschange` et le place par rapport à la charge utile. Vous pouvez également spécifier uniquement `data.xml` pour envoyer uniquement les données envoyées sans créer de hiérarchie de dossiers. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.

* **Pièces jointes** : vous pouvez utiliser l’option **[!UICONTROL Chemin d’accès aux pièces jointes]** pour spécifier le nom de dossier dans lequel stocker les pièces jointes chargées dans le formulaire adaptatif. Le dossier est créé par rapport à la payload. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.

* **Document d’enregistrement** : il contient le document d’enregistrement généré pour le formulaire adaptatif. Vous pouvez utiliser l’option **[!UICONTROL Chemin du document d’enregistrement]** pour spécifier le nom du fichier de document d’enregistrement et le chemin d’accès du fichier par rapport à la charge utile. Par exemple, le chemin d’accès `/addresschange/DoR.pdf` crée un dossier nommé `addresschange` relatif à la charge utile et place `DoR.pdf` relatif à la charge utile. Vous pouvez également spécifier uniquement `DoR.pdf` pour n’enregistrer que le document d’enregistrement sans créer de hiérarchie de dossiers. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.

Avant d’utiliser l’action Envoyer **[!UICONTROL Appeler un processus AEM]**, configurez les éléments suivants pour la configuration du **[!UICONTROL service de paramètres AEM DS]** :

* **[!UICONTROL URL du serveur de traitement]** : le serveur de traitement est le serveur sur lequel le processus Forms ou AEM est déclenché. Il peut s’agir de l’URL de l’instance de création AEM ou d’un autre serveur.

* **[!UICONTROL Nom d’utilisateur du serveur de traitement]** : nom d’utilisateur de l’utilisateur ou de l’utilisatrice du workflow

* **[!UICONTROL Mot de passe du serveur de traitement]** : mot de passe de l’utilisateur ou de l’utilisatrice du workflow

## Envoyer à SharePoint {#submit-to-sharedrive}

L’action de soumission **[!UICONTROL Soumettre à SharePoint]** connecte un formulaire adaptatif à un stockage Microsoft® SharePoint. Vous pouvez envoyer le fichier de données de formulaire, les pièces jointes ou le document d’enregistrement au stockage Microsoft® SharePoint connecté.

Grâce à l’option Envoyer à SharePoint, vous pouvez :
* [Connexion d’un formulaire adaptatif à la bibliothèque de documents SharePoint](#connect-af-sharepoint-doc-library)
* [Connecter un formulaire adaptatif à la liste SharePoint](#connect-af-sharepoint-list)


### Connexion d’un formulaire adaptatif à la bibliothèque de documents SharePoint {#connect-af-sharepoint-doc-library}

Pour utiliser l’action d’envoi **[!UICONTROL Submit to SharePoint Document Library]** dans un formulaire adaptatif :

1. [Créer une configuration de bibliothèque de documents SharePoint](#create-a-sharepoint-configuration-create-sharepoint-configuration) : elle connecte AEM Forms à votre stockage Microsoft® SharePoint.
2. [Utiliser l’action d’envoi Soumettre à SharePoint dans un formulaire adaptatif](#use-sharepoint-configuartion-in-af) : connecte votre formulaire adaptatif au stockage Microsoft® SharePoint configuré.

#### Création d’une configuration Bibliothèque de documents SharePoint {#create-sharepoint-configuration}

Pour connecter AEM Forms à votre stockage de bibliothèque de documents Microsoft® SharePoint, procédez comme suit :

1. Accédez à votre instance de **création AEM Forms** > **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Une fois que vous avez sélectionné le stockage **[!UICONTROL Microsoft® SharePoint]**, l’interface vous redirige vers le **[!UICONTROL navigateur SharePoint]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Bibliothèque de documents SharePoint]** dans la liste déroulante. L’assistant de configuration SharePoint s’affiche.

   ![Configuration de SharePoint](/help/forms/assets/sharepoint_configuration.png)
1. Spécifiez le **[!UICONTROL titre]**, l’**[!UICONTROL ID client]**, le **[!UICONTROL secret client]** et l’**[!UICONTROL URL OAuth]**. Pour savoir comment récupérer l’ID client et le secret client pour l’URL OAuth, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
   * Vous pouvez récupérer l’`Client ID` et le `Client Secret` de votre application sur le portail Microsoft® Azure.
   * Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
   * Ajoutez les autorisations d’API `offline_access` et `Sites.Manage.All` pour fournir les autorisations de lecture/écriture.
   * Utilisez l’URL OAuth `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

   >[!NOTE]
   >
   > Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. Cliquez sur **[!UICONTROL Connecter]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.

1. Maintenant, sélectionnez **Site SharePoint** > **Bibliothèque de documents** > **Dossier SharePoint**, pour enregistrer les données.

   >[!NOTE]
   >
   >* Par défaut, `forms-ootb-storage-adaptive-forms-submission` est présent sur le site SharePoint sélectionné.
   >* Créez un dossier sous la forme `forms-ootb-storage-adaptive-forms-submission`, s’il n’est pas déjà présent dans la bibliothèque `Documents` du site SharePoint sélectionné en cliquant sur **Créer un dossier**.

Vous pouvez désormais utiliser cette configuration de sites SharePoint pour l’action d’envoi dans un formulaire adaptatif.

#### Utilisation de la configuration de la bibliothèque de documents SharePoint dans un formulaire adaptatif {#use-sharepoint-configuartion-in-af}

Vous pouvez utiliser la configuration de la bibliothèque de documents SharePoint créée dans un formulaire adaptatif pour enregistrer des données ou générer un document d’enregistrement dans un dossier SharePoint. Pour utiliser une configuration de stockage de la bibliothèque de documents SharePoint dans un formulaire adaptatif, procédez comme suit :

1. Créez un [formulaire adaptatif](/help/forms/creating-adaptive-form.md).

   >[!NOTE]
   >
   > * Sélectionnez le même [!UICONTROL Conteneur de configuration] pour un formulaire adaptatif, où vous avez créé votre stockage dans la bibliothèque de documents SharePoint.
   > * Si aucun [!UICONTROL conteneur de configuration] n’est sélectionné, les dossiers de [!UICONTROL configuration de stockage] globaux s’affichent dans la fenêtre des propriétés de l’action d’envoi.

1. Sélectionnez l’**action d’envoi** **[!UICONTROL Soumettre à SharePoint]**.
   ![GIF SharePoint](/help/forms/assets/sharedrive-video.gif)
1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

Lorsque vous envoyez le formulaire, les données sont enregistrées dans le stockage de la bibliothèque de documents Microsoft® SharePoint spécifié.
La structure du dossier pour l’enregistrement des données est `/folder_name/form_name/year/month/date/submission_id/data`.

### Connecter un formulaire adaptatif à une liste Microsoft® SharePoint {#connect-af-sharepoint-list}

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

Pour utiliser l’action de soumission [!UICONTROL Soumettre à la liste SharePoint] dans un formulaire adaptatif :

1. [Créer une configuration de liste SharePoint](#create-sharepoint-list-configuration) : connecte AEM Forms à votre stockage de listes Microsoft® SharePoint.
1. [Utilisez Submit using Form Data Model (FDM) dans un formulaire adaptatif](#use-submit-using-fdm) : il connecte votre formulaire adaptatif à Microsoft® SharePoint configuré.

#### Créer une configuration de liste SharePoint {#create-sharepoint-list-configuration}

Pour connecter AEM Forms à votre liste Microsoft® SharePoint :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Liste SharePoint]** dans la liste déroulante. L’assistant de configuration SharePoint s’affiche.
1. Spécifiez le **[!UICONTROL titre]**, l’**[!UICONTROL ID client]**, le **[!UICONTROL secret client]** et l’**[!UICONTROL URL OAuth]**. Pour savoir comment récupérer l’ID client et le secret client pour l’URL OAuth, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
   * Vous pouvez récupérer l’`Client ID` et le `Client Secret` de votre application sur le portail Microsoft® Azure.
   * Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
   * Ajoutez les autorisations d’API `offline_access` et `Sites.Manage.All` dans l’onglet **Graphique Microsoft®** pour fournir des autorisations de lecture/écriture. Ajoutez l’autorisation `AllSites.Manage` dans l’onglet **Sharepoint** pour interagir à distance avec les données SharePoint.
   * Utilisez l’URL OAuth `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

     >[!NOTE]
     >
     > Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. Cliquez sur **[!UICONTROL Connecter]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.
1. Sélectionnez **[!UICONTROL Site SharePoint]** et **[!UICONTROL Liste SharePoint]** dans la liste déroulante.
1. Sélectionnez **[!UICONTROL Créer]** pour créer la configuration de cloud pour Microsoft® SharePointList.


#### Utilisation de l’option Submit using Form Data Model (FDM) dans un formulaire adaptatif {#use-submit-using-fdm}

Vous pouvez utiliser la configuration de liste SharePoint créée dans un formulaire adaptatif pour enregistrer des données ou un document d’enregistrement généré dans une liste SharePoint. Suivez les étapes ci-dessous pour utiliser une configuration de stockage de listes SharePoint dans un formulaire adaptatif :

1. [Création d’un modèle de données de formulaire (FDM) à l’aide de la configuration de liste SharePoint Microsoft®](/help/forms/create-form-data-models.md)
1. [Configuration du modèle de données de formulaire (FDM) pour récupérer et envoyer des données](/help/forms/work-with-form-data-model.md#configure-services)
1. [Créer un formulaire adaptatif](/help/forms/creating-adaptive-form.md)
1. [Configuration de l’action Envoyer à l’aide d’un modèle de données de formulaire (FDM)](/help/forms/configuring-submit-actions.md#submit-using-form-data-model)

Lorsque vous soumettez le formulaire, les données sont enregistrées dans le stockage de listes Microsoft® SharePoint que vous avez spécifié.

>[!NOTE]
>
> Dans la liste Microsoft® SharePoint, les types de colonnes suivants ne sont pas pris en charge :
> * Colonne image
> * Colonne métadonnées
> * Colonne personne
> * Colonne données externes


## Envoyer à OneDrive {#submit-to-onedrive}

L’action d’envoi **[!UICONTROL Soumettre à OneDrive]** connecte un formulaire adaptatif à un stockage Microsoft® OneDrive. Vous pouvez envoyer les données de formulaire, les fichiers, les pièces jointes ou le document d’enregistrement au stockage Microsoft® OneDrive connecté. Pour utiliser l’action d’envoi [!UICONTROL Envoyer à OneDrive] dans un formulaire adaptatif :

1. [Créer une configuration OneDrive](#create-a-onedrive-configuration-create-onedrive-configuration) : connecte AEM Forms à votre stockage Microsoft® OneDrive.
2. [Utiliser l’action d’envoi Soumettre à OneDrive dans un formulaire adaptatif](#use-onedrive-configuration-in-an-adaptive-form-use-onedrive-configuartion-in-af) : connecte votre formulaire adaptatif au
stockage Microsoft® OneDrive configuré.

### Créer une configuration OneDrive {#create-onedrice-configuration}

Pour connecter AEM Forms à votre stockage Microsoft® OneDrive :

1. Accédez à votre instance de **création AEM Forms** > **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Microsoft® OneDrive]**.
1. Une fois que vous avez sélectionné le stockage **[!UICONTROL Microsoft® OneDrive]**, l’interface vous redirige vers le **[!UICONTROL navigateur OneDrive]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]**. L’assistant de configuration OneDrive s’affiche.

   ![Écran de configuration OneDrive](/help/forms/assets/onedrive-configuration.png)

1. Spécifiez le **[!UICONTROL titre]**, l’**[!UICONTROL ID client]**, le **[!UICONTROL secret client]** et l’**[!UICONTROL URL OAuth]**. Pour savoir comment récupérer l’ID client et le secret client pour l’URL OAuth, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
   * Vous pouvez récupérer l’`Client ID` et le `Client Secret` de votre application sur le portail Microsoft® Azure.
   * Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/onedrive/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
   * Ajoutez les autorisations d’API `offline_access` et `Files.ReadWrite.All` pour fournir les autorisations de lecture/écriture.
   * Utilisez l’URL OAuth `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

   >[!NOTE]
   >
   > Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. Cliquez sur **[!UICONTROL Connecter]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.

1. Sélectionnez à présent **[!UICONTROL Conteneur OneDrive]** > **[Dossier OneDrive]** pour enregistrer les données.

   >[!NOTE]
   >
   >* Par défaut, `forms-ootb-storage-adaptive-forms-submission` se trouve dans le conteneur OneDrive.
   > * Créez un dossier tel que `forms-ootb-storage-adaptive-forms-submission`, le cas échéant, en cliquant sur **Créer un dossier**.

Vous pouvez désormais utiliser cette configuration de stockage OneDrive pour l’action d’envoi dans un formulaire adaptatif.

### Utiliser la configuration OneDrive dans un formulaire adaptatif {#use-onedrive-configuartion-in-af}

Vous pouvez utiliser la configuration de stockage OneDrive créée dans un formulaire adaptatif pour enregistrer des données ou un document d’enregistrement généré dans un dossier OneDrive. Suivez les étapes ci-après pour utiliser la configuration de stockage OneDrive dans un formulaire adaptatif :
1. Créez un [formulaire adaptatif](/help/forms/creating-adaptive-form.md).

   >[!NOTE]
   >
   > * Sélectionnez le même [!UICONTROL conteneur de configuration] pour le formulaire adaptatif dans lequel vous avez créé votre espace de stockage OneDrive.
   > * Si aucun [!UICONTROL conteneur de configuration] n’est sélectionné, les dossiers de [!UICONTROL configuration de stockage] globaux s’affichent dans la fenêtre des propriétés de l’action d’envoi.

1. Sélectionnez l’**action Envoyer** pour **[!UICONTROL Envoyer à OneDrive]**.
   ![GIF OneDrive](/help/forms/assets/onedrive-video.gif)
1. Sélectionnez la **[!UICONTROL configuration de stockage]** dans laquelle enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

Lorsque vous soumettez le formulaire, les données sont enregistrées dans le stockage Microsoft® OneDrive que vous avez spécifié.
La structure du dossier pour l’enregistrement des données est `/folder_name/form_name/year/month/date/submission_id/data`.

## Envoyer au stockage Blob Azure {#submit-to-azure-blob-storage}

L’action d’envoi **[!UICONTROL Envoyer au stockage Azure Blob]** connecte un formulaire adaptatif à un portail Microsoft® Azure. Vous pouvez envoyer les données de formulaire, le fichier, les pièces jointes ou le document d’enregistrement aux conteneurs de stockage Azure connectés. Pour utiliser l’action Envoyer pour le stockage Azure Blob :

1. [Créer un conteneur de stockage Azure Blob](#create-a-azure-blob-storage-container-create-azure-configuration) : connecte AEM Forms aux conteneurs de stockage Azure.
2. [Utiliser la configuration de stockage Azure dans un formulaire adaptatif](#use-azure-storage-configuration-in-an-adaptive-form-use-azure-storage-configuartion-in-af) : cela connecte votre formulaire adaptatif aux conteneurs de stockage Azure configurés.

### Créer un conteneur de stockage Azure Blob {#create-azure-configuration}

Pour connecter AEM Forms à vos conteneurs de stockage Azure :
1. Accédez à l’instance de **création AEM Forms** > **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Stockage Azure]**.
1. Sélectionnez **[!UICONTROL Stockage Azure]** pour accéder au **[!UICONTROL Navigateur de stockage Azure]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]**. L’assistant Créer une configuration de stockage Azure s’affiche.

   ![Configuration du stockage Azure](/help/forms/assets/azure-storage-configuration.png)

1. Spécifiez le **[!UICONTROL titre]**, le **[!UICONTROL compte de stockage Azure]** et la **[!UICONTROL clé d’accès Azure]**.

   * Vous pouvez récupérer le nom du `Azure Storage Account` et la `Azure Access key` à partir des comptes de stockage sur le portail Microsoft® Azure.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Désormais, vous pouvez utiliser cette configuration de conteneur de stockage Azure pour l’action d’envoi dans un formulaire adaptatif.

### Utiliser la configuration de stockage Azure dans un formulaire adaptatif {#use-azure-storage-configuartion-in-af}

Vous pouvez utiliser la configuration de conteneur de stockage Azure créée dans un formulaire adaptatif pour enregistrer des données ou un document d’enregistrement généré dans le conteneur de stockage Azure. Suivez les étapes ci-après pour utiliser la configuration de conteneur de stockage Azure dans un formulaire adaptatif :
1. Créez un [formulaire adaptatif](/help/forms/creating-adaptive-form.md).

   >[!NOTE]
   >
   > * Sélectionnez le même [!UICONTROL conteneur de configuration] pour le formulaire adaptatif dans lequel vous avez créé votre espace de stockage OneDrive.
   > * Si aucun [!UICONTROL conteneur de configuration] n’est sélectionné, les dossiers de [!UICONTROL configuration de stockage] globaux s’affichent dans la fenêtre des propriétés de l’action d’envoi.

1. Sélectionnez l’**action Envoyer** pour **[!UICONTROL Soumettre au stockage Azure Blob]**.
   ![GIF de stockage Azure Blob](/help/forms/assets/azure-submit-video.gif)

1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

Lorsque vous envoyez le formulaire, les données sont enregistrées dans la configuration de conteneur de stockage Azure spécifié.
La structure du dossier pour l’enregistrement des données est `/configuration_container/form_name/year/month/date/submission_id/data`.

Pour définir les valeurs d’une configuration, [générez des configurations OSGi à l’aide du SDK AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#generating-osgi-configurations-using-the-aem-sdk-quickstart) et [déployez la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#deployment-process) sur votre instance de Cloud Service.


## Envoyer à Power Automate {#microsoft-power-automate}

Vous pouvez configurer un formulaire adaptatif pour exécuter un flux cloud Power Automate lors de l’envoi. Le formulaire adaptatif configuré envoie les données capturées, les pièces jointes et le document d’enregistrement au flux Cloud Power Automate pour traitement. Il vous permet de créer une expérience de capture de données personnalisée tout en tirant parti de la puissance de Microsoft® Power Automate pour élaborer des logiques commerciales autour des données capturées et automatiser les workflows client. Voici quelques exemples de ce que vous pouvez faire après l’intégration d’un formulaire adaptatif à Microsoft® Power Automate :

* Utiliser des données de formulaires adaptatifs dans des processus d’entreprise Power Automate
* Utilisez Power Automate pour envoyer des données capturées à plus de 500 sources de données ou à toute API publique
* Exécuter des calculs complexes sur les données capturées
* Enregistrer des données de formulaires adaptatifs dans les systèmes de stockage selon un planning prédéfini

L’éditeur de formulaires adaptatifs fournit l’action d’envoi **Appeler un flux Microsoft® Power Automate** pour envoyer des données de formulaires adaptatifs et des pièces jointes, et un document d’enregistrement est envoyé au flux de cloud Power Automate. Pour utiliser l’action Envoyer afin d’envoyer les données capturées à Microsoft® Power Automate, [connectez votre instance Forms as a Cloud Service à Microsoft® Power Automate](forms-microsoft-power-automate-integration.md).

Une fois la configuration réussie, utilisez l’action d’envoi [Appeler un flux Microsoft® Power Automate](forms-microsoft-power-automate-integration.md#use-the-invoke-a-microsoft&reg;-power-automate-flow-submit-action-to-send-data-to-a-power-automate-flow-use-the-invoke-microsoft-power-automate-flow-submit-action) pour envoyer des données à un flux Power Automate.

## Envoyer vers Workfront Fusion {#workfront-fusion}

Vous pouvez configurer un formulaire adaptatif pour envoyer des données à Workfront Fusion lors de l’envoi. Workfront Fusion permet l’automatisation des processus afin que l’utilisateur puisse se concentrer sur de nouvelles tâches plutôt que de répéter les mêmes tâches encore et encore. Il automatise les tâches simples et complexes, ce qui permet de gagner du temps et d’assurer une exécution cohérente des processus.

L’éditeur de Forms adaptatif fournit l’action d’envoi **Invoke a Workfront Fusion Scenario** pour envoyer des données ou des pièces jointes à un scénario de fusion Workfront. Pour utiliser l’action d’envoi pour envoyer des données capturées à un scénario de fusion Workfront, reportez-vous à la section [Envoi d’un formulaire adaptatif à Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md).

## Utiliser l’envoi synchrone ou asynchrone {#use-synchronous-or-asynchronous-submission}

Une action d’envoi peut utiliser un envoi synchrone ou asynchrone.

**Envoi synchrone** : traditionnellement, les formulaires web sont configurés à des fins d’envoi synchrone. Dans un envoi synchrone, lorsque les utilisateurs envoient un formulaire, ils sont redirigés vers une page d’accusé de réception, une page de remerciement ou, en cas d’échec de l’envoi, une page d’erreur. Vous pouvez sélectionner l’option **[!UICONTROL Utiliser l’envoi asynchrone]** pour rediriger les utilisateurs vers une page web ou afficher un message lors de l’envoi.

![Configuration de l’action d’envoi](assets/thank-you-setting.png)

**Envoi asynchrone**: les expériences web modernes telles que les application d’une seule page gagnent en popularité. Dans une application de ce type, la page web reste statique tandis que l’interaction entre le client et le serveur se déroule en arrière-plan. [Vous pouvez désormais fournir cette expérience avec des formulaires adaptatifs en configurant l’envoi asynchrone](asynchronous-submissions-adaptive-forms.md).

## Revalidation côté serveur dans un formulaire adaptatif {#server-side-revalidation-in-adaptive-form}

En règle générale, dans n’importe quel système de capture de données en ligne, les développeurs placent des validations JavaScript côté client pour appliquer des règles métier. Mais dans les navigateurs modernes, les utilisateurs finaux peuvent contourner ces validations et effectuer les envois manuellement à l’aide de différentes méthodes, comme la console Web Browser DevTools. Ces méthodes sont également valables pour les formulaires adaptatifs. Un développeur de formulaires peut créer différentes logiques de validation, mais techniquement, les utilisateurs finaux peuvent contourner ces logiques de validation et soumettre des données non valides au serveur. Les données non valides enfreindraient les règles métier appliquées par un créateur ou une créatrice de formulaires.

La fonction de revalidation côté serveur permet également d’exécuter les validations fournies par un auteur de formulaires adaptatifs lors de la conception d’un formulaire adaptatif sur le serveur. Elle empêche toute erreur lors des envois de données et toute violation des règles de fonctionnement représentées en termes de validations de formulaire.

### Quels éléments valider sur le serveur ?  {#what-to-validate-on-server-br}

Les champs de validation en standard d’un formulaire adaptatif réexécutés sur le serveur sont les suivants :

* Requis
* Clause d’image de validation
* Expression de validation

### Activation de la validation côté serveur {#enabling-server-side-validation-br}

Utilisez **[!UICONTROL Revalider sur le serveur]** sous le conteneur de formulaires adaptatifs dans la zone latérale pour activer ou désactiver la validation côté serveur pour le formulaire actif.

![Activation de la validation côté serveur](assets/revalidate-on-server.png)

Activer la validation côté serveur

Si l’utilisateur final ou l’utilisatrice finale contourne ces validations et soumet les formulaires, le serveur effectue à nouveau la validation. Si la validation échoue du côté du serveur, la transaction d’envoi est arrêtée. Le formulaire d’origine est de nouveau présenté à l’utilisateur. Pour l’utilisateur, les données capturées et les données envoyées s’affichent en tant qu’erreurs.

>[!NOTE]
>
>La validation côté serveur permet de valider le modèle de formulaire. Il est recommandé de créer une bibliothèque client séparée pour les validations et de ne pas la mélanger à d’autres éléments. Par exemple, ne placez pas le style HTML et la manipulation DOM HTML dans la même bibliothèque client.

### Prendre en charge des fonctions personnalisées dans les expressions de validation {#supporting-custom-functions-in-validation-expressions-br}

Parfois, en cas de **règles de validation complexes**, le script de validation exact réside dans des fonctions personnalisées que l’auteur doit appeler à partir de l’expression du champ de validation. Pour rendre cette bibliothèque de fonctions personnalisées visible et disponible lors des validations côté serveur, l’auteur de formulaires peut configurer le nom de la bibliothèque cliente AEM sous l’onglet **[!UICONTROL Réglages de base]** des propriétés de conteneur de formulaires adaptatifs comme illustré ci-dessous.

![Prise en charge des fonctions personnalisées dans les expressions de validation](assets/clientlib-cat.png)

Prendre en charge des fonctions personnalisées dans les expressions de validation

L’auteur peut configurer la bibliothèque personnalisée JavaScript pour chaque formulaire adaptatif. Dans la bibliothèque, conservez uniquement les fonctions réutilisables ayant une dépendance sur les bibliothèques tierces jquery et underscore.js.

## Gérer les erreurs sur l’action d’envoi {#error-handling-on-submit-action}

Dans le cadre de la sécurité AEM et des conseils de renforcement, configurez les pages d’erreur personnalisées telles que 400.jsp, 404.jsp et 500.jsp. Ces gestionnaires sont appelés lorsque les erreurs 400, 404 ou 500 s’affichent au moment d’envoyer un formulaire. Les gestionnaires sont également appelés lorsque ces codes d’erreur sont déclenchés sur le nœud de publication. Vous pouvez également créer des pages JSP pour d’autres codes d’erreur HTTP.

Lorsque vous préremplissez un modèle de données de formulaire (FDM) ou un formulaire adaptatif basé sur un schéma avec une plainte de données XML ou JSON à un schéma qui est que les données ne contiennent pas de balises `<afData>`, `<afBoundData>` et `</afUnboundData>`, les données des champs non liés du formulaire adaptatif sont perdues. Le schéma peut être un schéma XML, un schéma JSON ou un modèle de données de formulaire (FDM). Les champs non liés sont des champs de formulaire adaptatif sans la propriété `bindref`.

<!-- For more information, see [Customizing Pages shown by the Error Handler](/help/sites-developing/customizing-errorhandler-pages.md). -->

>[!MORELIKETHIS]
>
>* [Création d’une action Envoyer personnalisée pour le Forms adaptatif](/help/forms/custom-submit-action-form.md)
