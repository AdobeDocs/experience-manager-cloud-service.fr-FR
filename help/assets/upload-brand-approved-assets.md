---
title: Charger les ressources approuvées par la marque vers [!DNL Content Hub]
description: Découvrez comment télécharger les ressources approuvées par la marque vers Content Hub
role: User
source-git-commit: 92c4cd64503653c5d9248c2c3f6952100b03ff86
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 0%

---


# Chargement de ressources approuvées pour la marque dans Content Hub {#upload-brand-approved-assets-content-hub}

Les administrateurs peuvent ajouter des ressources à Content Hub à partir du système de fichiers local ou importer des ressources à partir de OneDrive ou de sources de données Dropbox. Toutes les ressources s’affichent au niveau supérieur dans Content Hub, quelle que soit la structure de dossiers disponible sur votre système de fichiers local ou OneDrive et les sources de données Dropbox pour améliorer les fonctionnalités de recherche.

Pour améliorer davantage la recherche de ressources, Content Hub vous permet d’effectuer les opérations suivantes :

* Définissez des informations clés relatives au chargement de vos ressources, telles que le nom de la campagne, les mots-clés, les canaux, etc.

* Générez automatiquement davantage de propriétés pour chaque ressource en cas de téléchargement réussi, telles que la taille du fichier, le format, la résolution et certaines autres propriétés.

* Utiliser l&#39;intelligence artificielle fournie par [Adobe Sensei](https://www.adobe.com/fr/sensei.html) pour appliquer automatiquement des balises pertinentes à toutes vos ressources chargées. Ces balises, bien nommées Balises intelligentes, augmentent la vitesse du contenu de vos projets en vous aidant à trouver rapidement les ressources appropriées.

Assurez-vous de ne charger que votre [ressources approuvées par la marque dans Content Hub](/help/assets/approve-assets.md).

![Chargement de ressources approuvées par la marque](assets/upload-brand-approved-assets.png)

## Conditions préalables {#prerequisites-add-assets}

[Utilisateurs consommateurs de ressources Content Hub avec des autorisations d’envoi](/help/assets/deploy-content-hub.md#onboard-content-hub-consumer-users-submission-rights) peut charger des ressources vers Content Hub.

## Ajout de ressources à Content Hub à partir du système de fichiers local {#add-assets-local-file-system}

Pour ajouter des ressources à Content Hub, procédez comme suit :

1. Cliquez sur **[!UICONTROL Ajout d’Assets]** pour afficher la variable **[!UICONTROL Ajout des ressources approuvées]** qui vous permet de créer un téléchargement.

1. Dans le **[!UICONTROL Faire glisser des fichiers ou des dossiers ici]** dans le volet de droite, vous pouvez soit faire glisser les ressources à partir du système de fichiers local, soit cliquer sur **[!UICONTROL Parcourir]** pour sélectionner manuellement les fichiers ou les dossiers disponibles sur le système de fichiers local. Cette liste des fichiers qui font partie de votre chargement est disponible sous forme de liste.


   Vous pouvez également prévisualiser les images sélectionnées à l’aide des miniatures, puis cliquer sur l’icône X pour supprimer une image particulière de la liste. L’icône X s’affiche uniquement lorsque vous placez le pointeur de la souris sur le nom ou la taille de l’image. Cliquez également sur **[!UICONTROL Tout supprimer]** pour supprimer tous les éléments de votre liste de chargement.

   Pour terminer le processus de chargement et activer le **[!UICONTROL Bouton Télécharger]**, vous devez regrouper vos ressources sous un nom de campagne.

   ![Chargement de ressources dans Content Hub](assets/upload-assets-content-hub.png)

1. Définissez le nom de votre téléchargement à l’aide de la variable **[!UICONTROL Nom de la campagne]** champ . Vous pouvez utiliser un nom existant ou en créer un nouveau. Content Hub vous fournit d’autres options lorsque vous saisissez le nom. <!--You can define multiple Campaign names for your upload. While you are typing a name, either click anywhere else within the dialog box or press the `,` (Comma) key to register the name.-->

   En règle générale, Adobe recommande de spécifier des valeurs dans le reste des champs et de créer une expérience de recherche améliorée pour vos ressources chargées.

1. De même, définissez les valeurs de la variable **[!UICONTROL Mots-clés]**, **[!UICONTROL Canaux]**, **[!UICONTROL Période]**, et **[!UICONTROL Région]** des champs. Le balisage et le regroupement des ressources par mots-clés, canaux et emplacement permet à toutes les personnes qui utilisent le contenu de votre entreprise approuvé de trouver ces ressources et de les organiser.

1. Cliquez sur **[!UICONTROL Télécharger]** pour charger des ressources dans Content Hub. [!UICONTROL Détails de la révision] la boîte de confirmation s’affiche. Cliquez sur [!UICONTROL Continuer].

1. Assets commence le chargement. Cliquez sur [!UICONTROL Nouveau téléchargement] pour redémarrer la procédure de téléchargement. Cliquez sur [!UICONTROL Terminé] pour terminer le chargement.

Les administrateurs peuvent également configurer les champs obligatoires et facultatifs qui s’affichent lors du chargement des ressources, tels que le nom de la campagne, les mots-clés, les canaux, etc. Pour plus d’informations, voir [Configuration de l’interface utilisateur de Content Hub](configure-content-hub-ui-options.md#configure-upload-options-content-hub).


## Ajout de ressources à Content Hub à partir de sources de données OneDrive ou Dropbox {#add-assets-onedrive-dropbox}

Pour ajouter des ressources à Content Hub à partir de OneDrive ou de sources de données Dropbox :

1. Cliquez sur **[!UICONTROL Ajout d’Assets]** pour afficher la variable **[!UICONTROL Ajout des ressources approuvées]** qui vous permet d’importer des ressources à partir de OneDrive ou Dropbox.

1. Cliquez sur **[!UICONTROL OneDrive]** ou **[!UICONTROL Dropbox]** pour lancer le processus d&#39;import. Content Hub vous invite à vous connecter à votre compte OneDrive ou Dropbox, puis affiche votre structure de dossiers OneDrive ou Dropbox dans le volet de gauche.

1. Cliquez sur l’icône + en regard du fichier ou du nom du dossier pour afficher l’élément dans la liste des éléments sélectionnés. Après avoir sélectionné tous les fichiers à ajouter au portail Content Hub, répétez les étapes 3 à 6 de [Ajout de ressources à Content Hub à partir du système de fichiers local](#add-assets-local-file-system) pour terminer le processus de chargement.

   ![Transfert de ressources vers Content Hub à partir de OneDrive ou de Dropbox](assets/add-assets-onedrive-dropbox.png)

Les administrateurs peuvent également configurer les champs obligatoires et facultatifs qui s’affichent lors du chargement des ressources, tels que le nom de la campagne, les mots-clés, les canaux, etc. Pour plus d’informations, voir [Configuration de l’interface utilisateur de Content Hub](configure-content-hub-ui-options.md#configure-upload-options-content-hub).

