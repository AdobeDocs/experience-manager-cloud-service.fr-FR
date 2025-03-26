---
title: Modification des métadonnées en bloc dans  [!DNL Assets View]
description: Découvrez comment mettre à jour un ensemble prédéfini de champs de métadonnées standard pour plusieurs ressources disponibles sur la [DNL! Vue Assets] simultanément.
exl-id: f5fee1b3-2855-4010-ae4a-216beb20920d
source-git-commit: 46d64c089ff22492bc871ead36e8c08d683043b1
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 3%

---

# Modification des métadonnées en bloc dans [!DNL Assets View]{#how-to-edit-the-metadata-of-multiple-assets-simultaneously}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouvelle</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’interface utilisateur</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activation de Dynamic Media Prime et Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Bonnes pratiques relatives aux métadonnées</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Hub de contenus</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Fonctionnalités Dynamic Media avec OpenAPI</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Documentation de développement pour AEM Assets</b></a>
        </td>
    </tr>
</table>

La fonctionnalité **[!DNL Bulk Metadata Edit]** de [!DNL Assets View] vous permet de modifier simultanément un ensemble prédéfini de champs de métadonnées standard pour plusieurs fichiers de ressources. Sélectionnez plusieurs ressources et mettez à jour en une fois leur ensemble prédéfini de métadonnées standard au lieu de mettre à jour individuellement ces métadonnées standard pour chaque ressource. Cette fonctionnalité de modification en bloc de l’ensemble standard de propriétés de métadonnées pour plusieurs ressources à la fois maintient l’efficacité, la cohérence et la précision de ces propriétés de métadonnées standard sur l’ensemble important de ressources, améliorant ainsi la capacité de recherche et l’organisation de ces ressources.

## Modification en masse des métadonnées de ressources {#how-to-bulk-edit-the-metadata-of-multiple-assets-on-assets-view}

Exécutez les étapes suivantes pour modifier en bloc les métadonnées de plusieurs ressources à la fois :

1. Accédez à **[!DNL Assets View]** et cliquez sur **[!UICONTROL Assets]**.
1. Recherchez des ressources spécifiques ou recherchez-les à l’aide de mots-clés dans la barre de recherche.
1. Sélectionnez les ressources et cliquez sur **[!UICONTROL Modification des métadonnées en bloc]** dans le menu supérieur.
   ![bulk-metadata-edit](/help/assets/assets/bulk-metadata-edit1.png)
1. Sur la page [!UICONTROL  Modifier les métadonnées ], modifiez les champs suivants dans le panneau **[!UICONTROL Propriétés]** :
   * **[!UICONTROL Statut] :** sélectionnez un statut pour les ressources sélectionnées.
   * **[!UICONTROL Date d’expiration] :** définissez une date après laquelle les ressources ne sont plus valides ou nécessaires.
   * **[!UICONTROL Auteur] :** spécifiez le nom de l’auteur.
   * **[!UICONTROL Mots-clés] :** ajoutez des termes ou des chaînes de texte spécifiques qui fournissent des informations générales sur les ressources afin d’améliorer leur visibilité. Ajoutez un mot-clé et appuyez sur **Entrée** ou **Retour** pour ajouter un autre mot-clé à la liste.
   * **[!UICONTROL Balises] :** cliquez sur ![modification des métadonnées en bloc](/help/assets/assets/tags-icon.svg) pour sélectionner des balises dans les options disponibles. Les balises fournissent des informations plus spécifiques sur les ressources et améliorent leur visibilité. Les balises déjà appliquées aux ressources sélectionnées s’affichent dans le panneau **[!UICONTROL Propriétés]**. Si vous ne trouvez pas les balises appropriées, créez-les et affectez-les aux ressources sélectionnées. Voir [Gérer les balises dans [!DNL Assets view]](/help/assets/tagging-management-assets-view.md) pour plus d’informations sur la création et l’affectation de balises à des ressources.
   * Cliquez sur **[!UICONTROL Enregistrer]** pour appliquer les mises à jour de métadonnées ci-dessus aux ressources sélectionnées. Une fois enregistrés, les **[!UICONTROL Mots-clés]** et **[!UICONTROL Balises]** sont ajoutés, tandis que les détails mis à jour pour **[!UICONTROL Statut]**, **[!UICONTROL Date d’expiration]** et **[!UICONTROL Auteur]** remplacent leurs détails existants.
     ![save-bulk-metadata-edit-properties](/help/assets/assets/save-bulk-metadata-edit-properties2.png)

     >[!NOTE]
     >
     >Vous pouvez modifier les métadonnées de 100 ressources à la fois.

Pour afficher les mises à jour des métadonnées appliquées à une ressource, accédez à la [!DNL asset details page] (sélectionnez la ressource, cliquez sur **[!UICONTROL Détails]**), puis cliquez sur ![modification des métadonnées en bloc](/help/assets/assets/info-icon-solid-black.svg) pour afficher les métadonnées de la ressource dans le panneau **[!UICONTROL Informations]**.

>[!NOTE]
>
>**[!UICONTROL Statut]**, **[!UICONTROL Date d’expiration]**, **[!UICONTROL Auteur]**, **[!UICONTROL Mots-clés]** et **[!UICONTROL Balises]** sont des propriétés de métadonnées standard disponibles pour la modification de métadonnées en bloc, quelles que soient les métadonnées spécifiques au dossier. Ces propriétés de métadonnées s’affichent dans la page [!UICONTROL Détails de la ressource] uniquement si elles sont incluses dans le formulaire de métadonnées appliqué au dossier de la ressource. Si vous ne trouvez pas ces propriétés de métadonnées standard sur la page [!UICONTROL Détails de la ressource], modifiez le formulaire de métadonnées du dossier de ressources pour les inclure. Voir [Métadonnées dans [!DNL Assets View]](/help/assets/metadata-assets-view.md) pour savoir comment créer ou modifier un formulaire de métadonnées et l’appliquer à un dossier.
