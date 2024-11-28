---
title: Aperçu de la ressource et de ses propriétés dans [!DNL the Content Hub]
description: Découvrez comment prévisualiser des ressources et des propriétés dans [!DNL Content Hub]
role: User
exl-id: a85af980-4c51-4d30-9fad-afd16370e9db
source-git-commit: 2be8d61f1f00444f01772515760d15f2a6f81cd9
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 13%

---

# Aperçu de la ressource et de ses propriétés dans Content Hub {#asset-properties}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![Image de bannière de métadonnées](assets/metadata-banner-image.png)

>[!AVAILABILITY]
>
>Le guide Content Hub est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant Adobe Acrobat AI pour répondre à vos requêtes.
>
>[!BADGE PDF de guide Content Hub]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

[!DNL The Content Hub] vous permet d’afficher des informations sur la ressource qui sont essentielles pour une distribution efficace des ressources. Il s’agit de la collecte de toutes les données disponibles pour une ressource.

L’affichage de l’aperçu des ressources et de ses propriétés vous aide à classer les ressources de manière plus détaillée et s’avère utile à mesure que la quantité d’informations numériques augmente. Il est ainsi possible de gérer quelques centaines de fichiers en ne prenant en compte que leurs noms, leurs miniature et leur taille. Cependant, cette approche n’est pas évolutive lorsque le nombre de personnes impliquées et le nombre de ressources gérées augmentent. En outre, la valeur d’une ressource numérique augmente au fur et à mesure que la ressource devient :

* plus accessible : les systèmes et les utilisateurs peuvent la trouver facilement ;
* Plus facile à utiliser : vous disposez d’informations complètes sur les visuels des ressources et les informations connexes, afin de pouvoir agir plus rapidement et avec plus de confiance.
* Terminé : la ressource contient plus d’informations et de contexte.

## Conditions préalables {#prerequisites}

[Les utilisateurs de Content Hub](deploy-content-hub.md#onboard-content-hub-users) peuvent effectuer les actions mentionnées dans cet article.

## Aperçu de la ressource et de ses propriétés {#properties-ui}

Avant d’utiliser, de partager ou de télécharger une ressource, vous pouvez l’afficher pour en connaître les détails. La fonction d’aperçu vous permet d’afficher non seulement les images, mais également quelques autres types de ressources pris en charge. Vous pouvez non seulement afficher la ressource, mais également afficher ses informations détaillées et effectuer d’autres actions. Pour afficher les informations d’une ressource, accédez à la ressource ou [recherchez](search-assets.md) la ressource, puis cliquez sur la ressource pour ouvrir ses propriétés. La figure suivante illustre les champs disponibles sur une page de propriétés de ressource :

![Propriétés d’une interface utilisateur de ressource](assets/properties-ui.png)

* **A :** Titre d’une ressource
* **B :** Pourcentage de zoom ou d’aperçu de la ressource plus proche en effectuant un zoom avant ou arrière
* **C :** Annuler le zoom sur le pourcentage précédemment sélectionné
* **D :** Passez à la ressource précédente ou suivante
* **E :** Nombre Assets
* **F :** Télécharger la ressource
* **G :** Modifier une ressource à l’aide de [!DNL Adobe Express]
* **H:** Réduire ou prévisualiser les informations d’une ressource
* **I :** Partager la ressource
* **J:** Ajouter une ressource à [!DNL Collection]
* **K :** Fermer l’écran d’aperçu
* **L :** Informations d’une ressource qui incluent le titre, le format, la taille, la résolution, les balises, les balises de couleur et les balises intelligentes.

## Formats de ressources pris en charge {#supported-formats}

[!DNL Content Hub] prend en charge tous les types et formats de ressources pris en charge par le référentiel [!DNL Assets] sous-jacent. Le tableau suivant répertorie les formats de fichiers clés dans [!DNL the Content Hub], qui fournissent une prise en charge supplémentaire pour la prévisualisation visuelle des ressources :

<table> 
    <tbody>
     <tr>
      <th><strong>Type de fichier</strong></th>
      <th><strong>Formats pris en charge</strong></th>
     </tr>
     <tr>
      <td>Image</td>
      <td>
        <ul>
            <li>[!UICONTROL JPEG]</li> 
            <li>[!UICONTROL PNG]</li> 
            <li>[!UICONTROL SVG]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>Vidéo</td>
      <td>
        <ul>
            <li>[!UICONTROL Quicktime]</li>  
            <li>[!UICONTROL MP4]</li> 
        </ul>
      </td>
     </tr>
      <tr>
      <td>Document</td>
      <td>
        <ul>
            <li>[!UICONTROL txt] (brut)</li>  
            <li>[!UICONTROL Doc/Docx]</li> 
            <li>[!UICONTROL XML]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>Média d’impression</td>
      <td>
        <ul>
            <li>[!UICONTROL PDF]</li>  
        </ul>
      </td>
     </tr>  
    </tbody>
   </table>

### Propriétés dérivées {#derived-properties}

Certaines propriétés des ressources affichées dans [!DNL Content Hub] sont dérivées, ou générées automatiquement, lorsque les ressources sont chargées vers [!DNL Assets], puis approuvées pour disponibilité sur [!DNL Content Hub]. Voici une liste de certains d&#39;entre eux :

* **Taille :** La taille représente la taille du binaire de ressource stocké dans le référentiel sous-jacent.

<!--* **Tags:** Tags help you categorize assets that can be browsed and searched more efficiently. Tagging helps in propagating the appropriate taxonomy to other users and workflows. -->

* **Balises intelligentes :** [!DNL The Content Hub] utilise Adobe Sensei pour entraîner des ressources à l’aide d’un algorithme de reconnaissance sur la structure basée sur les balises. Cette intelligence de contenu est ensuite utilisée pour appliquer les balises pertinentes sur un ensemble de ressources différentes. Les balises intelligentes augmentent la vitesse du contenu de vos projets en vous aidant à trouver rapidement les ressources appropriées. Les balises intelligentes sont un exemple d’informations sur les ressources qui ne sont pas contenues dans l’image. [!DNL Experience Manager Assets] applique automatiquement des balises intelligentes aux ressources, par défaut.

* **Balises de couleur :** [ Les balises de couleur](#https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en) vous aident à reconnaître une ressource à l’aide de couleurs qui sont automatiquement identifiées dans une ressource à l’aide des fonctionnalités Sensei AI d’Adobe.

* Date du chargement

* Chargé par

* Dernière modification

* Dernière modification par

Certaines propriétés sont également spécifiées lors de l’ajout de ressources à Content Hub. Pour plus d’informations, voir [Ajout de ressources approuvées par la marque à Content Hub](upload-brand-approved-assets.md). Ces propriétés s’affichent également sur la page des propriétés de la ressource.

Les administrateurs peuvent également configurer les propriétés qui s’affichent pour chaque ressource :

* Dans l’interface utilisateur de prévisualisation des ressources : voir [Configuration de l’interface utilisateur de Content Hub](configure-content-hub-ui-options.md#configure-asset-details-content-hub).
* Sur les cartes de ressources dans les résultats de recherche ou les collections : voir [Configuration de l’interface utilisateur de Content Hub](configure-content-hub-ui-options.md#asset-card).

<!--

### Date range {#date-range} 

The date range allows you to select dates you want to see the assets. You can customize date range by choosing the start and end dates. 

-->
