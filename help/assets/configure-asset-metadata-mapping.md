---
title: Configuration du mappage des métadonnées de ressources entre Workfront et Experience Manager Assets
description: Mappez les champs de métadonnées des ressources entre Adobe Workfront et les applications as a Cloud Service Experience Manager. En raison du mappage des champs de métadonnées, lorsque vous envoyez une ressource de Workfront à Experience Manager Assets, vous pouvez afficher les métadonnées de ressource mappées dans Experience Manager Assets.
exl-id: 71400769-b2bc-4f5d-8b6b-a73598e837b4
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 10%

---

# Configuration du mappage des métadonnées de ressource entre Adobe Workfront et Experience Manager Assets {#asset-metadata-mapping-workfront-aem-assets}

Vous pouvez mapper les champs de métadonnées de la ressource entre Adobe Workfront et les applications as a Cloud Service Experience Manager. En raison du mappage des champs de métadonnées, lorsque vous envoyez une ressource de Workfront à Experience Manager Assets, vous pouvez afficher les métadonnées de ressource mappées dans Experience Manager Assets.

Par exemple, si vous devez conserver les champs de métadonnées d’une image telle que le nom, la description et le projet auxquels elle appartient dans Workfront lorsque vous envoyez l’image à Experience Manager Assets, configurez ces champs et mappez-les aux propriétés Experience Manager Assets.

**Cas d’utilisation**

Une image `add-users-workfront.png` existe dans la variable `Metadata Syncs` dans l’application Adobe Workfront. Vous devez envoyer cette image à Experience Manager Assets as a Cloud Service avec les métadonnées suivantes :

* Nom du projet

* Document Name

* Description du document

## Conditions préalables {#prerequisites}

* Un accès administrateur aux applications Workfront et Experience Manager Assets as a Cloud Service.

* Une intégration entre [Applications as a Cloud Service Workfront et Experience Manager Assets](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FDocuments%2FAdobe_Workfront_for_Experience_Manager_Assets_Essentials%2Fsetup-asset-essentials.htm&amp;_LANG=enus).

## Configuration du mappage des métadonnées dans Workfront {#set-up-metadata-mapping}

Pour définir le mappage des métadonnées pour les champs Nom du projet, Nom du document et Description du document dans Workfront :

1. Cliquez sur l’icône du menu principal ![Menu Afficher](assets/show-menu.svg) disponible dans le coin supérieur droit de l’application Adobe Workfront, puis cliquez sur **[!UICONTROL Configuration]**.

1. Sélectionner **[!UICONTROL Documents]** dans le panneau de gauche, puis sélectionnez **[!UICONTROL Experience Manager Assets]**.

1. Sélectionnez l’intégration Experience Manager Assets et cliquez sur **[!UICONTROL Modifier]**.

1. Cliquez sur **[!UICONTROL Métadonnées]**. Dans le **[!UICONTROL Ressources]** , mappez les [!UICONTROL Projet] > [!UICONTROL Nom] du champ Workfront `wm:projectName` Champ Experience Manager Assets. Si vous ne trouvez pas la correspondance exacte, Adobe recommande de rechercher la meilleure correspondance pour mapper le champ Workfront et Experience Manager Assets. Vous pouvez éviter de mapper des champs de différents types de données. Par exemple, mappage d’un champ Workfront de date à un champ de description Ressources.
1. Faites correspondre la variable [!UICONTROL Document] > [!UICONTROL Nom] du champ Workfront `wm:documentName` Champ Experience Manager Assets.

   ![Mappage dans Workfront](assets/workfront-metadata-mapping.png)

