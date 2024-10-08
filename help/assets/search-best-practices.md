---
title: Rechercher les bonnes pratiques pour  [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Bonnes pratiques pour rechercher, rechercher et récupérer les métadonnées des ressources dans votre application.
contentOwner: KK
exl-id: 446692de-5cea-4dbd-a98e-ec5177c7017e
feature: Best Practices
role: User
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '2542'
ht-degree: 8%

---

# Bonnes pratiques de recherche AEM Assets

| [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| --------------------------- |---------|----|-----|

[!DNL Adobe Experience Manager Assets] fournit des méthodes robustes de découverte de ressources qui vous aident à atteindre une vitesse de contenu plus élevée. Parfois, trouver la bonne ressource peut être ardu et chronophage. Par conséquent, la fonctionnalité de recherche de ressources dans [!DNL Adobe Experience Manager Assets] est essentielle à l’utilisation d’un système de gestion des ressources numériques, que ce soit pour une utilisation plus poussée par les créatifs, pour une gestion robuste des ressources par les utilisateurs professionnels et les marketeurs ou pour une administration par les administrateurs DAM.

Ce document d’aide contient AEM bonnes pratiques de recherche, à l’aide de divers scénarios, pour aider AEM utilisateurs à effectuer une recherche de base à avancée.

## Accès à la recherche d’Experience Manager {#access-experience-manager-search}

Vous trouverez ci-dessous les étapes de base à suivre dans Experience Manager avant de lancer votre recherche :

* Dans la **vue Admin**, accédez à Assets > Fichiers dans Experience Manager et cliquez sur l’icône de recherche dans la barre supérieure. Vous pouvez également utiliser une barre oblique (/) pour ouvrir le champ Omni Search.
Dans la **vue Assets**, la barre de recherche est visible en haut et est accessible directement.
* `Location:Assets` et `Path:/content/dam` sont pré-sélectionnés pour limiter la portée de la recherche à votre référentiel Experience Manager Assets. Si vous accédez à un autre dossier, `Path:/content/dam/<folder name>` s’affiche dans le champ Omni Search pour limiter la portée de la recherche au dossier actif.

## Recherche de base {#basic-search}

**Scénario 1 : effectuer une recherche de base à l’aide d’un `classic car` comme mot-clé de recherche.**

La recherche de mots-clés n’est pas sensible à la casse. Il s’agit d’une recherche de texte intégral dans les champs de métadonnées inclus dans l’index *recherche de texte intégral* de la ressource (configurable dans la définition d’index). Si plusieurs mots-clés sont utilisés, **AND est l’opérateur par défaut entre les mots-clés. Par conséquent, il considère qu’une recherche de &quot;voiture classique&quot; est &quot;voiture ET classique&quot;**.

Les résultats de recherche qui correspondent à tous les termes de recherche dans les champs de métadonnées s’affichent en premier, suivis des résultats de recherche correspondant à l’un des termes de recherche dans les balises intelligentes. L’ordre approximatif d’affichage des résultats de recherche est le suivant :

1. Correspondances de `Classic Car` dans les différents champs de métadonnées.
2. Correspondances de `Classic Car` dans les balises intelligentes.
3. Correspondances de `Classic` ou de `Car` dans les balises intelligentes.

Spécifiez `classic car` comme mot-clé de recherche et cliquez sur Rechercher. Vous pouvez afficher les suggestions de recherche dans une liste déroulante lorsque vous saisissez le mot-clé. Les suggestions de recherche sont basées sur le contenu de l’index de recherche sur votre déploiement Experience Manager. Si vous ne pouvez pas afficher les ressources appropriées dans le menu déroulant, appuyez sur la touche Entrée pour afficher la liste des résultats. Les résultats sont triés par pertinence, à partir des correspondances les plus proches.

<!--![Performing basic search method 1](assets/simple-search-1.png)-->

Vous pouvez rendre la recherche plus précise en ajoutant le mot-clé de recherche entre guillemets doubles (&quot;&quot;). Cette recherche inclut uniquement Assets qui contient les termes spécifiés ensemble. Les critères de recherche ressemblent à - `"classic car"`. Par conséquent, les résultats de la recherche avec les termes `classic` et `car` s’affichent.

<!--![Finding exact match](assets/simple-search-2.png)-->

La recherche affiche des résultats similaires si vous utilisez également la **[!UICONTROL vue Assets]**.

>[!VIDEO](https://video.tv.adobe.com/v/3425489)

## Fichiers et dossiers {#files-folders}

**Scénario 2 : recherchez tous les fichiers à l’aide du mot-clé `classic car` dans le dossier `automobile`.**

Le filtre Fichiers et dossiers vous aide à affiner votre recherche. Utilisez les options Fichiers, Dossiers ou Fichiers et Dossiers disponibles dans la liste déroulante en fonction de vos besoins. L’option de sélection parmi Fichiers, Dossiers ou Fichiers et Dossiers est accessible uniquement dans la **[!UICONTROL vue d’administration]**. Dans la **[!UICONTROL vue Assets]**, accédez à [!UICONTROL Chemin] et parcourez le dossier dans lequel vous souhaitez effectuer une recherche.

* Utilisez l’option **[!UICONTROL Files]** lorsque vous devez rechercher spécifiquement des fichiers à un chemin spécifique dans le référentiel. Vous n’avez pas besoin de rechercher des dossiers dans le chemin d’accès défini.
* Utilisez l’option **[!UICONTROL Dossiers]** lorsque vous devez limiter votre recherche aux dossiers à un chemin spécifique.
* Utilisez l’option **[!UICONTROL Fichiers et dossiers]** si vous devez rechercher toutes les ressources disponibles à l’emplacement spécifié dans le référentiel.

Pour réaliser ce scénario, procédez comme suit :

1. Spécifiez `classic car` comme mot-clé de recherche et cliquez sur Rechercher.
2. Cliquez sur Filtres et définissez le chemin du dossier du dossier `automobile`. Par exemple, `/content/dam/multiple-assets/automobile`
Sélectionnez le dossier à partir du chemin d’accès et accédez au dossier requis si vous souhaitez effectuer des recherches dans le dossier spécifique.
3. Sélectionnez Fichiers dans la liste déroulante pour afficher tous les fichiers avec le mot-clé `classic car`.

<!--![Search using files and folders](assets/files-folders.png)-->

>[!VIDEO](https://video.tv.adobe.com/v/3425487)

## Opérateurs  {#operators}

**Scénario 3 : recherchez des mots-clés `Classic Car` ou `Car` à l’aide de diverses combinaisons d’opérateurs pour affiner votre recherche.**

Pour exécuter le scénario ci-dessus dans la **[!UICONTROL vue d&#39;administration]**, vous pouvez utiliser une combinaison de divers opérateurs pour améliorer votre expérience de recherche. Les opérateurs pris en charge sont les suivants :

### Opérateur ET {#and-operator}

L’opérateur AND est l’opérateur par défaut entre deux mots-clés dans la recherche Omni. Par exemple, lorsque vous tapez `classic car` dans la barre de recherche, les résultats avec les mots-clés `classic` et `car` apparaissent dans les résultats de la recherche, par défaut.

![Recherche à l’aide de l’opérateur ET](assets/simple-search-1.png)

### Opérateur OU {#or-operator}

Lorsque vous souhaitez être spécifique aux résultats de la recherche et qu’une option doit apparaître dans les résultats de la recherche, vous pouvez utiliser l’opérateur OU. Par exemple, le mot-clé `classic OR car` fournit les résultats de recherche avec l’un des mots-clés de leurs métadonnées.

![Recherche à l’aide de l’opérateur OU](assets/or-operator.png)

### opérateur NOT {#not-operator}

Lorsque vous souhaitez récupérer des résultats, à l’exclusion de certains mots-clés, vous pouvez utiliser l’opérateur SAUF . L’opérateur SAUF utilise le trait d’union (-) pour diriger AEM recherche sur les éléments à exclure des résultats de la recherche. Par exemple, la requête de recherche `car - classic` qui spécifie les métadonnées qui contiennent `car` mais exclut `classic`.

![Recherche à l’aide de l’opérateur NOT](assets/not-operator.png)

De même, vous pouvez rechercher toutes les voitures, mais pas les jeep. La requête ressemble à : `car - jeep`. Il affiche toutes les ressources avec des métadonnées `car` mais exclut les ressources avec des métadonnées `jeep`.

![Recherche à l’aide de l’opérateur NOT](assets/images-jeep.png)

**[!UICONTROL La vue Assets]** ne prend pas en charge l’utilisation des opérateurs.

## Caractères génériques {#wildcards}

Les caractères génériques sont utilisés pour remplacer un ou plusieurs caractères dans la recherche. Pour exécuter le scénario ci-dessus dans la **[!UICONTROL vue d’administration]**, vous pouvez utiliser une combinaison de différents caractères génériques pour améliorer votre expérience de recherche. Deux caractères génériques sont utilisés pour effectuer la recherche - Point d’interrogation (?) et astérisque (*). Le symbole du point d’interrogation permet de rechercher un seul caractère, tandis que le symbole de l’astérisque permet de rechercher plusieurs caractères.

### Point d’interrogation (?) {#question-mark}

Le symbole du point d’interrogation peut être utilisé comme opérateur conditionnel pour faciliter votre recherche dans Experience Manager.

* La requête `car?` correspond au mot avec un caractère après la voiture. Par exemple, panier.
* La requête `?car` correspond au mot avec un caractère avant la voiture. Par exemple, cicatrice.
* La requête `car????` correspond au mot avec quatre caractères après la voiture. Par exemple, lessive à la voiture.

### Astérisque (*) {#asterisk}

L’astérisque est un opérateur de caractères génériques utilisé pour élargir votre recherche en tapant moins de caractères. Lorsque vous connaissez les caractères de départ de la ressource que vous recherchez, mais que vous ne connaissez pas le reste, vous pouvez utiliser l’opérateur astérisque dans votre recherche. Par exemple, la requête `*car` renvoie toutes les ressources avec la voiture de correctif disponible dans leurs métadonnées. Les résultats peuvent être des voitures classiques, des voitures de sport, des voitures classiques et sportives, etc. Vous trouverez ci-dessous quelques exemples d’utilisation de l’opérateur astérisque de différentes manières :

* `*car*` renvoie toutes les combinaisons possibles.
* `car*` renvoie des ressources avec lessive, opérateur, transport, etc.
* `*car` renvoie des ressources avec une voiture moderne, une voiture de sport, etc.

>[!VIDEO](https://video.tv.adobe.com/v/3425488)

**[!UICONTROL La vue Assets]** ne prend pas en charge l’utilisation des caractères génériques.

## Filtres {#filters}

Adobe Experience Manager fournit divers filtres de recherche que vous pouvez utiliser pour affiner et segmenter votre recherche à l’aide d’une requête étendue. Lorsque vous n’êtes pas certain du titre ou de la méta-description d’une ressource, vous pouvez utiliser divers filtres de recherche pour rendre votre recherche plus pertinente. Vous pouvez utiliser des filtres de recherche avec ou sans saisir de mot-clé. Pour ouvrir le panneau des filtres dans la **[!UICONTROL vue d’administration]**, cliquez sur l’icône **de navigation globale** et sélectionnez **[!UICONTROL Filtres]**. En revanche, pour ouvrir le panneau des filtres dans la **[!UICONTROL vue Assets]**, cliquez sur [!UICONTROL Filtres] en regard de la barre de recherche.

![Panneau Filtres](assets/filters.png)

Vous pouvez sélectionner un ou plusieurs filtres pour affiner votre recherche dans Adobe Experience Manager.
<!--The following filters are available out of the box for all the users of Experience Manager:

* File Type Search Filters  
* File Size Search Filters 
* Date of Creation 
* Created by 
* Last Modified date 
* Last Modified by 
* Search by Language 
* Search by Status 
* Search based on Orientation 
* Search by Style 
* Search based on insights 
* Search by Adobe Stock 
* Color specific Asset search 
* Content fragment model 
 -->

<!--**Scenario 5: Search for an Asset named 'classic car' in Black color which has either meta description or a similar asset in Japanese language.**  
 
To perform a search on such a requirement, type 'classic car' in the search bar.  Navigate to the filters panel and expand the language search filter drop-down. Type "ja-jp", which represents the Japanese language. Expand the 'Asset Color' filter and select black color or add the hexadecimal code for the black color (#000000).

![Filter example 1](assets/filter-1.png)
-->

**Scénario 4 : recherche de documents de type de fichier de PDF non publiés contenant le mot-clé `classic car`.**

Exécutez les étapes suivantes dans **[!UICONTROL Admin view]** :

1. Saisissez `classic car` dans la barre de recherche.
1. Accédez à Filtres. Sous [!UICONTROL Type de fichier], développez [!UICONTROL Documents], puis développez [!UICONTROL Traitement de texte].
1. Sélectionnez [!UICONTROL PDF].
1. Accédez à [!UICONTROL Status] > [!UICONTROL Publish] > [!UICONTROL Unpublish].

<!--![Filter example 2](assets/filter-2.png)-->

Exécutez les étapes suivantes dans la **[!UICONTROL vue Assets]** :

1. Saisissez `classic car` dans la barre de recherche.
1. Accédez à Filtres. Sous [!UICONTROL MIME Type], sélectionnez [!UICONTROL PDF].
1. Accédez à [!UICONTROL Asset Status], sélectionnez [!UICONTROL All] pour inclure toutes les ressources publiées et non publiées.

**Scénario 5 : recherche de toutes les images à l’exception de PNG**

Lorsque vous n’êtes pas certain du titre ou de la méta-description d’une ressource, vous pouvez utiliser divers filtres de recherche pour rendre votre recherche plus pertinente. Par exemple, pour rechercher des ressources dans **[!UICONTROL Vue d&#39;administration]**, procédez comme suit :

1. Accédez aux filtres de recherche.
1. Accédez à Filtres. Sous [!UICONTROL Type de fichier], développez [!UICONTROL Images] et sélectionnez [!UICONTROL Web enabled]
1. Désélectionnez PNG.

<!--![Search all images except jeep](assets/images-png.png)-->

Pour rechercher des ressources à l’aide du scénario mentionné dans la **[!UICONTROL vue Assets]**, procédez comme suit :

1. Accédez aux filtres de recherche.
1. Accédez à Filtres. Sous [!UICONTROL MIME Type], sélectionnez tous les types MIME donnés, mais désélectionnez PNG.

>[!VIDEO](https://video.tv.adobe.com/v/3425486)

## Recherche avancée {#advanced-search}

AEM recherche vous permet de concevoir des requêtes de recherche complexes avec moins d’effort. Vous trouverez ci-dessous différents exemples pour vous aider à créer des requêtes de recherche complexes :

**Scénario 6 : recherchez tous les documents du référentiel Experience Manager avec `classic car` dans leurs métadonnées. Le contenu du document doit contenir le mot-clé `classic car`.**

Adobe Experience Manager vous permet d’ajouter plusieurs critères à votre recherche. Vous pouvez utiliser une combinaison de mots-clés, d’opérateurs et de filtres pour affiner vos résultats de recherche.

Pour effectuer une recherche dans le scénario 6 :

1. Saisissez le mot-clé `classic car` dans la barre de recherche.
2. Accédez au panneau Filtres et sélectionnez Documents sous Type de fichier.
3. Affinez votre recherche à l’aide du caractère générique astérisque. Saisissez `"classic car"` pour rechercher toutes les ressources contenant le mot-clé `classic car`.

<!--![Scenario 6](assets/scenario-6.png)-->

Le scénario 6 ne peut pas s’exécuter dans **[!UICONTROL vue Assets]**, car il ne prend pas en charge l’utilisation de caractères génériques.

**Scénario 7 : recherchez tous les documents du référentiel Experience Manager dans lesquels le contenu du document doit inclure `car` mais exclure `classic`. La même condition s&#39;applique aux métadonnées d&#39;une ressource.**

Pour effectuer une recherche dans le scénario 7 :

Saisissez le mot-clé `car - classic` dans la barre de recherche. Accédez au panneau Filtres et sélectionnez Documents sous Type de fichier. L’ordre de priorité de la recherche est basé sur les éléments suivants :
Priorité 1 : Métadonnées
Priorité 2 : balises intelligentes

<!--![Scenario 7](assets/scenario-7.png)-->

Le scénario 7 ne peut pas s’exécuter dans **[!UICONTROL vue Assets]**, car il ne prend pas en charge l’utilisation de caractères génériques.

<!--
**Scenario 9: Search for all images except PNG**

When you are unsure about the title or meta description of an asset, you can use various search filters to make your search more relevant. Follow the steps below:

1. Go to search filters. 
1. Under [!UICONTROL File Type], expand [!UICONTROL Images] and select [!UICONTROL Web enabled]
1. Deselect PNG.

**Method 1:** Go to search bar and type `images - PNG`. All the images appear excluding PNG.

**Method 2:** Go to search filters. Under [!UICONTROL File Type], expand [!UICONTROL Images] > select [!UICONTROL Web enabled] > deselect PNG.

![Search all images except jeep](assets/images-jeep.png)
-->

**Scénario 8 : recherche de balises de métadonnées avec jeep de métadonnées**

Vous pouvez capturer un critère spécifique à l’aide de différents filtres de recherche. Tag est un mot-clé attribué à une ressource afin de l’identifier parmi un grand nombre de ressources. Par exemple, dans ce scénario, recherchez des ressources contenant des balises *jeep*. Pour ce faire, saisissez `tags:jeep` dans la barre de recherche. Seules les ressources qui répondent à ces critères sont répertoriées dans les résultats de recherche.

<!--![Search using tags](assets/search-tags.png)-->

La recherche affiche des résultats similaires si vous utilisez également la **[!UICONTROL vue Assets]**.

>[!VIDEO](https://video.tv.adobe.com/v/3425490)

**Scénario 9 : rechercher une correspondance similaire pour la voiture couleur rouge**

Lors de l’exécution de votre recherche sur AEM, vous pouvez filtrer vos résultats en affichant des ressources similaires aux ressources sélectionnées. Vous pouvez utiliser l’option **Rechercher des ressources similaires** pour restreindre votre recherche à la correspondance exacte ou similaire de la ressource recherchée. Cela permet de rechercher des ressources qui ont des balises intelligentes similaires à la ressource sélectionnée. Par exemple, pour rechercher des ressources similaires, procédez comme suit :

1. Recherchez la ressource selon vos besoins.
1. Passez la souris sur la ressource > cliquez sur les points de suspension > sélectionnez [!UICONTROL Rechercher des éléments similaires].
ou
Sélectionnez la ressource > accédez aux points de suspension en haut à droite > sélectionnez [!UICONTROL Rechercher des éléments similaires].

   ![Trouver similaire](assets/find-similar.png)

1. Remarquez la barre de recherche. La miniature de la ressource sélectionnée s’affiche dans la barre de recherche pour indiquer vos besoins en termes de recherche. Par conséquent, elle renvoie les ressources avec des balises intelligentes similaires.

Exécutez les étapes suivantes dans la **[!UICONTROL vue Assets]** :

1. Recherchez la ressource selon vos besoins.
1. Sélectionnez l’image > accédez à l’option [!UICONTROL Rechercher une image similaire] dans la barre de navigation supérieure.
Vous accédez alors à la collection de ressources avec des couleurs et des métadonnées similaires.

## Facettes de recherche personnalisées {#custom-search-facets}

Les facettes de recherche de Adobe Experience Manager vous permettent de rechercher des ressources de plusieurs manières plutôt que dans un seul ordre taxonomique, prédéterminé ou prédéfini. Vous pouvez personnaliser les facettes de recherche et ajouter des prédicats selon vos besoins. Lisez [Facettes de recherche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/search-facets.html?lang=en#) pour consulter le guide détaillé sur l’ajout d’un prédicat personnalisé.

<!--**Scenario 10: Search assets based on Sku ID**
to be added later
-->

**Scénario 10 : recherche de ressources spécifiques en fonction de leur date de dernière modification ou d’expiration**

Les contraintes de date vous permettent de réduire votre recherche personnalisée à une période spécifique, en utilisant par exemple les filtres de recherche de période. Pour rechercher la condition ci-dessus, saisissez `classic car` dans la barre de recherche. Sélectionnez la période dans les filtres de dates [!UICONTROL Date de création] et [!UICONTROL Dernière modification].

![Filtres de date](assets/date-filters.png)

La recherche affiche des résultats similaires si vous utilisez également la [!UICONTROL vue Assets].

## Renforcer la pertinence des mots-clés {#boosting-keywords}

Vous pouvez améliorer la pertinence des mots-clés pour des ressources particulières afin d’améliorer les recherches basées sur les mots-clés. En d’autres termes, les images pour lesquelles vous convertissez des mots-clés spécifiques apparaissent en haut des résultats de la recherche lorsque vous effectuez une recherche en fonction de ces mots-clés.

1. Dans l’interface utilisateur d’Assets, ouvrez la page des propriétés de la ressource. Cliquez sur [!UICONTROL Avancé] et cliquez sur [!UICONTROL Ajouter] sous [!UICONTROL Élever pour les mots-clés de recherche].
2. Dans la zone Rechercher une promotion , indiquez un mot-clé pour lequel vous souhaitez améliorer la recherche d’image, puis cliquez sur [!UICONTROL Ajouter]. Vous pouvez indiquer plusieurs mots-clés de la même manière.
3. Cliquez sur [!UICONTROL Enregistrer et fermer]. La ressource pour laquelle vous avez promu ce mot-clé apparaît en tête des résultats de recherche.

## Éléments notables lors de l’exécution d’une recherche dans Experience Manager {#notable-things}

* Fournissez les informations de métadonnées de la ressource pour préparer votre ressource pouvant faire l’objet de recherches par l’algorithme Omni Search. Vérifiez que les informations de métadonnées de la ressource sont mises à jour.
* Utilisez des guillemets doubles (&quot;&quot;) pour rendre votre recherche exacte et pertinente.
* Effectuez une vérification croisée du chemin d’accès que vous recherchez. Sélectionnez l’option appropriée parmi le dossier, le fichier ou le fichier et le dossier pour exécuter votre requête à l’emplacement approprié.
* Vous pouvez vérifier les filtres que vous appliquez à votre recherche dans la barre Omni Search.
* Si vous n’obtenez aucun résultat, vérifiez le chemin que vous recherchez. Vérifiez également le dossier à partir duquel vous effectuez votre recherche. Par exemple, si vous effectuez une recherche dans le &quot;dossier Automobile&quot; mais que le mot-clé que vous utilisez est lié à &quot;Vêtements&quot;, les résultats de la recherche ne sont pas appropriés.
* Vérifiez si vous avez ajouté un espace blanc avant le mot-clé que vous recherchez.
* L’utilisation d’un mélange et d’une correspondance de mots-clés, d’opérateurs et de filtres peut faciliter et améliorer votre expérience de recherche.

<!--
* Use stemming search approach while searching for the asset. It means using an exact keyword that you are looking for.
* Specify Smart tags to the asset properties to boost the ranking of the search results.
The newly added assets are not indexed.
-->

## Différences entre la [!UICONTROL vue d’administration] et la [!UICONTROL vue Assets] Rechercher {#differences-asset-and-admin-view}

<table>
    <tr>
        <th> Paramètres </th>
        <th> Vue Admin </th>
        <th> Vue Assets </th>
    </tr>
    <tr>
        <td> Facettes personnalisées </td>
        <td> Vous pouvez ajouter <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/search-facets.html?lang=fr">des facettes de recherche personnalisées en fonction des besoins.</td>
        <td> Les facettes personnalisées sont partiellement prises en charge dans la vue Assets. Les facettes prises en charge sont les suivantes :
            <ul>
            <li> Balises prédites
            <li> Nom
            <li> Confiance des balises prédites
            <li> Taille des ressources
            <li> Titre
            </ul>
        </td>
    </tr>
    <tr>
        <td> Opérateurs  </td>
        <td> Prend en charge AND, OR et NOT </td>
        <td> Pas de prise en charge </td>
    </tr>
    <tr>
        <td> Caractères génériques </td>
        <td> Prend en charge le point d’interrogation (?) et astérisque (*).</td>
        <td> Pas de prise en charge </td>
    </tr>
    <tr>
        <td> Amélioration des résultats de recherche </td>
        <td> Pris en charge </td>
        <td> Pas de prise en charge </td>
    </tr>
     <tr>
        <td> Effacer tous les filtres à la fois </td>
        <td> Pas de prise en charge </td>
        <td> Pris en charge</td>
    </tr>
     <tr>
        <td> Fichiers/Dossiers/Fichiers et dossiers </td>
        <td> Pris en charge </td>
        <td> Une option permettant de sélectionner un dossier est disponible sous "Type de fichier". </td>
    </tr>
     <tr>
        <td> Statut de la ressource </td>
        <td> 
            Les options prises en charge sont les suivantes :
            <ul>
            <li> Publier
            <li> Date de publication
            <li> Dernière publication par
            <li> Approbation 
            <li> Passage en caisse
            <li> Expiration
            <li> Dynamic Media
            </ul>
        </td>
        <td>
        Les options prises en charge sont les suivantes :
            <ul>
            <li> Tous
            <li> Approuvé
            <li> Refusé
            <li> Aucun statut
            </ul> 
        </td>
    </tr>
     <tr>
        <td> Type de fichier </td>
        <td>
        Les options prises en charge sont les suivantes :
            <ul>
            <li> Images
            <li> Documents
            <li> Multimédia
            <li> Archives 
            </ul>
            Elles comportent d’autres options hiérarchiques.
        </td>
        <td>
        Les options prises en charge sont les suivantes :
            <ul>
            <li> Images
            <li> Documents
            <li> Vidéo
            <li> Dossier 
            </ul> 
        D’autres options sont répertoriées sous le type MIME.
        </td>
    </tr>
     <tr>
        <td> Taille du fichier </td>
        <td>
        Les options prises en charge sont les suivantes :
            <ul>
            <li> De - À
            <li> Taille (octets, Ko, Mo, Go)
            </ul> 
        </td>
        <td> Pas de prise en charge </td>
    </tr>
     <tr>
        <td> Autres filtres </td>
        <td>
            <ul>
            <li> Langue
            <li> Statut
            <li> Orientation
            <li> Style 
            <li> Insights
            <li> Stock
            <li> Couleur de ressource
            <li> Modèle de fragment de contenu
            </ul> 
        </td>
        <td> Pas de prise en charge </td>
    </tr>
</table>

>[!MORELIKETHIS]
>
>* [Recherche de ressources](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/search-assets.html?lang=fr)
>* [Facettes de recherche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/search-facets.html?lang=fr)
