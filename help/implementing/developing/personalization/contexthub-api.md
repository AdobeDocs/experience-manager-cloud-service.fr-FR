---
title: Référence de l’API JavaScript ContextHub
description: L’API JavaScript ContextHub est disponible pour vos scripts lorsque le composant ContextHub a été ajouté à la page.
exl-id: ec35bef5-610c-4e85-a43a-d4201b5eb03e
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '4620'
ht-degree: 85%

---

# Référence de l’API JavaScript ContextHub {#contexthub-javascript-api-reference}

L’API JavaScript ContextHub est disponible pour vos scripts lorsque la variable [Le composant ContextHub a été ajouté à la page.](adding-contexthub.md).

## Constantes ContextHub {#contexthub-constants}

Valeurs constantes définies par l’API JavaScript ContextHub.

### Constantes d’événement {#event-constants}

Le tableau suivant répertorie les noms des événements qui se produisent pour les magasins ContextHub. Voir aussi [ContextHub.Utils.Eventing](#contexthub-utils-eventing).

| Constante | Description | Valeur |
|---|---|---|
| `ContextHub.Constants.EVENT_NAMESPACE` | Espace de nommage d’événement de ContextHub | `ch` |
| `ContextHub.Constants.EVENT_ALL_STORES_READY` | Indique que tous les magasins requis sont enregistrés, initialisés et prêts à être consommés | `all-stores-ready` |
| `ContextHub.Constants.EVENT_STORES_PARTIALLY_READY` | Indique que certains magasins n’ont pas été initialisés dans un délai défini | `stores-partially-ready` |
| `ContextHub.Constants.EVENT_STORE_REGISTERED` | Déclenché lorsqu’un magasin est enregistré | `store-registered` |
| `ContextHub.Constants.EVENT_STORE_READY` | Indique que le magasin est prêt à fonctionner. Il est déclenché immédiatement après l’enregistrement, à l’exception du cas des magasins JSONP où il est déclenché lorsque les données sont extraites). | `store-ready` |
| `ContextHub.Constants.EVENT_STORE_UPDATED` | Déclenché lorsqu’un magasin met à jour sa persistance | `store-updated` |
| `ContextHub.Constants.PERSISTENCE_CONTAINER_NAME` | Nom du conteneur de persistance | `ContextHubPersistence` |
| `ContextHub.Constants.SERVICE_RAW_RESPONSE_KEY` | Stocke le nom de clé de persistance spécifique où est stocké le résultat JSON brut | `/_/raw-response` |
| `ContextHub.Constants.SERVICE_RESPONSE_TIME_KEY` | Stocke une date et une heure spécifiques indiquant quand les données JSON ont été extraites | `/_/response-time` |
| `ContextHub.Constants.SERVICE_LAST_URL_KEY` | Stocke l’URL spécifique du service JSON utilisé pendant le dernier appel | `/_/url` |
| `ContextHub.Constants.IS_CONTAINER_EXPANDED` | Indique si l’IU ContextHub est développée | `/_/container-expanded` |

### Constantes d’événement de l’IU {#ui-event-constants}

Le tableau suivant répertorie les noms des événements qui se produisent pour l’IU ContextHub.

