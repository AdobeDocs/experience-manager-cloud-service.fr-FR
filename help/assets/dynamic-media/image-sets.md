---
title: Visionneuses d’images
description: Découvrez comment utiliser des visionneuses d’images dans Dynamic Media.
feature: Visionneuses d’images
role: User
exl-id: 2eb71f24-73d9-4b5c-8605-923a0e3d1505
source-git-commit: 1d42305b6a597dc95bff8b34eee8279eb0e511f3
workflow-type: ht
source-wordcount: '2044'
ht-degree: 100%

---

# Visionneuses d’images {#image-sets}

Les visionneuses d’images offrent aux utilisateurs une expérience de visionnage intégrée en leur permettant d’afficher différentes vues d’un élément en cliquant sur une miniature. Les visionneuses d’images permettent de présenter différentes vues d’un élément. Elles offrent des outils de zoom afin d’examiner les images de plus près.

Les visionneuses d’images sont désignées par une bannière comportant le mot `IMAGESET`. En outre, si la visionneuse d’images est publiée, la date de publication, indiquée par l’icône **[!UICONTROL Monde]**, est sur la bannière. En outre, la dernière date de modification, indiquée par l’icône **[!UICONTROL Crayon]**, s’affiche.

![chlimage_1-133](assets/chlimage_1-339.png)

Dans une visionneuse d’images, vous pouvez également créer des échantillons en créant une visionneuse d’images et en ajoutant des miniatures.

Cette application est utile lorsque vous souhaitez afficher un élément avec une couleur, un modèle ou une finition différente. Pour créer une visionneuse d’images avec des échantillons de couleur, vous avez besoin d’une image pour chaque couleur, modèle ou finition que vous souhaitez présenter aux utilisateurs. Vous avez également besoin d’un échantillon de couleurs, de modèle ou de finition pour chaque couleur, modèle ou finition.

Par exemple, supposons que vous souhaitez présenter les images d’une casquette avec différentes couleurs de visière : rouge, vert et bleu. Dans ce cas, vous avez besoin de trois prises de vue de la même casquette. Vous avez besoin d’une prise de vue avec une visière rouge, une avec une verte et une avec une bleue. Vous avez également besoin d’un échantillon de couleurs rouge, vert et bleu. Les échantillons de couleurs servent de miniatures sur lesquelles les utilisateurs cliquent dans la visionneuse des séries d’échantillons pour voir les visières rouge, verte ou bleue.

>[!NOTE]
>
>Pour plus d’informations sur l’interface utilisateur d’Assets, voir [Gestion des ressources avec l’interface utilisateur tactile](/help/assets/manage-digital-assets.md).

## Démarrage rapide : Visionneuses d’images {#quick-start-image-sets}

Pour démarrer rapidement :

1. Facultatif. [Créez un paramètre prédéfini d’ensemble par lot](/help/assets/dynamic-media/batch-set-presets-dm.md) et appliquez-le à un nouveau dossier dans lequel vos images de visionneuse à 360° seront chargées.

   Un paramètre prédéfini d’ensemble par lot peut vous aider à automatiser la création de votre visionneuse d’images.

   >[!IMPORTANT]
   >
   >Les ensembles par lots sont créés par IPS (Image Production System) dans le cadre de l’assimilation des ressources.

