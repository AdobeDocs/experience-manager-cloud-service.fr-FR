---
title: Partagez Assets dans  [!DNL the Content Hub]
description: Partagez Assets dans  [!DNL the Content Hub]
role: User
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: 0e66b355d09e2fd2c4c8a5ddacc9b2d033b41bf2
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 17%

---

# Partager des ressources dans le hub de contenus {#search-assets-as-a-link}

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

![Partager l’image de la bannière de ressources](assets/share-assets-banner.png)

>[!AVAILABILITY]
>
>Le guide de Content Hub est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Content Hub]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/content-hub.pdf"}

Créez un lien vers les ressources sélectionnées pour les partager facilement avec d’autres personnes. En tant qu’utilisateur [!DNL Content Hub] autorisé, sélectionnez une ou plusieurs ressources disponibles dans votre environnement [!DNL Content Hub], générez un lien et envoyez-le à d’autres utilisateurs privés ou publics.

## Prérequis {#prerequisites}

[Les utilisateurs de Content Hub](deploy-content-hub.md#onboard-content-hub-users) peuvent créer un lien vers les ressources sélectionnées et le partager avec d’autres utilisateurs.

## Partager des ressources {#share-assets}

Pour partager une ou plusieurs ressources avec des utilisateurs privés ou publics, procédez comme suit :
1. Accédez à la page d’accueil de votre [!DNL Content Hub], sélectionnez une ou plusieurs ressources, puis cliquez sur ![partager](/help/assets/assets/share.svg) **[!UICONTROL Partager]** pour afficher une seule ressource sélectionnée ou une liste de plusieurs ressources sélectionnées dans la boîte de dialogue **[!UICONTROL Partager les ressources]**.
Vous pouvez également sélectionner et partager des ressources disponibles dans ![collections](/help/assets/assets/Smock_Collection_18_N.svg) **[!UICONTROL Collections]**.
1. Affichez une ressource ou consultez la liste des ressources disponibles dans la boîte de dialogue **[!UICONTROL Partage de ressources]**. Cliquez sur ![désélectionner](/help/assets/assets/Close.svg) en regard d’une ressource pour la désélectionner de la liste.
1. Sélectionnez une **[!UICONTROL période d’expiration]** et cliquez sur **[!UICONTROL Générer un lien privé]** pour générer un lien à partager avec des utilisateurs privés. Les utilisateurs privés se connectent à leur environnement [!DNL Content Hub] pour accéder à la page des ressources partagées.
   ![lien privé et public](/help/assets/assets/private-and-public-link.png)
Activez le bouton (bascule) **[!UICONTROL Lien public]**, sélectionnez une **[!UICONTROL période d’expiration]** et cliquez sur **[!UICONTROL Générer un lien public]** pour générer un lien à partager avec les utilisateurs publics. Les utilisateurs publics, en tant qu’invités, accèdent à la page des ressources partagées sans se connecter à [!DNL Content Hub].
   ![lien privé et public](/help/assets/assets/public-and-private-link.png)

   >[!NOTE]
   > 
   > [Activez le partage de liens public à partir de la page de configuration](/help/assets/configure-content-hub-ui-options.md#enable-public-link-sharing) pour afficher le bouton bascule **[!UICONTROL Lien public]** dans la boîte de dialogue **[!UICONTROL Partager les ressources]**.

## Partage d’une ressource à partir de sa page d’aperçu {#share-asset-from-preview-page}

Pour partager une ressource en cours de prévisualisation, procédez comme suit :

1. Accédez à la page d’accueil [!DNL Content Hub] et cliquez sur la miniature de la ressource pour la prévisualiser et afficher les options de menu dans le volet droit de la boîte de dialogue.
1. Sélectionnez ![partager](/help/assets/assets/share.svg) pour afficher le panneau **[!UICONTROL Partager]**.
   ![partager une ressource lors de sa prévisualisation](/help/assets/assets/share-assets-from-share-panel.png)
1. Suivez l’étape 3 de la section [Partage de ressources](#share-assets) pour générer et partager le lien de la ressource (privée ou publique) à partir de ce panneau **[!UICONTROL Partage]**.

## Accéder aux ressources partagées {#access-shared-assets}

Accédez à la page des ressources partagées via le lien et procédez comme suit :

* Sélectionnez une ou plusieurs ressources, puis cliquez sur ![Télécharger](/help/assets/assets/download-icon.svg) **[!UICONTROL Télécharger]** pour sélectionner les rendus **[!UICONTROL Original]**, **[!UICONTROL Statique]** ou les deux à partir des options de téléchargement disponibles.
  ![](/help/assets/assets/download-shared-assets.png)
* Cliquez sur la miniature de la ressource pour afficher ses métadonnées.
* Sur la page des ressources partagées ([accessible via un lien privé](#share-assets)), cliquez sur la miniature d’une ressource et sélectionnez ![télécharger](/help/assets/assets/download-icon.svg) pour sélectionner et afficher les rendus dynamiques disponibles de la ressource dans le panneau **[!UICONTROL Télécharger]** avant de les sélectionner et de les télécharger.
  ![](/help/assets/assets/download-renditions-shared-assets-page.png)





