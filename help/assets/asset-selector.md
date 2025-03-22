---
title: Sélecteur de ressources pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Utilisez le sélecteur de ressources pour rechercher, trouver et récupérer les métadonnées et les rendus des ressources dans votre application.
contentOwner: KK
feature: Selectors
role: Admin,User
exl-id: 5f962162-ad6f-4888-8b39-bf5632f4f298
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '5385'
ht-degree: 41%

---

# Sélecteur de ressources micro front-end {#Overview}

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

Le sélecteur de ressources micro front-end fournit une interface utilisateur qui s’intègre facilement au référentiel [!DNL Experience Manager Assets] afin que vous puissiez parcourir ou rechercher des ressources numériques disponibles dans le référentiel et les utiliser dans votre expérience de création d’applications.

L’interface utilisateur micro front-end est mise à disposition dans votre expérience de l’application à l’aide du package Sélecteur de ressources. Toutes les mises à jour du package sont automatiquement importées et le dernier sélecteur de ressources déployé est automatiquement téléchargé dans votre application.

![Présentation](assets/overview.png)

Le sélecteur de ressources offre de nombreux avantages, notamment :

* Facilité d’intégration à l’une des applications [Adobe](#asset-selector-ims) ou [non-Adobe](#asset-selector-non-ims) utilisant la bibliothèque JavaScript Vanilla.
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

## Prérequis{#prereqs}

Vous devez vous assurer que les méthodes de communication suivantes sont disponibles :

* L’application s’exécute sur HTTPS.
* L’URL de l’application se trouve dans la liste autorisée d’URL de redirection du client IMS.
* Le flux de connexion IMS est configuré et rendu à l’aide d’une fenêtre contextuelle sur le navigateur web. Par conséquent, les fenêtres contextuelles doivent être activées ou autorisées sur le navigateur cible.

Utilisez les conditions préalables ci-dessus si vous avez besoin du workflow d’authentification IMS du sélecteur de ressources. Si votre authentification est déjà effective avec le workflow IMS, vous pouvez également ajouter les informations IMS à la place.

>[!IMPORTANT]
>
> Ce référentiel est destiné à servir de documentation supplémentaire décrivant les API disponibles et les exemples d’utilisation pour l’intégration du sélecteur de ressources. Avant d’essayer d’installer ou d’utiliser le sélecteur de ressources, assurez-vous que votre organisation a reçu l’accès au sélecteur de ressources dans le cadre du profil Experience Manager Assets as a Cloud Service. Si vous n’avez pas reçu les privilèges d’accès, vous ne pouvez pas intégrer ni utiliser ces composants. Pour demander la mise en service, l’administrateur de votre programme doit envoyer un ticket d’assistance P2 à Admin Console et inclure les informations suivantes :
>
>* Noms de domaine dans lesquels l’application d’intégration est hébergée.
>* Après l’approvisionnement, votre organisation reçoit `imsClientId`, `imsScope` et une `redirectUrl` correspondant aux environnements demandés qui sont essentiels à la configuration du sélecteur de ressources. Sans ces propriétés valides, vous ne pouvez pas exécuter les étapes d’installation.

## Installation {#installation}

Les sélecteurs de destination sont disponibles via le réseau CDN ESM (par exemple, [esm.sh](https://esm.sh/)/[skypack](https://www.skypack.dev/)) et la version [UMD](https://github.com/umdjs/umd).

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

Vous pouvez intégrer n’importe quelle application [!DNL Adobe] ou non Adobe à [!DNL Experience Manager Assets] référentiel et sélectionner des ressources dans l’application. Voir [ Intégration du sélecteur de ressources à diverses applications ](#asset-selector-integration-with-apps).

L’intégration est effectuée en important le package Sélecteur de ressources et en se connectant à Assets as a Cloud Service à l’aide de la bibliothèque JavaScript Vanilla. Modifiez un `index.html` ou tout fichier approprié dans votre application pour :

* Définition des détails d’authentification
* Accès au référentiel Assets as a Cloud Service
* Configuration des propriétés d’affichage du sélecteur de ressources

Vous pouvez effectuer une authentification sans définir certaines des propriétés IMS, si :

* Vous intégrez une application [!DNL Adobe] sur [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=fr).
* Un jeton IMS est déjà généré pour l’authentification.

## Intégration du sélecteur de ressources à diverses applications {#asset-selector-integration-with-apps}

Vous pouvez intégrer le sélecteur de ressources à diverses applications, telles que :

* [Intégration du sélecteur de ressources à une application  [!DNL Adobe] ](#adobe-app-integration-vanilla)
* [Intégrer le sélecteur de ressources à une application non Adobe](#adobe-non-app-integration)
* [Intégration de Dynamic Media aux fonctionnalités OpenAPI](#adobe-app-integration-polaris)

>[!BEGINTABS]

<!--Integration with an Adobe application content starts here-->

>[!TAB Intégration à une application Adobe]

### Prérequis{#prereqs-adobe-app}

Utilisez les conditions préalables suivantes si vous intégrez le sélecteur de ressources à une application [!DNL Adobe] :

* [Méthodes de communication](#prereqs)
* imsOrg
* imsToken
* apikey

### Intégration du sélecteur de ressources à une application [!DNL Adobe] {#adobe-app-integration-vanilla}

L’exemple suivant illustre l’utilisation du sélecteur de ressources lors de l’exécution d’une application [!DNL Adobe] sous Unified Shell ou lorsque vous avez déjà généré des `imsToken` pour l’authentification.

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
Les propriétés `ImsAuthProps` définissent les informations d’authentification et le flux que le sélecteur de ressources utilise pour obtenir une `imsToken`. En définissant ces propriétés, vous pouvez contrôler le comportement du flux d’authentification et enregistrer des écouteurs pour divers événements d’authentification.

| Nom de la propriété | Description |
|---|---|
| `imsClientId` | Valeur de chaîne représentant l’identifiant client IMS utilisé à des fins d’authentification. Cette valeur est fournie par Adobe et est spécifique à votre organisation Adobe AEM CS. |
| `imsScope` | Décrit les portées utilisées dans l’authentification. Les portées déterminent le niveau d’accès de l’application aux ressources de votre organisation. Plusieurs portées peuvent être séparées par des virgules. |
| `redirectUrl` | Représente l’URL de redirection de l’utilisateur après l’authentification. Cette valeur est généralement définie sur l’URL actuelle de l’application. Si aucun `redirectUrl` n’est fourni, `ImsAuthService` utilise redirectUrl pour enregistrer les `imsClientId` |
| `modalMode` | Valeur booléenne indiquant si le flux d’authentification doit être affiché dans une fenêtre modale (pop-up) ou non. S’il est défini sur `true`, le flux d’authentification s’affiche dans un pop-up. S’il est défini sur `false`, le flux d’authentification s’affiche lors d’un rechargement complet de la page. _Remarque :_ pour une meilleure expérience utilisateur, vous pouvez contrôler dynamiquement cette valeur si le pop-up du navigateur est désactivé. |
| `onImsServiceInitialized` | Une fonction de rappel appelée lors de l’initialisation du service d’authentification Adobe IMS. Cette fonction accepte un paramètre, `service`, qui est un objet représentant le service Adobe IMS. Voir [`ImsAuthService`](#imsauthservice-ims-auth-service) pour plus d’informations. |
| `onAccessTokenReceived` | Une fonction de rappel appelée lorsqu’un `imsToken` est reçu du service d’authentification Adobe IMS. Cette fonction accepte un paramètre, `imsToken`, qui est une chaîne représentant le jeton d’accès. |
| `onAccessTokenExpired` | Fonction de rappel appelée lorsqu’un jeton d’accès a expiré. Cette fonction est généralement utilisée pour déclencher un nouveau flux d’authentification afin d’obtenir un nouveau jeton d’accès. |
| `onErrorReceived` | Une fonction de rappel appelée lorsqu’une erreur se produit lors de l’authentification. Cette fonction utilise deux paramètres : le type d’erreur et le message d’erreur. Le type d’erreur est une chaîne représentant le type d’erreur et le message d’erreur est une chaîne représentant le message d’erreur. |

+++

+++**ImsAuthService**
`ImsAuthService` classe gère le flux d’authentification pour le sélecteur de ressources. Il est chargé d’obtenir un `imsToken` du service d’authentification Adobe IMS. Le `imsToken` permet d’authentifier l’utilisateur et d’autoriser l’accès au référentiel [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Assets. ImsAuthService utilise les propriétés `ImsAuthProps` pour contrôler le flux d’authentification et enregistrer des écouteurs pour divers événements d’authentification. Vous pouvez utiliser la fonction [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) pratique pour enregistrer l’instance _ImsAuthService_ avec le sélecteur de ressources. Les fonctions suivantes sont disponibles dans la classe `ImsAuthService`. Cependant, si vous utilisez la fonction _registerAssetsSelectorsAuthService_, vous n’avez pas besoin d’appeler directement ces fonctions.

| Nom de la fonction | Description |
|---|---|
| `isSignedInUser` | Détermine si l’utilisateur est actuellement connecté au service et renvoie une valeur booléenne en conséquence. |
| `getImsToken` | Récupère le `imsToken` d’authentification de l’utilisateur actuellement connecté, qui peut être utilisé pour authentifier des requêtes à d’autres services, tels que la génération du _rendu de ressource. |
| `signIn` | Lance le processus de connexion de l’utilisateur. Cette fonction utilise le `ImsAuthProps` pour afficher l’authentification dans un pop-up ou un rechargement complet de la page |
| `signOut` | Déconnecte l’utilisateur du service, invalide son jeton d’authentification et exige qu’il se reconnecte pour accéder aux ressources protégées. Appeler cette fonction recharge la page active. |
| `refreshToken` | Actualise le jeton d’authentification de l’utilisateur actuellement connecté, ce qui empêche son expiration et garantit un accès ininterrompu aux ressources protégées. Renvoie un nouveau jeton d’authentification pouvant être utilisé pour les requêtes suivantes. |

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

+++**Enregistrement des rappels vers le service IMS**

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

>[!TAB Intégration à une application non Adobe]

<!--### Integrate Asset Selector with a [!DNL non-Adobe] application {#adobe-non-app-integration}-->

### Prérequis {#prereqs-non-adobe-app}

Utilisez les conditions préalables suivantes si vous intégrez le sélecteur de ressources à une application non Adobe :

* [Méthodes de communication](#prereqs)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Le sélecteur de ressources prend en charge l’authentification au référentiel [!DNL Experience Manager Assets] à l’aide des propriétés IMS (Identity Management System) telles que `imsScope` ou `imsClientID` lorsque vous l’intégrez à une application non Adobe.

+++**Configuration du sélecteur de ressources pour une application non Adobe**
Pour configurer le sélecteur de ressources pour une application non Adobe, vous devez d’abord enregistrer un ticket d’assistance pour la mise en service, puis suivre les étapes d’intégration.

**Enregistrer un ticket d’assistance**
Procédure pour enregistrer un ticket d’assistance via l’Admin Console :

1. Ajoutez **Sélecteur de ressources avec AEM Assets** dans le titre du ticket.

1. Dans la description, veuillez fournir les détails suivants :

   * [!DNL Experience Manager Assets] comme URL [!DNL Cloud Service] (ID de programme et ID d’environnement).
   * Noms de domaine dans lesquels l’application web autre qu’Adobe est hébergée.
+++

+++**Étapes d’intégration**
Utilisez cet exemple de fichier `index.html` pour l’authentification lors de l’intégration du sélecteur de ressources à une application non Adobe.

Accédez au package Sélecteur de ressources à l’aide de la balise `Script`, comme illustré dans *ligne 9* à *ligne 11* de l’exemple de fichier `index.html`.

*Ligne 14* à *ligne 38* de l’exemple décrit les propriétés de flux IMS, telles que `imsClientId`, `imsScope` et `redirectURL`. La fonction requiert que vous définissiez au moins l’une des propriétés `imsClientId` et `imsScope`. Si vous ne définissez pas de valeur pour `redirectURL`, l’URL de redirection enregistrée pour l’ID client est utilisée.

Comme aucun `imsToken` n’est généré, utilisez les fonctions `registerAssetsSelectorsAuthService` et `renderAssetSelectorWithAuthFlow`, comme indiqué dans les lignes 40 à 50 de l’exemple de fichier `index.html`. Utilisez la fonction `registerAssetsSelectorsAuthService` avant de `renderAssetSelectorWithAuthFlow` pour enregistrer le `imsToken` avec le sélecteur de ressources. [!DNL Adobe] recommande d’appeler `registerAssetsSelectorsAuthService` lorsque vous instanciez le composant .

Définissez l’authentification et les autres propriétés liées à l’accès Assets as a Cloud Service dans la section `const props`, comme illustré dans *ligne 54* à *ligne 60* de l’exemple de fichier `index.html`.

La variable globale `PureJSSelectors`, mentionnée à la ligne *65*, est utilisée pour effectuer le rendu du sélecteur de ressources dans le navigateur web.

Le sélecteur de ressources est rendu sur l’élément de conteneur `<div>`, comme indiqué dans *ligne 74* à *ligne 81*. Cet exemple utilise une boîte de dialogue pour afficher le sélecteur de ressources.

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

+++**Accès au référentiel de diffusion impossible**

>[!TIP]
>
>Si vous avez intégré le sélecteur de ressources à l’aide du workflow de connexion à l’inscription mais que vous ne pouvez toujours pas accéder au référentiel de diffusion, assurez-vous que les cookies de navigateur sont nettoyés. Sinon, vous obtenez `invalid_credentials All session cookies are empty` erreur dans la console.

+++

<!--Integration with Polaris application content starts here-->

>[!TAB Intégration de Dynamic Media aux fonctionnalités OpenAPI]

### Prérequis {#prereqs-polaris}

Utilisez les conditions préalables suivantes si vous intégrez le sélecteur de ressources à Dynamic Media avec des fonctionnalités OpenAPI :

* [Méthodes de communication](#prereqs)
* Pour accéder à Dynamic Media avec des fonctionnalités OpenAPI, vous devez disposer de licences pour :
   * Référentiel Assets (par exemple, Experience Manager Assets as a Cloud Service).
   * AEM Dynamic Media.
* Seules les ressources [ approuvées ](#approved-assets.md) peuvent être utilisées pour garantir la cohérence de la marque.

### Intégration de Dynamic Media aux fonctionnalités OpenAPI{#adobe-app-integration-polaris}

L’intégration du sélecteur de ressources avec le processus OpenAPI Dynamic Media implique différentes étapes, notamment la création d’une URL Dynamic Media personnalisée ou l’obtention d’une URL Dynamic Media prête à être sélectionnée, etc.

+++**Intégration du sélecteur de ressources pour Dynamic Media aux fonctionnalités OpenAPI**

Les propriétés `rootPath` et `path` ne doivent pas faire partie de Dynamic Media avec les fonctionnalités OpenAPI. Vous pouvez plutôt configurer la propriété `aemTierType` . Voici la syntaxe de la configuration :

```
aemTierType:[1: "delivery"]
```

Cette configuration vous permet d’afficher toutes les ressources approuvées sans dossiers ou sous la forme d’une structure plate. Pour plus d’informations, accédez à `aemTierType` propriété sous [ Propriétés du sélecteur de ressources ](#asset-selector-properties)

+++

+++**Créer une URL de diffusion dynamique à partir de ressources approuvées**
Une fois que vous avez configuré le sélecteur de ressources, un schéma d’objets est utilisé pour créer une URL de diffusion dynamique à partir des ressources sélectionnées.
Par exemple, le schéma d’un objet d’un tableau d’objets reçu lors de la sélection d’une ressource :

```
{
"dc:format": "image/jpeg",
"repo:assetId": "urn:aaid:aem:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
"repo:name": "image-7.jpg",
"repo:repositoryId": "delivery-pxxxx-exxxxxx.adobe.com",
...
}
```

Toutes les ressources sélectionnées sont transportées par `handleSelection` fonction qui agit comme un objet JSON. Par exemple, `JsonObj`. L’URL de diffusion dynamique est créée en combinant les opérateurs ci-dessous :

| Objet | JSON |
|---|---|
| Hôte | `assetJsonObj["repo:repositoryId"]` |
| Racine de l’API | `/adobe/dynamicmedia/deliver` |
| asset-id | `assetJsonObj["repo:assetId"]` |
| seo-name | `assetJsonObj["repo:name"].split(".").slice(0,-1).join(".")` |
| format | `.jpg` |

**Spécification de l’API de diffusion des ressources validée**

Format de l&#39;URL :
`https://<delivery-api-host>/adobe/dynamicmedia/deliver/<asset-id>/<seo-name>.<format>?<image-modification-query-parameters>`

Où,

* L’hôte est `https://delivery-pxxxxx-exxxxxx.adobe.com`
* La racine de l’API est `"/adobe/dynamicmedia/deliver"`
* `<asset-id>` est l’identifiant de la ressource
* `<seo-name>` est le nom d’une ressource
* `<format>` est le format de sortie
* `<image modification query parameters>` comme prise en charge par la spécification de l’API de diffusion des ressources approuvées

**API de diffusion de ressources approuvées**

L’URL de diffusion dynamique possède la syntaxe suivante :
`https://<delivery-api-host>/adobe/assets/deliver/<asset-id>/<seo-name>`, où,

* L’hôte est `https://delivery-pxxxxx-exxxxxx.adobe.com`
* La racine de l’API pour la diffusion du rendu original est `"/adobe/assets/deliver"`.
* `<asset-id>` est l’identifiant de la ressource
* `<seo-name>`est le nom de la ressource qui peut ou non avoir une extension

+++

+++**Prêt à sélectionner l’URL de diffusion dynamique**
Toutes les ressources sélectionnées sont transportées par `handleSelection` fonction qui agit comme un objet JSON. Par exemple, `JsonObj`. L’URL de diffusion dynamique est créée en combinant les opérateurs ci-dessous :

| Objet | JSON |
|---|---|
| Hôte | `assetJsonObj["repo:repositoryId"]` |
| Racine de l’API | `/adobe/assets/deliver` |
| asset-id | `assetJsonObj["repo:assetId"]` |
| seo-name | `assetJsonObj["repo:name"]` |

Vous trouverez ci-dessous les deux façons de parcourir l’objet JSON :

![URL de diffusion dynamique](assets/dynamic-delivery-url.png)

* **Miniature :** les miniatures peuvent être des images et les ressources sont des PDF, des vidéos, des images, etc. Vous pouvez toutefois utiliser les attributs de hauteur et de largeur de la miniature d’une ressource comme rendu de diffusion dynamique.
L’ensemble de rendus suivant peut être utilisé pour les ressources de type PDF :
Une fois qu’un PDF est sélectionné dans le sidekick, le contexte de sélection propose les informations ci-dessous. Vous trouverez ci-dessous la manière de parcourir l’objet JSON :

  <!--![Thumbnail dynamic delivery url](image-1.png)-->

  Vous pouvez vous reporter à `selection[0].....selection[4]` pour le tableau du lien de rendu à partir de la capture d’écran ci-dessus. Par exemple, les propriétés de clé de l’un des rendus de miniature sont les suivantes :

  ```
  { 
      "height": 319, 
      "width": 319, 
      "href": "https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:8560f3a1-d9cf-429d-a8b8-d81084a42d41/as/algorithm design.jpg?accept-experimental=1&width=319&height=319&preferwebp=true", 
      "type": "image/webp" 
  } 
  ```

Dans la capture d’écran ci-dessus, l’URL de diffusion du rendu original PDF doit être incorporée dans l’expérience cible si PDF est requis, et non sa miniature. Par exemple, `https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:8560f3a1-d9cf-429d-a8b8-d81084a42d41/original/as/algorithm design.pdf?accept-experimental=1`.

* **Vidéo :** vous pouvez utiliser l’URL du lecteur vidéo pour les ressources de type vidéo qui utilisent un iFrame incorporé. Vous pouvez utiliser les rendus de tableau suivants dans l’expérience cible :
  <!--![Video dynamic delivery url](image.png)-->

  ```
  { 
      "height": 319, 
      "width": 319, 
      "href": "https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:2fdef732-a452-45a8-b58b-09df1a5173cd/as/asDragDrop.2.jpg?accept-experimental=1&width=319&height=319&preferwebp=true", 
      "type": "image/webp" 
  } 
  ```

  Vous pouvez vous reporter à `selection[0].....selection[4]` pour le tableau du lien de rendu à partir de la capture d’écran ci-dessus. Par exemple, les propriétés de clé de l’un des rendus de miniature sont les suivantes :

  L’extrait de code de la capture d’écran ci-dessus est un exemple de ressource vidéo. Il comprend un tableau de liens de rendus. La `selection[5]` dans l’extrait est l’exemple de miniature d’image qui peut être utilisée comme espace réservé de la miniature vidéo dans l’expérience cible. La `selection[5]` dans le tableau des rendus est pour le lecteur vidéo. Elle sert d’HTML et peut être définie comme `src` de l’iframe. Il prend en charge la diffusion en continu à débit adaptatif, qui est une diffusion de la vidéo optimisée pour le web.

  Dans l’exemple ci-dessus, l’URL du lecteur vidéo est `https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:2fdef732-a452-45a8-b58b-09df1a5173cd/play?accept-experimental=1`

+++**Interface utilisateur du sélecteur de ressources pour Dynamic Media avec les fonctionnalités OpenAPI**

Après l’intégration au sélecteur de ressources micro front-end d’Adobe, vous ne pouvez voir que la structure de toutes les ressources approuvées disponibles dans le référentiel de ressources Experience Manager.

![Dynamic Media avec interface utilisateur des fonctionnalités OpenAPI](assets/polaris-ui.png)

* **A** : [masquer/afficher le panneau](#hide-show-panel)
* **B** : [Assets](#repository)
* **C** : [Tri](#sorting)
* **D** : [filtres](#filters)
* **E** : [barre de recherche](#search-bar)
* **F** : [tri par ordre croissant ou décroissant](#sorting)
* **G** : Annuler la sélection
* **H** : sélectionner une ou plusieurs ressources

+++

+++**Configurer des filtres personnalisés**
Le sélecteur de ressources pour Dynamic Media avec les fonctionnalités OpenAPI vous permet de configurer des propriétés personnalisées et des filtres basés sur celles-ci. La propriété `filterSchema` est utilisée pour configurer ces propriétés. La personnalisation peut être exposée en tant que `metadata.<metadata bucket>.<property name>.` par rapport auxquelles les filtres peuvent être configurés, où,

* `metadata` est l’information d’une ressource
* `embedded` est le paramètre statique utilisé pour la configuration, et
* `<propertyname>` est le nom du filtre que vous configurez

Pour la configuration, les propriétés définies au niveau de l’`jcr:content/metadata/` sont exposées comme `metadata.<metadata bucket>.<property name>.` pour les filtres que vous souhaitez configurer.

Par exemple, dans le sélecteur de ressources pour Dynamic Media avec les fonctionnalités OpenAPI , une propriété sur `asset jcr:content/metadata/client_name:market` est convertie en `metadata.embedded.client_name:market` pour la configuration des filtres.

Pour obtenir le nom, une activité unique doit être effectuée. Effectuez un appel API de recherche pour la ressource et obtenez le nom de la propriété (le compartiment, essentiellement).

+++

>[!ENDTABS]

## Propriétés du sélecteur de ressources {#asset-selector-properties}

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
| *handleSelection* | Fonction | Non | | Appelée avec un tableau d’éléments de ressource lorsque des ressources sont sélectionnées et que vous cliquez sur le bouton `Select` en mode modal. Cette fonction est uniquement appelée en mode modal. En mode rail, utilisez les fonctions `handleAssetSelection` ou `onDrop`. Exemple : <pre>handleSelection=(assets: Asset[])=> {...}</pre> Voir [Type de ressource sélectionné](#selected-asset-type) pour plus d’informations. |
| *handleAssetSelection* | Fonction | Non | | Appelée avec un tableau d’éléments lorsque les ressources sont sélectionnées ou désélectionnées. Cela s’avère utile si vous souhaitez écouter les ressources lorsque l’utilisateur ou l’utilisatrice les sélectionne. Exemple : <pre>handleSelection=(assets: Asset[])=> {...}</pre> Voir [Type de ressource sélectionné](#selected-asset-type) pour plus d’informations. |
| *onClose* | Fonction | Non | | Appelée lorsque vous cliquez sur le bouton `Close` en mode modal. Cette fonction est uniquement appelée en mode `modal` et n’est pas prise en compte en mode `rail`. |
| *onFilterSubmit* | Fonction | Non | | Appelée avec des éléments de filtre lorsque l’utilisateur ou l’utilisatrice modifie des critères de filtre. |
| *selectionType* | Chaîne | Non | Célibataire | Configuration pour la sélection `single` ou `multiple` de ressources à la fois. |
| placer sur la liste autorisée *dragOptions.* | booléen | Non | | La propriété permet d’autoriser ou de refuser le déplacement de ressources qui ne sont pas sélectionnables. |
| *aemTierType* | Chaîne | Non |  | Il vous permet de choisir si vous souhaitez afficher les ressources du niveau de diffusion, du niveau de création ou des deux. Syntaxe de <br><br> : `aemTierType:[0]: "author" 1: "delivery"` <br><br> Par exemple, si les deux `["author","delivery"]` sont utilisées, le sélecteur de référentiels affiche des options pour l’auteur et la diffusion. |
| *handleNavigateToAsset* | Fonction | Non | | Il s’agit d’une fonction de rappel permettant de gérer la sélection d’une ressource. |
| *noWrap* | Booléen | Non | | La propriété *noWrap* permet d’effectuer le rendu du sélecteur de ressources dans le panneau du rail latéral. Si cette propriété n’est pas mentionnée, elle affiche la *vue de boîte de dialogue* par défaut. |
| *dialogSize* | prise de contrôle en petit, moyen, grand, plein écran ou plein écran | Chaîne | Facultatif | Vous pouvez contrôler la disposition en spécifiant sa taille à l’aide des options données. |
| *colorScheme* | Clair ou foncé | Non | | Cette propriété est utilisée pour définir le thème d’une application du sélecteur de ressources. Vous pouvez choisir entre le thème clair ou sombre. |
| *filterRepoList* | Fonction | Non |  | Vous pouvez utiliser `filterRepoList` fonction de rappel qui appelle le référentiel Experience Manager et renvoie une liste filtrée de référentiels. |
| *expiryOptions* | Fonction | | | Vous pouvez utiliser entre les deux propriétés suivantes : **getExpiryStatus** qui fournit le statut d’une ressource arrivée à expiration. La fonction renvoie des `EXPIRED`, des `EXPIRING_SOON` ou des `NOT_EXPIRED` en fonction de la date d’expiration d’une ressource que vous fournissez. Voir [ Personnalisation des ressources expirées ](#customize-expired-assets). De plus, vous pouvez utiliser **allowSelectionAndDrag** dans lequel la valeur de la fonction peut être `true` ou `false`. Lorsque la valeur est définie sur `false`, la ressource expirée ne peut pas être sélectionnée ni glissée-déplacée sur la zone de travail. |
| *showToast* | | Non | | Cela permet au sélecteur de ressources d’afficher un message toast personnalisé pour la ressource expirée. |

<!--
| *rootPath* | String | No | /content/dam/ | Folder path from which Asset Selector displays your assets. `rootPath` can also be used in the form of encapsulation. For example, given the following path, `/content/dam/marketing/subfolder/`, Asset Selector does not allow you to traverse through any parent folder, but only displays the children folders. |
| *path* | String | No | | Path that is used to navigate to a specific directory of assets when the Asset Selector is rendered. |
| *expirationDate* | Function | No | | This function is used to set the usability period of an asset. |
| *disableDefaultBehaviour* | Boolean | No | False | It is a function that is used to enable or disable the selection of an expired asset. You can customize the default behavior of an asset that is set to expire. See [customize expired assets](#customize-expired-assets). |
-->

## Exemples d’utilisation des propriétés du sélecteur de ressources {#usage-examples}

Vous pouvez définir les [propriétés](#asset-selector-properties) du sélecteur de ressources dans le fichier `index.html` pour personnaliser l’affichage du sélecteur de ressources dans votre application.

### Exemple 1 : sélecteur de ressources en mode rail

![rail-view-exemple](assets/rail-view-example-vanilla.png)

Si la valeur du `rail` AssetSelector est définie sur `false` ou n’est pas mentionnée dans les propriétés, le sélecteur de ressources s’affiche par défaut en mode modal. La propriété `acvConfig` permet des configurations détaillées, comme la fonction Glisser-déposer. Consultez [activer ou désactiver le glisser-déposer](#enable-disable-drag-and-drop) pour comprendre l’utilisation de `acvConfig` propriété.

<!--
### Example 2: Use selectedAssets property in addition to the path property

Use the `path` property to define the folder name that displays automatically when the Asset Selector is rendered. In addition, use the `selectedAssets` property to define the IDs for the assets that you need to select within the folder. Moreover, when you want to display assets that are pre-defined within the folder, you can use selectedAssets property.

   ![selected-assets-example](assets/selected-assets-example-vanilla.png)
-->

### Exemple 2 : fenêtre contextuelle de métadonnées

Utilisez différentes propriétés pour définir les métadonnées d’une ressource que vous souhaitez afficher à l’aide d’une icône d’infos. La fenêtre contextuelle d’infos fournit l’ensemble des informations sur la ressource ou le dossier, y compris le titre, les dimensions, la date de modification, l’emplacement et la description d’une ressource. Dans l’exemple ci-dessous, diverses propriétés sont utilisées pour afficher les métadonnées d’une ressource, par exemple : la propriété `repo:path` spécifie l’emplacement d’une ressource. <!--`repo` represents the repository from where the asset is showing, whereas, `path` represents the route from where the asset or folder is rendered.-->

![metadata-popover-example](assets/metadata-popover.png)

### Exemple 3 :propriété de filtre personnalisé dans la vue de rail

Outre la recherche à facettes, le sélecteur Assets vous permet de personnaliser divers attributs pour affiner votre recherche à partir de l’application [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]. Ajoutez le code suivant pour ajouter des filtres de recherche personnalisés dans votre application. Dans l’exemple ci-dessous, la recherche `Type Filter` qui filtre le type de ressource parmi les Images, Documents ou Vidéos ou le type de filtre que vous avez ajouté pour la recherche.

![custom-filter-example-vanilla](assets/custom-filter-example-vanilla.png)

<!--

## Customization after integrating Asset Selector 

### Custom metadata

Assets display panel shows the out of the box metadata that can be displayed in the info of the asset. In addition to this, [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application allows configuration of the asset selector by adding custom metadata that is shown in info panel of the asset.
-->

## Fragments de code de configuration fonctionnelle{#code-snippets}

Définissez les conditions préalables dans le fichier `index.html` ou un fichier similaire dans l’implémentation de votre application pour définir les détails d’authentification permettant d’accéder au référentiel [!DNL Experience Manager Assets]. Une fois cette opération terminée, vous pouvez ajouter des fragments de code en fonction de vos besoins.

### Personnaliser le panneau de filtrage {#customize-filter-panel}

Vous pouvez ajouter le fragment de code suivant dans `assetSelectorProps` objet pour personnaliser le panneau de filtrage :

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

### Personnaliser les informations en mode modal {#customize-info-in-modal-view}

Vous pouvez personnaliser la vue des détails d’une ressource en cliquant sur l’icône ![icône d’informations](assets/info-icon.svg). Exécutez le code ci-dessous :

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

Ajoutez les propriétés suivantes aux `assetSelectorProp` pour activer le mode glisser-déposer. Pour désactiver le glisser-déposer, remplacez le paramètre `true` par `false`.

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

Pour configurer la sélection de ressources uniques ou multiples, procédez comme suit :

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

### Personnaliser les ressources expirées {#customize-expired-assets}

Le sélecteur de ressources vous permet de contrôler l’utilisation d’une ressource arrivée à expiration. Vous pouvez personnaliser la ressource arrivée à expiration avec un badge **Expiration imminente** qui peut vous aider à connaître à l’avance les ressources qui arriveront à expiration dans les 30 jours suivant la date actuelle. De plus, cela peut être personnalisé en fonction des besoins. Vous pouvez également autoriser la sélection d’une ressource arrivée à expiration sur la zone de travail ou inversement. La personnalisation d’une ressource arrivée à expiration peut être effectuée à l’aide de certains fragments de code de différentes manières :

<!--{
    getExpiryStatus: function, // to control Expired/Expiring soon badges of the asset
    allowSelectionAndDrag: boolean, // set true to allow the selection of expired assets on canvas, set false, otherwise.
}-->

```
expiryOptions: {
    getExpiryStatus: getExpiryStatus;
}
```

#### Sélection d’une ressource arrivée à expiration {#selection-of-expired-asset}

Vous pouvez personnaliser l’utilisation d’une ressource arrivée à expiration afin de la rendre sélectionnable ou non. Vous pouvez personnaliser l’autorisation du glisser-déposer d’une ressource expirée sur la zone de travail du sélecteur de ressources. Pour ce faire, utilisez les paramètres suivants pour rendre une ressource non sélectionnable sur la zone de travail :

```
expiryOptions:{
    allowSelectionAndDrop: false;
}
```
<!--
Additionally, To do this, navigate to **[!UICONTROL Disable default expiry behavior]** under the [!UICONTROL Controls] tab and set the boolean value to `true` or `false` as per the requirement. If `true` is selected, you can see the select box over the expired asset, otherwise it remains unselected. You can hover to the info icon of an asset to know the details of an expired asset. 

![Disable default expiry behavior](assets/disable-default-expiry-behavior.png)-->

#### Définition de la durée d’une ressource arrivée à expiration {#set-duration-of-expired-asset}

Le fragment de code suivant vous permet de définir **Expiration prochaine** le badge des ressources qui expirent dans les cinq prochains jours : <!--The `expirationDate` property is used to set the expiration duration of an asset. Refer to the code snippet below:-->

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

Reportez-vous à l’exemple suivant pour comprendre comment la propriété fonctionne pour récupérer la date et l’heure actuelles :

```
const currentData = new Date();
currentData.getTime(),
```

renvoie `1718779013959` qui est selon le format de date 2024-06-19T06:36:53.959Z.

#### Personnaliser le message toast d’une ressource expirée {#customize-toast-message}

La propriété `showToast` est utilisée pour personnaliser le message toast que vous souhaitez afficher sur une ressource arrivée à expiration.

Syntaxe :

```
{
    type: 'ERROR', 'NEUTRAL', 'INFO', 'SUCCESS',
    message: '<message to be shown>',
    timeout: optional,
}
```

La temporisation par défaut est de 500 millisecondes. En revanche, vous pouvez la modifier selon vos besoins. En outre, la transmission de la valeur `timeout: 0` garde le toast ouvert jusqu’à ce que vous cliquiez sur la croix.

Vous trouverez ci-dessous un exemple d’affichage d’un message toast lorsqu’il est nécessaire d’interdire la sélection d’un dossier et d’afficher un message correspondant :

```
const showToast = {
    type: 'ERROR',
    message: 'Folder cannot be selected',
    timeout: 5000,
}
```

Utilisez le fragment de code suivant pour afficher un message toast pour l’utilisation d’une ressource arrivée à expiration :

![message toast](assets/toast-message.png)

### Filtre d’appel contextuel{#contextual-invocation-filter}

Le sélecteur de ressources vous permet d’ajouter un filtre de sélecteur de balises. Il prend en charge un groupe de balises qui combine toutes les balises pertinentes à un groupe de balises particulier. En outre, il vous permet de sélectionner des balises supplémentaires correspondant à la ressource que vous recherchez. De plus, vous pouvez également définir les groupes de balises par défaut sous le filtre d’appel contextuel que vous utilisez le plus souvent, afin qu’ils soient accessibles en déplacement.

>
>
> * Vous devez ajouter un fragment de code d’appel contextuel pour activer le filtre de balisage dans la recherche.
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

Pour ajouter des groupes de balises dans le panneau Filtres, il est obligatoire d’ajouter au moins un groupe de balises par défaut. De plus, utilisez le fragment de code ci-dessous pour ajouter les balises par défaut présélectionnées dans le groupe de balises.

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

Désactiver la sélection est utilisé pour masquer ou désactiver la sélection des ressources ou des dossiers. Cela masque la case à cocher de sélection de la carte ou de la ressource, ce qui l’empêche d’être sélectionnée. Pour utiliser cette fonction, vous pouvez déclarer la position d’une ressource ou d’un dossier à désactiver dans un tableau. Par exemple, si vous souhaitez désactiver la sélection d’un dossier apparaissant à la première position, vous pouvez ajouter le code suivant :
`disableSelection: [0]:folder`

Vous pouvez fournir au tableau une liste de types MIME (tels qu’image, dossier, fichier ou autres types MIME, par exemple image/jpeg) que vous souhaitez désactiver. Les types MIME que vous déclarez sont mappés dans les attributs `data-card-type` et `data-card-mimetype` d’une ressource.

De plus, vous pouvez faire glisser Assets avec la sélection désactivée. Pour désactiver le glisser-déposer d’un type de ressource particulier, vous pouvez utiliser `dragOptions.allowList` propriété .

La syntaxe de la désactivation de la sélection est la suivante :

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
> Dans le cas d’une ressource, la case à cocher de sélection est masquée, tandis que dans le cas d’un dossier, la sélection du dossier n’est pas possible, mais la navigation dans le dossier mentionné reste active.

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

Le sélecteur de ressources vous permet également de passer d’un référentiel à l’autre lors de la sélection de ressources. Vous pouvez sélectionner le référentiel de votre choix dans la liste déroulante disponible dans le panneau de gauche. Les options de référentiel disponibles dans la liste déroulante reposent sur la propriété `repositoryId` définie dans le fichier `index.html`. Cela dépend des environnements de l’organisation IMS sélectionnée à laquelle accède l’utilisateur ou l’utilisatrice connectés. Les clientes et clients peuvent transmettre une préférence `repositoryID` et, dans ce cas, le sélecteur de ressources arrête le rendu du sélecteur de référentiels et effectue uniquement le rendu des ressources à partir du référentiel donné.

### Référentiel de ressources

Il s’agit d’une collection de dossiers de ressources que vous pouvez utiliser pour effectuer des opérations.

### Filtres prêts à l’emploi {#filters}

Le sélecteur de ressources fournit également des options de filtres prêts à l’emploi pour affiner vos résultats de recherche. Les filtres suivants sont disponibles :

* **[!UICONTROL Statut] :** inclut le statut actuel de la ressource parmi `all`, `approved`, `rejected` ou `no status`.
* **[!UICONTROL Type de fichier] :** comprend `folder`, `file`, `images`, `documents` ou `video`.
* **[!UICONTROL Statut d’expiration] :** mentionne les ressources en fonction de leur durée d’expiration. Vous pouvez cocher la case `[!UICONTROL Expired]` pour filtrer les ressources expirées ou définir la `[!UICONTROL Expiration Duration]` d’une ressource pour afficher les ressources en fonction de leur durée d’expiration. Lorsqu’une ressource expire déjà ou est sur le point d’expirer, un badge s’affiche et la représente. De plus, vous pouvez contrôler si vous souhaitez autoriser l’utilisation (ou le glisser-déposer) d’une ressource expirée. Pour en savoir plus sur la [personnalisation des ressources expirées](#customize-expired-assets). Par défaut, le badge **Expiration prochaine** s’affiche pour les ressources qui expirent dans les 30 prochains jours. Cependant, vous pouvez configurer l’expiration à l’aide de la propriété `expirationDate`.

  >[!TIP]
  >
  > Si vous souhaitez afficher ou filtrer les ressources en fonction de leur date d’expiration, mentionnez la période dans le champ `[!UICONTROL Expiration Duration]`. Il affiche les ressources qui comportent le badge **Va bientôt expirer**.

* **[!UICONTROL Type MIME] :** comprend `JPG`, `GIF`, `PPTX`, `PNG`, `MP4`, `DOCX`, `TIFF`, `PDF`, `XLSX`.
* **[!UICONTROL Taille de l’image] :** inclut la largeur minimale et maximale, et la hauteur minimale et maximale de l’image.

  ![rail-view-example](assets/filters-asset-selector.png)

### Recherche personnalisée

Outre la recherche en texte intégral, le sélecteur de ressources vous permet de rechercher des ressources dans des fichiers à l’aide d’une recherche personnalisée. Vous pouvez utiliser des filtres de recherche personnalisés en modes Modal et Rail.

![custom-search](assets/custom-search1.png)

Vous pouvez également créer un filtre de recherche par défaut pour enregistrer les champs que vous recherchez fréquemment et les utiliser ultérieurement. Pour créer une recherche personnalisée de vos ressources, vous pouvez utiliser la propriété `filterSchema`.

### Barre de recherche {#search-bar}

Le sélecteur de ressources vous permet d’effectuer une recherche de texte intégral des ressources dans le référentiel sélectionné. Par exemple, si vous saisissez le mot-clé `wave` dans la barre de recherche, toutes les ressources qui contiennent le mot-clé `wave` dans l’une des propriétés de métadonnées s’affichent.

### Tri {#sorting}

Vous pouvez trier les ressources du sélecteur de ressources selon le nom, les dimensions ou la taille d’une ressource. Vous pouvez également trier les ressources par ordre croissant ou décroissant.

### Types de vues {#types-of-view}

Le sélecteur de ressources vous permet d’afficher la ressource dans quatre vues différentes :

* **![vue liste](assets/do-not-localize/list-view.png) [!UICONTROL Vue Liste]** : la vue Liste affiche les fichiers et dossiers à faire défiler dans une seule colonne.
* **![vue grille](assets/do-not-localize/grid-view.png) [!UICONTROL Vue Grille]** : la vue Grille affiche les fichiers et dossiers à faire défiler dans une grille de lignes et de colonnes.
* **![vue galerie](assets/do-not-localize/gallery-view.png) [!UICONTROL Vue Galerie]** : la vue Galerie affiche les fichiers ou les dossiers dans une liste horizontale verrouillée au milieu.
* **![vue cascade](assets/do-not-localize/waterfall-view.png) [!UICONTROL Vue Cascade]** : la vue Cascade affiche les fichiers ou les dossiers sous la forme d’un pont.

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
