---
title: Approbation des ressources dans Experience Manager
description: Découvrez comment approuver des ressources dans [!DNL Experience Manager].
role: User
exl-id: fe61a0f1-94d3-409a-acb9-195979668c25
source-git-commit: 9b3b93100c45c7053549c3f9899a344ca7db104d
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 2%

---

# Approuver des ressources dans [!DNL Experience Manager]

Les responsables de marques et les marketeurs contrôlent strictement les ressources de marque. Seule la version approuvée et la dernière version de la ressource peut être utilisée, ce qui garantit la cohérence de la marque sur tous les canaux et applications.

Vous pouvez approuver des ressources dans AEM Assets afin de rationaliser la gestion des ressources, en veillant à ce que le processus de gestion des ressources soit contrôlé et efficace.

## Avant de commencer {#pre-requisites}

Vous devez avoir accès à l’as a Cloud Service AEM Assets et aux autorisations nécessaires pour modifier la propriété **[!UICONTROL État de la révision]** pour une ressource.

## Configuration

Vous devez effectuer une mise à jour unique du schéma de métadonnées applicable dans la vue d’administration avant de pouvoir approuver une ressource. Vous pouvez ignorer cette configuration pour la vue Assets. Pour configurer le schéma de métadonnées, procédez comme suit :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.
1. Sélectionnez le schéma de métadonnées applicable et cliquez sur **[!UICONTROL Modifier]**. <br>L’ **[!UICONTROL éditeur de formulaire de schéma de métadonnées]** s’ouvre avec l’onglet **[!UICONTROL De base]** surligné.
1. Faites défiler l’écran vers le bas et cliquez sur **[!UICONTROL État de la révision]**.
1. Cliquez sur l’onglet **[!UICONTROL Rules]** dans le panneau de droite.
1. Décochez **[!UICONTROL Désactiver la modification]** et cliquez sur **[!UICONTROL Enregistrer]**.
Si vous devez afficher la propriété à laquelle le champ **[!UICONTROL État de la révision]** est mappé, accédez à l’onglet **[!UICONTROL Paramètres]** et affichez la valeur `./jcr:content/metadata/dam:status` dans le champ **[!UICONTROL Associer à la propriété]**.

>[!NOTE]
>
>Si vos ressources ou dossiers ont un schéma par défaut différent, veillez à effectuer cette mise à jour dans ce schéma particulier.

## Approuver des ressources {#approve-assets}

Pour approuver des ressources dans [!DNL Experience Manager Admin view], procédez comme suit :

1. Sélectionnez la ou les ressources et cliquez sur **[!UICONTROL Propriétés]** dans le volet supérieur.
1. Dans l’onglet **[!UICONTROL Basic]**, faites défiler l’écran jusqu’à **[!UICONTROL Review Status]**.
1. Remplacez l’état de révision par **[!UICONTROL Approuvé]**.
   ![image](/help/assets/assets/approve-old-ui.png)
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3427430)

   De même, vous pouvez approuver des ressources à l’aide de la [nouvelle vue Assets](/help/assets/manage-organize-assets-view.md).

## Approbation en bloc de ressources {#bulk-approve-assets}

Rationalisez votre workflow en approuvant rapidement plusieurs ressources à la fois. Vous pouvez approuver en masse des ressources afin d’accélérer le processus d’approbation, ce qui vous permet de gagner du temps et d’améliorer votre productivité.
<br>Pour approuver des ressources en vrac dans [!DNL Experience Manager Admin view], procédez comme suit :

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
>Cette approche approuve les ressources nouvellement créées dans le dossier . Pour les ressources existantes dans le dossier, vous devez les sélectionner et les approuver manuellement. <br> Vous pouvez également utiliser l’option **[!UICONTROL Retraiter]** pour appliquer les modifications du profil de métadonnées aux ressources plus anciennes.

De même, pour approuver en masse des ressources dans un dossier de la vue Assets :

1. Sélectionnez la ou les ressources, puis cliquez sur **[!UICONTROL Modifier les métadonnées en bloc]**.

1. Sélectionnez **[!UICONTROL Approuvé]** dans le champ **[!UICONTROL État]** disponible dans la section [!UICONTROL Propriétés] du volet de droite.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Copie de l’URL de diffusion pour les ressources approuvées {#copy-delivery-url-approved-assets}

L’URL de diffusion pour toutes les ressources approuvées dans le référentiel est disponible si [!UICONTROL Dynamic Media avec les fonctionnalités OpenAPI] sont activées sur votre instance AEM as a Cloud Service.

Pour copier l’URL de diffusion d’une ressource approuvée dans le référentiel :

1. Sélectionnez la ressource et cliquez sur **[!UICONTROL Details]**.

1. Cliquez sur l’icône Rendus disponible dans le volet de droite.

1. Sélectionnez **[!UICONTROL Dynamic Media avec OpenAPI]** disponible dans la section **[!UICONTROL Dynamic]** .

1. Cliquez sur **[!UICONTROL Copier l’URL]** pour copier l’URL de diffusion de la ressource.
   ![Copier l’URL de diffusion](/help/assets/assets/copy-delivery-url.png)

   >[!NOTE]
   >
   >L’option de copie de l’URL de diffusion pour les ressources approuvées est disponible dans la vue Assets.
