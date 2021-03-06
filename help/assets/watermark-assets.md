---
title: Mise en filigrane des ressources
description: Ajout d’un filigrane à vos ressources numériques.
contentOwner: AG
feature: Asset Management,Publishing
role: User,Admin
exl-id: 210f8925-bd15-4b4a-8714-5a1486eeb49e
source-git-commit: cf6cfb38a43004c8ac0c1d1e99153335a47860a8
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 100%

---

# Mise en filigrane de vos ressources {#watermark-assets}

[!DNL Adobe Experience Manager Assets] permet d’ajouter un filigrane numérique aux images. [!DNL Assets] prend en charge l’application d’une image en tant que filigrane pour d’autres fichiers image. Les filigranes peuvent aider les utilisateurs à vérifier l’authenticité et le copyright des ressources. Un filigrane peut également être utilisé pour indiquer le statut d’un document, tel que confidentiel, brouillon, validité, etc.

Pour configurer [!DNL Experience Manager] de façon à appliquer un filigrane à des ressources :

1. Un fichier PNG est appliqué comme filigrane. Chargez ce fichier dans votre référentiel DAM.

1. Accédez à **[!UICONTROL Outils > Ressources > Configurations des ressources]**.

1. Cliquez sur **[!UICONTROL Profil d’application d’un filigrane système]**.

1. Dans la [!UICONTROL page Profil d’application d’un filigrane système], spécifiez le chemin d’accès à l’image chargé dans votre référentiel DAM à l’étape 1.

1. Spécifiez l’échelle du filigrane, comprise entre 0,0 et 1,0, par rapport à la largeur de rendu, dans le champ **[!UICONTROL Échelle]**.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![Détecteur de doublons de ressources](assets/system-watermarking-profile.png)

   >[!NOTE]
   >
   >Si vous avez configuré le profil de filigrane système à l’aide du fichier de configuration `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.cfg.json` (configuration OSGi), vous pouvez continuer à l’utiliser, mais Adobe recommande d’utiliser la nouvelle méthode.


1. [Créez un profil de traitement](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) pour exploiter les microservices de ressources afin d’appliquer le filigrane.

   ![Profil de traitement des ressources pour créer un filigrane](assets/watermark-processing-profile.png)

   Assurez-vous que vous activez le bouton (bascule) **[!UICONTROL Filigrane]** lors de la création du profil de traitement.

1. [Appliquez les profils de traitement à un dossier](/help/assets/asset-microservices-configure-and-use.md#use-profiles) pour créer des ressources en filigrane.

## Conseils et restrictions {#tips-limitations-bestpractices}

* Vous pouvez utiliser une configuration unique pour mettre toutes vos ressources en filigrane. Une seule image est utilisée pour la mise en filigrane et sa largeur est fixe.
* Vous pouvez placer le filigrane au centre sans mosaïque.
* Les filigranes à base de texte ne sont pas pris en charge.

>[!MORELIKETHIS]
>
>* [Aperçu sur les microservices de ressources](/help/assets/asset-microservices-overview.md).
>* [Utilisation des microservices de ressources avec des profils de traitement](/help/assets/asset-microservices-configure-and-use.md).

