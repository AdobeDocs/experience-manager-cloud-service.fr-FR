---
title: Comment enregistrer le formulaire adaptatif basé sur les composants principaux en tant que brouillon et utiliser le composant Drafts and Submissions pour répertorier les brouillons et les envois ?
description: Découvrez comment enregistrer le formulaire adaptatif basé sur les composants principaux en tant que brouillon. Comprenez également comment utiliser le composant Drafts and Submissions pour répertorier les brouillons et les envois pour les utilisateurs connectés ?
feature: Adaptive Forms, Core Components
exl-id: c0653bef-afeb-40c1-b131-7d87ca5542bc
role: User, Developer
source-git-commit: 2933b3be569724800a77b4ea93e91441046746f6
workflow-type: tm+mt
source-wordcount: '1384'
ht-degree: 7%

---


# Enregistrer des formulaires en tant que brouillons et les répertorier sur la page Sites

<span class="preview"> Cet article contient du contenu sur la fonction **Enregistrement automatique**, une fonctionnalité de version préliminaire. La fonctionnalité de version préliminaire n’est accessible que par le biais de notre [canal de version préliminaire](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/prerelease#new-features).</span>

Prenons l’exemple d’un utilisateur qui commence à remplir un formulaire, mais qui doit se mettre en pause et revenir ultérieurement. AEM propose une option `save-as-draft`, permettant à l’utilisateur d’enregistrer le formulaire en tant que brouillon pour une exécution ultérieure. Pour faciliter cela, AEM fournit le composant Portail Forms **** prêt à l’emploi  Drafts &amp; Submissions{qui affiche les brouillons et les envois sur les pages AEM Sites. Le composant répertorie les formulaires qui ont été enregistrés en tant que brouillons pour une fin ultérieure, ainsi que ceux qui ont été envoyés. Seuls les utilisateurs connectés peuvent modifier leurs brouillons ou afficher leurs formulaires envoyés. Cependant, si un utilisateur anonyme parcourt la liste des formulaires à l’aide du composant **Search &amp; Lister** et enregistre un formulaire en tant que brouillon, ce brouillon n’est pas répertorié par le composant **Drafts &amp; Submissions**. Pour afficher les brouillons et les envois, les utilisateurs doivent être connectés au moment de l’envoi du formulaire.

![Icône Brouillons](assets/drafts-component.png)

## Prérequis

* [Activez les composants principaux de Forms adaptatif pour votre environnement.](/help/forms/enable-adaptive-forms-core-components.md)

  Après avoir déployé les derniers composants principaux dans votre environnement, les composants du portail Forms deviennent accessibles dans votre environnement de création.

* [ Configuration du connecteur Azure Storage et Unified Storage pour le composant Portail Forms Drafts &amp; Submissions](#configure-azure-storage-and-unified-storage-connector-for-drafts--submissions-forms-portal-component)

### Configuration du composant Portail Forms de stockage Azure et de stockage unifié pour les versions préliminaires et les envois

Le composant **Drafts &amp; Submissions** a besoin d’une configuration de stockage pour enregistrer et répertorier les brouillons sur la page AEM Sites. Le connecteur de stockage unifié offre une structure pour lier AEM avec un stockage externe. Pour enregistrer le formulaire en tant que brouillon, vérifiez que vous disposez d’un compte de stockage Azure et d’une clé d’accès pour autoriser l’accès au compte de stockage [!DNL Azure]. Une fois que vous disposez d’un compte de stockage Azure et de la clé d’accès, effectuez les étapes suivantes pour créer une configuration de stockage Azure :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Stockage Azure]**.

   ![Choix de carte de stockage Azure](/help/forms/assets/save-form-as-draft-azure-card.png)

1. Sélectionnez un dossier de configuration pour créer la configuration et sélectionnez **[!UICONTROL Créer]**.

   ![Sélectionner le dossier de configuration de stockage Azure](/help/forms/assets/save-form-as-draft-select-config-folder.png)

1. Indiquez un titre pour la configuration dans le champ **[!UICONTROL Titre]**.
1. Indiquez le nom du compte de stockage [!DNL Azure] dans les champs **[!UICONTROL Compte de stockage Azure]** et **[!UICONTROL Clé d’accès Azure]** .

   ![Configuration du stockage Azure](/help/forms/assets/save-form-as-draft-azure-storage.png)

   Saisissez `Connection String` dans la zone de texte `Azure Storage Account` et `Azure Key` dans la zone de texte `Azure Access key`.

1. Cliquez sur **Enregistrer**.

   >[!NOTE]
   >
   > Vous pouvez récupérer le **[!UICONTROL compte de stockage Azure]** et la **[!UICONTROL clé d’accès Azure]** à partir du [portail Microsoft Azure](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).

   Après, vous avez créé avec succès la configuration de stockage Azure, configurez le connecteur de stockage unifié pour le portail Forms, en procédant comme suit :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Connecteur de stockage unifié]**.

   ![Stockage du connecteur unifié](/help/forms/assets/save-form-as-draft-unified-connector.png)

1. Dans la section **[!UICONTROL Portail Formulaires]**, sélectionnez **[!UICONTROL Azure]** dans la liste déroulante **[!UICONTROL Stockage]**.
1. Spécifiez le chemin de configuration de la configuration du stockage Azure dans le champ **[!UICONTROL Chemin de configuration du stockage]**.

   ![ Paramètre de stockage du connecteur unifié](/help/forms/assets/save-form-as-draft-unified-connector-storage.png)

1. Sélectionnez **[!UICONTROL Enregistrer]**.

>[!NOTE]
>
> Si vous devez configurer une option de stockage autre qu’Azure, écrivez à aem-forms-ea@adobe.com à partir de votre adresse électronique officielle avec vos besoins détaillés.

Une fois que vous avez correctement configuré Azure Storage et Unified Storage Connector pour stocker les brouillons et les formulaires envoyés, ajoutez le composant **Drafts &amp; Submissions** sur la page AEM Sites.

## Comment ajouter le composant Drafts &amp; Submissions à une page AEM Sites ?

Vous pouvez utiliser des composants Forms Portal prêts à l’emploi pour répertorier les brouillons et les envois sur la page Sites. Effectuez les étapes suivantes pour ajouter le composant de portail **Drafts &amp; Submissions** :

1. Ouvrez la page AEM Sites en mode **Modifier** .
1. Accédez à **[!UICONTROL Informations sur la page]** > **[!UICONTROL Modifier le modèle]**.
   ![Modifier la stratégie de modèle](/help/forms/assets/save-form-as-draft-edit-template.png)

1. Cliquez sur la **[!UICONTROL stratégie]** et cochez la case **[!UICONTROL Drafts &amp; Submissions]** sous le **[nom de projet AEM archetype] - Forms and Communications Portal**.

   ![Sélection de stratégie](/help/forms/assets/save-form-as-draft-enable-policy.png)

1. Cliquez sur **[!UICONTROL Terminé]**.
1. Ouvrez à nouveau la page AEM Sites en mode création.
1. Recherchez la section dans l’éditeur de page qui vous permet d’ajouter le composant Portail Forms .
1. Cliquez sur l&#39;icône **Ajouter** . L’icône est un signe plus (+) qui indique l’option d’ajout de nouveaux composants.

   Cliquez sur l’icône **Ajouter** pour afficher une boîte de dialogue **Insérer un nouveau composant** qui affiche divers composants à insérer.

   >[!NOTE]
   >
   > Vous pouvez également faire glisser et déposer le composant.

1. Parcourez les composants disponibles dans la boîte de dialogue et sélectionnez un composant dans la liste. Par exemple, sélectionnez le composant **Drafts &amp; Submissions** dans la liste pour ajouter le composant **Drafts &amp; Submissions** du portail Forms.

   ![Ajouter un composant Drafts and Submission](/help/forms/assets/save-form-as-draft-add-dns.png)

Maintenant, configurez les propriétés du composant **Drafts and Submissions** en fonction des exigences.

## Configuration des propriétés du composant Drafts &amp; Submissions

Vous pouvez configurer les propriétés de la fonction **Drafts &amp; Submissions** :
1. Sélectionnez le composant **Drafts &amp; Submissions** .
1. Cliquez sur l’icône ![Configurer](assets/configure_icon.png) et la boîte de dialogue s’affiche.
1. Dans la boîte de dialogue **[!UICONTROL Drafts and Submissions]**, spécifiez ce qui suit :
   * **Titre** Pour identifier un composant dans une page Sites et, par défaut, le titre s’affiche au-dessus du composant.
   * **Sélectionner un type** : pour indiquer la liste de formulaires en tant que brouillons ou formulaires envoyés. Si vous choisissez **Brouillon de Forms**, les formulaires enregistrés en tant que brouillons s’affichent. Vous pouvez également sélectionner **Forms envoyée** pour afficher les formulaires envoyés par les utilisateurs connectés.
   * **Mise en page** : pour afficher la liste des brouillons de formulaires ou des formulaires envoyés au format carte ou liste.

   ![Propriétés du composant Drafts &amp; Submission](/help/forms/assets/save-form-as-draft-dns-properties.png)

## Configuration de formulaires à enregistrer en tant que brouillons

Vous pouvez configurer les Forms adaptatives de deux manières suivantes pour les enregistrer en tant que brouillons en vue d’une utilisation ultérieure :
* [Action de l’utilisateur ou de l’utilisatrice](#user-action)
* [Enregistrement automatique](#auto-save)

### Action de l’utilisateur ou de l’utilisatrice

>[!NOTE]
>
> Assurez-vous que la [version des composants principaux est définie sur 3.0.24 ou ultérieure](https://github.com/adobe/aem-core-forms-components) pour enregistrer les formulaires en tant que brouillons à l’aide de la règle **Enregistrer le formulaire**.

Pour enregistrer un formulaire en tant que brouillon, créez une règle **Enregistrer le formulaire** sur un composant de formulaire, comme un bouton. Lorsque vous cliquez sur le bouton, la règle se déclenche et le formulaire est enregistré en tant que brouillon. Effectuez les étapes suivantes pour créer une règle **Enregistrer le formulaire** sur un composant de bouton :

1. Ouvrez un formulaire adaptatif en mode d’édition.
1. Sélectionnez l’icône **[!UICONTROL Modifier les règles]** pour ouvrir l’éditeur de règles pour le composant **Bouton**.
1. Sélectionnez **[!UICONTROL Créer]** pour configurer et créer la règle pour le bouton.
1. Dans la section **[!UICONTROL When]**, sélectionnez **is click** et, dans la section **[!UICONTROL Then]**, sélectionnez l’option **Save Form** (Enregistrer le formulaire).
1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

   ![Créer une règle pour le bouton](/help/forms/assets/save-form-as-drfat-create-rule.png)

Lorsque vous prévisualisez un formulaire adaptatif, remplissez-le et cliquez sur le bouton **Enregistrer le formulaire**, le formulaire est enregistré en tant que brouillon.

### Enregistrement automatique

>[!NOTE]
>
> Assurez-vous que la [version des composants principaux est définie sur 3.0.52 ou version ultérieure](https://github.com/adobe/aem-core-forms-components) pour enregistrer les formulaires en tant que brouillons à l’aide de la fonction d’enregistrement automatique.

Vous pouvez également configurer un formulaire adaptatif pour l’enregistrer automatiquement en fonction d’un événement temporel, en vous assurant qu’il est enregistré après la durée spécifiée. Lorsque vous [activez les composants Forms Portal pour votre environnement](/help/forms/list-forms-on-sites-page.md#enable-forms-portal-components-for-your-existing-environment), l’onglet **Enregistrement automatique** s’affiche dans les propriétés du conteneur Forms. Vous pouvez configurer la fonction d’enregistrement automatique d’un formulaire adaptatif :

1. Dans l’instance d’auteur, ouvrez un formulaire adaptatif en mode d’édition.
1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône ![Propriétés du guide](/help/forms/assets/configure-icon.svg) de propriétés du conteneur de guide et ouvrez l’onglet **[!UICONTROL Enregistrement automatique]** .

   ![Enregistrement automatique](/help/forms/assets/auto-save.png)

1. Cochez la case **[!UICONTROL Activer]** pour activer l’enregistrement automatique du formulaire.
1. Configurez **[!UICONTROL Trigger]** comme **basé sur le temps** pour enregistrer automatiquement le formulaire <!--based on the occurrence of an event or--> après un intervalle de temps spécifique.
1. Spécifiez l’intervalle de temps dans **[!UICONTROL Enregistrement automatique sur cet intervalle (en secondes)]** pour définir la durée qui déclenche l’enregistrement automatique du formulaire à l’intervalle défini.
1. Cliquez sur **[!UICONTROL Terminé]**.

## Afficher les brouillons/formulaires envoyés sur la page Sites à l’aide du composant Drafts &amp; Submissions

Pour afficher les brouillons enregistrés ou les formulaires envoyés, utilisez le composant Portail Forms **Drafts &amp; Submissions**.
Lorsque **[!UICONTROL Select Type]** est sélectionné en tant que **Brouillon de Forms** dans la [boîte de dialogue de configuration du composant Drafts &amp; Submissions](#configure-properties-of-the-drafts--submissions-component), les formulaires enregistrés en tant que brouillons apparaissent sur la page Sites. Vous pouvez ouvrir les brouillons en cliquant sur les points de suspension (..) pour remplir le formulaire.

![Icône Brouillons](assets/drafts-component.png)

Lorsque **[!UICONTROL Select Type]** est sélectionné en tant que **Submitted Forms** dans la [boîte de dialogue de configuration du composant Drafts &amp; Submissions](#configure-properties-of-the-drafts--submissions-component), les formulaires envoyés s’affichent. Vous pouvez afficher les formulaires envoyés, mais ne pouvez pas les modifier.

![Icône Envois](assets/submission-listing.png)

Vous pouvez également ignorer les formulaires en cliquant sur les points de suspension (..) qui apparaissent dans le coin inférieur droit du formulaire.

## Étapes suivantes

Dans l’article suivant, apprenez [à ajouter des références à des formulaires sur la page Sites à l’aide du composant Link Forms Portal](/help/forms/add-form-link-to-aem-sites-page.md).

## Articles connexes

{{forms-portal-see-also}}

## Voir également {#see-also}

{{see-also}}