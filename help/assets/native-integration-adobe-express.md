---
title: Intégration native d’AEM Assets à Adobe Express
description: L’intégration native d’AEM Assets à Adobe Express vous permet d’accéder directement aux ressources stockées dans AEM Assets depuis l’interface utilisateur d’Adobe Express.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
feature: Collaboration
role: User
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 8%

---

# Intégration native à Adobe Express {#native-integration-adobe-express}

AEM Assets s’intègre de manière native à Adobe Express, ce qui vous permet d’accéder directement aux ressources stockées dans AEM Assets depuis l’interface utilisateur d’Adobe Express. Vous pouvez placer du contenu géré dans AEM Assets dans la zone de travail d’Express, puis enregistrer du contenu nouveau ou modifié dans un référentiel AEM Assets. L’intégration offre les principaux avantages suivants :

* Réutilisation accrue du contenu en modifiant et en enregistrant de nouvelles ressources dans AEM.

* Réduction du temps et des efforts nécessaires à la création de nouvelles ressources ou de nouvelles versions de ressources existantes.

## Prérequis {#prerequisites}

Autorisations d&#39;accès à Adobe Express et à au moins un environnement dans AEM Assets. L’environnement peut être n’importe lequel des référentiels d’Assets as a Cloud Service ou d’Assets Essentials.


## Utilisation d’AEM Assets dans l’éditeur Adobe Express {#use-aem-assets-in-express}

Pour commencer à utiliser AEM Assets dans l’éditeur Adobe Express, procédez comme suit :

1. Ouvrez l’application web Adobe Express.

2. Ouvrez une nouvelle zone de travail vierge en chargeant un nouveau modèle ou un nouveau projet, ou en créant une ressource.

3. Cliquez sur **[!UICONTROL Assets]** disponible dans le volet de navigation de gauche. Adobe Express affiche la liste des référentiels auxquels vous avez accès, ainsi que la liste des ressources et des dossiers disponibles au niveau racine.

4. Parcourez ou recherchez des ressources dans votre référentiel à faire glisser et à déposer sur la zone de travail. Vous pouvez filtrer les ressources à l’aide de différents filtres disponibles, tels que le type de fichier, le type MIME et les dimensions.

   >[!NOTE]
   >
   >Le filtrage par dimension ne s’applique pas aux vidéos.

   ![Inclure des ressources à partir du module complémentaire Assets](assets/adobe-express-native-integration.png)


## Enregistrement de projets Adobe Express dans AEM Assets {#save-express-projects-in-assets}

Après avoir incorporé les modifications appropriées dans la zone de travail Express, vous pouvez l’enregistrer dans le référentiel AEM Assets.

1. Cliquez sur **[!UICONTROL Partager]** pour ouvrir la boîte de dialogue **[!UICONTROL Partager]**.

   ![Enregistrement de ressources dans AEM](assets/adobe-express-share.png)

2. Dans la section Stockage du volet de droite, sélectionnez **AEM Assets**. Adobe Express affiche la boîte de dialogue de chargement.
3. Sélectionnez **Page actuelle** ou **Toutes les pages**. Spécifiez un nom et un format pour la ou les ressources à exporter. Vous pouvez exporter le contenu de la zone de travail aux formats PNG, JPEG, PDF, MP4, MP4+PNG ou MP4+JPEG. Le format s’ajuste automatiquement en fonction des ressources sur la ou les pages de la zone de travail.
Sélectionner **Page active** enregistre la ressource sur la page active dans le dossier de destination. Si vous sélectionnez **Toutes les pages** et que le format d’exportation n’est pas PDF, toutes les pages de la zone de travail sont enregistrées en tant que fichiers distincts dans un nouveau dossier de votre dossier de destination. Si le format d’exportation est PDF, toutes les pages de la zone de travail sont enregistrées en tant que fichier PDF unique dans le dossier de destination.

4. Cliquez sur l’icône de dossier sous **Dossier de destination** pour sélectionner un emplacement et enregistrer la ou les ressources.

   ![Enregistrement de ressources dans AEM](/help/assets/assets/page-selection-and-destination-folder.svg)

5. Facultatif : vous pouvez ajouter des métadonnées de campagne pour votre chargement à l’aide du champ **Nom du projet ou de la campagne**. Vous pouvez utiliser un nom existant ou en créer un nouveau. Vous pouvez définir plusieurs noms de projet ou de campagne pour votre chargement. Pour enregistrer le nom, saisissez simplement le nom et appuyez sur Entrée.
Adobe recommande, en règle générale, de spécifier des valeurs dans le reste des champs et de créer une expérience de recherche améliorée pour les ressources que vous avez chargées.

6. De même, définissez des valeurs pour les champs **[!UICONTROL Mots-clés]** et **[!UICONTROL Canaux]**.

7. Cliquez sur **[!UICONTROL Charger]** pour charger la ou les ressources dans AEM Assets.

## Limites {#limitations}

1. Pour l’importation et l’exportation, le type de fichier vidéo pris en charge est MP4.

2. Pour l’importation vidéo MP4 :

   1. La taille de fichier maximale prise en charge est de 200 Mo. Si cette limite dépasse, un message d’alerte s’affiche.
   2. La résolution maximale prise en charge est de 3 840 x 3 840 pixels.
   3. Les vidéos avec arrière-plans transparents (couche alpha) ne sont pas prises en charge.

3. Pour l’exportation de vidéos MP4 :

   1. La taille de fichier maximale prise en charge est de 200 Mo. Si cette limite est dépassée, une alerte suggère de réduire la vidéo à 200 Mo ou moins, ou de la charger manuellement dans le dossier de destination AEM Assets après l’avoir téléchargée.



