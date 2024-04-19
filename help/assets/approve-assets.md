---
title: Approbation des ressources dans Experience Manager
description: Découvrez comment approuver des ressources dans [!DNL Experience Manager].
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 3%

---

# Approbation des ressources dans [!DNL Experience Manager]

Les responsables de marques et les marketeurs contrôlent strictement les ressources de marque. Seule la version approuvée et la dernière version de la ressource peut être utilisée, ce qui garantit la cohérence de la marque sur tous les canaux et applications.

Vous pouvez approuver des ressources dans AEM Assets afin de rationaliser la gestion des ressources, en veillant à ce que le processus de gestion des ressources soit contrôlé et efficace.

## Avant de commencer {#pre-requisites}

Vous devez avoir accès à AEM Assets as a Cloud Service et aux autorisations nécessaires pour modifier la variable **[!UICONTROL État de révision]** pour une ressource.

## Configuration

Vous devez effectuer une mise à jour unique du schéma de métadonnées applicable dans la variable [!DNL Experience Manager] avant de pouvoir approuver une ressource. Vous pouvez ignorer cette configuration pour [!DNL Experience Manager Assets]. Pour configurer le schéma de métadonnées, procédez comme suit :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.
1. Sélectionnez le schéma de métadonnées approprié et cliquez sur **[!UICONTROL Modifier]**. <br>La variable **[!UICONTROL Éditeur de formulaire de schéma de métadonnées]** ouvre avec la fonction **[!UICONTROL De base]** en surbrillance.
1. Faites défiler la page vers le bas et cliquez sur **[!UICONTROL État de révision]**.
1. Cliquez sur le bouton **[!UICONTROL Règles]** dans le panneau de droite.
1. Décocher **[!UICONTROL Désactiver la modification]** et cliquez sur **[!UICONTROL Enregistrer]**.

>[!NOTE]
>
>Si vos ressources ou dossiers ont un schéma par défaut différent, veillez à effectuer cette mise à jour dans ce schéma particulier.

## Approbation des ressources {#approve-assets}

Vous pouvez approuver des ressources dans les deux [!DNL Experience Manager] et [!DNL Experience Manager Assets]. Pour approuver des ressources dans [!DNL Experience Manager], procédez comme suit :

1. Sélectionnez la ou les ressources, puis cliquez sur **[!UICONTROL Propriétés]** dans le volet supérieur.
1. Dans le **[!UICONTROL De base]** onglet, faites défiler jusqu’à **[!UICONTROL État de révision]**.
1. Remplacez l’état de révision par **[!UICONTROL Approuvé]**.
   ![image](/help/assets/assets/approve-old-ui.png)
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3427430)

   De même, vous pouvez approuver des ressources à l’aide de la variable [nouvelle vue Assets](https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/manage-organize.html?lang=en#manage-asset-status).

## Approbation en bloc de ressources {#bulk-approve-assets}

Rationalisez votre workflow en approuvant rapidement plusieurs ressources à la fois. Vous pouvez approuver en masse des ressources afin d’accélérer le processus d’approbation, ce qui vous permet de gagner du temps et d’améliorer votre productivité.
<br>Procédez comme suit pour approuver des ressources en bloc dans [!DNL Experience Manager]:

1. Créez un dossier dans l’environnement de création (https://author-pXXX-eYYY.adobeaemcloud.com). Remplacer _XXX_ avec votre ID de programme et _AAAA_ avec l’ID d’environnement du Experience Manager.
1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Profils de métadonnées]**.
1. Cliquez sur **[!UICONTROL Créer]** dans le coin supérieur droit de la page.
1. Ajoutez un titre de profil et cliquez sur **[!UICONTROL Créer]**. Le profil de métadonnées a été créé.
1. Sélectionnez le profil de métadonnées que vous venez de créer, puis cliquez sur **[!UICONTROL Modifier _(e)_]**. <br>La variable **[!UICONTROL Modifier le profil de métadonnées]**le formulaire s’ouvre avec la fonction **[!UICONTROL De base]**en surbrillance.
1. Faites glisser et déposez un **[!UICONTROL Champ de texte d’une seule ligne]** de la **[!UICONTROL Créer un formulaire]** dans la partie droite de la section Métadonnées du formulaire.
1. Cliquez sur le champ nouvellement ajouté, puis effectuez les mises à jour suivantes dans la variable **[!UICONTROL Paramètres]** panel :
   1. Modifiez la variable **[!UICONTROL Libellé du champ]** to _Ressources approuvées_.
   1. Mettez à jour le **[!UICONTROL Associer à la propriété]** to _./jcr:content/metadata/dam:status_.
   1. Remplacez la valeur par défaut par _approuvé_.

1. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Dans le **[!UICONTROL Profils de métadonnées]** , sélectionnez le profil de métadonnées nouvellement créé.
1. Cliquez sur **[!UICONTROL Application d’un profil de métadonnées à un ou plusieurs dossiers]** dans la barre d’actions supérieure.
1. Sélectionnez le ou les dossiers à approuver, puis cliquez sur **[!UICONTROL Appliquer]**.
   <br> L’autorisation pour l’ensemble du dossier est définie pour approbation et toutes les ressources chargées dans ce dossier sont automatiquement approuvées.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
>Cette approche approuve les ressources nouvellement créées dans le dossier . Pour les ressources existantes dans le dossier, vous devez les sélectionner et les approuver manuellement. <br> Vous pouvez également utiliser la variable **[!UICONTROL Retraiter]** pour appliquer les modifications du profil de métadonnées aux ressources plus anciennes.
