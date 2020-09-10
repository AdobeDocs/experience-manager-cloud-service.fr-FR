---
title: Extension de ContextHub
description: Définissez de nouveaux types de modules et de magasins ContextHub lorsque ceux qui sont fournis ne répondent pas à vos besoins en termes de solution.
translation-type: tm+mt
source-git-commit: ddfdcf74977adf00bc0ab01b0b1a669781f0d730
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 70%

---


# Extension de ContextHub {#extending-contexthub}

Définissez de nouveaux types de modules et de magasins ContextHub lorsque ceux qui sont fournis ne répondent pas à vos besoins en termes de solution.

## Création de candidats de magasin personnalisés {#creating-custom-store-candidates}

Les magasins ContextHub sont créés à partir de candidats de magasin enregistrés. Pour créer un magasin personnalisé, vous devez créer et enregistrer un candidat de magasin.

<!--The javascript file that includes the code that creates and registers the store candidate must be included in a [client library folder](/help/sites-developing/clientlibs.md#creating-client-library-folders). The category of the folder must match the following pattern:-->

Le fichier JavaScript contenant le code qui crée et enregistre le candidat de magasin doit être inclus dans un dossier de bibliothèque cliente. La catégorie du dossier doit correspondre au schéma suivant :

```xml
contexthub.store.[storeType]
```

The `storeType` part of the category is the `storeType` with which the store candidate is registered. (voir [Enregistrement d’un candidat de magasin ContextHub](#registering-a-contexthub-store-candidate)). Par exemple, pour le storeType `contexthub.mystore`, la catégorie du dossier de bibliothèque cliente doit être `contexthub.store.contexthub.mystore`.

### Création d’un candidat de magasin ContextHub {#creating-a-contexthub-store-candidate}

To create a store candidate, you use the [`ContextHub.Utils.inheritance.inherit`](contexthub-api.md#inherit-child-parent) function to extend one of the base stores:

* [`ContextHub.Store.PersistedStore`](contexthub-api.md#contexthub-store-persistedstore)
* [`ContextHub.Store.SessionStore`](contexthub-api.md#contexthub-store-sessionstore)
* [`ContextHub.Store.JSONPStore`](contexthub-api.md#contexthub-store-jsonpstore)
* [`ContextHub.Store.PersistedJSONPStore`](contexthub-api.md#contexthub-store-persistedjsonpstore)

Note that each base store extends the [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) store.

L’exemple suivant crée l’extension la plus simple du candidat de magasin `ContextHub.Store.PersistedStore` :

```javascript
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

En réalité, vos candidats de magasin personnalisés définissent des fonctions supplémentaires ou remplacent la configuration initiale du magasin. Several [sample store candidates](sample-stores.md) are installed in the repository below `/libs/granite/contexthub/components/stores`.

### Enregistrement d’un candidat de magasin ContextHub {#registering-a-contexthub-store-candidate}

Enregistrez un candidat de magasin pour l’intégrer dans la structure ContextHub et permettre la création de magasins à partir de celui-ci. Pour enregistrer un candidat de magasin, utilisez la fonction [`registerStoreCandidate`](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) de la classe `ContextHub.Utils.storeCandidates`.

Lorsque vous enregistrez un candidat de magasin, vous indiquez un nom pour le type de magasin. Lorsque vous créez un magasin à partir du candidat, vous utilisez le type de magasin pour identifier le candidat sur lequel il repose.

Lorsque vous enregistrez un candidat de magasin, vous indiquez sa priorité. Lorsqu’un candidat de magasin est enregistré avec le même type qu’un candidat déjà enregistré, c’est le candidat ayant la priorité la plus élevée qui est utilisé. Par conséquent, vous pouvez remplacer les candidats de magasin existants par les nouvelles implémentations.

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

Dans la plupart des cas, un seul candidat est nécessaire et la priorité peut être définie sur `0`, mais si vous êtes intéressé, vous pouvez en apprendre davantage sur les inscriptions [plus avancées,](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) ce qui permet à l&#39;une des quelques implémentations de magasins d&#39;être choisie en fonction de la condition javascript (`applies`) et de la priorité candidate.

## Création de types de modules d’interface utilisateur ContextHub {#creating-contexthub-ui-module-types}

Vous pouvez créer des types de modules d’interface utilisateur personnalisés lorsque ceux qui sont [installés avec ContextHub](sample-modules.md) ne répondent pas à vos attentes. Pour créer un type de module d’interface utilisateur, créez un moteur de rendu de module en étendant la classe `ContextHub.UI.BaseModuleRenderer`, puis en l’enregistrant auprès de `ContextHub.UI`.

To create a UI module renderer, create a `Class` object that contains the logic that renders the UI module. Votre classe doit, au minimum, effectuer les actions suivantes :

* Extend the `ContextHub.UI.BaseModuleRenderer` class. Cette classe est l’implémentation de base de tous les moteurs de rendu de module d’IU. L’objet `Class` définit une propriété nommée `extend` que vous utilisez pour désigner cette classe comme celle en cours d’extension.
* Indiquez une configuration par défaut. Create a `defaultConfig` property. Cette propriété est un objet qui contient les propriétés définies pour le module d’IU [`contexthub.base`](sample-modules.md#contexthub-base-ui-module-type), ainsi que toute autre propriété dont vous avez besoin.

La source pour `ContextHub.UI.BaseModuleRenderer` est située à `/libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js`.  Pour enregistrer le moteur de rendu, utilisez la méthode [`registerRenderer`](contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) de la classe `ContextHub.UI`. Vous devez indiquer un nom pour le type de module. Lorsque les administrateurs créent un module d’IU basé sur ce moteur de rendu, ils spécifient ce nom.

Créez et enregistrez la classe du module de rendu dans une fonction anonyme à exécution automatique. The following example is based on the source code for the `contexthub.browserinfo` UI module. Ce module est une extension simple de la classe `ContextHub.UI.BaseModuleRenderer`.

```javascript
;(function() {

    var SurferinfoRenderer = new Class({
        extend: ContextHub.UI.BaseModuleRenderer,

        defaultConfig: {
            icon: 'coral-Icon--globe',
            title: 'Browser/OS Information',

            storeMapping: {
                surferinfo: 'surferinfo'
            },

            template:
                '<p>{{surferinfo.browser.family}} {{surferinfo.browser.version}}</p>' +
                '<p>{{surferinfo.os.name}} {{surferinfo.os.version}}</p>'
        }
    });

    ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());

}());
```

<!--The javascript file that includes the code that creates and registers the renderer must be included in a [client library folder](/help/sites-developing/clientlibs.md#creating-client-library-folders). The category of the folder must match the following pattern:-->

Le fichier javascript qui inclut le code qui crée et enregistre le rendu doit être inclus dans un dossier de bibliothèque client. La catégorie du dossier doit correspondre au schéma suivant :

```javascript
contexthub.module.[moduleType]
```

The `[moduleType]` part of the category is the `moduleType` with which the module renderer is registered. Par exemple, pour le `moduleType` `contexthub.browserinfo`, la catégorie du dossier de bibliothèque cliente doit être `contexthub.module.contexthub.browserinfo`.
