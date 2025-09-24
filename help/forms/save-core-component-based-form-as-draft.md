---
title: Comment enregistrer le formulaire adaptatif basé sur les composants principaux en tant que brouillon et utiliser le composant Drafts and Submissions pour répertorier les brouillons et les envois ?
description: Découvrez comment enregistrer le formulaire adaptatif basé sur les composants principaux en tant que brouillon. Comprendre également comment utiliser le composant Brouillons et envois pour répertorier les brouillons et les envois pour les utilisateurs connectés ?
feature: Adaptive Forms, Core Components
exl-id: c0653bef-afeb-40c1-b131-7d87ca5542bc
role: User, Developer
source-git-commit: 8f1fa3a95f232f34ad6ae89c391e9e2272a2c072
workflow-type: tm+mt
source-wordcount: '1385'
ht-degree: 6%

---


# Enregistrer des formulaires en tant que brouillons et les répertorier sur la page Sites

<!--This article provides information about the Auto-save feature, which is currently available as a pre-release feature. The pre-release feature is accessible only through our [pre-release channel](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/prerelease#new-features).-->

Prenons le cas d’un utilisateur qui commence à remplir un formulaire, mais qui doit se suspendre et revenir ultérieurement. AEM propose une option `save-as-draft`, qui permet à l’utilisateur ou à l’utilisatrice d’enregistrer le formulaire en tant que brouillon en vue d’un remplissage ultérieur. Pour faciliter la tâche, AEM fournit le composant du portail Forms **Brouillons et envois** prêt à l’emploi, qui affiche les brouillons et les envois sur les pages AEM Sites. Le composant répertorie les formulaires qui ont été enregistrés en tant que brouillons en vue d’une finalisation ultérieure, ainsi que ceux qui ont été envoyés. Seuls les utilisateurs connectés peuvent modifier leurs brouillons ou afficher les formulaires qu’ils ont envoyés. Cependant, si un utilisateur anonyme parcourt la liste des formulaires à l’aide du composant **Search &amp; Lister** et enregistre un formulaire en tant que brouillon, ce dernier n’est pas répertorié par le composant **Drafts &amp; Submissions**. Pour afficher les brouillons et les envois, les utilisateurs doivent être connectés au moment de l’envoi du formulaire.

![Icône Brouillons](assets/drafts-component.png)

## Conditions préalables

* Installez la dernière version de pour activer les composants principaux de Forms adaptatif pour votre environnement AEM Cloud Service.

  Après le déploiement des derniers composants principaux dans votre environnement, les composants du portail Forms deviennent accessibles dans votre environnement de création.

* [Configurer le stockage Azure et le connecteur de stockage unifié pour le composant du portail Forms Drafts &amp; Submissions](#configure-azure-storage-and-unified-storage-connector-for-drafts--submissions-forms-portal-component)

### Configuration du connecteur de stockage unifié et du stockage Azure pour le composant du portail Forms Drafts &amp; Submissions

Le composant **Brouillons et envois** a besoin d’une configuration de stockage pour enregistrer et répertorier les brouillons sur la page AEM Sites. Le connecteur de stockage unifié offre une structure pour lier AEM au stockage externe. Pour enregistrer le formulaire en tant que brouillon, vérifiez que vous disposez d’un compte de stockage Azure et d’une clé d’accès pour autoriser l’accès au compte de stockage [!DNL Azure]. Une fois que vous disposez du compte de stockage Azure et de la clé d’accès, effectuez les étapes suivantes pour créer une configuration de stockage Azure :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Stockage Azure]**.

   ![Sélection de la carte de stockage Azure](/help/forms/assets/save-form-as-draft-azure-card.png)

1. Sélectionnez un dossier de configuration pour créer la configuration, puis sélectionnez **[!UICONTROL Créer]**.

   ![Sélectionnez le dossier de configuration du stockage Azure](/help/forms/assets/save-form-as-draft-select-config-folder.png)

1. Indiquez un titre pour la configuration dans le champ **[!UICONTROL Titre]**.
1. Indiquez le nom du compte de stockage [!DNL Azure] dans les champs **[!UICONTROL Compte de stockage Azure]** et **[!UICONTROL Clé d’accès Azure]**.

   ![Configuration du stockage Azure](/help/forms/assets/save-form-as-draft-azure-storage.png)

   Saisissez `Connection String` dans la zone de texte `Azure Storage Account` et `Azure Key` dans la zone de texte `Azure Access key`.

1. Cliquez sur **Enregistrer**.

   >[!NOTE]
   >
   > Vous pouvez récupérer le **[!UICONTROL Compte de stockage Azure]** et la **[!UICONTROL Clé d’accès Azure]** à partir du portail Azure [Microsoft](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).

   Une fois la configuration de stockage Azure créée, configurez le connecteur de stockage unifié pour le portail Forms en procédant comme suit :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Connecteur de stockage unifié]**.

   ![Stockage de connecteur unifié](/help/forms/assets/save-form-as-draft-unified-connector.png)

