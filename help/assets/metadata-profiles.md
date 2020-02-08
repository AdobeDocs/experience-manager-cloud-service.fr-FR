---
title: Profils de métadonnées
description: Découvrez les profils de métadonnées pour les ressources. Apprenez à créer un profil de métadonnées et à l’appliquer aux ressources d’un dossier.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Profils de métadonnées {#metadata-profiles}

Un profil de métadonnées vous permet d’appliquer des métadonnées par défaut aux fichiers d’un dossier. Créez un profil de métadonnées et appliquez-le à un dossier. Tout fichier que vous téléchargez ensuite vers le dossier hérite des métadonnées par défaut que vous avez configurées dans le profil de métadonnées.

<!-- See [Profiles for Processing Metadata, Images, and Videos](processing-profiles.md).

See also [Best Practices for Organizing your Digital Assets for using Processing Profiles](/help/assets/best-practices-for-file-management.md).

-->

## Ajout d’un profil de métadonnées {#adding-a-metadata-profile}

1. Tap the AEM logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**, and then tap  **[!UICONTROL Create]**.
1. Enter a title for the Metadata Profile, for example Sample Metadata, and tap **[!UICONTROL Submit]**. Le formulaire Modifier pour le profil de métadonnées s’affiche.
1. Click a component and configure its properties in the **[!UICONTROL Settings]** tab. For example, click the **[!UICONTROL Description]** component and edit its properties.
Edit the following properties for the **[!UICONTROL Description]** component:

   * **[!UICONTROL Libellé]** de champ : nom d’affichage de la propriété de métadonnées. Il est uniquement disponible à titre référence.
   * **[!UICONTROL Associer à la propriété]** : la valeur de cette propriété fournit le chemin/nom relatif au noeud de ressource où elle est enregistrée dans le référentiel. La valeur doit toujours commencer par `./` car elle indique que le chemin d’accès se trouve sous le noeud de la ressource.

      La valeur que vous spécifiez pour **[!UICONTROL Associer à la propriété]** est stockée en tant que propriété sous le noeud de métadonnées du fichier. Par exemple, si vous spécifiez . `/jcr:content/metadata/dc:desc` comme nom de la propriété **[!UICONTROL Associer à la propriété]**, AEM Assets stocke la valeur `dc:desc` au noeud de métadonnées de la ressource.

   * **[!UICONTROL Valeur]** par défaut - Utilisez cette propriété pour ajouter une valeur par défaut pour le composant de métadonnées. For example, if you specify &quot;My description&quot; then this value is assigned to the property `dc:desc` at the asset&#39;s metadata node.

      >[!NOTE]
      >
      >Ajout d’une valeur par défaut à une nouvelle propriété de métadonnées (qui n’existe pas déjà dans la . `/jcr:content/metadata` ) n’affiche pas par défaut la propriété et sa valeur sur la page Propriétés du fichier. Pour afficher la nouvelle propriété sur la page Propriétés des ressources, modifiez le formulaire de schéma correspondant.

1. (Optional) Add more components to the Edit Form from the **[!UICONTROL Build Form]** tab, and configure their properties in the **[!UICONTROL Settings]** tab. The following properties are available from the **[!UICONTROL Build Form]** tab:

| Component | Propriétés |
|------------------|----------------------------------------------------|
| En-tête de section | Libellé de champ, Description |
| Une seule ligne de texte | Libellé de champ, Associer à la propriété, Valeur par défaut |
| Texte à plusieurs valeurs | Libellé de champ, Associer à la propriété, Valeur par défaut |
| Nombre | Libellé de champ, Associer à la propriété, Valeur par défaut |
| Date | Libellé de champ, Associer à la propriété, Valeur par défaut |
| Balises standard | Libellé de champ, Faire correspondre à la propriété, Valeur par défaut, Description |

1. Appuyez sur **[!UICONTROL Terminé]**. The Metadata Profile is added to the list of profiles in the **[!UICONTROL Metadata Profiles]** page.

## Copie d’un profil de métadonnées {#copying-a-metadata-profile}

1. From the **[!UICONTROL Metadata Profiles]** page, select a Metadata Profile to make a copy of it.
1. Appuyez sur **[!UICONTROL Copier]** dans la barre d’outils.
1. Dans la boîte de dialogue **[!UICONTROL Copier le profil de métadonnées]**, saisissez un nom pour la nouvelle copie du profil de métadonnées.
1. Appuyez sur **[!UICONTROL Copier]**. The copy of the Metadata Profile appears in the list of profiles in the **[!UICONTROL Metadata Profiles]** page.

## Suppression d’un profil de métadonnées {#deleting-a-metadata-profile}

1. From the **[!UICONTROL Metadata Profiles]** page, select a profile to delete.
1. Tap **[!UICONTROL Delete Metadata Profiles]** in the toolbar.
1. Dans la boîte de dialogue, cliquez sur **[!UICONTROL Supprimer]** pour confirmer l’opération de suppression. Le profil de métadonnées est supprimé de la liste.

## Apply a metadata profile to folders {#applying-a-metadata-profile-to-folders}

Lorsque vous affectez un profil de métadonnées à un dossier, tout sous-dossier hérite automatiquement du profil de son dossier parent. Cela signifie que vous ne pouvez affecter qu’un seul profil de métadonnées à un dossier. Nous vous conseillons donc de choisir avec la plus grande attention la structure du dossier dans lequel vous transférez, stockez, utilisez et archivez des ressources.

Si vous avez affecté un profil de métadonnées différent à un dossier, le nouveau profil remplace le précédent. Les ressources du dossier précédent restent inchangées. Le nouveau profil est appliqué aux ressources ajoutées ultérieurement au dossier.

Les dossiers auxquels un profil est affecté sont indiqués dans l’interface utilisateur par le nom du profil apparaissant dans le nom de la carte.

Vous pouvez appliquer des profils de métadonnées à des dossiers spécifiques ou à l’ensemble des ressources.

You can reprocess assets in a folder that already has an existing metadata profile that you later changed. <!-- See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

### Apply metadata profiles to specific folders {#applying-metadata-profiles-to-specific-folders}

Vous pouvez appliquer un profil de métadonnées à un dossier à partir du menu **[!UICONTROL Outils]** ou, si vous êtes dans le dossier, à partir de **[!UICONTROL Propriétés]**. Cette section explique comment appliquer des profils de métadonnées à des dossiers de deux manières différentes.

Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.

You can reprocess assets in a folder that already has an existing video profile that you later changed. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

#### Apply metadata profiles to folders from Profiles user interface {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Tap the AEM logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Sélectionnez le profil de métadonnées à appliquer à un ou à plusieurs dossiers.
1. Tap **[!UICONTROL Apply Metadata Profile to Folder(s)]** and select the folder or multiple folders you want use to receive the newly uploaded assets and tap **[!UICONTROL Done]**. Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.

#### Apply metadata profiles to folders from Properties {#applying-metadata-profiles-to-folders-from-properties}

1. In the left rail, tap **[!UICONTROL Assets]** then navigate to the folder that you want to apply a metadata profile to.
1. On the folder, tap or click the check mark to select it and then tap or click **Properties**.
1. Select the **[!UICONTROL Metadata Profiles]** tab and select the profile from the drop-down menu and tap **Save]**. Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.

