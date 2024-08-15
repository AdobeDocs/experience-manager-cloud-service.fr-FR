---
title: Configuration du point de terminaison Dispatcher avec AEM sans affichage
description: Dispatcher est une couche de mise en cache et de sécurité pour les environnements de publication Adobe Experience Manager. Plusieurs configurations sont utilisées pour ouvrir les points d’entrée GraphQL aux applications découplées.
feature: Headless, Dispatcher, GraphQL API
exl-id: 78a20021-910f-4cf0-87bf-6e2223994f76
role: Admin, Developer
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 85%

---


# Dispatcher - Configuration de point de terminaison avec AEM sans affichage

[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr) est une couche de mise en cache et de sécurité pour les environnements de publication Adobe Experience Manager. Plusieurs configurations sont incluses par défaut pour ouvrir les points d’entrée GraphQL aux applications découplées.

>[!NOTE]
>
>Pour obtenir une documentation détaillée à propos du Dispatcher, veuillez consulter le [Guide du Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr).

Dans le cadre d’un projet AEM, un module du Dispatcher contenant les configurations du Dispatcher est inclus. Les projets nouvellement générés à partir de l’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) incluent automatiquement des [filtres](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=fr#defining-a-filter) qui activent les points d’entrée GraphQL.

## Points d’entrée GraphQL

Dans le cadre des filtres par défaut, les [points d’entrée GraphQL](/help/headless/graphql-api/graphql-endpoint.md) sont ouverts avec la règle suivante :

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

Le caractère générique `*` ouvre plusieurs points d’entrée sur l’instance AEM. La requête qui utilise un point d’entrée GraphQL s’effectue à l’aide de `POST` et la réponse n’est **pas** mise en cache.

## Requêtes persistantes GraphQL

La demande de requêtes persistantes s’effectue sur un autre point d’entrée. Dans le cadre de la configuration de filtre par défaut, l’URL pour les [requêtes persistantes](/help/headless/graphql-api/persisted-queries.md) est ouverte avec la règle suivante :

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

Les requêtes persistantes peuvent être demandées à l’aide de `GET`, mettant ainsi en cache la réponse au niveau du Dispatcher et du réseau CDN. Vous trouverez plus d’informations sur la mise en cache et l’invalidation du cache sous [l’ Introduction à la mise en cache dans AEM as a Cloud Service](/help/implementing/dispatcher/caching.md).
