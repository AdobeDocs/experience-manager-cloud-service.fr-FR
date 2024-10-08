---
title: Sélecteur de ressources pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Utilisez le sélecteur de ressources pour rechercher, rechercher et récupérer les métadonnées et les rendus des ressources dans votre application.
role: Admin, User
exl-id: 62b0b857-068f-45b7-9018-9c59fde01dc3
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1332'
ht-degree: 34%

---

# Sélecteur de ressources micro front-end {#Overview}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Le sélecteur de ressources micro front-end fournit une interface utilisateur qui s’intègre facilement au référentiel [!DNL Experience Manager Assets] afin que vous puissiez parcourir ou rechercher des ressources numériques disponibles dans le référentiel et les utiliser dans votre expérience de création d’applications.

L’interface utilisateur micro front-end est mise à disposition dans votre expérience de l’application à l’aide du package Sélecteur de ressources. Toutes les mises à jour du package sont automatiquement importées et le dernier sélecteur de ressources déployé est automatiquement téléchargé dans votre application.

![Présentation](assets/overview.png)

Le sélecteur de ressources offre de nombreux avantages, notamment :

* Facilité d&#39;intégration avec l&#39;une des applications [Adobe](/help/assets/integrate-asset-selector-adobe-app.md) ou [non-Adobe](/help/assets/integrate-asset-selector-non-adobe-app.md) utilisant la bibliothèque Vanilla JavaScript.
* Facile à gérer, car les mises à jour du package Sélecteur de ressources sont automatiquement déployées vers le sélecteur de ressources disponible pour votre application. Aucune mise à jour n’est requise dans votre application pour télécharger les dernières modifications.
* Facile à personnaliser, car il existe des propriétés qui contrôlent l’affichage du sélecteur de ressources dans votre application.
* Recherche de texte intégral, filtres prêts à l’emploi et filtres personnalisés pour accéder rapidement aux ressources à utiliser dans l’expérience de création.
* Possibilité de changer de référentiels au sein d’une organisation IMS pour la sélection de ressources.
* Possibilité de trier les ressources par nom, dimensions et taille, et de les afficher en mode Liste, Grille, Galerie ou Cascade.

<!--Perform the following tasks to integrate and use Asset Selector with your [!DNL Experience Manager Assets] repository:

