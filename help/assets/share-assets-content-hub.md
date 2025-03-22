---
title: Partagez Assets dans  [!DNL the Content Hub]
description: Partagez Assets dans  [!DNL the Content Hub]
role: User
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 11%

---

# Partager des ressources dans le hub de contenus {#search-assets-as-a-link}

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

![Partager l’image de la bannière de ressources](assets/share-assets-banner.png)

>[!AVAILABILITY]
>
>Le guide de Content Hub est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Content Hub]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/content-hub.pdf"}

Le partage de ressources par le biais d’un lien est un moyen pratique de mettre les ressources à la disposition des utilisateurs [!DNL the Content Hub]. Cette fonctionnalité permet aux utilisateurs autorisés d’accéder aux ressources partagées avec eux et de les télécharger. Lors du téléchargement des ressources à partir d’un lien partagé, [!DNL the Content Hub] utilise un service asynchrone qui offre un téléchargement plus rapide et ininterrompu.

## Prérequis {#prerequisites}

[Les utilisateurs de Content Hub](deploy-content-hub.md#onboard-content-hub-users) peuvent effectuer les actions mentionnées dans cet article.

## Partage d’une seule ressource {#share-a-single-asset}

Vous pouvez partager une seule ressource en procédant comme suit :

1. Sélectionnez une ressource et cliquez sur l’icône ![partager](assets/share.svg) pour la partager.

   ![Partage d’une ressource unique](assets/sharing-single-asset.png)

1. Utilisez le champ **[!UICONTROL Expiration]** pour spécifier une date d’expiration pour le lien. Sélectionnez l’une des options disponibles, par exemple 24 heures, 1 semaine, 30 jours, 90 jours, 1 an ou spécifiez une date personnalisée.

1. Cliquez sur **[!UICONTROL Copier le lien de partage]**. Vous pouvez ensuite partager le lien copié avec le destinataire.

## Partage de plusieurs ressources {#share-multiple-assets}

[!DNL The Content Hub] permet de partager plusieurs ressources via un lien partagé. Procédez comme suit :

1. Sélectionnez les ressources que vous devez partager avec le destinataire autorisé. Vous pouvez sélectionner plusieurs ressources une par une ou cliquer sur **[!UICONTROL Tout sélectionner]** pour sélectionner toutes les ressources disponibles en même temps. L’option **[!UICONTROL Tout sélectionner]** s’affiche uniquement lorsque vous sélectionnez au moins une ressource.

1. Cliquez sur l’icône ![icône de partage](assets/share.svg).

   ![Partage de plusieurs ressources](assets/sharing-multiple-assets.png)

1. Dans la section de prévisualisation, vous pouvez également supprimer des ressources en fonction de vos besoins. Utilisez le champ **[!UICONTROL Expiration]** pour spécifier une date d’expiration pour le lien. Sélectionnez l’une des options disponibles, par exemple 24 heures, 1 semaine, 30 jours, 90 jours, 1 an ou spécifiez une date personnalisée.

1. Cliquez sur **[!UICONTROL Copier le lien de partage]**. Vous pouvez ensuite partager le lien copié avec le destinataire.

## Prévisualisation et partage de ressources {#preview-assets}

Vous pouvez prévisualiser pour voir à quoi ressemble une ressource numérique que vous allez partager avant de la partager avec un destinataire de lien. Cliquez sur la ressource à prévisualiser. La [!DNL Content Hub] affiche la [ vue détaillée de la ressource ](asset-properties-content-hub.md).

Cliquez sur l’icône ![partager](assets/share.svg) pour partager une ressource. Utilisez le champ **[!UICONTROL Expiration]** pour spécifier une date d’expiration pour le lien. Sélectionnez l’une des options disponibles, par exemple 24 heures, 1 semaine, 30 jours, 90 jours, 1 an ou spécifiez une date personnalisée. Cliquez sur **[!UICONTROL Copier le lien de partage]**. Vous pouvez ensuite partager le lien copié avec le destinataire.

![Aperçu des ressources dans Content Hub](assets/preview-assets-content-hub.png)

## Accéder aux ressources partagées {#access-shared-assets}

Après avoir partagé le lien pour les ressources, les destinataires autorisés peuvent cliquer sur le lien pour prévisualiser ou télécharger les ressources partagées dans un navigateur web.

Cliquez sur le lien partagé, puis sur l’icône de téléchargement disponible sur la carte de la ressource pour télécharger une ressource.  Vous pouvez également sélectionner plusieurs ressources et cliquer sur **[!UICONTROL Télécharger]**. <!--You can either download original assets or Original+Renditions of an asset.--> [!DNL The Content Hub] télécharge chaque ressource une par une dans le système de fichiers local.

![Accès aux liens partagés](assets/content-hub-access-shared-links.png)