1. Faites correspondre la variable [!UICONTROL Document] > [!UICONTROL Description] du champ Workfront `dc:description` Champ Experience Manager Assets.

   >[!VIDEO](https://video.tv.adobe.com/v/344255)

## Envoi de l’image de Workfront vers Experience Manager Assets {#send-image-workfront-assets}

Pour envoyer l’image de Workfront à Experience Manager Assets :

1. Cliquez sur l’icône du menu principal ![Menu Afficher](assets/show-menu.svg) disponible dans le coin supérieur droit de l’application Adobe Workfront, puis cliquez sur **[!UICONTROL Projets]**.

1. Cliquez sur **[!UICONTROL Nouveau projet]** pour créer un projet.

1. Cliquez sur **[!UICONTROL Documents]** dans le volet de gauche, faites glisser l’image à envoyer à Experience Manager Assets, puis sélectionnez-la.

1. Cliquez sur **[!UICONTROL Envoyer à]**, puis choisissez le nom de l’intégration de Experience Manager Assets Essentials.

   ![Envoyer à AEM](assets/send-to-aem.png)

1. Sélectionnez le dossier de destination de la ressource, puis cliquez sur **[!UICONTROL Sélectionner un dossier]**.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Configuration du mappage des métadonnées de ressource dans Experience Manager as a Cloud Service {#metadata-mapping-aem}

Après [configuration du mappage des métadonnées des ressources dans Adobe Workfront](#set-up-metadata-mapping), vous devez utiliser le même mappage dans l’application Experience Manager Assets as a Cloud Service pour afficher les résultats de métadonnées appropriés pour l’image.

Le mappage des métadonnées est effectué à l’aide des schémas de métadonnées dans Experience Manager Assets. Vous pouvez modifier un formulaire de schéma de métadonnées existant ou nouvellement ajouté. Le formulaire de schéma de métadonnées comprend des onglets et des éléments de formulaire dans des onglets. Vous pouvez associer ou configurer ces éléments de formulaire dans un champ au sein d’un nœud de métadonnées dans le référentiel CRX. Vous pouvez ajouter des onglets ou des éléments de formulaire au formulaire de schéma de métadonnées. Pour plus d’informations, voir [Schémas de métadonnées](metadata-schemas.md).

Pour configurer le mappage des métadonnées à l’aide d’un nouveau formulaire de métadonnées dans Experience Manager Assets as a Cloud Service :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.

1. Cliquez sur **[!UICONTROL Créer]** dans la barre d’outils. Dans la boîte de dialogue, saisissez le titre du formulaire de schéma, puis cliquez sur **[!UICONTROL Créer]** pour terminer la création du formulaire.

1. Sélectionnez le formulaire de schéma et cliquez sur **[!UICONTROL Modifier]**.

1. (Facultatif) Dans l’éditeur de formulaire de schéma de métadonnées, cliquez sur `+` pour créer un onglet pour les champs Workfront.

1. Cliquez sur le bouton **[!UICONTROL Créer un formulaire]** et faites glisser l’objet **[!UICONTROL Une seule ligne de texte]** du formulaire. Cliquez sur le composant dans le formulaire. Dans le **[!UICONTROL Créer un formulaire]** tab :

   1. Spécifier `Project Name` dans le **[!UICONTROL Libellé du champ]** champ .

   1. Spécifier `./jcr:content/metadata/wm:projectName` dans le **[!UICONTROL Associer à la propriété]** champ . Pour vous guider, utilisez le modèle suivant pour définir les mappages de champs dans Experience Manager Assets :
      `./jcr:content/metadata/<mapping defined for the field in workfront>`.

      Lors de la configuration des mappages dans Workfront, vous avez mappé `wm:projectName` Sélectionnez le champ Experience Manager Assets dans Projet > Nommer Workfront .

      `wm` fait référence au nom de l’espace de noms et `projectName` fait référence au titre de la propriété. Utilisez la variable `namespace:propertyTitle` format pour définir les mappages de champs de métadonnées.

      ![Envoyer à AEM](assets/metadata-schema-mapping.png)

1. Cliquez sur le bouton **[!UICONTROL Créer un formulaire]** et faites glisser l’objet **[!UICONTROL Une seule ligne de texte]** du formulaire. Cliquez sur le composant dans le formulaire. Dans le **[!UICONTROL Créer un formulaire]** tab :

   1. Spécifier `Document Name` dans le **[!UICONTROL Libellé du champ]** champ .

   1. Spécifier `./jcr:content/metadata/wm:documentName` dans le **[!UICONTROL Associer à la propriété]** champ .
Lors de la configuration des mappages dans Workfront, vous avez mappé `wm:documentName` Le champ Experience Manager Assets devient Document > Nom Workfront .

1. Cliquez sur le bouton **[!UICONTROL Créer un formulaire]** et faites glisser l’objet **[!UICONTROL Texte multiligne]** du formulaire. Cliquez sur le composant dans le formulaire. Dans le **[!UICONTROL Créer un formulaire]** tab :

   1. Spécifier `Document Description` dans le **[!UICONTROL Libellé du champ]** champ .

   1. Spécifier `./jcr:content/metadata/dc:description` dans le **[!UICONTROL Associer à la propriété]** champ .
Lors de la configuration des mappages dans Workfront, vous avez mappé `dc:description` Champ Experience Manager Assets dans Document > Description Workfront.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

   >[!VIDEO](https://video.tv.adobe.com/v/344314)

## Application des paramètres de métadonnées au dossier d’image {#apply-metadata-settings-image-folder}

Après avoir configuré les paramètres de métadonnées dans l’application as a Cloud Service Experience Manager, appliquez ces paramètres à la variable [dossier contenant l’image envoyée à partir de l’application Workfront](#send-image-workfront-assets).

Pour appliquer des paramètres de métadonnées au dossier d’image :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.

1. Sélectionnez le schéma de métadonnées dans la liste disponible, puis cliquez sur **[!UICONTROL Appliquer au(x) dossier(s)]**.

1. Sélectionnez le dossier de destination vers lequel [l’image est envoyée à partir de l’application Adobe Workfront](#send-image-workfront-assets) et cliquez sur **[!UICONTROL Appliquer]**.

Vous pouvez accéder à l’image dans Experience Manager Assets et afficher les métadonnées associées à l’image. Sélectionnez l’image et cliquez sur **[!UICONTROL Propriétés]** pour afficher les métadonnées de l’image.
