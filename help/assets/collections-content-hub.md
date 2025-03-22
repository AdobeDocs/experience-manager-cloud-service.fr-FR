---
title: Gestion des collections dans Content Hub
description: Découvrez comment gérer les collections dans Content Hub
role: User
exl-id: ea74456c-f980-4a02-b26b-d7c46dac6aee
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 9%

---

# Gestion des collections dans [!DNL Content Hub] {#manage-collections}

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

<!-- ![Manage collections](assets/manage-collections.jpg) -->
![Gestion des collections](assets/manage-collection.png)

>[!AVAILABILITY]
>
>Le guide de Content Hub est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Content Hub]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/content-hub.pdf"}

Une collection fait référence à un ensemble de ressources pouvant être partagées entre les utilisateurs. Une collection peut inclure des ressources provenant de différents emplacements tout en conservant leur intégrité référentielle.

[!DNL Content Hub] permet de créer des collections publiques. Ces collections sont accessibles à tous les utilisateurs autorisés, ce qui crée un espace partagé où plusieurs utilisateurs peuvent accéder efficacement au contenu et l’utiliser. Les collections favorisent l’utilisation collaborative des ressources pour plus d’efficacité et de commodité. Dans la page de navigation des collections, vous pouvez :

* **Créer** : créez une ou plusieurs collections.
* **Affichage** : affichez les ressources et leurs propriétés.
* **Partager** : partagez des ressources sous la forme d’un lien avec d’autres personnes.
* **Télécharger** : téléchargez les ressources.
* **Supprimer** : permet de supprimer des ressources spécifiques d’une collection.
* **Supprimer** : permet de supprimer l’ensemble de la collection.

Il permet aux utilisateurs et utilisatrices d’accéder facilement aux différentes ressources disponibles dans [!DNL Content Hub] et de les gérer.

## Prérequis {#prerequisites}

[Les utilisateurs de Content Hub](deploy-content-hub.md#onboard-content-hub-users) peuvent effectuer les actions mentionnées dans cet article.

## Créer des collections{#create-collections}

Vous pouvez choisir de [créer une nouvelle collection](#create-new-collection) ou [ajouter des ressources à une collection existante](#add-assets-to-existing-collection).

### Créer une collection{#create-new-collection}

Sélectionnez les ressources à ajouter à une collection, puis cliquez sur **[!UICONTROL Ajouter à la collection]**.

![Créer une collection](assets/add-assets-collection.jpg)

Pour créer une nouvelle collection, accédez à l’onglet **[!UICONTROL Collections]** et cliquez sur **[!UICONTROL Créer une collection]**. Saisissez le **[!UICONTROL Titre]** et fournissez une **[!UICONTROL Description]** facultative pour les ressources. Cliquez sur **[!UICONTROL Créer]**.

### Ajout de ressources à une collection existante{#add-assets-to-existing-collection}

Pour ajouter des ressources à une collection existante, sélectionnez les ressources à ajouter à la collection. Cliquez sur **[!UICONTROL Ajouter à la collection]**. Vous êtes invité à sélectionner la collection.

![Créer une nouvelle collection](assets/create-add-collection.jpg)

Sélectionnez la collection dans laquelle vous devez ajouter la ressource. Vous pouvez également rechercher la collection existante à l’aide de la barre de recherche. <br>Sélectionnez la ou les collections auxquelles vous devez ajouter les ressources, puis cliquez sur **[!UICONTROL Ajouter à la collection]**.

## Affichage des collections{#view-collections}

Accédez à l’onglet **[!UICONTROL Collections]** et recherchez le nom de la collection. Pour afficher la liste des ressources disponibles dans une collection, cliquez sur le nom de la collection. Vous pouvez également appliquer des filtres dans une collection pour affiner les résultats de la ressource.

Cliquez sur la ressource à afficher dans une collection. [!DNL Content Hub] affiche la vue détaillée de la ressource. [Voir les détails de la ressource](asset-properties-content-hub.md).

<!--
![Asset details](assets/view-collection.jpg)

* **A**: Details and metadata of the asset 
* **B**: Zoom In or Zoom Out the asset 
* **C**: Reset Zoom view 
* **D**: View the previous or next asset 
* **E**: Download the asset 
* **F**: Open the asset in Adobe Express 
* **G**: Hide the metadata of the asset 
* **H**: Share the asset as a link 
-->

## Téléchargement des ressources disponibles dans une collection{#download-assets-within-collection}

Pour télécharger les ressources disponibles dans une collection, accédez à l’onglet **[!UICONTROL Collections]**.\
Cliquez sur l’icône ![icône de téléchargement](assets/download-icon.svg) sur la carte de collection.

![Onglet Collection](assets/download-collection.jpg)

Toutes les ressources de la collection sont téléchargées.

Vous pouvez également ouvrir la collection pour télécharger les ressources individuellement. Cliquez sur la collection contenant les ressources à télécharger. Sélectionnez les ressources et cliquez sur **[!UICONTROL Télécharger]**.

Découvrez comment [télécharger une ressource à partir du  [!DNL Content Hub]](download-assets-content-hub.md).

## Partage des ressources disponibles dans une collection {#share-assets-available-within-collection}

Vous pouvez également partager les ressources disponibles dans une collection. Accédez à l’onglet **[!UICONTROL Collections]**. Sélectionnez l’icône ![icône de partage](assets/share.svg) sur la vignette de collection. Le lien de partage est copié. Vous pouvez partager le lien copié avec le destinataire. En savoir plus sur le [partage de ressources dans la  [!DNL Content Hub]](share-assets-content-hub.md).

## Modification des détails d’une collection {#edit-details-of-collection}

Pour modifier **[!UICONTROL Titre]** et **[!UICONTROL Description]** d’une collection, cliquez sur le nom de la collection, puis sur l’icône ![icône d’informations](assets/info-icon.svg). L’écran [!UICONTROL Détails de la collection] qui s’affiche vous permet de modifier le **[!UICONTROL Titre]** et le **[!UICONTROL Description]** d’une collection. Cliquez sur **[!UICONTROL Enregistrer les modifications]** pour confirmer les modifications.

![détails de la collection](assets/collection-details.png)

## Supprimer les ressources d’une collection{#remove-assets-from-a-collection}

Vous pouvez supprimer une ou plusieurs ressources d’une collection. Pour supprimer des ressources d’une collection, cliquez sur la collection dans laquelle vous devez supprimer des ressources, sélectionnez-les et cliquez sur **[!UICONTROL Supprimer de la collection]**.

![Supprimer la collection](assets/remove-collection-new.jpg)

Vous êtes invité à confirmer la suppression de la ressource. Cliquez sur **[!UICONTROL Supprimer]**.\
Les ressources sélectionnées ont été supprimées de la collection.

## Suppression d’une collection{#delete-collection}

Pour supprimer une collection, accédez à l’onglet **[!UICONTROL Collections]** et cliquez sur la collection à supprimer. Cliquez sur l’icône ![supprimer](assets/remove-icon.svg) pour supprimer la collection.
