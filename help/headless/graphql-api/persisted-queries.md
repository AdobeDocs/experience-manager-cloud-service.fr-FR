---
title: Requêtes GraphQL persistantes
description: Découvrez comment conserver les requêtes GraphQL dans Adobe Experience Manager as a Cloud Service pour optimiser les performances. Les requêtes persistantes peuvent être demandées par les applications clientes à l’aide de la méthode GET HTTP et la réponse peut être mise en cache aux couches Dispatcher et CDN, ce qui améliore finalement les performances des applications clientes.
feature: Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
source-git-commit: 368c2d537d740b2126aa7cce657ca54f7ad6b329
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 53%

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

* l’IDE GraphiQL - voir [Enregistrement des requêtes persistantes](/help/headless/graphql-api/graphiql-ide.md##saving-persisted-queries)
* curl - voir l’exemple suivant
* Autres outils, notamment [Postman](https://www.postman.com/)

Vous trouverez ci-dessous la procédure à suivre pour conserver une requête donnée à l’aide de l’outil de ligne de commande **curl** :

1. Préparez la requête avec une commande PUT sur l’URL du nouveau point d’entrée `/graphql/persist.json/<config>/<persisted-label>`.

   Par exemple, créez une requête persistante :

   ```xml
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

   ```xml
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

   ```xml
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Mettez à jour une requête persistante avec une commande POST vers un chemin de requête existant.

   Par exemple, utilisez la requête persistante :

   ```xml
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

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Créez une requête ordinaire encapsulée avec le contrôle de cache.

   Par exemple :

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. Créez une requête persistante avec des paramètres :

   Par exemple :

   ```xml
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

1. Exécution d’une requête avec des paramètres.

   Par exemple :

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   
   $ curl -X GET \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   ```

## Transfert d’une requête persistante vers votre environnement de production  {#transfer-persisted-query-production}

En fin de compte, votre requête persistante doit se trouver dans votre environnement de publication de production (d’AEM as a Cloud Service), où elle peut être demandée par les applications clientes. Pour utiliser une requête persistante sur votre environnement de publication de production, l’arborescence persistante associée doit être répliquée :

* à l’auteur de production pour la validation du contenu nouvellement créé avec les requêtes,
* enfin, publier la production pour la consommation réelle

Il existe plusieurs méthodes pour transférer votre requête conservée :

1. Utilisation d’un module :
   1. Créez une définition de module.
   1. Incluez la configuration (par exemple, `/conf/wknd/settings/graphql/persistentQueries`).
   1. Créez le module.
   1. Transférez le package (téléchargez/téléchargez ou répliquez).
   1. Installez le package.

1. Utilisation d’un POST pour la réplication :

   ```xml
   $ curl -X POST   http://localhost:4502/bin/replicate.json \
   -H 'authorization: Basic YWRtaW46YWRtaW4=' \
   -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
   -F cmd=activate
   ```

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->

Une fois la configuration de la requête effectuée dans votre environnement de publication en production, les mêmes principes d’authentification s’appliquent, en utilisant simplement le point de terminaison de publication.

>[!NOTE]
>
>Pour un accès anonyme, le système suppose que l’ACL permet à « tout le monde » d’avoir accès à la configuration de la requête.
>
>Si ce n’est pas le cas, l’exécution sera impossible.

## Encodage de l’URL de requête à utiliser par une application {#encoding-query-url}

Pour une utilisation par une application, tout point-virgule (&quot;;&quot;) doit être codé dans les URL.

Par exemple, comme dans la demande d’exécution d’une requête persistante :

```xml
curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
```

Pour utiliser une requête persistante dans une application cliente, le SDK client AEM sans interface utilisateur doit être utilisé. [AEM client sans affichage pour JavaScript](https://github.com/adobe/aem-headless-client-js).