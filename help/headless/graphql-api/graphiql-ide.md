---
title: Utilisation de l’IDE GraphiQL dans AEM
description: Découvrez comment utiliser l’IDE GraphiQL dans Adobe Experience Manager.
feature: Content Fragments,GraphQL API
exl-id: be2ebd1b-e492-4d77-b6ef-ffdea9a9c775
source-git-commit: 377747d6bbb945b1de9cf1fdcbabc077babd7aa9
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 3%

---

# Utilisation de l’IDE GraphiQL {#graphiql-ide}

Une mise en oeuvre de la norme [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE est disponible pour une utilisation avec l’API GraphQL d’Adobe Experience Manager (AEM) as a Cloud Service.

>[!NOTE]
>
>GraphiQL est inclus dans tous les environnements d’AEM (mais sera accessible/visible uniquement lorsque vous configurez vos points de terminaison).
>
>Dans les versions précédentes, un module était nécessaire pour installer l’IDE GraphiQL. Si vous l’avez installé, il peut maintenant être supprimé.

>[!NOTE]
>Vous devez avoir [configuration de vos points de fin](/help/headless/graphql-api/graphql-endpoint.md) dans le [navigateur de configuration](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md) avant d’utiliser l’IDE GraphiQL.


Le **GraphiQL** vous permet de tester et de déboguer vos requêtes GraphQL en vous permettant de :
* sélectionnez la variable **Point d’entrée** approprié à la configuration Sites que vous souhaitez utiliser pour vos requêtes ;
* saisie directe de nouvelles requêtes
* créer et accéder à **[Requêtes persistantes](/help/headless/graphql-api/persisted-queries.md)**
* Exécutez vos requêtes pour afficher immédiatement les résultats.
* gérer **Variables de requête**
* enregistrement et gestion **Requêtes persistantes**
* publier ou annuler la publication, **Requêtes persistantes** (par exemple, pour/depuis `dev-publish`)
* voir la **Histoire** de vos requêtes précédentes
* utilisez la méthode **Explorateur de documentation** pour accéder à la documentation ; vous aide à apprendre et à comprendre les méthodes disponibles.

Vous pouvez accéder à l’éditeur de requêtes à partir de :

* **Outils** -> **Général** -> **Éditeur de requêtes GraphQL**
* directement; par exemple, `http://localhost:4502/aem/graphiql.html`

![Interface GraphiQL](assets/cfm-graphiql-interface.png "Interface GraphiQL")

Vous pouvez utiliser GraphiQL sur votre système afin que les requêtes puissent être demandées par votre application cliente à l’aide de requêtes GET et pour publier des requêtes. Pour l’utilisation de la production, vous pouvez alors [déplacer vos requêtes vers votre environnement de production ;](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production). Commencez par créer l’auteur de production pour valider le contenu nouvellement créé avec les requêtes, puis publiez la production pour la consommation en direct.

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

## Gestion du cache pour vos requêtes persistantes {#managing-cache}

[Requêtes persistantes](/help/headless/graphql-api/persisted-queries.md) sont recommandés, car ils peuvent être mis en cache aux couches dispatcher et CDN, ce qui améliore finalement les performances de l’application cliente qui demande. Par défaut, AEM invalide le cache du réseau de diffusion de contenu (CDN) en fonction d’une durée de vie par défaut (TTL).

Avec GraphQL, vous pouvez configurer les en-têtes de cache HTTP pour contrôler ces paramètres pour votre requête individuelle conservée.

1. Le **En-têtes** est accessible à partir des trois points verticaux situés à droite du nom de la requête conservée (panneau à l’extrême gauche) :

   ![En-têtes de cache HTTP de requête persistants](assets/cfm-graphqlapi-headers-01.png "En-têtes de cache HTTP de requête persistants")

1. Si vous sélectionnez cette option, le **Configuration du cache** dialog :

   ![Paramètres d’en-tête de cache HTTP de requête persistant](assets/cfm-graphqlapi-headers-02.png "Paramètres d’en-tête de cache HTTP de requête persistant")

1. Sélectionnez le paramètre approprié, puis ajustez la valeur selon les besoins :

   * **cache-control** - **max-age**
Les caches peuvent stocker ce contenu pendant un nombre spécifié de secondes. Il s’agit généralement de la durée de vie (TTL) du navigateur.
   * **contrôle de substitution** - **s-maxage**
Identique à l’âge maximal, mais s’applique spécifiquement aux caches de proxy.
   * **contrôle de substitution** - **stale-while-revalidate**
Les caches peuvent continuer à fournir une réponse mise en cache après qu’elle est devenue obsolète, pendant un maximum de secondes.
   * **contrôle de substitution** - **stale-if-error**
Les caches peuvent continuer à fournir une réponse mise en cache en cas d’erreur ou d’origine, pendant un maximum de secondes.

1. Sélectionner **Enregistrer** pour conserver les modifications.

## Publication des requêtes conservées {#publishing-persisted-queries}

Une fois que vous avez sélectionné votre requête conservée dans la liste (panneau de gauche), vous pouvez utiliser la variable **Publier** et **Annuler la publication** actions. Ils seront alors activés dans votre environnement de publication (par exemple, `dev-publish`) pour un accès facile à vos applications lors des tests.

>[!NOTE]
>
>Définition du cache de la requête conservée `Time To Live` {&quot;cache-control&quot;:&quot;parameter&quot;:value} a une valeur par défaut de 2 heures (7 200 secondes).

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
