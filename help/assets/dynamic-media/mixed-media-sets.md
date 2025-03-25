---
title: Visionneuses de médias mixtes
description: Découvrez comment utiliser des visionneuses de médias mixtes dans Dynamic Media.
contentOwner: Rick Brough
feature: Mixed Media Sets
role: User
exl-id: 7ccde741-38d2-44c9-9378-f2721384aab7
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '1507'
ht-degree: 97%

---

# Visionneuses de médias mixtes{#mixed-media-sets}

Une visionneuse de médias mixtes permet d’offrir un mélange d’images, de visionneuses d’images, de visionneuses à 360° et de vidéos dans une même présentation.

Les visionneuses de médias mixtes sont désignées par une bannière contenant les mots **[!UICONTROL MixedMediaSet]**. En outre, si la visionneuse de médias mixtes est publiée, la date de publication, indiquée par l’icône représentant la **[!UICONTROL Terre]**, figure sur la bannière avec la date de dernière modification, indiquée par l’icône représentant un **[!UICONTROL crayon]**.

![chlimage_1-137](assets/chlimage_1-348.png)

>[!NOTE]
>
>Pour plus d’informations sur l’interface utilisateur d’Assets, voir [Gestion des ressources avec l’interface utilisateur tactile](/help/assets/manage-digital-assets.md).

## Démarrage rapide : Visionneuses de médias mixtes {#quick-start-mixed-media-sets}

Pour démarrer rapidement, procédez comme suit :

