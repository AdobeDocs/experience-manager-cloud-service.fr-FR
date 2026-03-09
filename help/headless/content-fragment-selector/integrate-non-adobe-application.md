---
title: Intégrer le sélecteur de fragments de contenu à une application non Adobe ou tierce
description: Intégrez le sélecteur de fragment de contenu à diverses applications Adobe, non Adobe et tierces.
role: Admin, User, Developer
source-git-commit: 3af1a89489af96bf9c9908aea7fb20883956517b
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 5%

---

# Intégration à une application non Adobe {#integration-with-non-adobe-application}

Le sélecteur de fragment de contenu vous permet de l’intégrer à diverses applications non Adobe ou tierces pour leur permettre de travailler ensemble en toute transparence.

## Prérequis {#prerequisites}

Utilisez les conditions préalables suivantes si vous intégrez le sélecteur de fragments de contenu à une application non Adobe :

* [Prérequis](/help/headless/content-fragment-selector/overview.md#prerequisites)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Lorsque vous l’intégrez à une application non Adobe, le sélecteur de fragments de contenu prend en charge l’authentification auprès du référentiel Adobe Experience Manager (AEM) as a Cloud Service à l’aide des propriétés du système Identity Management (IMS) telles que `imsScope` ou `imsClientID`.

## Configuration du sélecteur de fragments de contenu pour une application non Adobe {#configure-content-fragment-selector-for-a-non-adobe-application}

Pour configurer le sélecteur de fragments de contenu pour une application non Adobe, vous devez d’abord enregistrer un ticket de support pour la mise en service avant de poursuivre les étapes d’intégration.

### Enregistrer un ticket d’assistance {#logging-a-support-ticket}

Étapes pour consigner un ticket d’assistance via Admin Console :

1. Ajoutez **Sélecteur de fragment de contenu avec des fragments AEM** dans le titre du ticket.

1. Dans la description, veuillez fournir les détails suivants :

   * URL Experience Manager as a Cloud Service (ID de programme et ID d’environnement).
   * Noms de domaine dans lesquels l’application web autre qu’Adobe est hébergée.

## Étapes d’intégration {#integration-steps}

Utilisez l’exemple de fichier `index.html` suivant pour l’authentification lors de l’intégration du sélecteur de fragments de contenu à une application non Adobe :

* Accédez au package Sélecteur de fragment de contenu à l’aide de la balise `Script` .

* Définissez les propriétés du flux IMS, telles que `imsClientId`, `imsScope` et `redirectURL`.

   * La fonction requiert que vous définissiez au moins l’une des propriétés `imsClientId` et `imsScope`.
   * Si vous ne définissez pas de valeur pour `redirectURL`, l’URL de redirection enregistrée pour l’ID client est utilisée.

* Comme l’exemple ne comporte pas de `imsToken` générée, utilisez les fonctions `registerFragmentsSelectorsAuthService` et `renderFragmentSelectorWithAuthFlow` .

   * Utilisez la fonction `registerFragmentsSelectorsAuthService` avant de `renderFragmentSelectorWithAuthFlow` pour enregistrer le `imsToken` avec le sélecteur de fragment de contenu.
   * Adobe recommande d’appeler `registerFragmentsSelectorsAuthService` lorsque vous instanciez le composant .

* Définissez l’authentification et les autres propriétés liées à l’accès de Fragments as a Cloud Service dans la section `const props` .
* La variable globale `PureJSContentFragmentSelectors` est utilisée pour effectuer le rendu du sélecteur de fragment de contenu dans le navigateur web.
* Le sélecteur de fragment de contenu est rendu sur l’élément de conteneur `<div>`. Cet exemple utilise une boîte de dialogue pour afficher le sélecteur de fragment de contenu.

**Exemple de`ìndex.html`**

```html {line-numbers="true"}
<!doctype html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <link rel="icon" type="image/svg+xml" href="/vite.svg" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>testing-cf-mfe-integration-with-3rd-party-app</title>
        <script
            id="content-fragments-selector"
            src="https://experience.adobe.com/solutions/CQ-sites-content-fragment-selector/static-assets/resources/content-fragment-selector.js"
        ></script>
        <script>
            const imsProps = {
                imsClientId: '<IMS_CLIENT_ID>',
                imsScope:
                    'additional_info.projectedProductContext, AdobeID, openid, read_organizations',
                redirectUrl: window.location.href,
                onImsServiceInitialized: (service) => {
                    // invoked when the ims service is initialized and is ready
                    console.log('onImsServiceInitialized', service);
                },
                onAccessTokenReceived: (token) => {
                    console.log('onAccessTokenReceived', token);
                },
                onAccessTokenExpired: () => {
                    console.log('onAccessTokenError');
                    // re-trigger sign-in flow
                },
                onErrorReceived: (type, msg) => {
                    console.log('onErrorReceived', type, msg);
                },
            };

            function load() {
                const registeredTokenService =
                    PureJSContentFragmentSelectors.registerContentFragmentSelectorAuthService(
                        imsProps
                    );
                imsInstance = registeredTokenService;
            }

            // initialize the IMS flow before attempting to render the content fragment selector
            load();

            // function that will render the content fragment selector
            function renderContentFragmentSelectorWithAuthFlow() {
                const contentFragmentSelectorDialog = document.getElementById(
                    'content-fragment-selector-dialog'
                );

                const contentFragmentSelectorProps = {
                    inventoryViewToggleEnabled: true,
                    isOpen: true,
                    noWrap: false,
                    orgId: 'YOUR_ORG_ID@AdobeOrg',
                    // repoId: "author-p12345-e67890.adobeaemcloud.com", // if wanted to restrict to a specific repo
                    runningInUnifiedShell: false,
                    onDismiss: () => contentFragmentSelectorDialog.close(),
                    onSubmit: ({ contentFragments }) => {
                        const selectedContentFragment = contentFragments[0];
                        alert(selectedContentFragment.path);
                    },
                };
                // container element on which you want to render the ContentFragmentSelector component
                const container = document.getElementById('content-fragment-selector');

                /// Use the PureJSContentFragmentSelectors in globals to render the ContentFragmentSelector component
                PureJSContentFragmentSelectors.renderContentFragmentSelectorWithAuthFlow(
                    container,
                    contentFragmentSelectorProps,
                    () => contentFragmentSelectorDialog.showModal()
                );
            }
        </script>
    </head>
    <body>
        <div>
            <button onclick="renderContentFragmentSelectorWithAuthFlow()">
                Content Fragment Selector - Select Content Fragments with Ims Flow
            </button>
        </div>
        <dialog id="content-fragment-selector-dialog">
            <div
                id="content-fragment-selector"
                style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px"
            ></div>
        </dialog>
    </body>
</html>
```

## Impossible d’accéder au référentiel de diffusion {#unable-to-access-delivery-repository}

Si vous avez intégré le sélecteur de fragments de contenu à l’aide du workflow de connexion à l’inscription mais que vous ne parvenez toujours pas à accéder au référentiel de diffusion, assurez-vous que les cookies du navigateur ont été nettoyés.

Sinon, l’erreur `invalid_credentials All session cookies are empty` risque de s’afficher dans la console.
