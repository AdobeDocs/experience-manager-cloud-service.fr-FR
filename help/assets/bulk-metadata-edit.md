---
title: Modification des métadonnées en bloc dans  [!DNL Assets View]
description: Découvrez comment mettre à jour un ensemble prédéfini de champs de métadonnées standard pour plusieurs ressources disponibles sur la [!DNL ! Vue Assets] simultanément.
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: f5fee1b3-2855-4010-ae4a-216beb20920d
source-git-commit: bcdfc9bb418ab405faa82c55820a6ec6062c2b17
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 34%

---

# Modification des métadonnées en bloc dans [!DNL Assets View]{#how-to-edit-the-metadata-of-multiple-assets-simultaneously}

La fonctionnalité **[!DNL Bulk Metadata Edit]** de [!DNL Assets View] vous permet de modifier simultanément un ensemble prédéfini de champs de métadonnées standard pour plusieurs fichiers de ressources. Sélectionnez plusieurs ressources et mettez à jour en masse leur ensemble prédéfini de métadonnées standard au lieu de mettre à jour individuellement ces métadonnées standard pour chaque ressource. Cette fonctionnalité permet de maintenir l’efficacité, la cohérence et la précision de l’ensemble des propriétés de métadonnées standard sur les grands ensembles de ressources, ce qui améliore la capacité de recherche et l’organisation de ces ressources.

## Modification en masse de métadonnées de ressources {#how-to-bulk-edit-the-metadata-of-multiple-assets-on-assets-view}

Procédez comme suit pour modifier en masse les métadonnées de plusieurs ressources en une seule fois :

1. Accédez à **[!DNL Assets View]** et cliquez sur **[!UICONTROL Assets]**.
1. Explorez manuellement pour rechercher des ressources spécifiques ou recherchez-les à l’aide de mots-clés dans la barre de recherche.
1. Sélectionnez les ressources, puis cliquez sur **[!UICONTROL Modifier les métadonnées en masse]** dans le menu supérieur.
   ![Modification de métadonnées en masse](/help/assets/assets/bulk-metadata-edit1.png)
1. Sur la page [!UICONTROL &#x200B; Modifier les métadonnées &#x200B;], modifiez les champs suivants dans le panneau **[!UICONTROL Propriétés]** :
   * **[!UICONTROL Statut] :** sélectionnez un statut pour les ressources sélectionnées.
   * **[!UICONTROL Date d’expiration] :** définissez une date après laquelle les ressources ne sont plus valides ou nécessaires.
   * **[!UICONTROL Auteur] :** spécifiez le nom de l’auteur.
   * **[!UICONTROL Mots-clés] :** ajoutez des termes ou des chaînes de texte spécifiques qui fournissent des informations générales sur les ressources afin d’améliorer leur visibilité. Ajoutez un mot-clé et appuyez sur **Entrée** ou **Retour** pour ajouter un autre mot-clé à la liste.
   * **[!UICONTROL Balises] :** cliquez sur ![modification des métadonnées en bloc](/help/assets/assets/tags-icon.svg) pour sélectionner des balises dans les options disponibles. Les balises fournissent des informations plus spécifiques sur les ressources et améliorent leur visibilité. Les balises déjà appliquées aux ressources sélectionnées s’affichent dans le panneau **[!UICONTROL Propriétés]**. Si vous ne trouvez pas les balises appropriées, créez-les et affectez-les aux ressources sélectionnées. Voir [Gérer les balises dans [!DNL Assets view]](/help/assets/tagging-management-assets-view.md) pour plus d’informations sur la création et l’affectation de balises à des ressources.
   * Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les mises à jour de métadonnées ci-dessus aux ressources sélectionnées. Une fois enregistrés, les **[!UICONTROL Mots-clés]** et **[!UICONTROL Balises]** sont ajoutés, tandis que les détails mis à jour pour **[!UICONTROL Statut]**, **[!UICONTROL Date d’expiration]** et **[!UICONTROL Auteur]** remplacent leurs détails existants.     ![Enregistrement des modifications de métadonnées en masse](/help/assets/assets/save-bulk-metadata-edit-properties2.png)

     >[!NOTE]
     >
     >Vous pouvez modifier les métadonnées de 100 ressources à la fois.

Pour afficher les mises à jour des métadonnées appliquées à une ressource, accédez à la [!DNL asset details page] (sélectionnez la ressource, cliquez sur **[!UICONTROL Détails]**), puis cliquez sur ![modification des métadonnées en bloc](/help/assets/assets/info-icon-solid-black.svg) pour afficher les métadonnées de la ressource dans le panneau **[!UICONTROL Informations]**.

>[!NOTE]
>
>**[!UICONTROL Statut]**, **[!UICONTROL Date d’expiration]**, **[!UICONTROL Auteur ou autrice]**, **[!UICONTROL Mots-clés]** et **[!UICONTROL Balises]** sont des propriétés de métadonnées standard disponibles pour la modification de métadonnées en masse, y compris pour les métadonnées spécifiques à un dossier. Ces propriétés de métadonnées s’affichent dans la page [!UICONTROL Détails de la ressource] uniquement si elles sont incluses dans le formulaire de métadonnées appliqué au dossier de la ressource. Si vous ne trouvez pas ces propriétés de métadonnées standard sur la page [!UICONTROL Détails de la ressource], modifiez le formulaire de métadonnées du dossier de ressources pour les inclure. Voir [Métadonnées dans [!DNL Assets View]](/help/assets/metadata-assets-view.md) pour savoir comment créer ou modifier un formulaire de métadonnées et l’appliquer à un dossier.


**Voir également**

* [Traduire les ressources](/help/assets/translate-assets.md)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](/help/assets/file-format-support.md)
* [Rechercher des ressources](/help/assets/search-assets.md)
* [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](/help/assets/asset-reports.md)
* [Schémas de métadonnées](/help/assets/metadata-schemas.md)
* [Télécharger des ressources](/help/assets/download-assets-from-aem.md)
* [Gestion des métadonnées](/help/assets/manage-metadata.md)
* [Gérer les modèles Dynamic Media](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Gérer les rapports](/help/assets/manage-reports-assets-view.md)
* [Facettes de recherche](/help/assets/search-facets.md)
* [Gérer les collections](/help/assets/manage-collections.md)
* [Import des métadonnées en bloc](/help/assets/metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