1. [Install Asset Selector](#installation)
2. [Integrate Asset Selector using Vanilla JS](#integration-using-vanilla-js)
3. [Use Asset Selector](#using-asset-selector)
-->

<!--
## Setting up Asset Selector {#asset-selector-setup}

![Asset Selector set up](assets/asset-selector-prereqs.png)
-->

## Conditions préalables{#prereqs}

Vous devez vous assurer que les méthodes de communication suivantes sont disponibles :

* L’application s’exécute sur HTTPS.
* L’URL de l’application se trouve dans la liste autorisée d’URL de redirection du client IMS.
* Le flux de connexion IMS est configuré et rendu à l’aide d’une fenêtre contextuelle sur le navigateur web. Par conséquent, les fenêtres contextuelles doivent être activées ou autorisées sur le navigateur cible.

Utilisez les conditions préalables ci-dessus si vous avez besoin du workflow d’authentification IMS du sélecteur de ressources. Si vous êtes déjà authentifié avec le workflow IMS, vous pouvez également ajouter les informations IMS à la place.

**Voir plus**

* [Intégration du sélecteur de ressources à une application d’Adobe](/help/assets/integrate-asset-selector-adobe-app.md)
* [Intégration du sélecteur de ressources à une application non Adobe](/help/assets/integrate-asset-selector-non-adobe-app.md)
* [Intégration des API d’ouverture de Dynamic Media Sélecteur de ressources](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)


>[!IMPORTANT]
>
> Ce référentiel est destiné à servir de documentation supplémentaire décrivant les API disponibles et les exemples d’utilisation pour l’intégration du sélecteur de ressources. Avant d’essayer d’installer ou d’utiliser le sélecteur de ressources, assurez-vous que votre organisation a reçu l’accès au sélecteur de ressources dans le cadre du profil as a Cloud Service Experience Manager Assets. Si vous n’avez pas reçu les privilèges d’accès, vous ne pouvez pas intégrer ni utiliser ces composants. Pour demander la mise en service, l’administrateur de votre programme doit envoyer à l’Admin Console un ticket d’assistance portant la mention P2 et inclure les informations suivantes :
>
>* Noms de domaine dans lesquels l’application d’intégration est hébergée.
>* Après la mise en service, votre organisation reçoit `imsClientId`, `imsScope` et un `redirectUrl` correspondant aux environnements demandés qui sont essentiels à la configuration du sélecteur de ressources. Sans ces propriétés valides, vous ne pouvez pas exécuter les étapes d’installation.

## Installation {#installation}

Le sélecteur de ressources est disponible via le réseau de diffusion de contenu ESM (par exemple, [esm.sh](https://esm.sh/)/[skypack](https://www.skypack.dev/)) et la version [UMD](https://github.com/umdjs/umd).

Dans les navigateurs utilisant la **version UMD** (recommandé) :

```
<script src="https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js"></script>

<script>
  const { renderAssetSelector } = PureJSSelectors;
</script>
```

Dans les navigateurs avec la prise en charge `import maps` à l’aide de la **version du réseau CDN ESM** :

```
<script type="module">
  import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
</script>
```

Dans la fédération de modules Deno/Webpack à l’aide de la **version du réseau CDN ESM** :

```
import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
```

## Utilisation du sélecteur de ressources {#using-asset-selector}

Une fois que le sélecteur de ressources est configuré et que vous êtes authentifié(e) pour l’utiliser avec votre application [!DNL Adobe Experience Manager] as a [!DNL Cloud Service], vous pouvez sélectionner des ressources ou effectuer d’autres opérations pour rechercher vos ressources dans le référentiel.

![using-asset-selector](assets/using-asset-selector.png)

* **A** : [masquer/afficher le panneau](#hide-show-panel)
* **B** : [sélecteur de référentiels](#repository-switcher)
* **C** : [ressources](#repository)
* **D** : [filtres](#filters)
* **E** : [barre de recherche](#search-bar)
* **F** : [tri](#sorting)
* **G** : [tri par ordre croissant ou décroissant](#sorting)
* **H** : [vue](#types-of-view)

### Masquer/Afficher le panneau {#hide-show-panel}

Pour masquer les dossiers dans le volet de navigation de gauche, cliquez sur l’icône **[!UICONTROL Masquer les dossiers]** . Pour annuler les modifications, cliquez à nouveau sur l’icône **[!UICONTROL Masquer les dossiers]**.

### Sélecteur de référentiels {#repository-switcher}

Le sélecteur de ressources vous permet également de basculer entre des référentiels pour la sélection de ressources. Vous pouvez sélectionner le référentiel de votre choix dans la liste déroulante disponible dans le panneau de gauche. Les options de référentiel disponibles dans la liste déroulante reposent sur la propriété `repositoryId` définie dans le fichier `index.html`. Il est basé sur l’environnement de l’organisation IMS sélectionnée accessible par l’utilisateur connecté. Les clientes et clients peuvent transmettre une préférence `repositoryID` et, dans ce cas, le sélecteur de ressources arrête le rendu du sélecteur de référentiels et effectue uniquement le rendu des ressources à partir du référentiel donné.

### Référentiel de ressources

Il s’agit d’une collection de dossiers de ressources que vous pouvez utiliser pour effectuer des opérations.

### Filtres prêts à l’emploi {#filters}

Le sélecteur de ressources fournit également des options de filtres prêts à l’emploi pour affiner vos résultats de recherche. Les filtres suivants sont disponibles :

* **[!UICONTROL Status] :** inclut l’état actuel de la ressource parmi `all`, `approved`, `rejected` ou `no status`.
* **[!UICONTROL Type de fichier] :** comprend `folder`, `file`, `images`, `documents` ou `video`.
* **[!UICONTROL État d’expiration] :** mentionne les ressources en fonction de leur durée d’expiration. Vous pouvez cocher la case `[!UICONTROL Expired]` pour filtrer les ressources expirées ou définir `[!UICONTROL Expiration Duration]` d’une ressource pour afficher les ressources en fonction de leur durée d’expiration. Lorsqu’une ressource arrive déjà à expiration ou est sur le point d’expirer, un badge semble représenter la même chose. De plus, vous pouvez contrôler si vous souhaitez autoriser l’utilisation (ou le glisser-déposer) d’une ressource expirée. Pour en savoir plus sur la [personnalisation des ressources expirées](/help/assets/asset-selector-customization.md#customize-expired-assets). Par défaut, le badge **Expiration prochaine** s’affiche pour les ressources qui expirent dans les 30 prochains jours. Cependant, vous pouvez configurer l’expiration à l’aide de la propriété `expirationDate` .

  >[!TIP]
  >
  > Si vous souhaitez afficher ou filtrer les ressources en fonction de leur date d’expiration future, mentionnez la période future dans le champ `[!UICONTROL Expiration Duration]`. Il affiche les ressources dont le badge **expirant bientôt** leur est associé.

* **[!UICONTROL Type MIME] :** comprend `JPG`, `GIF`, `PPTX`, `PNG`, `MP4`, `DOCX`, `TIFF`, `PDF`, `XLSX`.
* **[!UICONTROL Taille de l’image] :** comprend une largeur minimale/maximale, une hauteur minimale/maximale de l’image.

  ![rail-view-example](assets/filters-asset-selector.png)

### Recherche personnalisée

Outre la recherche de texte intégral, le sélecteur de ressources vous permet de rechercher des ressources dans des fichiers à l’aide d’une recherche personnalisée. Vous pouvez utiliser des filtres de recherche personnalisés en modes Modal et Rail.

![custom-search](assets/custom-search1.png)

Vous pouvez également créer un filtre de recherche par défaut pour enregistrer les champs que vous recherchez fréquemment et les utiliser ultérieurement. Pour créer une recherche personnalisée de vos ressources, vous pouvez utiliser la propriété `filterSchema`.

### Barre de recherche {#search-bar}

Le sélecteur de ressources vous permet d’effectuer une recherche de texte intégral des ressources dans le référentiel sélectionné. Par exemple, si vous saisissez le mot-clé `wave` dans la barre de recherche, toutes les ressources qui contiennent le mot-clé `wave` dans l’une des propriétés de métadonnées s’affichent.

### Tri {#sorting}

Vous pouvez trier les ressources du sélecteur de ressources selon le nom, les dimensions ou la taille d’une ressource. Vous pouvez également trier les ressources par ordre croissant ou décroissant.

### Types de vues {#types-of-view}

Le sélecteur de ressources vous permet d’afficher la ressource dans quatre vues différentes :

* **![Mode Liste](assets/do-not-localize/list-view.png) ** Le mode Liste affiche les fichiers et dossiers défilables dans une seule colonne.
* **![vue de grille](assets/do-not-localize/grid-view.png) [!UICONTROL Affichage de grille]** La vue de grille affiche les fichiers et dossiers défilants dans une grille de lignes et de colonnes.
* **![vue de la galerie](assets/do-not-localize/gallery-view.png) ** La vue de la galerie affiche les fichiers ou les dossiers dans une liste horizontale verrouillée au centre.
* **![Vue de la cascade](assets/do-not-localize/waterfall-view.png) ** La vue de la cascade affiche des fichiers ou des dossiers sous la forme d’un Bridge.

**Graphique d’aperçu**


## En savoir plus sur les principales fonctionnalités {#key-capabilities-asset-selector}

<table>
<tr>
    <td>
        <img src="assets/integrate-asset-selector.gif" width="70px" height="70px" alt="Graphique du sélecteur de ressources Integrate"><br/>
        <a href="integrate-asset-selector.md">Intégrer le sélecteur de ressources</a>
        <p>
        <em> Découvrez les différentes fonctionnalités permettant d’intégrer le sélecteur de ressources à plusieurs applications.
        </p>
     </td>
    <td>
        <img src="assets/with-adobe-app.gif" width="70px" height="70px" alt="Intégrer le sélecteur de ressources au graphique des applications d’Adobe"><br/>
        <a href="integrate-asset-selector.md">Intégrer le sélecteur de ressources avec les applications d’Adobe</a>
        <p>
        <em>Découvrez comment intégrer le sélecteur de ressources à diverses applications d’Adobe.</em>
        </p>
    </td>
    <td>
        <img src="assets/third-party-app.gif" width="70px" height="70px" alt="Graphique du sélecteur de ressources Integrate"><br/>
        <a href="integrate-asset-selector.md">Intégrer le sélecteur de ressources à des applications tierces</a>
        <p>
        <em>Développez les fonctionnalités permettant d’intégrer le sélecteur de ressources à des applications non Adobes.</em>
        </p>
    </td>
    <td>
        <img src="assets/with-dynamic-media-open-api.gif" width="70px" height="70px" alt="Graphique du sélecteur de ressources Integrate"><br/>
        <a href="integrate-asset-selector.md"> Intégration du sélecteur de ressources aux API Dynamic Media Open </a>
        <p>
        <em>Comprendre comment intégrer le sélecteur de ressources aux API Dynamic Media Open.</em>
        </p>
     </td>
     <td>
        <img src="assets/asset-selector-examples.gif" width="70px" height="70px" alt="Graphique des propriétés du sélecteur de ressources"><br/>
        <a href="asset-selector-customization.md"> Propriétés du sélecteur de ressources</a>
        <p>
        <em>Découvrez les principes de base de la personnalisation de divers composants du sélecteur de ressources, tels que les filtres, la sélection de ressources, les ressources expirées, etc. </em>
        </p>
    </td>
</tr>
<tr>
    <td>
        <img src="assets/asset-selector-properties.gif" width="70px" height="70px" alt="Exemple graphique d’exemples de sélecteur de ressources"><br/>
        <a href="asset-selector-customization.md"> Exemples de sélecteur de ressources</a>
        <p>
        <em>Comprendre l’utilisation des propriétés d’une manière pratique. </em>
        </p>
    </td>
    <td>
        <img src="assets/customize-asset-selector.gif" width="70px" height="70px" alt="Graphique Personnaliser le sélecteur de ressources"><br/>
        <a href="asset-selector-customization.md"> Personnalisations du sélecteur de ressources</a>
        <p>
        <em>Configurez et personnalisez divers composants du sélecteur de ressources en fonction de votre convivialité. </em>
        </p>
    </td>
    <td>
        <img src="assets/asset-selector-upload.gif" width="70px" height="70px" alt="Graphique de chargement du sélecteur de ressources"><br/>
        <a href="asset-selector-upload.md"> Chargement du sélecteur de ressources</a>
        <p>
        <em>Découvrez comment télécharger des fichiers ou des dossiers vers le sélecteur de ressources à partir de votre système de fichiers local ou tiers. </em>
        </p>
    </td>
     <td>
        <img src="assets/asset-selector-collections.gif" width="70px" height="70px" alt="Graphique des collections du sélecteur de ressources"><br/>
        <a href="asset-selector-collections.md"> Collections de sélecteurs de ressources</a>
        <p>
        <em>Découvrez comment utiliser des collections dans le sélecteur de ressources à l’aide du référentiel Experience Manager. </em>
        </p>
    </td>
    <td>
    </td>
</tr>
</table>

>[!MORELIKETHIS]
>
>* [Personnalisations du sélecteur de ressources](/help/assets/asset-selector-customization.md)
>* [Intégrer le sélecteur de ressources à diverses applications](/help/assets/integrate-asset-selector.md)
>* [Propriétés du sélecteur de ressources](/help/assets/asset-selector-properties.md)
>* [Intégrer le sélecteur de ressources à Dynamic Media avec les fonctionnalités OpenAPI](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
