---
title: Sélecteur de ressources pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Utilisez le sélecteur de ressources pour rechercher, rechercher et récupérer les métadonnées et les rendus des ressources dans votre application.
role: Admin,User
source-git-commit: fb1350c91468f9c448e34b66dc938fa3b5a3e9a9
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 1%

---


# Chargement de fichiers et de dossiers dans le sélecteur de ressources {#upload-files-folders}

Vous pouvez charger des fichiers ou des dossiers vers le sélecteur de ressources à partir de votre système de fichiers local. Pour charger des fichiers à l’aide du système de fichiers local, vous devez généralement utiliser une fonctionnalité de chargement fournie par une application front-end micro-Sélecteur de ressources.

## Chargement de ressources à partir du système de fichiers local {#basic-upload}

Pour ajouter des ressources au sélecteur de ressources, procédez comme suit :

1. Si vous utilisez la vue de rail, sélectionnez les points de suspension, puis cliquez sur ![icône de téléchargement](assets/upload-icon.svg) **[!UICONTROL Télécharger]**. D’un autre côté, cliquez sur ![ icône de téléchargement ](assets/upload-icon.svg) **** en haut à droite en cas de vue modale. L’écran [!UICONTROL Télécharger Assets] s’affiche.

   ![Téléchargement de ressources vers le sélecteur de ressources](assets/upload-assets.png)

   De plus, dans la section **[!UICONTROL Faire glisser des fichiers ou des dossiers ici]** , vous pouvez soit faire glisser les ressources depuis le système de fichiers local, soit cliquer sur **[!UICONTROL Parcourir]** pour sélectionner manuellement les fichiers ou les dossiers disponibles sur le système de fichiers local. Cette liste des fichiers qui font partie de votre chargement est disponible sous forme de liste.

   ![Chargement de base de ressources dans le sélecteur de ressources](assets/basic-upload.png)

   Vous pouvez également prévisualiser les images sélectionnées à l’aide des miniatures, puis cliquer sur l’icône X pour supprimer une image particulière de la liste. L’icône X s’affiche uniquement lorsque vous placez le pointeur de la souris sur le nom ou la taille de l’image. Vous pouvez également cliquer sur **[!UICONTROL Tout supprimer]** pour supprimer tous les éléments de votre liste de chargement.

1. Pour terminer le processus de chargement, cliquez sur **[!UICONTROL Télécharger]**. Vos ressources chargées apparaissent. Voir [chargement de base](asset-selector-customization.md#basic-upload) pour connaître le code configurable.

## Chargement de ressources avec des métadonnées {#upload-assets-with-metadata}

Vous pouvez ajouter des métadonnées aux ressources tout en les chargeant immédiatement dans votre application. Les métadonnées comprennent divers champs tels que l’objet commercial, les détails du produit, la campagne, etc. Pour ce faire, la propriété `metadataSchema` est utilisée. Accédez à [propriétés du sélecteur de ressources](asset-selector-properties.md) pour en savoir plus sur la propriété `metadataSchema`.

Voir [chargement avec des métadonnées](#upload-with-metadata) pour connaître le fragment de code requis pour la configuration.

![Chargement de ressources avec des métadonnées](assets/upload-with-metadata.png)

1. Définissez le nom de votre téléchargement à l’aide du champ **[!UICONTROL Nom de la campagne]**. Vous pouvez utiliser un nom existant ou en créer un nouveau. Le sélecteur de ressources vous fournit d’autres options lorsque vous saisissez le nom.

   En règle générale, Adobe recommande de spécifier des valeurs dans le reste des champs et de créer une expérience de recherche améliorée pour vos ressources chargées.

1. De même, définissez des valeurs pour les champs **[!UICONTROL Mots-clés]**, **[!UICONTROL Canaux]**, **[!UICONTROL Période]** et **[!UICONTROL Région]**. Le balisage et le regroupement des ressources par mots-clés, canaux et emplacement permet à toutes les personnes qui utilisent le contenu de votre entreprise approuvé de trouver ces ressources et de les organiser.

1. Cliquez sur **[!UICONTROL Télécharger]** pour télécharger des ressources vers le sélecteur de ressources. La boîte de confirmation [!UICONTROL Détails de la révision] s’affiche. Cliquez sur [!UICONTROL Continuer].

1. Assets commence le chargement. Cliquez sur [!UICONTROL Nouveau téléchargement] pour redémarrer la procédure de téléchargement. Cliquez sur [!UICONTROL Terminé] pour terminer le téléchargement.


## Chargement personnalisé {#customize-upload}

Le sélecteur de ressources vous permet d’ajouter un formulaire de téléchargement personnalisé. Plusieurs personnalisations sont disponibles. Par exemple, la propriété [hideUploadButton](#asset-selector-properties.md) vous permet de masquer le bouton de téléchargement qui s’affiche par défaut dans l’application. Au lieu de cela, vous pouvez personnaliser le rendu en dehors de l’application MFE selon les besoins. Voir [téléchargement personnalisé](#asset-selector-customization.md#customized-upload) pour la configuration.

![Chargement personnalisé](assets/customized-upload.png)