1. Dans la section **[!UICONTROL Portail Formulaires]**, sélectionnez **[!UICONTROL Azure]** dans la liste déroulante **[!UICONTROL Stockage]**.
1. Spécifiez le chemin de configuration de la configuration de stockage Azure dans le champ **[!UICONTROL Chemin de configuration de stockage]**.

   ![Paramètre de stockage du connecteur unifié](/help/forms/assets/save-form-as-draft-unified-connector-storage.png)

1. Sélectionnez **[!UICONTROL Enregistrer]**.

>[!NOTE]
>
> Si vous devez configurer une option de stockage autre qu’Azure, écrivez à aem-forms-ea@adobe.com à partir de votre adresse e-mail officielle en indiquant vos exigences détaillées.

Une fois que vous avez correctement configuré le stockage Azure et le connecteur de stockage unifié pour stocker les brouillons et les formulaires envoyés, ajoutez le composant **Brouillons et envois** sur la page AEM Sites.

## Comment ajouter le composant Brouillons et envois à une page AEM Sites ?

Vous pouvez utiliser les composants prêts à l’emploi du portail Forms pour répertorier les brouillons et les envois sur la page Sites. Pour ajouter le composant de portail **Brouillons et envois**, procédez comme suit :

1. Ouvrez la page AEM Sites en mode **Modifier**.
1. Accédez à **[!UICONTROL Informations sur la page]** > **[!UICONTROL Modifier le modèle]**.
   ![Modifier la politique du modèle](/help/forms/assets/save-form-as-draft-edit-template.png)

1. Cliquez sur la **[!UICONTROL Politique]** et cochez la case **[!UICONTROL Brouillons et envois]** sous **[Nom du projet de l’archétype AEM] - Portail Forms et communications**.

   ![Sélection de politique](/help/forms/assets/save-form-as-draft-enable-policy.png)

1. Cliquez sur **[!UICONTROL Terminé]**.
1. Rouvrez maintenant la page AEM Sites en mode création.
1. Recherchez la section dans l’éditeur de page qui vous permet d’ajouter le composant Forms Portal.
1. Cliquez sur l’icône **Ajouter**. L’icône est un signe plus (+) qui signifie que vous pouvez ajouter de nouveaux composants.

   Cliquez sur l’icône **Ajouter** pour afficher une boîte de dialogue **Insérer un nouveau composant** qui affiche différents composants à insérer.

   >[!NOTE]
   >
   > Vous pouvez également effectuer un glisser-déposer du composant.

1. Parcourez les composants disponibles dans la boîte de dialogue et sélectionnez le composant de votre choix dans la liste. Par exemple, sélectionnez le composant **Brouillons et envois** dans la liste pour ajouter le composant **Brouillons et envois** Portail Forms.

   ![Ajouter un composant Brouillon et Envoi](/help/forms/assets/save-form-as-draft-add-dns.png)

Maintenant, configurez les propriétés du composant **Brouillons et envois** en fonction des exigences.

## Configurer les propriétés du composant Brouillons et envois

Vous pouvez configurer les propriétés du **Brouillons et envois** :
1. Sélectionnez le composant **Brouillons et envois**.
1. Cliquez sur l’icône ![Configurer](assets/configure_icon.png) et la boîte de dialogue s’affiche.
1. Dans la boîte de dialogue **[!UICONTROL Brouillons et envois]**, spécifiez ce qui suit :
   * **Titre** pour identifier un composant dans une page Sites et, par défaut, le titre s’affiche au-dessus du composant.
   * **Sélectionner un type** : pour indiquer la liste des formulaires en tant que brouillons ou formulaires envoyés. Si vous choisissez **Brouillon de Forms**, les formulaires enregistrés en tant que brouillons s’affichent. Vous pouvez également sélectionner **Forms envoyé** pour afficher les formulaires envoyés par les utilisateurs connectés.
   * **Disposition** : affichage de listes de brouillons de formulaires ou de formulaires envoyés au format vignette ou liste.

   ![Propriétés des composants Brouillon et Envoi](/help/forms/assets/save-form-as-draft-dns-properties.png)

## Configuration des formulaires à enregistrer en tant que brouillons