1. [Chargez vos ressources](#uploading-assets).

   Commencez par charger les images et les vidéos pour les visionneuses de médias mixtes. Le cas échéant, créez les [Visionneuses d’images](/help/assets/dynamic-media/image-sets.md) et [Visionneuses à 360°](/help/assets/dynamic-media/spin-sets.md). Comme les utilisateurs peuvent zoomer sur les images dans la visionneuse de médias mixtes, assurez-vous de tenir compte du zoom lorsque vous sélectionnez des images. Assurez-vous que les images font au moins 2 000 pixels dans leur plus grande dimension.

   Voir [Dynamic Media - Formats d’image raster pris en charge](/help/assets/file-format-support.md#image-support-dynamic-media) pour obtenir une liste des formats pris en charge par les ensembles de supports variés.

1. [Créez des ensembles de supports variés](#creating-mixed-media-sets).

   Pour créer un jeu de médias mixtes, dans la page Ressources, accédez à **[!UICONTROL Créer]** > **[!UICONTROL Visionneuse de supports variés]**. Attribuez ensuite un nom au jeu, sélectionnez des ressources et choisissez l’ordre dans lequel doivent apparaître les images.

   Voir [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).

1. Configurez des [paramètres prédéfinis de visionneuse de médias mixtes](/help/assets/dynamic-media/managing-viewer-presets.md), suivant les besoins.

   Les administrateurs peuvent créer ou modifier les paramètres prédéfinis de visionneuse de médias mixtes. Pour afficher votre visionneuse de médias mixtes avec un paramètre prédéfini, sélectionnez la visionneuse puis, dans le menu contextuel du rail gauche, sélectionnez **[!UICONTROL Visionneuses]**.

   Pour créer ou modifier des paramètres prédéfinis de visionneuse, accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis de visionneuse]**.

   Voir [Ajout et modification des paramètres prédéfinis de visionneuse](/help/assets/dynamic-media/managing-viewer-presets.md).

1. [Prévisualisez une visionneuse de médias mixtes](#previewing-mixed-media-sets).

   Sélectionnez la visionneuse de médias mixtes pour pouvoir la prévisualiser. Pour examiner votre jeu de médias mixtes dans la visionneuse sélectionnée, cliquez sur les icônes de miniature. Vous pouvez choisir différentes visionneuses dans le menu **[!UICONTROL Visionneuses]** disponible dans le menu déroulant du rail gauche.

1. [Publiez une visionneuse de médias mixtes](#publishing-mixed-media-sets).

   La publication d’une visionneuse de médias mixtes active la chaîne URL et d’incorporation. Vous devez, en outre, [publier le paramètre prédéfini de la visionneuse](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets).

1. [Liez des URL à l’application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) ou [incorporez la vidéo ou la visionneuse d’images](/help/assets/dynamic-media/embed-code.md).

   Adobe Experience Manager Assets crée des appels URL pour les visionneuses de médias mixtes et les active une fois que vous avez publié les visionneuses. Vous pouvez copier ces URL lorsque vous prévisualisez les ressources. Vous pouvez également les incorporer à votre site web.

   Sélectionnez la visionneuse de médias mixtes puis, dans le menu déroulant du rail gauche, sélectionnez **[!UICONTROL Visionneuses]**.

   Voir [Liaison d’une visionneuse de médias mixtes à une page web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) et [Intégration de la vidéo ou de la visionneuse d’images](/help/assets/dynamic-media/embed-code.md).

Si nécessaire, vous pouvez modifier les [Visionneuses de médias mixtes](#editing-mixed-media-sets). Vous pouvez, en outre, afficher et modifier les [propriétés de la visionneuse de médias mixtes](/help/assets/manage-digital-assets.md#editing-properties).

>[!NOTE]
>
>Si vous rencontrez des problèmes lors de la création des jeux, reportez-vous à la section [Dépanner Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md).

## Charger des ressources {#uploading-assets}

Commencez par charger les images et les vidéos pour les visionneuses de médias mixtes. N’oubliez pas que les utilisateurs peuvent effectuer un zoom sur les images dans la visionneuse de médias mixtes. Ainsi, choisissez les images en gardant à l’esprit cette fonction de zoom. Assurez-vous que les images font au moins 2 000 pixels dans leur plus grande dimension.

Si vous souhaitez ajouter des visionneuses à 360° ou des visionneuses d’images à la visionneuse de médias mixtes, créez-les aussi.

Voir [Dynamic Media - Formats d’image raster pris en charge](/help/assets/file-format-support.md#image-support-dynamic-media) pour obtenir une liste des formats pris en charge par les ensembles de supports variés.

## Créez une visionneuse de médias mixtes {#creating-mixed-media-sets}

Vous pouvez ajouter des images, des visionneuses d’images, des visionneuses à 360° et des vidéos à votre visionneuse de médias mixtes. Assurez-vous que les fichiers, visionneuses d’images et visionneuses à 360° sont prêts pour la publication avant de les ajouter à la visionneuse de médias mixtes.

Lorsque vous ajoutez des ressources à votre visionneuse, elles sont automatiquement ajoutées dans l’ordre alphanumérique. Vous pouvez réorganiser ou trier manuellement les ressources après les avoir ajoutées.

**Pour créer des jeux de médias mixtes :**

1. Dans Ressources, accédez à l’emplacement où vous souhaitez créer un jeu de médias mixtes, cliquez sur **[!UICONTROL Créer]**, puis sélectionnez **[!UICONTROL Jeu de médias mixtes]**. Vous pouvez également la créer depuis un dossier qui contient les ressources. L’éditeur de visionneuse de médias mixtes s’affiche.

   ![chlimage_1-138](assets/chlimage_1-349.png)

1. Dans le **[!UICONTROL Titre]** de la visionneuse de médias mixtes, saisissez un nom pour la visionneuse. Le nom apparaît dans la bannière de la visionneuse de supports variés. Vous pouvez aussi saisir une description.

   ![chlimage_1-139](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Lors de la création de la visionneuse de médias mixtes, vous pouvez modifier la miniature de la visionneuse ou permettre à Experience Manager de sélectionner la miniature automatiquement en fonction des ressources de la visionneuse de médias mixtes. Pour sélectionner une miniature, sélectionnez **[!UICONTROL Modifier la miniature]** et sélectionnez une image (vous pouvez également accéder à d’autres dossiers pour trouver des images). Si vous avez sélectionné une miniature, puis décidé que vous souhaitez qu’Experience Manager en génère une depuis la visionneuse de médias mixtes, sélectionnez **[!UICONTROL Basculer vers les miniatures automatiques]**.

1. Pour sélectionner les ressources à inclure dans votre jeu de médias mixtes, sélectionnez le sélecteur de ressources. Sélectionnez-les, puis sélectionnez **[!UICONTROL Sélectionner]**.

   Le sélecteur de ressources vous permet de rechercher des ressources en saisissant un mot-clé, puis en sélectionnant **[!UICONTROL Retour]**. Vous pouvez également appliquer des filtres pour affiner vos résultats de recherche. Vous pouvez filtrer par chemin, collection, type de fichier et balise. Sélectionnez le filtre, puis sélectionnez l’icône **[!UICONTROL Filtre]** de la barre d’outils. Modifiez l’affichage en sélectionnant l’icône **[!UICONTROL Vue]** et en choisissant ensuite la vue **[!UICONTROL Liste]**, **[!UICONTROL Colonnes]** ou **[!UICONTROL Carte]**.

   Voir [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).

   ![chlimage_1-140](assets/chlimage_1-351.png)

1. Réorganisez les ressources en les faisant glisser vers le haut ou le bas de la liste (sélectionnez l’icône de **[!UICONTROL réorganisation]**), le cas échéant.

   ![chlimage_1-141](assets/chlimage_1-352.png)

   Si vous souhaitez ajouter une miniature, sélectionnez l’icône **+** **[!UICONTROL miniature]** située en regard de l’image et accédez à la miniature de votre choix. Lorsque vous avez terminé de sélectionner toutes les miniatures, sélectionnez **[!UICONTROL Enregistrer]**.

   >[!NOTE]
   >
   >Si vous souhaitez ajouter des ressources, sélectionnez **[!UICONTROL Ajouter une ressource]**.

1. Pour supprimer une ressource, sélectionnez la case correspondante, puis sélectionnez **[!UICONTROL Supprimer la ressource]**.
1. Pour appliquer un paramètre prédéfini aux ressources, sélectionnez **[!UICONTROL Paramètre prédéfini]** dans le coin supérieur droit, puis sélectionnez le paramètre prédéfini de votre choix.
1. Sélectionnez **[!UICONTROL Enregistrer]**. La visionneuse de médias mixtes créée apparaît dans le dossier dans lequel vous l’avez créée.

## Modification d’une visionneuse de médias mixtes {#editing-mixed-media-sets}

Vous pouvez effectuer différentes tâches de modification sur les ressources dans les visionneuses de médias mixtes, directement dans l’interface utilisateur, [comme vous le feriez dans AEM Assets](/help/assets/manage-digital-assets.md). Vous pouvez également effectuer les actions suivantes dans les visionneuses de médias mixtes :

* Ajouter des ressources à la visionneuse de médias mixtes.
* Réorganiser des ressources de la visionneuse de médias mixtes.
* Supprimer des ressources de la visionneuse de médias mixtes.
* Appliquez les paramètres d’affichage prédéfinis.
* Modifiez la miniature par défaut.

**Pour modifier une visionneuse de médias mixtes :**

1. Effectuez l’une des opérations suivantes :

   * Pointez sur une ressource de visionneuse de médias mixtes, puis sélectionnez **[!UICONTROL Modifier]** (icône crayon).
   * Pointez sur une ressource de visionneuse de médias mixtes, sélectionnez **[!UICONTROL Sélectionner]** (icône de coche), puis **[!UICONTROL Modifier]** dans la barre d’outils.

   * Sélectionnez une ressource de visionneuse de médias mixtes puis sélectionnez **[!UICONTROL Modifier]** (icône de crayon) sur la barre d’outils.

1. Dans l’éditeur de visionneuse de médias mixtes, effectuez l’une des actions suivantes :

   * Pour réorganiser les éléments : dans le panneau de gauche, sélectionnez **[!UICONTROL Ressources]** (icône image), puis faites glisser une ressource vers un nouvel emplacement.
   * Pour ajouter des ressources : dans la barre d’outils, sélectionnez **[!UICONTROL Ajouter une ressource]**. Accédez aux ressources. Pour chaque élément à ajouter, pointez sur l’image de la ressource (et non sur son nom), puis sélectionnez l’icône de coche. Dans le coin supérieur droit, sélectionnez **[!UICONTROL Sélectionner]**.

   * Pour supprimer une ressource : dans le panneau de gauche, sélectionnez **[!UICONTROL Ressources]** (icône image), puis sélectionnez la ressource. Dans la barre d’outils, sélectionnez **[!UICONTROL Supprimer l’élément]**.

   * Pour trier des ressources selon leur nom par ordre croissant ou décroissant, dans le panneau de gauche, sélectionnez **[!UICONTROL Ressources]** (icône image). À droite de l’en-tête **[!UICONTROL Ressources]**, sélectionnez les icônes lambda vers le haut ou vers le bas.

     >[!NOTE]
     >
     >* Pour supprimer une visionneuse de médias mixtes dans son ensemble, depuis n’importe quel mode d’affichage (**[!UICONTROL Carte]** ou **[!UICONTROL Colonnes]**, par exemple), accédez à la visionneuse de médias mixtes. Placez le pointeur de la souris sur la ressource, puis sélectionnez l’icône de coche pour pouvoir la sélectionner. Appuyez sur la touche **[!UICONTROL Retour arrière]** du clavier ou sélectionnez **[!UICONTROL Plus]** (points de suspension) dans la barre d’outils, puis sélectionnez **[!UICONTROL Supprimer]**.
     >
     >* Vous pouvez modifier les fichiers d’une visionneuse de médias mixtes en accédant à la visionneuse. Dans le rail de gauche, appuyez sélectionnez **[!UICONTROL Définir les membres]**, puis l’icône **[!UICONTROL Crayon]** d’une ressource individuelle pour ouvrir la fenêtre de modification.

1. Sélectionnez **[!UICONTROL Enregistrer]** lorsque vous avez terminé la modification.

   >[!NOTE]
   >
   >* Pour modifier les ressources dans une visionneuse de médias mixtes – Accédez à la visionneuse de médias mixtes. Sélectionnez la visionneuse (sans la sélectionner) afin de pouvoir l’ouvrir dans la page Aperçu de la visionneuse Experience Manager. Dans le rail de gauche, sélectionnez l’icône lambda vers le bas pour ouvrir la liste déroulante, puis sélectionnez **[!UICONTROL Définir les membres]**. Dans la page Définir des membres, passez la souris sur une ressource, puis sélectionnez **[!UICONTROL Modifier]** (icône représentant un crayon) pour ouvrir la page de modification.
   >
   >* Pour supprimer une visionneuse de médias mixtes dans son ensemble – À partir de n’importe quel mode d’affichage (Mode Carte ou Colonne, par exemple), accédez à la visionneuse de médias mixtes. Pointez sur la visionneuse, puis sélectionnez **[!UICONTROL Sélectionner]** (icône de coche). Appuyez sur la touche **[!UICONTROL Retour arrière]** de votre clavier ou sélectionnez **[!UICONTROL Plus]** (trois points de suspension), puis **[!UICONTROL Supprimer]**.

## Prévisualisez une visionneuse de médias mixtes {#previewing-mixed-media-sets}

Pour obtenir des informations sur la prévisualisation d’une visionneuse de médias mixtes, voir [Aperçu des ressources](/help/assets/dynamic-media/previewing-assets.md).

## Publiez une visionneuse de médias mixtes {#publishing-mixed-media-sets}

Pour obtenir des informations sur la publication d’une visionneuse de médias mixtes, voir [Publication de ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

>[!NOTE]
>
>Si la visionneuse de médias mixtes n’apparaît pas complètement dans le service de diffusion la première fois que vous la publiez, publiez-la une seconde fois.
