---
title: Gestion des collections dans Content Hub
description: Découvrez comment gérer les collections dans Content Hub
role: User
exl-id: ea74456c-f980-4a02-b26b-d7c46dac6aee
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 6%

---

# Gestion des collections dans [!DNL Content Hub] {#manage-collections}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

<!-- ![Manage collections](assets/manage-collections.jpg) -->
![Gestion des collections](assets/manage-collection.png)

>[!AVAILABILITY]
>
>Le guide Content Hub est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant Adobe Acrobat AI pour répondre à vos requêtes.
>
>[!BADGE PDF de guide Content Hub]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Une collection fait référence à un ensemble de ressources qui peuvent être partagées entre les utilisateurs. Une collection peut inclure des ressources provenant de différents emplacements tout en conservant leur intégrité référentielle.

[!DNL Content Hub] permet de créer des collections publiques. Ces collections sont accessibles à tous les utilisateurs autorisés, ce qui crée un espace partagé où plusieurs utilisateurs peuvent accéder efficacement au contenu et l’utiliser. Les collections favorisent l’utilisation collaborative des ressources pour une efficacité et une commodité accrues. Dans la page de navigation de la collection, vous pouvez :

* **Créer** : créez une ou plusieurs collections.
* **View** : affichez les ressources et leurs propriétés.
* **Partager** : partagez des ressources en tant que lien avec d’autres personnes.
* **Télécharger** : téléchargez les ressources.
* **Supprimer** : supprimez des ressources spécifiques d’une collection.
* **Supprimer** : supprimez la collection entière.

Cela permet aux utilisateurs d’accéder facilement aux différentes ressources disponibles dans [!DNL Content Hub] et de les gérer.

## Conditions préalables {#prerequisites}

[Les utilisateurs de Content Hub](deploy-content-hub.md#onboard-content-hub-users) peuvent effectuer les actions mentionnées dans cet article.

## Créer des collections{#create-collections}

Vous pouvez choisir de [créer une collection](#create-new-collection) ou [ajouter des ressources à une collection existante](#add-assets-to-existing-collection).

### Créer une collection{#create-new-collection}

Sélectionnez les ressources à ajouter à une collection et cliquez sur **[!UICONTROL Ajouter à la collection]**.

![Créer une collection](assets/add-assets-collection.jpg)

Pour créer une collection, accédez à l’onglet **[!UICONTROL Collections]** et cliquez sur **[!UICONTROL Créer une collection]**. Saisissez le **[!UICONTROL titre]** et fournissez une **[!UICONTROL description]** facultative pour les ressources. Cliquez sur **[!UICONTROL Créer]**.

### Ajout de ressources à une collection existante{#add-assets-to-existing-collection}

Pour ajouter des ressources à une collection existante, sélectionnez les ressources à ajouter à la collection. Cliquez sur **[!UICONTROL Ajouter à la collection]**. Vous êtes invité à sélectionner la collection.

![Créer une collection](assets/create-add-collection.jpg)

Sélectionnez la collection dans laquelle vous devez ajouter la ressource. Vous pouvez également rechercher la collection existante à l’aide de la barre de recherche. <br>Sélectionnez la ou les collections auxquelles vous devez ajouter les ressources et cliquez sur **[!UICONTROL Ajouter à la collection]**.

## Affichage des collections{#view-collections}

Accédez à l’onglet **[!UICONTROL Collections]** et recherchez le nom de la collection. Pour afficher la liste des ressources disponibles dans une collection, cliquez sur son nom. Vous pouvez également appliquer des filtres au sein d’une collection pour affiner les résultats des ressources.

Cliquez sur la ressource que vous devez afficher dans une collection. [!DNL Content Hub] affiche la vue détaillée de la ressource. [Voir les détails de la ressource](asset-properties-content-hub.md).

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

## Téléchargement de ressources disponibles dans une collection{#download-assets-within-collection}

Pour télécharger des ressources disponibles dans une collection, accédez à l’onglet **[!UICONTROL Collections]**.\
Cliquez sur l’icône ![ de téléchargement ](assets/download-icon.svg) sur la carte de collection.

![Onglet Collection](assets/download-collection.jpg)

Toutes les ressources de la collection sont téléchargées.

Vous pouvez également ouvrir la collection pour télécharger les ressources individuellement. Cliquez sur la collection contenant les ressources à télécharger. Sélectionnez les ressources et cliquez sur **[!UICONTROL Télécharger]**.

Découvrez comment [télécharger une ressource à partir de [!DNL Content Hub]](download-assets-content-hub.md).

## Partage de ressources disponibles dans une collection {#share-assets-available-within-collection}

Vous pouvez également partager les ressources disponibles dans une collection. Accédez à l’onglet **[!UICONTROL Collections]** . Sélectionnez l’icône ![partager](assets/share.svg) sur la carte de collection. Le lien de partage est copié. Vous pouvez partager le lien copié avec le destinataire. En savoir plus sur le [partage de ressources dans  [!DNL Content Hub]](share-assets-content-hub.md).

## Modification des détails d’une collection {#edit-details-of-collection}

Pour modifier le **[!UICONTROL titre]** et la **[!UICONTROL description]** d&#39;une collection, cliquez sur le nom de la collection, puis sur l&#39;icône ![info](assets/info-icon.svg). L’écran [!UICONTROL Détails de la collection] s’affiche et vous permet de modifier le **[!UICONTROL Titre]** et la **[!UICONTROL Description]** d’une collection. Cliquez sur **[!UICONTROL Enregistrer les modifications]** pour confirmer les modifications.

![détails de la collection](assets/collection-details.png)

## Supprimer les ressources d’une collection{#remove-assets-from-a-collection}

Vous pouvez supprimer une ou plusieurs ressources d’une collection. Pour supprimer des ressources d’une collection, cliquez sur la collection à partir de laquelle vous devez supprimer des ressources, sélectionnez les ressources et cliquez sur **[!UICONTROL Supprimer de la collection]**.

![Supprimer la collection](assets/remove-collection-new.jpg)

Vous êtes invité à confirmer la suppression de la ressource. Cliquez sur **[!UICONTROL Supprimer]**.\
Les ressources sélectionnées sont supprimées de la collection.

## Suppression d’une collection{#delete-collection}

Pour supprimer une collection, accédez à l’onglet **[!UICONTROL Collections]** et cliquez sur la collection que vous devez supprimer. Cliquez sur l’icône ![Supprimer l’icône](assets/remove-icon.svg) pour supprimer la collection.