Vous pouvez configurer les Forms adaptatives des deux manières suivantes pour les enregistrer en tant que brouillons en vue d’une utilisation ultérieure :
* [Action de l’utilisateur ou de l’utilisatrice](#user-action)
* [Enregistrement automatique](#auto-save)

### Action de l’utilisateur ou de l’utilisatrice

>[!NOTE]
>
> Assurez-vous que la version [Core Components) est définie sur 3.0.24 ou une version ultérieure](https://github.com/adobe/aem-core-forms-components) pour enregistrer les formulaires en tant que brouillons à l’aide de la règle **Enregistrer le formulaire**.

Pour enregistrer un formulaire en tant que brouillon, créez une règle **Enregistrer le formulaire** sur un composant de formulaire, tel qu’un bouton. Lorsque l’utilisateur clique sur le bouton, la règle se déclenche et le formulaire est enregistré en tant que brouillon. Pour créer une règle **Enregistrer le formulaire** sur un composant de bouton, procédez comme suit :

1. Ouvrez un formulaire adaptatif en mode d’édition.
1. Sélectionnez l’icône **[!UICONTROL Modifier les règles]** pour ouvrir l’éditeur de règles pour le composant **Bouton**.
1. Sélectionnez **[!UICONTROL Créer]** pour configurer et créer la règle pour le bouton.
1. Dans la section **[!UICONTROL Quand]**, sélectionnez **est cliqué** et dans la section **[!UICONTROL Alors]**, sélectionnez l’option **Enregistrer le formulaire**.
1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

   ![Bouton Créer une règle pour](/help/forms/assets/save-form-as-drfat-create-rule.png)

Lorsque vous prévisualisez un formulaire adaptatif, le remplissez et cliquez sur le bouton **Enregistrer le formulaire**, le formulaire est enregistré en tant que brouillon.

### Brouillons

>[!NOTE]
>
> Assurez-vous que la version [Composants principaux) est définie sur 3.0.52 ou une version ultérieure](https://github.com/adobe/aem-core-forms-components) pour enregistrer les formulaires en tant que brouillons à l’aide de la fonction d’enregistrement automatique.

Vous pouvez également configurer un formulaire adaptatif pour qu’il soit enregistré automatiquement en fonction d’un événement temporel, en veillant à ce que le formulaire soit enregistré après la durée spécifiée. Lorsque vous [activez les composants du portail Forms pour votre environnement](/help/forms/list-forms-on-sites-page.md#enable-forms-portal-components-for-your-existing-environment), l’onglet **Enregistrement automatique** s’affiche dans les propriétés du conteneur Forms. Vous pouvez configurer la fonction d’enregistrement automatique pour un formulaire adaptatif :

1. Dans l’instance d’auteur, ouvrez un formulaire adaptatif en mode d’édition.
1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône Propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg) et ouvrez l’onglet **[!UICONTROL Brouillons]**.

   ![ Enregistrement automatique ](/help/forms/assets/auto-save.png)

1. Cochez la case **[!UICONTROL Enregistrer automatiquement les brouillons]** pour activer l’enregistrement automatique du formulaire en tant que brouillons.
1. Configurez **[!UICONTROL Enregistrer la préférence]** comme **Enregistrer les brouillons à intervalles réguliers** pour enregistrer automatiquement le <!--based on the occurrence of an event or--> de formulaire après un intervalle de temps spécifique.
1. Indiquez l’intervalle de temps dans **[!UICONTROL Fréquence d’enregistrement (secondes)]** pour définir la durée qui déclenche l’enregistrement automatique du formulaire à l’intervalle défini.
1. Cliquez sur **[!UICONTROL Terminé]**.

## Affichez les brouillons/formulaires envoyés sur la page Sites à l’aide du composant Brouillons et envois

Pour afficher les brouillons enregistrés ou les formulaires envoyés, utilisez le composant du portail Forms **Brouillons et envois**.
Lorsque l’option **[!UICONTROL Sélectionner le type]** est sélectionnée en tant que **Brouillon Forms** dans la boîte de dialogue [configurer du composant Brouillons et envois](#configure-properties-of-the-drafts--submissions-component), les formulaires enregistrés en tant que brouillons apparaissent sur la page Sites. Vous pouvez ouvrir les brouillons en cliquant sur les points de suspension (...) pour remplir le formulaire.

![Icône Brouillons](assets/drafts-component.png)

Lorsque l’option **[!UICONTROL Sélectionner le type]** est sélectionnée en tant que **Forms envoyé** dans la boîte de dialogue [configurer du composant Drafts &amp; Submissions](#configure-properties-of-the-drafts--submissions-component), les formulaires envoyés s’affichent. Vous pouvez afficher les formulaires envoyés, mais ne pouvez pas les modifier.

![Icône Envois](assets/submission-listing.png)

Vous pouvez également ignorer les formulaires en cliquant sur les points de suspension (...) qui s’affichent dans le coin inférieur droit du formulaire.

>[!NOTE]
>
> La liste Envois du portail Forms affiche uniquement les envois de formulaires de base.

## Étapes suivantes

Dans l’article suivant, découvrez [ comment ajouter des références à des formulaires sur la page Sites à l’aide du composant Lien du portail Forms ](/help/forms/add-form-link-to-aem-sites-page.md).

## Articles connexes

{{forms-portal-see-also}}

## Voir également {#see-also}

{{see-also}}