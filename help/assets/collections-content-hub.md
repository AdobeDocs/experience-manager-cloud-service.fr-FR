---
title: Gestion des collections dans Content Hub
description: Découvrez comment gérer les collections dans Content Hub
role: User
exl-id: ea74456c-f980-4a02-b26b-d7c46dac6aee
source-git-commit: 6bc838ff76edda3e03cbde8da4a28f65cba3b36a
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 10%

---

# Gestion des collections dans [!DNL Content Hub] {#manage-collections}

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

Vous pouvez choisir de [créer une nouvelle collection](#create-new-collection) ou [ajouter des ressources à une collection existante](#add-assets-to-existing-collection) tout en gérant la gouvernance.

### Créer une collection{#create-new-collection}

Pour contrôler l’accès lors de la création de collections, procédez comme suit :

1. Accédez à **[!DNL Collections]** onglet et cliquez sur **[!UICONTROL Créer une collection]**. La fenêtre Nouvelle collection s’affiche.

1. Ajoutez **[!UICONTROL Titre]** et **[!UICONTROL Description]** pour la collection.

   ![autorisations de collection](assets/collection-permissions.png)

1. Sous **[!UICONTROL Qui peut accéder]** liste déroulante > sélectionnez le type de contrôle d’accès. Les options suivantes sont disponibles :

   | Méthode d’accès | Type d’accès | Description |
   |---|---|---|
   | **Seuls vous et les administrateurs pouvez accéder à** | Privée | Seuls le créateur et les administrateurs peuvent modifier cette collection et y accéder. |
   | **Tout le monde peut y accéder** | Public | Tout le monde peut accéder à cette collection, mais seuls les créateurs et les administrateurs peuvent la modifier. |
   | **Tout le monde peut accéder à et modifier** | Public | Cette collection est ouverte à tous, avec un accès complet et des autorisations de modification accordées sans restriction. |

1. Cliquez sur **[!UICONTROL Créer]**. Une fois cette opération terminée, vous pouvez [ajouter des ressources à la collection](#add-assets-to-existing-collection).

>[!VIDEO](https://video.tv.adobe.com/v/3463336)

>[!NOTE]
>
>La gouvernance des collections est une fonctionnalité à disponibilité limitée. Vous pouvez l’activer en créant un ticket d’assistance. Une fois activé, vous devez [Configurer les collections dans Content Hub](configure-content-hub-ui-options.md#configure-collections-content-hub).

<!--To create a new collection, navigate to the **[!UICONTROL Collections]** tab and click **[!UICONTROL Create new collection]**. Enter the **[!UICONTROL Title]** and provide an optional **[!UICONTROL Description]** for the assets. Click **[!UICONTROL Create]**.
![Create collection](assets/add-assets-collection.jpg)          
-->

### Ajout de ressources à une collection existante{#add-assets-to-existing-collection}

Pour ajouter des ressources à une collection existante, sélectionnez les ressources à ajouter à la collection. Cliquez sur **[!UICONTROL Ajouter à la collection]**. Vous êtes invité à sélectionner la collection.

![Créer une nouvelle collection](assets/create-add-collection.jpg)

Sélectionnez la collection dans laquelle vous devez ajouter la ressource. Vous pouvez également rechercher la collection existante à l’aide de la barre de recherche. <br>Sélectionnez la ou les collections auxquelles vous devez ajouter les ressources, puis cliquez sur **[!UICONTROL Ajouter à la collection]**.

## Affichage des collections{#view-collections}

Accédez à l’onglet **[!UICONTROL Collections]** et recherchez le nom de la collection. Vous pouvez utiliser des filtres pour affiner vos résultats de recherche en sélectionnant des critères spécifiques, ce qui vous permet de trouver rapidement les collections les plus pertinentes.

Pour afficher la liste des ressources disponibles dans une collection, cliquez sur le nom de la collection. Vous pouvez également appliquer des filtres dans une collection pour affiner les résultats de la ressource. Cliquez sur la ressource à afficher dans une collection. [!DNL Content Hub] affiche la vue détaillée de la ressource. [Voir les détails de la ressource](asset-properties-content-hub.md).

### Filtrer la vue des collections {#filter-collections-view}

Content Hub vous permet de filtrer la vue des collections afin de trouver facilement ce que vous recherchez en réduisant les options en fonction de vos préférences. Assurez-vous de la [configuration des collections dans Content Hub](configure-content-hub-ui-options.md#configure-collections-content-hub).

Pour filtrer la vue Collections, accédez à **[!DNL Collections]** onglet et à la liste déroulante Collections . Choisissez l’une des options suivantes :

* **[!UICONTROL Toutes les collections] :** sélectionnez cette option pour afficher toutes les collections privées et partagées avec vous.
* **[!UICONTROL Moi seul] :** sélectionnez cette option pour afficher les collections qui vous sont accessibles.
* **[!UICONTROL Tout le monde peut afficher] :** cette option permet de filtrer les collections accessibles à tous, mais modifiables uniquement par le créateur ou la créatrice.
* **[!UICONTROL Tout le monde peut modifier] :** sélectionnez cette option pour filtrer les collections qui sont à la fois accessibles et modifiables par tous.

  ![vue Filtrer les collections](assets/filter-collection-view.png)

De plus, pour filtrer la vue des collections en fonction des autorisations d’accès, accédez à **[!DNL Collections]**’onglet et à l’une des options suivantes :

* **[!UICONTROL Créé par n’importe qui] :** ce filtre vous limite à l’affichage des collections créées par n’importe quel utilisateur.

* **[!UICONTROL Créé par moi] :** ce filtre vous limite à l’affichage des collections créées par vous.

  ![vue Filtrer les collections](assets/filter-collection-view1.png)

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

![Onglet Collection](assets/download-collection.png)

Toutes les ressources de la collection sont téléchargées.

Vous pouvez également ouvrir la collection pour télécharger les ressources individuellement. Cliquez sur la collection contenant les ressources à télécharger. Sélectionnez les ressources et cliquez sur **[!UICONTROL Télécharger]**.

Découvrez comment [télécharger une ressource à partir du  [!DNL Content Hub]](download-assets-content-hub.md).

## Partage des ressources disponibles dans une collection {#share-assets-available-within-collection}

Vous pouvez également partager les ressources disponibles dans une collection. Veillez à [activer le partage de liens public dans Content Hub](configure-content-hub-ui-options.md#enable-public-link-sharing). Accédez à l’onglet **[!UICONTROL Collections]**. Sélectionnez l’icône ![icône de partage](assets/share.svg) sur la vignette de collection. Le lien de partage est copié. Vous pouvez partager le lien copié avec le destinataire. En savoir plus sur le [partage de ressources dans la  [!DNL Content Hub]](share-assets-content-hub.md).

Lors du partage de collections dans Content Hub, vous pouvez définir la portée de l’accès et des actions que les destinataires peuvent effectuer sur les ressources numériques du système. Les collections Content Hub fournissent des outils de gouvernance complets pour une gestion efficace des ressources, y compris des autorisations de partage personnalisables et des fonctionnalités de collaboration. De l’accès en lecture seule au contrôle administratif complet, ces paramètres prennent en charge une gouvernance fine de la distribution des ressources.

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



