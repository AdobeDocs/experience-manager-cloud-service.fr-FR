---
title: Comment enregistrer le formulaire adaptatif basé sur les composants principaux en tant que brouillon ?
description: Découvrez comment enregistrer le formulaire adaptatif basé sur des composants principaux en tant que brouillon, créer un portail Forms et utiliser les composants principaux prêts à l’emploi sur une page AEM Sites.
feature: Adaptive Forms, Core Components
exl-id: c0653bef-afeb-40c1-b131-7d87ca5542bc
role: User, Developer, Admin
source-git-commit: 52b87073cad84705b5dc0c6530aff44d1e686609
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 11%

---


# Enregistrer le formulaire adaptatif basé sur les composants principaux en tant que brouillon {#save-af-form}

L’enregistrement d’un formulaire adaptatif en tant que brouillon est une fonctionnalité essentielle qui améliore l’efficacité et la précision de l’utilisateur. Cette fonctionnalité permet aux utilisateurs d’enregistrer la progression et de revenir à l’exécution des tâches ultérieurement sans perdre les informations saisies. Le fait de disposer d’une option `save-as-draft` offre une certaine souplesse dans la gestion du temps, réduit le risque de perte de données et conserve la précision des envois. Vous pouvez enregistrer des formulaires sous forme de brouillons pour les terminer ultérieurement.

## Considérations

* [Activez les composants principaux de Forms adaptatif pour votre environnement.](/help/forms/enable-adaptive-forms-core-components.md)

