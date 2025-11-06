---
title: Requêtes GraphQL persistantes
description: Découvrez comment conserver les requêtes GraphQL dans Adobe Experience Manager as a Cloud Service pour optimiser les performances. Les requêtes persistantes peuvent être demandées par les applications clientes à l’aide de la méthode GET HTTP et la réponse peut être mise en cache aux couches Dispatcher et CDN, ce qui améliore finalement les performances des applications clientes.
feature: Headless, Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1952'
ht-degree: 80%

---

# Requêtes GraphQL persistantes {#persisted-graphql-queries}

Les requêtes persistantes sont des requêtes GraphQL qui sont créées et stockées sur le serveur Adobe Experience Manager (AEM) as a Cloud Service. Elles peuvent être demandées avec une requête GET par les applications clientes. La réponse d’une requête GET peut être mise en cache aux couches Dispatcher et CDN, ce qui améliore finalement les performances de l’application cliente qui la demande. Elles sont en cela différentes des requêtes GraphQL standard, qui sont exécutées à l’aide de requêtes POST dans lesquelles la réponse ne peut pas être facilement mise en cache.

>[!NOTE]
>
>Des requêtes persistantes sont recommandées. Voir [Bonnes pratiques de requête GraphQL (Dispatcher)](/help/headless/graphql-api/content-fragments.md#graphql-query-best-practices) pour plus d’informations et la configuration Dispatcher associée.

L’[IDE GraphiQL](/help/headless/graphql-api/graphiql-ide.md) est disponible dans AEM pour que vous puissiez le développer, le tester et conserver vos requêtes GraphQL, avant de [le transférer vers votre environnement de production](#transfer-persisted-query-production). Dans les cas qui nécessitent une personnalisation (par exemple, pour la [personnalisation du cache](/help/headless/graphql-api/graphiql-ide.md#caching-persisted-queries)) vous pouvez utiliser l’API ; consultez l’exemple de cURL fourni dans [Conservation d’une requête GraphQL](#how-to-persist-query).

## Requêtes et points d’entrée persistants {#persisted-queries-and-endpoints}

Les requêtes persistantes doivent toujours utiliser le point d’entrée associé à la [configuration Sites appropriée](graphql-endpoint.md) afin qu’ils puissent utiliser l’une des fonctionnalités ou les deux :

* Configuration globale et point d’entrée
La requête a accès à tous les modèles de fragment de contenu.
* Configuration(s) de sites spécifiques et point(s) d’entrée
La création d’une requête persistante pour une configuration Sites spécifique nécessite un point d’entrée spécifique à la configuration Sites correspondant (pour fournir l’accès aux modèles de fragment de contenu associés).
Par exemple, pour créer une requête persistante spécifique à la configuration WKND Sites, une configuration de sites spécifique à WKND correspondante et un point d’entrée spécifique à WKND doivent être créés à l’avance.

>[!NOTE]
>
>Voir [Activation de la fonctionnalité de fragment de contenu dans le navigateur de configuration](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser) pour plus d’informations.
>
>Les **requêtes persistantes GraphQL** doivent être activées pour la configuration appropriée des sites.

Par exemple, s’il existe une requête spécifique appelée `my-query`, qui utilise un modèle `my-model` de la configuration Sites `my-conf` :

* Vous pouvez créer une requête à l’aide du point d’entrée `my-conf` spécifique, puis la requête est enregistrée comme suit :
  `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* Vous pouvez créer la même requête à l’aide du point d’entrée `global`, mais elle est dans ce cas enregistrée comme suit :
  `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>Il s’agit de deux requêtes différentes, enregistrées sous des chemins différents.
>
>Il se trouve qu’elles utilisent le même modèle – mais via différents points d’entrée.

## Conservation d’une requête GraphQL {#how-to-persist-query}

Il est recommandé d’appliquer des requêtes persistantes dans un environnement de création d’AEM dès le départ, puis de [transférer la requête](#transfer-persisted-query-production) à votre environnement de publication AEM de production, pour être utilisées par les applications.

Il existe différentes méthodes pour créer des requêtes persistantes, notamment :

* IDE GraphiQL - voir [Enregistrement des requêtes persistantes](/help/headless/graphql-api/graphiql-ide.md#saving-persisted-queries) (méthode préférée)
* cURL - Consultez l’exemple suivant
* Autres outils, notamment [Postman](https://www.postman.com/)

L’IDE GraphiQL est la méthode **préférée** pour les requêtes persistantes. Pour conserver une requête donnée à l’aide de l’outil de ligne de commande **cURL** :

1. Préparez la requête avec une commande PUT sur l’URL du nouveau point d’entrée `/graphql/persist.json/<config>/<persisted-label>`.

   Par exemple, créez une requête persistante :

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
       }
     }
   }'
   ```

1. À ce stade, vérifiez la réponse.

   Par exemple, contrôlez le succès :

   ```json
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. Vous pouvez ensuite exécuter à nouveau la requête persistante avec une commande GET sur l’URL `/graphql/execute.json/<shortPath>`.

   Par exemple, utilisez la requête persistante :

   ```shell
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Mettez à jour une requête persistante avec une commande POST vers un chemin de requête existant.

   Par exemple, utilisez la requête persistante :

   ```shell
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
         referencearticle {
           _path
         }
       }
     }
   }'
   ```

1. Créez une requête ordinaire encapsulée.

   Par exemple :

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Créez une requête ordinaire encapsulée avec le contrôle de cache.

   Par exemple :

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. Créez une requête persistante avec des paramètres :

   Par exemple :

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-parameters" \
       -d \
   'query GetAsGraphqlModelTestByPath($apath: String!, $withReference: Boolean = true) {
     articleByPath(_path: $apath) {
       item {
         _path
           author
           main {
           plaintext
           }
           referencearticle @include(if: $withReference) {
           _path
           }
         }
       }
     }'
   ```


