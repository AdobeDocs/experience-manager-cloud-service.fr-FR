---
title: Purge du cache du réseau CDN
description: Découvrez comment supprimer des objets mis en cache du cache CDN d’Adobe en configurant le jeton API de purge qui peut ensuite être utilisé dans les appels API.
feature: CDN Cache
exl-id: 4d091677-b817-4aeb-b131-7a5407ace3e0
role: Admin
source-git-commit: 5b777171cb9246c2a0174985e060d7d1b6ed8591
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 1%

---

# Purge du cache du réseau CDN {#cdn-purge-cache}

La purge supprime un objet du cache de réseau de diffusion de contenu Adobe, ce qui entraîne de futures demandes qui reviennent à l’origine comme une absence de cache, plutôt que d’être diffusées à partir du cache.
AEM as a Cloud Service vous permet de configurer un jeton API de purge, qui peut ensuite être utilisé dans les appels API de purge. Lisez la section [Configuration des informations d’identification et de l’authentification CDN](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) pour apprendre à configurer ce jeton à l’aide des directives d’authentification du pipeline de configuration Cloud Manager.

Il existe trois variations de purge prises en charge :

* [Purge d’URL unique](#single-purge) : purge d’une seule ressource à la fois.
* [Purger par clé de substitution](#surrogate-key-purge) : purge simultanée de plusieurs ressources.
* [Purge complète](#full-purge) - purge de toutes les ressources.

Toutes les variations de purge partagent les éléments suivants :

* La méthode HTTP doit être définie sur `PURGE`.
* L’URL peut être n’importe quel domaine associé au service d’AEM auquel la requête de purge est destinée.
* `X-AEM-Purge-Key` doit être fourni dans un en-tête HTTP.

>[!CAUTION]
>La purge du cache CDN, en particulier avec l’indicateur dur, augmente le trafic à l’origine et peut entraîner une interruption lorsqu’il n’est pas exécuté correctement.

Vous pouvez référencer [un tutoriel](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/caching/how-to/purge-cache) axé sur la configuration des clés de purge et l’exécution de la purge du cache CDN.

## Purge d’URL unique {#single-purge}

Vous pouvez purger une seule ressource à la fois comme suit :

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com/resource-path" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H 'X-AEM-Purge: soft'
```

Comme illustré dans l’exemple ci-dessus, vous pouvez **éventuellement** spécifier si le CDN doit effectuer une purge **hard** (par défaut) ou une purge **soft** sur les objets mis en cache.

La purge dure par défaut rend le contenu immédiatement inaccessible aux nouvelles requêtes jusqu’à ce que le contenu soit récupéré à partir de l’origine. La purge progressive marque le contenu comme obsolète, mais l’diffuse toujours aux clients afin qu’ils n’aient pas besoin d’attendre que le contenu soit récupéré à partir de l’origine.

## Purge des clés de substitution {#surrogate-key-purge}

Les clés de substitution sont des identifiants uniques que vous utilisez pour purger un ensemble de contenu. Elles sont appliquées au contenu en ajoutant un en-tête `Surrogate-Key` à la réponse. Une ou plusieurs clés de substitution peuvent être référencées dans un appel API de purge.

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "Surrogate-Key: my-surrogate-key"
-H "X-AEM-Purge: soft" #optional
```

Les `Surrogate-Key` sont séparés par des espaces. De la même manière que la purge d’URL unique, vous pouvez configurer une purge dure ou douce.

## Purge complète {#full-purge}

Vous pouvez effectuer une purge complète de toutes les ressources mises en cache comme suit :

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "X-AEM-Purge: all"
```

N’oubliez pas que l’en-tête `X-AEM-Purge` doit inclure la valeur &quot;all&quot;.

## Interactions avec le calque Apache/Dispatcher {#apache-layer}

Comme décrit sous [Flux de diffusion de contenu](/help/implementing/dispatcher/overview.md), le réseau de diffusion de contenu récupère le contenu de la couche Apache/Dispatcher, si le cache a expiré. Cela signifie qu’avant de purger une ressource sur le réseau de diffusion de contenu, vous devez vous assurer qu’une nouvelle version du contenu est également disponible sur Dispatcher. Pour plus d’informations, voir [Invalidation du cache de Dispatcher](/help/implementing/dispatcher/caching.md#disp).
