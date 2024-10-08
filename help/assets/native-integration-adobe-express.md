---
title: Intégration native d’AEM Assets avec Adobe Express
description: L’intégration native d’AEM Assets avec Adobe Express vous permet d’accéder directement aux ressources stockées dans AEM Assets à partir de l’interface utilisateur d’Adobe Express.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
feature: Collaboration
role: User
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 9%

---

# Intégration native avec Adobe Express {#native-integration-adobe-express}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

AEM Assets s’intègre de manière native à Adobe Express, ce qui vous permet d’accéder directement aux ressources stockées dans AEM Assets depuis l’interface utilisateur d’Adobe Express. Vous pouvez placer du contenu géré dans AEM Assets dans la zone de travail d’Express, puis enregistrer du contenu nouveau ou modifié dans un référentiel AEM Assets. L’intégration offre les avantages clés suivants :

* Réutilisation accrue du contenu en modifiant et en enregistrant de nouvelles ressources dans AEM.

* Réduction du temps et des efforts généraux pour créer de nouvelles ressources ou créer de nouvelles versions des ressources existantes.

## Conditions préalables {#prerequisites}

Droits d’accès à Adobe Express et à au moins un environnement dans AEM Assets. L’environnement peut être l’un des référentiels dans les Assets Essentials as a Cloud Service ou Assets.


## Utilisation d’AEM Assets dans l’éditeur d’Adobes Express {#use-aem-assets-in-express}

Effectuez les étapes suivantes pour commencer à utiliser AEM Assets dans l’éditeur d’Adobe Express :

1. Ouvrez l’application web d’Adobe Express.

2. Ouvrez un nouveau canevas vierge en chargeant un nouveau modèle ou projet ou en créant une ressource.

3. Cliquez sur **[!UICONTROL Assets]** dans le volet de navigation de gauche. Adobe Express affiche la liste des référentiels auxquels vous avez droit, ainsi que la liste des ressources et des dossiers disponibles au niveau racine.

4. Parcourez ou recherchez des ressources dans votre référentiel pour les faire glisser sur la zone de travail. Vous pouvez filtrer les ressources à l’aide de divers filtres disponibles, tels que le type de fichier, le type MIME et les dimensions.

   >[!NOTE]
   >
   >Le filtrage par dimension ne s’applique pas aux vidéos.

   ![Inclure des ressources à partir du module complémentaire Assets](assets/adobe-express-native-integration.png)


## Enregistrement des projets d’Adobe Express dans AEM Assets {#save-express-projects-in-assets}

Après avoir incorporé les modifications appropriées dans le canevas express, vous pouvez les enregistrer dans le référentiel AEM Assets.

1. Cliquez sur **[!UICONTROL Partager]** pour ouvrir la boîte de dialogue **[!UICONTROL Partager]**.

   ![Enregistrer des ressources dans AEM](assets/adobe-express-share.png)

2. Dans la section Stockage du volet de droite, sélectionnez **AEM Assets**. Adobe Express affiche la boîte de dialogue de chargement.
3. Sélectionnez **Page active** ou **Toutes les pages**. Indiquez le nom et le format des ressources à exporter. Vous pouvez exporter le contenu du canevas aux formats PNG, JPEG, PDF, MP4, MP4+PNG ou MP4+JPEG. Le format s’ajuste automatiquement en fonction des ressources sur la ou les pages de la zone de travail.
Sélectionnez **Page active** pour enregistrer la ressource sur votre page active dans votre dossier de destination. Si vous sélectionnez **Toutes les pages** et que le format d’exportation n’est pas PDF, toutes les pages de canevas sont enregistrées en tant que fichiers distincts dans un nouveau dossier de votre dossier de destination. Si le format d’exportation est PDF, toutes les pages de canevas sont enregistrées en tant que fichier de PDF unique dans le dossier de destination.

4. Cliquez sur l’icône de dossier sous **Dossier de destination** pour sélectionner un emplacement et enregistrer la ou les ressources.

   ![Enregistrer des ressources dans AEM](/help/assets/assets/page-selection-and-destination-folder.svg)

5. Facultatif : vous pouvez ajouter des métadonnées de campagne pour votre téléchargement à l’aide du champ **Projet ou nom de campagne**. Vous pouvez utiliser un nom existant ou en créer un nouveau. Vous pouvez définir plusieurs noms de projet ou de campagne pour votre téléchargement. Pour enregistrer le nom, saisissez simplement le nom et appuyez sur Entrée.
En règle générale, Adobe recommande de spécifier des valeurs dans le reste des champs et de créer une expérience de recherche améliorée pour vos ressources chargées.

6. De même, définissez des valeurs pour les champs **[!UICONTROL Mots-clés]** et **[!UICONTROL Canaux]** .

7. Cliquez sur **[!UICONTROL Télécharger]** pour télécharger la ou les ressources vers AEM Assets.

## Limites {#limitations}

1. Pour l’importation et l’exportation, le type de fichier vidéo pris en charge est MP4.

2. Pour l’importation vidéo MP4 :

   1. La taille de fichier maximale prise en charge est de 200 Mo. Si cette limite est supérieure, un message d’alerte s’affiche.
   2. La résolution maximale prise en charge est de 3 840 x 3 840 pixels.
   3. Les vidéos avec des arrière-plans transparents (canal alpha) ne sont pas prises en charge.

3. Pour l’exportation vidéo MP4 :

   1. La taille de fichier maximale prise en charge est de 200 Mo. Si cette limite est supérieure, une alerte vous suggère de réduire la vidéo à 200 Mo ou moins, ou de la télécharger manuellement vers le dossier de destination AEM Assets après l’avoir téléchargée.



