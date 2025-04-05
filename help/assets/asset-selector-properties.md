---
title: Sélecteur de ressources pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Utilisez le sélecteur de ressources pour rechercher, trouver et récupérer les métadonnées et les rendus des ressources dans votre application.
role: Admin, User
exl-id: cd5ec1de-36b0-48a5-95c9-9bd22fac9719
source-git-commit: 97a432270c0063d16f2144d76beb437f7af2895a
workflow-type: tm+mt
source-wordcount: '1326'
ht-degree: 47%

---

# Propriétés du sélecteur de ressources {#asset-selector-properties}

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

Vous pouvez utiliser les propriétés du sélecteur de ressources pour personnaliser le rendu du sélecteur de ressources. Le tableau suivant répertorie les propriétés que vous pouvez utiliser pour personnaliser et utiliser le sélecteur de ressources.

| Propriété | Type | Requis | Valeur par défaut | Description |
|---|---|---|---|---|
| *rail* | Booléen | Non | False | S’il est marqué `true`, le sélecteur de ressources s’affiche dans un rail à gauche. S’il est marqué `false`, le sélecteur de ressources s’affiche dans le mode modal. |
| *imsOrg* | Chaîne | Oui | | Identifiant Adobe Identity Management System (IMS) attribué lors de l’approvisionnement de [!DNL Adobe Experience Manager] en tant que [!DNL Cloud Service] pour votre organisation. La clé `imsOrg` est requise pour vous authentifier, que l’organisation à laquelle vous accédez se trouve sous Adobe IMS ou non. |
| *imsToken* | Chaîne | Non | | Jeton de support IMS utilisé pour l’authentification. `imsToken` est obligatoire si vous utilisez une application [!DNL Adobe] pour l’intégration. |
| *apiKey* | Chaîne | Non | | Clé d’API utilisée pour accéder au service AEM Discovery. `apiKey` est obligatoire si vous utilisez une intégration d’application [!DNL Adobe]. |
| *filterSchema* | Tableau | Non | | Modèle utilisé pour configurer les propriétés de filtre. Cela s’avère utile lorsque vous souhaitez limiter certaines options de filtre dans le sélecteur de ressources. |
| *filterFormProps* | Objet | Non | | Spécifiez les propriétés de filtre à utiliser pour affiner votre recherche. Pour ! Par exemple, JPG de type MIME, PNG, GIF. |
| *selectedAssets* | Tableau `<Object>` | Non |                 | Spécifiez les ressources sélectionnées lors du rendu du sélecteur de ressources. Un tableau d’objets contenant une propriété d’ID des ressources est requis. Par exemple : `[{id: 'urn:234}, {id: 'urn:555'}]`. Une ressource doit être disponible dans le répertoire actuel. Si vous devez utiliser un autre répertoire, saisissez également une valeur pour la propriété `path`. |
| *acvConfig* | Objet | Non | | Propriété d’affichage de collection de ressources qui contient un objet contenant une configuration personnalisée pour remplacer les valeurs par défaut. En outre, cette propriété est utilisée avec `rail` propriété pour activer la vue de rail de la visionneuse de ressources. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | Non |                 | Si les traductions prêtes à l’emploi ne sont pas suffisantes pour répondre aux besoins de votre application, vous pouvez exposer une interface par laquelle vous pouvez transmettre vos propres valeurs localisées et personnalisées via la propriété `i18nSymbols`. La transmission d’une valeur par le biais de cette interface remplace les traductions fournies par défaut par les vôtres. Pour effectuer le remplacement, vous devez transmettre un objet [Descripteur de message](https://formatjs.io/docs/react-intl/api/#message-descriptor) valide à la clé de `i18nSymbols` que vous voulez remplacer. |
| *intl* | Objet | Non | | Le sélecteur de ressources fournit des traductions prêtes à l’emploi par défaut. Vous pouvez sélectionner la langue de traduction en fournissant une chaîne de paramètres régionaux valide via la propriété `intl.locale`. Par exemple : `intl={{ locale: "es-es" }}` </br></br>. Les chaînes de paramètres régionaux prises en charge suivent la norme [ISO 639 - Codes](https://www.iso.org/fr/iso-639-language-codes.html) pour la représentation des noms des normes linguistiques. </br></br> Liste des paramètres régionaux pris en charge : anglais (en-us, par défaut), espagnol (es-es), allemand (de-de), français (fr-FR), italien (it-it), japonais (ja-jp), coréen (ko-kr), portugais (pt-br), chinois (traditionnel, zh-cn), chinois (Taïwan, zh-tw). |
| *repositoryId* | Chaîne | Non | &#39;&#39; | Référentiel à partir duquel le sélecteur de ressources charge le contenu. |
| *additionalAemSolutions* | `Array<string>` | Non | [ ] | Elle vous permet d’ajouter une liste de référentiels AEM supplémentaires. Si aucune information n’est fournie dans cette propriété, seule la bibliothèque de médias ou les référentiels AEM Assets sont pris en compte. |
| *hideTreeNav* | Booléen | Non |  | Indique s’il faut afficher ou masquer la barre latérale de navigation de l’arborescence de ressources. Elle est utilisée uniquement en mode modal et, par conséquent, cette propriété n’a aucun impact en mode rail. |
| *onDrop* | Fonction | Non | | La propriété active la fonctionnalité de dépôt d’une ressource. |
| *dropOptions* | `{allowList?: Object}` | Non | | Configure les options de dépôt à l’aide de la « liste autorisée ». |
| *colorScheme* | Chaîne | Non | | Configure le thème (`light` ou `dark`) du sélecteur de ressources. |
| *Thème* | Chaîne | Non | Par défaut | Appliquez le thème à l’application du sélecteur de ressources entre `default` et `express`. Il prend également en charge les `@react-spectrum/theme-express`. |
| *handleSelection* | Fonction | Non | | Appelée avec un tableau d’éléments de ressource lorsque des ressources sont sélectionnées et que vous cliquez sur le bouton `Select` en mode modal. Cette fonction est uniquement appelée en mode modal. En mode rail, utilisez les fonctions `handleAssetSelection` ou `onDrop`. Exemple : <pre>handleSelection=(assets: Asset[])=> {...}</pre> Pour plus d’informations, consultez la section [sélection de ressources](/help/assets/asset-selector-customization.md#selection-of-assets). |
| *handleAssetSelection* | Fonction | Non | | Appelée avec un tableau d’éléments lorsque les ressources sont sélectionnées ou désélectionnées. Cela s’avère utile si vous souhaitez écouter les ressources lorsque l’utilisateur ou l’utilisatrice les sélectionne. Exemple : <pre>handleSelection=(assets: Asset[])=> {...}</pre> Pour plus d’informations, consultez la section [sélection de ressources](/help/assets/asset-selector-customization.md#selection-of-assets). |
| *onClose* | Fonction | Non | | Appelée lorsque vous cliquez sur le bouton `Close` en mode modal. Cette fonction est uniquement appelée en mode `modal` et n’est pas prise en compte en mode `rail`. |
| *onFilterSubmit* | Fonction | Non | | Appelée avec des éléments de filtre lorsque l’utilisateur ou l’utilisatrice modifie des critères de filtre. |
| *selectionType* | Chaîne | Non | Célibataire | Configuration pour la sélection `single` ou `multiple` de ressources à la fois. |
| placer sur la liste autorisée *dragOptions.* | booléen | Non | | La propriété permet d’autoriser ou de refuser le déplacement de ressources qui ne sont pas sélectionnables. Voir [propriété dragOptions](/help/assets/asset-selector-customization.md#drag-options-property) |
| *aemTierType* | Chaîne | Non |  | Il vous permet de choisir si vous souhaitez afficher les ressources du niveau de diffusion, du niveau de création ou des deux. Syntaxe de <br><br> : `aemTierType:[0]: "author" 1: "delivery"` <br><br> Par exemple, si les deux `["author","delivery"]` sont utilisées, le sélecteur de référentiels affiche des options pour l’auteur et la diffusion. |
| *handleNavigateToAsset* | Fonction | Non | | Il s’agit d’une fonction de rappel permettant de gérer la sélection d’une ressource. |
| *noWrap* | Booléen | Non | | La propriété *noWrap* permet d’effectuer le rendu du sélecteur de ressources dans le panneau du rail latéral. Si cette propriété n’est pas mentionnée, elle affiche la *vue de boîte de dialogue* par défaut. |
| *dialogSize* | prise de contrôle en petit, moyen, grand, plein écran ou plein écran | Chaîne | Facultatif | Vous pouvez contrôler la disposition en spécifiant sa taille à l’aide des options données. |
| *colorScheme* | Clair ou foncé | Non | | Cette propriété est utilisée pour définir le thème d’une application du sélecteur de ressources. Vous pouvez choisir entre le thème clair ou sombre. |
| *filterRepoList* | Fonction | Non |  | Vous pouvez utiliser `filterRepoList` fonction de rappel qui appelle le référentiel Experience Manager et renvoie une liste filtrée de référentiels. |
| *expiryOptions* | Fonction | | | Vous pouvez utiliser entre les deux propriétés suivantes : **getExpiryStatus** qui fournit le statut d’une ressource arrivée à expiration. La fonction renvoie des `EXPIRED`, des `EXPIRING_SOON` ou des `NOT_EXPIRED` en fonction de la date d’expiration d’une ressource que vous fournissez. Voir [ Personnalisation des ressources expirées ](/help/assets/asset-selector-customization.md#customize-expired-assets). De plus, vous pouvez utiliser **allowSelectionAndDrag** dans lequel la valeur de la fonction peut être `true` ou `false`. Lorsque la valeur est définie sur `false`, la ressource expirée ne peut pas être sélectionnée ni glissée-déplacée sur la zone de travail. |
| *showToast* | | Non | | Cela permet au sélecteur de ressources d’afficher un message toast personnalisé pour la ressource expirée. |
| *metadataSchema* | Tableau | Non | | Ajoutez un tableau de champs que vous fournissez pour collecter les métadonnées de l’utilisateur. Cette propriété vous permet également d’utiliser des métadonnées masquées qui sont automatiquement affectées à une ressource, mais ne sont pas visibles par l’utilisateur. |
| *onMetadataFormChange* | Fonction de rappel | Non | | Il se compose de `property` et de `value`. `Property` est égal à *mapToProperty* du champ transmis à partir du *metadataSchema* dont la valeur est mise à jour. Tandis que `value` est égal à , la nouvelle valeur est fournie en tant qu’entrée. |
| *targetUploadPath* | Chaîne |  | `"/content/dam"` | Le chemin de chargement cible pour les fichiers qui sont par défaut la racine du référentiel de ressources. |
| *hideUploadButton* | Booléen | | False | Cela permet de s’assurer que le bouton de chargement interne doit être masqué ou non. |
| *onUploadStart* | Fonction | Non |  | Il s’agit d’une fonction de rappel utilisée pour transmettre la source de chargement entre Dropbox, OneDrive ou le déploiement local. La syntaxe est `(uploadInfo: UploadInfo) => void` |
| *importSettings* | Fonction | | | Elle permet la prise en charge de l’importation de ressources provenant de sources tierces. `sourceTypes` utilise un tableau des sources d’importation que vous souhaitez activer. Les sources prises en charge sont Onedrive et Dropbox. La syntaxe est `{ sourceTypes?: ImportSourceType[]; apiKey?: string; }` |
| *onUploadComplete* | Fonction | Non | | Il s’agit d’une fonction de rappel utilisée pour transmettre le statut de chargement du fichier parmi les valeurs réussi, échec ou dupliqué. La syntaxe est `(uploadStats: UploadStats) => void` |
| *onFilesChange* | Fonction | Non | | Il s’agit d’une fonction de rappel utilisée pour afficher le comportement d’un chargement lorsqu’un fichier est modifié. Il transmet le nouveau tableau de fichiers en attente de chargement et le type de source du chargement. Le type Source peut être nul en cas d&#39;erreur. La syntaxe est `(newFiles: File[], uploadType: UploadType) => void` |
| *uploadingPlaceholder* | Chaîne | | | Il s’agit d’une image d’espace réservé qui remplace le formulaire de métadonnées lorsqu’un chargement de la ressource est lancé. La syntaxe est `{ href: string; alt: string; } ` |
| *uploadConfig* | Objet | | | Il s’agit d’un objet qui contient la configuration personnalisée pour le chargement. |
| *featureSet* | Tableau | Chaîne | | La propriété `featureSet:[ ]` est utilisée pour activer ou désactiver une fonctionnalité particulière dans l’application du sélecteur de ressources. Pour activer le composant ou une fonctionnalité, vous pouvez transmettre une valeur de chaîne dans le tableau ou laisser le tableau vide pour désactiver ce composant. Par exemple, si vous souhaitez activer la fonctionnalité de chargement dans le sélecteur de ressources, utilisez la syntaxe `featureSet:[0:"upload"]`. |

<!--
| *rootPath* | String | No | /content/dam/ | Folder path from which Asset Selector displays your assets. `rootPath` can also be used in the form of encapsulation. For example, given the following path, `/content/dam/marketing/subfolder/`, Asset Selector does not allow you to traverse through any parent folder, but only displays the children folders. |
| *path* | String | No | | Path that is used to navigate to a specific directory of assets when the Asset Selector is rendered. |
| *expirationDate* | Function | No | | This function is used to set the usability period of an asset. |
| *disableDefaultBehaviour* | Boolean | No | False | It is a function that is used to enable or disable the selection of an expired asset. You can customize the default behavior of an asset that is set to expire. See [customize expired assets](/help/assets/asset-selector-customization.md#customize-expired-assets). |
-->
