---
title: Profils de métadonnées
description: Découvrez les profils de métadonnées pour les ressources. Apprenez à créer un profil de métadonnées et à l’appliquer aux ressources d’un dossier.
contentOwner: AG
translation-type: ht
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Profils de métadonnées {#metadata-profiles}

Un profil de métadonnées vous permet d’appliquer des métadonnées par défaut aux ressources d’un dossier. Créez un profil de métadonnées et appliquez-le à un dossier. Toute ressource chargée par la suite dans le dossier héritera des métadonnées par défaut que vous avez configurées dans le profil de métadonnées.

<!-- See [Profiles for Processing Metadata, Images, and Videos](processing-profiles.md).

See also [Best Practices for Organizing your Digital Assets for using Processing Profiles](/help/assets/best-practices-for-file-management.md).

-->

## Ajout d’un profil de métadonnées {#adding-a-metadata-profile}

1. Appuyez sur le logo AEM et accédez à **[!UICONTROL Outils > Ressources > Profils de métadonnées]**, puis appuyez sur **[!UICONTROL Créer]**.
1. Saisissez un titre pour le profil de métadonnées (Exemple de métadonnées, par exemple), puis appuyez sur **[!UICONTROL Envoyer]**. La page Modifier le formulaire pour le profil de métadonnées s’affiche.
1. Cliquez sur un composant, puis configurez ses propriétés dans l’onglet **[!UICONTROL Paramètres]**. Cliquez par exemple sur le composant **[!UICONTROL Description]** et modifiez ses propriétés.
Modifiez les propriétés suivantes pour le composant **[!UICONTROL Description]** :

   * **[!UICONTROL Libellé du champ]** : nom sous lequel s’affiche la propriété des métadonnées. Il est uniquement disponible à titre de référence.
   * **[!UICONTROL Associer à la propriété]** : la valeur de cette propriété fournit le nom/chemin relatif au nœud de la ressource où elle est enregistrée dans le référentiel. Cette valeur doit toujours commencer par `./`, car cela indique que le chemin d’accès se situe sous le nœud de la ressource.

      La valeur que vous indiquez pour **[!UICONTROL Associer à la propriété]** est stockée en tant que propriété sous le nœud de métadonnées de la ressource. Par exemple, si vous spécifiez . `/jcr:content/metadata/dc:desc` comme nom pour **[!UICONTROL Associer à la propriété]**, AEM Assets stocke la valeur `dc:desc` comme nœud de métadonnées de la ressource.

   * **[!UICONTROL Valeur par défaut]** : utilisez cette propriété pour ajouter une valeur par défaut pour le composant des métadonnées. Par exemple, si vous indiquez « Ma description », cette valeur est affectée à la propriété `dc:desc` au niveau du nœud de métadonnées de la ressource.

      >[!NOTE]
      >
      >Si vous ajoutez une valeur par défaut à une nouvelle propriété de métadonnées (qui n’existe pas encore au niveau du nœud `/jcr:content/metadata`), la propriété et sa valeur ne s’affichent pas, par défaut, sur la page Propriétés de la ressource. Pour afficher la nouvelle propriété sur cette page, modifiez le formulaire de schéma correspondant.

1. (Facultatif) Ajoutez d’autres composants à la page Modifier le formulaire depuis l’onglet **[!UICONTROL Créer le formulaire]**, puis configurez leurs propriétés dans l’onglet **[!UICONTROL Paramètres]**. Les propriétés suivantes sont disponibles à partir de l’onglet **[!UICONTROL Créer le formulaire]** :

| Composant | Propriétés |
|------------------|----------------------------------------------------|
| En-tête de section | Libellé de champ, Description |
| Une seule ligne de texte | Libellé de champ, Associer à la propriété, Valeur par défaut |
| Texte à plusieurs valeurs | Libellé de champ, Associer à la propriété, Valeur par défaut |
| Nombre | Libellé de champ, Associer à la propriété, Valeur par défaut |
| Date | Libellé de champ, Associer à la propriété, Valeur par défaut |
| Balises standard | Libellé de champ, Associer à la propriété Valeur par défaut, Description |

1. Appuyez sur **[!UICONTROL Terminé]**. Le profil de métadonnées est ajouté à la liste des profils de la page **[!UICONTROL Profils de métadonnées]**.

## Copie d’un profil de métadonnées {#copying-a-metadata-profile}

1. Sélectionnez un profil de métadonnées sur la page **[!UICONTROL Profils de métadonnées]** pour en faire une copie.
1. Appuyez sur **[!UICONTROL Copier]** dans la barre d’outils.
1. Dans la boîte de dialogue **[!UICONTROL Copier le profil de métadonnées]**, saisissez le nom de la nouvelle copie du profil de métadonnées.
1. Appuyez sur **[!UICONTROL Copier]**. La copie du profil de métadonnées apparaît dans la liste des profils de la page **[!UICONTROL Profils de métadonnées]**.

## Suppression d’un profil de métadonnées {#deleting-a-metadata-profile}

1. Dans la page **[!UICONTROL Profils de métadonnées]**, sélectionnez un profil à supprimer.
1. Appuyez sur **[!UICONTROL Supprimer les profils de métadonnées]** dans la barre d’outils.
1. Dans la boîte de dialogue, cliquez sur **[!UICONTROL Supprimer]** pour confirmer l’opération de suppression. Le profil de métadonnées est supprimé de la liste.

## Application d’un profil de métadonnées à des dossiers {#applying-a-metadata-profile-to-folders}

Lorsque vous affectez un profil de métadonnées à un dossier, tout sous-dossier hérite automatiquement du profil de son dossier parent. Cela signifie que vous ne pouvez affecter qu’un seul profil de métadonnées à un dossier. Nous vous conseillons donc de choisir avec la plus grande attention la structure du dossier dans lequel vous transférez, stockez, utilisez et archivez des ressources.

Si vous avez affecté un profil de métadonnées différent à un dossier, le nouveau profil remplace le précédent. Les ressources du dossier précédent restent inchangées. Le nouveau profil est appliqué aux ressources ajoutées ultérieurement au dossier.

Les dossiers auxquels un profil est affecté sont indiqués dans l’interface utilisateur par le nom du profil apparaissant dans le nom de la carte.

Vous pouvez appliquer des profils de métadonnées à des dossiers spécifiques ou à l’ensemble des ressources.

Vous pouvez retraiter des ressources dans un dossier qui comporte déjà un profil de métadonnées que vous avez modifié. <!-- See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

### Application de profils de métadonnées à des dossiers spécifiques {#applying-metadata-profiles-to-specific-folders}

Vous pouvez appliquer un profil de métadonnées à un dossier à partir du menu **[!UICONTROL Outils]** ou, si vous êtes dans le dossier, à partir de **[!UICONTROL Propriétés]**. Cette section explique comment appliquer des profils de métadonnées à des dossiers de deux manières différentes.

Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.

Vous pouvez retraiter des ressources dans un dossier qui comporte déjà un profil vidéo que vous avez modifié ultérieurement. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

#### Application de profils de métadonnées à des dossiers à partir de l’interface utilisateur des profils {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Appuyez sur le logo AEM et accédez à **[!UICONTROL Outils > Ressources > Profils de métadonnées]**.
1. Sélectionnez le profil de métadonnées à appliquer à un ou à plusieurs dossiers.
1. Appuyez sur **[!UICONTROL Appliquer le profil de métadonnées au ou aux dossiers]** et sélectionnez ensuite le(s) dossier(s) que vous souhaitez utiliser pour recevoir les ressources récemment chargées. Ensuite, appuyez sur **[!UICONTROL Terminé]**. Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.

#### Application de profils de métadonnées aux dossiers à partir des propriétés {#applying-metadata-profiles-to-folders-from-properties}

1. Dans le rail de gauche, appuyez sur **[!UICONTROL Ressources]**, puis accédez au dossier auquel vous souhaitez appliquer un profil de métadonnées.
1. Dans le dossier, appuyez ou cliquez sur la coche afin de la sélectionner, puis appuyez ou cliquez sur **Propriétés**.
1. Sélectionnez l’onglet **[!UICONTROL Profils de métadonnées]**, sélectionnez le profil dans le menu déroulant, puis appuyez sur **Enregistrer**. Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.

### Application d’un profil de métadonnées à l’ensemble des ressources {#applying-a-metadata-profile-globally}

En plus d’appliquer un profil à un dossier, vous pouvez en appliquer un de façon globale, de sorte que tout contenu chargé dans AEM Assets soit traité par ce profil, indifféremment du dossier.

Vous pouvez retraiter des ressources dans un dossier qui comporte déjà un profil de métadonnées que vous avez modifié ultérieurement. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

**Pour appliquer un profil de façon globale, effectuez l’une des opérations suivantes :**

* Accédez à `https://<AEM server>/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` et appliquez le profil approprié, puis appuyez sur **Enregistrer**.

* Accédez au nœud suivant de CRXDE Lite : `/content/dam/jcr:content`. Ajoutez la propriété `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>` et appuyez sur **Tout enregistrer**.

## Suppression d’un profil de métadonnées d’un dossier {#removing-a-metadata-profile-from-folders}

Lorsque vous supprimez un profil de métadonnées d’un dossier, tout sous-dossier hérite automatiquement de la suppression du profil de son dossier parent. Cependant, le traitement des fichiers qui s’est produit dans les dossiers reste intact.

Vous pouvez supprimer un profil de métadonnées d’un dossier à partir du menu **Outils** ou, si vous êtes dans le dossier, à partir de **Propriétés**. Cette section explique comment supprimer des profils de métadonnées des dossiers de deux manières différentes.

### Suppression de profils de métadonnées d’un dossier via l’interface utilisateur des profils   {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Appuyez ou cliquez sur le logo AEM et accédez à **[!UICONTROL Outils > Ressources > Profils de métadonnées]**.
1. Sélectionnez le profil de métadonnées à supprimer d’un ou de plusieurs dossiers.
1. Appuyez sur **[!UICONTROL Supprimer le profil de métadonnées du ou des dossiers]** et sélectionnez ensuite le(s) dossier(s) duquel (desquels) vous souhaitez supprimer le profil. Ensuite, appuyez sur **[!UICONTROL Terminé]**.

   Le fait que le nom du profil n’apparaît plus sous celui du dossier indique que le profil de métadonnées n’est plus appliqué à un dossier.

### Suppression des profils de métadonnées des dossiers via Propriétés {#removing-metadata-profiles-from-folders-via-properties}

1. Appuyez sur le logo AEM, puis accédez à **[!UICONTROL Ressources]** et au dossier duquel vous souhaitez supprimer un profil de métadonnées.
1. Dans le dossier, appuyez sur la coche pour la sélectionner, puis sur **[!UICONTROL Propriétés]**.
1. Sélectionnez l’onglet **[!UICONTROL Profils de métadonnées]**, puis **[!UICONTROL Aucun]** dans le menu déroulant, et cliquez sur **[!UICONTROL Enregistrer]**. Dans le cas des dossiers auxquels un profil est déjà affecté, le nom du profil est affiché directement sous celui du dossier.
