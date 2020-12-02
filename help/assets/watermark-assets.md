---
title: Mise en filigrane des ressources
description: Ajout d’un filigrane à vos ressources numériques.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5be8ab734306ad1442804b3f030a56be1d3b5dfa
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 88%

---


# Mise en filigrane de vos ressources {#watermark-assets}

[!DNL Adobe Experience Manager Assets] permet d’ajouter un filigrane numérique aux images. [!DNL Assets] prend en charge l’application d’une image en tant que filigrane pour d’autres fichiers image. Les filigranes peuvent aider les utilisateurs à vérifier l’authenticité et le copyright des ressources. Un filigrane peut également être utilisé pour indiquer l’état d’un document, tel que confidentiel, brouillon, validité, etc.

Procédez de la manière suivante pour configurer [!DNL Experience Manager] pour mettre des ressources en filigrane :

1. Un fichier PNG est appliqué comme filigrane. Chargez ce fichier dans votre référentiel DAM.

1. Accédez au référentiel Git [!DNL Cloud Manager] associé à votre environnement. Validez un fichier nommé `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.cfg.json` dans le référentiel avec le contenu suivant. Pour obtenir des instructions, voir [comment effectuer la configuration OSGi dans [!DNL Experience Manager] as a [!DNL Cloud Service]](/help/implementing/deploying/configuring-osgi.md).

   ```json
   {
   "watermark": "/content/dam/<path-to-watermark-image.png>",
    "width": 100
   }
   ```

1. [Créez un profil de traitement](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) pour exploiter les microservices de ressources afin d’appliquer le filigrane.

   ![Profil de traitement des ressources pour créer un filigrane](assets/watermark-processing-profile.png)

1. [Appliquez les profils de traitement à un dossier](/help/assets/asset-microservices-configure-and-use.md#use-profiles) pour créer des ressources en filigrane.

## Conseils et restrictions {#tips-limitations-bestpractices}

* Vous pouvez utiliser une configuration unique pour mettre toutes vos ressources en filigrane. Une seule image est utilisée pour la mise en filigrane et sa largeur est fixe.
* Vous pouvez placer le filigrane au centre sans mosaïque.
* Les filigranes à base de texte ne sont pas pris en charge.

>[!MORELIKETHIS]
>
>* [Présentation des microservices de ressources](/help/assets/asset-microservices-overview.md).
>* [Utilisation des microservices de ressources avec des profils de traitement](/help/assets/asset-microservices-configure-and-use.md).

