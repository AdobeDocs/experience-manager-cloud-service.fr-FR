---
title: Configuration du partage des ressources cross-origin (CORS) avec AEM sans affichage
description: Le partage des ressources cross-origin (CORS) de Adobe Experience Manager permet aux applications web sans interface utilisateur d’effectuer des appels côté client vers AEM. Une configuration CORS est nécessaire pour activer l’accès au point d’entrée GraphQL.
feature: GraphQL API
source-git-commit: 0cc131209f497241949f8da6e8144dfcaffe7e6e
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 28%

---


# Configuration du partage des ressources cross-origin (CORS)

>[!NOTE]
>
>Pour un aperçu détaillé de la politique de partage des ressources CORS dans AEM, voir [Description du partage des ressources Cross-Origin (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=fr#understand-cross-origin-resource-sharing-(cors)).

Pour accéder au point d’entrée GraphQL, une stratégie CORS doit être configurée et ajoutée à un projet AEM qui est [déployé vers AEM via Cloud Manager](/help/implementing/cloud-manager/deploy-code.md). Vous devez pour cela ajouter un fichier de configuration CORS OSGi approprié pour le ou les points d’entrée souhaités. Plusieurs configurations CORS peuvent être créées et déployées dans différents environnements. Vous trouverez des exemples dans la section [Site de référence WKND](https://github.com/adobe/aem-guides-wknd/tree/master/ui.config/src/main/content/jcr_root/apps/wknd/osgiconfig)

La configuration CORS doit spécifier une origine de site web approuvée. `alloworigin` ou `alloworiginregexp` dont l&#39;accès doit être accordé.

Le fichier de configuration doit être nommé comme suit : `com.adobe.granite.cors.impl.CORSPolicyImpl~appname-graphql.cfg.json` where `appname` reflète le nom de votre application.

Par exemple, pour accorder l’accès au point d’entrée GraphQL `/content/cq:graphql/wknd/endpoint` et point de terminaison de requêtes persistant pour `https://my.domain` vous pouvez utiliser :

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


