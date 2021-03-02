---
title: Visionneuses de médias mixtes
description: Découvrez comment travailler avec des visionneuses de médias mixtes dans Dynamic Media..
translation-type: tm+mt
source-git-commit: dce527d5798ef003dc499baec97b169debab445a
workflow-type: tm+mt
source-wordcount: '1464'
ht-degree: 75%

---


# Visionneuses de médias mixtes {#mixed-media-sets}

Une visionneuse de médias mixtes permet d’offrir un mélange d’images, de visionneuses d’images, de visionneuses à 360° et de vidéos dans une même présentation.

Les visionneuses de médias mixtes sont désignées par une bannière contenant les mots **[!UICONTROL Visionneuse de médias mixtes]**. En outre, si la visionneuse de médias mixtes est publiée, la date de publication, indiquée par l’icône représentant la **[!UICONTROL Terre]**, figure sur la bannière avec la date de dernière modification, indiquée par l’icône représentant un **[!UICONTROL crayon]**.

![chlimage_1-137](assets/chlimage_1-348.png)

>[!NOTE]
>
>Pour plus d’informations sur l’interface utilisateur d’Assets, voir [Gestion des ressources avec l’interface utilisateur tactile](/help/assets/manage-digital-assets.md).

## Démarrage rapide : Visionneuses de médias mixtes {#quick-start-mixed-media-sets}

Pour démarrer rapidement, procédez comme suit :

