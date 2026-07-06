---
title: Propriétés du gestionnaire de contenu
description: Utilisez les propriétés pour personnaliser le rendu du gestionnaire d’accès lorsque vous l’intégrez à votre application.
role: Admin, User
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: cd5ec1de-36b0-48a5-95c9-9bd22fac9719
source-git-commit: 230ca753bd5f3d5b26b30a962a526dc0edfc9bd4
workflow-type: tm+mt
source-wordcount: '2549'
ht-degree: 26%

---

# Installation et propriétés du gestionnaire d’accès {#content-advisor-installation-properties}

Content Advisor peut également être intégré à des applications non Adobe (tierces), ce qui permet d’étendre la découverte intelligente des ressources au-delà des applications Adobe. Le même ensemble riche de fonctionnalités, notamment la recherche optimisée par l’IA, les recommandations contextuelles, la découverte basée sur des résumés de campagne, l’accès aux rendus Dynamic Media, la découverte de fragments de contenu, les filtres et les métadonnées de ressource, est pris en charge dans les intégrations tierces.

## Prérequis{#prereqs}

Vous devez vous assurer que les méthodes de communication suivantes sont disponibles :

* L’application hôte s’exécute sur HTTPS.
* Vous ne pouvez pas exécuter l’application sur `localhost`. Si vous souhaitez intégrer le gestionnaire d’accès sur votre ordinateur local, vous devez créer un domaine personnalisé, par exemple `[https://<your_campany>.localhost.com:<port_number>]`, et l’ajouter dans le `redirectUrl list`.
* Vous pouvez configurer et ajouter des clientID dans la variable d’environnement Cloud Service AEM avec les `imsClientId` correspondants.
<!--
* You can configure and add `ADOBE_PROVIDED_CLIENT_ID` into the AEM Cloud Service environment variable with the respective `imsClientId`.
![Asset Selector IMS Client id environment](assets/asset-selector-ims-client-id-env.png)
-->
* La liste des portées IMS doit être définie dans la configuration de l’environnement.
* L’URL de l’application se trouve dans la liste autorisée d’URL de redirection du client IMS.
* Le flux de connexion IMS est configuré et rendu à l’aide d’une fenêtre contextuelle sur le navigateur web. Par conséquent, les fenêtres contextuelles doivent être activées ou autorisées sur le navigateur cible.

Utilisez les conditions préalables ci-dessus si vous avez besoin du workflow d’authentification IMS du gestionnaire de contenu. Si votre authentification est déjà effective avec le workflow IMS, vous pouvez également ajouter les informations IMS à la place.

>[!IMPORTANT]
>
> Ce référentiel est destiné à servir de documentation supplémentaire décrivant les API disponibles et des exemples d’utilisation pour l’intégration de la fonction de conseil sur l’utilisation des ressources. Avant de tenter d’installer ou d’utiliser le gestionnaire d’accès, vérifiez que l’accès au gestionnaire d’accès a été attribué à votre entreprise dans le cadre du profil Experience Manager Assets as a Cloud Service. Si vous n’avez pas reçu les privilèges d’accès, vous ne pouvez pas intégrer ni utiliser ces composants. Pour demander l’approvisionnement, l’administrateur ou l’administratrice de votre programme doit envoyer à Admin Console un ticket d’assistance portant la mention P2 et inclure les informations suivantes :
>
>* Noms de domaine dans lesquels l’application d’intégration est hébergée.
>* Après la mise en service, votre entreprise recevra `imsClientId`, `imsScope` et un `redirectUrl` correspondant aux environnements demandés qui sont essentiels à la configuration du gestionnaire de contenu. Sans ces propriétés valides, vous ne pouvez pas exécuter les étapes d’installation.

## Installation {#content-advisor-installation}

