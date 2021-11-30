---
title: Questions fréquentes as a Cloud Service sur Screens
description: Cette page décrit les questions fréquentes as a Cloud Service à Screens.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
source-git-commit: 02c9cbff56399ea2ca1baad7d2289d5d4c17c1c5
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# Questions fréquentes as a Cloud Service sur Screens {#screens-cloud-faqs}

La section suivante fournit des réponses aux questions fréquentes relatives au projet Screens as a Cloud Service.

## Que dois-je faire si le lecteur AEM Screens pointant vers Screens as a Cloud Service ne sélectionne pas les clientlibs personnalisées au format /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css ?

AEM as a Cloud Service modifie les longues clés de cache avec chaque déploiement. AEM Screens génère les caches hors ligne lorsque le contenu est modifié, plutôt que lorsque Cloud Manager exécute le déploiement. Ces longues clés de cache dans les manifestes ne sont pas valides. Le lecteur ne parvient donc pas à les télécharger. *clientlibs*.

Utilisation `longCacheKey="none"` dans votre `clientlib` supprime complètement les clés de cache longues pour ces *clientlibs*.


## Que devons-nous faire si le manifeste hors ligne n’inclut pas toutes les ressources comme prévu ? {#offline-manifest}

Les caches hors ligne sont générés à l’aide de **bulk-offline-update-screens-service** utilisateur du service. Certains chemins ne sont pas accessibles par `bulk-offline-update-screens-service`, entraîne l’absence de contenu dans les manifestes hors ligne.

Dans votre code, c’est-à-dire : `ui.config or ui.apps`, créez une configuration OSGi dans le dossier de configuration, avec le contenu suivant et donnez au nom du fichier le titre `org.apache.sling.jcr.repoinit.RepositoryInitializer-serviceusersandacls-content.config`

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

Il est recommandé d&#39;utiliser des images au format `.png` et `.jpeg` dans un canal as a Cloud Service AEM Screens, pour une expérience de signalétique digitale optimale.
Les images au format `*.tif` (Format de fichier image de balise) ne sont pas pris en charge dans AEM Screens as a Cloud Service. Si un canal présente ce format d’image, l’image ne sera pas rendue du côté du lecteur.

## Que dois-je faire si un canal en mode Développeur (en ligne) n’est pas rendu sur le lecteur AEM Screens ?{#screens-cloud-online-channel-blank-iframe}

Il est recommandé d’utiliser les fonctionnalités de mise en cache d’AEM Screens, mais si vous devez exécuter votre canal en mode Développeur et que le lecteur AEM Screens affiche un écran vide, vérifiez les outils de développement de votre lecteur et recherchez `X-Frame-Options` ou `frame-ancestors` erreurs. La résolution consiste à configurer Dispatcher pour autoriser l’exécution du contenu dans les iFrames. En règle générale, la configuration suivante fonctionne :

```
Header set Content-Security-Policy "frame-ancestors ‘self’ file: localhost:*;"
```

## À quoi sert la limite du code d’enregistrement ?

Il est recommandé de limiter l’utilisation du code d’enregistrement. Si un code d&#39;enregistrement est compromis, mais a une limite de 100 enregistrements, l&#39;attaquant peut s&#39;enregistrer uniquement jusqu&#39;à ce nombre, mais pas plus. Vous pouvez toujours mettre à jour la limite d’utilisation après la création du code d’enregistrement et l’enregistrement de certains lecteurs du client. Si le client observe une activité d’enregistrement inhabituelle pour un code d’enregistrement spécifique, il peut réduire la limite en temps réel pendant qu’il enquête et peut augmenter le nombre s’il s’agit d’une fausse alarme, sans affecter les lecteurs déjà enregistrés.