### Apply a metadata profile globally {#applying-a-metadata-profile-globally}

En plus d’appliquer un profil à un dossier, vous pouvez également en appliquer un de façon globale, de sorte que tout contenu transféré dans AEM Assets soit traité par ce profil, indifféremment du dossier.

You can reprocess assets in a folder that already has an existing metadata profile that you later changed. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

**Pour appliquer un profil de métadonnées globalement, effectuez l’une des opérations suivantes :**

* Accédez à `https://<AEM server>/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` et appliquez le profil approprié, puis appuyez sur **Enregistrer**.

* Navigate to CRXDE Lite to the following node: `/content/dam/jcr:content`. Ajoutez la propriété `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>` et appuyez sur **Enregistrer tout**.

## Suppression d’un profil de métadonnées d’un dossier {#removing-a-metadata-profile-from-folders}

Lorsque vous supprimez un profil de métadonnées d’un dossier, tout sous-dossier hérite automatiquement de la suppression du profil de son dossier parent. Cependant, le traitement des fichiers qui s’est produit dans les dossiers reste intact.

You can remove a metadata profile from a folder from within the **Tools** menu or if you are in the folder, from the **Properties**. Cette section explique comment supprimer des profils de métadonnées des dossiers de deux manières différentes.

### Suppression de profils de métadonnées d’un dossier via l’interface utilisateur des profils {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Tap or click the AEM logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Sélectionnez le profil de métadonnées à supprimer d’un ou de plusieurs dossiers.
1. Tap **[!UICONTROL Remove Metadata Profile from Folder(s)]** and select the folder or multiple folders you want use to remove a profile from and tap **[!UICONTROL Done]**.

   Le fait que le nom du profil n’apparaît plus sous celui du dossier indique que le profil de métadonnées n’est plus appliqué à un dossier.

### Suppression des profils de métadonnées des dossiers via Propriétés {#removing-metadata-profiles-from-folders-via-properties}

1. Tap the AEM logo and navigate **[!UICONTROL Assets]** and then to the folder that you want to remove an metadata profile from.
1. On the folder, tap the check mark to select it and then tap **[!UICONTROL Properties]**.
1. Sélectionnez l’onglet **[!UICONTROL Profils de métadonnées]**, puis **[!UICONTROL Aucun]** dans le menu déroulant, et cliquez sur **[!UICONTROL Enregistrer]**. Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.
