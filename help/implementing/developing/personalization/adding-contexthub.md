---
title: Ajout de ContextHub à des pages et accès à des magasins
description: Ajoutez ContextHub à vos pages pour activer les fonctionnalités ContextHub et créer un lien vers les bibliothèques JavaScript ContextHub.
translation-type: tm+mt
source-git-commit: 3277d7470c1abdcc1f759c87e2c1a7ffb3390f47
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 67%

---


# Ajout de ContextHub à des pages et accès à des magasins  {#adding-contexthub-to-pages-and-accessing-stores}

Ajoutez ContextHub sur vos pages pour activer les fonctionnalités ContextHub et pour créer un lien vers les bibliothèques Javascript ContextHub.

L’API JavaScript ContextHub permet d’accéder aux données contextuelles gérées par ContextHub. Cette page décrit brièvement les principales fonctionnalités de l’API pour l’accès et la manipulation des données contextuelles. Suivez les liens vers la documentation de référence de l’API pour consulter des informations détaillées et des exemples de code.

## Ajout de ContextHub à un composant de page {#adding-contexthub-to-a-page-component}

Pour activer les fonctionnalités ContextHub et créer un lien vers les bibliothèques Javascript ContextHub, incluez le composant `contexthub` dans la section `head` de votre page. Le code HTML de votre composant de page doit ressembler à l’exemple suivant :

```xml
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

Notez que vous devez également déterminer si la barre d’outils ContextHub apparaît ou non dans le mode Aperçu. Voir [Affichage et masquage de l’IU ContextHub](configuring-contexthub.md#showing-and-hiding-the-contexthub-ui).

## À propos des magasins ContextHub  {#about-contexthub-stores}

Utilisez des magasins ContextHub pour conserver des données contextuelles. ContextHub fournit les types de magasins suivants, qui constituent la base de tous les types :

* [PersistedStore](contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](contexthub-api.md#contexthub-store-persistedstore)

Tous les types de magasins sont des extensions de la classe [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core). Pour plus d’informations sur la création d’un type de magasin, voir [Création de magasins personnalisés](extending-contexthub.md#creating-custom-store-candidates). Pour plus d’informations sur les exemples de types de magasins, voir [Exemples de candidats au titre de magasins ContextHub](sample-stores.md).

### Modes de persistance  {#persistence-modes}

Les magasins ContextHub utilisent l’un des modes de persistance suivants :

* **Local** : utilise HTML5 localStorage pour conserver les données. L’espace de stockage local est conservé sur le navigateur entre les sessions.
* **Session :** utilise sessionStorage HTML5 pour conserver les données. Le stockage de session est conservé pendant toute la durée de la session du navigateur et est disponible dans toutes les fenêtres du navigateur.
* **Cookie** : utilise la prise en charge native des cookies du navigateur pour le stockage des données. Les données de cookie sont échangées avec le serveur dans des requêtes HTTP.
* **Window.name** : utilise la propriété window.name pour conserver les données.
* **Mémoire** : utilise un objet JavaScript pour conserver les données.

Par défaut, ContextHub utilise le mode de persistance Local. Si le navigateur ne prend pas en charge ni n’autorise HTML5 localStorage, la persistance de session est utilisée. Si le navigateur ne prend pas en charge ni n’autorise HTML5 sessionStorage, la persistance Window.name est utilisée.

### Données du magasin {#store-data}

En interne, les données de magasin forment une structure arborescente, ce qui permet d’ajouter des valeurs en tant qu’objets complexes ou que types principaux. Lorsque vous ajoutez des objets complexes à des magasins, leurs propriétés forment des branches dans l’arborescence de données. Par exemple, l’objet complexe suivant est ajouté à une boutique vide nommée emplacement :

```javascript
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

La structure arborescente du magasin peut être conceptualisée comme suit :

