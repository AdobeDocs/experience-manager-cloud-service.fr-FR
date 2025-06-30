---
title: Approbation de ressources dans Experience Manager
description: Découvrez comment approuver des ressources dans  [!DNL Experience Manager].
role: User
exl-id: fe61a0f1-94d3-409a-acb9-195979668c25
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 7%

---

# Approbation de ressources dans [!DNL Experience Manager]

Les chefs de marque et les marketeurs contrôlent strictement les ressources de la marque. Seule la version approuvée et la plus récente de la ressource peut être utilisée, ce qui garantit la cohérence de la marque sur tous les canaux et applications.

Vous pouvez approuver des ressources dans AEM Assets afin de rationaliser leur gestion, ce qui garantit un processus contrôlé et efficace de gestion des ressources.

## Avant de commencer {#pre-requisites}

Vous devez avoir accès à AEM Assets as a Cloud Service et disposer des autorisations pour modifier la propriété **[!UICONTROL Statut de révision]** d’une ressource.

## Configuration

Vous devez effectuer une mise à jour unique sur le schéma de métadonnées applicable dans la vue Administrateur avant de pouvoir approuver une ressource. Vous pouvez ignorer cette configuration pour la vue Assets. Pour configurer le schéma de métadonnées, procédez comme suit :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.
1. Sélectionnez le schéma de métadonnées applicable et cliquez sur **[!UICONTROL Modifier]**. <br>L’**[!UICONTROL Éditeur de formulaire de schéma de métadonnées]** s’ouvre avec l’onglet **[!UICONTROL De base]** en surbrillance.
1. Faites défiler vers le bas et cliquez sur **[!UICONTROL Statut de révision]**.
1. Cliquez sur l’onglet **[!UICONTROL Règles]** dans le panneau latéral droit.
1. Décochez **[!UICONTROL Désactiver la modification]**.
Si vous devez afficher la propriété à laquelle le champ **[!UICONTROL Statut de la révision]** est mappé, accédez à l’onglet **[!UICONTROL Paramètres]** et affichez la valeur `./jcr:content/metadata/dam:status` dans le champ **[!UICONTROL Mapper à la propriété]**.
1. Faites glisser et déposez un champ **[!UICONTROL Liste déroulante]** de la section **[!UICONTROL Créer le formulaire]** sur le côté droit vers la section Métadonnées du formulaire.
1. Cliquez sur le champ nouvellement ajouté, puis effectuez les mises à jour suivantes dans le panneau **[!UICONTROL Paramètres]** :
   1. Remplacez **[!UICONTROL Libellé du champ]** par _Cible d&#39;approbation_.
   1. Mettez à jour **[!UICONTROL Mappez à la propriété]** sur _./jcr:content/metadata/dam:activationTarget_.
   1. Ajoutez les choix avec `contenthub` et `delivery` comme valeurs d’option.

   >[!NOTE]
   >
   >Lorsque vous sélectionnez la cible de validation en tant que Content Hub dans la vue Assets, les ressources sont mises à la disposition des utilisateurs de la même organisation dans Content Hub. Lorsque vous sélectionnez la cible de validation comme Diffusion , les ressources sont disponibles pour tous les utilisateurs.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

>[!NOTE]
>
>Si vos ressources ou dossiers ont un schéma par défaut différent, veillez à effectuer cette mise à jour dans ce schéma particulier.

## Approuver des ressources {#approve-assets}

Pour approuver des ressources dans [!DNL Experience Manager Admin view], procédez comme suit :

1. Sélectionnez la ou les ressources, puis cliquez sur **[!UICONTROL Propriétés]** dans le volet supérieur.
1. Dans l’onglet **[!UICONTROL De base]**, faites défiler l’écran jusqu’à **[!UICONTROL Statut de révision]**.
1. Remplacez le statut de révision par **[!UICONTROL Approuvé]**.
   ![image](/help/assets/assets/approve-old-ui.png)
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3427430)

   De même, vous pouvez approuver des ressources à l’aide de la [ nouvelle vue Assets ](/help/assets/manage-organize-assets-view.md).

## Approbation en bloc de ressources {#bulk-approve-assets}

Simplifiez votre workflow en approuvant rapidement plusieurs ressources à la fois. Vous pouvez approuver en bloc des ressources pour accélérer le processus d’approbation, ce qui vous permet de gagner du temps et d’améliorer la productivité.
<br>Pour approuver des ressources en bloc dans [!DNL Experience Manager Admin view], procédez comme suit :

1. Créez un dossier dans l’environnement de création (https://author-pXXX-eYYY.adobeaemcloud.com). Remplacez _XXX_ par votre ID de programme et _YYY_ par l’ID d’environnement d’Experience Manager.
1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Assets]** > **[!UICONTROL Profils de métadonnées]**.
1. Cliquez sur **[!UICONTROL Créer]** en haut à droite de la page.
1. Ajoutez un titre de profil et cliquez sur **[!UICONTROL Créer]**. Le profil de métadonnées a été créé.
1. Sélectionnez le profil de métadonnées que vous venez de créer et cliquez sur **[!UICONTROL Modifier le(s) _(s)_]**. <br>Le formulaire **[!UICONTROL Modifier le profil de métadonnées]**&#x200B;s’ouvre avec l’onglet **[!UICONTROL De base]**&#x200B;en surbrillance.
1. Effectuez un glisser-déposer d’un **[!UICONTROL champ de texte monoligne]** de la section **[!UICONTROL Créer un formulaire]** sur le côté droit de la section Métadonnées du formulaire.
1. Cliquez sur le champ nouvellement ajouté, puis effectuez les mises à jour suivantes dans le panneau **[!UICONTROL Paramètres]** :
   1. Remplacez **[!UICONTROL Libellé du champ]** par _Assets approuvé_.
   1. Mettez à jour **[!UICONTROL Mappez à la propriété]** sur _./jcr:content/metadata/dam:status_.
   1. Remplacez la valeur Par défaut par _approuvé_.

