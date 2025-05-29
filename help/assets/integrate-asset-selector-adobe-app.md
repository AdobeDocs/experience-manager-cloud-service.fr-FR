---
title: 'Intégration du sélecteur de ressources à l’application  [!DNL Adobe] '
description: Intégrer le sélecteur de ressources à diverses applications Adobe, non Adobe et tierces.
role: Admin, User
exl-id: a0c030e2-2213-406b-ad92-4761f1e2ee9f
source-git-commit: 08fc43bc8edeea91bfeb01f053d435e136658e7f
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 19%

---

# Intégration du sélecteur de ressources à l’application Adobe {#integrate-asset-selector-with-adobe-app}

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

Le sélecteur de ressources vous permet de les intégrer à l’aide de diverses applications Adobe afin de leur permettre de travailler ensemble en toute transparence.

## Prérequis{#prereqs-adobe-app}

Utilisez les conditions préalables suivantes si vous intégrez le sélecteur de ressources à une application [!DNL Adobe] :

* [Méthodes de communication](/help/assets/overview-asset-selector.md#prereqs)
* imsOrg
* imsToken
* apikey

## Intégration du sélecteur de ressources à une application [!DNL Adobe] {#adobe-app-integration-vanilla}

L’exemple suivant illustre l’utilisation du sélecteur de ressources lors de l’exécution d’une application [!DNL Adobe] sous Unified Shell ou lorsque vous avez déjà généré des `imsToken` pour l’authentification.

Insérez le package Sélecteur de ressources dans votre code à l’aide de la balise `script`, comme illustré dans les _lignes 6 à 15_ de l’exemple ci-dessous. Une fois le script chargé, vous pouvez utiliser la variable globale `PureJSSelectors`. Définissez les [propriétés](/help/assets/asset-selector-properties.md) du sélecteur de ressources comme illustré dans les _lignes 16 à 23_. Les propriétés `imsOrg` et `imsToken` sont toutes deux requises pour l’authentification dans l’application Adobe. La propriété `handleSelection` sert à gérer les ressources sélectionnées. Pour effectuer le rendu du sélecteur de ressources, appelez la fonction `renderAssetSelector` comme indiqué dans la _ligne 17_. Le sélecteur de ressources s’affiche dans l’élément de conteneur `<div>`, comme indiqué dans les _lignes 21 et 22_.

En suivant ces étapes, vous pouvez utiliser le sélecteur de ressources avec votre application [!DNL Adobe].

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Asset Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js"></script>
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

### ImsAuthProps {#ims-auth-props}

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

### ImsAuthService {#ims-auth-service}

`ImsAuthService` classe gère le flux d’authentification pour le sélecteur de ressources. Il est chargé d’obtenir un `imsToken` du service d’authentification Adobe IMS. Le `imsToken` permet d’authentifier l’utilisateur et d’autoriser l’accès au référentiel [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Assets. ImsAuthService utilise les propriétés `ImsAuthProps` pour contrôler le flux d’authentification et enregistrer des écouteurs pour divers événements d’authentification. Vous pouvez utiliser la fonction [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) pratique pour enregistrer l’instance _ImsAuthService_ avec le sélecteur de ressources. Les fonctions suivantes sont disponibles dans la classe `ImsAuthService`. Cependant, si vous utilisez la fonction _registerAssetsSelectorsAuthService_, vous n’avez pas besoin d’appeler directement ces fonctions.

| Nom de la fonction | Description |
|---|---|
| `isSignedInUser` | Détermine si l’utilisateur est actuellement connecté au service et renvoie une valeur booléenne en conséquence. |
| `getImsToken` | Récupère le `imsToken` d’authentification de l’utilisateur actuellement connecté, qui peut être utilisé pour authentifier des requêtes à d’autres services, tels que la génération du _rendu de ressource. |
| `signIn` | Lance le processus de connexion de l’utilisateur. Cette fonction utilise le `ImsAuthProps` pour afficher l’authentification dans un pop-up ou un rechargement complet de la page |
| `signOut` | Déconnecte l’utilisateur du service, invalide son jeton d’authentification et exige qu’il se reconnecte pour accéder aux ressources protégées. Appeler cette fonction recharge la page active. |
| `refreshToken` | Actualise le jeton d’authentification de l’utilisateur actuellement connecté, ce qui empêche son expiration et garantit un accès ininterrompu aux ressources protégées. Renvoie un nouveau jeton d’authentification pouvant être utilisé pour les requêtes suivantes. |

### Validation avec jeton IMS fourni {#validation-ims-token}

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

### Enregistrement des rappels vers le service IMS {#register-callback-ims-service}

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

>[!MORELIKETHIS]
>
>* [Intégration du sélecteur de ressources à diverses applications](/help/assets/integrate-asset-selector.md)
>* [Propriétés du sélecteur de ressources](/help/assets/asset-selector-properties.md)
>* [Intégration du sélecteur de ressources à Dynamic Media avec fonctionnalités OpenAPI](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
>* [Personnalisation du sélecteur de ressources](/help/assets/asset-selector-customization.md)
