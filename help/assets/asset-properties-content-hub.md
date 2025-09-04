---
title: Aperçu de la ressource et de ses propriétés dans  [!DNL the Content Hub]
description: Découvrez comment prévisualiser des ressources et des propriétés dans  [!DNL Content Hub]
role: User
exl-id: a85af980-4c51-4d30-9fad-afd16370e9db
source-git-commit: 45e731d2286b07db5852138ae1ac914a56b13a6a
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 11%

---

# Aperçu de la ressource et de ses propriétés dans Content Hub {#asset-properties}

![Image de bannière de métadonnées](assets/metadata-banner-image.png)

[!DNL The Content Hub] vous permet d’afficher des informations sur la ressource, ce qui est essentiel pour une distribution efficace des ressources. Il s’agit de la collecte de toutes les données disponibles pour une ressource.

L’affichage de l’aperçu des ressources et de ses propriétés vous permet de classer les ressources de manière plus détaillée à mesure que le volume d’informations numériques augmente. Il est ainsi possible de gérer quelques centaines de fichiers en ne prenant en compte que leurs noms, leurs miniature et leur taille. Toutefois, cette approche n’est pas évolutive lorsque le nombre de personnes impliquées et le nombre de ressources gérées augmentent. En outre, la valeur d’une ressource numérique augmente à mesure que la ressource devient :

* plus accessible : les systèmes et les utilisateurs peuvent la trouver facilement ;
* Action plus facile : vous disposez d’informations complètes sur les visuels des ressources et les informations connexes, afin d’agir plus rapidement et avec plus de confiance.
* Terminé : la ressource apporte plus d’informations et de contexte.

## Prérequis {#prerequisites}

[Les utilisateurs de Content Hub](deploy-content-hub.md#onboard-content-hub-users) peuvent effectuer les actions mentionnées dans cet article.

## Aperçu de la ressource et de ses propriétés {#properties-ui}

Avant d’utiliser, de partager ou de télécharger une ressource, vous pouvez l’afficher pour en connaître les détails. La fonction d’aperçu vous permet d’afficher non seulement les images, mais également quelques autres types de ressources pris en charge. Vous pouvez non seulement afficher la ressource, mais également afficher ses informations détaillées et effectuer d’autres actions. Pour afficher les informations d’une ressource, accédez à la ressource ou [recherchez](search-assets.md) puis cliquez sur la ressource pour ouvrir ses propriétés. La figure suivante illustre les champs disponibles sur une page de propriétés de ressource :

![Propriétés d’une interface utilisateur de ressource](assets/properties-ui.png)

* **A:** Titre d’une ressource
* **B :** pourcentage de zoom ou de prévisualisation de la ressource avec un zoom avant ou arrière
* **C:** Annuler le zoom sur le pourcentage sélectionné précédemment
* **D :** passer à la ressource précédente ou suivante
* **E:** Nombre d’Assets
* **F :** Télécharger la ressource
* **G :** modification de ressource à l’aide de [!DNL Adobe Express]
* **H:** réduire ou prévisualiser les informations d’une ressource ;
* **I:** Partager la ressource
* **J:** Ajouter une ressource à [!DNL Collection]
* **K:** Fermer l’écran d’aperçu
* **L:** Informations sur une ressource qui incluent le titre, le format, la taille, la résolution, les balises, les balises de couleur et les balises intelligentes.

## Formats de ressources pris en charge {#supported-formats}

[!DNL Content Hub] prend en charge tous les types et formats de ressources pris en charge par le référentiel [!DNL Assets] sous-jacent. Le tableau suivant répertorie les formats de fichiers clés dans [!DNL the Content Hub], qui offrent une prise en charge supplémentaire de la prévisualisation visuelle des ressources :

<table> 
    <tbody>
     <tr>
      <th><strong>Type de fichier</strong></th>
      <th><strong>Formats pris en charge</strong></th>
     </tr>
     <tr>
        <td rowspan="3"> Image </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL JPEG]</td>
    </tr>
    <tr>
        <td>[!UICONTROL PNG]</td>
    </tr>
    <tr>
        <td rowspan="4"> Vidéo </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL Quicktime]</td>
    </tr>
    <tr>
        <td>[!UICONTROL MP4]</td>
    </tr>
    <tr>
        <td>[!UICONTROL MPEG]</td>
    </tr>
    <tr>
        <td rowspan="4"> Document </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL txt] (brut)</td>
    </tr>
    <tr>
        <td>[!UICONTROL Doc/Docx]</td>
    </tr>
    <tr>
        <td>[!UICONTROL XML]</td>
    </tr>
    <tr>
        <td rowspan="2"> Média imprimé </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL PDF]</td>
    </tr>
    </tbody>
</table>

### Propriétés dérivées {#derived-properties}

Certaines propriétés des ressources affichées dans [!DNL Content Hub] sont dérivées ou générées automatiquement lorsque des ressources sont chargées vers [!DNL Assets], puis approuvées pour disponibilité sur [!DNL Content Hub]. Voici une liste de certains d’entre eux :

* **Taille:** Taille représente la taille du fichier binaire de ressource stocké dans le référentiel sous-jacent.

<!--* **Tags:** Tags help you categorize assets that can be browsed and searched more efficiently. Tagging helps in propagating the appropriate taxonomy to other users and workflows. -->

* **Balises intelligentes :** [!DNL The Content Hub] utilise les services de contenu dynamique d’Adobe Sensei pour entraîner des ressources à l’aide de l’algorithme de reconnaissance sur la structure basée sur les balises. Cette intelligence de contenu est ensuite utilisée pour appliquer les balises pertinentes sur un ensemble de ressources différentes. Les balises intelligentes augmentent la vitesse du contenu de vos projets en vous permettant de trouver rapidement les ressources appropriées. Les balises intelligentes sont un exemple d’informations de ressource qui ne sont pas contenues dans l’image. [!DNL Experience Manager Assets] applique automatiquement les balises intelligentes aux ressources, par défaut.

* **Balises de couleurs :** [Balises de couleurs](#https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en) permet de reconnaître une ressource à l’aide de couleurs automatiquement identifiées dans une ressource à l’aide des fonctionnalités d’IA d’Adobe Sensei.

* Date du chargement

* Chargé par

* Dernière modification

* Dernière modification par

Certaines propriétés sont également spécifiées lors de l’ajout de ressources à Content Hub. Pour plus d’informations, voir [Ajout de ressources approuvées par la marque à Content Hub](upload-brand-approved-assets.md). Ces propriétés sont également affichées sur la page des propriétés de la ressource.

L’administration peut également configurer les propriétés affichées pour chaque ressource :

* Dans l’interface utilisateur de prévisualisation de la ressource : consultez [Configuration de l’interface utilisateur de Content Hub](configure-content-hub-ui-options.md#configure-asset-details-content-hub).
* Sur les cartes de ressources dans les résultats de recherche ou les collections : consultez [Configuration de l’interface utilisateur de Content Hub](configure-content-hub-ui-options.md#asset-card).

<!--

### Date range {#date-range} 

The date range allows you to select dates you want to see the assets. You can customize date range by choosing the start and end dates. 

-->
