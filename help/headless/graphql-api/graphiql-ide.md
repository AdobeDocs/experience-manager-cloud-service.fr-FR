---
title: Utilisation de l’IDE GraphiQL dans AEM
description: Découvrez comment utiliser l’IDE GraphiQL dans Adobe Experience Manager.
feature: Content Fragments,GraphQL API
exl-id: be2ebd1b-e492-4d77-b6ef-ffdea9a9c775
source-git-commit: a2e36e296749c79040c9687bbd88288d8977086d
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 2%

---

# Utilisation de l’IDE GraphiQL {#graphiql-ide}

Une mise en oeuvre de la norme [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE est disponible pour une utilisation avec l’API GraphQL d’Adobe Experience Manager (AEM) as a Cloud Service.

>[!NOTE]
>
>Certaines fonctionnalités de cette fonctionnalité sont disponibles dans le canal de version préliminaire. En particulier, les fonctionnalités liées aux requêtes persistantes.
> 
>Voir [Documentation sur les canaux de version préliminaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#enable-prerelease) pour plus d’informations sur l’activation de la fonctionnalité dans votre environnement.

>[!NOTE]
>
>GraphiQL est inclus dans AEM, mais il est activé par défaut uniquement sur la variable `dev-authors` des environnements.

>[!NOTE]
>Vous devez avoir [configuration de vos points de fin](/help/headless/graphql-api/graphql-endpoint.md) dans le [navigateur de configuration](/help/assets/content-fragments/content-fragments-configuration-browser.md) avant d’utiliser l’IDE GraphiQL.


Le **GraphiQL** vous permet de tester et de déboguer vos requêtes GraphQL en vous permettant de :
* sélectionnez la variable **Point d’entrée** approprié à la configuration Sites que vous souhaitez utiliser pour vos requêtes ;
* saisie directe de nouvelles requêtes
* créer et accéder à **[Requêtes persistantes](/help/headless/graphql-api/persisted-queries.md)**
* Exécutez vos requêtes pour afficher immédiatement les résultats.
* gérer **Variables de requête**
* enregistrement et gestion **Requêtes persistantes**
* publier ou annuler la publication, **Requêtes persistantes** (vers/depuis) `dev-publish`)
* voir la **Histoire** de vos requêtes précédentes
* utilisez la méthode **Explorateur de documentation** pour accéder à la documentation ; vous aide à apprendre et à comprendre les méthodes disponibles.

Par exemple :

* `http://localhost:4502/aem/graphiql.html`

![Interface GraphiQL](assets/cfm-graphiql-interface.png "Interface GraphiQL")

Vous pouvez utiliser GraphiQL sur votre système de création de développement afin qu’il puisse être demandé par votre application cliente à l’aide de requêtes de GET et de requêtes de publication. Pour l’utilisation de la production, vous devez [déplacer vos requêtes vers votre environnement de production ;](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production). Commencez par créer l’auteur de production pour valider le contenu nouvellement créé avec les requêtes, puis publiez la production pour la consommation en direct.

## Sélection de votre point de terminaison {#selecting-endpoint}

Pour commencer, vous devez sélectionner la variable **[Point d’entrée](/help/headless/graphql-api/graphql-endpoint.md)** que vous souhaitez utiliser pour les requêtes. Le point de terminaison est adapté à la configuration Sites que vous souhaitez utiliser pour vos requêtes.

Elle est disponible dans la liste déroulante en haut à droite.

## Création et persistance d’une nouvelle requête {#creating-new-query}

Vous pouvez saisir votre nouvelle requête dans l’éditeur, qui se trouve dans le panneau du milieu à gauche, directement sous le logo GraphiQL.

>[!NOTE]
>
>Si une requête persistante est déjà sélectionnée et s’affiche dans le panneau de l’éditeur, sélectionnez `+` (en regard de **Requêtes persistantes**) pour vider l’éditeur prêt pour votre nouvelle requête.

Il suffit de commencer à taper, l&#39;éditeur aussi :

* utilise le survol de la souris pour afficher des informations supplémentaires sur les éléments.
* fournit des fonctionnalités telles que la mise en surbrillance de la syntaxe, la saisie automatique et la suggestion automatique ;

>[!NOTE]
>
>Les requêtes GraphQL commencent généralement par une `{` caractère.
>
>Lignes commençant par un `#` sont ignorées.

Utilisation **Enregistrer sous** pour conserver votre nouvelle requête.

## Mise à jour de la requête conservée {#updating-persisted-query}

Sélectionnez la requête à mettre à jour dans la liste du **Requêtes persistantes** panneau (à l’extrême gauche).

La requête s’affiche dans le panneau de l’éditeur. Apportez les modifications nécessaires, puis utilisez **Enregistrer** pour valider vos mises à jour dans la requête persistante.

## Exécution de requêtes {#running-queries}

Vous pouvez exécuter une nouvelle requête immédiatement ou charger et exécuter une requête persistante. Pour charger une requête persistante, sélectionnez-la dans la liste ; la requête s’affichera dans le panneau de l’éditeur.

Dans les deux cas, la requête affichée dans le panneau de l’éditeur est la requête qui sera exécutée lorsque vous :

* cliquez/appuyez sur le bouton **Exécuter la requête** icon
* utiliser la combinaison clavier ; `Control-Enter`

## Variables de requête {#query-variables}

<!-- more details needed here? -->

L’IDE GraphiQL vous permet également de gérer vos [Variables de requête](/help/headless/graphql-api/content-fragments.md#graphql-variables).

Par exemple :

![Variables GraphQL](assets/cfm-graphqlapi-03.png "Variables GraphQL")

## Publication des requêtes persistantes (recette-publication) {#publishing-persisted-queries}

Une fois que vous avez sélectionné votre requête conservée dans la liste (panneau de gauche), vous pouvez utiliser la variable **Publier** et **Annuler la publication** actions. Cela les active dans votre environnement de publication de développement (`dev-publish`) pour un accès facile à vos applications lors des tests.

>[!NOTE]
>
>Définition du cache de la requête conservée `Time To Live` {&quot;cache-control&quot;:&quot;parameter&quot;:value} a une valeur par défaut de 2 heures (7 200 secondes).

## Mise en cache de vos requêtes persistantes {#caching-persisted-queries}

AEM invalide le cache du réseau de diffusion de contenu (CDN) en fonction d’une durée de vie par défaut (TTL).

Cette valeur est définie sur :

* 7 200 secondes est la durée de vie par défaut du Dispatcher et du réseau de diffusion de contenu ; également connu sous le nom *caches partagés*
   * default : s-maxage=7200
* 60 est la durée de vie par défaut du client (par exemple, un navigateur).
   * default : maxage=60

AEM les requêtes GraphQL qui ont été conservées dans l’interface utilisateur GraphiQL utiliseront le TTL par défaut lors de l’exécution. Si vous souhaitez modifier la durée de vie de votre requête GraphLQ, la requête doit être conservée à la place à l’aide de la méthode API . Cela implique de publier la requête sur AEM à l’aide de CURL dans votre interface de ligne de commande.

Par exemple :

```xml
curl -X PUT \
    -H 'authorization: Basic YWRtaW46YWRtaW4=' \
    -H "Content-Type: application/json" \
    "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
    -d \
'{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
```

Le `cache-control` peut être défini au moment de la création (PUT) ou ultérieurement (par exemple, via une demande de POST). Le contrôle du cache est facultatif lors de la création de la requête conservée, car AEM peut fournir la valeur par défaut. Voir [Comment conserver une requête GraphQL](/help/headless/graphql-api/persisted-queries.md#how-to-persist-query), par exemple pour conserver une requête à l’aide de curl.

## Copier l’URL pour accéder directement à la requête {#copy-url}

Le **Copier l’URL** permet de simuler une requête en copiant l’URL utilisée pour accéder directement à la requête conservée et consulter les résultats. Il peut ensuite être utilisé à des fins de test ; par exemple, en accédant à dans un navigateur :

<!--
  >[!NOTE]
  >
  >The URL will need [encoding before using programmatically](/help/headless/graphql-api/persisted-queries.md#encoding-query-url).
  >
  >The target environment might need adjusting, depending on your requirements.
-->

Par exemple :

`http://localhost:4502/graphql/execute.json/global/article-list-01`

En utilisant cette URL dans un navigateur, vous pouvez confirmer les résultats :

![GraphiQL - Copier l’URL](assets/cfm-graphiql-copy-url.png "GraphiQL - Copier l’URL")

Le **Copier l’URL** est accessible à partir des trois points verticaux situés à droite du nom de la requête conservée (panneau à l’extrême gauche) :

![GraphiQL - Copier l’URL](assets/cfm-graphiql-persisted-query-options.png "GraphiQL - Copier l’URL")

## Suppression de requêtes persistantes {#deleting-persisted-queries}

Le **Supprimer** est également accessible à partir des trois points verticaux situés à droite du nom de la requête conservée (panneau à l’extrême gauche).

<!-- what happens if you try to delete something that is still published? -->


## Installation de la requête persistante en production {#installing-persisted-query-production}

Après avoir développé et testé votre requête persistante avec GraphiQL, l’objectif final est de [le transférer vers votre environnement de production ;](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production) à utiliser par vos applications.

## Raccourcis clavier {#keyboard-shortcuts}

Plusieurs raccourcis clavier permettent d’accéder directement aux icônes d’action dans l’IDE :

* Confirmer la requête :  `Shift-Control-P`
* Merge Query :  `Shift-Control-M`
* Exécuter la requête :  `Control-Enter`
* Remplissage automatique :  `Control-Space`

>[!NOTE]
>
>Sur certains claviers, la fonction `Control` la clé est étiquetée comme `Ctrl`.