1. [Chargez vos ressources](#uploading-assets).

   Commencez par charger les images et les vidéos pour les visionneuses de médias mixtes. Le cas échéant, créez les [Visionneuses d’images](/help/assets/dynamic-media/image-sets.md) et [Visionneuses à 360°](/help/assets/dynamic-media/spin-sets.md). Etant donné que les utilisateurs peuvent effectuer un zoom sur les images de la visionneuse de supports variés, veillez à tenir compte de la fonction de zoom lorsque vous choisissez des images. Assurez-vous que les images font au moins 2 000 pixels dans leur dimension la plus grande.

1. [Créez une visionneuse de médias mixtes.](#creating-mixed-media-sets)

   Pour créer une visionneuse de médias mixtes, dans la page Ressources, sélectionnez **[!UICONTROL Créer > Visionneuse de médias mixtes]**. Attribuez ensuite un nom à la visionneuse, sélectionnez des ressources et choisissez l’ordre dans lequel doivent apparaître les images.

   Voir [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).

1. Configurez des [paramètres prédéfinis de visionneuse de médias mixtes](/help/assets/dynamic-media/managing-viewer-presets.md), suivant les besoins.

   Les administrateurs peuvent créer ou modifier les paramètres prédéfinis de visionneuse de médias mixtes. Pour afficher votre visionneuse de médias mixtes avec un paramètre prédéfini, sélectionnez la visionneuse puis, dans le menu contextuel du rail gauche, sélectionnez **[!UICONTROL Visionneuses]**.

   Pour créer ou modifier des paramètres prédéfinis de visionneuse, voir **[!UICONTROL Outils > Ressources > Paramètres prédéfinis de la visionneuse]**.

   Voir [Ajout et modification de paramètres prédéfinis de la visionneuse](/help/assets/dynamic-media/managing-viewer-presets.md).

1. [Prévisualisez une visionneuse de médias mixtes.](#previewing-mixed-media-sets)

   Sélectionnez la visionneuse de médias mixtes pour pouvoir la prévisualiser. Pour examiner votre visionneuse de supports variés dans la visionneuse sélectionnée, cliquez sur les icônes de miniature. Vous pouvez choisir différentes visionneuses dans le menu **[!UICONTROL Visionneuses]** disponible dans le menu déroulant du rail gauche.

1. [Publiez une visionneuse de médias mixtes.](#publishing-mixed-media-sets)

   La publication d’une visionneuse de médias mixtes active la chaîne URL et d’incorporation. Vous devez, en outre, [publier le paramètre prédéfini de la visionneuse](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets).

1. [Liez des URL à l’application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) ou [incorporez la vidéo ou la visionneuse d’images](/help/assets/dynamic-media/embed-code.md).

   Adobe Experience Manager Assets crée des appels d’URL pour les visionneuses de supports variés et les active après la publication des visionneuses de supports mixtes. Vous pouvez copier ces URL lorsque vous prévisualisez les ressources. Vous pouvez également les incorporer à votre site web.

   Sélectionnez la visionneuse de médias mixtes puis, dans le menu déroulant du rail gauche, sélectionnez **[!UICONTROL Visionneuses]**.

   Voir [Liaison d’une visionneuse de médias mixtes à une page web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) et [Incorporation de la vidéo ou de la visionneuse d’images](/help/assets/dynamic-media/embed-code.md).

Si nécessaire, vous pouvez modifier [Visionneuses de supports variés](#editing-mixed-media-sets). Vous pouvez, en outre, afficher et modifier les [propriétés de la visionneuse de médias mixtes](/help/assets/manage-digital-assets.md#editing-properties).

>[!NOTE]
>
>Si vous rencontrez des problèmes lors de la création des visionneuses, reportez-vous à la section [Dépannage de Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md).

## Chargement des ressources {#uploading-assets}

Commencez par charger les images et les vidéos pour les visionneuses de médias mixtes. N’oubliez pas que les utilisateurs peuvent effectuer un zoom sur les images dans la visionneuse de supports variés. Par conséquent, choisissez les images dont vous tenez compte de cette fonction de zoom. Assurez-vous que les images font au moins 2 000 pixels dans leur dimension la plus grande.

En outre, si vous souhaitez ajouter des visionneuses à 360° ou des visionneuses d’images à la visionneuse de supports mixtes, créez-les également.

## Création d’une visionneuse de médias mixtes {#creating-mixed-media-sets}

Vous pouvez ajouter des images, des visionneuses d’images, des visionneuses à 360° et des vidéos à votre visionneuse de médias mixtes. Assurez-vous que les fichiers, visionneuses d’images et visionneuses à 360° sont prêts pour la publication avant de les ajouter à la visionneuse de médias mixtes.

Lorsque vous ajoutez des ressources à votre visionneuse, elles sont automatiquement ajoutées dans l’ordre alphanumérique. Vous pouvez réorganiser ou trier manuellement les fichiers après leur ajout.

**Création d’une visionneuse de médias mixtes**

1. Dans Assets, accédez à l’emplacement où vous souhaitez créer une visionneuse de médias mixtes, cliquez sur **[!UICONTROL Créer]**, puis sélectionnez **[!UICONTROL Visionneuse de médias mixtes]**. Vous pouvez également la créer depuis un dossier qui contient les ressources. L’éditeur de visionneuse de médias mixtes s’affiche.

   ![chlimage_1-138](assets/chlimage_1-349.png)

1. Dans le **[!UICONTROL Titre]** de la visionneuse de médias mixtes, saisissez un nom pour la visionneuse. Le nom apparaît dans la bannière située sur la visionneuse de médias mixtes. Vous pouvez aussi saisir une description.

   ![chlimage_1-139](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Lors de la création de la visionneuse de supports mixtes, vous pouvez modifier la miniature de la visionneuse de supports mixtes ou autoriser le Experience Manager à sélectionner automatiquement la miniature en fonction des fichiers de la visionneuse de supports mixtes. Pour sélectionner une miniature, cliquez sur **[!UICONTROL Modifier la miniature]** et sélectionnez une image (vous pouvez également accéder à d’autres dossiers pour trouver des images). Si vous avez sélectionné une miniature, décidez que vous souhaitez que le Experience Manager en génère une à partir de la visionneuse de supports mixtes, sélectionnez **[!UICONTROL Passer à la miniature automatique]**.

1. Pour sélectionner les fichiers à inclure dans votre visionneuse de supports variés, appuyez sur le sélecteur de fichiers. Sélectionnez-les, puis cliquez sur **[!UICONTROL Sélectionner]**.

   Le sélecteur de ressources vous permet de rechercher des ressources en saisissant un mot-clé, puis en appuyant sur **[!UICONTROL Retour]**. Vous pouvez également appliquer des filtres pour affiner vos résultats de recherche. Vous pouvez filtrer par chemin, collection, type de fichier et balise. Sélectionnez le filtre, puis appuyez sur l’icône **[!UICONTROL Filtre]** dans la barre d’outils. Modifiez l’affichage en sélectionnant l’icône **[!UICONTROL Afficher]** et en choisissant ensuite le mode **[!UICONTROL Liste]**, **[!UICONTROL Colonnes]** ou **[!UICONTROL Carte]**.

   Voir [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).

   ![chlimage_1-140](assets/chlimage_1-351.png)

1. Réorganisez les ressources en les faisant glisser vers le haut ou vers le bas de la liste (vous devez sélectionner l&#39;icône **[!UICONTROL Réorganiser]**), si nécessaire.

   ![chlimage_1-141](assets/chlimage_1-352.png)

   Si vous souhaitez ajouter une miniature, cliquez sur l’icône **+** **[!UICONTROL miniature]** située en regard de l’image et accédez à la miniature de votre choix. Lorsque vous avez terminé de sélectionner toutes les miniatures, cliquez sur **[!UICONTROL Enregistrer]**.

   >[!NOTE]
   >
   >Si vous souhaitez ajouter des ressources, appuyez sur **[!UICONTROL Ajouter une ressource]**.

1. Pour supprimer une ressource, cochez la case correspondante, puis appuyez sur **[!UICONTROL Supprimer l’élément]**.
1. Pour appliquer un paramètre prédéfini aux ressources, appuyez sur **[!UICONTROL Paramètre prédéfini]** dans le coin supérieur droit, puis sélectionnez le paramètre prédéfini de votre choix.
1. Cliquez sur **[!UICONTROL Enregistrer]**. La visionneuse de médias mixtes nouvellement créée apparaît dans le dossier dans lequel vous l’avez créée.

## Modification d’une visionneuse de médias mixtes  {#editing-mixed-media-sets}

Vous pouvez effectuer différentes tâches de modification des fichiers dans les visionneuses de supports variés directement dans l’interface utilisateur [comme vous le feriez pour tout fichier dans Assets](/help/assets/manage-digital-assets.md). Vous pouvez également effectuer les actions suivantes dans les visionneuses de médias mixtes :

* Ajouter des ressources à la visionneuse de médias mixtes.
* Réorganiser les fichiers dans la visionneuse de supports variés.
* Supprimer des ressources de la visionneuse de médias mixtes.
* Appliquer des paramètres prédéfinis de visionneuse.
* Modifier la vignette par défaut.

**Modification d’une visionneuse de médias mixtes**

1. Effectuez l’une des opérations suivantes :

   * Pointez sur une ressource de visionneuse de médias mixtes, puis appuyez sur **[!UICONTROL Modifier]** (icône crayon).
   * Pointez sur une ressource de visionneuse de médias mixtes, appuyez sur **[!UICONTROL Sélectionner]** (icône de coche), puis sur **[!UICONTROL Modifier]** dans la barre d’outils.

   * Appuyez sur une ressource de visionneuse de médias mixtes, puis sur **[!UICONTROL Modifier]** (icône crayon) dans la barre d’outils.

1. Dans l’éditeur de visionneuse de médias mixtes, effectuez l’une des actions suivantes :

   * Pour réorganiser les éléments : dans le panneau de gauche, appuyez sur **[!UICONTROL Ressources]** (icône image), puis faites glisser une ressource vers un nouvel emplacement.
   * Pour ajouter des ressources : dans la barre d’outils, appuyez sur **[!UICONTROL Ajouter une ressource]**. Accédez aux ressources. Pour chaque élément à ajouter, pointez sur l’image de la ressource (et non sur son nom), puis appuyez sur l’icône de coche. Dans le coin supérieur droit, appuyez sur **[!UICONTROL Sélectionner]**.

   * Pour supprimer une ressource : dans le panneau de gauche, appuyez sur **[!UICONTROL Ressources]** (icône image), puis sélectionnez la ressource. Dans la barre d’outils, appuyez sur **[!UICONTROL Supprimer l’actif]**.

   * Pour trier des ressources selon leur nom par ordre croissant ou décroissant, dans le panneau de gauche, appuyez sur **[!UICONTROL Ressources]** (icône image). À droite de l’en-tête **[!UICONTROL Ressources]**, appuyez sur les icônes lambda vers le haut ou vers le bas.

      >[!NOTE]
      >
      >* Pour supprimer une visionneuse de médias mixtes dans son ensemble, depuis n’importe quel mode d’affichage (**[!UICONTROL Carte]** ou **[!UICONTROL Colonnes]**, par exemple), accédez à la visionneuse de médias mixtes. Passez la souris sur la ressource, puis appuyez sur l’icône en forme de coche pour la sélectionner. Appuyez sur la touche **[!UICONTROL Retour arrière]** du clavier ou sur **[!UICONTROL Plus]** (points de suspension) dans la barre d’outils, puis appuyez sur **[!UICONTROL Supprimer]**.
         >
         >
      * Vous pouvez modifier les fichiers d’une visionneuse de supports variés en accédant à la visionneuse. Dans le rail de gauche, appuyez sur **[!UICONTROL Définir les membres]**, puis sur l&#39;icône **[!UICONTROL Crayon]** d&#39;un fichier individuel pour ouvrir la fenêtre de modification.


1. Appuyez sur **[!UICONTROL Enregistrer]** lorsque vous avez terminé la modification.

   >[!NOTE]
   >
   >* Pour modifier les ressources dans une visionneuse de médias mixtes – Accédez à la visionneuse de médias mixtes. Appuyez sur (ne sélectionnez pas) le jeu pour l’ouvrir dans la page Prévisualisation du jeu de Experience Manager. Dans le rail de gauche, cliquez sur l’icône lambda vers le bas pour ouvrir la liste déroulante, puis appuyez sur **[!UICONTROL Définir les membres]**. Dans la page Définir les membres, placez le pointeur sur une ressource, puis appuyez sur **[!UICONTROL Modifier]** (icône crayon) pour ouvrir la page de modification.
      >
      >
   * Pour supprimer une visionneuse de médias mixtes dans son ensemble – À partir de n’importe quel mode d’affichage (Mode Carte ou Colonne, par exemple), accédez à la visionneuse de médias mixtes. Placez le pointeur de souris sur la visionneuse, puis appuyez sur **[!UICONTROL Sélectionner]** (icône de coche). Appuyez sur la touche **[!UICONTROL Retour arrière]** de votre clavier ou sur **[!UICONTROL Plus]** (trois points de suspension), puis appuyez sur **[!UICONTROL Supprimer]**.


## Aperçu d’une visionneuse de médias mixtes {#previewing-mixed-media-sets}

Pour obtenir des informations sur l’aperçu d’une visionneuse de médias mixtes, voir [Aperçu des ressources](/help/assets/dynamic-media/previewing-assets.md).

## Publication d’une visionneuse de médias mixtes  {#publishing-mixed-media-sets}

Pour obtenir des informations sur la publication d’une visionneuse de médias mixtes, voir [Publication de ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

>[!NOTE]
>
>Si la visionneuse de supports mixtes ne se retrouve pas entièrement dans le service de diffusion lors de sa première publication, publiez la visionneuse de supports mixtes une seconde fois.