1. Faites glisser et déposez un champ **[!UICONTROL Liste déroulante]** de la section **[!UICONTROL Créer le formulaire]** sur le côté droit vers la section Métadonnées du formulaire.
1. Cliquez sur le champ nouvellement ajouté, puis effectuez les mises à jour suivantes dans le panneau **[!UICONTROL Paramètres]** :
   1. Remplacez **[!UICONTROL Libellé du champ]** par _Cible d&#39;approbation_.
   1. Mettez à jour **[!UICONTROL Mappez à la propriété]** sur _./jcr:content/metadata/dam:activationTarget_.
   1. Ajoutez les choix avec `contenthub` et `delivery` comme valeurs d’option.

   >[!NOTE]
   >
   >Lorsque vous sélectionnez la cible de validation en tant que Content Hub dans la vue Assets, les ressources sont mises à la disposition des utilisateurs de la même organisation dans Content Hub. Lorsque vous sélectionnez la cible de validation comme Diffusion , les ressources sont disponibles pour tous les utilisateurs.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Sur la page **[!UICONTROL Profils de métadonnées]**, sélectionnez le profil de métadonnées que vous venez de créer.
1. Cliquez sur **[!UICONTROL Appliquer le profil de métadonnées au(x) dossier(s)]** dans la barre d’actions supérieure.
1. Sélectionnez le ou les dossiers à approuver, puis cliquez sur **[!UICONTROL Appliquer]**.
   <br> L’autorisation pour l’ensemble du dossier est définie pour approbation et toutes les ressources chargées dans ce dossier sont automatiquement approuvées.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
>Cette approche approuve les ressources nouvellement créées dans le dossier . Pour les ressources existantes dans le dossier , vous devez les sélectionner et les approuver manuellement. <br> Vous pouvez également utiliser l’option **[!UICONTROL Retraiter]** pour appliquer les modifications du profil de métadonnées aux ressources plus anciennes.

De même, pour approuver en bloc des ressources dans un dossier dans la vue Assets :

1. Sélectionnez la ou les ressources, puis cliquez sur **[!UICONTROL Modifier les métadonnées en masse]**.

1. Sélectionnez **[!UICONTROL Approuvé]** dans le champ **[!UICONTROL Statut]** disponible dans la section [!UICONTROL Propriétés] du volet de droite.

   Si vous sélectionnez le statut comme `Approved` et si [Dynamic Media avec des fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) ou [Content Hub](/help/assets/product-overview.md), ou les deux sont activés pour votre Experience Manager Assets, vous pouvez afficher les options `Delivery` et `Content Hub` disponibles dans le champ **[!UICONTROL Cible d’approbation]**.

   * Sélectionnez **[!UICONTROL Diffusion]** pour rendre les ressources disponibles pour Dynamic Media avec les fonctionnalités OpenAPI et Content Hub. Si Content Hub n’est pas activé, la sélection de cette option rend les ressources disponibles uniquement pour Dynamic Media avec les fonctionnalités OpenAPI.
   * Sélectionnez **[!UICONTROL Content Hub]** pour rendre les ressources disponibles pour Content Hub.

   ![Statut d&#39;approbation](/help/assets/assets/approval-status-delivery.png)

   Si vous n’utilisez pas le formulaire de métadonnées par défaut et que vous ne pouvez pas afficher le champ **[!UICONTROL Cible d’approbation]**, [modifiez votre formulaire de métadonnées](/help/assets/metadata-assets-view.md#metadata-forms) pour faire glisser le champ **[!UICONTROL Approbation de]** des composants disponibles vers votre formulaire de métadonnées et cliquez sur **[!UICONTROL Enregistrer]**.

   >[!NOTE]
   >
   >Si vous sélectionnez la cible de validation comme `Content Hub` dans la vue Assets d’une organisation, les ressources sont mises à la disposition des utilisateurs de la même organisation dans Content Hub.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Copier l’URL de diffusion des ressources approuvées {#copy-delivery-url-approved-assets}

L’URL de diffusion de toutes les ressources approuvées dans le référentiel est disponible si les fonctionnalités [!UICONTROL Dynamic Media avec OpenAPI] sont activées sur votre instance AEM as a Cloud Service.

Pour copier l’URL de diffusion d’une ressource approuvée dans le référentiel :

1. Sélectionnez la ressource et cliquez sur **[!UICONTROL Détails]**.

1. Cliquez sur l’icône Dynamic Media disponible dans le volet de droite.

1. Sélectionnez **[!UICONTROL Dynamic Media avec OpenAPI]** disponible dans le panneau **[!UICONTROL Dynamic Media]**.

1. Cliquez sur **[!UICONTROL Copier l’URL]** pour copier l’URL de diffusion de la ressource.
   ![Rendus dynamiques](/help/assets/assets/dm-with-openapi-non-image-assets.png)

   >[!NOTE]
   >
   >L’option permettant de copier l’URL de diffusion pour les ressources approuvées est uniquement disponible dans la vue Assets.

Pour plus d’informations sur les autres rendus qui s’affichent dans le panneau Dynamic Media, voir [Affichage et téléchargement des rendus Dynamic Media](/help/assets/renditions.md#view-download-dm-renditions).
