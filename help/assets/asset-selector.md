---
title: Sélecteur de ressources pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Utilisez le sélecteur de ressources pour rechercher, trouver et récupérer les métadonnées et les rendus des ressources dans votre application.
contentOwner: KK
role: Admin,User
exl-id: 5f962162-ad6f-4888-8b39-bf5632f4f298
source-git-commit: e357dd0b9b2e67d4989a34054737a91743d0933a
workflow-type: tm+mt
source-wordcount: '4550'
ht-degree: 39%

---

# Sélecteur de ressources micro front-end {#Overview}

Le sélecteur de ressources micro front-end fournit une interface utilisateur qui s’intègre facilement au référentiel [!DNL Experience Manager Assets] afin que vous puissiez parcourir ou rechercher des ressources numériques disponibles dans le référentiel et les utiliser dans votre expérience de création d’applications.

L’interface utilisateur micro front-end est mise à disposition dans votre expérience de l’application à l’aide du package Sélecteur de ressources. Toutes les mises à jour du package sont automatiquement importées et le dernier sélecteur de ressources déployé est automatiquement téléchargé dans votre application.

![Présentation](assets/overview.png)

Le sélecteur de ressources offre de nombreux avantages, notamment :

* Facilité d&#39;intégration avec l&#39;une des applications [Adobe](#asset-selector-ims) ou [non-Adobe](#asset-selector-non-ims) utilisant la bibliothèque Vanilla JavaScript.
* Facile à gérer, car les mises à jour du package Sélecteur de ressources sont automatiquement déployées vers le sélecteur de ressources disponible pour votre application. Aucune mise à jour n’est requise dans votre application pour télécharger les dernières modifications.
* Facile à personnaliser, car il existe des propriétés qui contrôlent l’affichage du sélecteur de ressources dans votre application.
* Recherche de texte intégral, filtres prêts à l’emploi et filtres personnalisés pour accéder rapidement aux ressources à utiliser dans l’expérience de création.
* Possibilité de changer de référentiels au sein d’une organisation IMS pour la sélection de ressources.
* Possibilité de trier les ressources par nom, dimension et taille, et de les afficher en mode Liste, Grille, Galerie ou Cascade.

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

>[!IMPORTANT]
>
> Ce référentiel est destiné à servir de documentation supplémentaire décrivant les API disponibles et les exemples d’utilisation pour l’intégration du sélecteur de ressources. Avant d’essayer d’installer ou d’utiliser le sélecteur de ressources, assurez-vous que votre organisation a reçu l’accès au sélecteur de ressources dans le cadre du profil as a Cloud Service Experience Manager Assets. Si vous n’avez pas reçu les privilèges d’accès, vous ne pouvez pas intégrer ni utiliser ces composants. Pour demander la mise en service, l’administrateur de votre programme doit envoyer un ticket d’assistance marqué comme P2 à un Admin Console et inclure les informations suivantes :
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

## Intégration du sélecteur de ressources à l’aide de Vanilla JS {#integration-using-vanilla-js}

Vous pouvez intégrer n&#39;importe quelle application [!DNL Adobe] ou non Adobe au référentiel [!DNL Experience Manager Assets] et sélectionner des ressources dans l&#39;application. Voir [Intégration de sélecteur de ressources avec diverses applications](#asset-selector-integration-with-apps).

L’intégration est effectuée en important le package Sélecteur de ressources et en se connectant à Assets as a Cloud Service à l’aide de la bibliothèque JavaScript Vanilla. Modifiez un `index.html` ou tout fichier approprié dans votre application pour :

* Définition des détails d’authentification
* Accès au référentiel Assets as a Cloud Service
* Configuration des propriétés d’affichage du sélecteur de ressources

Vous pouvez effectuer une authentification sans définir certaines des propriétés IMS, si :

* Vous intégrez une application [!DNL Adobe] sur [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=fr).
* Un jeton IMS est déjà généré pour l’authentification.

## Intégration du sélecteur de ressources à différentes applications {#asset-selector-integration-with-apps}

Vous pouvez intégrer le sélecteur de ressources à diverses applications, telles que :

