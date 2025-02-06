---
title: Extension de ContextHub
description: Définissez de nouveaux types de modules et de magasins ContextHub lorsque ceux qui sont fournis ne répondent pas à vos besoins.
exl-id: ba817c18-f8bd-485d-b043-87593a6a93b5
feature: Developing, Personalization
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 85%

---

# Extension de ContextHub {#extending-contexthub}

Définissez de nouveaux types de modules et de magasins ContextHub lorsque ceux qui sont fournis ne répondent pas à vos besoins en termes de solution.

## Création de candidats de magasin personnalisés {#creating-custom-store-candidates}

Les magasins ContextHub sont créés à partir de candidats de magasins enregistrés. Pour créer un magasin personnalisé, vous devez créer et enregistrer un candidat de magasin.

Le fichier JavaScript contenant le code qui crée et enregistre le magasin candidat doit être inclus dans un [dossier de bibliothèque cliente](/help/implementing/developing/introduction/clientlibs.md). La catégorie du dossier doit correspondre au schéma suivant :

```xml
contexthub.store.[storeType]
```

La partie `storeType` de la catégorie correspond au `storeType` auprès duquel le candidat de magasin est enregistré. (voir [Enregistrement d’un candidat de magasin ContextHub](#registering-a-contexthub-store-candidate)). Par exemple, pour le storeType `contexthub.mystore`, la catégorie du dossier de bibliothèque cliente doit être `contexthub.store.contexthub.mystore`.

### Création d’un candidat de magasin ContextHub {#creating-a-contexthub-store-candidate}

Pour créer un candidat de magasin, vous utilisez la fonction [`ContextHub.Utils.inheritance.inherit`](contexthub-api.md#inherit-child-parent) afin d’étendre l’un des magasins de base :

* [`ContextHub.Store.PersistedStore`](contexthub-api.md#contexthub-store-persistedstore)
* [`ContextHub.Store.SessionStore`](contexthub-api.md#contexthub-store-sessionstore)
* [`ContextHub.Store.JSONPStore`](contexthub-api.md#contexthub-store-jsonpstore)
* [`ContextHub.Store.PersistedJSONPStore`](contexthub-api.md#contexthub-store-persistedjsonpstore)

Chaque magasin de base étend le magasin [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core).

L’exemple suivant crée l’extension la plus simple du candidat de magasin `ContextHub.Store.PersistedStore` :

```javascript
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

En réalité, vos candidats de magasin personnalisés définissent des fonctions supplémentaires ou remplacent la configuration initiale du magasin. Plusieurs [exemples de candidats de magasin](sample-stores.md) sont installés dans le référentiel sous `/libs/granite/contexthub/components/stores`.

### Enregistrement d’un candidat de magasin ContextHub {#registering-a-contexthub-store-candidate}

Enregistrez un candidat de magasin pour l’intégrer dans la structure ContextHub et permettre la création de magasins à partir de celui-ci. Pour enregistrer un candidat de magasin, utilisez la fonction [`registerStoreCandidate`](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) de la classe `ContextHub.Utils.storeCandidates`.

Lorsque vous enregistrez un candidat de magasin, vous attribuez un nom au type de magasin. Lorsque vous créez un magasin à partir du candidat, vous utilisez le type de magasin pour identifier le candidat sur lequel il repose.

Lorsque vous enregistrez un candidat de magasin, vous indiquez sa priorité. Lorsqu’un candidat de magasin est enregistré avec le même type qu’un candidat déjà enregistré, c’est le candidat ayant la priorité la plus élevée qui est utilisé. Par conséquent, vous pouvez remplacer les candidats de magasin existants par les nouvelles implémentations.

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

Dans la plupart des cas, un seul candidat est nécessaire et la priorité peut être définie sur `0`, mais si vous êtes intéressé, vous pouvez en savoir plus sur les [enregistrements plus avancés](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies), ce qui permet de choisir l’une des rares implémentations de magasin en fonction de la condition JavaScript (`applies`) et de la priorité du candidat.

## Création de types de modules d’interface utilisateur ContextHub {#creating-contexthub-ui-module-types}

Vous pouvez créer des types de modules d’interface utilisateur personnalisés lorsque ceux qui sont [installés avec ContextHub](sample-modules.md) ne répondent pas à vos attentes. Pour créer un type de module d’interface utilisateur, créez un moteur de rendu de module d’interface utilisateur en étendant la classe `ContextHub.UI.BaseModuleRenderer`, puis en l’enregistrant auprès de `ContextHub.UI`.

Pour créer un moteur de rendu de module d’interface utilisateur, créez un objet `Class` contenant le logiciel qui effectue le rendu de ce module. Votre classe doit, au minimum, effectuer les actions suivantes :

* Étendez la classe `ContextHub.UI.BaseModuleRenderer`. Cette classe est l’implémentation de base de tous les moteurs de rendu de module d’IU. L’objet `Class` définit une propriété nommée `extend` que vous utilisez pour désigner cette classe comme celle en cours d’extension.
* Indiquez une configuration par défaut. Créez une propriété `defaultConfig`. Cette propriété est un objet qui contient les propriétés définies pour le module d’IU [`contexthub.base`](sample-modules.md#contexthub-base-ui-module-type), ainsi que toute autre propriété dont vous avez besoin.

La source pour `ContextHub.UI.BaseModuleRenderer` est située à l’emplacement `/libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js`. Pour enregistrer le moteur de rendu, utilisez la méthode [`registerRenderer`](contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) de la classe `ContextHub.UI`. Vous devez attribuer un nom au type de module. Lorsque les administrateurs et administratrices créent un module d’interface utilisateur basé sur ce moteur de rendu, ils spécifient ce nom.

Créez et enregistrez la classe du moteur de rendu dans une fonction anonyme auto-exécutée. L’exemple suivant repose sur le code source du module d’IU `contexthub.browserinfo`. Ce module est une extension simple de la classe `ContextHub.UI.BaseModuleRenderer`.

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

Le fichier JavaScript contenant le code qui crée et enregistre le module de rendu doit être inclus dans un [dossier de bibliothèque cliente](/help/implementing/developing/introduction/clientlibs.md). La catégorie du dossier doit correspondre au schéma suivant :

```javascript
contexthub.module.[moduleType]
```

La partie `[moduleType]` de la catégorie correspond au `moduleType` auprès duquel le moteur de rendu du module est enregistré. Par exemple, pour le `moduleType` de `contexthub.browserinfo`, la catégorie du dossier de bibliothèque cliente doit être `contexthub.module.contexthub.browserinfo`.
