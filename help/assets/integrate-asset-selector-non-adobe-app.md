---
title: Intégration du sélecteur de ressources à une application non Adobe ou tierce
description: Intégrer le sélecteur de ressources à diverses applications Adobe, non Adobe et tierces.
role: Admin, User
exl-id: 55848de0-aff2-42a0-b959-c771235d9425
source-git-commit: 19a7d8089a3c33f2d066bcbb4b7a99e77777eb91
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 18%

---

# Intégration à une application non Adobe {#integrate-asset-selector-non-adobe-app}

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

Le sélecteur de ressources vous permet de l’intégrer à l’aide de diverses applications non Adobe ou tierces pour leur permettre de travailler ensemble en toute transparence.

## Prérequis {#prereqs-non-adobe-app}

Utilisez les conditions préalables suivantes si vous intégrez le sélecteur de ressources à une application non Adobe :

* [Méthodes de communication](/help/assets/overview-asset-selector.md#prereqs)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Le sélecteur de ressources prend en charge l’authentification au référentiel [!DNL Experience Manager Assets] à l’aide des propriétés IMS (Identity Management System) telles que `imsScope` ou `imsClientID` lorsque vous l’intégrez à une application non Adobe.

## Configuration du sélecteur de ressources pour une application non Adobe {#configure-non-adobe-app}

Pour configurer le sélecteur de ressources pour une application non Adobe, vous devez d’abord enregistrer un ticket d’assistance pour la mise en service, puis suivre les étapes d’intégration.

### Enregistrer un ticket d’assistance {#log-a-support-ticket}

Étapes pour consigner un ticket d’assistance via Admin Console :

1. Ajoutez **Sélecteur de ressources avec AEM Assets** dans le titre du ticket.

1. Dans la description, veuillez fournir les détails suivants :

   * [!DNL Experience Manager Assets] comme URL [!DNL Cloud Service] (ID de programme et ID d’environnement).
   * Noms de domaine dans lesquels l’application web autre qu’Adobe est hébergée.

## Étapes d’intégration {#non-adobe-app-integration-steps}

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
            PureJSSelectors.renderAssetSelectorWithAuthFlow(container, assetSelectorProps, () =>
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
>Si vous avez intégré le sélecteur de ressources à l’aide du workflow de connexion à l’inscription mais que vous ne pouvez toujours pas accéder au référentiel de diffusion, assurez-vous que les cookies de navigateur sont nettoyés. Sinon, vous obtenez `invalid_credentials All session cookies are empty` erreur dans la console.

>[!MORELIKETHIS]
>
>* [Intégration du sélecteur de ressources à diverses applications](/help/assets/integrate-asset-selector.md)
>* [Propriétés du sélecteur de ressources](/help/assets/asset-selector-properties.md)
>* [Intégration du sélecteur de ressources à Dynamic Media avec fonctionnalités OpenAPI](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
>* [Personnalisation du sélecteur de ressources](/help/assets/asset-selector-customization.md)
