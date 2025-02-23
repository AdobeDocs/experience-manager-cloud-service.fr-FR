---
title: Sélecteur de ressources pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Intégrez le sélecteur de ressources à diverses applications Adobe, non Adobe et tierces.
role: Admin, User
exl-id: 55848de0-aff2-42a0-b959-c771235d9425
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 6%

---

# Intégration à une application non-Adobe {#integrate-asset-selector-non-adobe-app}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Le sélecteur de ressources vous permet d’intégrer à l’aide de diverses applications tierces ou non Adobes afin de leur permettre de travailler ensemble de manière transparente.

## Conditions préalables {#prereqs-non-adobe-app}

Utilisez les conditions préalables suivantes si vous intégrez le sélecteur de ressources à une application non Adobe :

* [Méthodes de communication](/help/assets/overview-asset-selector.md#prereqs)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Le sélecteur de ressources prend en charge l’authentification au référentiel [!DNL Experience Manager Assets] à l’aide des propriétés Identity Management System (IMS) telles que `imsScope` ou `imsClientID` lorsque vous l’intégrez à une application non Adobe.

## Configuration du sélecteur de ressources pour une application non Adobe {#configure-non-adobe-app}

Pour configurer le sélecteur de ressources pour une application non Adobe, vous devez d’abord consigner un ticket d’assistance pour l’approvisionnement, suivi des étapes d’intégration.

### Journalisation d’un ticket d’assistance {#log-a-support-ticket}

Étapes pour consigner un ticket d’assistance via Admin Console :

1. Ajoutez **Sélecteur de ressources avec AEM Assets** dans le titre du ticket.

1. Dans la description, veuillez fournir les détails suivants :

   * [!DNL Experience Manager Assets] comme URL [!DNL Cloud Service] (ID de programme et ID d’environnement).
   * Noms de domaine dans lesquels l’application web non Adobe est hébergée.

## Étapes d’intégration {#non-adobe-app-integration-steps}

Utilisez cet exemple de fichier `index.html` pour l’authentification lors de l’intégration du sélecteur de ressources avec une application non Adobe.

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
        src="https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js"></script>
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

## Impossible d’accéder au référentiel de diffusion {#unable-to-access-delivery-repository}

>[!TIP]
>
>Si vous avez intégré le sélecteur de ressources à l’aide du workflow S’inscrire mais que vous ne parvenez toujours pas à accéder au référentiel de diffusion, assurez-vous que les cookies de navigateur sont nettoyés. Sinon, vous obtenez une erreur `invalid_credentials All session cookies are empty` dans la console.

>[!MORELIKETHIS]
>
>* [Intégrer le sélecteur de ressources à diverses applications](/help/assets/integrate-asset-selector.md)
>* [Propriétés du sélecteur de ressources](/help/assets/asset-selector-properties.md)
>* [Intégrer le sélecteur de ressources à Dynamic Media avec les fonctionnalités OpenAPI](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
>* [Personnalisations du sélecteur de ressources](/help/assets/asset-selector-customization.md)
