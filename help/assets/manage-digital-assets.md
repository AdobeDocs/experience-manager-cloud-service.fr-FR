---
title: Gestion de vos ressources numériques dans Experience Manager
description: Découvrez les différentes méthodes de gestion et de modification des ressources.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: fb0a04fac1715d8077e1e69b1dc24bda4d3a667f

---


# Manage assets {#manage-assets}

Cet article explique comment gérer et modifier des ressources dans les ressources Adobe Experience Manager (AEM). Pour gérer les fragments de contenu, reportez-vous à la section Fichiers [de fragments](content-fragments/content-fragments.md) de contenu.

## Création de dossiers {#creating-folders}

Lorsque vous organisez une collection de ressources, comme toutes les images `Nature`, vous pouvez créer des dossiers pour les conserver ensemble. Vous pouvez utiliser des dossiers pour classer et organiser vos ressources. AEM Assets ne nécessite pas de classer les ressources dans des dossiers pour mieux fonctionner.

>[!NOTE]
>
>Partager un dossier de ressources du type `sling:OrderedFolder` n’est pas pris en charge lors du partage vers Marketing Cloud. If you want to share a folder, do not select [!UICONTROL Ordered] when creating a folder.

1. Dans le dossier Ressources numériques, accédez à l’emplacement où vous souhaitez créer un dossier. Dans le menu, cliquez sur **[!UICONTROL Créer]**. Select **[!UICONTROL New Folder]**.
1. In the **[!UICONTROL Title]** field, provide a folder name. Par défaut, DAM utilise le titre que vous avez fourni comme nom du dossier. Une fois le dossier créé, vous pouvez remplacer le nom par défaut et entrer un autre nom de dossier.
1. Cliquez sur **[!UICONTROL Créer]**. Le dossier apparaît dans le dossier Ressources numériques.

Les caractères suivants (liste de ceux-ci séparés par des espaces) ne sont pas pris en charge :

