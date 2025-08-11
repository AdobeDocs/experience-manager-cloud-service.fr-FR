---
title: Aperçu des ressources avant de les utiliser dans vos pages AEM Sites
description: Dynamic Media avec des fonctionnalités OpenAPI vous permet de prévisualiser des ressources sur les pages d’aperçu Sites Adobe Experience Manager (AEM). Cet aperçu de ressource vous permet, à vous et à vos parties prenantes, de vérifier et de valider les mises à jour de vos ressources avant de publier les pages de création (avec les ressources mises à jour) pour la consommation publique.
role: Admin, User
source-git-commit: e343cc5754ec5565e57a5a932d59d7bfe78c6027
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# Aperçu des ressources avant de les utiliser dans vos pages AEM Sites {#asset-preview-using-Dynamic-Media-with-OpenAPI-capabilities}

[!DNL Dynamic Media with OpenAPI capabilities] vous permet de prévisualiser les ressources disponibles dans vos pages de création [!DNL Adobe Experience Manager (AEM) Sites] avant de les rendre publiques. L’aperçu de la ressource est disponible au niveau auteur et aperçu de votre site.

Pour [prévisualiser des ressources sur les pages d’aperçu d’AEM Sites](#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities), mettez à jour les pages d’auteur de votre site en ajoutant les ressources à prévisualiser ou en remplaçant celles qui sont disponibles dans votre page de sites actifs. Publiez ensuite les pages de création mises à jour dans le niveau d’aperçu pour générer une URL d’aperçu.

Partagez la page d’aperçu avec les parties prenantes pour recueillir leurs commentaires sur la qualité visuelle et l’alignement contextuel des ressources mises à jour. Affinez les ressources en fonction des commentaires. Créez et gérez plusieurs versions de la ressource pendant le cycle de révision.

Une fois que vous avez finalisé les ressources pour une utilisation publique, mettez-les à jour dans vos pages de création et publiez les pages au niveau de publication pour un accès public.

## Avant de commencer{#prerequisites-for-previewing-assets-using-Dynamic-Media-with-OpenAPI-capabilities}

Vérifiez que vous disposez des éléments suivants :

* Accès à [!DNL AEM Assets as a Cloud Service].
* Autorisation de modifier la propriété Statut des ressources.
* [Ajout d’une valeur [!UICONTROL Aperçu] à la propriété de métadonnées Statut du  disponible dans l’onglet [!UICONTROL De base]](/help/assets/metadata-assets-view.md#edit-metadata-forms) du formulaire de métadonnées appliqué au dossier contenant les ressources à prévisualiser.
  ![Option Ajouter un aperçu](/help/assets/assets/metedata-form-preview.png)
* Clé permettant de générer le jeton d’aperçu. [Contactez l’assistance Adobe](https://helpx.adobe.com/in/contact.html) puis demandez la clé.

## Aperçu des ressources dans la page d’aperçu de vos sites {#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities}

Vous pouvez prévisualiser les nouvelles ressources ou les ressources déjà approuvées. Les ressources approuvées s’affichent uniquement sur vos pages Sites actives.

Exécutez les étapes suivantes pour définir le statut de la ressource à prévisualiser dans [!DNL Assets View], puis publiez votre page de création Sites dans le niveau d’aperçu pour générer une URL d’aperçu de la page :

1. Définissez le statut de la ressource sur **[!UICONTROL Aperçu]** en procédant comme suit :

   1. Dans [!DNL Assets View], sélectionnez **[!UICONTROL Assets]** et accédez à votre dossier.
   1. Sélectionnez la ressource à prévisualiser.
   1. Cliquez sur **[!UICONTROL Détails]**.
   1. Dans le [!UICONTROL Panneau d’informations], définissez **[!UICONTROL Statut]** sur **[!UICONTROL Aperçu]**, puis cliquez sur **[!UICONTROL Enregistrer]**.
      ![Prévisualisation](/help/assets/assets/preview-boat-at-bay.png)

1. Accédez à la page de création de Sites. Exécutez les étapes de la section [Accès aux ressources distantes dans l’éditeur de page d’AEM](/help/assets/integrate-remote-approved-assets-with-sites.md#access-remote-assets-in-aem-page-editor) pour sélectionner la ressource que vous avez récemment définie sur Aperçu (statut) à l’aide du panneau Sélecteur de ressources.

   >[!NOTE]
   >
   > Le sélecteur de ressources affiche les ressources dont la mise à jour de statut la plus récente est définie sur Approuvé ou Aperçu.

1. Publiez votre page dans le niveau d’aperçu à l’aide de l’option **[!UICONTROL Gérer la publication]**. Exécutez les étapes de la section [Publication de contenu en vue de la prévisualisation](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/sites/authoring/sites-console/previewing-content) pour publier votre page au niveau d’aperçu. Après publication, générez une URL d’aperçu de votre page. La page Aperçu affiche les ressources (avec les mises à jour de statut les plus récentes) dans votre page Sites.

Partagez cette URL d’aperçu avec les parties prenantes pour examen et commentaires. Assurez-vous que vos parties prenantes ont accès à la page d’aperçu. Voir [Accès au service d’aperçu](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments#access-preview-service) pour plus d’informations sur la fourniture d’accès aux pages d’aperçu.

>[!NOTE]
>
>Le composant principal [Image V3](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/wcm-components/image#version-and-compatibility) prend en charge la version d’aperçu des ressources par défaut. Lorsque vous sélectionnez une version d’aperçu d’une ressource (ressource avec statut d’aperçu) à l’aide du panneau [Sélecteur de ressources](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/asset-selector-upload), le composant Image V3 la rend automatiquement dans le niveau Aperçu (une version d’aperçu sur votre page de création Sites).

Une fois la version de la ressource finalisée, [publiez vos pages au niveau de publication](#publish-your-pages-to-publish-tier) pour la consommation publique.

## Publiez vos pages avec des ressources approuvées pour une utilisation publique.{#publish-your-pages-to-publish-tier}

Après avoir finalisé la version de la ressource pour une utilisation publique, définissez le statut de la ressource sur **[!UICONTROL Approuvé]**. Publiez ensuite vos pages dans le niveau de publication. Pour publier votre page, procédez comme suit :

1. Suivez l’étape 1 de la section [Aperçu des ressources dans la page d’aperçu de vos sites](#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities) ci-dessus pour modifier le statut de la ressource en **[!UICONTROL Approuvé]**.
1. Accédez à la page de création de Sites et publiez-la sur le [!DNL Publish tier]. Publiez les pages en suivant les étapes décrites dans la section [Publication à partir de l’éditeur de page](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/sites/authoring/page-editor/publishing#publishing-from-the-page-editor).
Vous pouvez également suivre les étapes de la section [Publication de pages à partir de la console Sites](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/sites/authoring/sites-console/publishing-pages#publishing-from-the-sites-console) pour publier votre page à partir de la console de votre site.

   >[!NOTE]
   >
   > Seules les ressources approuvées peuvent être diffusées au niveau Publication. Approuvez les ressources avant de publier votre page au niveau Publication pour une utilisation publique.

   ![La page a été publiée](/help/assets/assets/the-page-has-been-publushed.png)
Un message de confirmation **[!UICONTROL La page a été publiée]** s’affiche après la publication réussie. Accédez à la page publiée au niveau de publication pour confirmer que les mises à jour sont en ligne et que le contenu s’affiche comme prévu.

