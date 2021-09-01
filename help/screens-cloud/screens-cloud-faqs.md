---
title: FAQ sur Screens as a Cloud Service
description: Cette page décrit les questions fréquentes de Screens en tant que Cloud Service.
source-git-commit: 7a26bb50a8b95a2358912249e21daeb9c5e9c1a3
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# FAQ sur Screens as a Cloud Service {#screens-cloud-faqs}

La section suivante fournit des réponses aux questions fréquentes relatives à Screens en tant que projet de Cloud Service.

## Que dois-je faire si le lecteur AEM Screens pointant vers Screens en tant que Cloud Service ne sélectionne pas les clientlibs personnalisées au format /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css ?

AEM en tant que Cloud Service modifie les longues clés de cache avec chaque déploiement. AEM Screens génère les caches hors ligne lorsque le contenu est modifié, plutôt que lorsque Cloud Manager exécute le déploiement. Ces longues clés de cache dans les manifestes ne sont pas valides. Par conséquent, le lecteur ne parvient pas à télécharger ces *clientlibs*.

L’utilisation de `longCacheKey="none"` dans votre dossier `clientlib` supprime complètement les clés de cache longues pour ces *clientlibs*.


## Que devons-nous faire si le manifeste hors ligne n’inclut pas toutes les ressources comme prévu ? {#offline-manifest}

Les caches hors ligne sont générés à l’aide de l’utilisateur du service **bulk-offline-update-screens-service** . Certains chemins, inaccessibles par `bulk-offline-update-screens-service`, entraînent l’absence de contenu dans les manifestes hors ligne.

Dans votre code, c’est-à-dire `ui.config or ui.apps`, créez une configuration OSGi dans le dossier de configuration, avec le contenu suivant, et nommez le fichier `org.apache.sling.jcr.repoinit.RepositoryInitializer-serviceusersandacls-content.config`.

```
scripts=[
        "
        set principal ACL for bulk-offline-update-screens-service
                allow jcr:read on /content/mysite
                allow jcr:read on /apps/my-resources
        end
        "] 
```
