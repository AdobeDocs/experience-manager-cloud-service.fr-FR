---
title: Filigrane des ressources
description: Ajout d’un filigrane à vos ressources numériques.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7ea7af1cf784b6866f3c2484475a8072ff76be2c
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 3%

---


# Mettre vos fichiers en filigrane {#watermark-assets}

[!DNL Adobe Experience Manager Assets] vous permet d’ajouter un filigrane numérique aux images. [!DNL Assets] prend en charge l’application d’une image en tant que filigrane à d’autres fichiers image. Les filigranes peuvent aider les utilisateurs à vérifier l’authenticité et la propriété des fichiers sous copyright. Un filigrane peut également être utilisé pour indiquer un état de document tel que confidentiel, brouillon, validité, etc.

Pour configurer [!DNL Experience Manager] les fichiers de filigrane, procédez comme suit :

1. Un fichier PNG est appliqué en filigrane. Téléchargez ce fichier dans votre référentiel DAM.

1. Accédez au référentiel [!DNL Cloud Manager] Git associé à votre environnement. Validez un fichier nommé `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.json` dans leur référentiel [!DNL Cloud Manager] Git avec le contenu suivant. Pour plus d’informations, voir [comment configurer OSGi [!DNL Experience Manager] en tant que Cloud Service](/help/implementing/deploying/configuring-osgi.md).

   ```json
   {
   "watermark": "/content/dam/<path-to-watermark-image.png>",
    "width": 100
   }
   ```

1. [Créez un profil](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) de traitement pour exploiter les microservices de ressources afin d’appliquer le filigrane.

   ![Profil de traitement des ressources pour créer un filigrane](assets/watermark-processing-profile.png)

1. [Appliquez les profils de traitement à un dossier](/help/assets/asset-microservices-configure-and-use.md#use-profiles) pour créer des fichiers en filigrane.

## Conseils et restrictions {#tips-limitations-bestpractices}

* Vous pouvez utiliser une seule configuration pour mettre en filigrane tous vos fichiers. Une seule image est utilisée pour le filigrane et sa largeur est fixe.
* Vous pouvez placer le filigrane au centre sans carrelage.
* Les filigranes basés sur du texte ne sont pas pris en charge.

>[!MORELIKETHIS]
>
>* [Présentation](/help/assets/asset-microservices-overview.md)des microservices de ressources.
>* [Utilisez les microservices de ressources avec les profils](/help/assets/asset-microservices-configure-and-use.md)de traitement.