| **Constante** | **Description** | **Valeur** |
|---|---|---|
| `ContextHub.Constants.EVENT_UI_MODE_REGISTERED` | Déclenché lorsqu’un mode est enregistré | `ui-mode-registered` |
| `ContextHub.Constants.EVENT_UI_MODE_UNREGISTERED` | Déclenché lorsque l’enregistrement d’un mode est annulé | `ui-mode-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODE_RENDERER_REGISTERED` | Déclenché lorsqu’un moteur de rendu de mode est enregistré | `ui-mode-renderer-registered` |
| `ContextHub.Constants.EVENT_UI_MODE_RENDERER_UNREGISTERED` | Déclenché lorsque l’enregistrement d’un moteur de rendu est annulé | `ui-mode-renderer-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODE_ADDED` | Déclenché lorsqu’un nouveau mode est ajouté | `ui-mode-added` |
| `ContextHub.Constants.EVENT_UI_MODE_REMOVED` | Déclenché lorsqu’un mode est supprimé | `ui-mode-removed` |
| `ContextHub.Constants.EVENT_UI_MODE_SELECTED` | Déclenché lorsqu’un mode est sélectionné par l’utilisateur | `ui-mode-selected` |
| `ContextHub.Constants.EVENT_UI_MODULE_REGISTERED` | Déclenché lorsqu’un nouveau module est enregistré | `ui-module-registered` |
| `ContextHub.Constants.EVENT_UI_MODULE_UNREGISTERED` | Déclenché lorsque l’enregistrement d’un module est annulé | `ui-module-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODULE_RENDERER_REGISTERED` | Déclenché lorsqu’un moteur de rendu de module est enregistré | `ui-module-renderer-registered` |
| `ContextHub.Constants.EVENT_UI_MODULE_RENDERER_UNREGISTERED` | Déclenché lorsque l’enregistrement d’un moteur de rendu de mode est annulé | `ui-module-renderer-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODULE_ADDED` | Déclenché lorsqu’un nouveau module est ajouté | `ui-module-added` |
| `ContextHub.Constants.EVENT_UI_MODULE_REMOVED` | Déclenché lorsqu’un module est supprimé | `ui-module-removed` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_ADDED` | Déclenché lorsque le conteneur d’IU est ajouté à la page | `ui-container-added` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_OPENED` | Déclenché lorsque l’IU ContextHub est ouverte | `ui-container-opened` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_CLOSED` | Déclenché lorsque l’IU ContextHub est réduite | `ui-container-closed` |
| `ContextHub.Constants.EVENT_UI_PROPERTY_MODIFIED` | Déclenché lorsqu’une propriété est modifiée | `ui-property-modified` |
| `ContextHub.Constants.EVENT_UI_RENDERED` | Déclenché à chaque fois que l’IU ContextHub est rendue (par exemple, après un changement de propriété) | `ui-rendered` |
| `ContextHub.Constants.EVENT_UI_INITIALIZED` | Déclenché lorsque le conteneur d’IU est initialisé | `ui-initialized` |
| `ContextHub.Constants.ACTIVE_UI_MODE` | Indique le mode d’IU actif | `/_/active-ui-mode` |

## Référence de l’API JavaScript ContextHub {#contexthub-javascript-api-reference-2}

L’objet ContextHub fournit l’accès à tous les magasins.

### Fonctions (ContextHub) {#functions-contexthub}

#### getAllStores() {#getallstores}

Renvoie tous les magasins ContextHub enregistrés.

Cette fonction ne comporte aucun paramètre.

##### Renvoie {#returns-}

Un objet qui contient tous les magasins ContextHub. Chaque magasin est un objet qui utilise le même nom que le magasin.

##### Exemple {#example-}

L’exemple suivant récupère tous les magasins, puis récupère le magasin de géolocalisation :

```javascript
var allStores = ContextHub.getAllStores();
var geoloc = allStores.geolocation
```

#### getStore(name) {#getstore-name}

Récupère un magasin en tant qu’objet JavaScript.

##### Paramètres {#parameters-}

* **`name` :** nom sous lequel le magasin a été enregistré.

##### Renvoie {#returns-getstore-name}

Un objet qui représente le magasin.

##### Exemple {#example-getstore-name}

L’exemple suivant récupère le magasin de géolocalisation :

```javascript
var geoloc = ContextHub.getStore("geolocation");
```

## ContextHub.SegmentEngine.Segment {#contexthub-segmentengine-segment}

Représente un segment ContextHub. Utilisez `ContextHub.SegmentEngine.SegmentManager` pour obtenir des segments.

### Fonctions (ContextHub.ContextEngine.Segment) {#functions-contexthub-contextengine-segment}

#### getName() {#getname}

Renvoie le nom du segment sous la forme d’une valeur String .

#### getPath() {#getpath}

Renvoie le chemin du référentiel pour la définition de segment sous forme de chaîne.

## ContextHub.SegmentEngine.SegmentManager {#contexthub-segmentengine-segmentmanager}

Fournit un accès aux segments ContextHub.

### Fonctions (ContextHub.SegmentEngine.SegmentManager) {#functions-contexthub-segmentengine-segmentmanager}

#### getResolvedSegments() {#getresolvedsegments}

Renvoie les segments résolus dans le contexte actuel. Cette fonction ne comporte aucun paramètre.

##### Renvoie {#returns-getresolvedsegments}

Un tableau d’objets `ContextHub.SegmentEngine.Segment`.

## ContextHub.Store.Core {#contexthub-store-core}

Classe de base pour les magasins ContextHub.

### Propriétés (ContextHub.Store.Core) {#properties-contexthub-store-core}

#### eventing {#eventing}

Un objet [`ContextHub.Utils.Eventing`](#contexthub-utils-eventing). Utilisez cet objet pour que les fonctions de liaison stockent les événements. Pour plus d’informations sur la valeur par défaut et l’initialisation, voir [`init(name,config)`](#init-name-config).

#### name {#name}

Nom du magasin

#### persistence {#persistence}

Un objet `ContextHub.Utils.Persistence`. Pour plus d’informations sur la valeur par défaut et l’initialisation, voir [`init(name,config)`](#init-name-config).

### Fonctions (ContextHub.Store.Core) {#functions-contexthub-store-core}

#### addAllItems(tree, options) {#addallitems-tree-options}

Fusionne un objet de données ou un tableau contenant les données de magasin. Chaque paire clé/valeur de l’objet ou du tableau est ajoutée au magasin (via la fonction `setItem`) :

* **Objet :** les clés sont les noms des propriétés.
* **Table :** les clés sont les index de tableau.

Notez que les valeurs peuvent être des objets.

##### Paramètres {#parameters-addallitems}

* **`tree` :** (objet ou tableau). Données à ajouter au magasin.
* **`options` :** (objet). Objet facultatif d’options transmis à la fonction setItem. Pour plus d’informations, reportez-vous au paramètre `options` de [`setItem(key,value,options)`](#setitem-key-value-options).

##### Renvoie {#returns-addallitems}

Une valeur `boolean` :

* Une valeur `true` indique que l’objet de données a été stocké.
* Une valeur `false` indique que le magasin de données reste inchangé.

#### addReference(key, anotherKey) {#addreference-key-anotherkey}

Crée une référence d’une clé à une autre. Une clé ne peut pas se référencer.

##### Paramètres {#parameters-addreference}

* **`key` :** clé qui référence `anotherKey`.

* **`anotherkey` :** clé référencée par le paramètre `key`.

##### Renvoie {#returns-addreference}

Une valeur `boolean` :

* Une valeur `true` indique que la référence a été ajoutée.
* Une valeur `false` indique qu’aucune référence n’a été ajoutée.

#### announceReadiness() {#announcereadiness}

Déclenche l’événement `ready` pour ce magasin. Cette fonction ne comporte aucun paramètre et ne renvoie aucune valeur.

#### clean() {#clean}

Supprime toutes les données du magasin. La fonction ne comporte aucun paramètre et aucune valeur renvoyée.

#### getItem(key)  {#getitem-key}

Renvoie la valeur associée à une clé.

##### Paramètres {#parameters-getitem}

* **`key` :** (chaîne) clé pour laquelle il faut retourner la valeur.

##### Renvoie {#returns-getitem}

Un objet qui représente la valeur de la clé.

#### getKeys(includeInternals) {#getkeys-includeinternals}

Récupère les clés du magasin. Vous pouvez éventuellement récupérer les clés utilisées en interne par la structure ContextHub.

##### Paramètres {#parameters-getkeys}

* **`includeInternals` :** une valeur `true` inclut les clés utilisées en interne dans les résultats. Ces clés commencent par le caractère de soulignement (`_`). La valeur par défaut est `false`.

##### Renvoie {#returns-getkeys}

Tableau de noms de clés (valeurs `string`).

#### getReferences() {#getreferences}

Récupère les références du magasin.

##### Renvoie {#returns-getreferences}

Tableau qui utilise des clés de référencement comme index des clés référencées :

* Les clés de référencement correspondent au paramètre `key` de la fonction `addReference`.
* Les clés référencées correspondent au paramètre `anotherKey` de la fonction `addReference`.

#### getTree(includeInternals) {#gettree-includeinternals}

Récupère l’arbre de données du magasin. Vous pouvez éventuellement inclure les paires clé/valeur utilisées en interne par la structure ContextHub.

##### Paramètres {#parameters-gettree}

* `includeInternals:` une valeur de `true` inclut les paires clé/valeur utilisées en interne dans les résultats. Les clés de ces données commencent par le caractère de soulignement (`_`). La valeur par défaut est `false`.

##### Renvoie {#returns-gettree}

Un objet qui représente l’arbre de données. Les clés sont les noms des propriétés de l’objet.

#### init(name, config)  {#init-name-config}

Initialise le magasin.

* Définit les données du magasin sur un objet vide.
* Définit les références du magasin sur un objet vide.
* Le `eventChannel` est `data:<name>`, où `<name>` correspond au nom du magasin.
* Le `storeDataKey` est `/store/<name>`, où `<name>` correspond au nom du magasin.

##### Paramètres {#parameters-init}

* **`name` :** nom du magasin.
* **`config` :** objet qui contient des propriétés de configuration :
   * `eventDeferring` : la valeur par défaut est 32.
   * `eventing` : objet [ContextHub.Utils.Eventing](#contexthub-utils-eventing) pour ce magasin. La valeur par défaut est l’objet `ContextHub.eventing` utilisé.
   * `persistence` : objet `ContextHub.Utils.Persistence` pour ce magasin. La valeur par défaut est l’objet `ContextHub.persistence`.

#### isEventingPaused() {#iseventingpaused}

Détermine si le déclenchement d’événement est suspendu pour ce magasin.

##### Renvoie {#returns-iseventingpaused}

Une valeur booléenne :

* `true` : le mode Eventing est suspendu afin qu’aucun événement ne soit déclenché pour ce magasin.
* `false` : le mode Eventing n’est pas suspendu, de sorte que les événements sont déclenchés pour ce magasin.

#### pauseEventing() {#pauseeventing}

Suspend le mode Eventing pour le magasin afin qu’aucun événement ne soit déclenché. Cette fonction ne nécessite aucun paramètre et ne renvoie aucune valeur.

#### removeItem(key, options)  {#removeitem-key-options}

Supprime une paire clé/valeur du magasin.

Lorsqu’une clé est supprimée, la fonction déclenche l’événement `data`. Les données d’événement incluent le nom du magasin, le nom de la clé qui a été supprimée, la valeur qui a été supprimée, la nouvelle valeur pour la clé (null) et le type d’action « remove ».

En option, vous pouvez empêcher le déclenchement de l’événement `data`.

##### Paramètres {#parameters-removeitem}

* **`key` :** (chaîne). Nom de la clé à supprimer.
* **`options` :** (objet). Objet d’options. Les propriétés d’objet suivantes sont valides :
   * silent : une valeur `true` empêche le déclenchement de l’événement `data`. La valeur par défaut est `false`.

##### Renvoie {#returns-removeitem}

Une valeur `boolean` :

* Une valeur `true` indique que la paire clé/valeur a été supprimée.
* Une valeur `false` indique que le magasin de données reste inchangé, car la clé est introuvable dans le magasin.

#### removeReference(key) {#removereference-key}

Supprime une référence du magasin.

##### Paramètres {#parameters-removereference}

* **`key` :** référence de clé à supprimer. Ce paramètre correspond au paramètre `key` de la fonction `addReference`.

##### Renvoie {#returns-removereference}

Une valeur `boolean` :

* Une valeur `true` indique que la référence a été supprimée.
* Une valeur `false` indique que la clé n’était pas valide et que le magasin reste inchangé.

#### reset(keepRemainingData) {#reset-keepremainingdata}

Rétablit les valeurs d’origine des données persistantes du magasin. En option, vous pouvez supprimer toutes les autres données du magasin. L’événement est suspendu pour ce magasin pendant sa réinitialisation. Cette fonction ne renvoie aucune valeur.

Les valeurs initiales sont fournies dans la propriété `initialValues` de l’objet de configuration utilisé pour instancier l’objet magasin.

##### Paramètres {#parameters-reset}

* **`keepRemainingData`** : (booléen). Une valeur true entraîne la persistance des données non initiales. Une valeur false entraîne la suppression de toutes les données, à l’exception des valeurs initiales.

#### resolveReference(key, retry) {#resolvereference-key-retry}

Récupère une clé référencée. Vous pouvez éventuellement spécifier le nombre d’itérations à utiliser pour résoudre la meilleure correspondance.

##### Paramètres {#parameters-resolvereference}

* **`key` :** (chaîne). Clé pour laquelle il faut résoudre la référence. Ce paramètre `key` correspond au paramètre `key` de la fonction `addReference`.
* **`retry` :** (nombre). Nombre d’itérations à utiliser.

##### Renvoie {#returns-resolvereference}

Valeur `string` représentant la clé référencée. Si aucune référence n’est résolue, la valeur du paramètre `key` est renvoyée.

#### resumeEventing() {#resumeeventing}

Rétablit le mode Eventing pour ce magasin afin que les événements soient déclenchés. Cette fonction ne définit aucun paramètre et ne renvoie aucune valeur.

#### setItem(key, value, options)  {#setitem-key-value-options}

Ajoute une paire clé/valeur au magasin.

Déclenche la variable `data` uniquement si la valeur de la clé est différente de la valeur actuellement stockée pour la clé. Vous pouvez éventuellement empêcher le déclenchement de l’événement `data`.

Les données d’événement incluent le nom du magasin, la clé, la valeur précédente, la nouvelle valeur et le type d’action `set`.

##### Paramètres {#parameters-setitem}

* **`key` :** (chaîne). Nom de la clé.
* **`options` :** (objet). Objet d’options. Les propriétés d’objet suivantes sont valides :
   * `silent` : une valeur `true` empêche le déclenchement de l’événement `data`. La valeur par défaut est `false`.
* **`value` :** (objet). Valeur à associer à la clé.

##### Renvoie {#returns-setitem}

Une valeur `boolean` :

* Une valeur `true` indique que l’objet de données a été stocké.
* Une valeur `false` indique que le magasin de données reste inchangé.

## ContextHub.Store.JSONPStore {#contexthub-store-jsonpstore}

Un magasin contenant des données JSON. Les données sont extraites d’un service JSONP externe ou, facultativement, d’un service qui renvoie des données JSON. Spécifiez les détails du service à l’aide de la fonction [`init`](#init-name-config) lorsque vous créez une instance de cette classe.

Le magasin utilise la persistance en mémoire (variable JavaScript). Les données de magasin sont disponibles uniquement pendant la durée de vie de la page.

ContextHub.Store.JSONPStore étend [ContextHub.Store.Core](#contexthub-store-core) et hérite des fonctions de cette classe.

### Fonctions (ContextHub.Store.JSONPStore) {#functions-contexthub-store-jsonpstore}

#### configureService(serviceConfig, override) {#configureservice-serviceconfig-override}

Configure les détails de connexion au service JSONP que cet objet utilise. Vous pouvez mettre à jour ou remplacer la configuration existante. La fonction ne renvoie aucune valeur.

##### Paramètres {#parameters-configureservice}

* **`serviceConfig` :** objet qui contient les propriétés ci-dessous.
   * `host` : (chaîne). Nom ou adresse IP du serveur.
   * `jsonp` : (booléen). Une valeur true indique que le service est un service JSONP, false dans le cas contraire. Si la valeur est true, l’objet {callback: &quot;ContextHub.Callbacks.*Object.name*} est ajouté à l’objet service.params.
   * `params` : (objet) Paramètres d’URL représentés sous forme de propriétés d’objet. Les noms des paramètres correspondent aux noms de propriétés et leurs valeurs aux valeurs des propriétés.
   * `path` : (chaîne). Chemin d’accès au service.
   * `port` : (nombre). Numéro de port du service.
   * `secure` : (chaîne ou booléen). Détermine le protocole à utiliser pour l’URL du service :
      * `auto` : //
      * `true` : https://
      * `false` : http://
* **override :** (booléen). Une valeur `true` donne lieu au remplacement de la configuration de service existante par les propriétés de `serviceConfig`. Une valeur `false` entraîne la fusion des propriétés de configuration de service existantes avec les propriétés de `serviceConfig`.

#### getRawResponse() {#getrawresponse}

Renvoie la réponse brute mise en cache depuis le dernier appel au service JSONP. La fonction ne nécessite aucun paramètre.

##### Renvoie {#returns-getrawresponse}

Objet représentant la réponse brute.

#### getServiceDetails() {#getservicedetails}

Récupère l’objet de service pour cet objet ContextHub.Store.JSONPStore. L’objet service contient toutes les informations requises pour créer l’URL du service.

##### Renvoie {#returns-getservicedetails}

Un objet possédant les propriétés suivantes :

* **`host` :** (chaîne). Nom ou adresse IP du serveur.
* **`jsonp` :** (booléen). Une valeur true indique que le service est un service JSONP, false dans le cas contraire. Si la valeur est true, l’objet {callback: &quot;ContextHub.Callbacks.*Object.name*} est ajouté à l’objet service.params.
* **`params` :** (objet) Paramètres d’URL représentés sous forme de propriétés d’objet. Les noms des paramètres correspondent aux noms de propriétés et leurs valeurs aux valeurs des propriétés.
* **`path` :** (chaîne). Chemin d’accès au service.
* **`port` :** (nombre). Numéro de port du service.
* **`secure` :** (chaîne ou booléen). Détermine le protocole à utiliser pour l’URL du service :
   * `auto` : //
   * `true` : https://
   * `false` : http://

#### getServiceURL(resolve) {#getserviceurl-resolve}

Récupère l’URL du service JSONP.

##### Paramètres {#parameters-getserviceurl}

* **`resolve` :** (booléen). Détermine s’il faut inclure les paramètres résolus dans l’URL. Une valeur `true` résout les paramètres, `false` le contraire.

##### Renvoie {#returns-getserviceurl}

Une valeur `string` représentant l’URL du service.

#### init(name, config)  {#init-name-config-1}

initialise l’objet `ContextHub.Store.JSONPStore`.

##### Paramètres {#parameters-init-1}

* **`name` :** (chaîne). Nom du magasin.
* **`config` :** (objet). Objet contenant la propriété du service. L’objet JSONPStore utilise les propriétés de l’objet `service` pour construire l’URL du service JSONP :
   * `eventDeferring` : 32.
   * `eventing` : objet ContextHub.Utils.Eventing pour ce magasin. La valeur par défaut est l’objet `ContextHub.eventing`.
   * `persistence` : objet ContextHub.Utils.Persistence pour ce magasin. Par défaut, la persistance de la mémoire est utilisée (objet JavaScript).
   * `service`: (objet)
      * `host` : (chaîne). Nom ou adresse IP du serveur.
      * `jsonp` : (booléen). Une valeur true indique que le service est un service JSONP, false dans le cas contraire. Si la valeur est true, l’objet `{callback: "ContextHub.Callbacks.*Object.name*}` est ajouté à `service.params`.
      * `params` : (objet) Paramètres d’URL représentés sous forme de propriétés d’objet. Les noms et les valeurs des paramètres sont ceux des propriétés de l’objet, respectivement.
      * `path` : (chaîne). Chemin d’accès au service.
      * `port` : (nombre). Numéro de port du service.
      * `secure` : (chaîne ou booléen). Détermine le protocole à utiliser pour l’URL du service :
         * `auto` : //
         * `true` : https://
         * `false` : http://
      * `timeout` : (nombre). Délai d’attente avant que le service JSONP ne réponde, en millisecondes.
         * `ttl` : délai minimal en millisecondes qui s’écoule entre les appels au service JSONP. (Voir la fonction [queryService](#queryservice-reload)).

#### queryService(reload) {#queryservice-reload}

Interroge le service JSONP distant et met en cache la réponse. Si la durée écoulée depuis l’appel précédent à cette fonction est inférieure à la valeur de `config.service.ttl`, le service n’est pas appelé et la réponse mise en cache n’est pas modifiée. En option, vous pouvez forcer l’appel du service. La propriété `config.service.ttl` est définie lors de l’appel de la fonction [init](#init-name-config) pour initialiser le magasin.

Déclenche l’événement ready lorsque la requête est terminée. Si l’URL du service JSONP n’est pas définie, la fonction ne fait rien.

##### Paramètres {#parameters-queryservice}

* **`reload` :** (booléen) une valeur true supprime la réponse mise en cache et force l’appel du service JSONP.

#### reset {#reset}

Réinitialise les valeurs initiales des données persistantes du magasin, puis appelle le service JSONP. En option, vous pouvez supprimer toutes les autres données du magasin. L’événement est suspendu pour ce magasin pendant que les valeurs initiales sont réinitialisées. Cette fonction ne renvoie aucune valeur.

Les valeurs initiales sont fournies dans la propriété initialValues de l’objet de configuration utilisé pour instancier l’objet magasin.

##### Paramètres {#parameters-reset-1}

* **`keepRemainingData` :** (booléen). Une valeur true entraîne la persistance des données non initiales. Une valeur false entraîne la suppression de toutes les données, à l’exception des valeurs initiales.

#### resolveParameter(f) {#resolveparameter-f}

Résout le paramètre donné.

## ContextHub.Store.PersistedJSONPStore {#contexthub-store-persistedjsonpstore}

`ContextHub.Store.PersistedJSONPStore` étend le paramètre [ContextHub.Store.JSONPStore](#contexthub-store-jsonpstore) pour qu’il hérite de toutes les fonctions de cette classe. Toutefois, les données extraites du service JSONP sont conservées conformément à la configuration de la persistance ContextHub. (Voir [Modes de persistance :](adding-contexthub.md#persistence-modes))

## ContextHub.Store.PersistedStore {#contexthub-store-persistedstore}

`ContextHub.Store.PersistedStore` étend [ContextHub.Store.Core](#contexthub-store-core) pour qu’il hérite de toutes les fonctions de cette classe. Les données de ce magasin sont conservées en fonction de la configuration de la persistance ContextHub.

## ContextHub.Store.SessionStore {#contexthub-store-sessionstore}

`ContextHub.Store.SessionStore` étend [ContextHub.Store.Core](#contexthub-store-core) pour qu’il hérite de toutes les fonctions de cette classe. Les données de ce magasin sont conservées en utilisant la persistance en mémoire (objet JavaScript).

## ContextHub.UI {#contexthub-ui}

Gère les modules d’IU et les moteurs de rendu des modules d’IU.

### Fonctions (ContextHub.UI) {#functions-contexthub-ui}

#### registerRenderer(moduleType, renderer, dontRender) {#registerrenderer-moduletype-renderer-dontrender}

Enregistre un moteur de rendu de module d’IU avec ContextHub. Une fois le moteur de rendu enregistré, il peut être utilisé pour [créer des modules d’IU](configuring-contexthub.md#adding-a-ui-module). Utilisez cette fonction lorsque vous [étendez `ContextHub.UI.BaseModuleRenderer`](extending-contexthub.md#creating-contexthub-ui-module-types) pour créer un moteur de rendu de module d’IU personnalisé.

##### Paramètres {#parameters-registerrenderer}

* **`moduleType` :** (chaîne). Identificateur du rendu du module d’IU. Si un moteur de rendu est déjà enregistré à l’aide de la valeur spécifiée, le moteur de rendu existant n’est pas enregistré avant l’enregistrement de ce convertisseur.
* **`renderer` :** (chaîne). Nom de la classe avec laquelle le module d’IU est rendu.
* **`dontRender` :** (booléen). Définir sur `true` pour empêcher le rendu de l’IU ContextHub après l’enregistrement du moteur de rendu. La valeur par défaut est `false`.

##### Exemple {#example-registerrenderer}

L’exemple suivant enregistre un moteur de rendu en tant que type de module `contexthub.browserinfo`.

```javascript
ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());
```

## ContextHub.Utils.Cookie {#contexthub-utils-cookie}

Classe d’utilitaire permettant d’interagir avec les cookies.

### Fonctions (ContextHub.Utils.Cookie) {#functions-contexthub-utils-cookie}

#### exists(key) {#exists-key}

Détermine si un cookie existe.

##### Paramètres {#parameters-exists}

* **`key` :** chaîne `String` qui contient la clé du cookie que vous testez.

##### Renvoie {#returns-exists}

Une valeur `boolean` indique que le cookie existe.

##### Exemple {#example-exists}

```javascript
if (ContextHub.Utils.Cookie.exists("name")) {
   // conditionally-executed code
}
```

#### getAllItems(filter) {#getallitems-filter}

Renvoie tous les cookies dont les clés correspondent à un filtre.

##### Paramètres {#parameters-getallitems}

* **`filter` :** (optionnel) critères d’appariement des clés de cookie. Pour renvoyer tous les cookies, ne spécifiez aucune valeur. Les types suivants sont pris en charge :
   * Chaîne : La chaîne est comparée à la clé du cookie.
   * Tableau : chaque élément du tableau est un filtre.
   * Un objet RegExp : La fonction de test de l’objet est utilisée pour faire correspondre les clés de cookie.
   * Une fonction : fonction qui teste une clé de cookie pour chercher une correspondance. La fonction doit utiliser la clé de cookie comme paramètre et renvoyer la valeur true si le test confirme une correspondance.

##### Renvoie {#returns-getallitems}

Un objet de cookies. Les propriétés de l’objet sont des clés de cookie et les valeurs de clé sont des valeurs de cookie.

##### Exemple {#example-getallitems}

```javascript
ContextHub.Utils.Cookie.getAllItems([/^cq-authoring/, /^cq-editor/])
```

#### getItem(key) {#getitem-key-1}

Renvoie une valeur de cookie.

##### Paramètres {#parameters-getitem-1}

* **`key` :** clé du cookie dont vous voulez renvoyer la valeur.

##### Renvoie {#returns-getitem-1}

La valeur du cookie ou la valeur `null` si aucun cookie n’a été identifié pour la clé.

##### Exemple {#example-getitem-1}

```javascript
ContextHub.Utils.Cookie.getItem("name");
```

#### getKeys(filter) {#getkeys-filter}

Renvoie un tableau des clés des cookies existants correspondant à un filtre.

##### Paramètres {#parameters-getkeys-1}

* **`filter` :** critères d’appariement des clés de cookie. Les types suivants sont pris en charge :
   * Chaîne : La chaîne est comparée à la clé du cookie.
   * Tableau : chaque élément du tableau est un filtre.
   * Un objet RegExp : La fonction de test de l’objet est utilisée pour faire correspondre les clés de cookie.
   * Une fonction : fonction qui teste une clé de cookie pour chercher une correspondance. La fonction doit utiliser la clé de cookie comme paramètre et renvoyer la valeur `true` si le test confirme une correspondance.

##### Renvoie {#returns-getkeys-1}

Un tableau de chaînes où chaque chaîne est la clé d’un cookie qui répond aux critères du filtre.

##### Exemple {#example-getkeys-1}

```javascript
ContextHub.Utils.Cookie.getKeys([/^cq-authoring/, /^cq-editor/])
```

#### removeItem(key, options) {#removeitem-key-options-1}

Supprime un cookie. Pour supprimer le cookie, la valeur est définie sur une chaîne vide et la date d’expiration est définie sur le jour précédant la date actuelle.

##### Paramètres {#parameters-removeitem-1}

* **`key` :** valeur `String` représentant la clé du cookie à supprimer.
* **`options` :** objet contenant des valeurs de propriété pour la configuration des attributs de cookie. Voir la fonction [`setItem`](#setitem-key-value-options) pour plus d’informations. La propriété `expires` n’a aucun effet.

##### Renvoie {#returns-removeitem-1}

Cette fonction ne renvoie pas de valeur.

##### Exemple {#example-removeitem-1}

```javascript
ContextHub.Utils.Cookie.vanish([/^cq-authoring/, 'cq-scrollpos']);
```

#### setItem(key, value, options)  {#setitem-key-value-options-1}

Crée un cookie de la clé et de la valeur en question et ajoute le cookie au document en cours. Vous pouvez éventuellement spécifier des options qui configurent les attributs du cookie.

##### Paramètres {#parameters-setitem-1}

* **`key` :** chaîne contenant la clé du cookie.
* **`value` :** chaîne contenant la valeur du cookie.
* **`options` :** (facultatif). Objet contenant l’une des propriétés suivantes qui configurent les attributs de cookie :
   * `expires` : valeur `date` ou `number` qui définit le délai d’expiration du cookie. Une valeur de date spécifie l’heure absolue d’expiration. Un nombre (en jours) définit l’heure d’expiration sur l’heure actuelle plus le nombre. La valeur par défaut est `undefined`.
   * `secure` : valeur `boolean` qui définit l’attribut `Secure` du cookie. La valeur par défaut est `false`.
   * `path` : valeur `String` à utiliser comme attribut `Path` du cookie. La valeur par défaut est `undefined`.

##### Renvoie {#returns-setitem-1}

Le cookie avec la valeur définie.

##### Exemple {#example-setitem-1}

```javascript
ContextHub.Utils.Cookie.setItem("name", "mycookie", {
    expires: 3,
    domain: 'localhost',
    path: '/some/directory',
    secure: true
});
```

#### vanish(filter, options) {#vanish-filter-options}

Supprime tous les cookies répondant aux critères d’un filtre donné. Les cookies sont mis en correspondance à l’aide de la fonction `getKeys` et supprimés à l’aide de la fonction `removeItem`.

##### Paramètres {#parameters-vanish}

* **`filter` :** argument `filter` à utiliser dans l’appel de la fonction [`getKeys`](#getkeys-filter).
* **`options` :** argument `options` à utiliser dans l’appel de la fonction [`removeItem`](#removeitem-key-options).

##### Renvoie {#returns-vanish}

Cette fonction ne renvoie pas de valeur.

## ContextHub.Utils.Eventing {#contexthub-utils-eventing}

Vous permet d’associer et de dissocier des fonctions aux événements du magasin ContextHub. Accédez aux objets `ContextHub.Utils.Eventing` d’un magasin à l’aide de sa propriété [eventing](#eventing).

### Fonctions (ContextHub.Utils.Eventing) {#functions-contexthub-utils-eventing}

#### off(name, selector) {#off-name-selector}

Dissocie une fonction d’un événement.

##### Paramètres {#parameters-off}

* **`name` :** [nom de l’événement](#contexthub-utils-eventing) duquel vous dissociez la fonction.
* **`selector` :** sélecteur identifiant l’association. (Voir le paramètre `selector` pour les fonctions [`on`](#on-name-handler-selector-triggerforpastevents) et [`once`](#once-name-handler-selector-triggerforpastevents)).

##### Renvoie {#returns-off}

Cette fonction ne renvoie aucune valeur.

#### on(name, handler, selector, triggerForPastEvents) {#on-name-handler-selector-triggerforpastevents}

Associe une fonction à un événement. La fonction est appelée à chaque fois que l’événement se produit. Vous pouvez éventuellement appeler la fonction pour les événements survenus dans le passé, avant que la liaison ne soit établie.

##### Paramètres {#parameters-on}

* **`name` :** (chaîne). [Nom de l’événement](#contexthub-utils-eventing) auquel vous associez la fonction.
* **`handler` :** (fonction). Fonction à associer à l’événement.
* **`selector` :** (chaîne). Identificateur unique de la liaison. Le sélecteur est nécessaire pour identifier l’association si vous souhaitez utiliser la fonction `off` pour supprimer l’association.
* **`triggerForPastEvents` :** (booléen). Indique si le gestionnaire doit être exécuté pour les événements survenus dans le passé. Une valeur `true` appelle le gestionnaire pour les événements passés. Une valeur `false` appelle le gestionnaire pour les événements futurs. La valeur par défaut est `true`.

##### Renvoie {#returns-on}

Lorsque l’argument `triggerForPastEvents` est défini sur `true`, cette fonction renvoie une valeur `boolean` qui indique si l’événement s’est déjà produit :

* `true`: L’événement s’est produit dans le passé et le gestionnaire est appelé.
* `false` : l’événement ne s’est pas produit dans le passé.

Si `triggerForPastEvents` est défini sur `false`, cette fonction ne renvoie aucune valeur.

##### Exemple {#example-on}

L’exemple suivant associe une fonction à l’événement de données du magasin de géolocalisation. La fonction remplit un élément sur la page avec la valeur de l’élément de données de latitude du magasin.

```html
<div class="location">
    <p>latitude: <span id="lat"></span></p>
</div>

<script>
    var geostore = ContextHub.getStore("geolocation");
    geostore.eventing.on(ContextHub.Constants.EVENT_DATA_UPDATE,getlat,"getlat");

    function getlat(){
       latitude = geostore.getItem("latitude");
       $("#lat").html(latitude);
    }
</script>
```

#### once(name, handler, selector, triggerForPastEvents) {#once-name-handler-selector-triggerforpastevents}

Associe une fonction à un événement. La fonction est appelée une seule fois, pour la première occurrence de l’événement. Vous pouvez éventuellement appeler la fonction pour l’événement qui s’est produit dans le passé, avant que la liaison ne soit établie.

##### Paramètres {#parameters-once}

* **`name` :** (chaîne). [Nom de l’événement](#contexthub-utils-eventing) auquel vous associez la fonction.
* **`handler` :** (fonction). Fonction à associer à l’événement.
* **`selector` :** (chaîne). Identificateur unique de la liaison. Le sélecteur est nécessaire pour identifier l’association si vous souhaitez utiliser la fonction `off` pour supprimer l’association.
* **`triggerForPastEvents` :** (booléen). Indique si le gestionnaire doit être exécuté pour les événements survenus dans le passé. Une valeur `true` appelle le gestionnaire pour les événements passés. Une valeur `false` appelle le gestionnaire pour les événements futurs. La valeur par défaut est `true`.

##### Renvoie {#returns-once}

Lorsque l’argument `triggerForPastEvents` est défini sur `true`, cette fonction renvoie une valeur `boolean` qui indique si l’événement s’est déjà produit :

* `true`: L’événement s’est produit dans le passé et le gestionnaire est appelé.
* `false` : l’événement ne s’est pas produit dans le passé.

Si `triggerForPastEvents` est défini sur `false`, cette fonction ne renvoie aucune valeur.

## ContextHub.Utils.inheritance {#contexthub-utils-inheritance}

Classe d’utilitaire qui permet à un objet d’hériter des propriétés et des méthodes d’un autre objet.

### Fonctions (ContextHub.Utils.inheritance) {#functions-contexthub-utils-inheritance}

#### inherit(child, parent) {#inherit-child-parent}

Permet à l’objet d’hériter des propriétés et des méthodes d’un autre objet.

##### Paramètres {#parameters-inherit}

* **`child` :** (objet). Objet qui hérite des propriétés.
* **`parent` :** (objet). Objet qui définit les propriétés et les méthodes héritées.

## ContextHub.Utils.JSON {#contexthub-utils-json}

Fournit des fonctions pour sérialiser les objets au format JSON et désérialiser des chaînes JSON en objets.

### Fonctions (ContextHub.Utils.JSON) {#functions-contexthub-utils-json}

#### parse(data) {#parse-data}

Analyse une valeur de chaîne au format JSON et la convertit en objet JavaScript.

##### Paramètres {#parameters-parse}

* **`data` :** valeur de chaîne au format JSON.

##### Renvoie {#returns-parse}

Objet JavaScript.

##### Exemple {#example-parse}

Le code :

```javascript
ContextHub.Utils.JSON.parse("{'city':'Basel','country':'Switzerland','population':'173330'}");
```

Renvoie l’objet suivant :

```javascript
Object {
   city: "Basel",
   country: "Switzerland",
   population: 173330
}
```

#### stringify(data) {#stringify-data}

Sérialise les valeurs et les objets JavaScript en valeurs de chaîne au format JSON.

##### Paramètres {#parameters-stringify}

* **`data` :** valeur ou objet à sérialiser. Cette fonction prend en charge des valeurs booléennes, tableaux, nombres chaînes et dates.

##### Renvoie {#returns-stringify}

La valeur de chaîne sérialisée. Lorsque `data` est une valeur R `egExp`, cette fonction renvoie un objet vide. Lorsque `data` est une fonction, renvoie `undefined`.

##### Exemple {#example-stringify}

Le code suivant :

```javascript
ContextHub.Utils.JSON.stringify({
   city: "Basel",
   country: "Switzerland",
   population: 173330
});
```

Renvoie :

```javascript
"{'city':'Basel','country':'Switzerland','population':'173330'}":
```

## ContextHub.Utils.JSON.tree {#contexthub-utils-json-tree}

Cette classe facilite la manipulation des objets de données à stocker ou à extraire des magasins ContextHub.

### Fonctions (ContextHub.Utils.JSON.tree) {#functions-contexthub-utils-json-tree}

#### addAllItems() {#addallitems}

Crée une copie d’un objet de données et y ajoute l’arbre de données d’un second objet. La fonction renvoie la copie et ne modifie aucun des objets d’origine. Lorsque les arborescences de données des deux objets contiennent des clés identiques, la valeur du deuxième objet remplace la valeur du premier objet.

##### Paramètres {#parameters-addallitems-1}

* **`tree` :** objet qui est copié.
* **`secondTree` :** l’objet fusionné avec la copie de l’objet `tree`.

##### Renvoie {#returns-addallitems-1}

Objet contenant les données fusionnées.

#### cleanup() {#cleanup}

Crée une copie d’un objet, identifie et supprime les éléments de l’arbre de données qui ne contiennent aucune valeur, une valeur nulle ou indéfinie et renvoie la copie.

##### Paramètres {#parameters-cleanup}

* **`tree` :** objet à nettoyer.

##### Renvoie {#returns-cleanup}

Une copie de l’arborescence qui est nettoyée.

#### getItem() {#getitem}

Récupère la valeur d’un objet pour une clé donnée.

##### Paramètres {#parameters-getitem-2}

* **`tree` :** objet de données.
* **`key` :** clé de la valeur que vous voulez récupérer.

##### Renvoie {#returns-getitem-2}

La valeur qui correspond à la clé. Si la clé possède des clés enfants, cette fonction renvoie un objet complexe. Lorsque le type de la valeur de la clé est `undefined`, la valeur `null` est renvoyée.

##### Exemple {#example-getitem-2}

Examinez l’objet JavaScript suivant :

```javascript
myObject {
  user: {
    location: {
      city: "Basel",
        details: {
          population: 173330,
          elevation: 260
        }
      }
    }
  }
```

L’exemple de code suivant renvoie la valeur `260` :

```javascript
ContextHub.Utils.JSON.tree.getItem(myObject, "/user/location/details/elevation");
```

L’exemple de code suivant récupère la valeur d’une clé possédant des clés enfants :

```javascript
ContextHub.Utils.JSON.tree.getItem(myObject, "/user");
```

La fonction renvoie l’objet suivant :

```javascript
Object {
  location: {
    city: "Basel",
    details: {
      population: 173330,
      elevation: 260
    }
  }
}
```

#### getKeys() {#getkeys}

Récupère toutes les clés de l’arbre de données d’un objet. En option, vous pouvez récupérer uniquement les clés des enfants d’une clé spécifique. Vous pouvez également spécifier un ordre de tri des clés récupérées.

##### Paramètres {#parameters-getkeys-2}

* **`tree` :** objet à partir duquel récupérer les clés de l’arbre de données.
* **`parent` :** (facultatif). Clé d’un élément de l’arbre de données pour lequel vous souhaitez récupérer les clés des éléments enfants.
* **`order` :** (facultatif). Fonction qui détermine l’ordre de tri des clés renvoyées. (Voir [`Array.prototype.sort`](https://developer.mozilla.org/fr-FR/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) sur le réseau de développeurs Mozilla.)

##### Renvoie {#returns-getkeys-2}

Un tableau de clés.

##### Exemple {#example-getkeys-2}

Étudions l’objet suivant :

```javascript
myObject {
  location: {
    weather: {
      temperature: "28C",
      humidity: "77%",
      precipitation: "10%",
      wind: "8km/h"
    },
    city: "Basel",
    country: "Switzerland",
    longitude: 7.5925727,
    latitude: 47.557421
  }
}
```

Le script `ContextHub.Utils.JSON.tree.getKeys(myObject);` renvoie le tableau suivant :

```javascript
["/location", "/location/city", "/location/country", "/location/latitude", "/location/longitude", "/location/weather", "/location/weather/humidity", "/location/weather/precipitation", "/location/weather/temperature", "/location/weather/wind"]
```

#### removeItem() {#removeitem}

Crée une copie d’un objet donné, supprime la branche spécifiée de l’arbre de données et renvoie la copie modifiée.

##### Paramètres {#parameters-removeitem-2}

* **`tree` :** objet de données.
* **`key` :** clé à supprimer.

##### Renvoie {#returns-removeitem-2}

Une copie de l’objet de données d’origine avec la clé supprimée.

##### Exemple {#example-removeitem-2}

Étudions l’objet suivant :

```javascript
myObject {
  one: {
    foo: "bar",
    two: {
      three: {
        four: {
          five: 5,
          six: 6
        }
      }
    }
  }
}
```

L’exemple de script suivant supprime la branche /un/deux/trois/quatre de l’arborescence de données :

```javascript
myObject = ContextHub.Utils.JSON.tree.removeItem(myObject, "/one/two/three/four");
```

La fonction renvoie l’objet suivant :

```javascript
myObject {
  one: {
    foo: "bar"
  }
}
```

#### sanitizeKey(key) {#sanitizekey-key}

Assainit les valeurs de chaîne pour les rendre utilisables sous forme de clés. Pour assainir une chaîne, cette fonction effectue les actions suivantes :

* Réduit plusieurs barres obliques consécutives en une seule barre oblique.
* Supprime les espaces au début et à la fin de la chaîne.
* Divise le résultat en un tableau de chaînes délimitées par des barres obliques.

Utilisez le tableau obtenu pour créer une clé utilisable.

##### Paramètres {#parameters-sanitizekey}

* **`key` :** le `string` à assainir.

##### Renvoie {#returns-sanitizekey}

Un tableau de valeurs `string` où chaque chaîne est la partie de la `key` délimitée par des barres obliques. représente la clé assainie. Si le tableau assaini a une longueur égale à zéro, cette fonction renvoie la valeur `null`.

##### Exemple {#example-sanitizekey}

Le code suivant assainit une chaîne pour générer le tableau `["this", "is", "a", "path"]`, puis génère la clé `"/this/is/a/path"` à partir du tableau :

```javascript
var key = " / this////is/a/path ";
ContextHub.Utils.JSON.tree.sanitizeKey(key)
"/" + ContextHub.Utils.JSON.tree.sanitizeKey(key).join("/");
```

#### setItem(tree, key, value) {#setitem-tree-key-value}

Ajoute une paire clé/valeur à l’arbre de données d’une copie d’un objet. Pour plus d’informations sur les arbres de données, voir [Persistance.](contexthub.md#persistence)

##### Paramètres {#parameters-setitem-2}

* **`tree` :** objet de données.
* **`key` :** clé à associer à la valeur que vous ajoutez. La clé représente le chemin d’accès à l’élément dans l’arbre de données. Cette fonction appelle `ContextHub.Utils.JSON.tree.sanitize` pour assainir la clé avant de l’ajouter.
* **`value` :** valeur à ajouter à l’arbre de données.

##### Renvoie {#returns-setitem-2}

Une copie de l’objet `tree` qui comporte la paire `key`/`value`.

##### Exemple {#example-setitem-2}

Examinez le code JavaScript suivant :

```javascript
var myObject = {
     user: {
        location: {
           city: "Basel"
           }
        }
     };

var myKey = "/user/location/details";

var myValue = {
      population: 173330,
      elevation: 260
     };

myObject = ContextHub.Utils.JSON.tree.setItem(myObject, myKey, myValue);
```

## ContextHub.Utils.storeCandidates {#contexthub-utils-storecandidates}

Vous permet d’enregistrer des magasins candidats et de récupérer les candidats enregistrés.

### Fonctions (ContextHub.Utils.storeCandidates) {#functions-contexthub-utils-storecandidates}

#### getRegisteredCandidates(storeType) {#getregisteredcandidates-storetype}

Renvoie les types de magasins enregistrés en tant que magasins candidats. Récupère les candidats enregistrés d’un type de magasin spécifique ou de tous les types de magasin.

##### Paramètres {#parameters-getregisteredcandidates}

* **`storeType` :** (chaîne). Nom du type de magasin. Voir le paramètre `storeType` de la fonction [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#contexthub-utils-storecandidates).

##### Renvoie {#returns-getregisteredcandidates}

Un objet de types de magasin. Les propriétés de l’objet sont les noms des types de magasin et les valeurs de propriété sont un tableau des magasins candidats enregistrés.

#### getStoreFromCandidates(storeType) {#getstorefromcandidates-storetype}

Renvoie un type de magasin parmi les candidats enregistrés. Si plus d’un type de magasin du même nom sont enregistrés, la fonction renvoie le type de magasin avec la priorité la plus élevée.

##### Paramètres {#parameters-getstorefromcandidates}

* `storeType` : (chaîne). Nom du magasin candidat. Voir le paramètre `storeType` de la fonction [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#registerstorecandidate-store-storetype-priority-applies).

##### Renvoie {#returns-getstorefromcandidates}

Un objet qui représente le magasin candidat enregistré. Si le type de magasin demandé n’est pas enregistré, une erreur est générée.

#### getSupportedStoreTypes() {#getsupportedstoretypes}

Renvoie les noms des magasins enregistrés en tant que magasins candidats. Cette fonction ne nécessite aucun paramètre.

##### Renvoie {#returns-getsupportedstoretypes}

Un tableau de valeurs sous forme de chaîne où chaque chaîne correspond au type de magasin avec lequel un magasin candidat a été enregistré. Voir le paramètre `storeType` de la fonction [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#contexthub-utils-storecandidates).

#### registerStoreCandidate(store, storeType, priority, applies) {#registerstorecandidate-store-storetype-priority-applies}

Enregistre un objet magasin en tant que magasin candidat à l’aide d’un nom et d’une priorité.

La priorité est un nombre qui indique l’importance des magasins de même nom. Lorsqu’un magasin candidat est enregistré sous le même nom qu’un magasin candidat déjà enregistré, le candidat ayant la priorité la plus élevée est utilisé. Lors de l’enregistrement d’un candidat de magasin, le magasin n’est enregistré que si la priorité est supérieure aux candidats de magasin enregistrés portant le même nom.

##### Paramètres {#parameters-registerstorecandidate}

* **`store` :** (objet). Objet magasin à enregistrer en tant que magasin candidat.
* **`storeType` :** (chaîne). Nom du magasin candidat. Cette valeur est requise lors de la création d’une instance du magasin candidat.
* **`priority` :** (nombre). Priorité du magasin candidat.
* **`applies` :** (Fonction). Fonction à appeler pour évaluer l’applicabilité du magasin dans l’environnement actuel. La fonction doit renvoyer la valeur `true` si le magasin est applicable, et `false` dans le cas contraire. La valeur par défaut est une fonction qui renvoie la valeur true : `function() {return true;}`

##### Exemple {#example-registerstorecandidate}

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandiate', 0);
```
