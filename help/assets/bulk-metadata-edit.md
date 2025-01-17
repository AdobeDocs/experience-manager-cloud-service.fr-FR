---
title: Modification des métadonnées en bloc dans la vue Assets
description: Découvrez comment modifier simultanément les métadonnées de plusieurs ressources disponibles dans la vue Assets.
exl-id: f5fee1b3-2855-4010-ae4a-216beb20920d
source-git-commit: 55cb3bb5771c154191fe5b59e56cf9f077590169
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Modification des métadonnées en bloc dans la vue Assets{#how-to-edit-the-metadata-of-multiple-assets-simultaneously}

La fonction **Modification des métadonnées en bloc** de la vue Assets permet aux utilisateurs de modifier simultanément un ensemble prédéfini de champs de métadonnées standard pour plusieurs fichiers de ressources. Sélectionnez plusieurs ressources et mettez à jour en une fois leur ensemble prédéfini de métadonnées standard au lieu de mettre à jour individuellement ces métadonnées standard pour chaque ressource. Cette fonctionnalité améliore l’efficacité, la cohérence et la précision des propriétés de métadonnées standard sur un large ensemble de ressources, améliorant ainsi la capacité de recherche et l’organisation des ressources.

## Modification en masse des métadonnées de ressources {#how-to-bulk-edit-the-metadata-of-multiple-assets-on-assets-view}

Exécutez les étapes suivantes pour modifier en bloc les métadonnées de plusieurs ressources à la fois :

1. Dans la vue Assets, cliquez sur **Assets**.
1. Recherchez des ressources spécifiques ou recherchez-les à l’aide de mots-clés dans la barre de recherche.
1. Sélectionnez les ressources et cliquez sur **Modification des métadonnées en bloc** dans le menu supérieur.
   ![bulk-metadata-edit](/help/assets/assets/bulk-metadata-edit1.png)
1. Sur la page Modifier les métadonnées , modifiez les champs suivants dans le panneau **Propriétés** :
   * **Statut :** sélectionnez un statut pour les ressources sélectionnées.
   * **Date d’expiration :** définissez une date après laquelle les ressources ne sont plus valides ou nécessaires.
   * **Auteur :** indiquez le nom de l’auteur.
   * **Mots-clés :** ajoutez des termes ou des chaînes de texte spécifiques qui fournissent des informations générales sur les ressources afin d’améliorer leur visibilité. Ajoutez un mot-clé et appuyez sur Entrée ou Retour pour ajouter un autre mot-clé à la liste.
   * **Balises :** cliquez sur ![icône des balises](/help/assets/assets/tags-icon.svg) pour sélectionner des balises dans les options disponibles. Les balises fournissent des informations plus spécifiques sur les ressources et améliorent leur visibilité. Les balises déjà appliquées aux ressources sélectionnées s’affichent dans le panneau **Propriétés**. Si vous ne trouvez pas les balises appropriées, créez-les et affectez-les aux ressources sélectionnées. Voir [Gérer les balises dans la vue Assets](/help/assets/tagging-management-assets-view.md) pour plus d’informations sur la création et l’affectation de balises à des ressources.
   * Cliquez sur **Enregistrer** pour appliquer les mises à jour de métadonnées ci-dessus aux ressources sélectionnées. Une fois enregistrés, les mots-clés et les balises sont ajoutés, tandis que les détails mis à jour pour le statut, la date d’expiration et l’auteur remplacent leurs détails existants.
     ![save-bulk-metadata-edit-properties](/help/assets/assets/save-bulk-metadata-edit-properties2.png)

     >[!NOTE]
     >
     >Vous pouvez modifier les métadonnées de 100 ressources à la fois.

Pour afficher les métadonnées appliquées mises à jour dans une ressource, accédez à la page des détails de la ressource (sélectionnez la ressource, cliquez sur **Détails**), puis cliquez sur ![](/help/assets/assets/info-icon-solid-black.svg) pour afficher les métadonnées de la ressource dans le panneau **Informations**.

>[!NOTE]
>
>**Statut**, **Date d’expiration**, **Auteur**, **Mots-clés** et **Balises** sont des propriétés de métadonnées standard disponibles pour la modification de métadonnées en bloc, quelles que soient les métadonnées spécifiques au dossier. Ces propriétés de métadonnées s’affichent dans la page des détails de la ressource uniquement si elles sont incluses dans le formulaire de métadonnées appliqué au dossier de la ressource. Si vous ne trouvez pas ces propriétés de métadonnées standard sur la page des détails de la ressource, modifiez le formulaire de métadonnées du dossier de ressources pour les inclure. Voir [Métadonnées dans la vue Assets](/help/assets/metadata-assets-view.md) pour savoir comment créer ou modifier un formulaire de métadonnées et l’appliquer à un dossier.