```text
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

La structure arborescente définit les éléments de données du magasin sous la forme de paires clé/valeur. Dans l&#39;exemple ci-dessus, la clé `/number` correspond à la valeur `321` et la clé `/data/country` à la valeur `Switzerland`.

### Manipulation d’objets {#manipulating-objects}

ContextHub fournit la classe [`ContextHub.Utils.JSON.tree`](contexthub-api.md#contexthub-utils-json-tree) pour manipuler les objets Javascript. Utilisez les fonctions de cette classe pour manipuler des objets JavaScript avant de les ajouter à un magasin ou après les avoir récupérés d’un magasin.

De plus, la classe [`ContextHub.Utils.JSON`](contexthub-api.md#contexthub-utils-json) fournit des fonctions permettant de sérialiser des objets sur des tableaux et de désérialiser des chaînes sur des objets. Utilisez cette classe pour gérer les données JSON afin de prendre en charge les navigateurs qui n’incluent pas de façon native les fonctions `JSON.parse` et `JSON.stringify`.

## Interaction avec les magasins ContextHub {#interacting-with-contexthub-stores}

Utilisez l’objet JavaScript [`ContextHub`](contexthub-api.md#ui-event-constants) pour obtenir un magasin comme objet JavaScript. Une fois que vous avez obtenu l’objet de magasin, vous pouvez manipuler les données qu’il contient. Utilisez la fonction [`getAllStores`](contexthub-api.md#getallstores) ou [`getStore`](contexthub-api.md#getstore-name) pour obtenir le magasin.

### Accès aux données du magasin {#accessing-store-data}

La classe Javascript [`ContexHub.Store.Core`](contexthub-api.md#contexthub-store-core) définit plusieurs fonctions pour interagir avec les données de stockage. Les fonctions suivantes stockent et récupèrent plusieurs éléments de données contenus dans des objets :

* [addAllItems](contexthub-api.md#addallitems-tree-options)
* [getTree](contexthub-api.md#gettree-includeinternals)

Les différents éléments de données sont stockés sous la forme d’un ensemble de paires clé/valeur. Pour stocker et récupérer des valeurs, spécifiez la clé correspondante :

* [getItem](contexthub-api.md#getitem-key)
* [setItem](contexthub-api.md#setitem-key-value-options)

Notez que les magasins candidats personnalisés peuvent définir des fonctions supplémentaires qui permettent d’accéder aux données du magasin.

>[!NOTE]
>
>Par défaut, ContextHub ne connaît pas les utilisateurs actuellement connectés sur les serveurs de publication. Il considère ces utilisateurs comme étant anonymes.
>
>Vous pouvez sensibiliser ContextHub aux utilisateurs connectés en chargeant le magasin de profils. Reportez-vous à l&#39;[exemple de code sur GitHub ici](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### Génération d’événements ContextHub {#contexthub-eventing}

ContextHub comprend une structure d’événements qui vous permet de répondre automatiquement aux événements du magasin. Chaque objet du magasin contient un objet [`ContextHub.Utils.Eventing`](contexthub-api.md#contexthub-utils-eventing) disponible sous la forme d’une propriété [`eventing`](contexthub-api.md#eventing) du magasin. Utilisez la fonction [`on`](contexthub-api.md#on-name-handler-selector-triggerforpastevents) ou [`once`](contexthub-api.md#once-name-handler-selector-triggerforpastevents) pour lier une fonction JavaScript à un événement de magasin.

## Utilisation de ContextHub pour manipuler des cookies {#using-context-hub-to-manipulate-cookies}

L’API JavaScript ContextHub offre une prise en charge de plusieurs navigateurs pour la gestion des cookies de navigateur. L&#39;espace de nommage [`ContextHub.Utils.Cookie`](contexthub-api.md#contexthub-utils-cookie) définit plusieurs fonctions permettant de créer, manipuler et supprimer des cookies.

## Identification de segments ContextHub résolus {#determining-resolved-contexthub-segments}

Le moteur de segments ContextHub vous permet de déterminer quels segments enregistrés sont résolus dans le contexte actuel. Utilisez la fonction getResolvedSegments de la classe [`ContextHub.SegmentEngine.SegmentManager`](contexthub-api.md#contexthub-segmentengine-segmentmanager) pour récupérer les segments résolus. Ensuite, utilisez la fonction `getName` ou `getPath` de la classe [`ContextHub.SegmentEngine.Segment`](contexthub-api.md#contexthub-segmentengine-segment) pour tester un segment.

### Segments ContextHub {#contexthub-segments}

Les segments ContextHub sont installés sous le noeud `/conf/<site>/settings/wcm/segments`.

Les segments suivants sont installés avec le [site de didacticiel WKND.](/help/implementing/developing/introduction/develop-wknd-tutorial.md)

* summer
* winter

Les règles utilisées pour résoudre ces segments sont résumées comme suit :

* Tout d&#39;abord, le magasin [géolocalisation](sample-stores.md#contexthub-geolocation-sample-store-candidate) est utilisé pour déterminer la latitude de l&#39;utilisateur.
* Ensuite, l&#39;élément de données du mois du [magasin surferinfo](sample-stores.md#contexthub-surferinfo-sample-store-candidate) détermine la saison où il se trouve dans cette latitude.

>[!WARNING]
>
>Les segments installés sont fournis en tant que configurations de référence pour vous aider à créer votre propre configuration dédiée pour votre projet et ne doivent donc pas être utilisés directement.

## Débogage de ContextHub {#debugging-contexthub}

Il existe un certain nombre d’options pour déboguer ContextHub, y compris la génération de journaux. Voir [Configuration de ContextHub pour plus d’informations.](configuring-contexthub.md#logging-debug-messages-for-contexthub)

## Affichage d’un aperçu de la structure ContextHub {#see-an-overview-of-the-contexthub-framework}

ContextHub fournit une [page de diagnostics](contexthub-diagnostics.md) qui affiche un aperçu de sa structure.
