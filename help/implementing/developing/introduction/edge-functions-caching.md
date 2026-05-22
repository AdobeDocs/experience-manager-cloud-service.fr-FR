---
title: Mise en cache dans les fonctions AEM Edge
description: Découvrez comment le cache de réseau CDN et le cache de récupération des fonctions Edge interagissent, comment configurer le comportement de mise en cache et comment purger le contenu mis en cache sur les deux couches.
feature: Developing, Edge Delivery Services
role: Developer
source-git-commit: ea43e2f4c7e52f98e8458e86bb48f124191dc03c
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 1%

---

# Mise en cache dans les fonctions AEM Edge {#edge-functions-caching}

>[!IMPORTANT]
>
>AEM Edge Functions est une fonctionnalité **bêta**. Les fonctionnalités et la documentation peuvent changer sans préavis. Pour rejoindre le programme d’accès anticipé et soumettre vos commentaires, envoyez un e-mail à l’adresse [&#128279;](mailto:aemcs-edgecompute-feedback@adobe.com).

Cette page fournit des conseils techniques détaillés sur le fonctionnement de la mise en cache dans les fonctions AEM Edge, y compris l’architecture à deux caches, sur la manière de contrôler le comportement de mise en cache dans votre code et sur la manière de purger les entrées de cache lorsque le contenu change.

Pour obtenir des informations générales sur le fonctionnement de la mise en cache d’AEM Cloud Service, consultez [Mise en cache dans AEM as a Cloud Service](/help/implementing/dispatcher/caching.md) et [Le réseau CDN dans AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md). Pour obtenir des exemples de code, reportez-vous au [Modèle des fonctions AEM Edge — Mise en cache](https://github.com/adobe/aem-edge-functions-boilerplate/blob/main/README.md#caching).

## Architecture de mise en cache {#architecture}

Les fonctions AEM Edge se trouvent entre le réseau CDN et les services principaux à partir desquels la fonction récupère. Ces serveurs principaux peuvent être des instances de publication AEM, des API tierces, des bases de données externes ou tout point d’entrée HTTP que votre code appelle. Le flux de requêtes comporte **deux caches distincts** chacun fonctionnant indépendamment :

```
Browser → AEM CDN (CDN Cache) → AEM Edge Functions (Fetch Cache) → Backend (AEM, APIs, etc.)
```

| Cache | Ce qu’il met en cache | Influencé par | Purge |
|---|---|---|---|
| **Cache CDN** | La réponse de la fonction Edge au navigateur | En-têtes de réponse définis par la fonction Edge (`Cache-Control`, `Surrogate-Control`, `Surrogate-Key`) | [API de purge du cache CDN](/help/implementing/dispatcher/cdn-cache-purge.md) |
| **Cache de récupération de fonction** | Réponses du serveur principal aux appels `fetch()` dans la fonction Edge et données stockées via l’API Core Cache | En-têtes de réponse du serveur principal, `CacheOverride` sur des appels de récupération ou clés de substitution programmatiques via l’API Core Cache | Commande ou `purgeSurrogateKey()` de l’interface de ligne de commande `aio aem edge-functions purge-cache` |

Il est essentiel de comprendre cette architecture à deux couches, car chaque cache a une portée différente, des contrôles différents et un mécanisme de purge différent. Une mise en cache efficace nécessite une configuration délibérée aux deux niveaux.

## Cache CDN (externe) {#cdn-cache}

Le cache du réseau CDN se trouve entre le navigateur et la fonction Edge. Il met en cache la **réponse** de la fonction Edge. Vous contrôlez son comportement en définissant des en-têtes de cache HTTP standard sur vos réponses de fonction Edge :

```js
return new Response(body, {
  headers: {
    'Surrogate-Key': 'page-home product-123',
    'Cache-Control': 'public, max-age=3600'
  }
});
```

Plusieurs clés de substitution sont séparées par des espaces. Ces clés de substitution peuvent être utilisées pour purger le cache du réseau CDN à l’aide de l’[API de purge du cache CDN](/help/implementing/dispatcher/cdn-cache-purge.md). Le concept de purge de clé de substitution est identique à celui décrit dans [Purge du cache pour un groupe de ressources](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/caching/how-to/purge-cache#purge-the-cache-for-a-group-of-resources) — la différence essentielle est que les clés de substitution du réseau CDN sont ici définies par votre code de fonction Edge plutôt que par le serveur principal.

## Cache de récupération des fonctions Edge (interne) {#fetch-cache}

Le cache de récupération de la fonction Edge se trouve entre la fonction Edge et les serveurs principaux qu’elle appelle. Il met en cache la réponse **du serveur principal** aux appels `fetch()` effectués dans votre code de fonction Edge. Il contient également toutes les données stockées par votre code via l’[**API Core Cache**](https://js-compute-reference-docs.edgecompute.app/docs/fastly:cache/CoreCache) ou l’[**API Simple Cache**](https://js-compute-reference-docs.edgecompute.app/docs/fastly:cache/SimpleCache), des interfaces de mise en cache programmatiques qui vous permettent de contrôler précisément ce qui est mis en cache, pendant combien de temps et sous quelles clés de substitution.

Il n’est **pas** influencé par les en-têtes que vous définissez sur la réponse sortante de la fonction Edge, mais uniquement par les en-têtes de réponse du serveur principal, par [`CacheOverride`](https://js-compute-reference-docs.edgecompute.app/docs/fastly:cache-override/CacheOverride/) options sur vos appels de récupération ou par les clés de substitution que vous attribuez par programmation lors de l’écriture dans l’API Core Cache.

>[!NOTE]
>
>L’en-tête `Surrogate-Key` que vous définissez sur la *réponse sortante* de votre fonction Edge au navigateur contrôle le **cache CDN externe**, et non ce cache interne. Les clés de substitution du cache interne proviennent de l’en-tête de réponse `Surrogate-Key` du serveur principal ou des clés que vous attribuez lors de l’écriture dans l’API Core Cache.

### Mise en cache des réponses du serveur principal {#cache-override}

Pour mettre en cache les réponses du serveur principal pendant une durée spécifique :

```js
import { CacheOverride } from "fastly:cache-override";

const response = await fetch(request, {
  backend: "my-origin",
  cacheOverride: new CacheOverride({ ttl: 300 })
});
```

### Contournement du cache {#cache-pass}

Pour contourner entièrement le cache de récupération et toujours effectuer une récupération à partir du serveur principal, utilisez le mode `pass` :

```js
import { CacheOverride } from "fastly:cache-override";

const response = await fetch(request, {
  backend: "my-origin",
  cacheOverride: new CacheOverride({ mode: "pass" })
});
```

## Purge du cache {#cache-purging}

Lorsque le contenu mis en cache devient obsolète, vous devez le purger explicitement. Comme les deux caches fonctionnent indépendamment, il est important de comprendre quel calque vous invalidez et comment ils interagissent.

### Coordination Des Purges Sur Les Deux Calques {#coordinating-purges}

Comme la fonction Edge se trouve derrière le réseau CDN en tant que serveur principal (accessible via [sélecteurs d’origine](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors)), la purge d’une couche de cache sans l’autre peut produire des résultats inattendus :

1. **La purge uniquement du cache du réseau CDN** entraîne l’appel de la fonction Edge par la requête suivante. Si le cache de récupération de la fonction Edge contient toujours des données obsolètes, il renvoie l’ancien contenu, que le réseau CDN met à nouveau en cache.
2. **La purge uniquement du cache de fonction Edge** efface l’état interne, mais le réseau CDN continue à servir sa copie précédemment mise en cache jusqu’à ce qu’elle expire ou soit purgée séparément.

**Bonne pratique :** lorsque les données sous-jacentes sont modifiées, purgez **les deux** les caches : utilisez l’API de purge du cache CDN pour la couche externe et `purge-cache` (ou `purgeSurrogateKey()`) pour la couche interne de fonction Edge. L’utilisation de clés de substitution cohérentes sur les deux couches simplifie l’invalidation coordonnée. Pour un exemple complet de ce modèle, reportez-vous à la section [Modèle des fonctions AEM Edge — Purge](https://github.com/adobe/aem-edge-functions-boilerplate/blob/main/README.md#purging-the-edge-function-fetch-cache).

### Purge du cache du réseau CDN {#purge-cdn-cache}

Pour purger le cache CDN externe (la réponse de la fonction Edge mise en cache au niveau de la couche CDN), utilisez l’[API de purge du cache CDN](/help/implementing/dispatcher/cdn-cache-purge.md). Il s’agit du même mécanisme de purge utilisé pour tout le contenu AEM Cloud Service mis en cache sur le réseau CDN — voir [Comment purger le cache CDN](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/caching/how-to/purge-cache) pour des conseils détaillés.

Dans l’architecture AEM as a Cloud Service, les fonctions Edge reçoivent le trafic du réseau CDN via des [sélecteurs d’origine](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) (voir également [Routage CDN](/help/implementing/developing/introduction/edge-functions.md#cdn-routing)). Le flux de requête complet est :

```
Client → AEM CDN (VCL) → Origin Selector → Edge Function → Backend
```

Le réseau CDN met en cache la réponse finale renvoyée par la fonction Edge. Une purge du réseau CDN efface **uniquement** cette réponse mise en cache externe ; elle n’a aucun effet sur les caches internes de la fonction Edge.

### Purge du cache de récupération des fonctions Edge {#purge-fetch-cache}

La commande de l’interface de ligne de commande `purge-cache` purge le cache de récupération de la fonction Edge **&#x200B;**&#x200B;(les réponses du serveur principal mises en cache dans la fonction Edge). Il ne purge **pas** cache du réseau CDN externe. Pour connaître les options et les indicateurs de l’interface de ligne de commande complète, consultez la référence des commandes [&#128279;](https://github.com/adobe/aio-cli-plugin-aem-edge-functions/blob/main/README.md#purge-cache).`purge-cache`

#### D’Où Proviennent Les Clés De Substitution {#surrogate-key-origin}

Les clés de substitution utilisées dans les commandes de purge doivent correspondre aux clés **balisées sur le contenu mis en cache au moment de son stockage**. Il s’agit du même concept que la [purge par clé de substitution](/help/implementing/dispatcher/cdn-cache-purge.md#surrogate-key-purge) utilisée dans le réseau CDN d’AEM, mais appliquée au cache interne de la fonction Edge. Ces clés proviennent de :

- En-tête de réponse `Surrogate-Key` que le serveur principal renvoie lorsque la fonction Edge récupère à partir de celui-ci.
- Les clés que vous attribuez par programmation lors de l’écriture dans l’[API Core Cache](https://js-compute-reference-docs.edgecompute.app/docs/fastly:cache/CoreCache) (par exemple, via l’option `surrogateKeys` lors de l’insertion d’une entrée de cache).

Par exemple, si votre serveur principal répond avec :

```
HTTP/1.1 200 OK
Content-Type: text/html
Surrogate-Key: page-about product-456 category-shoes
Cache-Control: public, max-age=3600
```

Ensuite, la réponse mise en cache est balisée avec trois clés de substitution : `page-about`, `product-456` et `category-shoes`. Vous pouvez ensuite le purger à l’aide de l’une de ces clés :

```bash
# Purge all cached content tagged with "product-456"
aio aem edge-functions purge-cache <function-name> --surrogateKey product-456

# Purge multiple keys at once
aio aem edge-functions purge-cache <function-name> -k page-about -k category-shoes
```

>[!TIP]
>
>Choisissez des conventions de dénomination de clés de substitution qui correspondent à votre modèle de contenu, par exemple, par chemin de page (`page-about`), ID de contenu (`product-456`) ou type de contenu (`category-shoes`). Cela rend l’invalidation du cache ciblée intuitive lorsque le contenu change.

#### Tout purger {#purge-all}

```bash
# Purge all cached content (use with caution)
aio aem edge-functions purge-cache <function-name> --all
```

#### Purge soft {#soft-purge}

Utilisez l’indicateur `--soft` pour effectuer une purge réversible, qui conserve les entrées obsolètes dans le cache et réduit la charge du serveur principal tout en activant la revalidation obsolète :

```bash
aio aem edge-functions purge-cache <function-name> --surrogateKey product-456 --soft
```

#### Purge programmatique {#programmatic-purge}

Vous pouvez également purger les clés de substitution par programmation à partir de votre code de fonction Edge à l’aide de [`purgeSurrogateKey`](https://js-compute-reference-docs.edgecompute.app/docs/fastly:compute/purgeSurrogateKey) :

```js
import { purgeSurrogateKey } from "fastly:compute";

// Hard purge (immediate removal)
purgeSurrogateKey("product-456");

// Soft purge (retain stale entries for revalidation)
purgeSurrogateKey("product-456", true);
```

>[!CAUTION]
>
>La purge de tout le contenu mis en cache augmente le trafic vers les serveurs principaux. Utilisez l’indicateur `--all` avec précaution et préférez les purges de clé de substitution ciblées dans la mesure du possible.