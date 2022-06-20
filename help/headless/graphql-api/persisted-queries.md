---
title: Requêtes GraphQL persistantes
description: Découvrez comment conserver les requêtes GraphQL dans Adobe Experience Manager as a Cloud Service pour optimiser les performances. Les requêtes persistantes peuvent être demandées par les applications clientes à l’aide de la méthode GET HTTP et la réponse peut être mise en cache aux couches Dispatcher et CDN, ce qui améliore finalement les performances des applications clientes.
feature: Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
source-git-commit: 8a9cdc451a5da09cef331ec0eaadd5d3a68b1985
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 30%

---

# Requêtes GraphQL persistantes {#persisted-queries-caching}

Les requêtes persistantes sont des requêtes GraphQL qui sont créées et stockées sur le serveur as a Cloud Service Adobe Experience Manager (AEM). Ils peuvent être demandés avec une demande de GET par les applications clientes. La réponse d’une requête GET peut être mise en cache aux couches Dispatcher et CDN, ce qui améliore finalement les performances de l’application cliente qui la demande. Cela diffère des requêtes GraphQL standard, qui sont exécutées à l’aide de requêtes de POST dans lesquelles la réponse ne peut pas être facilement mise en cache.

>[!NOTE]
>
>Les requêtes persistantes sont recommandées. Voir [Bonnes pratiques de requête GraphQL (Dispatcher)](/help/headless/graphql-api/content-fragments.md#graphql-query-best-practices) pour plus d’informations et la configuration Dispatcher associée.

Le [IDE GraphiQL](/help/headless/graphql-api/graphiql-ide.md) est disponible dans AEM pour que vous puissiez développer, tester et conserver vos requêtes GraphQL, avant [transfert vers votre environnement de production](#transfer-persisted-query-production). Dans les cas qui nécessitent une personnalisation (par exemple, lorsque [personnalisation du cache](/help/headless/graphql-api/graphiql-ide.md#caching-persisted-queries)) vous pouvez utiliser l’API ; voir l’exemple de curl fourni dans [Comment conserver une requête GraphQL](#how-to-persist-query).

## Requêtes et points de fin persistants {#persisted-queries-and-endpoints}

Les requêtes persistantes doivent toujours utiliser le point d’entrée associé à la [configuration Sites appropriée](graphql-endpoint.md) afin qu’ils puissent utiliser l’une des fonctionnalités ou les deux :

* Configuration globale et point d’entrée
La requête a accès à tous les modèles de fragment de contenu.
* Configuration(s) de sites spécifiques et point(s) d’entrée
La création d’une requête persistante pour une configuration Sites spécifique nécessite un point d’entrée spécifique à la configuration Sites correspondant (pour fournir l’accès aux modèles de fragment de contenu associés).
Par exemple, pour créer une requête persistante spécifique à la configuration WKND Sites, une configuration de sites spécifique à WKND correspondante et un point d’entrée spécifique à WKND doivent être créés à l’avance.

>[!NOTE]
>
>Voir [Activation de la fonctionnalité de fragment de contenu dans le navigateur de configuration](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) pour plus d’informations.
>
>Le **Requêtes persistantes GraphQL** doivent être activés pour la configuration Sites appropriée.

Par exemple, s’il existe une requête spécifique appelée `my-query`, qui utilise un modèle `my-model` de la configuration Sites `my-conf` :

* Vous pouvez créer une requête à l’aide du point d’entrée `my-conf` spécifique, puis la requête sera enregistrée comme suit :
   `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* Vous pouvez créer la même requête à l’aide du point d’entrée `global`, mais elle sera dans ce cas enregistrée comme suit :
   `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>Il s’agit de deux requêtes différentes, enregistrées sous des chemins différents.
>
>Il se trouve qu’elles utilisent le même modèle – mais via différents points d’entrée.

## Conservation d’une requête GraphQL {#how-to-persist-query}

Il est recommandé de conserver les requêtes dans un environnement de création d’AEM au départ, puis [transférer la requête](#transfer-persisted-query-production) à votre environnement de production AEM publication, pour une utilisation par les applications.

Il existe différentes méthodes de requête persistante, notamment :

* IDE GraphiQL - voir [Enregistrement des requêtes persistantes](/help/headless/graphql-api/graphiql-ide.md##saving-persisted-queries) (méthode préférée)
* curl - voir l’exemple suivant
* Autres outils, notamment [Postman](https://www.postman.com/)

L’IDE GraphiQL est l’IDE **preferred** pour les requêtes persistantes. Pour conserver une requête donnée à l’aide de la fonction **curl** outil de ligne de commande :

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


## Exécution d’une requête persistante {#execute-persisted-query}

Pour exécuter une requête persistante, une application client effectue une requête GET en utilisant la syntaxe suivante :

```
GET <AEM_HOST>/graphql/execute.json/<PERSISTENT_PATH>
```

Où `PERSISTENT_PATH` est un chemin raccourci vers l’emplacement d’enregistrement de la requête persistante.

1. Par exemple `wknd` est le nom de la configuration et `plain-article-query` est le nom de la requête persistante. Pour exécuter la requête :

   ```shell
   $ curl -X GET \
       https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query
   ```

1. Exécution d’une requête avec des paramètres.

   >[!NOTE]
   >
   > Les variables et valeurs de requête doivent être correctement [encoded](#encoding-query-url) lors de l’exécution d’une requête persistante.

   Par exemple :

   ```xml
   $ curl -X GET \
       "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query-parameters%3Bapath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fmagazine%2Falaska-adventure%2Falaskan-adventures%3BwithReference%3Dfalse
   ```

   Voir Utilisation [variables de requête](#query-variables) pour plus d’informations.

## Utilisation de variables de requête {#query-variables}

Les variables de requête peuvent être utilisées avec les requêtes persistantes. Les variables de requête sont ajoutées à la requête précédée d’un point-virgule (`;`) à l’aide du nom et de la valeur de la variable. Plusieurs variables sont séparées par des points-virgules.

Le modèle ressemble à ce qui suit :

```
<AEM_HOST>/graphql/execute.json/<PERSISTENT_QUERY_PATH>;variable1=value1;variable2=value2
```

Par exemple, la requête suivante contient une variable . `activity` pour filtrer une liste en fonction d’une valeur d’activité :

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

Cette requête peut être conservée sous un chemin `wknd/adventures-by-activity`. Pour appeler la requête persistante où `activity=Camping` la requête ressemblerait à ceci :

```
<AEM_HOST>/graphql/execute.json/wknd/adventures-by-activity%3Bactivity%3DCamping
```

Notez que `%3B` est l’encodage UTF-8 pour `;` et `%3D` est l’encodage pour `=`. Les variables de requête et les caractères spéciaux doivent être [correctement encodé](#encoding-query-url) pour que la requête persistante s’exécute.

## Encodage de l’URL de requête à utiliser par une application {#encoding-query-url}

Pour une utilisation par une application, tout caractère spécial utilisé lors de la création de variables de requête (c’est-à-dire des points-virgules (`;`), signe égal (`=`), barres obliques `/`) doit être converti pour utiliser le codage UTF-8 correspondant.

Par exemple :

```xml
curl -X GET \ "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/adventure-by-path%3BadventurePath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fadventures%2Fbali-surf-camp%2Fbali-surf-camp"
```

L’URL peut être divisée en plusieurs parties :

| Partie de l’URL | Description |
|----------| -------------|
| `/graphql/execute.json` | Point d’entrée de requête persistant |
| `/wknd/adventure-by-path` | Chemin de requête persistant |
| `%3B` | Encodage de `;` |
| `adventurePath` | Variable de requête |
| `%3D` | Encodage de `=` |
| `%2F` | Encodage de `/` |
| `%2Fcontent%2Fdam...` | Chemin codé vers le fragment de contenu |

En texte brut, l’URI de requête ressemble à ce qui suit :

```plaintext
/graphql/execute.json/wknd/adventure-by-path;adventurePath=/content/dam/wknd/en/adventures/bali-surf-camp/bali-surf-camp
```

Pour utiliser une requête persistante dans une application cliente, le SDK client AEM sans interface utilisateur doit être utilisé pour [JavaScript](https://github.com/adobe/aem-headless-client-js), [Java](https://github.com/adobe/aem-headless-client-java)ou [NodeJS](https://github.com/adobe/aem-headless-client-nodejs). Le SDK client sans tête codera automatiquement toutes les variables de requête correctement dans la requête.

## Transfert d’une requête persistante vers votre environnement de production  {#transfer-persisted-query-production}

Les requêtes persistantes doivent toujours être créées sur un service AEM Author, puis publiées (répliquées) sur un service AEM Publish. Souvent, les requêtes persistantes sont créées et testées dans des environnements inférieurs tels que les environnements locaux ou de développement. Il est ensuite nécessaire de promouvoir les requêtes persistantes dans des environnements de niveau supérieur, ce qui rend ces requêtes disponibles dans un environnement de publication AEM de production pour que les applications clientes puissent les utiliser.

### Requêtes persistantes de package

Les requêtes persistantes peuvent être intégrées à [AEM de modules](/help/implementing/developing/tools/package-manager.md). AEM les packages peuvent ensuite être téléchargés et installés dans différents environnements. Les modules AEM peuvent également être répliqués d’un environnement de création AEM vers des environnements de publication AEM.

Pour créer un module :

1. Accédez à **Outils** > **Déploiement** > **Packages**.
1. Créez un module en appuyant sur **Créer un module**. Une boîte de dialogue s’ouvre alors pour définir le module.
1. Dans la boîte de dialogue Définition de module, sous **Général** saisir une **Nom** comme &quot;wknd-persistent-requêtes&quot;.
1. Saisissez un numéro de version du type &quot;1.0&quot;.
1. Sous **Filtres** ajouter une nouvelle **Filtrer**. Utilisez l’outil de recherche de chemin pour sélectionner la variable `persistentQueries` sous la configuration. Par exemple, pour la variable `wknd` configuration Le chemin complet sera `/conf/wknd/settings/graphql/persistentQueries`.
1. Appuyer **Enregistrer** pour enregistrer la nouvelle définition de module et fermer la boîte de dialogue.
1. Appuyez sur le bouton **Build** dans la définition de package nouvellement créée.

Une fois le module créé, vous pouvez :
* **Télécharger** le package et effectuez un nouveau chargement sur un autre environnement.
* **Répliquer** le module en appuyant sur **Plus** > **Répliquer**. Cela répliquera le module dans l’environnement de publication AEM connecté.

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->
