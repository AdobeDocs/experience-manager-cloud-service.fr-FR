---
title: Fonctions d’AEM Edge
description: Découvrez comment exécuter JavaScript au niveau de la couche CDN avec les fonctions AEM Edge pour activer la personnalisation, la sécurité et les expériences dynamiques proches de l’utilisateur final.
feature: Developing, Edge Delivery Services
role: Developer
exl-id: 9cebe65c-6aea-4096-9c58-f88295a80639
source-git-commit: 3d12f495e0f1a07c81033b93fd607fd260023c48
workflow-type: tm+mt
source-wordcount: '1441'
ht-degree: 2%

---

# Fonctions d’AEM Edge {#aem-edge-functions}

>[!IMPORTANT]
>
>AEM Edge Functions est une fonctionnalité **bêta**. Les fonctionnalités et la documentation peuvent changer sans préavis. Pour rejoindre le programme d’accès anticipé et soumettre vos commentaires, envoyez un e-mail à l’adresse [](mailto:aemcs-edgecompute-feedback@adobe.com).

AEM Edge Functions vous permet d’exécuter JavaScript au niveau de la couche CDN, ce qui rapproche le traitement des données de l’utilisateur final. Cela réduit la latence et permet d’offrir des expériences réactives et dynamiques sans aller-retour vers votre origine.

Cas d’utilisation courants :

- Personnaliser le contenu en fonction d’informations telles que la géolocalisation, le type d’appareil ou les attributs utilisateur
- Fonctionnement en tant que middleware entre le réseau CDN et votre origine
- Reformatage ou agrégation des réponses provenant d’API tierces avant qu’elles n’atteignent le navigateur
- Composer et diffuser des HTML générées par serveur à la périphérie à l’aide de contenu groupé à partir de plusieurs serveurs principaux

Les fonctions AEM Edge sont compatibles avec Edge Delivery Services et la pile Java AEM as a Cloud Service.

## Principaux avantages {#key-benefits}

| Avantage | Description |
|---|---|
| **Performances** | Accélération du TTFB à travers le rendu côté serveur renvoyant un HTML entièrement rendu. Appels d’API à faible latence via des récupérations parallèles et des sauts réseau optimisés. |
| **SEO/GÉO** | Le serveur HTML est indexé à la première explore. Le contenu entièrement rendu est prêt pour les robots d&#39;exploration d’IA. |
| **Sécurité** | Conserver les informations d’identification d’API côté serveur, masquées dans le JavaScript client. Authentifiez-vous auprès d’un fournisseur d’identité et limitez l’accès au contenu. |
| **Personnalisation** | Personnalisez le contenu avant le chargement de la page en fonction des signaux géographiques et des appareils. Exécutez des recherches d’audience à la périphérie pour une diffusion ciblée. |

## Conditions préalables {#prerequisites}

