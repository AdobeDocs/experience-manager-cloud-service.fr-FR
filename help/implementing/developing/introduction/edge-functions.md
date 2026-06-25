---
title: Fonctions d’AEM Edge
description: Découvrez comment exécuter JavaScript au niveau de la couche CDN avec les fonctions AEM Edge pour activer la personnalisation, la sécurité et les expériences dynamiques proches de l’utilisateur final.
feature: Developing, Edge Delivery Services
role: Developer
exl-id: 9cebe65c-6aea-4096-9c58-f88295a80639
source-git-commit: e0a62aa70aa24c4aa85c65a3dc1dfa0432f189eb
workflow-type: tm+mt
source-wordcount: '1975'
ht-degree: 1%

---

# Fonctions d’AEM Edge {#aem-edge-functions}

>[!IMPORTANT]
>
>AEM Edge Functions est une fonctionnalité **bêta publique** qui vous permet de l’essayer en libre-service sans contacter Adobe pour l’activer. Adobe vous encourage à envoyer un e-mail à l’adresse [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) pour décrire votre cas d’utilisation afin qu’Adobe puisse vous assurer qu’il est pris en charge et vous fournir tous les conseils nécessaires. En utilisant le Beta Fonctions d’AEM Edge, vous reconnaissez qu’il est toujours en développement et que vous ne devriez pas vous fier au bon fonctionnement de la technologie ou à la disponibilité des données. Cette fonctionnalité est fournie en l’état, peut changer sans préavis et n’est pas couverte par la production.

AEM Edge Functions vous permet d’exécuter JavaScript au niveau de la couche CDN, ce qui rapproche le traitement des données de l’utilisateur final. Cela réduit la latence et permet d’offrir des expériences réactives et dynamiques sans aller-retour vers votre origine.

Cas d’utilisation courants :

- Personnaliser le contenu en fonction d’informations telles que la géolocalisation, le type d’appareil ou les attributs utilisateur
- Fonctionnement en tant que middleware entre le réseau CDN et votre origine
- Reformatage ou agrégation des réponses provenant d’API tierces avant qu’elles n’atteignent le navigateur
- Composer et diffuser des HTML générées par serveur à la périphérie à l’aide de contenu groupé à partir de plusieurs serveurs principaux

AEM Edge Functions est compatible avec la pile Java Edge Delivery Services et AEM as a Cloud Service, pour les clients AEM Sites.

<!-- Follow this tutorial for a concrete walk-through for both Edge Delivery Services and AEM as a Cloud Service Java-stack variations. -->

## Principaux avantages {#key-benefits}

| Avantage | Description |
|---|---|
| **Performances** | Accélération du TTFB à travers le rendu côté serveur renvoyant un HTML entièrement rendu. Appels d’API à faible latence via des récupérations parallèles et des sauts réseau optimisés. |
| **SEO/GÉO** | Les robots d&#39;exploration d’IA peuvent indexer le contenu assemblé côté serveur. |
| **Sécurité** | Conserver les informations d’identification d’API côté serveur, masquées dans le JavaScript client. Authentifiez-vous auprès d’un fournisseur d’identité et limitez l’accès au contenu. |
| **Personnalisation** | Personnalisez le contenu avant le chargement de la page en fonction des signaux géographiques et des appareils. Exécutez des recherches d’audience à la périphérie pour une diffusion ciblée. |

## Conditions préalables {#prerequisites}

- Un programme Cloud Manager, qui contient des environnements Java-stack AEM ou des sites Edge Delivery Services. Découvrez comment [intégrer EDS Sites à Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).
- Un pipeline de configuration Cloud Manager (appelé pipeline Edge Delivery Services pour les sites EDS).
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

## Enregistrement De Votre Fonction AEM Edge {#register-your-function}

Les fonctions AEM Edge sont déclarées dans un fichier de configuration YAML et déployées via le pipeline de configuration Cloud Manager.

### &#x200B;1. Configuration d’un pipeline de configuration {#configuration-pipeline}

Avant de créer une fonction Edge, assurez-vous que dans Cloud Manager, un pipeline de configuration existe pour votre environnement (si vous utilisez la pile Java AEM) ou qu’il existe un pipeline Edge Delivery Services si votre projet est implémenté avec Edge Delivery Services. Voir [Utiliser des pipelines de configuration](/help/operations/config-pipeline.md) pour plus d’informations sur la configuration des pipelines.

>[!NOTE]
>
>Si vous utilisez un environnement de développement rapide (RDE), vous pouvez déployer la configuration directement avec `aio aem rde:install -t env-config ./config` au lieu de passer par un pipeline de configuration.

### &#x200B;2. Déclaration De Votre Fonction Edge {#declare-functions}

