---
title: Sélecteur de ressources pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Intégrez le sélecteur de ressources à diverses applications Adobe, non Adobe et tierces.
role: Admin, User
exl-id: a0c030e2-2213-406b-ad92-4761f1e2ee9f
source-git-commit: f9f5b2a25933e059cceacf2ba69e23d528858d4b
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 12%

---

# Intégration du sélecteur de ressources à l’application Adobe {#integrate-asset-selector-with-adobe-app}

Le sélecteur de ressources vous permet d’intégrer à l’aide de diverses applications Adobe afin de leur permettre de travailler ensemble de manière transparente.

## Conditions préalables{#prereqs-adobe-app}

Utilisez les conditions préalables suivantes si vous intégrez le sélecteur de ressources à une application [!DNL Adobe] :

* [Méthodes de communication](/help/assets/overview-asset-selector.md#prereqs)
* imsOrg
* imsToken
* apikey

## Intégrer le sélecteur de ressources à une application [!DNL Adobe] {#adobe-app-integration-vanilla}

L’exemple suivant illustre l’utilisation du sélecteur de ressources lors de l’exécution d’une application [!DNL Adobe] sous Shell unifié ou lorsque `imsToken` est déjà généré pour l’authentification.

Insérez le package Sélecteur de ressources dans votre code à l’aide de la balise `script`, comme illustré dans les _lignes 6 à 15_ de l’exemple ci-dessous. Une fois le script chargé, vous pouvez utiliser la variable globale `PureJSSelectors`. Définissez les [propriétés](/help/assets/asset-selector-properties.md) du sélecteur de ressources comme illustré dans les _lignes 16 à 23_. Les propriétés `imsOrg` et `imsToken` sont toutes deux requises pour l’authentification dans l’application Adobe. La propriété `handleSelection` sert à gérer les ressources sélectionnées. Pour effectuer le rendu du sélecteur de ressources, appelez la fonction `renderAssetSelector` comme indiqué dans la _ligne 17_. Le sélecteur de ressources s’affiche dans l’élément de conteneur `<div>`, comme indiqué dans les _lignes 21 et 22_.

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

### ImsAuthProps {#ims-auth-props}

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

### ImsAuthService {#ims-auth-service}

La classe `ImsAuthService` gère le flux d’authentification pour le sélecteur de ressources. Il est responsable de l&#39;obtention d&#39;un `imsToken` auprès du service d&#39;authentification Adobe IMS. `imsToken` est utilisé pour authentifier l’utilisateur et autoriser l’accès à [!DNL Adobe Experience Manager] en tant que référentiel Assets [!DNL Cloud Service]. ImsAuthService utilise les propriétés `ImsAuthProps` pour contrôler le flux d’authentification et enregistrer les écouteurs pour divers événements d’authentification. Vous pouvez utiliser la fonction [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) pratique pour enregistrer l’instance _ImsAuthService_ avec le sélecteur de ressources. Les fonctions suivantes sont disponibles sur la classe `ImsAuthService`. Cependant, si vous utilisez la fonction _registerAssetsSelectorsAuthService_, vous n’avez pas besoin d’appeler directement ces fonctions.

| Nom de la fonction | Description |
|---|---|
| `isSignedInUser` | Détermine si l’utilisateur est actuellement connecté au service et renvoie une valeur booléenne en conséquence. |
| `getImsToken` | Récupère l’authentification `imsToken` pour l’utilisateur actuellement connecté, qui peut être utilisée pour authentifier les requêtes sur d’autres services, comme la génération de la ressource _rendition. |
| `signIn` | Lance le processus de connexion de l’utilisateur. Cette fonction utilise le `ImsAuthProps` pour afficher l’authentification dans une fenêtre contextuelle ou un rechargement de page complet. |
| `signOut` | Déclenche l’utilisateur du service, invalide son jeton d’authentification et l’oblige à se reconnecter pour accéder aux ressources protégées. L’appel de cette fonction recharge la page active. |
| `refreshToken` | Actualise le jeton d’authentification de l’utilisateur actuellement connecté, l’empêchant d’expirer et assurant un accès ininterrompu aux ressources protégées. Renvoie un nouveau jeton d’authentification qui peut être utilisé pour les requêtes suivantes. |

### Validation avec le jeton IMS fourni {#validation-ims-token}

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

### Enregistrement des rappels au service IMS {#register-callback-ims-service}

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
>* [Intégrer le sélecteur de ressources à diverses applications](/help/assets/integrate-asset-selector.md)
>* [Propriétés du sélecteur de ressources](/help/assets/asset-selector-properties.md)
>* [ API d’ouverture de média dynamique du sélecteur de ressources ](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
>* [Personnalisation du sélecteur de ressources](/help/assets/asset-selector-customization.md)