## Procédure d’exécution d’une requête persistante {#execute-persisted-query}

Pour exécuter une requête persistante, une application cliente effectue une requête GET en utilisant la syntaxe suivante :

```
GET <AEM_HOST>/graphql/execute.json/<PERSISTENT_PATH>
```

Où `PERSISTENT_PATH` est un chemin raccourci vers l’emplacement d’enregistrement de la requête persistante.

1. Par exemple, `wknd` est le nom de la configuration et `plain-article-query` est le nom de la requête persistante. Pour exécuter la requête :

   ```shell
   $ curl -X GET \
       https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query
   ```

1. Exécuter une requête avec des paramètres.

   >[!NOTE]
   >
   > Les variables et valeurs de requête doivent être correctement [encodées](#encoding-query-url) lors de l’exécution d’une requête persistante.

   Par exemple :

   ```xml
   $ curl -X GET \
       "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query-parameters%3Bapath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fmagazine%2Falaska-adventure%2Falaskan-adventures%3BwithReference%3Dfalse
   ```

   Voir la section Utiliser [les variables de requête](#query-variables) pour plus d’informations.

## Utiliser les variables de requête {#query-variables}

Les variables de requête peuvent être utilisées avec les requêtes persistantes. Les variables de requête sont ajoutées à la requête précédée d’un point-virgule (`;`) à l’aide du nom et de la valeur de la variable. Plusieurs variables sont séparées par des points-virgules.

Le modèle ressemble à ce qui suit :

```
<AEM_HOST>/graphql/execute.json/<PERSISTENT_QUERY_PATH>;variable1=value1;variable2=value2
```

Par exemple, la requête suivante contient une variable `activity` pour filtrer une liste en fonction d’une valeur d’activité.

```graphql
query getAdventuresByActivity($activity: String!) {
      adventureList (filter: {
        adventureActivity: {
          _expressions: [
            {
              value: $activity
            }
          ]
        }
      }){
        items {
          _path
        adventureTitle
        adventurePrice
        adventureTripLength
      }
    }
  }
```

Cette requête peut être conservée sous un chemin `wknd/adventures-by-activity`. Pour appeler la requête persistante où `activity=Camping` la requête ressemblerait à ceci :

```
<AEM_HOST>/graphql/execute.json/wknd/adventures-by-activity%3Bactivity%3DCamping
```

Le `%3B` de codage UTF-8 est pour `;` et `%3D` est le codage pour `=`. Les variables de requête et les caractères spéciaux doivent être [correctement encodés](#encoding-query-url) pour que la requête persistante s’exécute.

### Utilisation des variables de requête - Bonnes pratiques {#query-variables-best-practices}

Lorsque vous utilisez des variables dans vos requêtes, quelques bonnes pratiques doivent être suivies :

* Encodage
En règle générale, il est toujours recommandé de coder tous les caractères spéciaux ; par exemple, `;`, `=`, `?`, `&`, entre autres.

* Point-virgule
Les requêtes persistantes qui utilisent plusieurs variables (séparées par des points-virgules) doivent avoir l’une des caractéristiques suivantes :
   * le codage des points-virgules (`%3B`) ; le codage de l’URL effectuera également cette opération
   * ou un point-virgule de fin ajouté à la fin de la requête

* `CACHE_GRAPHQL_PERSISTED_QUERIES`
Lorsque `CACHE_GRAPHQL_PERSISTED_QUERIES` est activé pour le Dispatcher, les paramètres qui contiennent les caractères `/` ou `\` dans leur valeur sont codés deux fois au niveau du Dispatcher.
Pour éviter cette situation :

   * Activez `DispatcherNoCanonURL` sur le Dispatcher.
Cette instruction indique au Dispatcher de transférer l’URL d’origine vers AEM, afin d’éviter les codages dupliqués.
Cependant, ce paramètre ne fonctionne actuellement qu’au niveau des `vhost`. Par conséquent, si vous disposez déjà de configurations Dispatcher pour réécrire les URL (par exemple, lors de l’utilisation d’URL raccourcies), vous aurez peut-être besoin d’une `vhost` distincte pour les URL de requête persistante.

   * Envoyez `/` ou `\` caractères non codés.

     Lors de l’appel de l’URL de la requête persistante , assurez-vous que tous les caractères `/` ou `\` ne sont pas codés dans la valeur des variables de la requête persistante.

     >[!NOTE]
     >
     >Cette option n’est recommandée que lorsque la solution `DispatcherNoCanonURL` ne peut pas être mise en œuvre, quelle que soit la raison.

* `CACHE_GRAPHQL_PERSISTED_QUERIES`

  Lorsque `CACHE_GRAPHQL_PERSISTED_QUERIES` est activé pour le Dispatcher, le caractère `;` ne peut pas être utilisé dans la valeur d’une variable.

## Mettre en cache vos requêtes persistantes {#caching-persisted-queries}

Les requêtes persistantes sont recommandées, car elles peuvent être mises en cache au niveau des couches [Dispatcher](/help/headless/deployment/dispatcher.md) et réseau de diffusion de contenu (CDN), ce qui améliore les performances de l’application cliente effectuant les requêtes.

Par défaut, AEM invalide le cache en fonction d’une définition de durée de vie (TTL). Ces TTL peuvent être définies par les paramètres suivants. Ces paramètres sont accessibles de plusieurs manières, avec des variantes dans les noms en fonction du mécanisme utilisé :

| Type de cache | [En-tête HTTP](https://developer.mozilla.org/fr-FR/docs/Web/HTTP/Headers/Cache-Control) | cURL | Configuration OSGi  | Cloud Manager |
|--- |--- |--- |--- |--- |
| Navigateur | `max-age` | `cache-control : max-age` | `cacheControlMaxAge` | `graphqlCacheControl` |
| Réseau de diffusion de contenu | `s-maxage` | `surrogate-control : max-age` | `surrogateControlMaxAge` | `graphqlSurrogateControl` | 60 |
| Réseau de diffusion de contenu | `stale-while-revalidate` | `surrogate-control : stale-while-revalidate ` | `surrogateControlStaleWhileRevalidate` | `graphqlStaleWhileRevalidate` |
| Réseau de diffusion de contenu | `stale-if-error` | `surrogate-control : stale-if-error` | `surrogateControlStaleIfError` | `graphqlStaleIfError` |

{style="table-layout:auto"}

### Instances de création {#author-instances}

Pour les instances de création, les valeurs par défaut sont les suivantes :

* `max-age` : 60
* `s-maxage` : 60
* `stale-while-revalidate` : 86400
* `stale-if-error` : 86400

Celles-ci :

* ne peuvent pas être remplacées :
   * par une configuration OSGi
* peuvent être remplacées :
   * par une requête qui définit les paramètres d’en-tête HTTP à l’aide de cURL ; elle doit inclure des paramètres appropriés pour `cache-control` et/ou `surrogate-control` ; pour consulter des exemples, voir [Gestion du cache au niveau de la requête persistante](#cache-persisted-query-level).
   * si vous spécifiez des valeurs dans la boîte de dialogue **En-têtes** de l’[IDE GraphiQL](#http-cache-headers-graphiql-ide).

### Instances de publication {#publish-instances}

Pour les instances de publication, les valeurs par défaut sont les suivantes :

* `max-age` : 60
* `s-maxage` : 7200
* `stale-while-revalidate` : 86400
* `stale-if-error` : 86400

Elles peuvent être remplacées :

* [à partir de l’IDE GraphQL](#http-cache-headers-graphiql-ide)

* [au niveau de la requête persistante](#cache-persisted-query-level) ; cela implique de publier la requête sur AEM à l’aide de cURL dans votre interface de ligne de commande et de publier la requête persistante.

* [par les variables Cloud Manager](#cache-cloud-manager-variables)

* [par une configuration OSGi](#cache-osgi-configration)

### Gestion des en-têtes de cache HTTP dans l’IDE GraphiQL {#http-cache-headers-graphiql-ide}

L’IDE GraphiQL - Consultez [Enregistrement de requêtes persistantes](/help/headless/graphql-api/graphiql-ide.md#managing-cache)

### Gestion du cache au niveau de la requête persistante {#cache-persisted-query-level}

Cela implique de publier la requête dans AEM à l’aide de cURL dans votre interface de ligne de commande.

Pour un exemple de la méthode PUT (création) :

```bash
curl -u admin:admin -X PUT \
--url "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
--header "Content-Type: application/json" \
--data '{ "query": "{articleList { items { _path author } } }", "cache-control": { "max-age": 300 }, "surrogate-control": {"max-age":600, "stale-while-revalidate":1000, "stale-if-error":1000} }'
```

Pour un exemple de la méthode POST (mise à jour) :

```bash
curl -u admin:admin -X POST \
--url "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
--header "Content-Type: application/json" \
--data '{ "query": "{articleList { items { _path author } } }", "cache-control": { "max-age": 300 }, "surrogate-control": {"max-age":600, "stale-while-revalidate":1000, "stale-if-error":1000} }'
```

Le `cache-control` peut être défini au moment de la création (PUT) ou ultérieurement (par exemple, via une demande de POST). Le contrôle du cache est facultatif lors de la création de la requête persistante car AEM peut fournir la valeur par défaut. Consultez [Conservation d’une requête GraphQL](#how-to-persist-query), par exemple pour conserver une requête à l’aide de cURL.

### Gestion du cache avec les variables Cloud Manager {#cache-cloud-manager-variables}

[Les variables d’environnement Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) peuvent être définies avec Cloud Manager pour définir les valeurs requises :

| Nom | Valeur | Service appliqué | Type |
|--- |--- |--- |--- |
| `graphqlStaleIfError` | 86400 | *En fonction des besoins* | *En fonction des besoins* |
| `graphqlSurrogateControl` | 600 | *En fonction des besoins* | *En fonction des besoins* |

{style="table-layout:auto"}

### Gestion du cache avec une configuration OSGi {#cache-osgi-configration}

Pour gérer le cache globalement, vous pouvez [configurer les paramètres OSGi](/help/implementing/deploying/configuring-osgi.md) pour la **Configuration du service de requête persistante**.

>[!NOTE]
>
>Pour le contrôle du cache, la configuration OSGi n’est appropriée que pour les instances de publication. La configuration existe sur les instances de création, mais elle est ignorée.

>[!NOTE]
>
>La **configuration du service de requête persistante** est également utilisée pour [configurer le code de réponse à la requête](#configuring-query-response-code).

Configuration OSGi par défaut pour les instances de publication :

* lit les variables Cloud Manager si elles sont disponibles :

  | Propriétés de configuration OSGi | lit ceci | Variable Cloud Manager |
  |--- |--- |--- |
  | `cacheControlMaxAge` | lit | `graphqlCacheControl` |
  | `surrogateControlMaxAge` | lit | `graphqlSurrogateControl` |
  | `surrogateControlStaleWhileRevalidate` | lit | `graphqlStaleWhileRevalidate` |
  | `surrogateControlStaleIfError` | lit | `graphqlStaleIfError` |

  {style="table-layout:auto"}

* et, si elle n’est pas disponible, la configuration OSGi utilise les [valeurs par défaut des instances de publication](#publish-instances).

## Configurer le code de réponse à la requête {#configuring-query-response-code}

Par défaut, le `PersistedQueryServlet` envoie une réponse `200` lors de l’exécution d’une requête, quel que soit le résultat réel.

Vous pouvez [configurer les paramètres OSGi](/help/implementing/deploying/configuring-osgi.md) pour la **Configuration du service de requête persistante** afin de contrôler si des codes d’état plus détaillés sont renvoyés par le point d’entrée `/execute.json/persisted-query`, en cas d’erreur dans la requête persistante.

>[!NOTE]
>
>La **configuration du service de requête persistante** est également utilisée pour la [gestion du cache](#cache-osgi-configration).

Le champ `Respond with application/graphql-response+json` (`responseContentTypeGraphQLResponseJson`) peut être défini selon les besoins :

* `false` (valeur par défaut) :
peu importe que la requête persistante soit réussie ou non. L’en-tête `Content-Type` renvoyé est `application/json` et le code d’état `/execute.json/persisted-query` *always* renvoie `200`.

* `true` :
Le `Content-Type` renvoyé est `application/graphql-response+json` et le point d’entrée renvoie le code de réponse approprié en cas d’erreur lors de l’exécution de la requête persistante :

  | Code | Description |
  |--- |--- |
  | 200 | Réponse réussie |
  | 400 | Indique qu’il manque des en-têtes ou qu’il y a un problème avec le chemin d’accès à la requête persistante. Par exemple, nom de configuration non spécifié, suffixe non spécifié et autres.<br>Voir [Dépannage - Point d’entrée GraphQL non configuré](/help/headless/graphql-api/persisted-queries-troubleshoot.md#missing-path-query-url). |
  | 404 | La ressource demandée est introuvable. Par exemple, le point d’entrée Graphql n’est pas disponible sur le serveur.<br>Voir [Dépannage - Chemin manquant dans l’URL de la requête persistante GraphQL](/help/headless/graphql-api/persisted-queries-troubleshoot.md#graphql-endpoint-not-configured). |
  | 500 | Erreur interne du serveur. Par exemple, les erreurs de validation, l’erreur de persistance, etc. |

  >[!NOTE]
  >
  >Voir aussi https://graphql.github.io/graphql-over-http/draft/#sec-Status-Codes

## Encoder l’URL de requête devant être utilisé par une application {#encoding-query-url}

Pour une utilisation par une application, tout caractère spécial utilisé lors de la création de variables de requête (c’est-à-dire les points-virgules (`;`), le signe égal (`=`), les barres obliques `/`) doit être converti pour utiliser le codage UTF-8 correspondant.

Par exemple :

```xml
curl -X GET \ "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/adventure-by-path%3BadventurePath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fadventures%2Fbali-surf-camp%2Fbali-surf-camp"
```

L’URL peut être divisée en plusieurs parties :

| Partie de l’URL | Description |
|----------| -------------|
| `/graphql/execute.json` | Point d’entrée de requête persistante |
| `/wknd/adventure-by-path` | Chemin de requête persistante |
| `%3B` | Encodage de `;` |
| `adventurePath` | Variable de requête |
| `%3D` | Encodage de `=` |
| `%2F` | Encodage de `/` |
| `%2Fcontent%2Fdam...` | Chemin codé vers le fragment de contenu |

En texte brut, l’URI de requête ressemble à ce qui suit :

```plaintext
/graphql/execute.json/wknd/adventure-by-path;adventurePath=/content/dam/wknd/en/adventures/bali-surf-camp/bali-surf-camp
```

Pour utiliser une requête persistante dans une application cliente, le SDK client AEM Headless doit être utilisé pour [JavaScript](https://github.com/adobe/aem-headless-client-js), [Java](https://github.com/adobe/aem-headless-client-java) ou [NodeJS](https://github.com/adobe/aem-headless-client-nodejs). Le SDK client Headless codera automatiquement toutes les variables de requête correctement dans la requête concernée.

## Transférer une requête persistante vers votre environnement de production  {#transfer-persisted-query-production}

Les requêtes persistantes doivent toujours être créées sur un service de création AEM, puis publiées (répliquées) sur un service de publication AEM. Souvent, les requêtes persistantes sont créées et testées dans des environnements inférieurs tels que les environnements locaux ou de développement. Il est alors nécessaire de promouvoir les requêtes persistantes dans des environnements de niveau supérieur, ce qui rend ces requêtes disponibles dans un environnement de publication AEM de production pour que les applications clientes puissent les utiliser.

### Requêtes persistantes de package

Les requêtes persistantes peuvent être intégrées aux [packages AEM](/help/implementing/developing/tools/package-manager.md). Les packages AEM peuvent ensuite être téléchargés et installés dans différents environnements. Les packages AEM peuvent également être répliqués d’un environnement de création AEM vers des environnements de publication AEM.

Création d’un package :

1. Accédez à **Outils** > **Déploiement** > **Packages**.
1. Créez un nouveau package en appuyant sur **Créer un package**. Une boîte de dialogue s’ouvre alors pour définir le package.
1. Dans la boîte de dialogue Définition de package, sous **Général**, saisissez un **Nom** comme « wknd-persistent-queries ».
1. Saisissez un numéro de version comme « 1.0 ».
1. Sous **Filtres** ajoutez un nouveau **Filtre**. Utilisez l’outil de recherche de chemin pour sélectionner le dossier `persistentQueries` sous la configuration. Par exemple, pour la configuration `wknd`, le chemin d’accès complet sera `/conf/wknd/settings/graphql/persistentQueries`.
1. Sélectionnez **Enregistrer** pour enregistrer la nouvelle définition de package et fermez la boîte de dialogue.
1. Sélectionnez le bouton **Créer** dans la définition de package créée.

Une fois le package créé, vous pouvez :

* **Télécharger** le package et effectuer un nouveau chargement sur un autre environnement.
* **Répliquer** le package en appuyant sur **Plus** > **Répliquer**. Cela répliquera le package dans l’environnement de publication AEM connecté.

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->