1. [Chargez les images sources originales pour plusieurs vues](#uploading-assets-in-image-sets).

   Chargez les images pour vos visionneuses d’images. N’oubliez pas que les utilisateurs peuvent effectuer un zoom sur les images dans la visionneuse d’images. Par conséquent, choisissez soigneusement vos images. Assurez-vous que les images font au moins 2 000 pixels dans leur plus grande dimension. Experience Manager Assets prend en charge de nombreux formats de fichier image, mais les formats sans perte TIFF, PNG et EPS sont recommandés.

1. [Créez une visionneuse d’images](#creating-image-sets).

   Dans les visionneuses d’images, les utilisateurs cliquent sur les images miniatures dans la visionneuse d’images.

   Pour créer une visionneuse d’images dans AEM Assets, sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Visionneuses d’images]**. Ajoutez ensuite des images et cliquez sur **[!UICONTROL Enregistrer]**.

   Voir [Préparation du chargement de ressources de visionneuse d’images et Chargement des fichiers](#uploading-assets-in-image-sets).

   Voir [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).

1. Ajoutez des [paramètres prédéfinis de visionneuse d’images](/help/assets/dynamic-media/managing-viewer-presets.md), selon les besoins.

   Les administrateurs peuvent créer ou modifier les paramètres prédéfinis de visionneuse d’images. Pour afficher vos images avec un paramètre prédéfini de visionneuse, sélectionnez la visionneuse d’images, puis dans la Liste déroulante du rail gauche, sélectionnez **[!UICONTROL Visionneuses]**.

   Pour créer ou modifier des paramètres prédéfinis de visionneuse, voir **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètre prédéfini de visionneuse]**.

1. (Facultatif) [Afficher les visionneuses d’images](/help/assets/dynamic-media/image-sets.md#viewing-image-sets) créées à l’aide de paramètres prédéfinis d’ensemble par lot.
1. [Prévisualisez une visionneuse d’images](/help/assets/dynamic-media/previewing-assets.md).

   Sélectionnez la visionneuse d’images pour pouvoir la prévisualiser. Pour examiner votre visionneuse d’images dans la visionneuse sélectionnée, sélectionnez les icônes de miniature. Vous pouvez choisir parmi les différentes visionneuses dans le menu **[!UICONTROL Visionneuses]** disponible dans la liste déroulante du rail gauche.

1. [Publiez une visionneuse d’images](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

   La publication d’une visionneuse d’images active la chaîne URL et d’incorporation. En outre, vous devez [publier tous les paramètres prédéfinis de visionneuse personnalisés](/help/assets/dynamic-media/managing-viewer-presets.md) que vous avez créés. Les paramètres prédéfinis de visionneuse prêts à l’emploi sont déjà publiés.

1. [Liez des URL à l’application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) ou [incorporez la vidéo ou la visionneuse d’images](/help/assets/dynamic-media/embed-code.md).

   Experience Manager Assets crée des appels URL pour les visionneuses d’images et les active une fois que vous avez publié la visionneuse d’images. Vous pouvez copier ces URL lorsque vous prévisualisez les ressources. Vous pouvez également les incorporer à votre site web.

   Sélectionnez la visionneuse d’images, puis, dans la liste déroulante du rail de gauche, sélectionnez **[!UICONTROL Visionneuses]**.

   Voir [Liaison d’une visionneuse d’images à une page web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) et [Intégration de la visionneuse de vidéos ou d’images](/help/assets/dynamic-media/embed-code.md).

Pour modifier des visionneuses d’images, voir [Modification de visionneuses d’images](#editing-image-sets). Vous pouvez en outre afficher et modifier les [propriétés de la visionneuse d’images](/help/assets/manage-digital-assets.md#editing-properties).

Si vous rencontrez des problèmes lors de la création des visionneuses, voir Images et visionneuses dans la section [Dépannage de Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md#images-and-sets).

## Chargement de ressources pour les visionneuses d’images {#uploading-assets-in-image-sets}

Commencez par charger les ressources d’images pour les visionneuses d’images. N’oubliez pas que les utilisateurs peuvent effectuer un zoom sur les images dans la visionneuse d’images. Par conséquent, choisissez soigneusement vos images. Assurez-vous que les images font au moins 2 000 pixels dans leur plus grande dimension pour obtenir un détail de zoom optimal. Dynamic Media peut générer des images faisant jusqu’à 25 mégapixels chacune. Par exemple, vous pouvez utiliser une image de 5 000 x 5 000 mégapixels ou toute autre combinaison de taille pouvant atteindre 25 mégapixels.

Les visionneuses d’images prennent en charge de nombreux formats de fichier image, mais les formats sans perte TIFF, PNG et EPS sont recommandés.

Vous pouvez charger des images pour les visionneuses d’images comme vous le feriez pour [charger une autre ressource dans AEM Assets](/help/assets/manage-digital-assets.md#uploading-assets).

### Préparation du chargement de ressources de visionneuse d’images {#preparing-image-set-assets-for-upload}

Avant de créer une visionneuse d’images, assurez-vous que la taille et le format des images sont corrects.

Pour créer une visionneuse d’images à plusieurs vues, vous avez besoin d’images qui montrent un élément depuis différents points de vue ainsi que différents aspects du même élément. L’objectif est de mettre en avant les fonctionnalités importantes d’un élément afin que les utilisateurs aient un tableau complet de son apparence et son fonctionnement.

Comme les utilisateurs peuvent zoomer sur les images dans les visionneuses d’images, assurez-vous que la plus grande dimension des images comporte au moins 2000 pixels. Experience Manager Assets prend en charge de nombreux formats de fichier image, mais les formats sans perte TIFF, PNG et EPS sont recommandés.

>[!NOTE]
>
>Si vous utilisez des miniatures pour indiquer des échantillons de produit, procédez comme suit :
>
>Créez des vignettes ou des prises de vue différentes de la même image la présentant avec différentes couleurs, modèles et finitions. Vous avez également besoin de fichiers de miniatures qui correspondent aux différentes couleurs, modèles et finitions. Par exemple, pour présenter des miniatures avec une visionneuse d’images de la même veste en noir, marron et vert, vous avez besoin :
>
>* D’une prise de vue en noir, en marron et en vert de la même veste.
>* Une miniature de couleur noire, marron et verte.


## Créez une visionneuse d’images {#creating-image-sets}

Vous pouvez créer des visionneuses d’images par le biais de l’interface utilisateur ou par l’API.

>[!NOTE]
>
>Vous pouvez également créer des visionneuses d’images automatiquement par l’intermédiaire des [paramètres prédéfinis d’ensemble par lot](/help/assets/dynamic-media/batch-set-presets-dm.md).
>**Important** : les ensembles par lot sont créés par le système IPS (Image Production System) dans le cadre de l’ingestion des ressources.

Lorsque vous ajoutez des ressources à votre visionneuse, elles sont automatiquement ajoutées dans l’ordre alphanumérique. Vous pouvez réorganiser ou trier manuellement les ressources après les avoir ajoutées.

>[!NOTE]
>
>Les visionneuses d’images ne sont pas prises en charge pour les ressources dont le nom de fichier contient une virgule « , ».

**Pour créer une visionneuse d’images** :

1. Dans Adobe Experience Manager, sélectionnez le logo d’Experience Manager pour accéder à la console de navigation globale.
1. Appuyez sur **[!UICONTROL Navigation]** > **[!UICONTROL Ressources]**. Naviguez jusqu’à l’emplacement où vous souhaitez créer une visionneuse d’images, puis accédez à **[!UICONTROL Créer]** > **[!UICONTROL Visionneuse d’images]** pour ouvrir la page de l’éditeur de visionneuse d’images.

   Vous pouvez également la créer depuis un dossier qui contient les ressources.

   ![6_5_imagesets-createpulldown](assets/6_5_imagesets-createpulldown.png)

1. Dans le champ **[!UICONTROL Titre]** de la page de l’éditeur de visionneuse d’images, tapez un nom pour la visionneuse d’images. Le nom apparaît dans la bannière située sur la visionneuse d’images. Vous pouvez aussi saisir une description.

   ![6_5_imageset-creatingnewset](assets/6_5_imageset-creatingnewset.png)

1. Effectuez l’une des opérations suivantes :

   * Dans le coin supérieur gauche de la page de l’éditeur de visionneuse d’images, sélectionnez **[!UICONTROL Ajouter une ressource]**.

   * Au milieu de la page de l’éditeur de visionneuse d’images, sélectionnez **[!UICONTROL Appuyer pour ouvrir le sélecteur de ressources]**.
   Appuyez pour sélectionner les ressources que vous souhaitez inclure dans la visionneuse d’images. Les ressources sélectionnées sont cochées. Lorsque vous avez terminé, en haut à droite de la page, sélectionnez **[!UICONTROL Sélectionner]**.

   Le sélecteur de ressources vous permet de rechercher des ressources en saisissant un mot-clé, puis en sélectionnant **[!UICONTROL Retour]**. Vous pouvez également appliquer des filtres pour affiner vos résultats de recherche. Vous pouvez filtrer par chemin, collection, type de fichier et balise. Sélectionnez le filtre, puis sélectionnez l’icône **[!UICONTROL Filtre]** de la barre d’outils. Modifiez l’affichage en sélectionnant l’icône Affichage et en sélectionnant **[!UICONTROL Mode Colonnes]**, **[!UICONTROL Mode Carte]** ou **[!UICONTROL Mode Liste]**.

   Voir [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).

   ![6_5_imageset-addingassets](assets/6_5_imageset-addingassets.png)

1. Lorsque vous ajoutez des ressources à votre visionneuse, elles sont automatiquement ajoutées dans l’ordre alphanumérique. Vous pouvez réorganiser ou trier manuellement les ressources une fois qu’elles ont été ajoutées.

   Si nécessaire, faites glisser l’icône Réorganiser d’une ressource vers la droite du nom de fichier de la ressource pour réorganiser les images vers le haut ou le bas de la liste définie.

   ![6_5_imageset-reorderassets](assets/6_5_imageset-reorderassets.png)

   Pour changer une miniature ou un échantillon, cliquez sur l’icône **+** **miniature** en regard de l’image et naviguez jusqu’à la miniature ou l’échantillon de votre choix. Lorsque vous avez sélectionné toutes les images, cliquez sur **[!UICONTROL Enregistrer]**.

1. (En option) Effectuez l’une des actions suivantes :

   * Pour supprimer une image, sélectionnez-la et sélectionnez **[!UICONTROL Supprimer l’élément]**.

   * Pour appliquer un paramètre prédéfini, en haut à droite de la page, sélectionnez **[!UICONTROL Paramètre prédéfini]**, puis sélectionnez un paramètre prédéfini à appliquer en une seule fois à toutes les ressources.
   >[!NOTE]
   >
   >Lors de la création de la visionneuse d’images, vous pouvez modifier la miniature de la visionneuse. Vous pouvez également laisser Experience Manager sélectionner automatiquement la miniature en fonction des ressources de la visionneuse d’images. Pour sélectionner une miniature, sélectionnez **[!UICONTROL Modifier la miniature]** au-dessus du champ Titre de la page de l’Éditeur de visionneuse d’images. Sélectionnez ensuite une image (vous pouvez également accéder à d’autres dossiers pour rechercher des images). Si vous avez sélectionné une miniature, puis que vous souhaitez qu’Experience Manager génère une miniature depuis la visionneuse d’images, sélectionnez **[!UICONTROL Basculer vers]** **[!UICONTROL les miniatures automatiques]**.

1. Cliquez sur **[!UICONTROL Enregistrer]**. La nouvelle visionneuse d’images apparaît dans le dossier dans lequel vous l’avez créée.

## Affichage de visionneuses d’images {#viewing-image-sets}

Vous pouvez créer des visionneuses d’images dans l’interface utilisateur ou automatiquement à l’aide des [paramètres prédéfinis d’ensemble par lot](/help/assets/dynamic-media/batch-set-presets-dm.md).

>[!IMPORTANT]
>
>Les ensembles par lots sont créés par IPS [Image Production System] dans le cadre de l’assimilation des ressources.

Notez toutefois que les visionneuses créées à l’aide de paramètres prédéfinis d’ensemble par lot *ne s’affichent pas* dans l’interface utilisateur. Vous pouvez afficher ces visionneuses de trois manières différentes. (Ces méthodes sont disponibles même si vous avez créé les visionneuses d’images dans l’interface utilisateur.)

* Ouvrez les propriétés d’une ressource. Les propriétés indiquent les visionneuses dont la ressource sélectionnée fait partie ou auxquelles elle est référencée. Pour afficher l’ensemble de la visionneuse, sélectionnez son nom.

   ![6_5_imageset-assetproperties](assets/6_5_imageset-assetproperties.png)

* À partir de l’image membre d’une visionneuse, sélectionnez le menu **[!UICONTROL Visionneuses]** pour afficher les visionneuses dont la ressource fait partie.

   ![6_5_imageset-setspulldownmenu](assets/6_5_imageset-setspulldownmenu.png)

* À partir de la recherche, vous pouvez sélectionner **[!UICONTROL Filtre]**, développer **[!UICONTROL Dynamic Media]**, puis sélectionner **[!UICONTROL Jeux]**.

   La recherche renvoie les visionneuses correspondantes qui ont soit été créées manuellement dans l’interface utilisateur, soit automatiquement au moyen de paramètres prédéfinis d’ensemble par lot. Pour les visionneuses automatisées, la requête de recherche est effectuée à l’aide de « Commence par ». Ce critère de recherche est différent de celui d’Experience Manager qui s’appuie sur l’utilisation de « Contient ». La définition du filtre sur **[!UICONTROL Visionneuses]** constitue la seule méthode de recherche dans des visionneuses automatisées.

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Vous pouvez afficher les visionneuses par le biais de l’interface utilisateur, comme indiqué dans la section [Modification d’une visionneuse d’images](#editing-image-sets).

## Modification d’une visionneuse d’images {#editing-image-sets}

Vous pouvez effectuer diverses tâches de modification sur les visionneuses d’images, telles que :

* Ajouter des images à la visionneuse d’images.
* Réorganiser des images dans la visionneuse d’images.
* Supprimer des ressources de la visionneuse d’images.
* Appliquer des paramètres prédéfinis de visionneuse.
* Supprimer la visionneuse d’images.

**Pour modifier les visionneuses d’images :**

1. Effectuez l’une des opérations suivantes :

   * Pointez sur une ressource d’image, puis sélectionnez **[!UICONTROL Modifier]** (icône de crayon).
   * Pointez sur une ressource de visionneuse d’image, sélectionnez **[!UICONTROL Sélectionner]** (icône de coche), puis sélectionnez **[!UICONTROL Modifier]** dans la barre d’outils.
   * Appuyez sur une ressource de visionneuse d’images, puis sélectionnez **[!UICONTROL Modifier]** (icône de crayon) dans la barre d’outils.

1. Pour modifier les images d’une visionneuse d’images, procédez comme suit :

   * Pour réorganiser les ressources, faites glisser une image vers un nouvel emplacement (sélectionnez l’icône de réorganisation pour déplacer des éléments).
   * Pour trier les éléments dans l’ordre ascendant ou descendant, cliquez sur l’en-tête de colonne.
   * Pour ajouter une ressource ou mettre à jour une ressource existante, cliquez sur **[!UICONTROL Ajouter une ressource]**. Accédez à une ressource, sélectionnez-la, puis sélectionnez **[!UICONTROL Sélectionner]** en haut à droite de la page.

      >[!NOTE]
      >
      >Si vous supprimez l’image utilisée par Experience Manager pour la miniature en la remplaçant par une autre image, la ressource originale s’affiche toujours.
   * Pour supprimer une ressource, sélectionnez-la et sélectionnez **[!UICONTROL Supprimer l’élément]**.
   * Pour appliquer un paramètre prédéfini, en haut à droite de la page, sélectionnez **[!UICONTROL Paramètre prédéfini]**, puis sélectionnez un paramètre prédéfini de visionneuse.
   * Pour ajouter ou changer une miniature, sélectionnez l’icône de miniature située à droite de la ressource. Naviguez jusqu’à la nouvelle miniature ou ressource d’échantillon, sélectionnez-la, puis sélectionnez **[!UICONTROL Sélectionner]**.
   * Pour supprimer l’ensemble d’une visionneuse d’images, accédez à cette visionneuse, sélectionnez-la, puis sélectionnez **[!UICONTROL Supprimer]**.

   >[!NOTE]
   >
   >Vous pouvez modifier les images dans une visionneuse d’images. Accédez à la visionneuse et sélectionnez **[!UICONTROL Définir les membres]** dans le rail de gauche. Pour ouvrir la fenêtre de modification, sélectionnez l’icône représentant un crayon dans une ressource.

1. Appuyez sur **[!UICONTROL Enregistrer]** lorsque vous avez terminé la modification.

## Prévisualisez une visionneuse d’images {#previewing-image-sets}

Voir [Aperçu des ressources](/help/assets/dynamic-media/previewing-assets.md).

## Publication de visionneuses d’images {#publishing-image-sets}

Voir [Publication de ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).
