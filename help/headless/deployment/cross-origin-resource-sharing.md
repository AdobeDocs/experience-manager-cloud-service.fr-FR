---
title: Configuration du partage des ressources cross-origin (CORS) avec AEM découplé
description: Le partage des ressources cross-origin (CORS) d’Adobe Experience Manager permet aux applications web découplées d’effectuer des appels côté client vers AEM. Une configuration CORS est nécessaire pour activer l’accès au point d’entrée GraphQL.
feature: GraphQL API
exl-id: 426be9f9-f44a-4744-ac08-e64bb97308a0
source-git-commit: 316680823fe4bc85e1f4359305047c0d1f517dc7
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 90%

---

# Configuration du partage des ressources cross-origin (CORS)

>[!CAUTION]
>
>If [La mise en cache dans Dispatcher a été activée.](/help/headless/deployment/dispatcher-caching.md) Le filtre CORS n’est pas nécessaire. Cette section peut donc être ignorée.

>[!NOTE]
>
>Pour un aperçu détaillé de la politique de partage des ressources CORS dans AEM, voir [Description du partage des ressources Cross-Origin (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=fr#understand-cross-origin-resource-sharing-(cors)).

Pour accéder au point d’entrée GraphQL, une politique CORS doit être configurée et ajoutée à un projet AEM qui soit [déployé vers AEM via Cloud Manager](/help/implementing/cloud-manager/deploy-code.md). Vous devez pour cela ajouter un fichier de configuration CORS OSGi approprié pour le ou les points d’entrée souhaités. Plusieurs configurations CORS peuvent être créées et déployées dans différents environnements. Vous trouverez des exemples dans la section [Site de référence WKND](https://github.com/adobe/aem-guides-wknd/tree/master/ui.config/src/main/content/jcr_root/apps/wknd/osgiconfig)

La configuration CORS doit spécifier une origine de site web approuvée `alloworigin` ou `alloworiginregexp` pour laquelle l’accès doit être accordé.

Le fichier de configuration doit être nommé comme suit : `com.adobe.granite.cors.impl.CORSPolicyImpl~appname-graphql.cfg.json` où `appname` reflète le nom de votre application.

Par exemple, pour accorder l’accès au point d’entrée GraphQL `/content/cq:graphql/wknd/endpoint` et aux points d’entrée des requêtes persistantes pour `https://my.domain`, vous pouvez utiliser :

```json
{
  "supportscredentials":false,
  "supportedmethods":[
    "GET",
    "HEAD",
    "POST"
  ],
  "exposedheaders":[
    ""
  ],
  "alloworigin":[
    "https://my.domain"
  ],
  "maxage:Integer":1800,
  "alloworiginregexp":[
    ""
  ],
  "supportedheaders":[
    "Origin",
    "Accept",
    "X-Requested-With",
    "Content-Type",
    "Access-Control-Request-Method",
    "Access-Control-Request-Headers"
  ],
  "allowedpaths":[
    "/content/cq:graphql/wknd/endpoint.json",
    "/graphql/execute.json/.*"
  ]
}
```

Si vous avez configuré un chemin d’accès Vanity pour le point d’entrée, vous pouvez également l’utiliser dans `allowedpaths`.
