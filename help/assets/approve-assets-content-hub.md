---
title: Approuver des ressources pour le hub de contenus
description: Découvrez comment approuver des ressources dans Assets as a Cloud Service pour les rendre disponibles dans Content Hub.
exl-id: fc849028-ab56-4388-b8d6-e36cac8f868f
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '774'
ht-degree: 6%

---

# Approuver des ressources pour le hub de contenus {#approve-assets-content-hub}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![Approuver des ressources pour Content Hub](assets/content-hub-approve-assets.png)

>[!AVAILABILITY]
>
>Le guide Content Hub est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant Adobe Acrobat AI pour répondre à vos requêtes.
>
>[!BADGE PDF de guide Content Hub]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Les responsables de marques et les marketeurs contrôlent strictement les ressources de marque. Seule la version approuvée et la dernière version de la ressource peut être utilisée dans Content Hub, ce qui garantit la cohérence de la marque sur tous les canaux et applications.

Vous pouvez approuver des ressources à l’aide d’AEM Assets as a Cloud Service afin de rationaliser la gestion des ressources, en veillant à un processus contrôlé et efficace de gestion des ressources.

## Avant de commencer {#pre-requisites}

Avant de commencer, vous devez disposer des éléments suivants :

* Accès à AEM Assets as a Cloud Service

* Autorisations d’écriture pour modifier les métadonnées de la ressource afin de pouvoir modifier le champ **[!UICONTROL Status]** disponible dans les [propriétés de la ressource](/help/assets/manage-organize-assets-view.md##manage-asset-status) pour une ressource.

## Approuver des ressources pour le hub de contenus{#approve-assets-for-content-hub}

Les ressources marquées comme `approved` dans Assets as a Cloud Service sont automatiquement disponibles dans Content Hub.

>[!NOTE]
>
Assets as a Cloud Service et Content Hub doivent utiliser la même organisation pour que les ressources s’affichent dans Content Hub.

Pour définir l’état de la ressource sur `approved` à l’aide de la vue Assets dans AEM as a Cloud Service :

1. Sélectionnez la ressource, puis cliquez sur **[!UICONTROL Détails]** dans la barre d’outils.

1. Dans l’onglet **[!UICONTROL Basic]** , sélectionnez l’état de la ressource `approved` dans la liste déroulante **[!UICONTROL Status]** .
1. Cliquez sur **[!UICONTROL Enregistrer]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3433172)

Si vous devez approuver des ressources à l’aide de la vue d’administration, reportez-vous à la section [Approbation des ressources à l’aide de la vue d’administration](/help/assets/approve-assets.md#approve-assets).

## Approbation en bloc de ressources pour Content Hub à l’aide de la vue Assets {#bulk-approve-assets-content-hub}

Approbation en bloc de ressources à l’aide de la vue Assets pour AEM Assets as a Cloud Service. Toutes les ressources, approuvées en bloc, sont ensuite disponibles dans Content Hub.

Pour approuver en masse des ressources dans un dossier dans la vue Assets :

1. Sélectionnez la ou les ressources, puis cliquez sur **[!UICONTROL Modifier les métadonnées en bloc]**.

1. Sélectionnez **[!UICONTROL Approuvé]** dans le champ **[!UICONTROL État]** disponible dans la section [!UICONTROL Propriétés] du volet de droite.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Automatiser l’approbation des ressources nouvellement ingérées dans la vue d’administration {#automate-approval-newly-ingested-assets}

Après avoir basculé de la vue Assets à la vue Admin, vous pouvez configurer les paramètres du dossier afin que toutes les nouvelles ressources ajoutées au dossier soient automatiquement approuvées.

Vous pouvez basculer entre les vues Admin et Assets comme suit :
![Présentation de My Workspace](assets/assets-view.png)

Pour automatiser l’approbation des ressources nouvellement ingérées dans [!DNL Experience Manager Admin view], procédez comme suit :

1. Créez un dossier dans l’environnement de création (https://author-pXXX-eYYY.adobeaemcloud.com). Remplacez _XXX_ par votre ID de programme et _YYY_ par l’ID d’environnement de l’Experience Manager.
1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Assets]** > **[!UICONTROL Profils de métadonnées]**.
1. Cliquez sur **[!UICONTROL Créer]** dans le coin supérieur droit de la page.
1. Ajoutez un titre de profil et cliquez sur **[!UICONTROL Créer]**. Le profil de métadonnées a été créé.
1. Sélectionnez le profil de métadonnées nouvellement créé et cliquez sur **[!UICONTROL Modifier _(e)_]**. <br>Le formulaire **[!UICONTROL Modifier le profil de métadonnées]**s’ouvre avec l’onglet **[!UICONTROL De base]**surligné.
1. Faites glisser et déposez un **[!UICONTROL champ de texte d’une seule ligne]** de la section **[!UICONTROL Créer le formulaire]** dans la partie droite de la section Métadonnées dans le formulaire.
1. Cliquez sur le champ nouvellement ajouté, puis effectuez les mises à jour suivantes dans le panneau **[!UICONTROL Paramètres]** :
   1. Remplacez le **[!UICONTROL libellé du champ]** par _Assets approuvé_.
   1. Mettez à jour la **[!UICONTROL map to property]** vers _./jcr:content/metadata/dam:status_.
   1. Remplacez la valeur par défaut par _approved_.

1. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Sur la page **[!UICONTROL Profils de métadonnées]** , sélectionnez le profil de métadonnées nouvellement créé.
1. Cliquez sur **[!UICONTROL Appliquer le profil de métadonnées au(x) dossier(s)]** dans la barre d’actions supérieure.
1. Sélectionnez le ou les dossiers à approuver et cliquez sur **[!UICONTROL Appliquer]**.
   <br> L’autorisation pour l’ensemble du dossier est définie pour approbation et toutes les ressources chargées dans ce dossier sont automatiquement approuvées.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
Cette approche approuve les ressources nouvellement créées dans le dossier . Pour les ressources existantes dans le dossier, vous devez les sélectionner et les approuver manuellement.

## Gestion des ressources chargées à l’aide de Content Hub {#manage-assets-uploaded-using-content-hub}

[ Les utilisateurs Content Hub autorisés à ajouter des ressources](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets) peuvent [ ajouter des ressources à Content Hub](/help/assets/upload-brand-approved-assets.md) à partir d’un système de fichiers local ou importer des ressources à partir de OneDrive ou de sources de données de Dropbox. Toutes les ressources s’affichent au niveau supérieur dans Content Hub, quelle que soit la structure de dossiers disponible sur votre système de fichiers local ou OneDrive et les sources de données Dropbox pour améliorer les fonctionnalités de recherche.

L’affichage des ressources chargées à l’aide de Content Hub dépend de l’activation ou non de la [activation du bouton d’approbation automatique](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) :

* Si le bouton d’approbation automatique **[!UICONTROL est activé, les ressources que vous chargez à l’aide de Content Hub sont automatiquement disponibles.]**

* Si le bouton d’approbation **[!UICONTROL automatique]** est désactivé, les ressources que vous chargez à l’aide de Content Hub ne s’affichent pas automatiquement. Les ressources sont disponibles dans le dossier `hydrated-assets` de votre environnement as a Cloud Service Assets. Accédez au dossier et [modifiez en masse](#bulk-approve-assets-content-hub) l’état de ces ressources sur `Approved` pour que ces ressources s’affichent dans Content Hub.

![Processus d’approbation de Content Hub](/help/assets/assets/content-hub-approval.png)
