---
title: Modification des métadonnées en bloc dans la vue Assets
description: Découvrez comment modifier simultanément les métadonnées de plusieurs ressources disponibles dans la vue Assets.
source-git-commit: 5778d0dac141174c1b950625057f920af0301a8b
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Modification des métadonnées en bloc dans la vue Assets{#how-to-edit-the-metadata-of-multiple-assets-simultaneously}

À l’aide de la fonction **Modification des métadonnées en bloc** dans l’interface utilisateur d’affichage Assets, vous pouvez modifier simultanément les métadonnées de plusieurs fichiers de ressources. Au lieu de modifier les métadonnées de chaque ressource individuellement, vous appliquez des modifications à un grand groupe de ressources à la fois. Cette fonctionnalité améliore l’efficacité, la cohérence et la précision des propriétés de métadonnées sur un large ensemble de ressources, améliorant ainsi la capacité de recherche et l’organisation des ressources.

## Modification en masse des métadonnées de ressources {#how-to-bulk-edit-the-metadata-of-multiple-assets-on-assets-view}

Exécutez les étapes suivantes pour modifier en bloc les métadonnées de plusieurs ressources à la fois :

1. Dans la vue Assets, cliquez sur **Assets**.
1. Parcourez les ressources ou saisissez des mots-clés pertinents dans la barre de recherche pour localiser des ressources spécifiques.
1. Sélectionnez plusieurs ressources et cliquez sur **Modification des métadonnées en bloc** dans le menu supérieur.
   ![bulk-metadata-edit](/help/assets/assets/bulk-metadata-edit.png)
1. Sur la page Modifier les métadonnées , modifiez les champs suivants dans le panneau **Propriétés** :
   * **Statut :** sélectionnez un statut pour définir la convivialité des ressources sélectionnées.
   * **Date d’expiration :** définissez une date après laquelle les ressources ne sont plus valides ou nécessaires.
   * **Auteur :** indiquez le nom de l’auteur.
   * **Mots-clés :** ajoutez des termes ou des chaînes de texte qui fournissent des informations générales sur les ressources afin d’améliorer leur visibilité. Ajoutez un mot-clé et appuyez sur Entrée ou Retour pour ajouter un autre mot-clé à la liste.
     <!-- * **Tags:** Click ![tags icon](/help/assets/assets/tags-icon.svg) to select tags from the available options. Tags provide more specific information about the assets and enhances their discoverability. Tags already applied to the selected assets are only displayed in the **Properties** panel. If you cannot find the relevant tags, create the tags and assign them to the selected assets. See [Manage tags in Assets view](/help/assets/tagging-management-assets-view.md) for details.-->
   * Cliquez sur **Enregistrer** pour ajouter des mots-clés et <!-- Tags while--> remplacer les détails existants pour le statut, la date d’expiration et l’auteur.
     ![save-bulk-metadata-edit-properties](/help/assets/assets/save-bulk-metadata-edit-properties1.png)

     >[!NOTE]
     >
     >Vous pouvez modifier les métadonnées de 100 ressources à la fois.

Pour afficher les modifications apportées aux métadonnées d’une ressource, accédez à la page des détails de la ressource (sélectionnez la ressource, cliquez sur **Détails**), puis cliquez sur ![](/help/assets/assets/info-icon-solid-black.svg) pour afficher les métadonnées de la ressource dans le panneau **Informations**.

>[!NOTE]
>
>Les <!-- and Tags--> État, Date d’expiration, Auteur et Mots-clés sont des propriétés de métadonnées standard disponibles pour la modification de métadonnées en bloc, quelles que soient les métadonnées spécifiques au dossier. Ces propriétés de métadonnées s’affichent dans la page des détails de la ressource uniquement si elles sont incluses dans le formulaire de métadonnées appliqué au dossier de la ressource.  Si ces propriétés de métadonnées ne s’affichent pas sur la page des détails de la ressource, modifiez le formulaire de métadonnées du dossier de ressources pour les inclure. Voir [Métadonnées dans la vue Assets](/help/assets/metadata-assets-view.md) pour savoir comment créer ou modifier un formulaire de métadonnées et l’appliquer à un dossier.


