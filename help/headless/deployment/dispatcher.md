---
title: Configuration du point de terminaison Dispatcher avec AEM sans affichage
description: Dispatcher est une couche de mise en cache et de sécurité pour les environnements de publication Adobe Experience Manager. Plusieurs configurations sont utilisées pour ouvrir les points d’entrée GraphQL aux applications découplées.
feature: Dispatcher, GraphQL API
exl-id: 78a20021-910f-4cf0-87bf-6e2223994f76
source-git-commit: 316680823fe4bc85e1f4359305047c0d1f517dc7
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 51%

---


# Dispatcher : configuration du point d’entrée avec AEM sans affichage

[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr) est une couche de mise en cache et de sécurité pour les environnements de publication Adobe Experience Manager. Plusieurs configurations sont incluses par défaut pour ouvrir les points d’entrée GraphQL aux applications découplées.

>[!NOTE]
>
>Pour obtenir une documentation détaillée sur Dispatcher, voir la section [Guide de Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr).

Dans le cadre d’un projet AEM, un module de Dispatcher contient des configurations pour Dispatcher. Projets nouvellement générés à partir de la fonction [AEM Archétype de projet](https://github.com/adobe/aem-project-archetype) inclusion automatique [filtres](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=fr#defining-a-filter) qui activent les points de fin GraphQL.

## Points d’entrée GraphQL

Dans le cadre des filtres par défaut, les [points d’entrée GraphQL](/help/headless/graphql-api/graphql-endpoint.md) sont ouverts avec la règle suivante :

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

Le caractère générique `*` ouvre plusieurs points d’entrée sur l’instance AEM. La requête à l’aide d’un point de terminaison GraphQL est effectuée à l’aide de `POST` et la réponse est **not** mis en cache.

## Requêtes persistantes GraphQL

La demande de requêtes persistantes est effectuée sur un autre point de terminaison. Dans le cadre de la configuration de filtre par défaut, l’URL pour [Requêtes persistantes](/help/headless/graphql-api/persisted-queries.md) s’ouvre avec la règle suivante :

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

Les requêtes persistantes peuvent être demandées à l’aide de `GET`, en mettant en cache la réponse au niveau du Dispatcher et du réseau de diffusion de contenu. Vous trouverez plus d’informations sur la mise en cache et l’invalidation du cache [ici](/help/implementing/dispatcher/caching.md).
