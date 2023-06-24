---
title: Questions fréquentes sur Screens as a Cloud Service
description: Cette page décrit les questions fréquentes as a Cloud Service à Screens.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 58%

---

# Questions fréquentes sur Screens as a Cloud Service {#screens-cloud-faqs}

La section suivante fournit des réponses aux questions fréquentes relatives au projet Screens as a Cloud Service.

## Que dois-je faire si le lecteur AEM Screens pointant vers Screens as a Cloud Service ne sélectionne pas les clientlibs personnalisées au format /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css ?

AEM as a Cloud Service modifie les longues clés de cache lors de chaque déploiement. AEM Screens génère les caches hors ligne lorsque le contenu est modifié et pas lorsque Cloud Manager exécute le déploiement. Ces longues clés de cache dans les manifestes ne sont pas valides. Par conséquent, le lecteur ne parvient pas à télécharger la variable *clientlibs*.

Utilisation `longCacheKey="none"` dans votre `clientlib` supprime complètement les clés de cache longues pour le dossier *clientlibs*.


## Que dois-je faire si le manifeste hors ligne n’inclut pas toutes les ressources comme prévu ? {#offline-manifest}

Les caches hors ligne sont générés à l’aide de l’utilisateur de service **bulk-offline-update-screens-service**. Certains chemins ne sont pas accessibles par `bulk-offline-update-screens-service`, ce qui entraîne à du contenu manquant dans les manifestes hors ligne.

Dans votre code, soit `ui.config or ui.apps`, créez une configuration OSGi dans le dossier de configuration avec le contenu suivant et donnez au fichier le titre suivant `org.apache.sling.jcr.repoinit.RepositoryInitializer-serviceusersandacls-content.config`

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

Il est recommandé d’utiliser des images au format `.png` et `.jpeg` dans un canal AEM Screens as a Cloud Service, pour une expérience de signalétique numérique optimale.
Les images au format `*.tif` (format de fichier image de balise) ne sont pas pris en charge dans AEM Screens as a Cloud Service. Si un canal présente ce format d’image, l’image n’est pas rendue du côté du lecteur.

## Que dois-je faire si un canal en mode Développeur (en ligne) n’est pas rendu sur le lecteur AEM Screens ? {#screens-cloud-online-channel-blank-iframe}

Adobe vous recommande d’utiliser les fonctionnalités de mise en cache d’AEM Screens. Cependant, si vous devez exécuter votre canal en mode Développeur et que le lecteur AEM Screens affiche un écran vide, vérifiez les outils de développement de votre lecteur et recherchez `X-Frame-Options` ou `frame-ancestors` erreurs. La résolution consiste à configurer Dispatcher pour autoriser l’exécution du contenu dans les iFrames. En règle générale, la configuration suivante fonctionne :

```
Header set Content-Security-Policy "frame-ancestors 'self' file: localhost:*;"
```

## À quoi sert la limite du code d’enregistrement ?

Il est recommandé de limiter l’utilisation du code d’enregistrement. Si un code d’enregistrement est compromis, mais a une limite de 100 enregistrements, la personne malveillante peut s’enregistrer uniquement jusqu’à ce nombre, mais pas au-delà. Vous pouvez toujours mettre à jour la limite d’utilisation après la création du code d’enregistrement et l’enregistrement de certains lecteurs du client. Si le client observe une activité d’enregistrement inhabituelle pour un code d’enregistrement spécifique, il peut réduire la limite en temps réel pendant son enquête. Ils peuvent augmenter le nombre s&#39;il s&#39;agissait d&#39;une fausse alarme, sans affecter les lecteurs déjà enregistrés.