Le gestionnaire de contenu est disponible via le réseau CDN ESM (par exemple, [esm.sh](https://esm.sh/)/[skypack](https://www.skypack.dev/)) et la version [UMD](https://github.com/umdjs/umd).

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

## Propriétés du gestionnaire de contenu {#content-advisor-propertiess}

Vous pouvez utiliser les propriétés de la fonction de conseil pour personnaliser son rendu. Le tableau suivant répertorie les propriétés que vous pouvez utiliser pour personnaliser et utiliser la fonction de conseil sur le contenu.

| Propriété | Type | Requis | Valeur par défaut | Description |
|---|---|---|---|---|
| *rail* | Booléen | Non | False | S’il est marqué `true`, le gestionnaire d’accès s’affiche dans un rail à gauche. S’il est marqué `false`, le gestionnaire d’accès est rendu en mode modal. |
| *imsOrg* | Chaîne | Oui | | Identifiant Adobe Identity Management System (IMS) attribué lors de l’approvisionnement de [!DNL Adobe Experience Manager] en tant que [!DNL Cloud Service] pour votre organisation. La clé `imsOrg` est requise pour vous authentifier, que l’organisation à laquelle vous accédez se trouve sous Adobe IMS ou non. |
| *imsToken* | Chaîne | Non | | Jeton de support IMS utilisé pour l’authentification. `imsToken` est obligatoire si vous utilisez une application [!DNL Adobe] pour l’intégration. |
| *apiKey* | Chaîne | Non | | Clé d’API utilisée pour accéder au service AEM Discovery. `apiKey` est obligatoire si vous utilisez une intégration d’application [!DNL Adobe]. |
| *externalBrief* | Chaîne | Non | | Permet de charger un document de résumé de campagne pour découvrir les ressources appropriées sans saisir manuellement les mots-clés de recherche. Le conseiller d’accès analyse les informations du résumé de la campagne afin de comprendre l’intention de la campagne et recommande les ressources appropriées disponibles dans AEM Assets. |
| *filterSchema* | Tableau | Non | | Modèle utilisé pour configurer les propriétés de filtre. Cela s’avère utile lorsque vous souhaitez limiter certaines options de filtre dans le gestionnaire d’accès. |
| *filterFormProps* | Objet | Non | | Spécifiez les propriétés de filtre à utiliser pour affiner votre recherche. Pour ! Par exemple, JPG de type MIME, PNG, GIF. |
| *selectedAssets* | Tableau `<Object>` | Non |                 | Spécifiez l’Assets sélectionnée lors du rendu du gestionnaire d’accès. Un tableau d’objets contenant une propriété d’ID des ressources est requis. Par exemple : `[{id: 'urn:234}, {id: 'urn:555'}]`. Une ressource doit être disponible dans le répertoire actuel. Si vous devez utiliser un autre répertoire, saisissez également une valeur pour la propriété `path`. |
| *acvConfig* | Objet | Non | | Propriété d’affichage de collection de ressources qui contient un objet contenant une configuration personnalisée pour remplacer les valeurs par défaut. En outre, cette propriété est utilisée avec `rail` propriété pour activer la vue de rail de la visionneuse de ressources. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | Non |                 | Si les traductions prêtes à l’emploi ne sont pas suffisantes pour répondre aux besoins de votre application, vous pouvez exposer une interface par laquelle vous pouvez transmettre vos propres valeurs localisées et personnalisées via la propriété `i18nSymbols`. Le transfert d’une valeur par le biais de cette interface remplace les traductions fournies par défaut par les vôtres. Pour effectuer le remplacement, vous devez transmettre un objet [Descripteur de message](https://formatjs.io/docs/react-intl/api/#message-descriptor) valide à la clé de `i18nSymbols` que vous voulez remplacer. |
| *intl* | Objet | Non | | Le gestionnaire d’accès fournit les traductions prêtes à l’emploi par défaut. Vous pouvez sélectionner la langue de traduction en fournissant une chaîne de paramètres régionaux valide via la propriété `intl.locale`. Par exemple : `intl={{ locale: "es-es" }}` </br></br> Les chaînes de paramètres régionaux prises en charge suivent la norme [ISO 639 - Codes](https://www.iso.org/fr/iso-639-language-codes.html) pour la représentation des noms des normes linguistiques. </br></br> Liste des paramètres régionaux pris en charge : anglais (en-us, par défaut), espagnol (es-es), allemand (de-de), français (fr-fr), italien (it-it), japonais (ja-jp), coréen (ko-kr), portugais (pt-br), chinois (traditionnel, zh-cn), chinois (Taïwan, zh-tw). |
| *repositoryId* | Chaîne | Non | &#39;&#39; | Référentiel à partir duquel le gestionnaire d’accès charge le contenu. |
| *additionalAemSolutions* | `Array<string>` | Non | [ ] | Elle vous permet d’ajouter une liste de référentiels AEM supplémentaires. Si aucune information n’est fournie dans cette propriété, seule la bibliothèque de médias ou les référentiels AEM Assets sont pris en compte. |
| *hideTreeNav* | Booléen | Non |  | Indique s’il faut afficher ou masquer la barre latérale de navigation de l’arborescence de ressources. Elle est utilisée uniquement en mode modal et, par conséquent, cette propriété n’a aucun impact en mode rail. |
| *onDrop* | Fonction | Non | | La fonctionnalité Lors du dépôt permet de faire glisser une ressource et de la libérer dans une zone de dépôt désignée. Il permet des interfaces utilisateur interactives où les ressources peuvent être déplacées et traitées en toute simplicité. |
| *dropOptions* | `{allowList?: Object}` | Non | | Configure les options de dépôt à l’aide de la « liste autorisée ». |
| *theme* | Chaîne | Non | Par défaut | Appliquez le thème à l’application du gestionnaire d’accès entre `default` et `express`. Il prend également en charge les `@react-spectrum/theme-express`. |
| *handleSelection* | Fonction | Non | | Appelée avec un tableau d’éléments de ressource lorsque des ressources sont sélectionnées et que vous cliquez sur le bouton `Select` en mode modal. Cette fonction est uniquement appelée en mode modal. En mode rail, utilisez les fonctions `handleAssetSelection` ou `onDrop`. Exemple : <pre>handleSelection=(assets: Asset[])=> {...}</pre> Pour plus d’informations, consultez la section [sélection de ressources](/help/assets/content-advisor-customization.md#selection-of-assets). |
| *handleAssetSelection* | Fonction | Non | | Appelée avec un tableau d’éléments lorsque les ressources sont sélectionnées ou désélectionnées. Cela s’avère utile si vous souhaitez écouter les ressources lorsque l’utilisateur ou l’utilisatrice les sélectionne. Exemple : <pre>handleAssetSelection=(assets: Asset[])=> {...}</pre> Pour plus d’informations, consultez la section [sélection de ressources](/help/assets/content-advisor-customization.md#selection-of-assets). |
| *onClose* | Fonction | Non | | Appelée lorsque vous cliquez sur le bouton `Close` en mode modal. Cette fonction est uniquement appelée en mode `modal` et n’est pas prise en compte en mode `rail`. |
| *onFilterSubmit* | Fonction | Non | | Appelée avec des éléments de filtre lorsque l’utilisateur ou l’utilisatrice modifie des critères de filtre. |
| *selectionType* | Chaîne | Non | Célibataire | Configuration pour la sélection `single` ou `multiple` de ressources à la fois. |
| *dragOptions.* | booléen | Non | | La propriété permet d’autoriser ou de refuser le déplacement de ressources qui ne sont pas sélectionnables. Voir [propriété dragOptions](/help/assets/content-advisor-customization.md#drag-options-property) |
| *aemTierType* | Chaîne | Non |  | Il vous permet de choisir si vous souhaitez afficher les ressources du niveau de diffusion, du niveau de création ou des deux. <br><br> Syntaxe : `aemTierType: "author"  "delivery"` <br><br> Par exemple, si les deux `["author","delivery"]` sont utilisées, le sélecteur de référentiels affiche des options pour l’auteur et la diffusion. |
| *handleNavigateToAsset* | Fonction | Non | | Il s’agit d’une fonction de rappel permettant de gérer la sélection d’une ressource. |
| *noWrap* | Booléen | Non | | La propriété *noWrap* empêche le gestionnaire de contenu d&#39;être encapsulé dans une boîte de dialogue. Si cette propriété n’est pas mentionnée, elle affiche la *vue de boîte de dialogue* par défaut. |
| *dialogSize* | S, M, L, fullscreen, fullscreenTakeover | Chaîne | Facultatif | Vous pouvez contrôler la disposition en spécifiant sa taille à l’aide des options données. |
| *colorScheme* | Chaîne (claire, foncée) | Non | | Cette propriété est utilisée pour définir le thème d&#39;une application de la fonction de conseil en contenu. Vous pouvez choisir entre le thème clair ou sombre. |
| *filterRepoList* | Fonction | Non | | Une fonction qui reçoit la liste des référentiels et renvoie une liste filtrée. |
| *expiryOptions* | Fonction | | | Vous pouvez utiliser entre les deux propriétés suivantes : **getExpiryStatus** qui fournit le statut d’une ressource arrivée à expiration. La fonction renvoie des `EXPIRED`, des `EXPIRING_SOON` ou des `NOT_EXPIRED` en fonction de la date d’expiration d’une ressource que vous fournissez. Voir [ Personnalisation des ressources expirées ](/help/assets/content-advisor-customization.md#customize-expired-assets). De plus, vous pouvez utiliser **allowSelectionAndDrag** dans lequel la valeur de la fonction peut être `true` ou `false`. Lorsque la valeur est définie sur `false`, la ressource expirée ne peut pas être sélectionnée ni glissée-déplacée sur la zone de travail. |
| *showToast* | | Non | | Il permet au gestionnaire de contenu d’afficher un message toast personnalisé pour la ressource expirée. |
| *uploadConfig* | Objet | | | Il s’agit d’un objet qui contient la configuration personnalisée pour le chargement. Pour plus d’informations](#content-advisor-customization.md#upload-config) consultez la section [configuration de chargement . |
| *uploadConfig* > *metadataSchema* | Tableau | Non | | Cette propriété est imbriquée sous `uploadConfig` propriété . Ajoutez un tableau de champs que vous fournissez pour collecter les métadonnées de l’utilisateur. Cette propriété vous permet également d’utiliser des métadonnées masquées qui sont automatiquement affectées à une ressource, mais ne sont pas visibles par l’utilisateur. |
| *uploadConfig* > *onMetadataFormChange* | Fonction de rappel | Non | | Cette propriété est imbriquée sous `uploadConfig` propriété . Il se compose de `property` et de `value`. `Property` est égal à *mapToProperty* du champ transmis à partir du *metadataSchema* dont la valeur est mise à jour. Tandis que `value` est égal à , la nouvelle valeur est fournie en tant qu’entrée. |
| *uploadConfig* > *targetUploadPath* | Chaîne |  | `"/content/dam"` | Cette propriété est imbriquée sous `uploadConfig` propriété . Le chemin de chargement cible pour les fichiers qui sont par défaut la racine du référentiel de ressources. |
| *uploadConfig* > *hideUploadButton* | Booléen | | False | Cela permet de s’assurer que le bouton de chargement interne doit être masqué ou non. Cette propriété est imbriquée sous `uploadConfig` propriété . |
| *uploadConfig* > *onUploadStart* | Fonction | Non |  | Il s’agit d’une fonction de rappel utilisée pour transmettre la source de chargement entre Dropbox, OneDrive ou le déploiement local. La syntaxe est `(uploadInfo: UploadInfo) => void`. Cette propriété est imbriquée sous `uploadConfig` propriété . |
| *uploadConfig* > *importSettings* | Fonction | | | Elle permet la prise en charge de l’importation de ressources provenant de sources tierces. `sourceTypes` utilise un tableau des sources d’importation que vous souhaitez activer. Les sources prises en charge sont Onedrive et Dropbox. La syntaxe est `{ sourceTypes?: ImportSourceType[]; apiKey?: string; }`. De plus, cette propriété est imbriquée sous `uploadConfig` propriété . |
| *uploadConfig* > *onUploadComplete* | Fonction | Non | | Il s’agit d’une fonction de rappel utilisée pour transmettre le statut de chargement du fichier parmi les valeurs réussi, échec ou dupliqué. La syntaxe est `(uploadStats: UploadStats) => void`. De plus, cette propriété est imbriquée sous `uploadConfig` propriété . |
| *uploadConfig* > *onFilesChange* | Fonction | Non | | Cette propriété est imbriquée sous `uploadConfig` propriété . Il s’agit d’une fonction de rappel utilisée pour afficher le comportement d’un chargement lorsqu’un fichier est modifié. Il transmet le nouveau tableau de fichiers en attente de chargement et le type de source du chargement. Le type Source peut être nul en cas d&#39;erreur. La syntaxe est `(newFiles: File[], uploadType: UploadType) => void` |
| *uploadConfig* > *uploadingPlaceholder* | Chaîne | | | Il s’agit d’une image d’espace réservé qui remplace le formulaire de métadonnées lorsqu’un chargement de la ressource est lancé. La syntaxe est `{ href: string; alt: string; }`. De plus, cette propriété est imbriquée sous `uploadConfig` propriété . |
| *featureSet* | Tableau | Chaîne | | La propriété `featureSet:[ ]` permet d’activer ou de désactiver une fonctionnalité particulière dans l’application du gestionnaire d’accès. Pour activer le composant ou une fonctionnalité, vous pouvez transmettre une valeur de chaîne dans le tableau ou laisser le tableau vide pour désactiver les fonctionnalités ajoutées et simplement avoir la fonctionnalité de base. Par exemple, si vous souhaitez activer la fonctionnalité de chargement dans le gestionnaire d’accès, utilisez la syntaxe `featureSet:["upload"]`. De même, vous pouvez utiliser `featureSet:["content-fragments"]` pour activer les fragments de contenu dans le gestionnaire d’accès. Pour utiliser plusieurs fonctionnalités ensemble, la syntaxe est featureSet:[« upload », « content-fragments »]. |

<!--
| *selectedRendition* | Object | | | This property allows users to define and control which renditions of an asset are displayed when the panel is accessed. This customization enhances user experience by filtering out unnecessary renditions and showcasing only the most relevant renditions. For example, `CopyUrlHref` allows you to use Dynamic Media renditions in your Asset Selector application (delivery URL). |
| *featureSet* | Array | String | | The `featureSet:[ ]` property is used to enable or disable a particular functionaly in the Asset Selector application. To enable the component or a feature, you can pass a string value in the array or leave the array empty to disable that component. For example, you want to enable upload functionality in the Asset Selector, use the syntax `featureSet:[0:"upload"]`. Similarly, you can use `featureSet:[0:"collections"]` to enable collections in the Asset Selector. Addidionally, use `featureSet:[0:"detail-panel"]` to enable [details panel](overview-asset-selector.md#asset-details-and-metadata) of an asset. Also, `featureSet:[0:"dm-renditions"]` to show Dynamic Media renditions of an asset.|
| *rootPath* | String | No | /content/dam/ | Folder path from which Asset Selector displays your assets. `rootPath` can also be used in the form of encapsulation. For example, given the following path, `/content/dam/marketing/subfolder/`, Asset Selector does not allow you to traverse through any parent folder, but only displays the children folders. |
| *path* | String | No | | Path that is used to navigate to a specific directory of assets when the Asset Selector is rendered. |
| *expirationDate* | Function | No | | This function is used to set the usability period of an asset. |
| *disableDefaultBehaviour* | Boolean | No | False | It is a function that is used to enable or disable the selection of an expired asset. You can customize the default behavior of an asset that is set to expire. See [customize expired assets](/help/assets/asset-selector-customization.md#customize-expired-assets). |
-->

### ImsAuthProps {#ims-auth-props}

Les propriétés `ImsAuthProps` définissent les informations d’authentification et le flux que le gestionnaire d’accès utilise pour obtenir une `imsToken`. En définissant ces propriétés, vous pouvez contrôler le comportement du flux d’authentification et enregistrer des écouteurs pour divers événements d’authentification.

| Nom de la propriété | Description |
|---|---|
| `imsClientId` | Valeur de chaîne représentant l’identifiant client IMS utilisé à des fins d’authentification. Cette valeur est fournie par Adobe et est spécifique à votre organisation Adobe AEM CS. |
| `imsScope` | Décrit les portées utilisées dans l’authentification. Les portées déterminent le niveau d’accès de l’application aux ressources de votre organisation. Plusieurs portées peuvent être séparées par des virgules. |
| `redirectUrl` | Représente l’URL de redirection de l’utilisateur après l’authentification. Cette valeur est généralement définie sur l’URL actuelle de l’application. Si aucun `redirectUrl` n’est fourni, `ImsAuthService` utilise redirectUrl pour enregistrer les `imsClientId` |
| `modalMode` | Valeur booléenne indiquant si le flux d’authentification doit être affiché dans une fenêtre modale (pop-up) ou non. S’il est défini sur `true`, le flux d’authentification s’affiche dans un pop-up. S’il est défini sur `false`, le flux d’authentification s’affiche lors d’un rechargement complet de la page. _Remarque :_pour une meilleure expérience utilisateur, vous pouvez contrôler dynamiquement cette valeur si le pop-up du navigateur est désactivé. |
| `onImsServiceInitialized` | Une fonction de rappel appelée lors de l’initialisation du service d’authentification Adobe IMS. Cette fonction accepte un paramètre, `service`, qui est un objet représentant le service Adobe IMS. Voir [`ImsAuthService`](#imsauthservice-ims-auth-service) pour plus d’informations. |
| `onAccessTokenReceived` | Une fonction de rappel appelée lorsqu’un `imsToken` est reçu du service d’authentification Adobe IMS. Cette fonction accepte un paramètre, `imsToken`, qui est une chaîne représentant le jeton d’accès. |
| `onAccessTokenExpired` | Fonction de rappel appelée lorsqu’un jeton d’accès a expiré. Cette fonction est généralement utilisée pour déclencher un nouveau flux d’authentification afin d’obtenir un nouveau jeton d’accès. |
| `onErrorReceived` | Une fonction de rappel appelée lorsqu’une erreur se produit lors de l’authentification. Cette fonction utilise deux paramètres : le type d’erreur et le message d’erreur. Le type d’erreur est une chaîne représentant le type d’erreur et le message d’erreur est une chaîne représentant le message d’erreur. |

### ImsAuthService {#ims-auth-service}

`ImsAuthService` classe gère le flux d’authentification du gestionnaire d’accès. Il est chargé d’obtenir un `imsToken` du service d’authentification Adobe IMS. Le `imsToken` permet d’authentifier l’utilisateur et d’autoriser l’accès au référentiel [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Assets. ImsAuthService utilise les propriétés `ImsAuthProps` pour contrôler le flux d’authentification et enregistrer des écouteurs pour divers événements d’authentification. Vous pouvez utiliser la fonction de [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) pratique pour enregistrer l’instance _ImsAuthService_ auprès du gestionnaire d’accès. Les fonctions suivantes sont disponibles dans la classe `ImsAuthService`. Cependant, si vous utilisez la fonction _registerAssetsSelectorsAuthService_, vous n’avez pas besoin d’appeler directement ces fonctions.

| Nom de la fonction | Description |
|---|---|
| `isSignedInUser` | Détermine si l’utilisateur est actuellement connecté au service et renvoie une valeur booléenne en conséquence. |
| `getImsToken` | Récupère le `imsToken` d’authentification de l’utilisateur actuellement connecté, qui peut être utilisé pour authentifier des requêtes à d’autres services, tels que la génération du _rendu de ressource. |
| `signIn` | Lance le processus de connexion de l’utilisateur. Cette fonction utilise le `ImsAuthProps` pour afficher l’authentification dans un pop-up ou un rechargement complet de la page |
| `signOut` | Déconnecte l’utilisateur du service, invalide son jeton d’authentification et exige qu’il se reconnecte pour accéder aux ressources protégées. Appeler cette fonction recharge la page active. |
| `refreshToken` | Actualise le jeton d’authentification de l’utilisateur actuellement connecté, ce qui empêche son expiration et garantit un accès ininterrompu aux ressources protégées. Renvoie un nouveau jeton d’authentification pouvant être utilisé pour les requêtes suivantes. |

### contentFragmentSelectorProps {#content-fragment-selector-properties}

`contentFragmentSelectorProps` permet de configurer l’accès aux fragments de contenu et leur affichage dans la fonction de conseil sur le contenu. En activant la fonctionnalité de fragments de contenu dans le `featureSet` et en fournissant la configuration requise, vous pouvez intégrer facilement la sélection de fragments de contenu aux ressources. Cela permet aux utilisateurs et utilisatrices de parcourir, rechercher et sélectionner des fragments de contenu dans la même interface unifiée, assurant ainsi une expérience de sélection de contenu cohérente entre les ressources et le contenu structuré.

```
const assetSelectorProps = {
     featureSet: [
       'upload',            /* Include upload or other featureSet values to ensure no missing functionality */
       'content-fragments', /* Content Fragments pill will be shown */
     ],
     contentFragmentSelectorProps: {
       /* Configures the Content Fragments Pill experience */
       /* ...props @aem-sites/content-fragment-selector MFE supports */
    }
}

<AssetSelector {...assetSelectorProps} />
```

Dans `contentFragmentSelectorProps`, vous pouvez mentionner l’une des propriétés disponibles dans [Propriétés du sélecteur de fragment de contenu](/help/headless/content-fragment-selector/properties.md).

Pour plus d’informations sur l’intégration de la fonction de conseil sur les contenus avec les applications Angular, React et JavaScript, consultez les exemples d’intégration de la fonction de conseil sur les contenus [Content Advisor](https://github.com/adobe/aem-assets-selectors-mfe-examples/tree/consolidate-docs-to-experience-league/examples).


**Voir également**

* [Traduire les ressources](/help/assets/translate-assets.md)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](/help/assets/file-format-support.md)
* [Rechercher des ressources](/help/assets/search-assets.md)
* [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](/help/assets/asset-reports.md)
* [Schémas de métadonnées](/help/assets/metadata-schemas.md)
* [Télécharger des ressources](/help/assets/download-assets-from-aem.md)
* [Gestion des métadonnées](/help/assets/manage-metadata.md)
* [Gérer les modèles Dynamic Media](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Gérer les rapports](/help/assets/manage-reports-assets-view.md)
* [Facettes de recherche](/help/assets/search-facets.md)
* [Gérer les collections](/help/assets/manage-collections.md)
* [Import des métadonnées en bloc](/help/assets/metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
