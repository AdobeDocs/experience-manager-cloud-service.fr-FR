---
title: Configuration du Dispatcher avec AEM découplé
description: Dispatcher est une couche de mise en cache et de sécurité pour les environnements de publication Adobe Experience Manager. Plusieurs configurations sont utilisées pour ouvrir les points d’entrée GraphQL aux applications découplées.
feature: Dispatcher, GraphQL API
exl-id: 78a20021-910f-4cf0-87bf-6e2223994f76
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: ht
source-wordcount: '233'
ht-degree: 100%

---

# Configuration du Dispatcher avec AEM découplé

[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr) est une couche de mise en cache et de sécurité pour les environnements de publication Adobe Experience Manager. Plusieurs configurations sont incluses par défaut pour ouvrir les points d’entrée GraphQL aux applications découplées.

>[!NOTE]
>
>Pour obtenir une documentation détaillée à propos de Dispatcher, veuillez consulter le [Guide de Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr)

Dans le cadre d’un projet AEM, un module de Dispatcher contenant les configurations du Dispatcher est inclus. Les projets nouvellement générés à partir de l’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) incluent automatiquement des [filtres](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=fr#defining-a-filter) qui activent les points d’entrée GraphQL.

## Point(s) d’entrée GraphQL

Dans le cadre des filtres par défaut, les [points d’entrée GraphQL](/help/headless/graphql-api/graphql-endpoint.md) sont ouverts avec la règle suivante :

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

Le caractère générique `*` ouvre plusieurs points d’entrée sur l’instance AEM. La requête qui utilise un point d’entrée GraphQL s’effectue à l’aide de `POST` et la réponse ne sera **pas** mise en cache.

## Requêtes persistantes GraphQL

La demande de requêtes persistantes s’efectue sur un autre point d’entrée. Dans le cadre de la configuration de filtre par défaut, les URL pour les [Requêtes persistantes](/help/headless/graphql-api/persisted-queries.md) sont ouvertes avec la règle suivante :

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

Les requêtes persistantes peuvent être demandées à l’aide de `GET`, mettant ainsi en cache la réponse au niveau du Dispatcher et du réseau CDN. Vous trouverez plus d’informations sur la mise en cache et l’invalidation du cache [ici](/help/implementing/dispatcher/caching.md).
