---
title: Intégration du sélecteur de fragment de contenu à une application Adobe
description: Intégrer le sélecteur de fragments de contenu à diverses applications Adobe.
role: Admin, User, Developer
source-git-commit: a16d9e9fa6483a89283c595372abcc437d1d962e
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 1%

---

# Intégration du sélecteur de fragment de contenu à l’application Adobe {#integrate-content-fragment-selector-with-adobe-application}

Le sélecteur de fragment de contenu vous permet de l’intégrer à diverses applications Adobe pour leur permettre de travailler ensemble en toute transparence.

## Prérequis {#prerequisites}

Utilisez les conditions préalables suivantes si vous intégrez le sélecteur de fragments de contenu à une application Adobe :

* [Prérequis](/help/headless/content-fragment-selector/overview.md#prerequisites)
* imsOrg
* imsToken
* apikey

## Intégration du sélecteur de fragment de contenu à une application Adobe {#integrate-content-fragment-selector-with-an-adobe-application}

L’exemple suivant illustre l’utilisation du sélecteur de fragment de contenu lors de l’exécution d’une application Adobe sous Unified Shell ou lorsque vous avez déjà généré un `imsToken` pour l’authentification.

Incluez le package Sélecteur de fragment de contenu dans votre code à l’aide de la balise `script`, comme illustré dans l’exemple ci-dessous.

* Une fois le script chargé, vous pouvez utiliser la variable globale `PureJSContentFragmentSelectors` .
* Définissez le sélecteur de fragment de contenu [propriétés](/help/headless/content-fragment-selector/properties.md) :

   * les propriétés `imsOrg` et `imsToken` sont toutes deux requises pour l’authentification dans l’application Adobe
   * la propriété `handleSelection` est utilisée pour gérer les fragments sélectionnés.

* Pour effectuer le rendu du sélecteur de fragment de contenu, appelez la fonction `renderFragmentSelector` .
* Le sélecteur de fragment de contenu s’affiche dans l’élément de conteneur `<div>` .

En suivant ces étapes, vous pouvez utiliser le sélecteur de fragments de contenu avec votre application Adobe.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Fragment Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-fragmentss-selectors/static-fragments/resources/fragments-selectors.js"></script>
    <script>
        // get the container element in which we want to render the FragmentSelector component
        const container = document.getElementById('fragment-selector-container');
        // imsOrg and imsToken are required for authentication in Adobe application
        const fragmentSelectorProps = {
            imsOrg: 'example-ims@AdobeOrg',
            imsToken: "example-imsToken",
            apiKey: "example-apiKey-associated-with-imsOrg",
            handleSelection: (fragmentss: SelectedFragmentType[]) => {},
        };
        // Call the `renderFragmentSelector` available in PureJSContentFragmentSelectors globals to render FragmenttSelector
        PureJSContentFragmentSelectors.renderFragmentSelector(container, fragmentSelectorProps);
    </script>
</head>

<body>
    <div id="fragment-selector-container" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
    </div>
</body>

</html>
```

### ImsAuthProps {#imsauthprops}

Les propriétés `ImsAuthProps` définissent les informations d’authentification et le flux que le sélecteur de fragment de contenu utilise pour obtenir une `imsToken`. En définissant ces propriétés, vous pouvez contrôler le comportement du flux d’authentification et enregistrer des écouteurs pour divers événements d’authentification.

Pour plus d’informations sur les propriétés, voir [Propriétés ImsAuthProps](/help/headless/content-fragment-selector/properties.md#imsauthprops-properties)

### ImsAuthService {#imsauthservice}

`ImsAuthService` classe gère le flux d’authentification pour le sélecteur de fragments. Il est chargé d’obtenir un `imsToken` du service d’authentification Adobe IMS. Le `imsToken` permet d’authentifier l’utilisateur et d’autoriser l’accès au référentiel AEM as a Cloud Service. `ImsAuthService` utilise les propriétés `ImsAuthProps` pour contrôler le flux d’authentification et enregistrer des écouteurs pour divers événements d’authentification. Vous pouvez utiliser la fonction `registerFragmentsSelectorsAuthService` pour enregistrer l’instance `ImsAuthService` avec le sélecteur de fragments. Les fonctions suivantes sont disponibles dans la classe `ImsAuthService`. Cependant, si vous utilisez la fonction `registerFragmentsSelectorsAuthService`, vous n’avez pas besoin d’appeler directement ces fonctions.

Pour plus d’informations sur les propriétés, voir [ Propriétés ImsAuthService ](/help/headless/content-fragment-selector/properties.md#imsauthservice-properties)

### Validation avec jeton IMS fourni {#validation-with-provided-ims-token}

```javascript
<script>
    const apiToken="<valid IMS token>";
    function handleSelection(selection) {
    console.log("Selected fragment: ", selection);
    };
    function renderFragmentSelectorInline() {
    console.log("initializing Fragment Selector");
    const props = {
    "repositoryId": "delivery-p64502-e544757.adobeaemcloud.com",
    "apiKey": "ngdm_test_client",
    "imsOrg": "<IMS org>",
    "imsToken": apiToken,
    handleSelection,
    hideTreeNav: true
    }
    const container = document.getElementById('fragment-selector-container');
    PureJSContentFragmentSelectors.renderFragmentSelector(container, props);
    }
    $(document).ready(function() {
    renderFragmentSelectorInline();
    });
</script>
```

### Enregistrement des rappels vers le service IMS {#register-callbacks-to-ims-service}

```java
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
