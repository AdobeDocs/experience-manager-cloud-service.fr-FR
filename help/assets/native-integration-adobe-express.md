---
title: Intégration native d’AEM Assets avec Adobe Express
description: L’intégration native d’AEM Assets avec Adobe Express vous permet d’accéder directement aux ressources stockées dans AEM Assets à partir de l’interface utilisateur d’Adobe Express.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
source-git-commit: 8bbf9a2ba8f708a5a03d11bc0388d39b32d4c7b3
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 6%

---

# Intégration native avec Adobe Express {#native-integration-adobe-express}

AEM Assets s’intègre de manière native à Adobe Express, ce qui vous permet d’accéder directement aux ressources stockées dans AEM Assets depuis l’interface utilisateur d’Adobe Express. Vous pouvez placer du contenu géré dans AEM Assets dans la zone de travail d’Express, puis enregistrer du contenu nouveau ou modifié dans un référentiel AEM Assets. L’intégration offre les avantages clés suivants :

* Réutilisation accrue du contenu en modifiant et en enregistrant de nouvelles ressources dans AEM.

* Réduction du temps et des efforts généraux pour créer de nouvelles ressources ou créer de nouvelles versions des ressources existantes.

## Conditions préalables {#prerequisites}

Droits d’accès à Adobe Express et à au moins un environnement dans AEM Assets. L’environnement peut être l’un des référentiels dans Assets as a Cloud Service ou Assets Essentials.


## Utilisation d’AEM Assets dans l’éditeur d’Adobes Express {#use-aem-assets-in-express}

Effectuez les étapes suivantes pour commencer à utiliser AEM Assets dans l’éditeur d’Adobe Express :

1. Ouvrez l’application web d’Adobe Express.

1. Ouvrez un nouveau canevas vierge en chargeant un nouveau modèle ou projet ou en créant une ressource.

1. Cliquez sur **[!UICONTROL Ressources]** disponible dans le volet de navigation de gauche. Adobe Express affiche la liste des référentiels auxquels vous avez droit, ainsi que la liste des ressources et des dossiers disponibles au niveau racine.

1. Parcourez ou recherchez des ressources dans votre référentiel pour les faire glisser sur la zone de travail. Vous pouvez filtrer les ressources à l’aide de divers filtres disponibles, tels que le type de fichier, le type MIME et les dimensions.

   ![Inclusion de ressources à partir du module complémentaire Assets.](assets/adobe-express-native-integration.png)


## Enregistrement des projets d’Adobe Express dans AEM Assets {#save-express-projects-in-assets}

Après avoir incorporé les modifications appropriées dans la zone de travail express, vous pouvez les enregistrer dans le référentiel AEM Assets.

1. Cliquez sur **[!UICONTROL Partager]** pour ouvrir le **[!UICONTROL Partager]** boîte de dialogue.

   ![Enregistrement des ressources dans AEM](assets/adobe-express-share.png)

1. Sélectionner **[!UICONTROL AEM Assets]** de la **[!UICONTROL Stockage]** dans le volet de droite. Adobe Express affiche la boîte de dialogue de chargement.
1. Spécifiez le nom et le format de la ressource. Vous pouvez enregistrer le contenu du canevas au format PNG ou JPEG.

1. Cliquez sur l’icône de dossier située en regard de la propriété **[!UICONTROL Emplacement]** , accédez à l’emplacement où vous devez enregistrer la ressource, puis cliquez sur **[!UICONTROL Sélectionner]**. Le nom du dossier s’affiche dans la variable **[!UICONTROL Emplacement]** champ .

   ![Enregistrement des ressources dans AEM](assets/adobe-express-upload.png)

1. Facultatif : vous pouvez ajouter des métadonnées de campagne pour votre téléchargement à l’aide de la variable **[!UICONTROL Nom du projet ou de la campagne]** champ . Vous pouvez utiliser un nom existant ou en créer un nouveau. Vous pouvez définir plusieurs noms de projet ou de campagne pour votre téléchargement. Lorsque vous saisissez un nom, cliquez ailleurs dans la boîte de dialogue ou appuyez sur la touche `,` (Virgule) pour enregistrer le nom.

   En règle générale, Adobe recommande de spécifier des valeurs dans le reste des champs et de créer une expérience de recherche améliorée pour vos ressources chargées.
1. De même, définissez les valeurs de la variable **[!UICONTROL Mots-clés]** et **[!UICONTROL Canaux]** des champs.

1. Cliquez sur **[!UICONTROL Télécharger]** pour charger la ressource dans AEM Assets.




## Limites {#limitations}

Certains utilisateurs qui ont accès à plusieurs référentiels Assets ont rencontré un bogue connu lors de l’enregistrement d’un document avec des ressources de plusieurs référentiels.