* Un nom de fichier ne peut pas contenir les caractères suivants : `* / : [ \\ ] | # % { } ? &`
* Un nom de dossier de ressources ne peut pas contenir les caractères suivants : `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Upload assets {#uploading-assets}

Voir [Ajout de ressources numériques à Experience Manager](add-assets.md)pour en savoir plus.

## Aperçu des fichiers {#previewing-assets}

Pour prévisualiser un fichier, procédez comme suit.

1. Dans l’interface utilisateur Ressources, accédez à l’emplacement du fichier à prévisualiser.
1. Appuyez sur la ressource concernée pour l’ouvrir.

1. En mode Aperçu, les options de zoom sont disponibles pour les [types d’images pris en charge](/help/assets/file-format-support.md) (avec modification interactive).

   To zoom into an asset, tap/click `+` (or tap/click the magnifying glass on the asset). Pour effectuer un zoom arrière, appuyez/cliquez sur `-`. Lorsque vous effectuez un zoom avant, vous pouvez observer en détail une zone de l’image en réalisant un panoramique. La flèche de zoom réinitialisé vous ramène à la vue d’origine.

   Tap **[!UICONTROL Reset]** to reset the view to the original size.

## Modifier les propriétés {#editing-properties}

1. Accédez à l’emplacement de la ressource dont vous souhaitez modifier les métadonnées.

1. Select the asset, and tap/click **[!UICONTROL Properties]** from the toolbar to view asset properties. Vous pouvez également sélectionner l’action rapide **[!UICONTROL Propriétés]** sur la carte de la ressource.

   ![properties_quickaction](assets/properties_quickaction.png)

1. In the [!UICONTROL Properties] page, edit the metadata properties under various tabs. Par exemple, sous l’onglet **[!UICONTROL De base]**, modifiez le titre, la description et ainsi de suite.

   >[!NOTE]
   >
   >The layout of the [!UICONTROL Properties] page and the metadata properties available depend on the underlying metadata schema. To learn how to modify the layout of the [!UICONTROL Properties] page, see [Metadata Schemas](/help/assets/metadata-schemas.md).

1. Pour programmer une date/heure spécifique pour l’activation de la ressource, utilisez le sélecteur de date en regard du champ **[!UICONTROL Heure]**.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. To deactivate the asset after a particular duration, choose the deactivation date/time from the date picker beside the **[!UICONTROL Off Time]** field. La date de désactivation doit être postérieure à la date d’activation de la ressource. Après l’heure [!UICONTROL de]désactivation, une ressource et ses rendus ne sont pas disponibles via l’interface Web Ressources ou via l’API HTTP.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. Sélectionnez une ou plusieurs balises dans le champ **[!UICONTROL Balises]**. Pour ajouter une balise personnalisée, saisissez le nom de la balise dans la zone et appuyez sur la touche Entrée. La nouvelle balise est enregistrée dans AEM.

   YouTube requiert que les balises soient publiées et comportent un lien vers YouTube (si un lien approprié peut être trouvé).

   >[!NOTE]
   >
   >Pour créer des balises, vous devez disposer d’une autorisation d’écriture sur le `/content/cq:tags/default` chemin d’accès dans le référentiel CRX.

1. To view usage usage statistics for the asset, click/tap the **[!UICONTROL Insights]** tab.

   Les statistiques d’utilisation comprennent les suivantes :

   * Le nombre de fois que la ressource a été visualisée ou téléchargée.
   * Les canaux/périphériques via lesquels la ressource a été utilisée.
   * Des solutions de création où la ressource a été récemment utilisée.
   Pour plus d’informations, reportez-vous à la section [Informations sur les ressources](assets-insights.md).

1. Appuyez/cliquez sur **[!UICONTROL Enregistrer et fermer]**.

1. Accédez à l’interface utilisateur Ressources. Les propriétés de métadonnées modifiées, y compris le titre, la description et les balises, sont affichées sur la carte de ressources en mode Carte et sous les colonnes appropriées en mode Liste.

## Copie de fichiers {#copying-assets}

Lorsque vous copiez une ressource ou un dossier, l’intégralité de la ressource ou le dossier sont copiés, avec la structure du contenu. Une ressource copiée ou un dossier sont dupliqués à l’emplacement cible. La ressource stockée à l’emplacement source n’est pas modifiée.

Quelques attributs uniques à une copie spécifique d’une ressource ne sont pas reportés. Voici quelques exemples :

* ID du fichier, date et heure de création, versions et historique des versions. Some of these properties are indicated by the properties `jcr:uuid`, `jcr:created`, and `cq:name`.

* L’heure de création et les chemins référencés sont uniques pour chaque ressource et chaque rendu.

Les autres propriétés et informations de métadonnées sont conservées. Une copie partielle n’est pas créée lors de la copie d’une ressource.

1. From the Assets UI, select one or more assets, and then tap/click the **[!UICONTROL Copy]** icon from the toolbar. Vous pouvez également sélectionner l’action rapide **[!UICONTROL Copier]** ![copie_icône](assets/copy_icon.png) depuis la carte de ressources.

   >[!NOTE]
   >
   >If you use the [!UICONTROL Copy] quick action, you can only copy one asset at a time.

1. Accédez à l’emplacement où vous souhaitez copier les ressources.

   >[!NOTE]
   >
   >Si vous copiez une ressource au même endroit, AEM génère automatiquement une variante du nom. For example, if you copy an asset titled `Square`, AEM automatically generates the title for its copy as `Square1`.

1. Click the **[!UICONTROL Paste]** asset icon from the toolbar. Les ressources sont copiées à cet emplacement.

   ![chlimage_1-219](assets/chlimage_1-219.png)

   >[!NOTE]
   >
   >The **[!UICONTROL Paste]** icon is available in the toolbar until the paste operation is completed.

### Déplacer ou renommer des fichiers {#moving-or-renaming-assets}

1. Accédez à l’emplacement de la ressource à déplacer.

1. Select the asset, and tap/click the **[!UICONTROL Move]** icon ![move_icon](assets/move_icon.png) from the toolbar.

1. Dans l’Assistant de déplacement des ressources, procédez comme suit :

   * Spécifiez le nom de la ressource après l’avoir déplacée. Then tap/click **[!UICONTROL Next]** to proceed.

   * Tap/click **[!UICONTROL Cancel]** to stop the process.
   >[!NOTE]
   >
   >* Vous pouvez attribuer le même nom à la ressource si aucune autre ressource portant ce nom n’existe dans le nouvel emplacement. Cependant, vous devez utiliser un nouveau nom si vous déplacez la ressource vers un emplacement dans lequel une ressource portant le même nom existe. Si vous utilisez le même nom, le système génère automatiquement une variante du nom. Par exemple, si votre ressource porte le nom Carré, le système génère le nom Carré1 pour sa copie.
   >* Lors de l’attribution d’un nouveau nom à un fichier, aucun espace n’est autorisé dans le nom.


1. On the **[!UICONTROL Select Destination]** dialog, do one of the following:

   * Navigate to the new location for the assets, and then tap/click **[!UICONTROL Next]** to proceed.

   * Tap/click **[!UICONTROL Back]** to return to the **[!UICONTROL Rename]** screen.

1. If the assets being moved have any referencing pages, assets, or collections, the **[!UICONTROL Adjust References]** tab appears beside the **[!UICONTROL Select Destination]** tab.

   Do one of the following in the **[!UICONTROL Adjust References]** screen:

   * Specify the references to be adjusted based on the new details, and then tap/click **[!UICONTROL Move]** to proceed.

   * Dans la colonne **[!UICONTROL Ajuster]**, sélectionnez/annulez la sélection des références aux ressources.
   * Tap/click **[!UICONTROL Back]** to return to the **[!UICONTROL Select Destination]** screen.

   * Tap/click **[!UICONTROL Cancel]** to stop the move operation.
   Si vous ne mettez pas à jour les références, elles continuent à pointer vers le chemin précédent de la ressource. Si vous adaptez les références, elles sont mises à jour avec le nouveau chemin de la ressource.

### Gestion des rendus {#managing-renditions}

1. Vous pouvez ajouter ou supprimer des rendus correspondant à une ressource, à l’exception de celle d’origine. Accédez à l’emplacement de la ressource pour laquelle vous souhaitez ajouter ou supprimer des rendus.

1. Appuyez/cliquez sur la ressource pour ouvrir sa page.

   ![chlimage_1-220](assets/chlimage_1-220.png)

1. Tap/click the GlobalNav icon, and select **[!UICONTROL Renditions]** from the list.

   ![renditions_menu](assets/renditions_menu.png)

1. Dans le panneau **[!UICONTROL Rendus]**, consultez la liste des rendus générés pour la ressource.

   ![renditions_panel](assets/renditions_panel.png)

   >[!NOTE]
   >
   >Par défaut, AEM Assets n’affiche pas le rendu d’origine de la ressource en mode Aperçu. Si vous êtes administrateur, vous pouvez utiliser des incrustations pour configurer AEM Assets de manière à afficher les rendus d’origine dans ce mode.

1. Sélectionnez un rendu afin de l’afficher ou de le supprimer.

   **Suppression d’un rendu**

   Select a rendition from the **[!UICONTROL Renditions]** panel, and then tap/click the **[!UICONTROL Delete Rendition]** icon from the toolbar.

   ![delete_renditionicon](assets/delete_renditionicon.png)

   **Téléchargement d’un nouveau rendu**

   Accédez à la page des détails de la ressource, puis appuyez/cliquez sur l’icône **[!UICONTROL Ajouter le rendu]** dans la barre d’outils pour télécharger un nouveau rendu pour la ressource.

   ![chlimage_1-221](assets/chlimage_1-221.png)

   >[!NOTE]
   >
   >Si vous sélectionnez un rendu dans le panneau **[!UICONTROL Rendus]**, la barre d’outils change de contexte et affiche uniquement les actions pertinentes pour le rendu. Les options, telles que l’icône Télécharger le rendu, ne s’affichent pas. Pour afficher ces options dans la barre d’outils, accédez à la page des détails de la ressource.

   Vous pouvez configurer les dimensions du rendu à afficher dans la page de détails d’une ressource image ou vidéo. AEM Assets affiche le rendu selon les dimensions exactes ou les plus proches de celles spécifiées.

   Pour configurer les dimensions de rendu d’une image au niveau des détails de la ressource, superposez le nœud `renditionpicker` (`libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker`) et configurez la valeur de la propriété de largeur. Configurez la **[!UICONTROL taille de la propriété (Long) en Ko]** au lieu de la largeur pour personnaliser le rendu sur la page des détails de la ressource en fonction de la taille de l’image. Pour effectuer une personnalisation basée sur la taille, la propriété `preferOriginal` attribue une préférence à l’original si la taille du rendu associé est supérieure à celle de l’original.

   De même, vous pouvez personnaliser l’image de la page Annotation en superposant `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker`.

   ![chlimage_1-222](assets/chlimage_1-222.png)

   To configure rendition dimensions for a video asset, navigate to the `videopicker` node in the CRX repository at the location `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker`, overlay the node, and then edit the appropriate property.

   >[!NOTE]
   >
   >Les annotations vidéo ne sont prises en charge que sur les navigateurs qui acceptent les formats vidéo compatibles avec HTML5. Selon le navigateur, différents formats vidéo sont en outre pris en charge.

## Supprimer des ressources {#delete-assets}

Pour résoudre ou supprimer les références entrantes provenant d’autres pages, mettez à jour les références appropriées avant de supprimer une ressource.

De plus, désactivez le bouton Forcer la suppression à l’aide d’un recouvrement afin d’empêcher les utilisateurs de supprimer des ressources référencées et de conserver des liens rompus.

1. Accédez à l’emplacement des ressources que vous souhaitez supprimer.

1. Select the asset, and tap/click the **[!UICONTROL Delete]** icon from the toolbar.

   ![delete_icon](assets/delete_icon.png)

1. Dans la boîte de dialogue de confirmation, cliquez sur :

   * **[!UICONTROL Annuler]** pour arrêter l’action
   * **[!UICONTROL Supprimer]** pour confirmer l’action :

      * Si la ressource ne comporte aucune référence, elle est supprimée.
      * Si la ressource comporte des références, un message d’erreur vous informe qu’**une ou plusieurs ressources sont référencées.** Vous pouvez sélectionner **[!UICONTROL Forcer la suppression]** ou **[!UICONTROL Annuler]**.
   >[!NOTE]
   >
   >Vous avez besoin des autorisations de suppression sur le barrage/la ressource pour pouvoir supprimer une ressource. Si vous disposez uniquement d’autorisations de modification, vous pourrez seulement modifier les métadonnées de la ressource et ajouter des annotations à cette dernière. Toute suppression s’avérera impossible.

   >[!NOTE]
   >
   >Pour résoudre ou supprimer les références entrantes provenant d’autres pages, mettez à jour les références appropriées avant de supprimer une ressource.
   >
   >
   >De plus, désactivez le bouton Forcer la suppression à l’aide d’un recouvrement afin d’empêcher les utilisateurs de supprimer des ressources référencées et de conserver des liens rompus.

## Téléchargement de ressources {#download-assets}

Voir [Téléchargement de ressources à partir d’AEM](/help/assets/download-assets-from-aem.md).

## Publish assets {#publish-assets}

<!--
>[!NOTE]
>
>For more information specific to Dynamic Media, see [Publishing Dynamic Media Assets.](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)
-->

1. Accédez à l’emplacement des fichiers/dossiers que vous souhaitez publier.

1. Sélectionnez l’action rapide **[!UICONTROL Publier]** dans la carte de ressources ou sélectionnez la ressource et appuyez/cliquez sur l’icône **[!UICONTROL Publication rapide]** dans la barre d’outils.
1. Si la ressource fait référence à d’autres ressources, ses références sont répertoriées dans l’Assistant. Seules les références qui ont été modifiées ou dont la publication a été annulée depuis leur dernière publication/annulation de publication sont affichées. Choisissez les références que vous souhaitez publier.

   ![chlimage_1-225](assets/chlimage_1-225.png)

   >[!NOTE]
   >
   >Si le dossier que vous souhaitez publier comprend un sous-dossier vide, ce dernier n’est pas publié.

1. Appuyez/cliquez sur **[!UICONTROL Publier]** pour confirmer l’activation des ressources.

>[!CAUTION]
>
>Si vous publiez une ressource qui est en cours de traitement, seul le contenu original est publié. Les rendus sont absents. Vous pouvez attendre la fin du traitement avant de publier ou republier la ressource une fois le traitement terminé.

## Annulation de la publication de fichiers {#unpublishing-assets}

1. Accédez à l’emplacement de la ressource/du dossier de ressources que vous souhaitez supprimer de l’environnement de publication (annuler la publication).

1. Select the asset/folder to unpublish, and tap/click the **[!UICONTROL Manage Publication]** icon from the toolbar.

   ![manage_publication](assets/manage_publication.png)

1. Select the **[!UICONTROL Unpublish]** action from the list.

   ![unpublish_action](assets/unpublish_action.png)

1. Pour annuler la publication de la ressource à une date ultérieure, sélectionnez **[!UICONTROL Annuler la publication ultérieurement]**, puis choisissez une date d’annulation de la publication de la ressource.
1. Planifiez une date à laquelle la ressource devient indisponible dans l’environnement de publication.
1. Si la ressource fait référence à d’autres ressources, sélectionnez les références dont vous souhaitez annuler la publication. Tap/click **[!UICONTROL Unpublish]**.
1. Dans la boîte de dialogue de confirmation, appuyez/cliquez sur :

   * **[!UICONTROL Annuler]** pour arrêter l’action
   * **[!UICONTROL Annulez la publication]** pour confirmer que les fichiers sont dépubliés (ils ne sont plus disponibles dans l’environnement de publication) à la date spécifiée.
   >[!NOTE]
   >
   >Lorsque vous annulez la publication d’un fichier complexe, annulez uniquement la publication du fichier. Evitez de dépublier les références, car elles peuvent être référencées par d’autres ressources publiées.

## Closed user group {#closed-user-group}

Les groupes d’utilisateurs fermés permettent de limiter l’accès à des dossiers de ressources spécifiques publiés à partir d’AEM. Si vous créez un groupe d’utilisateurs fermé pour un fichier, l’accès au dossier (y compris aux ressources du dossier et à ses sous-dossiers) est limité aux membres ou aux groupes attribués. Pour accéder au dossier, ils doivent se connecter à l’aide de leurs informations d’identification de sécurité.

Les groupes d’utilisateurs fermés constituent un moyen supplémentaire de limiter l’accès à vos ressources. Vous pouvez également configurer une page de connexion pour le dossier.

1. Sélectionnez un dossier dans l’IU Assets, puis appuyez/cliquez sur l’icône Propriétés de la barre d’outils pour afficher la page de propriétés.
1. Sous l’onglet **[!UICONTROL Autorisations]**, ajoutez les membres ou les groupes sous **[!UICONTROL Groupe d’utilisateurs fermé]**.

   ![add_user](assets/add_user.png)

1. Pour afficher un écran de connexion lorsque les utilisateurs accèdent au dossier, sélectionnez l’option **[!UICONTROL Activer]**. Ensuite, sélectionnez le chemin de la page de connexion dans AEM et enregistrez les modifications.

   ![login_page](assets/login_page.png)

   >[!NOTE]
   >
   >Si vous ne spécifiez pas le chemin d’une page de connexion, AEM affiche la page de connexion par défaut dans l’instance de publication.

1. Publiez le dossier, puis tentez d’y accéder à partir de l’instance de publication. Un écran de connexion s’affiche.
1. Si vous êtes membre d’un groupe d’utilisateurs fermé, saisissez vos informations d’identification de sécurité. Le dossier s’affiche après qu’AEM vous a authentifié.

## Recherche de ressources {#search-assets}

La recherche de ressources est essentielle pour l’utilisation d’un système de gestion des ressources numériques, que ce soit pour une utilisation plus poussée par les créatifs, pour une gestion robuste des ressources par les utilisateurs et spécialistes du marketing ou pour l’administration par les administrateurs DAM.

Pour des recherches simples, avancées et personnalisées pour découvrir et utiliser les ressources les plus appropriées, voir [Recherche des ressources dans AEM](/help/assets/search-assets.md).

## Actions rapides {#quick-actions}

Les icônes d’action rapide sont disponibles pour une ressource à la fois. Selon le périphérique, effectuez les actions suivantes pour afficher les icônes d’action rapide :

* Appareils tactiles : appuyez longuement. Par exemple, sur un iPad, vous pouvez appuyer sur un fichier et le maintenir en mémoire afin que les actions rapides s’affichent.
* Appareils non tactiles : survolez avec le pointeur de la souris. Sur un périphérique de bureau, par exemple, la barre d’action rapide s’affiche si vous passez le pointeur sur la miniature du fichier.

## Modification des images {#editing-images}

Les outils de modification de l’interface d’AEM Assets permettent d’effectuer de petites tâches de modification sur les ressources d’image. Vous pouvez recadrer les images, les faire pivoter, les retourner et effectuer d’autres tâches de modification. Vous pouvez également ajouter des zones cliquables aux ressources.

>[!NOTE]
>
>Pour certains composants, le mode plein écran comporte des options supplémentaires disponibles.

1. Pour ouvrir une ressource en mode Modification, effectuez l’une des opérations suivantes :

   * Select the asset and then click/tap the **[!UICONTROL Edit]** icon in the toolbar.
   * Tap/click the **[!UICONTROL Edit]** icon that appears on an asset in the Card view.
   * Sur la page Ressource, appuyez/cliquez sur l’icône **[!UICONTROL Modifier]** de la barre d’outils.
   ![edit_icon](assets/edit_icon.png)

1. To crop the image, tap/click the **Crop** icon.

   ![chlimage_1-226](assets/chlimage_1-226.png)

1. Sélectionnez une option dans la liste. La zone de recadrage s’affiche sur l’image en fonction de l’option choisie. L’option **Main libre** vous permet de recadrer l’image sans restriction de format.

   ![chlimage_1-227](assets/chlimage_1-227.png)

1. Sélectionnez la zone à recadrer et redimensionnez ou repositionnez-la sur l’image.
1. Utilisez l’icône **Terminer** (coin supérieur droit) pour recadrer l’image. L’icône **Terminer** déclenche également la régénération des rendus.

   ![chlimage_1-228](assets/chlimage_1-228.png)

1. Utilisez les icônes **Annuler** et **Rétablir** en haut à droite pour rétablir l’image non recadrée ou conserver l’image recadrée, respectivement.

   ![chlimage_1-229](assets/chlimage_1-229.png)

1. Appuyez/cliquez sur l’icône Faire pivoter adéquate pour faire pivoter l’image dans le sens des aiguilles d’une montre ou dans le sens inverse des aiguilles d’une montre.

   ![chlimage_1-230](assets/chlimage_1-230.png)

1. Appuyez/cliquez sur l’icône Symétrie adéquate pour retourner l’image horizontalement ou verticalement.

   ![chlimage_1-231](assets/chlimage_1-231.png)

1. Tap/click the **Finish** icon to save the changes.

   ![chlimage_1-232](assets/chlimage_1-232.png)

>[!NOTE]
>
>La modification d’images est prise en charge pour les formats de fichiers BMP, GIF, PNG et JPEG.

<!-- You can also add image maps using the image editor. For details, see [Adding Image Maps](/help/assets/image-maps.md). -->

>[!NOTE]
>
>To edit a TXT file, set **Day CQ Link Externalizer** from Configuration Manager.

## Chronologie {#timeline}

La frise chronologique permet d’afficher différents événements d’un élément sélectionné, comme les workflows actifs pour une ressource, les commentaires/annotations, les journaux d’activité et les versions.

![Tri des entrées de chronologie pour un fichier](assets/sort_timeline.gif)*Figure : Tri des entrées de chronologie pour un fichier*

>[!NOTE]
>
>Dans la [console Collections](/help/assets/manage-collections.md#navigate-the-collections-console), la liste **[!UICONTROL Tout afficher]** contient des options permettant de n’afficher que les commentaires et les workflows. De plus, la frise chronologique ne s’affiche que pour les collections de niveau supérieur répertoriées dans la console. Elle ne s’affiche pas si vous accédez à l’intérieur des collections.

>[!NOTE]
>
>La chronologie comprend plusieurs [options spécifiques aux fragments de contenu](content-fragments/content-fragments.md).

## Annotation {#annotating}

Les annotations sont des commentaires ou des notes d’explication ajoutées aux images ou vidéos. Les annotations offrent aux marketeurs la possibilité de collaborer et de laisser des commentaires sur des ressources.

Les annotations vidéo ne sont prises en charge que sur les navigateurs qui acceptent les formats vidéo compatibles avec HTML5. Les formats vidéo pris en charge par AEM Assets dépendent du navigateur.

>[!NOTE]
>
>Pour les fragments de contenu, [les annotations sont créées dans l’éditeur de fragment](content-fragments/content-fragments.md).

1. Accédez à l’emplacement de la ressource à laquelle vous souhaitez ajouter des annotations.
1. Tap/click the **[!UICONTROL Annotate]** icon from one of the following:

   * [Actions rapides](#quick-actions)
   * Dans la barre d’outils, après avoir sélectionné la ressource   ou avoir accédé à la page de la ressource
   ![chlimage_1-233](assets/chlimage_1-233.png)

1. Ajoutez un commentaire dans la zone **[!UICONTROL Commentaire]** au bas du journal. Vous pouvez également marquer une zone de l’image et ajouter une annotation dans la boîte de dialogue **[!UICONTROL Ajouter une annotation]**.

   ![chlimage_1-234](assets/chlimage_1-234.png)

1. Pour signaler une annotation à un utilisateur, indiquez l’adresse électronique de l’utilisateur et ajoutez le commentaire. Par exemple, pour signaler une annotation à Aaron MacDonald, saisissez @aa. Des conseils à l’usage des utilisateurs correspondant s’affichent dans une liste. Sélectionnez l’adresse électronique d’Aaron dans la liste pour la marquer avec le commentaire. De même, vous pouvez marquer d’autres utilisateurs à n’importe quel emplacement de l’annotation, avant ou après celle-ci.

   >[!NOTE]
   >
   >For a non-administrator user, suggestions appear only if the user has Read permissions at */home* in Crx-de.

   ![chlimage_1-235](assets/chlimage_1-235.png)

1. Après avoir ajouté l’annotation, cliquez sur **[!UICONTROL Ajouter]** pour l’enregistrer. Une notification relative à l’annotation est envoyée à Aaron.

   ![chlimage_1-236](assets/chlimage_1-236.png)

   >[!NOTE]
   >
   >Vous pouvez ajouter plusieurs annotations avant de les enregistrer.

1. Appuyez/cliquez sur **[!UICONTROL Fermer]** pour quitter le mode Annotation.
1. To view the notification, log in to AEM Assets with Aaron MacDonald&#39;s credentials and click the **[!UICONTROL Notifications]** icon to view the notification.

   >[!NOTE]
   >
   >Vous pouvez ajouter des annotations à des ressources vidéo. Lorsque vous annotez des vidéos, le lecteur se met en pause pour vous permettre d’ajouter une annotation sur une image. For details, see [managing video assets](manage-video-assets.md).

1. Pour sélectionner une autre couleur afin de différencier les utilisateurs, cliquez/appuyez sur l’icône Profil et ensuite sur **[!UICONTROL Mes préférences]**.

   ![chlimage_1-237](assets/chlimage_1-237.png)

   Indiquez la couleur de votre choix dans la zone **[!UICONTROL Couleur d’annotation]**, puis cliquez/appuyez sur **[!UICONTROL Accepter]**.

   ![chlimage_1-238](assets/chlimage_1-238.png)

>[!NOTE]
>
>Vous pouvez également ajouter des annotations à une collection. Cependant, si une collection contient des collections enfants, vous ne pouvez ajouter des annotations/commentaires qu’à la collection parent. L’option Annoter n’est pas disponible pour les collections enfants.

### Afficher les annotations enregistrées {#viewing-saved-annotations}

1. Pour afficher les annotations enregistrées pour une ressource, accédez à l’emplacement de la ressource et ouvrez la page Ressource de la ressource.

1. Tap/click the GlobalNav icon, and choose **[!UICONTROL Timeline]** from the list.

   ![chlimage_1-239](assets/chlimage_1-239.png)

1. Dans la liste **[!UICONTROL Tout afficher]** du journal, sélectionnez **[!UICONTROL Commentaires]** pour filtrer les résultats en fonction des annotations.

   ![chlimage_1-240](assets/chlimage_1-240.png)

   Dans le panneau **[!UICONTROL Frise chronologique]**, appuyez/cliquez sur un commentaire pour afficher l’annotation correspondante sur l’image.

   ![chlimage_1-241](assets/chlimage_1-241.png)

   Pour supprimer un commentaire spécifique, appuyez/cliquez sur **[!UICONTROL Supprimer]**.

### Imprimer les annotations {#printing-annotations}

Si un fichier comporte des annotations ou a été soumis à un processus de révision, vous pouvez l’imprimer avec des annotations et l’état de révision en tant que fichier PDF pour révision hors ligne.

Vous pouvez également choisir de n’imprimer que les annotations ou l’état de révision.

Pour imprimer les annotations et l’état de révision, cliquez/appuyez sur l’icône **[!UICONTROL Imprimer]** et suivez les instructions de l’assistant. The **[!UICONTROL Print]** icon appears in the toolbar only when the asset has at least one annotation or review status assigned to it.

1. Ouvrez la page d’aperçu d’une ressource à partir de l’interface utilisateur d’Assets.
1. Utilisez l’une des méthodes suivantes :

   * Pour imprimer toutes les annotations et l’état de révision, ignorez l’étape 3 et passez directement à l’étape 4.
   * To print specific annotations and review status, open the [timeline](/help/assets/manage-digital-assets.md#timeline) and then go to step 3.

1. Pour imprimer des annotations spécifiques, sélectionnez-les dans la frise chronologique.

   ![chlimage_1-242](assets/chlimage_1-242.png)

   Pour n’imprimer que l’état de révision, sélectionnez-le dans la frise chronologique.

   ![chlimage_1-243](assets/chlimage_1-243.png)

1. Appuyez/cliquez sur l’icône **[!UICONTROL Imprimer]** dans la barre d’outils.

   ![chlimage_1-244](assets/chlimage_1-244.png)

1. Dans la boîte de dialogue Imprimer, sélectionnez la position dans laquelle vous souhaitez afficher les annotations/l’état de révision dans le fichier PDF. For example, if you want the annotations/status to be printed at the top-right of the page that contains the printed image, use the **Top-Left** setting. Ce paramètre est sélectionné par défaut.

   ![chlimage_1-245](assets/chlimage_1-245.png)

   Vous pouvez choisir d’autres paramètres en fonction de l’emplacement où vous souhaitez que les annotations/l’état apparaissent dans le PDF imprimé. Si vous souhaitez que les annotations/états s’affichent dans une page distincte du fichier imprimé, choisissez **[!UICONTROL Page suivante]**.

   >[!NOTE]
   >
   >Il se peut que les annotations trop longues ne s’affichent pas correctement dans le fichier PDF. Pour un rendu optimal, Adobe recommande de limiter la taille des annotations à 50 mots.

1. Appuyez/cliquez sur **[!UICONTROL Imprimer]**. Selon l’option choisie à l’étape 2, le fichier PDF généré affiche les annotations/l’état à l’emplacement spécifié. Par exemple, si vous choisissez d’imprimer les annotations et l’état de révision à l’aide du paramètre **En haut à gauche**, la sortie générée ressemble au fichier PDF illustré ici.

   ![chlimage_1-246](assets/chlimage_1-246.png)

1. Téléchargez ou imprimez le fichier PDF à l’aide des options situées dans le coin supérieur droit.

   ![chlimage_1-247](assets/chlimage_1-247.png)

   Pour modifier l’aspect du fichier PDF généré (la couleur, la taille et le style de la police, la couleur d’arrière-plan des commentaires et des états, par exemple), ouvrez la **[!UICONTROL configuration du PDF d’annotation]** dans Configuration Manager et modifiez ensuite les options souhaitées. Par exemple, pour modifier la couleur d’affichage de l’état approuvé, modifiez le code couleur dans le champ correspondant. Pour plus d’informations sur la modification de la couleur de police des annotations, voir [Annotations](/help/assets/manage-digital-assets.md#annotating).

   ![chlimage_1-248](assets/chlimage_1-248.png)

   Revenez au fichier PDF généré et actualisez-le. Le fichier PDF actualisé affiche désormais les modifications que vous avez effectuées.

## Asset versioning {#asset-versioning}

La gestion de versions permet de créer un instantané de ressources numériques à un moment donné. De plus, elle aide à restaurer ultérieurement des ressources dans leur état précédent. Par exemple, si vous souhaitez annuler une modification apportée à une ressource, restaurez la version non modifiée de la ressource.

Voici quelques scénarios de création de versions :

* Vous modifiez une image dans une autre application et la téléchargez vers AEM Assets. Une version de l’image est créée afin que votre image d’origine ne soit pas remplacée.
* Vous modifiez les métadonnées d’une ressource.
* Utilisez l’application de bureau AEM pour extraire un fichier existant et enregistrer vos modifications. Une nouvelle version est créée chaque fois que la ressource est enregistrée.

Vous pouvez également activer la création de versions automatique à l’aide d’un workflow. Lorsque vous créez une version pour un fichier, les métadonnées et les rendus sont enregistrés avec la version. Les rendus sont d’autres affichages d’une même image (un rendu PNG d’un fichier JPEG téléchargé, par exemple).

La création de versions permet d’effectuer les opérations suivantes :

* créer une version d’une ressource ;
* afficher la révision actuelle d’une ressource ;
* restaurer une version précédente de la ressource.

1. Accédez à l’emplacement de la ressource pour laquelle vous souhaitez créer une version et appuyez/cliquez dessus pour afficher la page Ressource correspondante.

1. Appuyez/cliquez sur l’icône de navigation globale, puis sélectionnez **[!UICONTROL Frise chronologique]** dans le menu.

   ![chronologie](assets/timeline.png)

1. Tap/click the **[!UICONTROL Actions]** (arrow) icon at the bottom to view the available actions you can perform on the asset.

   ![chlimage_1-249](assets/chlimage_1-249.png)

1. Appuyez/cliquez sur **[!UICONTROL Enregistrer comme version]** pour créer une version de la ressource.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Add a label and comment, and then click **[!UICONTROL Create]** to create a version. Alternatively, tap/click **Cancel** to exit the operation.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Pour afficher la nouvelle version, ouvrez la liste **[!UICONTROL Tout afficher]** dans le journal de la page des détails de la ressource ou de l’interface utilisateur d’Assets, puis choisissez **[!UICONTROL Versions]**. Toutes les versions créées pour un fichier sont répertoriées sous l’onglet journal. Vous pouvez filtrer la liste pour afficher les versions en cliquant sur la flèche et en sélectionnant **[!UICONTROL Versions]** dans la liste.

   ![versions_option](assets/versions_option.png)

1. Sélectionnez une version spécifique de la ressource pour la prévisualiser ou lui permettre de s’afficher dans l’IU Assets.

   ![select_version](assets/select_version.png)

1. Ajoutez un libellé et un commentaire pour la version afin de rétablir la version spécifique dans l’IU Assets.

   ![save_version](assets/save_version.png)

1. Pour générer un aperçu de la version, appuyez/cliquez sur **[!UICONTROL Aperçu de la version]**.
1. To display this version in the Assets UI, select **[!UICONTROL Revert to this Version]**.
1. Pour comparer deux versions, accédez à la page Ressource de la ressource et appuyez/cliquez sur la version à comparer à la version actuelle.

   ![select_version_tocompare](assets/select_version_tocompare.png)

1. Dans la frise chronologique, sélectionnez la version à comparer, puis faites glisser le curseur vers la gauche pour superposer cette version sur la version actuelle à comparer.

   ![compare_versions](assets/compare_versions.png)

### Starte a workflow on an asset {#starting-a-workflow-on-an-asset}

1. Accédez à l’emplacement de la ressource pour laquelle vous souhaitez commencer un workflow et appuyez/cliquez sur la ressource pour afficher la page Ressource.
1. Tap/click the GlobalNav icon, and the choose **[!UICONTROL Timeline]** from the menu to display the timeline.

   ![timeline-1](assets/timeline-1.png)

1. Tap/click the **[!UICONTROL Actions]** (arrow) icon at the bottom to open the list of actions available for the asset.

   ![chlimage_1-252](assets/chlimage_1-252.png)

1. Tap/click **[!UICONTROL Start Workflow]** from the list.

   ![chlimage_1-253](assets/chlimage_1-253.png)

1. Dans la section **[!UICONTROL Démarrer le workflow]**, sélectionnez un modèle de workflow dans la liste.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. (Facultatif) Spécifiez le titre du workflow, qui peut permettre de référencer l’instance du workflow.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Appuyez/cliquez sur **[!UICONTROL Démarrer]**, puis appuyez/cliquez sur **[!UICONTROL Continuer]** dans la boîte de dialogue pour confirmer votre choix. Chaque étape du processus est affichée dans la journal sous la forme d’un événement.

   ![chlimage_1-256](assets/chlimage_1-256.png)

## Collections {#collections}

Une collection est un ensemble de ressources classées. Vous pouvez utiliser des collections pour partager des ressources entre utilisateurs.

* Une collection peut comporter des ressources provenant de différents emplacements, car elle ne contient que les références à ces ressources. Chaque collection préserve l’intégrité du référentiel des ressources.
* Vous pouvez partager des ressources avec plusieurs utilisateurs dont les niveaux de privilèges sont différents (modification, affichage, etc.).

See [Managing Collections](/help/assets/manage-collections.md) for details on collection management.
