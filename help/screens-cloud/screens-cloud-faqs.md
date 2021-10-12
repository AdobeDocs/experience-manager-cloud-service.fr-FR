---
title: Questions fréquentes as a Cloud Service sur Screens
description: Cette page décrit les questions fréquentes as a Cloud Service à Screens.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
source-git-commit: cf091056bdb96917a6d22bf1197d9b34ebbf9610
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Questions fréquentes as a Cloud Service sur Screens {#screens-cloud-faqs}

La section suivante fournit des réponses aux questions fréquentes relatives au projet Screens as a Cloud Service.

## Que dois-je faire si le lecteur AEM Screens pointant vers Screens as a Cloud Service ne sélectionne pas les clientlibs personnalisées au format /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css ?

AEM as a Cloud Service modifie les longues clés de cache avec chaque déploiement. AEM Screens génère les caches hors ligne lorsque le contenu est modifié, plutôt que lorsque Cloud Manager exécute le déploiement. Ces longues clés de cache dans les manifestes ne sont pas valides. Par conséquent, le lecteur ne parvient pas à télécharger ces *clientlibs*.

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

## Quels formats d’image sont recommandés pour un rendu transparent des images dans un canal as a Cloud Service AEM Screens ?{#screens-cloud-image-format}

Il est recommandé d’utiliser des images au format `.png` et `.jpeg` dans un canal as a Cloud Service AEM Screens, pour une expérience de signalétique digitale optimale.
Les images au format `*.tif` (format de fichier image de balise) ne sont pas prises en charge dans AEM Screens as a Cloud Service. Si un canal présente ce format d’image, l’image ne sera pas rendue du côté du lecteur.