* [Intégrer le sélecteur de ressources à une application  [!DNL Adobe] ](#adobe-app-integration-vanilla)
* [Intégration du sélecteur de ressources à une application non Adobe](#adobe-non-app-integration)

>[!BEGINTABS]

<!--Integration with an Adobe application content starts here-->

>[!TAB Intégration à une application d&#39;Adobe]

### Conditions préalables{#prereqs-adobe-app}

Utilisez les conditions préalables suivantes si vous intégrez le sélecteur de ressources à une application [!DNL Adobe] :

* [Méthodes de communication](#prereqs)
* imsOrg
* imsToken
* apikey

### Intégrer le sélecteur de ressources à une application [!DNL Adobe] {#adobe-app-integration-vanilla}

L’exemple suivant illustre l’utilisation du sélecteur de ressources lors de l’exécution d’une application [!DNL Adobe] sous Shell unifié ou lorsque `imsToken` est déjà généré pour l’authentification.

Insérez le package Sélecteur de ressources dans votre code à l’aide de la balise `script`, comme illustré dans les _lignes 6 à 15_ de l’exemple ci-dessous. Une fois le script chargé, vous pouvez utiliser la variable globale `PureJSSelectors`. Définissez les [propriétés](#asset-selector-properties) du sélecteur de ressources comme illustré dans les _lignes 16 à 23_. Les propriétés `imsOrg` et `imsToken` sont toutes deux requises pour l’authentification dans l’application Adobe. La propriété `handleSelection` sert à gérer les ressources sélectionnées. Pour effectuer le rendu du sélecteur de ressources, appelez la fonction `renderAssetSelector` comme indiqué dans la _ligne 17_. Le sélecteur de ressources s’affiche dans l’élément de conteneur `<div>`, comme indiqué dans les _lignes 21 et 22_.

En suivant ces étapes, vous pouvez utiliser le sélecteur de ressources avec votre application [!DNL Adobe].

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Asset Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js"></script>
    <script>
        // get the container element in which we want to render the AssetSelector component
        const container = document.getElementById('asset-selector-container');
        // imsOrg and imsToken are required for authentication in Adobe application
        const assetSelectorProps = {
            imsOrg: 'example-ims@AdobeOrg',
            imsToken: "example-imsToken",
            apiKey: "example-apiKey-associated-with-imsOrg",
            handleSelection: (assets: SelectedAssetType[]) => {},
        };
        // Call the `renderAssetSelector` available in PureJSSelectors globals to render AssetSelector
        PureJSSelectors.renderAssetSelector(container, assetSelectorProps);
    </script>
</head>

<body>
    <div id="asset-selector-container" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
    </div>
</body>

</html>
```

<!--For detailed example, visit [Asset Selector Code Example](https://github.com/adobe/aem-assets-selectors-mfe-examples).-->

+++**ImsAuthProps**
Les propriétés `ImsAuthProps` définissent les informations d’authentification et le flux que le sélecteur de ressources utilise pour obtenir un `imsToken`. En définissant ces propriétés, vous pouvez contrôler le comportement du flux d’authentification et enregistrer les écouteurs pour divers événements d’authentification.

| Nom de la propriété | Description |
|---|---|
| `imsClientId` | Une valeur string représentant l’ID client IMS utilisé à des fins d’authentification. Cette valeur est fournie par Adobe et est spécifique à votre Adobe AEM organisation CS. |
| `imsScope` | Décrit les portées utilisées dans l’authentification. Les portées déterminent le niveau d’accès de l’application aux ressources de votre organisation. Plusieurs portées peuvent être séparées par des virgules. |
| `redirectUrl` | Représente l’URL vers laquelle l’utilisateur est redirigé après l’authentification. Cette valeur est généralement définie sur l’URL actuelle de l’application. Si `redirectUrl` n&#39;est pas fourni, `ImsAuthService` utilise redirectUrl utilisé pour enregistrer le `imsClientId` |
| `modalMode` | Valeur booléenne indiquant si le flux d’authentification doit être affiché dans un modal (fenêtre contextuelle). S’il est défini sur `true`, le flux d’authentification s’affiche dans une fenêtre contextuelle. S’il est défini sur `false`, le flux d’authentification s’affiche dans un rechargement de page complet. _Remarque :_ pour un meilleur UX, vous pouvez contrôler dynamiquement cette valeur si la fenêtre contextuelle de l’utilisateur est désactivée. |
| `onImsServiceInitialized` | Fonction de rappel appelée lorsque le service d’authentification Adobe IMS est initialisé. Cette fonction prend un paramètre, `service`, qui est un objet représentant le service Adobe IMS. Voir [`ImsAuthService`](#imsauthservice-ims-auth-service) pour plus de détails. |
| `onAccessTokenReceived` | Fonction de rappel appelée lorsqu’un `imsToken` est reçu du service d’authentification Adobe IMS. Cette fonction utilise un paramètre, `imsToken`, qui est une chaîne représentant le jeton d’accès. |
| `onAccessTokenExpired` | Fonction de rappel appelée lorsqu’un jeton d’accès a expiré. Cette fonction est généralement utilisée pour déclencher un nouveau flux d’authentification afin d’obtenir un nouveau jeton d’accès. |
| `onErrorReceived` | Fonction de rappel appelée lorsqu’une erreur se produit lors de l’authentification. Cette fonction prend deux paramètres : le type d&#39;erreur et le message d&#39;erreur. Le type d’erreur est une chaîne représentant le type d’erreur et le message d’erreur est une chaîne représentant le message d’erreur. |

+++

+++**ImsAuthService**
La classe `ImsAuthService` gère le flux d’authentification pour le sélecteur de ressources. Il est responsable de l&#39;obtention d&#39;un `imsToken` auprès du service d&#39;authentification Adobe IMS. `imsToken` est utilisé pour authentifier l’utilisateur et autoriser l’accès à [!DNL Adobe Experience Manager] en tant que référentiel Assets [!DNL Cloud Service]. ImsAuthService utilise les propriétés `ImsAuthProps` pour contrôler le flux d’authentification et enregistrer les écouteurs pour divers événements d’authentification. Vous pouvez utiliser la fonction [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) pratique pour enregistrer l’instance _ImsAuthService_ avec le sélecteur de ressources. Les fonctions suivantes sont disponibles sur la classe `ImsAuthService`. Cependant, si vous utilisez la fonction _registerAssetsSelectorsAuthService_, vous n’avez pas besoin d’appeler directement ces fonctions.

| Nom de la fonction | Description |
|---|---|
| `isSignedInUser` | Détermine si l’utilisateur est actuellement connecté au service et renvoie une valeur booléenne en conséquence. |
| `getImsToken` | Récupère l’authentification `imsToken` pour l’utilisateur actuellement connecté, qui peut être utilisée pour authentifier les requêtes sur d’autres services, comme la génération de la ressource _rendition. |
| `signIn` | Lance le processus de connexion de l’utilisateur. Cette fonction utilise le `ImsAuthProps` pour afficher l’authentification dans une fenêtre contextuelle ou un rechargement de page complet. |
| `signOut` | Déclenche l’utilisateur du service, invalide son jeton d’authentification et l’oblige à se reconnecter pour accéder aux ressources protégées. L’appel de cette fonction recharge la page active. |
| `refreshToken` | Actualise le jeton d’authentification de l’utilisateur actuellement connecté, l’empêchant d’expirer et assurant un accès ininterrompu aux ressources protégées. Renvoie un nouveau jeton d’authentification qui peut être utilisé pour les requêtes suivantes. |

+++

+++**Validation avec jeton IMS fourni**

```
<script>
    const apiToken="<valid IMS token>";
    function handleSelection(selection) {
    console.log("Selected asset: ", selection);
    };
    function renderAssetSelectorInline() {
    console.log("initializing Asset Selector");
    const props = {
    "repositoryId": "delivery-p64502-e544757.adobeaemcloud.com",
    "apiKey": "ngdm_test_client",
    "imsOrg": "<IMS org>",
    "imsToken": apiToken,
    handleSelection,
    hideTreeNav: true
    }
    const container = document.getElementById('asset-selector-container');
    PureJSSelectors.renderAssetSelector(container, props);
    }
    $(document).ready(function() {
    renderAssetSelectorInline();
    });
</script>
```

+++

+++**Enregistrer des rappels au service IMS**

```
// object `imsProps` to be defined as below 
let imsProps = {
    imsClientId: <IMS Client Id>,
        imsScope: "openid",
        redirectUrl: window.location.href,
        modalMode: true,
        adobeImsOptions: {
            modalSettings: {
            allowOrigin: window.location.origin,
},
        useLocalStorage: true,
},
onImsServiceInitialized: (service) => {
            console.log("onImsServiceInitialized", service);
},
onAccessTokenReceived: (token) => {
            console.log("onAccessTokenReceived", token);
},
onAccessTokenExpired: () => {
            console.log("onAccessTokenError");
// re-trigger sign-in flow
},
onErrorReceived: (type, msg) => {
            console.log("onErrorReceived", type, msg);
},
}
```

+++

<!--Integration with non-Adobe application content starts here-->

>[!TAB Intégration avec une application non-Adobe]

<!--### Integrate Asset Selector with a [!DNL non-Adobe] application {#adobe-non-app-integration}-->

### Conditions préalables {#prereqs-non-adobe-app}

Utilisez les conditions préalables suivantes si vous intégrez le sélecteur de ressources à une application non Adobe :

* [Méthodes de communication](#prereqs)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Le sélecteur de ressources prend en charge l’authentification au référentiel [!DNL Experience Manager Assets] à l’aide des propriétés Identity Management System (IMS) telles que `imsScope` ou `imsClientID` lorsque vous l’intégrez à une application non Adobe.

+++**Configuration du sélecteur de ressources pour une application non Adobe**
Pour configurer le sélecteur de ressources pour une application non Adobe, vous devez d’abord consigner un ticket d’assistance pour l’approvisionnement, suivi des étapes d’intégration.

**Journalisation d’un ticket d’assistance**
Étapes pour enregistrer un ticket d’assistance via l’Admin Console :

1. Ajoutez **Sélecteur de ressources avec AEM Assets** dans le titre du ticket.

1. Dans la description, veuillez fournir les détails suivants :

   * [!DNL Experience Manager Assets] comme URL [!DNL Cloud Service] (ID de programme et ID d’environnement).
   * Noms de domaine dans lesquels l’application web non Adobe est hébergée.
+++

+++**Étapes d’intégration**
Utilisez cet exemple de fichier `index.html` pour l’authentification lors de l’intégration du sélecteur de ressources à une application non Adobe.

Accédez au package Sélecteur de ressources à l’aide de la balise `Script`, comme illustré dans la *ligne 9* vers *ligne 11* de l’exemple de fichier `index.html`.

*Ligne 14* à *ligne 38* de l’exemple décrit les propriétés de flux IMS, telles que `imsClientId`, `imsScope` et `redirectURL`. La fonction requiert que vous définissiez au moins une des propriétés `imsClientId` et `imsScope` . Si vous ne définissez pas de valeur pour `redirectURL`, l’URL de redirection enregistrée pour l’ID client est utilisée.

Comme vous ne disposez pas d’une `imsToken` générée, utilisez les fonctions `registerAssetsSelectorsAuthService` et `renderAssetSelectorWithAuthFlow`, comme illustré dans la ligne 40 à la ligne 50 de l’exemple de fichier `index.html`. Utilisez la fonction `registerAssetsSelectorsAuthService` précédant `renderAssetSelectorWithAuthFlow` pour enregistrer le `imsToken` auprès du sélecteur de ressources. [!DNL Adobe] recommande d’appeler `registerAssetsSelectorsAuthService` lorsque vous instanciez le composant.

Définissez l’authentification et les autres propriétés liées à l’accès as a Cloud Service Assets dans la section `const props`, comme illustré dans la *ligne 54* à la *ligne 60* de l’exemple de fichier `index.html`.

La variable globale `PureJSSelectors`, mentionnée dans *ligne 65*, est utilisée pour effectuer le rendu du sélecteur de ressources dans le navigateur web.

Le sélecteur de ressources est rendu sur l’élément de conteneur `<div>`, comme mentionné dans *ligne 74* à *ligne 81*. L’exemple utilise une boîte de dialogue pour afficher le sélecteur de ressources.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta charset="utf-8">
    <title>Asset Selectors</title>
    <link rel="stylesheet" href="index.css">
    <script id="asset-selector"
        src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/asset-selectors.js"></script>
    <script>

        const imsProps = {
            imsClientId: "<obtained from IMS team>",
            imsScope: "openid, <other scopes>",
            redirectUrl: window.location.href,
            modalMode: true, // false to open in a full page reload flow
            onImsServiceInitialized: (service) => {
                // invoked when the ims service is initialized and is ready
                console.log("onImsServiceInitialized", service);
            },
            onAccessTokenReceived: (token) => {
                console.log("onAccessTokenReceived", token);
            },
            onAccessTokenExpired: () => {
                console.log("onAccessTokenError");
                // re-trigger sign-in flow
            },
            onErrorReceived: (type, msg) => {
                console.log("onErrorReceived", type, msg);
            },
        }

        function load() {
            const registeredTokenService = PureJSSelectors.registerAssetsSelectorsAuthService(imsProps);
            imsInstance = registeredTokenService;
        };

        // initialize the IMS flow before attempting to render the asset selector
        load();
        

        //function that will render the asset selector
            const otherProps = {
            // any other props supported by asset selector
            }
            const assetSelectorProps = {
                "imsOrg": "imsorg",
                ...otherProps
            }
             // container element on which you want to render the AssetSelector/DestinationSelector component
            const container = document.getElementById('asset-selector');

            /// Use the PureJSSelectors in globals to render the AssetSelector/DestinationSelector component
            PureJSSelectors.renderAssetSelectorWithAuthFlow(container, assetSelectorProps, () => {
                const assetSelectorDialog = document.getElementById('asset-selector-dialog');
                assetSelectorDialog.showModal();
            });
        }
    </script>

</head>
<body class="asset-selectors">
    <div>
        <button onclick="renderAssetSelectorWithAuthFlowFlow()">Asset Selector - Select Assets with Ims Flow</button>
    </div>
        <dialog id="asset-selector-dialog">
            <div id="asset-selector" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
            </div>
        </dialog>
    </div>
</body>

</html>
```

+++

+++**Impossible d’accéder au référentiel de diffusion**

>[!TIP]
>
>Si vous avez intégré le sélecteur de ressources à l’aide du workflow S’inscrire mais que vous ne parvenez toujours pas à accéder au référentiel de diffusion, assurez-vous que les cookies de navigateur sont nettoyés. Sinon, vous obtenez une erreur `invalid_credentials All session cookies are empty` dans la console.

>[!ENDTABS]

## Propriétés du sélecteur de ressources {#asset-selector-properties}

Vous pouvez utiliser les propriétés du sélecteur de ressources pour personnaliser le rendu du sélecteur de ressources. Le tableau suivant répertorie les propriétés que vous pouvez utiliser pour personnaliser et utiliser le sélecteur de ressources.

| Propriété | Type | Requis | Valeur par défaut | Description |
|---|---|---|---|---|
| *rail* | Booléen | Non | False | S’il est marqué `true`, le sélecteur de ressources s’affiche dans un rail à gauche. S’il est marqué `false`, le sélecteur de ressources s’affiche dans le mode modal. |
| *imsOrg* | Chaîne | Oui | | Identifiant Adobe Identity Management System (IMS) attribué lors de l’approvisionnement de [!DNL Adobe Experience Manager] en tant que [!DNL Cloud Service] pour votre organisation. La clé `imsOrg` est requise pour vous authentifier, que l’organisation à laquelle vous accédez se trouve sous Adobe IMS ou non. |
| *imsToken* | Chaîne | Non | | Jeton de support IMS utilisé pour l’authentification. `imsToken` est requis si vous utilisez une application [!DNL Adobe] pour l’intégration. |
| *apiKey* | Chaîne | Non | | Clé d’API utilisée pour accéder au service AEM Discovery. `apiKey` est requis si vous utilisez une intégration d’application [!DNL Adobe]. |
| *rootPath* | Chaîne | Non | /content/dam/ | Chemin du dossier à partir duquel le sélecteur de ressources affiche vos ressources. `rootPath` peut également être utilisé sous la forme d’encapsulation. Par exemple, avec le chemin suivant, `/content/dam/marketing/subfolder/`, le sélecteur de ressources ne vous permet pas de parcourir les dossiers parents, mais affiche uniquement les dossiers enfants. |
| *Chemin.* | Chaîne | Non | | Chemin d’accès utilisé pour accéder à un répertoire spécifique de ressources lors du rendu du sélecteur de ressources. |
| *filterSchema* | Tableau | Non | | Modèle utilisé pour configurer les propriétés de filtre. Cela s’avère utile lorsque vous souhaitez limiter certaines options de filtre dans le sélecteur de ressources. |
| *filterFormProps* | Objet | Non | | Spécifiez les propriétés de filtre à utiliser pour affiner votre recherche. Pour ! Par exemple, type MIME JPG, PNG, GIF. |
| *selectedAssets* | Tableau `<Object>` | Non |                 | Spécifiez les ressources sélectionnées lors du rendu du sélecteur de ressources. Un tableau d’objets contenant une propriété d’ID des ressources est requis. Par exemple : `[{id: 'urn:234}, {id: 'urn:555'}]`. Une ressource doit être disponible dans le répertoire actuel. Si vous devez utiliser un autre répertoire, saisissez également une valeur pour la propriété `path`. |
| *acvConfig* | Objet | Non | | Propriété d’affichage de collection de ressources qui contient un objet contenant une configuration personnalisée pour remplacer les valeurs par défaut. Cette propriété est également utilisée avec la propriété `rail` pour activer l’affichage en rail de la visionneuse de ressources. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | Non |                 | Si les traductions prêtes à l’emploi ne sont pas suffisantes pour répondre aux besoins de votre application, vous pouvez exposer une interface par laquelle vous pouvez transmettre vos propres valeurs localisées par le biais de la prop `i18nSymbols`. Le transfert d’une valeur par le biais de cette interface remplace les traductions fournies par défaut et utilise plutôt la vôtre. Pour effectuer le remplacement, vous devez transmettre un objet [Descripteur de message](https://formatjs.io/docs/react-intl/api/#message-descriptor) valide à la clé de `i18nSymbols` que vous voulez remplacer. |
| *intl* | Objet | Non | | Le sélecteur de ressources fournit des traductions prêtes à l’emploi par défaut. Vous pouvez sélectionner la langue de traduction en fournissant une chaîne de paramètres régionaux valide via la propriété `intl.locale`. Par exemple : `intl={{ locale: "es-es" }}` </br></br>. Les chaînes de paramètres régionaux prises en charge suivent la norme [ISO 639 - Codes](https://www.iso.org/fr/iso-639-language-codes.html) pour la représentation des noms des normes linguistiques. </br></br> Liste des paramètres régionaux pris en charge : anglais (en-us, par défaut), espagnol (es-es), allemand (de-de), français (fr-FR), italien (it-it), japonais (ja-jp), coréen (ko-kr), portugais (pt-br), chinois (traditionnel, zh-cn), chinois (Taïwan, zh-tw). |
| *repositoryId* | Chaîne | Non | &#39;&#39; | Référentiel à partir duquel le sélecteur de ressources charge le contenu. |
| *additionalAemSolutions* | `Array<string>` | Non | [ ] | Il vous permet d’ajouter une liste de référentiels d’AEM supplémentaires. Si aucune information n’est fournie dans cette propriété, seule la bibliothèque de médias ou les référentiels AEM Assets sont pris en compte. |
| *hideTreeNav* | Booléen | Non |  | Indique s’il faut afficher ou masquer la barre latérale de navigation de l’arborescence de ressources. Elle est utilisée uniquement en mode modal et, par conséquent, cette propriété n’a aucun impact en mode rail. |
| *onDrop* | Fonction | Non | | La propriété active la fonctionnalité de dépôt d’une ressource. |
| *dropOptions* | `{allowList?: Object}` | Non | | Configure les options de dépôt à l’aide de la « liste autorisée ». |
| *colorScheme* | Chaîne | Non | | Configure le thème (`light` ou `dark`) du sélecteur de ressources. |
| *handleSelection* | Fonction | Non | | Appelée avec un tableau d’éléments de ressource lorsque des ressources sont sélectionnées et que vous cliquez sur le bouton `Select` en mode modal. Cette fonction est uniquement appelée en mode modal. En mode rail, utilisez les fonctions `handleAssetSelection` ou `onDrop`. Exemple : <pre>handleSelection=(assets: Asset[])=> {...}</pre> Voir [Type de ressource sélectionné](#selected-asset-type) pour plus d’informations. |
| *handleAssetSelection* | Fonction | Non | | Appelée avec un tableau d’éléments lorsque les ressources sont sélectionnées ou désélectionnées. Cela s’avère utile si vous souhaitez écouter les ressources lorsque l’utilisateur ou l’utilisatrice les sélectionne. Exemple : <pre>handleSelection=(assets: Asset[])=> {...}</pre> Voir [Type de ressource sélectionné](#selected-asset-type) pour plus d’informations. |
| *onClose* | Fonction | Non | | Appelée lorsque vous cliquez sur le bouton `Close` en mode modal. Cette fonction est uniquement appelée en mode `modal` et n’est pas prise en compte en mode `rail`. |
| *onFilterSubmit* | Fonction | Non | | Appelée avec des éléments de filtre lorsque l’utilisateur ou l’utilisatrice modifie des critères de filtre. |
| *selectionType* | Chaîne | Non | Célibataire | Configuration pour la sélection `single` ou `multiple` de ressources à la fois. |
| *dragOptions.liste autorisée* | booléen | Non | | La propriété est utilisée pour autoriser ou refuser le déplacement des ressources qui ne peuvent pas être sélectionnées. |
| *aemLevelType* | Chaîne | Non |  | Il vous permet de choisir d’afficher les ressources du niveau de diffusion, du niveau auteur ou des deux. <br><br> Syntaxe : `aemTierType:[0]: "author" 1: "delivery"` <br><br> Par exemple, si `["author","delivery"]` sont utilisés, le sélecteur de référentiel affiche les options pour l’auteur et la diffusion. |
| *handleNavigateToAsset* | Fonction | Non | | Il s’agit d’une fonction de rappel permettant de gérer la sélection d’une ressource. |
| *noWrap* | Booléen | Non | | La propriété *noWrap* permet de rendre le sélecteur de ressources dans le panneau du rail latéral. Si cette propriété n’est pas mentionnée, elle effectue le rendu de la *vue de boîte de dialogue* par défaut. |
| *dialogSize* | prise en charge de petite, moyenne, grande, plein écran ou plein écran | Chaîne | Facultatif | Vous pouvez contrôler la mise en page en spécifiant sa taille à l’aide des options données. |
| *colorScheme* | Clair ou foncé | Non | | Cette propriété est utilisée pour définir le thème d’une application de sélecteur de ressources. Vous pouvez choisir entre le thème clair ou sombre. |
| *filterRepoList* | Fonction | Non |  | Vous pouvez utiliser la fonction de rappel `filterRepoList` qui appelle le référentiel Experience Manager et renvoie une liste filtrée de référentiels. |
| *getExpiryStatus* | Fonction | Non | | Elle indique l’état d’une ressource expirée. La fonction renvoie `EXPIRED`, `EXPIRING_SOON` ou `NOT_EXPIRED` en fonction de la date d’expiration d’une ressource que vous fournissez. Voir [Personnaliser les ressources expirées](#customize-expired-assets). |
| *allowSelectionAndDrag* | Booléen | Non | False | La valeur de la fonction peut être `true` ou `false`. Lorsque la valeur est définie sur `false`, la ressource expirée ne peut pas être sélectionnée ou déplacée sur la zone de travail. |
| *showToast* | | Non | | Il permet au sélecteur de ressources d’afficher un message de toast personnalisé pour la ressource expirée. |
<!--
| *expirationDate* | Function | No | | This function is used to set the usability period of an asset. |
| *disableDefaultBehaviour* | Boolean | No | False | It is a function that is used to enable or disable the selection of an expired asset. You can customize the default behavior of an asset that is set to expire. See [customize expired assets](#customize-expired-assets). |
-->

## Exemples d’utilisation des propriétés du sélecteur de ressources {#usage-examples}

Vous pouvez définir les [propriétés](#asset-selector-properties) du sélecteur de ressources dans le fichier `index.html` pour personnaliser l’affichage du sélecteur de ressources dans votre application.

### Exemple 1 : sélecteur de ressources en mode rail

![rail-view-exemple](assets/rail-view-example-vanilla.png)

Si la valeur de AssetSelector `rail` est définie sur `false` ou n’est pas mentionnée dans les propriétés, le sélecteur de ressources s’affiche par défaut dans la vue modale. La propriété `acvConfig` permet de définir des configurations plus détaillées, telles que le glisser-déposer. Visitez [ pour activer ou désactiver le glisser-déposer ](#enable-disable-drag-and-drop) afin de comprendre l’utilisation de la propriété `acvConfig`.

<!--
### Example 2: Use selectedAssets property in addition to the path property

Use the `path` property to define the folder name that displays automatically when the Asset Selector is rendered. In addition, use the `selectedAssets` property to define the IDs for the assets that you need to select within the folder. Moreover, when you want to display assets that are pre-defined within the folder, you can use selectedAssets property.

   ![selected-assets-example](assets/selected-assets-example-vanilla.png)
-->

### Exemple 2 : fenêtre contextuelle de métadonnées

Utilisez différentes propriétés pour définir les métadonnées d’une ressource que vous souhaitez afficher à l’aide d’une icône d’infos. La fenêtre contextuelle d’infos fournit l’ensemble des informations sur la ressource ou le dossier, y compris le titre, les dimensions, la date de modification, l’emplacement et la description d’une ressource. Dans l’exemple ci-dessous, diverses propriétés sont utilisées pour afficher les métadonnées d’une ressource, par exemple : la propriété `repo:path` spécifie l’emplacement d’une ressource. <!--`repo` represents the repository from where the asset is showing, whereas, `path` represents the route from where the asset or folder is rendered.-->

![metadata-popover-example](assets/metadata-popover.png)

### Exemple 3 :propriété de filtre personnalisé dans la vue de rail

En plus de la recherche facettée, le sélecteur Assets vous permet de personnaliser divers attributs pour affiner votre recherche à partir de [!DNL Adobe Experience Manager] en tant qu’application [!DNL Cloud Service]. Ajoutez le code suivant pour ajouter des filtres de recherche personnalisés à votre application. Dans l’exemple ci-dessous, la recherche `Type Filter` qui filtre le type de ressource parmi les Images, Documents ou Vidéos ou le type de filtre que vous avez ajouté pour la recherche.

![custom-filter-example-vanilla](assets/custom-filter-example-vanilla.png)

<!--

## Customization after integrating Asset Selector 

### Custom metadata

Assets display panel shows the out of the box metadata that can be displayed in the info of the asset. In addition to this, [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application allows configuration of the asset selector by adding custom metadata that is shown in info panel of the asset.
-->

## Fragments de code de configuration fonctionnels{#code-snippets}

Définissez les conditions préalables dans le fichier `index.html` ou un fichier similaire dans l’implémentation de votre application pour définir les détails d’authentification pour accéder au référentiel [!DNL Experience Manager Assets]. Une fois que vous avez terminé, vous pouvez ajouter des fragments de code en fonction de vos besoins.

### Personnalisation du panneau de filtrage {#customize-filter-panel}

Vous pouvez ajouter le fragment de code suivant dans l’objet `assetSelectorProps` pour personnaliser le panneau de filtrage :

```
filterSchema: [
    {
    header: 'File Type',
    groupKey: 'TopGroup',
    fields: [
    {
    element: 'checkbox',
    name: 'type',
    options: [
    {
    label: 'Images',
    value: '<comma separated mimetypes, without space, that denote all images, for e.g., image/>',
    },
    {
    label: 'Videos',
    value: '<comma separated mimetypes, without space, that denote all videos for e.g., video/,model/vnd.mts,application/mxf>'
    }
    ]
    }
    ]
    },
    {
    fields: [
    {
    element: 'checkbox',
    name: 'type',
    options: [
    { label: 'JPG', value: 'image/jpeg' },
    { label: 'PNG', value: 'image/png' },
    { label: 'TIFF', value: 'image/tiff' },
    { label: 'GIF', value: 'image/gif' },
    { label: 'MP4', value: 'video/mp4' }
    ],
    columns: 3,
    },
    ],
    header: 'Mime Types',
    groupKey: 'MimeTypeGroup',
    }},
    {
    fields: [
    {
    element: 'checkbox',
    name: 'property=metadata.application.xcm:keywords.value',
    options: [
    { label: 'Fruits', value: 'fruits' },
    { label: 'Vegetables', value: 'vegetables'}
    ],
    columns: 3,
    },
    ],
    header: 'Food Category',
    groupKey: 'FoodCategoryGroup',
    }
],
```

### Personnalisation des informations dans la vue modale {#customize-info-in-modal-view}

Vous pouvez personnaliser la vue des détails d’une ressource lorsque vous cliquez sur l’icône ![icône d’information](assets/info-icon.svg) . Exécutez le code ci-dessous :

```
// Create an object infoPopoverMap and set the property `infoPopoverMap` with it in assetSelectorProps
const infoPopoverMap = (map) => {
// for example, to skip `path` from the info popover view
let defaultPopoverData = PureJSSelectors.getDefaultInfoPopoverData(map);
return defaultPopoverData.filter((i) => i.label !== 'Path'
};
assetSelectorProps.infoPopoverMap = infoPopoverMap;
```

### Activation ou désactivation du mode glisser-déposer {#enable-disable-drag-and-drop}

Ajoutez les propriétés suivantes à `assetSelectorProp` pour activer le mode glisser-déposer. Pour désactiver la fonction glisser-déposer, remplacez le paramètre `true` par `false`.

```
rail: true,
acvConfig: {
dragOptions: {
allowList: {
'*': true,
},
},
selectionType: 'multiple'
}

// the drop handler to be implemented
function drop(e) {
e.preventDefault();
// following helps you get the selected assets – an array of objects.
const data = JSON.parse(e.dataTransfer.getData('collectionviewdata'));
}
```

### Sélection d’Assets {#selection-of-assets}

Le type de ressource sélectionné est un tableau d’objets qui contient des informations sur les ressources lors de l’utilisation des fonctions `handleSelection`, `handleAssetSelection`, et `onDrop`.

Exécutez les étapes suivantes pour configurer la sélection d’une ou de plusieurs ressources :

```
acvConfig: {
selectionType: 'multiple' // 'single' for single selection
}
// the `handleSelection` callback, always gets you the array of selected assets
```

**Syntaxe du schéma**

```
interface SelectedAsset {
    'repo:id': string;
    'repo:name': string;
    'repo:path': string;
    'repo:size': number;
    'repo:createdBy': string;
    'repo:createDate': string;
    'repo:modifiedBy': string; 
    'repo:modifyDate': string; 
    'dc:format': string; 
    'tiff:imageWidth': number;
    'tiff:imageLength': number;
    'repo:state': string;
    computedMetadata: Record<string, any>;
    _links: {
        'https://ns.adobe.com/adobecloud/rel/rendition': Array<{
            href: string;
            type: string;
            'repo:size': number;
            width: number;
            height: number;
            [others: string]: any;
        }>;
    };
}
```

Le tableau suivant décrit des propriétés importantes de l’objet Ressource sélectionnée.

| Propriété | Type | Description |
|---|---|---|
| *repo:repositoryId* | chaîne | Identifiant unique du référentiel dans lequel la ressource est stockée. |
| *repo:id* | chaîne | Identifiant unique de la ressource. |
| *repo:assetClass* | chaîne | Classification de la ressource (par exemple, image ou vidéo, document). |
| *repo:name* | chaîne | Nom de la ressource, y compris l’extension de fichier. |
| *repo:size* | nombre | Taille de la ressource en octets. |
| *repo:path* | chaîne | Emplacement de la ressource dans le référentiel. |
| *repo:ancestors* | `Array<string>` | Tableau d’éléments ancêtres de la ressource dans le référentiel. |
| *repo:state* | chaîne | État actuel de la ressource dans le référentiel (par exemple, active, supprimée, etc.). |
| *repo:createdBy* | chaîne | L’utilisateur, l’utilisatrice ou le système qui a créé la ressource. |
| *repo:createDate* | chaîne | Date et heure de création de la ressource. |
| *repo:modifiedBy* | chaîne | L’utilisateur, l’utilisatrice ou le système qui a modifié la ressource pour la dernière fois. |
| *repo:modifyDate* | chaîne | Date et heure de la dernière modification de la ressource. |
| *dc:format* | chaîne | Format de la ressource, tel que le type de fichier (par exemple, JPEG, PNG, etc.). |
| *tiff:imageWidth* | nombre | Largeur d’une ressource. |
| *tiff:imageLength* | nombre | Hauteur d’une ressource. |
| *computedMetadata* | `Record<string, any>` | Objet qui représente un compartiment pour tous les types de métadonnées de la ressource (référentiel, application ou métadonnées incorporées). |
| *_links* | `Record<string, any>` | Liens hypermédias pour la ressource associée. Inclut des liens pour des ressources telles que des métadonnées et des rendus. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition>* | `Array<Object>` | Tableau d’objets contenant des informations sur les rendus de la ressource. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].href>* | chaîne | URI du rendu. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].type>* | chaîne | Type MIME du rendu. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].repo:size>&#39;* | nombre | Taille du rendu en octets. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].width>* | nombre | Largeur du rendu. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].height>* | nombre | Hauteur du rendu. |

<!--For a complete list of properties and detailed example, visit [Asset Selector Code Example](https://github.com/adobe/aem-assets-selectors-mfe-examples).-->

### Personnalisation des ressources expirées {#customize-expired-assets}

Le sélecteur de ressources vous permet de contrôler l’utilisation d’une ressource expirée. Vous pouvez personnaliser la ressource expirée avec un badge **Expiration prochaine** qui peut vous aider à connaître à l’avance les ressources qui vont expirer dans les 30 jours à compter de la date actuelle. De plus, il peut être personnalisé selon les besoins. Vous pouvez également autoriser la sélection d’une ressource expirée sur la zone de travail ou vice versa. La personnalisation d’une ressource expirée peut être effectuée à l’aide de fragments de code de différentes manières :

<!--{
    getExpiryStatus: function, // to control Expired/Expiring soon badges of the asset
    allowSelectionAndDrag: boolean, // set true to allow the selection of expired assets on canvas, set false, otherwise.
}-->

```
expiryOptions: {
    getExpiryStatus: getExpiryStatus;
}
```

#### Sélection d’une ressource expirée {#selection-of-expired-asset}

Vous pouvez personnaliser l’utilisation d’une ressource expirée pour la rendre sélectionnable ou non sélectionnable. Vous pouvez personnaliser si vous souhaitez autoriser ou non le glisser-déposer d’une ressource expirée sur le canevas du sélecteur de ressources. Pour ce faire, utilisez les paramètres suivants pour rendre une ressource non sélectionnable sur la zone de travail :

```
expiryOptions:{
    allowSelectionAndDrop: false;
}
```
<!--
Additionally, To do this, navigate to **[!UICONTROL Disable default expiry behavior]** under the [!UICONTROL Controls] tab and set the boolean value to `true` or `false` as per the requirement. If `true` is selected, you can see the select box over the expired asset, otherwise it remains unselected. You can hover to the info icon of an asset to know the details of an expired asset. 

![Disable default expiry behavior](assets/disable-default-expiry-behavior.png)-->

#### Définition de la durée d’une ressource expirée {#set-duration-of-expired-asset}

Le fragment de code suivant vous permet de définir le badge **Expiration prochaine** pour les ressources qui expirent dans les cinq jours suivants : <!--The `expirationDate` property is used to set the expiration duration of an asset. Refer to the code snippet below:-->

```
/**
  const getExpiryStatus = async (asset) => {
  if (!asset.expirationDate) {
    return null;
  }
  const currentDate = new Date();
  const millisecondsInDay = 1000 * 60 * 60 * 24;
  const fiveDaysFromNow = new Date(value: currentDate.getTime() + 5 * millisecondsInDay);
  const expirationDate = new Date(asset.expirationDate);
  if (expirationDate.getTime() < currentDate.getTime()) {
    return 'EXPIRED';
  } else if (expirationDate.getTime() < fiveDaysFromNow.getTime()) {
    return 'EXPIRING_SOON';
  } else {
    return 'NOT_EXPIRED';
  }
};
```

<!--In the above code snippet, the `getExpiryStatus` function is used to show the **Expiring soon** badge that have expiration date stored in `customExpirationDate`. Additionally, it sets the expiration date of an asset to five days from the current date. The `millisecondsInDay` helps you set expiry of an asset by specifying the time range in milliseconds. You can replace milliseconds with hours directly or customize function as per the requirement. Whereas, the `getTime()` function returns the number of milliseconds for the mentioned date. See [properties](#asset-selector-properties) to know about `expirationDate` property.-->

Reportez-vous à l’exemple suivant pour comprendre le fonctionnement de la propriété pour récupérer la date et l’heure actuelles :

```
const currentData = new Date();
currentData.getTime(),
```

renvoie `1718779013959` selon le format de date 2024-06-19T06:36:53.959Z.

#### Personnaliser le message du toast d’une ressource expirée {#customize-toast-message}

La propriété `showToast` est utilisée pour personnaliser le message toast que vous souhaitez afficher sur une ressource expirée.

Syntaxe :

```
{
    type: 'ERROR', 'NEUTRAL', 'INFO', 'SUCCESS',
    message: '<message to be shown>',
    timeout: optional,
}
```

Le délai par défaut est de 500 millisecondes. En revanche, vous pouvez la modifier selon vos besoins. De plus, la transmission de la valeur `timeout: 0` permet de garder le toast ouvert jusqu&#39;à ce que vous cliquiez sur le bouton croix.

Vous trouverez ci-dessous un exemple d’affichage d’un message toast lorsqu’il est nécessaire pour interdire la sélection d’un dossier et afficher un message correspondant :

```
const showToast = {
    type: 'ERROR',
    message: 'Folder cannot be selected',
    timeout: 5000,
}
```

Utilisez le fragment de code suivant pour afficher un message de toast pour l’utilisation d’une ressource expirée :

![message de toast](assets/toast-message.png)

### Filtre d’appel contextuel{#contextual-invocation-filter}

Le sélecteur de ressources vous permet d’ajouter un filtre de sélecteur de balises. Il prend en charge un groupe de balises qui combine toutes les balises pertinentes avec un groupe de balises particulier. En outre, il vous permet de sélectionner des balises supplémentaires correspondant à la ressource que vous recherchez. De plus, vous pouvez définir les groupes de balises par défaut sous le filtre d’appel contextuel qui sont principalement utilisés par vous afin qu’ils vous soient accessibles en déplacement.

> 
>
> * Vous devez ajouter un extrait de code d’appel contextuel pour activer le filtre de balisage dans la recherche.
> * Il est obligatoire d’utiliser la propriété name correspondant au type de groupe de balises `(property=xcm:keywords.id=)`.

Syntaxe :

```
const filterSchema=useMemo(() => {
    return: [
        {
            element: 'taggroup',
            name: 'property=xcm:keywords.id='
        },
    ];
}, []);
```

Pour ajouter des groupes de balises dans le panneau Filtres, il est obligatoire d’ajouter au moins un groupe de balises par défaut. En outre, utilisez le fragment de code ci-dessous pour ajouter les balises par défaut présélectionnées dans le groupe de balises.

```
export const WithAssetTags = (props) = {
const [selectedTags, setSelectedTags] = useState (
new Set(['orientation', 'color', 'facebook', 'experience-fragments:', 'dam', 'monochrome'])
const handleSelectTags = (selected) => {
setSelectedTags (new Set (selected)) ;
};
const filterSchema = useMemo ((); => {
    return {
        schema: [
            ｛
                fields: [
                    {
                    element: 'checkbox', 
                    name: 'property=xcm:keywords=', 
                    defaultValue: Array. from(selectedTags), 
                    options: assetTags, 
                    orientation: 'vertical',
                    },
                ],
    header: 'Asset Tags', 
    groupkey: 'AssetTagsGroup',
        ],
    },
｝；
}, [selectedTags]);
```

![filtre de groupe de balises](assets/tag-group.gif)

## Gestion de la sélection de ressources à l’aide du schéma d’objet {#handling-selection}

La propriété `handleSelection` est utilisée pour gérer des sélections uniques ou multiples de ressources dans le sélecteur de ressources. L’exemple ci-dessous indique la syntaxe de l’utilisation de `handleSelection`.

![handle-selection](assets/handling-selection.png)

## Désactivation de la sélection d’Assets {#disable-selection}

L’option Désactiver la sélection permet de masquer ou de désactiver la sélection des ressources ou des dossiers. Elle masque la case à cocher de la carte ou de la ressource qui l’empêche d’être sélectionnée. Pour utiliser cette fonction, vous pouvez déclarer la position d’une ressource ou d’un dossier que vous souhaitez désactiver dans un tableau. Par exemple, si vous souhaitez désactiver la sélection d’un dossier apparaissant à la première position, vous pouvez ajouter le code suivant :
`disableSelection: [0]:folder`

Vous pouvez fournir au tableau une liste des types MIME (images, dossiers, fichiers ou autres types MIME, par exemple image/jpeg) que vous souhaitez désactiver. Les types MIME que vous déclarez sont mappés aux attributs `data-card-type` et `data-card-mimetype` d’une ressource.

En outre, il est possible de faire glisser Assets avec une sélection désactivée. Pour désactiver la fonction glisser-déposer d’un type de ressource spécifique, vous pouvez utiliser la propriété `dragOptions.allowList` .

La syntaxe de la sélection de désactivation est la suivante :

```
(args)=> {
    return(
        <ASDialogWrapper
            {...args}
            disableSelection={args.disableSelection}
            handleAssetSelection={action('handleAssetSelection')}
            handleSelection={action('handleSelection')}
            selectionType={args.selectionType}
        />
    );
}
```

>[!NOTE]
>
> Dans le cas d’une ressource, la case à cocher de sélection est masquée, alors que dans le cas d’un dossier, il n’est pas possible de sélectionner le dossier, mais la navigation du dossier en question continue à s’afficher.

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

Pour masquer les dossiers dans le volet de navigation de gauche, cliquez sur l’icône **[!UICONTROL Masquer les dossiers]**. Pour annuler les modifications, cliquez à nouveau sur l’icône **[!UICONTROL Masquer les dossiers]**.

### Sélecteur de référentiels {#repository-switcher}

Le sélecteur de ressources vous permet également de basculer entre des référentiels pour la sélection de ressources. Vous pouvez sélectionner le référentiel de votre choix dans la liste déroulante disponible dans le panneau de gauche. Les options de référentiel disponibles dans la liste déroulante reposent sur la propriété `repositoryId` définie dans le fichier `index.html`. Il est basé sur l’environnement de l’organisation IMS sélectionnée accessible par l’utilisateur connecté. Les clientes et clients peuvent transmettre une préférence `repositoryID` et, dans ce cas, le sélecteur de ressources arrête le rendu du sélecteur de référentiels et effectue uniquement le rendu des ressources à partir du référentiel donné.

### Référentiel de ressources

Il s’agit d’une collection de dossiers de ressources que vous pouvez utiliser pour effectuer des opérations.

### Filtres prêts à l’emploi {#filters}

Le sélecteur de ressources fournit également des options de filtres prêts à l’emploi pour affiner vos résultats de recherche. Les filtres suivants sont disponibles :

* **[!UICONTROL Status] :** inclut l’état actuel de la ressource parmi `all`, `approved`, `rejected` ou `no status`.
* **[!UICONTROL Type de fichier] :** comprend `folder`, `file`, `images`, `documents` ou `video`.
* **[!UICONTROL État d’expiration] :** mentionne les ressources en fonction de leur durée d’expiration. Vous pouvez cocher la case `[!UICONTROL Expired]` pour filtrer les ressources expirées ou définir `[!UICONTROL Expiration Duration]` d’une ressource pour afficher les ressources en fonction de leur durée d’expiration. Lorsqu’une ressource arrive déjà à expiration ou est sur le point d’expirer, un badge s’affiche, qui la représente. De plus, vous pouvez contrôler si vous souhaitez autoriser l’utilisation (ou le glisser-déposer) d’une ressource expirée. Pour en savoir plus sur la [personnalisation des ressources expirées](#customize-expired-assets). Par défaut, le badge **Expiration prochaine** s’affiche pour les ressources qui expirent dans les 30 prochains jours. Cependant, vous pouvez configurer l’expiration à l’aide de la propriété `expirationDate` .

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

<!--
### Modes to view Asset Selector

Asset Selector supports two types of out of the box views:

**  Modal view or Inline view:** The modal view or inline view is the default view of Asset Selector that represents Assets folders in the front area. The modal view allows users to view assets in a full screen to ease the selection of multiple assets for import. Use `<AssetSelector rail={false}>` to enable modal view.

    ![modal-view](assets/modal-view.png)

**  Rail view:** The rail view represents Assets folders in a left panel. The drag and drop of assets can be performed in this view. Use `<AssetSelector rail={true}>` to enable rail view.

    ![rail-view](assets/rail-view.png)
-->
<!--

### Application Integration

Asset Selector is flexible and can be integrated within your existing [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application. It is accessible and localized to add, search, and select assets in your application. With Asset Selector you can:
*   **Configure** You can configure the files/folders that you want to show at the upfront. The assets that are chosen to view can be of any supported formats, for example, JPEG. It lets you control the display of various text or symbols as per your choice.
*   **Perfect fit** Asset selector easily fits in your existing [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application and choose the way you want to view. The mode of view can be inline, rail, or modal view.
*   **Accessible** With Asset Selector, you can reach the desired asset in an easy manner.
*   **Localize** Assets can be availed for the various locales available as per Adobe's localization standards.
-->
<!--

### Support for multiple instances

The micro front-end design supports the display of multiple instances of Asset Selector on a single screen.

![multiple-instance](assets/multiple-instance.png)
-->

<!--

### Controlled selection with multi-select

You can make default multi-selection of assets by specifying the assets to the component using `selectedAssets` property. You should specify an array of asset IDs. For example, `[{id: 'urn:234}, {id: 'urn:555'}].`
-->
<!--

### Action buttons

When you customize your application with Asset Selector based on ReactJS, you are provided with the following action buttons to perform various actions:
*   **Open in media library** Lets you open the asset in media library.
*   **Upload** Lets you upload an asset directly.
*   **Download** Downloads the asset in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
-->
<!--

### Status of an asset

Asset Selector lets you know the status of your uploaded assets. The status can be `Approved`, `Rejected`, or `Expired` of the asset. 
-->
<!--

### Localization

The integration of Asset Selector with [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] allows localized content appear in your application.
-->



<!--Best Practice-->
<!--
+++**Control default selection of the filter**
You can make the selection of filter default by implementing the following code snippet:

```
"defaultValue": [
    "image/*",
    "application/*"
],

{
    "label": "Documents",
    "value": "application/*"
}
```

+++
-->
