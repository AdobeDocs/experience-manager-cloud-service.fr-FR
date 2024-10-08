---
title: Chargement des ressources approuvées par votre marque vers [!DNL Content Hub]
description: Découvrez comment télécharger les ressources approuvées par la marque vers Content Hub
role: User
exl-id: f1be7cfc-1803-4c17-bb58-947104aa883c
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 0%

---

# Chargement de ressources approuvées pour la marque dans Content Hub {#upload-brand-approved-assets-content-hub}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

[Les utilisateurs de Content Hub autorisés à ajouter des ressources](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets) peuvent ajouter des ressources à Content Hub à partir du système de fichiers local ou importer des ressources à partir de OneDrive ou de sources de données de Dropbox. Toutes les ressources s’affichent au niveau supérieur dans Content Hub, quelle que soit la structure de dossiers disponible sur votre système de fichiers local ou OneDrive et les sources de données Dropbox pour améliorer les fonctionnalités de recherche.

Les ressources marquées comme `Approved` dans Assets as a Cloud Service sont automatiquement disponibles dans Content Hub. Pour plus d’informations, voir [Approbation de ressources pour Content Hub](/help/assets/approve-assets-content-hub.md).

Pour améliorer davantage la recherche de ressources, Content Hub vous permet d’effectuer les opérations suivantes :

* Définissez des informations clés relatives au chargement de vos ressources, telles que le nom de la campagne, les mots-clés, les canaux, etc.

* Générez automatiquement davantage de propriétés pour chaque ressource en cas de téléchargement réussi, telles que la taille du fichier, le format, la résolution et certaines autres propriétés.