* Assurez-vous que le [composant principal est défini sur la version 3.0.24 ou ultérieure](https://github.com/adobe/aem-core-forms-components) pour utiliser cette fonctionnalité.
* Assurez-vous que vous disposez d’un [compte de stockage Azure et d’une clé d’accès](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal) pour autoriser l’accès au compte de stockage Azure.

## Enregistrer un formulaire adaptatif en tant que brouillon

[!DNL Experience Manager Forms] Data Integration (data-integration.md) fournit une configuration de stockage [!DNL Azure] pour intégrer des formulaires à des services de stockage [!DNL Azure]. Le modèle de données de formulaire (FDM) peut être utilisé pour créer un Forms adaptatif qui interagit avec le serveur [!DNL Azure] pour activer les processus d’entreprise.

Pour enregistrer le formulaire en tant que brouillon, vérifiez que vous disposez d’un compte de stockage Azure et d’une clé d’accès pour autoriser l’accès au compte de stockage [!DNL Azure]. Pour enregistrer le formulaire en tant que brouillon, procédez comme suit :

1. [Créer une configuration de stockage Azure](#create-azure-storage-configuration)
1. [Configurer le connecteur de stockage unifié pour le portail Formulaires](#configure-usc-forms-portal)
1. [Créer une règle pour enregistrer un formulaire adaptatif en tant que brouillon](#rule-to-save-adaptive-form-as-draft)


### 1. Créer une configuration de stockage Azure {#create-azure-storage-configuration}

Une fois que vous disposez d’un compte de stockage Azure et d’une clé d’accès pour autoriser l’accès au compte de stockage [!DNL Azure], effectuez les étapes suivantes pour créer la configuration Azure Storage :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Stockage Azure]**.

   ![Choix de carte de stockage Azure](/help/forms/assets/save-form-as-draft-azure-card.png)

1. Sélectionnez un dossier de configuration pour créer la configuration et sélectionnez **[!UICONTROL Créer]**.

   ![Sélectionner le dossier de configuration de stockage Azure](/help/forms/assets/save-form-as-draft-select-config-folder.png)

1. Indiquez un titre pour la configuration dans le champ **[!UICONTROL Titre]**.
1. Indiquez le nom du compte de stockage [!DNL Azure] dans les champs **[!UICONTROL Compte de stockage Azure]** et **[!UICONTROL Clé d’accès Azure]** .

   ![Configuration du stockage Azure](/help/forms/assets/save-form-as-draft-azure-storage.png)

1. Cliquez sur **Enregistrer**.

>[!NOTE]
>
> Vous pouvez récupérer le **[!UICONTROL compte de stockage Azure]** et la **[!UICONTROL clé d’accès Azure]** à partir du [portail Microsoft Azure](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).


### 2. Configuration du connecteur de stockage unifié pour Forms Portal {#configure-usc-forms-portal}

Après, vous avez créé avec succès la configuration de stockage Azure, configurez le connecteur de stockage unifié pour le portail Forms, en procédant comme suit :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Connecteur de stockage unifié]**.

   ![Stockage du connecteur unifié](/help/forms/assets/save-form-as-draft-unified-connector.png)

1. Dans la section **[!UICONTROL Portail Formulaires]**, sélectionnez **[!UICONTROL Azure]** dans la liste déroulante **[!UICONTROL Stockage]**.
1. Spécifiez le [chemin de configuration pour la configuration de stockage Azure](#create-azure-storage-configuration) dans le champ **[!UICONTROL Chemin de configuration de stockage]**.

   ![ Paramètre de stockage du connecteur unifié](/help/forms/assets/save-form-as-draft-unified-connector-storage.png)

1. Sélectionnez **[!UICONTROL Save]** , puis **[!UICONTROL Publish]** pour publier la configuration.

### 3. Création de règles pour enregistrer un formulaire adaptatif en tant que brouillon {#rule-to-save-adaptive-form-as-draft}

Pour enregistrer un formulaire en tant que brouillon, créez une règle **Enregistrer le formulaire** sur un composant de formulaire, comme un bouton. Lorsque vous cliquez sur le bouton, la règle se déclenche et le formulaire est enregistré en tant que brouillon. Effectuez les étapes suivantes pour créer la règle **Enregistrer le formulaire** sur un composant de bouton :

1. Dans l’instance d’auteur, ouvrez un formulaire adaptatif en mode d’édition.
1. Dans le volet de gauche, sélectionnez ![Icône Composants](assets/components_icon.png) et faites glisser le composant **[!UICONTROL Bouton]** vers le formulaire.
1. Sélectionnez le composant **[!UICONTROL Bouton]**, puis sélectionnez l’ ![icône de configuration](assets/configure_icon.png).
1. Sélectionnez l’icône **[!UICONTROL Modifier les règles]** pour ouvrir l’éditeur de règles.
1. Sélectionnez **[!UICONTROL Créer]** pour configurer et créer la règle.
1. Dans la section **[!UICONTROL When]**, sélectionnez **is click** et, dans la section **[!UICONTROL Then]**, sélectionnez l’option **Save Form** (Enregistrer le formulaire).
1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

![Créer une règle pour le bouton](/help/forms/assets/save-form-as-drfat-create-rule.png)

Lorsque vous prévisualisez un formulaire adaptatif, remplissez-le et cliquez sur le bouton **Enregistrer le formulaire**, le formulaire est enregistré en tant que brouillon pour une utilisation ultérieure.

## Composant Drafts &amp; Submissions pour répertorier les brouillons sur la page AEM Sites

AEM Forms fournit le composant de portail **Drafts &amp; Submissions** prêt à l’emploi pour afficher les formulaires enregistrés sur les pages AEM Sites. Le composant **Drafts &amp; Submissions** affiche les formulaires enregistrés en tant que brouillons pour une fin ultérieure, ainsi que les formulaires envoyés. Ce composant offre une expérience personnalisée à tout utilisateur connecté en répertoriant les brouillons et les envois liés à la Forms adaptative créée par l’utilisateur.

Vous pouvez utiliser des composants Forms Portal prêts à l’emploi pour répertorier les brouillons de formulaire dans la page AEM Sites. Effectuez les étapes suivantes pour utiliser le composant de portail **Drafts &amp; Submissions** :

1. [Activation du composant Portail Forms Brouillons et envois](#enable-component)
2. [Ajout d’un composant Drafts &amp; Submissions sur la page AEM Sites](#Add-drafts-submissions-component)
3. [Configuration du composant Brouillons et envois](#configure-drafts-submissions-component)

### 1. Activation du composant Portail Forms Brouillons et envois{#enable-component}

Pour activer le composant **[!UICONTROL Drafts &amp; Submissions]** dans la stratégie de modèle, procédez comme suit :

1. Ouvrez la page AEM Sites en mode **Modifier** .
1. Accédez à **[!UICONTROL Informations sur la page]** > **[!UICONTROL Modifier le modèle]**.
   ![Modifier la stratégie de modèle](/help/forms/assets/save-form-as-draft-edit-template.png)

1. Cliquez sur la **[!UICONTROL stratégie]** et cochez la case **[!UICONTROL Drafts &amp; Submissions]** sous le **[nom de projet AEM archetype] - Forms and Communications Portal**.

   ![Sélection de stratégie](/help/forms/assets/save-form-as-draft-enable-policy.png)

1. Cliquez sur **[!UICONTROL Terminé]**.

Une fois qu’un composant Portal est activé, vous pouvez l’utiliser dans l’instance d’auteur de votre page AEM Sites.

### 2. Ajout du composant Drafts &amp; Submissions dans la page AEM Sites{#Add-drafts-submissions-component}

Vous pouvez créer et personnaliser le Portail Formulaires sur les sites web créés à l’aide d’AEM en ajoutant et en configurant les composants du portail. Assurez-vous que le composant [Drafts &amp; Submissions (Brouillons et envois) est activé](#enable-component) avant de l’utiliser dans la page AEM Sites.

Pour ajouter un composant, faites-le glisser du composant du volet **Drafts &amp; Submissions** vers le conteneur de mises en page ou sélectionnez l’icône d’ajout dans le conteneur de mises en page et ajoutez le composant à partir de la boîte de dialogue **[!UICONTROL Insérer un nouveau composant]**.

![Ajouter un composant Drafts and Submission](/help/forms/assets/save-form-as-draft-add-dns.png)

### 3. Configuration du composant Drafts &amp; Submissions {#configure-drafts-submissions-component}

Le composant **Drafts &amp; Submissions** affiche les formulaires enregistrés en tant que brouillons en vue de leur remplissage ultérieur et les formulaires envoyés. Pour configurer **Drafts &amp; Submissions**, procédez comme suit :
1. Sélectionnez le composant **Drafts &amp; Submissions** .
1. Cliquez sur l’icône ![Configurer](assets/configure_icon.png) et la boîte de dialogue s’affiche.
1. Dans la boîte de dialogue **[!UICONTROL Drafts and Submissions]**, spécifiez ce qui suit :
   * **Titre** Pour identifier un composant dans une page Sites et, par défaut, le titre s’affiche au-dessus du composant.
   * **Type** : pour indiquer la liste de formulaires en tant que brouillons ou formulaires envoyés.
   * **Mise en page** : pour afficher la liste des brouillons de formulaires ou des formulaires envoyés au format carte ou liste.

   ![Propriétés du composant Drafts &amp; Submission](/help/forms/assets/save-form-as-draft-dns-properties.png)

1. Cliquez sur **Terminé**.

Lorsque **[!UICONTROL Select Type]** est sélectionné en tant que **Draft Forms**, les formulaires enregistrés en tant que brouillons s’affichent :
![Icône Brouillons](assets/drafts-component.png)

Lorsque **[!UICONTROL Select Type]** est sélectionné en tant que **Submitted Forms**, les formulaires envoyés apparaissent :

![Icône Envois](assets/submission-listing.png)

Vous pouvez ouvrir le formulaire en cliquant sur le formulaire correspondant.

<!--

### Configure Search & Lister Component {#configure-search-lister-component}

The Search & Lister component is used to list adaptive forms on a page and to implement search on the listed forms. 

![Search and Lister icon](assets/search-and-lister-component.png)

To configure, select the component and then select the ![Configure icon](assets/configure_icon.png). The [!UICONTROL Search and Lister] dialog opens.

1. In the [!UICONTROL Display] tab, configure the following:
    * In **[!UICONTROL Title]**, specify the title for the Search & Lister component. An indicative title enables the users perform quick search across the list of forms.
    * From the **[!UICONTROL Layout]** list, select the layout to represent the forms in card or list format.
    * Select **[!UICONTROL Hide Search]** and **[!UICONTROL Hide Sorting]** to hide the search and sort by features.
    * In **[!UICONTROL Tooltip]**, provide the tooltip that appears when you hover over the component. 
1. In the [!UICONTROL Asset Folder] tab, specify the location from where the forms are pulled and listed on the page. You can configure multiple folder locations.
1. In the [!UICONTROL Results] tab, configure the maximum number of forms to display per page. The default is eight forms per page.

### Configure Link Component {#configure-link-component}

The link component enables you to provide links to an adaptive form on the page. To configure, select the component and then select the ![Configure icon](assets/configure_icon.png). The [!UICONTROL Edit Link Component] dialog opens.

1. In the [!UICONTROL Display] tab, provide the link caption and tooltip to ease identification of the forms represented by the link.
1. In the [!UICONTROL Asset Info] tab, specify the repository path where the asset is stored. 
1. In the [!UICONTROL Query Params] tab, specify the additional parameters in the key-value pair format. When the link is clicked, these additional parameters and passed along with the form.

## Configure Asynchronous Form Submission Using Adobe Sign {#configure-asynchronous-form-submission-using-adobe-sign}

You can configure to submit an adaptive form only when all the recipients have completed the signing ceremony. Follow the steps below to configure the setting using Adobe Sign.

1. In the author instance, open an Adaptive Form in the edit mode.
1. From the left pane, select the Properties icon and expand the **[!UICONTROL ELECTRONIC SIGNTATURE]** option.
1. Select **[!UICONTROL Enable Adobe Sign]**. Various configuration options display. 
1. In the [!UICONTROL Submit the form] section, select the **[!UICONTROL after every recipient completes signing ceremony]** option to configure the Submit Form action, where the form is first sent to all the recipients for signing. Once all the recipients have signed the form, only then the form is submitted. 

## Save Adaptive Forms As Drafts {#save-adaptive-forms-as-drafts}

You can save forms as Drafts for completing them later. There are two ways in which a form is saved as a draft:

* Create a "Save Form" rule on a form component, for example, a button. On clicking the button, the rule triggers and the form are saved a draft.
* Enable Auto-Save feature, which saves the form as per the specified event or after a configured interval of time.

### Create Rules to Save an Adaptive Form as Draft {#rule-to-save-adaptive-form-as-draft}

To create a "Save Form" rule on a form component, for example, a button, follow the steps below:

1. In the author instance, open an Adaptive Form in edit mode.
1. From the left pane, select ![Components icon](assets/components_icon.png) and drag the [!UICONTROL Button] component to the form.
1. Select the [!UICONTROL Button] component and then select the ![Configure icon](assets/configure_icon.png). 
1. Select the [!UICONTROL Edit Rules] icon to open the Rule Editor. 
1. Select **[!UICONTROL Create]** to configure and create the rule.
1. In the [!UICONTROL When] section, select "is clicked" and in the [!UICONTROL Then] section, select the "Save Form" options.
1. Select **[!UICONTROL Done]** to save the rule.

### Enable Auto-save {#enable-auto-save}

You can configure the auto-save feature for an adaptive form as follows:

1. In the author instance, open an Adaptive Form in edit mode.
1. From the left pane, select the ![Properties icon](assets/configure_icon.png) and expand the [!UICONTROL AUTO-SAVE] option.
1. Select the **[!UICONTROL Enable]** check box to enable auto-save of the form. You can configure the following:
* By default, the [!UICONTROL Adaptive Form Event] is set to "true", which implies that the form is auto-saved after every event.
* In [!UICONTROL Trigger], configure to trigger auto-save based on the occurrence of an event or after a specific interval of time.
-->

## Voir également {#see-also}

{{see-also}}



<!--

>[!MORELIKETHIS]
>
>* [Configure data sources for AEM Forms](/help/forms/configure-data-sources.md)
>* [Configure Azure storage for AEM Forms](/help/forms/configure-azure-storage.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)

-->
