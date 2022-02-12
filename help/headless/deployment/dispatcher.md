---
title: Configuration du Dispatcher avec AEM sans affichage
description: Dispatcher est une couche de mise en cache et de sécurité devant les environnements de publication Adobe Experience Manager. Plusieurs configurations sont utilisées pour ouvrir les points d’entrée GraphQL aux applications sans interface utilisateur graphique.
feature: Dispatcher, GraphQL API
source-git-commit: 0cc131209f497241949f8da6e8144dfcaffe7e6e
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 6%

---


# Configuration du Dispatcher avec AEM sans affichage

Le [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr) est une couche de mise en cache et de sécurité devant les environnements de publication Adobe Experience Manager. Plusieurs configurations sont incluses par défaut pour ouvrir les points d’entrée GraphQL aux applications sans interface utilisateur graphique.

>[!NOTE]
>
>Pour obtenir une documentation détaillée sur Dispatcher, reportez-vous à la section [Guide de Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)

Dans le cadre d’un projet AEM, un module de Dispatcher contenant les configurations du Dispatcher est inclus. Projets nouvellement générés à partir de la fonction [AEM Archétype de projet](https://github.com/adobe/aem-project-archetype) inclut automatiquement [filtres](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?#defining-a-filter) qui active les points d’entrée GraphQL.

## Points d’entrée GraphQL

Dans le cadre des filtres par défaut, [Points d’entrée GraphQL](/help/headless/graphql-api/graphql-endpoint.md) sont ouvertes avec la règle suivante :

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

Le `*` Le caractère générique ouvre plusieurs points de terminaison sur l’instance AEM. La requête à l’aide d’un point d’entrée GraphQL s’effectue à l’aide de `POST` et la réponse sera **not** être mis en cache.

## Requêtes persistantes GraphQL

La demande de requêtes persistantes est effectuée sur un autre point de terminaison. Dans le cadre de la configuration de filtre par défaut, l’URL pour [Requêtes persistantes](/help/headless/graphql-api/persisted-queries.md) sont ouvertes avec la règle suivante :

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

Les requêtes persistantes peuvent être demandées à l’aide de `GET`, mettant ainsi en cache la réponse au niveau du Dispatcher et du réseau de diffusion de contenu. Vous trouverez plus d’informations sur la mise en cache et l’invalidation du cache. [here](/help/implementing/dispatcher/caching.md).