- Un environnement AEM as a Cloud Service
- Le profil de produit Administrateur AEM sur l’instance d’auteur de votre environnement Cloud Service, **ou** le rôle Responsable de déploiement Cloud Manager dans Admin Console pour les sites Edge Delivery Services
- [Node.js et npm](https://nodejs.org/)

## Configuration {#setup}

### Installation de l’interface de ligne de commande Adobe {#install-adobe-cli}

Installez l’interface de ligne de commande Adobe Developer (`aio`) :

```bash
npm install -g @adobe/aio-cli
```

Installez le plug-in des fonctions AEM Edge :

```bash
aio plugins install @adobe/aio-cli-plugin-aem-edge-functions
```

Authentifiez et configurez le plug-in pour votre environnement :

```bash
aio login
aio aem edge-functions setup
```

La commande de configuration vous invite à vous connecter, puis à sélectionner l’environnement AEM sur lequel vous souhaitez utiliser les fonctions AEM Edge.

### Clonez la plaque chauffante {#boilerplate}

Copiez le [aem-edge-functions-boilerplate](https://github.com/adobe/aem-edge-functions-boilerplate) dans votre propre référentiel, puis installez les dépendances :

```bash
npm install
```

## Création De Votre Première Fonction {#create-your-function}

Les services de fonction AEM Edge sont déclarés dans un fichier de configuration YAML et déployés via le pipeline de configuration Cloud Manager.

### &#x200B;1. Configuration d’un pipeline de configuration {#configuration-pipeline}

Avant de créer une fonction Edge, assurez-vous qu’il existe un pipeline de configuration pour votre environnement dans Cloud Manager. Dans le cas contraire, commencez par [créer un pipeline de configuration](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

>[!NOTE]
>
>Si vous utilisez un environnement de développement rapide (RDE), vous pouvez déployer la configuration directement avec `aio aem rde:install -t env-config ./config` au lieu de passer par un pipeline de configuration.

### &#x200B;2. Déclaration Des Services De Fonction Edge {#declare-services}

Créez un fichier nommé `edgeFunctions.yaml` dans votre répertoire de configuration :

```yaml
kind: "EdgeFunctions"
version: "1"
data:
  services:
    - name: my-edge-function
    # Uncomment to enable secrets
    # secrets:
    #   - key: API_TOKEN
    #     value: ${{ API_TOKEN_SECRET }}
```

La limite par défaut est de 1 fonction pour les environnements AEM as a Cloud Service et de 3 pour les sites Edge Delivery Services. Les clés de niveau supérieur sont les suivantes :

| Clé | Description |
|---|---|
| `services` | Liste des services de fonction Edge, chacun identifié par un `name`. |
| `configs` | Paires clé/valeur exposées à tous les services de fonction Edge en tant que variables d’environnement. |
| `secrets` | Paires clé/valeur faisant référence à des secrets Cloud Manager, exposées à tous les services de fonction Edge. |
| `kvs` | Bouton bascule booléen pour configurer un magasin KV pour les données de valeur-clé de lecture/écriture d’exécution partagées sur tous les services de fonction Edge. |

### &#x200B;3. Ajout de règles au sélecteur d’origine du réseau CDN {#cdn-routing}

Les fonctions Edge sont appelées en leur acheminant le trafic du réseau CDN via les règles du sélecteur d’origine. Ajoutez les éléments suivants à votre fichier de configuration `cdn.yaml` (ou créez-en un s’il n’existe pas) :

```yaml
kind: 'CDN'
version: '1'
data:
  originSelectors:
    rules:
      - name: route-weather-to-edge-function
        when: { reqProperty: path, equals: "/weather" }
        action:
          type: selectAemOrigin
          originName: edgefunction-my-edge-function
      - name: route-hello-world-to-edge-function
        when: { reqProperty: path, equals: "/hello-world" }
        action:
          type: selectAemOrigin
          originName: edgefunction-my-edge-function
```

Les règles du sélecteur d’origine vous permettent d’acheminer le trafic vers vos fonctions Edge en fonction de toute condition disponible dans le moteur de règles du réseau CDN, telle qu’un chemin, un domaine ou un en-tête de requête spécifique. Plusieurs règles peuvent acheminer différents chemins vers la même fonction Edge. Voir [Sélecteurs d’origine](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) pour connaître la syntaxe complète des règles.

### &#x200B;4. Déploiement de la configuration {#deploy-configuration}

Validez les `edgeFunctions.yaml` et les `cdn.yaml` dans votre référentiel Git Cloud Manager et déclenchez le pipeline de configuration. Une fois le pipeline terminé avec succès, vos points d’entrée de fonction Edge sont disponibles à l’adresse :

- `publish-pXXXXX-eYYYYY.adobeaemcloud.com/weather`
- `publish-pXXXXX-eYYYYY.adobeaemcloud.com/hello-world`

où `pXXXXX-eYYYYY` sont les coordonnées de votre environnement. Si un domaine personnalisé est configuré, les fonctions sont également accessibles au niveau de ces chemins de domaine (par exemple, `example.com/weather`).

## Créer et déployer le code de fonction AEM Edge {#build-deploy}

### Créer {#build}

Regroupez le code de votre fonction Edge pour le déploiement :

```bash
aio aem edge-functions build
```

### Déployer {#deploy}

Déployez le package créé sur un service de fonction Edge nommé. L’argument `function-name` doit correspondre à la valeur `name` dans `edgeFunctions.yaml` :

```bash
aio aem edge-functions deploy <function-name>
```

## Développement local {#local-development}

### Exécuter localement {#local-run}

Démarrez un serveur de développement local à l’adresse `http://127.0.0.1:7676` :

```bash
aio aem edge-functions serve
```

Voir cette [documentation Compute JavaScript](https://www.fastly.com/documentation/guides/compute/javascript/) pour plus d’informations sur ce que prend en charge l’exécution locale.

### Tester {#test}

Exécutez la suite de tests avec [Mocha](https://mochajs.org/) :

```bash
npm run test
```

### Débogage à distance {#remote-debugging}

Le réseau CDN géré par Adobe n’expose pas de débogueur distant, mais expose la diffusion en continu du journal. Suivez les logs pour qu’une fonction déployée reçoive `console.log` sortie directement dans votre terminal :

```bash
aio aem edge-functions tail-logs <function-name>
```

## Mise en cache et purge du cache {#caching}

Les fonctions Edge peuvent réduire considérablement la charge d’origine et améliorer les temps de réponse en mettant en cache les données Edge. Cependant, la mise en cache nécessite une conception intentionnelle, en particulier dans les fonctions Edge où **deux couches de cache indépendantes** sont impliquées :

```
Browser → AEM CDN (CDN Cache) → AEM Edge Functions (Fetch Cache) → Backend (AEM, APIs, etc.)
```

Avant de configurer la mise en cache, examinez le comportement de votre contenu :

- **Le contenu véritablement unique par demande** (jetons de session, tarification en temps réel pour un utilisateur spécifique) doit contourner la mise en cache pour éviter de fournir des résultats incorrects.
- La **personnalisation basée sur les cohortes** (contenu adapté par région, type d’appareil ou segment d’audience) peut souvent être mise en cache avec des TTL plus courtes ou des en-têtes de `Vary`, car de nombreux utilisateurs partagent la même variante.
- **Contenu stable et partagé** (catalogues de produits, pages CMS, réponses d’API qui changent selon un planning connu) bénéficie d’une mise en cache agressive avec invalidation explicite via des clés de substitution.
- **Se tromper dans un sens ou dans l’autre a des conséquences.** Le surcaching entraîne des bugs de contenu obsolètes, difficiles à diagnostiquer sur deux couches de cache. Le sous-caching va à l’encontre des performances et de l’objectif de déchargement d’origine de l’utilisation des fonctions Edge.

Comme le réseau CDN et le cache de récupération interne de la fonction Edge fonctionnent indépendamment, toute modification des données sous-jacentes nécessite l’invalidation délibérée des couches **des deux**. La compréhension de cette architecture est essentielle pour une gestion fiable du cache.

Pour obtenir des conseils techniques détaillés sur la configuration du comportement de mise en cache, le contrôle des durées de vie du cache, l’utilisation de clés de substitution et la purge du contenu mis en cache, voir [ Mise en cache dans les fonctions AEM Edge ](/help/implementing/developing/introduction/edge-functions-caching.md).

## Limites {#limitations}

Chaque appel de fonction Edge s’exécute dans un sandbox avec des limites de ressources appliquées par la plateforme de calcul sous-jacente.

### Nbre max. d&#39;appels de récupération sortante par appel {#max-fetch-calls}

Les fonctions AEM Edge appliquent une limite stricte de **32 requêtes principales par exécution** (c’est-à-dire par requête entrante gérée par votre fonction). Une fois cette limite atteinte, tous les autres appels `fetch()` échouent avec l’erreur suivante :

```
Requested backend named '…' does not exist
```

Lorsque cette erreur s’affiche et que votre configuration d’origine est correcte, la cause la plus probable est que le quota de requêtes du serveur principal par appel a été épuisé. Consultez [Limites des ressources du calcul rapide](https://docs.fastly.com/products/compute-resource-limits#default-limits) pour obtenir la liste complète des limites de la plateforme.

## Référence de configuration {#configuration-reference}

### Origines {#origins}

Par défaut, les fonctions Edge peuvent être extraites de n’importe quelle origine. Pour restreindre une fonction à un ensemble défini d’origines, déclarez-les sous `origins` dans `edgeFunctions.yaml` :

```yaml
origins:
  - name: my-origin-name
    domain: example.com
```

Référencez l’origine nommée dans le code de votre fonction à l’aide de l’option de récupération `backend` :

```js
const request = new Request("https://example.com/test");
const response = await fetch(request, { backend: "my-origin-name" });
```

>[!NOTE]
>
>Les magasins de services (`configs`, `secrets` et `kvs`) ne sont pas disponibles dans les [programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Les services de fonction Edge eux-mêmes s’exécutent normalement sur des environnements sandbox - seuls les magasins ne sont pas approvisionnés.

### Configuration du service {#service-configuration}

Exposez les variables d’environnement à vos fonctions à l’aide de la clé `configs` dans `edgeFunctions.yaml`. Les valeurs sont stockées dans un magasin de configurations nommé `config_default` :

```yaml
configs:
  - key: LOG_LEVEL
    value: DEBUG
```

Lisez les valeurs de configuration dans votre code de fonction :

```js
import { ConfigStore } from "fastly:config-store";

const config = new ConfigStore('config_default');
const logLevel = config.get('LOG_LEVEL') || 'info';
```

>[!NOTE]
>
>- Le magasin de configuration est toujours nommé `config_default`.
>- Les noms clés respectent la casse.
>- Le magasin de configuration est partagé par tous les services de fonction Edge dans le même environnement.

### Secrets de service {#service-secrets}

Les secrets sont référencés, et non stockés, dans `edgeFunctions.yaml`. Le champ `value` doit pointer vers un secret Cloud Manager en utilisant la syntaxe `${{SECRET_REFERENCE}}`. Définissez d’abord le secret sous-jacent dans Cloud Manager — consultez [Variables du secret Cloud Manager](/help/implementing/cloud-manager/environment-variables.md).

```yaml
secrets:
  - key: API_TOKEN
    value: ${{ API_TOKEN_SECRET }}
```

Récupérez les secrets du code de votre fonction à l’aide de l’assistant `SecretStoreManager` à partir de la page standard :

```js
import { SecretStoreManager } from "./lib/config";

const apiToken = await SecretStoreManager.getSecret('API_TOKEN');
```

>[!NOTE]
>
>- Le secret store est toujours nommé `secret_default`.
>- Les noms clés respectent la casse.
>- Les secrets sont immuables une fois créés.
>- La banque de secrets est partagée sur tous les services de fonction Edge dans le même environnement.

### Service KV Store {#service-kv-store}

Les fonctions Edge peuvent lire et écrire des données de valeur-clé arbitraires au moment de l’exécution via un magasin KV. Pour l’activer, définissez `kvs: true` dans `edgeFunctions.yaml` :

```yaml
kvs: true
```

Cela fournit un magasin KV vide nommé `kv_default`. Renseignez-le au moment de l’exécution à partir du code de votre fonction Edge à l’aide de l’[API Fastly KV Store](https://js-compute-reference-docs.edgecompute.app/docs/fastly:kv-store/KVStore) :

```js
import { KVStore } from "fastly:kv-store";

const kv = new KVStore('kv_default');

// Read a value
const entry = await kv.get('visit-count');
const count = entry ? Number(await entry.text()) : 0;

// Write a value
await kv.put('visit-count', String(count + 1));
```

>[!NOTE]
>
>- Le magasin KV est toujours nommé `kv_default`.
>- Le magasin KV est vide au moment de la mise en service ; renseignez-le au moment de l’exécution via l’[API Fastly KV Store](https://js-compute-reference-docs.edgecompute.app/docs/fastly:kv-store/KVStore). Les entrées de clé/valeur déclaratives dans `edgeFunctions.yaml` ne sont pas prises en charge.
>- Le magasin KV est partagé par tous les services de fonction Edge dans le même environnement.

### Journalisation {#logging}

AEM Edge Functions s’intègre à la fonctionnalité [Transfert de journal AEM](/help/implementing/developing/introduction/log-forwarding.md). Créez un fichier `logForwarding.yaml` avec votre `edgeFunctions.yaml` :

```yaml
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["rde", "dev", "stage", "prod"]
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

Utilisez l’enregistreur dans le code de votre fonction pour écrire des entrées de journal structurées :

```js
import { Logger } from "fastly:logger";

const logger = new Logger("customerSplunk");
logger.log(JSON.stringify({
  method: event.request.method,
  url: event.request.url
}));
```

>[!NOTE]
>
>Les journaux CDN, qui incluent les entrées du journal des fonctions AEM Edge, peuvent être téléchargés à partir de Cloud Manager pour les environnements Java-stack, mais pas pour les sites Edge Delivery Services.
>
