---
title: Importer  [!DNL Admin View]  formulaires de métadonnées dans  [!DNL Assets View]
description: Cet article décrit comment importer le formulaire de métadonnées disponible dans  [!DNL Admin View] vers [!DNL Assets View]
contentOwner: AG
feature: Metadata
role: User, Admin
source-git-commit: 1ee93bee379ba48a9b42b13b5d11ff89f705b298
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 8%

---


# Importation de formulaires de métadonnées [!DNL Admin View] dans [!DNL Assets View] {#import-admin-view-metadata-forms-to-assets-view}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’IU</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activer Dynamic Media Prime et Ultimate</b></a>
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

[!DNL Adobe Experience Manager Assets] vous permet d’importer des formulaires de métadonnées et leurs associations de dossiers de [!DNL Admin View] vers [!DNL Assets View].

## Avant de commencer{#prerequisites-for-importing-metadata-forms-to-assets-view}

Assurez-vous de disposer des droits d’administrateur pour importer les formulaires de métadonnées et leurs associations de dossiers de [!DNL Admin View] vers [!DNL Assets View].

## Importation de formulaires de métadonnées dans [!DNL Assets View]{#import-metadata-forms-to-assets-view}

En tant qu’administrateur, procédez comme suit pour importer les formulaires de métadonnées disponibles dans [!DNL Admin View] vers [!DNL Assets View] :

1. Accédez à la page d’accueil [!DNL Assets View] et cliquez sur **[!UICONTROL le Forms de métadonnées]** sous **[!UICONTROL Paramètres]** pour ouvrir la page **[!UICONTROL Forms de métadonnées]** qui répertorie les formulaires de métadonnées disponibles dans [!DNL Assets View].
   ![page formulaires de métadonnées](/help/assets/assets/metadata-forms-page.png)
1. Sélectionnez **[!UICONTROL Importer]**, un message relatif au traitement s’affiche (par exemple, *Traitement de 2 formulaires de métadonnées ... Veuillez patienter.*) pendant que l&#39;importation est en cours. Une fois le traitement terminé, le tableau **[!UICONTROL Importer des formulaires de métadonnées]** s’affiche, avec la liste des formulaires de métadonnées disponibles dans [!DNL Admin View]. La ligne du tableau comprend le nom du formulaire de métadonnées (sous **[!UICONTROL Nom]**), les dossiers associés à ce formulaire (sous **[!UICONTROL Association de dossiers]**) et une option permettant de prévisualiser ![prévisualiser](/help/assets/assets/Preview.svg) le formulaire avant de l’importer.
   ![Page Importer un Forms de métadonnées ](/help/assets/assets/import-metadata-forms-page.png)

   >[!NOTE]
   > 
   > Dans le **[!UICONTROL Forms d’importation des métadonnées]**, le tableau d’un libellé **[!UICONTROL Dupliquer]** à côté d’un nom de formulaire indique que le formulaire est déjà appliqué à un dossier dans [!DNL Assets View]. L’importation de ce formulaire en double remplace celui appliqué au dossier. Pour éviter ce remplacement, renommez le formulaire avant de l’importer. Cliquez sur le nom du formulaire pour le renommer.
1. Cliquez sur ![Sélectionner un dossier](/help/assets/assets/x.svg) en regard d’un nom de dossier (sous [!UICONTROL Association de dossiers]) pour supprimer l’association de dossier au formulaire.
1. Cliquez sur ![Sélectionner un dossier](/help/assets/assets/add-to-folder.svg) pour sélectionner un dossier auquel affecter le formulaire de métadonnées correspondant.
1. Cliquez sur le cercle rouge pour afficher les détails sur les composants de métadonnées ou les mappages non pris en charge dans le formulaire qui sont exclus de l’importation.
   ![Page Importer un Forms de métadonnées ](/help/assets/assets/unsupported-import-elements.png)
1. Sélectionnez un ou plusieurs formulaires dans le tableau, puis cliquez sur **[!UICONTROL Démarrer l’importation]** pour importer les formulaires de métadonnées et leurs dossiers associés dans [!DNL Assets View]. Un message de traitement s’affiche (par exemple, *Importation de 3 formulaires de métadonnées. Veuillez patienter.*). Une fois l’importation terminée, un message de réussite confirme que les formulaires ont bien été importés et la page **[!UICONTROL Forms de métadonnées]** (sur [!DNL Assets View]) affiche les formulaires récemment importés et les formulaires existants disponibles dans [!DNL Assets View]. Vous pouvez effectuer les opérations suivantes sur cette page :
   * Cliquez sur l’en-tête de colonne pour trier le tableau par [!UICONTROL Nom], [!UICONTROL Modifié] ou [!UICONTROL Auteur].
   * Sélectionnez le formulaire importé et cliquez sur **[!UICONTROL Supprimer du ou des dossiers)]** puis vérifiez le nom du dossier dans le chemin d’accès au dossier pour vous assurer que le dossier est correctement transféré.

     ![page vérifier les formulaires de métadonnées](/help/assets/assets/confirm-ported-folder.png)
   * Sélectionnez le formulaire importé et cliquez sur **[!UICONTROL Modifier]** pour afficher toutes les configurations prises en charge du formulaire de métadonnées. Consultez [Configuration du Forms de métadonnées](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/metadata#metadata-forms) pour plus d’informations sur les formulaires de métadonnées, leurs composants et champs.

     ![page vérifier les formulaires de métadonnées](/help/assets/assets/verify-metadata-forms-page.png)

## Vérification des formulaires de métadonnées importés{#Verify-the-imported-metadata-forms}

Après avoir importé les formulaires de métadonnées de [!DNL Admin View] vers [!DNL Assets View], procédez comme suit pour vérifier l’importation :

1. Accédez à l’un des dossiers associés au formulaire de métadonnées importé.
1. Accédez à la page des détails d’une [ ressource](/help/assets/navigate-assets-view.md#preview-assets) et vérifiez que les composants de métadonnées, les champs de composant et les valeurs de champ pris en charge sont synchronisés à partir de [!DNL Admin View]. Consultez l’article [Métadonnées dans Assets Essentials](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/metadata) pour plus d’informations sur les composants de métadonnées, les champs de composant et les valeurs de champ.

   >[!NOTE]
   >
   > Dans [[!DNL Assets View] la page de détails](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/metadata-assets-view#metadata-forms) ou [[!DNL Admin View] la page de propriétés](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/administer/metadata-schemas), les modifications apportées aux valeurs de propriété des métadonnées sont automatiquement synchronisées entre les deux interfaces. Toutefois, les modifications structurelles du formulaire, telles que l’ajout ou la suppression de champs, ou d’autres modifications, ne sont pas synchronisées.