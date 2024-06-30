---
title: Recherche de ressources dans Content Hub
description: Découvrez comment rechercher des ressources dans [!DNL Content Hub]
role: User
source-git-commit: 5a968440c8841abe7af2c81c4af12258b7e4547f
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---


# Rechercher dans Assets dans [!DNL Content Hub] {#search-assets}

![Image de la bannière de ressources](assets/search.png)

Lorsque votre référentiel contient un grand nombre de ressources, la recherche de la ressource appropriée prend du temps. [!DNL The Content Hub] search vous permet de rechercher les ressources approuvées afin que vous puissiez y effectuer des actions supplémentaires, telles que télécharger, partager ou créer des collections. Vous pouvez utiliser différentes fonctionnalités pour affiner vos résultats de recherche, par exemple, en effectuant une recherche textuelle à l’aide de filtres, en effectuant une recherche par balises intelligentes ou par balises intelligentes, en recherchant un format de fichier particulier, etc.

## Conditions préalables {#prerequisites}

[Utilisateurs de Content Hub](deploy-content-hub.md#onboard-content-hub-users) peuvent effectuer les actions mentionnées dans cet article.

## Ce que vous pouvez rechercher  {#what-you-can-search}

La variable [!DNL Content Hub] La recherche fournit des résultats basés sur :

* **Texte correspondant :** La variable [!DNL Content Hub] search vous permet de rechercher une ressource à l’aide de son nom ou de sa description. Vous pouvez effectuer une recherche par mot-clé, qui compare le mot-clé au texte disponible dans les propriétés d’une ressource.

* **Contexte de correspondance :** [!DNL Content Hub] la liste des résultats de recherche contient les résultats immédiats des ressources que vous obtenez en fonction du contexte correspondant. Par exemple, si vous saisissez `cool` dans la barre de recherche, les ressources liées à `winter`, `snow`, `cold surroundings`, s’affiche dans la liste de recherche.

* **Informations sur les ressources (titre, balises ou balises intelligentes) :** [!DNL Content Hub] utilise l’algorithme de recherche dynamique pour classer les résultats de recherche avec précision et autant de pertinence que possible. [Métadonnées](#asset-properties.md) est la collecte de toutes les données disponibles pour une ressource, mais elles ne sont pas nécessairement contenues dans cette ressource. [Il vous aide à classer les ressources de manière plus détaillée et s’avère utile à mesure que la quantité d’informations numériques augmente.](/help/assets/configure-content-hub-ui-options.md##configure-metadata-search-content-hub).

* **Date de dernière modification :** Les ressources qui ont été modifiées récemment apparaissent en haut de la liste des résultats de recherche. Vous pouvez également filtrer la période selon vos besoins.

* **Utilisation :** Les ressources fréquemment utilisées apparaissent en haut de la liste de recherche.

* **Historique de recherche :** Cliquez dans la zone de recherche sans saisir de caractère pour obtenir votre historique de recherche. Vous pouvez également supprimer un mot-clé particulier de l’historique. L’historique de recherche est enregistré dans la mémoire cache d’un navigateur web, ce qui signifie que si vous accédez à la variable [!DNL Content Hub] effectuer une recherche dans un autre navigateur ou effacer la mémoire cache du navigateur, vous ne pouvez plus afficher l’historique de recherche.

* **Effectuez une recherche lorsque vous tapez :** La variable [!DNL Content Hub] la recherche améliore votre expérience de recherche en fournissant des suggestions de saisie automatique dès que vous commencez à saisir du texte.

## Recherche de base {#basic-search}

Pour effectuer une recherche de base sur [!DNL the Content Hub], accédez à la barre de recherche et spécifiez le mot-clé à rechercher. Accédez aux filtres disponibles dans le volet de gauche et appliquez-les pour affiner les résultats de la recherche.

Par exemple, recherchez toutes les **[!UICONTROL JPEG]** images avec mot-clé `architect` dans , qui est modifié au cours de l’année écoulée. Pour exécuter ce scénario, procédez comme suit :

1. Spécifier `architect` comme mot-clé de recherche.

1. Accédez au panneau Filtres > **[!UICONTROL Format]** > sélectionner **[!UICONTROL JPEG]**.

1. Accédez à **[!UICONTROL Modifié]** > indiquez la période.

   ![Recherche de base](assets/basic-search.png)

## Limitation des résultats de recherche à l’aide de filtres {#narrow-down-search-results}

Utilisez le panneau Filtres pour rechercher des ressources en fonction des métadonnées. Vous pouvez filtrer les résultats de recherche en fonction de différents prédicats de recherche. Vous pouvez sélectionner tous les prédicats appropriés pour réduire ou réduire les résultats de recherche. Lorsque vous sélectionnez plusieurs options dans un filtre, Content Hub affiche les ressources qui correspondent à l’une des options sélectionnées dans un filtre. Cependant, lorsque vous sélectionnez plusieurs options sur plusieurs filtres, Content Hub affiche uniquement les ressources qui correspondent à toutes les options sélectionnées sur plusieurs filtres pour réduire les résultats de la recherche.

Les filtres par défaut incluent le format de fichier, l’approbation, la date d’approbation, les ressources expirées et non expirées, ainsi que la date d’expiration. Les administrateurs peuvent également configurer les filtres qui s’affichent dans la liste des filtres. Pour plus d’informations, voir [Configuration de l’interface utilisateur de Content Hub](configure-content-hub-ui-options.md#configure-filters-content-hub).

<!--

<table>
    <tbody>
     <tr>
      <th><strong>Search Predicate</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Properties</strong></th>
     </tr>
     <tr>
      <td> Campaigns </td>
      <td> Allows you to search using planned activity performed to take any particular action. For example, advertisement campaign run on Ferrari to know the understand the interests of people using number of clicks people perform.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Channels </td>
      <td> Helps you to understand the path from where the asset is coming from. For example, web, social media, books, catalog, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Region </td>
      <td> Helps you to understand the location where the asset is created. For example, Japan, EMEA, Worldwide, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Keywords </td>
      <td> Keyword helps you search using terms or the words that you enter based on the topic. For example, images, low-resolution, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Timeframe </td>
      <td> Helps you search assets using timeline. For example, search by year 2024, Q3 2023, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td>File format</td>
      <td>Composition of an asset. The supported assets include image, document, video, printable media, and so on.</td>
      <td>
        <ul>
            <li>[!UICONTROL JPEG]</li> 
            <li>[!UICONTROL Quicktime]</li> 
            <li>[!UICONTROL PNG]</li> 
            <li>[!UICONTROL WebP]</li> 
            <li>[!UICONTROL MP4]</li> 
            <li>[!UICONTROL Plain]</li> 
            <li>[!UICONTROL PDF]</li>
            <li>[!UICONTROL SVG + XML]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>Tags</td>
      <td>Tags help you categorize assets that can be browsed and searched more efficiently based on hierarchical taxonomies.</td>
      <td>
        <ul>
            <li>Field label</li>
            <li>Property name</li>
            <li>Path</li>
            <li>Description</li>
        </ul>
      </td>
     </tr>
     <!--<tr>
      <td>Subject</td>
      <td>Classification of assets based on their theme. For example, colorful, hiking, outdoors.</td>
      <td>NA</td>
     </tr>
          <tr>
      <td>Last modified</td>
      <td>Search assets based on their last modification. Specify the date range using the Start date and End date fields.</td>
      <td>
        <ul>
            <li>Range text (From)</li> 
            <li>Range text (To) </li>
        </ul>
      </td>
     </tr>    
     <!--<tr>
      <td>Asset ID</td>
      <td>Unique number that identifies the asset.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Colors </td>
      <td> Helps you search assets using colors that are automatically identified in an asset using Adobe's Sensei AI capabilities.</td>
      <td>NA</td>
     </tr>  
    </tbody>
   </table>

-->

## En savoir plus sur la recherche {#do-more-with-search}

[!DNL The Content Hub] ne se limite pas à la recherche ; il vous permet d’effectuer d’autres actions, telles que [télécharger](download-assets-content-hub.md), [share](share-assets-content-hub.md), et [ajouter des ressources à la collection](collections-content-hub.md), directement depuis l’interface de recherche ou de prévisualisation. Sélectionnez les ressources de la page des résultats de recherche pour afficher ces options.