Créez un fichier nommé `edgeFunctions.yaml` dans votre répertoire de configuration :

```yaml
kind: "EdgeFunctions"
version: "1"
data:
  functions:
    - name: my-edge-function
    # add advanced configuration under here
```

Les environnements Java-stack possèdent 1 fonction Edge et les implémentations Edge Delivery Services ont 3 fonctions Edge. Les clés de niveau supérieur facultatives sont les suivantes :

| Clé | Description |
|---|---|
| `functions` | Liste des fonctions Edge, chacune identifiée par un `name`. Pour une rétrocompatibilité, `services` est également acceptée, mais `functions` est la clé préférée. L’utilisation des deux dans le même fichier n’est pas autorisée. |
| `configs` | Paires clé/valeur exposées aux fonctions Edge d’un environnement en tant que variables d’environnement. |
| `secrets` | Paires clé/valeur faisant référence à des secrets Cloud Manager pour les fonctions Edge d’un environnement |
| `kvs` | Bouton bascule booléen pour configurer un magasin KV pour les données de valeur-clé de lecture/écriture d’exécution partagées entre toutes les fonctions Edge dans un environnement. |

Consultez la configuration avancée telle que `configs`, `secrets` et `kvs` dans la [section de configuration avancée](#advanced-function-configuration) ci-dessous.

### &#x200B;3. Déploiement de la fonction Edge via Cloud Manager {#deploy-functions-via-cm}

À l’aide de Cloud Manager, déployez le pipeline de sorte que la fonction Edge soit enregistrée sur le réseau CDN.

## Créer, créer et déployer du code de fonction AEM Edge {#build-deploy}

### Création {#author}

Écrivez votre logique commerciale de code de fonction Edge, en utilisant le [dossier `src` du modèle standard](https://github.com/adobe/aem-edge-functions-boilerplate/tree/main/src) comme point de départ.

### Créer {#build}

Regroupez le code de votre fonction Edge pour le déploiement :

```bash
aio aem edge-functions build
```

### Déployer {#deploy}

Déployez le code de fonction Edge empaqueté sur la fonction Edge nommée. L’argument `function-name` doit correspondre à la valeur `name` dans `edgeFunctions.yaml` :

```bash
aio aem edge-functions deploy <function-name>
```

### Tester {#test}

Assurez-vous que la fonction Edge fonctionne comme prévu. Vous pouvez le tester à l’adresse :

`edgefunction-pXXXXX-eYYYYY-<function name>.adobeaemcloud.com/<path>`

Par exemple, pour la Java-stack AEM : <br/>
`edgefunction-pXXXXX-eYYYYY-my-edge-function.adobeaemcloud.com/weather`

ou pour Edge Delivery Services:<br/>
`edgefunction-pXXXXX-dYYYYY-my-edge-function.adobeaemcloud.com/weather`

Ce domaine avec le préfixe *edgefunction* est uniquement destiné au débogage, mais *ne doit pas être référencé pour le trafic en direct* car il ne s’agit pas d’un nom stable. Pour déterminer la valeur de AAAA, consultez la sortie de la commande de déploiement .


## Connecter au flux de diffusion de contenu {#wiring}

Le trafic des fonctions Edge doit être envoyé au domaine du site web, qui est généralement un domaine personnalisé pour la pile Java AEM, et *doit* être un domaine personnalisé pour Edge Delivery Services Sites.

### &#x200B;1. Définir des sélecteurs d’origine {#origin-selectors}

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

### &#x200B;2. Déploiement de la configuration {#deploy-to-cdn}

Validez le `cdn.yaml` dans votre référentiel Git Cloud Manager et déclenchez le pipeline de configuration. Une fois le pipeline terminé avec succès, vos points d’entrée de fonction Edge sont disponibles à l’adresse :

- `example.com/weather`
- `example.com/hello-world`

Pour le débogage, vous pouvez référencer la fonction Edge au `publish-pXXXXX-eYYYYY.adobeaemcloud.com` du domaine (pour la pile Java AEM) ou `publish-pXXXXX-dYYYYY.adobeaemcloud.com` (pour les sites Edge Delivery Services). N’utilisez pas ce domaine en exploitation, car il ne s’agit pas d’un nom stable. Pour déterminer la valeur de AAAA, consultez la sortie de la commande de déploiement .

## Développement local {#local-development}

### Exécuter localement {#local-run}

Démarrez un serveur de développement local à l’adresse `http://127.0.0.1:7676` :

```bash
aio aem edge-functions serve
```

Voir cette [documentation Compute JavaScript](https://www.fastly.com/documentation/guides/compute/javascript/) pour plus d’informations sur ce que prend en charge l’exécution locale.

### Tester {#test-localdev}

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

- Chaque appel de fonction Edge s’exécute dans un sandbox avec des limites de ressources appliquées par la plateforme de calcul sous-jacente.

- La taille maximale de l’artefact d’assemblage web créé (wasm) est de 100MB

- La consommation mémoire maximale est de 1 Mo de pile d&#39;octets, 128MB tas

- Informations importantes sur l’exécution de la fonction Edge :
   - Une exécution est terminée après 120 s d’heure du mur
   - Les exécutions seront interrompues à 1s du calcul (pas en temps réel)
   - Le temps moyen d’exécution de la fonction Edge doit être inférieur à 100 ms.

- Voir les limites liées aux [Variables de configuration de la fonction ](#function-configuration), aux [Variables secrètes de la fonction Edge](#function-secrets) et aux [magasins KV de fonction Edge](#function-kv-store).

### Nbre max. d&#39;appels de récupération sortante par appel {#max-fetch-calls}

Les fonctions AEM Edge appliquent une limite stricte de **32 requêtes principales par exécution** (c’est-à-dire par requête entrante gérée par votre fonction). Une fois cette limite atteinte, tous les autres appels `fetch()` échouent avec l’erreur suivante :

```
Requested backend named '…' does not exist
```

Lorsque cette erreur s’affiche et que votre configuration d’origine est correcte, la cause la plus probable est que le quota de requêtes du serveur principal par appel a été épuisé. Consultez [Limites des ressources du calcul rapide](https://docs.fastly.com/products/compute-resource-limits#default-limits) pour obtenir la liste complète des limites de la plateforme.

## Configuration avancée des fonctions Edge {#advanced-function-configuration}

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
>Les configurations, secrets et kvs ne sont pas disponibles dans les [programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Les fonctions Edge s’exécutent normalement dans des environnements sandbox, mais seules ces entités ne sont pas configurées.

### Variables de configuration de la fonction Edge {#function-configuration}

Exposez les variables d’environnement à vos fonctions à l’aide de la clé `configs` dans `edgeFunctions.yaml`. Les valeurs sont stockées dans un magasin de configurations nommé `config_default` :

```yaml
kind: "EdgeFunctions"
version: "1"
data:
  functions:
    - name: my-edge-function
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
>- Le magasin de configuration est partagé avec toutes les fonctions Edge dans le même environnement.
>- Le magasin de configuration est répliqué sur le réseau global de diffusion de contenu géré par Adobe
>- 500 entrées max.
>- tailles max. de nom/valeur : 255 et 8 000 caractères


### Variables secrètes de fonction Edge {#function-secrets}

Les secrets sont référencés, et non stockés, dans `edgeFunctions.yaml`. Le champ `value` doit pointer vers un secret Cloud Manager en utilisant la syntaxe `${{SECRET_REFERENCE}}`. Définissez d’abord le secret sous-jacent dans Cloud Manager — consultez [Variables du secret Cloud Manager](/help/implementing/cloud-manager/environment-variables.md).


```yaml
kind: "EdgeFunctions"
version: "1"
data:
  functions:
    - name: my-edge-function
  secrets:
    - key: API_TOKEN
      value: ${{API_TOKEN_SECRET}}
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
>- La banque de secrets est partagée sur toutes les fonctions Edge dans le même environnement.
>- La banque de secrets est répliquée sur le réseau mondial du réseau CDN géré par Adobe
>- La taille maximale de tous les secrets est de 64 Ko

### Boutique KV de fonction Edge {#function-kv-store}

Les fonctions Edge peuvent lire et écrire des données de valeur-clé arbitraires au moment de l’exécution via un magasin KV. Pour l’activer, définissez `kvs: true` dans `edgeFunctions.yaml` :


```yaml
kind: "EdgeFunctions"
version: "1"
data:
  functions:
    - name: my-edge-function
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
>- Le magasin KV est partagé par toutes les fonctions Edge dans le même environnement.
>- Le magasin KV est répliqué sur le réseau global de diffusion de contenu géré par Adobe
>- Les KV Stores offrent une cohérence éventuelle, ce qui signifie que la lecture d&#39;une clé immédiatement après son écriture peut ne pas renvoyer la valeur mise à jour.
>- Les noms des clés KV sont des fichiers UTF-8 de 1 024 octets maximum
>- Taille d&#39;entrée KV max. 25M
>- Les articles du KV Store ont une limite de taux de 1 écriture par seconde par article.
>- Les demandes par lots d’articles du KV Store sont limitées à 100 000 articles par demande.


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
>Les journaux CDN, qui incluent les entrées du journal des fonctions AEM Edge, peuvent être téléchargés à partir de Cloud Manager pour les environnements Java-stack, mais pas pour les sites Edge Delivery.
>