* Utilisez l’intelligence artificielle fournie par [Adobe Sensei](https://www.adobe.com/fr/sensei.html) pour appliquer automatiquement les balises pertinentes à toutes vos ressources chargées. Ces balises, bien nommées Balises intelligentes, augmentent la vitesse du contenu de vos projets en vous aidant à trouver rapidement les ressources appropriées.

Assurez-vous de ne charger que vos [ressources approuvées par la marque vers Content Hub](/help/assets/approve-assets.md).

![Télécharger les ressources approuvées par la marque](assets/upload-brand-approved-assets.png)

## Conditions préalables {#prerequisites-add-assets}

[Les utilisateurs de Content Hub ayant les droits d’ajouter des ressources](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets) peuvent charger des ressources vers Content Hub.

## Ajout de ressources à Content Hub à partir du système de fichiers local {#add-assets-local-file-system}

Pour ajouter des ressources à Content Hub, procédez comme suit :

1. Cliquez sur **[!UICONTROL Ajouter Assets]** pour afficher la boîte de dialogue **[!UICONTROL Ajouter vos ressources approuvées]** qui vous permet de créer un téléchargement.

1. Dans la section **[!UICONTROL Faire glisser les fichiers ou les dossiers ici]** disponible dans le volet de droite, vous pouvez soit faire glisser les ressources depuis le système de fichiers local, soit cliquer sur **[!UICONTROL Parcourir]** pour sélectionner manuellement les fichiers ou les dossiers disponibles sur le système de fichiers local. Cette liste des fichiers qui font partie de votre chargement est disponible sous forme de liste.


   Vous pouvez également prévisualiser les images sélectionnées à l’aide des miniatures, puis cliquer sur l’icône X pour supprimer une image particulière de la liste. L’icône X s’affiche uniquement lorsque vous placez le pointeur de la souris sur le nom ou la taille de l’image. Vous pouvez également cliquer sur **[!UICONTROL Tout supprimer]** pour supprimer tous les éléments de votre liste de chargement.

   Pour terminer le processus de chargement et activer le **[!UICONTROL bouton Télécharger]**, vous devez regrouper vos ressources sous un nom de campagne.

   ![Téléchargement de ressources vers Content Hub](assets/upload-assets-content-hub.png)

1. Définissez le nom de votre téléchargement à l’aide du champ **[!UICONTROL Nom de la campagne]**. Vous pouvez utiliser un nom existant ou en créer un nouveau. Content Hub vous fournit d’autres options lorsque vous saisissez le nom. <!--You can define multiple Campaign names for your upload. While you are typing a name, either click anywhere else within the dialog box or press the `,` (Comma) key to register the name.-->

   En règle générale, Adobe recommande de spécifier des valeurs dans le reste des champs et de créer une expérience de recherche améliorée pour vos ressources chargées.

1. De même, définissez des valeurs pour les champs **[!UICONTROL Mots-clés]**, **[!UICONTROL Canaux]**, **[!UICONTROL Période]** et **[!UICONTROL Région]**. Le balisage et le regroupement des ressources par mots-clés, canaux et emplacement permet à toutes les personnes qui utilisent le contenu de votre entreprise approuvé de trouver ces ressources et de les organiser.

1. Cliquez sur **[!UICONTROL Télécharger]** pour télécharger des ressources vers Content Hub. La boîte de confirmation [!UICONTROL Détails de la révision] s’affiche. Cliquez sur [!UICONTROL Continuer].

1. Assets commence le chargement. Cliquez sur [!UICONTROL Nouveau téléchargement] pour redémarrer la procédure de téléchargement. Cliquez sur [!UICONTROL Terminé] pour terminer le téléchargement.

Les administrateurs peuvent également configurer les champs obligatoires et facultatifs qui s’affichent lors du chargement des ressources, tels que le nom de la campagne, les mots-clés, les canaux, etc. Pour plus d’informations, voir [Configuration de l’interface utilisateur de Content Hub](configure-content-hub-ui-options.md#configure-upload-options-content-hub).


## Ajout de ressources à Content Hub à partir de sources de données OneDrive ou Dropbox {#add-assets-onedrive-dropbox}

Pour ajouter des ressources à Content Hub à partir de OneDrive ou de sources de données Dropbox :

1. Cliquez sur **[!UICONTROL Ajouter Assets]** pour afficher la boîte de dialogue **[!UICONTROL Ajouter vos ressources approuvées]** qui vous permet d’importer des ressources à partir de OneDrive ou de Dropbox.

1. Cliquez sur **[!UICONTROL OneDrive]** ou **[!UICONTROL Dropbox]** pour lancer le processus d’importation. Content Hub vous invite à vous connecter à votre compte OneDrive ou Dropbox, puis affiche votre structure de dossiers OneDrive ou Dropbox dans le volet de gauche.

1. Cliquez sur l’icône + en regard du fichier ou du nom du dossier pour afficher l’élément dans la liste des éléments sélectionnés. Après avoir sélectionné tous les fichiers à ajouter au portail Content Hub, répétez les étapes 3 à 6 de [Ajout de ressources à Content Hub à partir du système de fichiers local](#add-assets-local-file-system) pour terminer le processus de chargement.

   ![Téléchargement de ressources vers Content Hub à partir de OneDrive ou de Dropbox](assets/add-assets-onedrive-dropbox.png)

Les administrateurs peuvent également configurer les champs obligatoires et facultatifs qui s’affichent lors du chargement des ressources, tels que le nom de la campagne, les mots-clés, les canaux, etc. Pour plus d’informations, voir [Configuration de l’interface utilisateur de Content Hub](configure-content-hub-ui-options.md#configure-upload-options-content-hub).

## Gestion des ressources chargées à l’aide de Content Hub {#manage-assets-uploaded-using-content-hub}

[ Les utilisateurs Content Hub autorisés à ajouter des ressources](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets) peuvent [ ajouter des ressources à Content Hub](/help/assets/upload-brand-approved-assets.md) à partir d’un système de fichiers local ou importer des ressources à partir de OneDrive ou de sources de données de Dropbox. Toutes les ressources s’affichent au niveau supérieur dans Content Hub, quelle que soit la structure de dossiers disponible sur votre système de fichiers local ou OneDrive et les sources de données Dropbox pour améliorer les fonctionnalités de recherche.

L’affichage des ressources chargées à l’aide de Content Hub dépend de l’activation ou non de la [activation du bouton d’approbation automatique](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) :

* Si le bouton d’approbation automatique **[!UICONTROL est activé, les ressources que vous chargez à l’aide de Content Hub sont automatiquement disponibles.]**

* Si le bouton d’approbation **[!UICONTROL automatique]** est désactivé, les ressources que vous chargez à l’aide de Content Hub ne s’affichent pas automatiquement. Les ressources sont disponibles dans le dossier `hydrated-assets` de votre environnement as a Cloud Service Assets. Accédez au dossier et [modifiez en masse](#bulk-approve-assets-content-hub) l’état de ces ressources sur `Approved` pour que ces ressources s’affichent dans Content Hub.

![Processus d’approbation de Content Hub](/help/assets/assets/content-hub-approval.png)
