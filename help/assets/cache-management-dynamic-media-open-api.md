---
title: Gestion du cache dans Dynamic Media avec les API ouvertes
description: Gestion du cache dans Dynamic Media avec les API ouvertes
role: User
exl-id: 203a5291-edb5-4900-8b0a-32e1ebae5395
source-git-commit: 8c9e59108d28ee02a4609c58bf7a2543783f47e2
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 1%

---

# Gestion du cache dans Dynamic Media avec les API ouvertes {#cache-management-dynamic-media-open-apis}

Une gestion efficace du cache est essentielle pour fournir des ressources numériques hautes performances, évolutives et à jour. Dans Dynamic Media avec des API ouvertes, la gestion du cache définit la manière dont le contenu est stocké, actualisé et diffusé sur les différents calques du pipeline de diffusion. Les réponses de diffusion des ressources sont mises en cache sur plusieurs couches pour garantir des performances optimales et une diffusion rapide du contenu.

La mise en cache prolongée dans Dynamic Media avec les API ouvertes se compose de [mise en cache de la couche CDN](#cdn-layer-caching) et [contrôle de cache externe (mise en cache BYOCDN et navigateur)](#byocdn-browser-caching).

## Mise en cache de la couche CDN {#cdn-layer-caching}

Les réponses de diffusion des ressources sont mises en cache sur le [réseau CDN géré par Adobe](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn#aem-managed-cdn) pendant une période prolongée afin d’optimiser les performances et de minimiser la charge sur l’origine. Cette mise en cache est entièrement gérée par Adobe afin d’assurer une expérience de haute qualité cohérente pour les utilisateurs finaux et utilisatrices finales. La durée de mise en cache est intentionnellement optimisée pour les performances et ne peut pas être personnalisée par les utilisateurs pour maintenir la fiabilité et l’efficacité de la diffusion du contenu à tous les clients.

Toutes les URL de diffusion sont mises en cache à la périphérie (rapidement) pendant une durée prolongée afin d’assurer des performances optimales. Les objets de diffusion mis en cache comprennent les rendus statiques, les vidéos, les fichiers binaires d’image d’origine et les images transformées dynamiquement, telles que les ressources redimensionnées ou reformatées générées par le biais de paramètres d’URL. <!--The CDN is designed to serve these assets directly from the cache without revalidating them, unless an explicit purge is performed.-->

## Contrôle de cache externe (BYOCDN et mise en cache du navigateur) {#byocdn-browser-caching}

Les réponses de diffusion des ressources incluent un en-tête `Cache-Control` avec une `max-age` par défaut de **10 minutes** pour les couches de mise en cache en aval. Cela s’applique aux configurations ** BYOCDN) personnalisées, *navigateurs de l’utilisateur final* et à tout *proxy de mise en cache intermédiaire*, afin d’assurer un contrôle de cache cohérent sur l’ensemble du chemin de diffusion.

### Personnalisation des en-têtes de contrôle du cache {#customizing-cache-control-headers}

L’augmentation du temps d’expiration du cache au-delà de la configuration par défaut augmente la probabilité de diffuser du contenu obsolète, ce qui peut retarder la visibilité des mises à jour de contenu dans l’expérience de l’utilisateur final. Si vous devez modifier le comportement du contrôle du cache pour votre cas d’utilisation spécifique, vous pouvez configurer des règles CDN personnalisées pour ajuster les en-têtes de réponse. Vous pouvez ainsi définir différentes durées de mise en cache en fonction de vos besoins. Reportez-vous à [Règles de réseau CDN personnalisé AEM pour les en-têtes de réponse](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic).

```
responseTransformations:
    rules:
      - name: cache-asset-delivery
        when:
          allOf:
            - reqProperty: path
              like: '/adobe/assets/urn:aaid:aem:*'
            - reqProperty: tier
              equals: delivery
        actions:
          - type: set
            respHeader: Cache-Control
            value: max-age=300
```

Pour toute assistance supplémentaire ou toute question sur la gestion du cache, contactez [l’assistance Adobe](https://helpx.adobe.com/in/contact.html).

## Invalidation du cache actif {#active-cache-invalidation}

Chaque fois qu’une ressource est mise à jour, supprimée ou modifiée (tout changement de métadonnées), Dynamic Media avec des API ouvertes invalide automatiquement chaque URL de diffusion associée sur le réseau CDN géré par Adobe. Cela s’applique aux URL qui utilisent des ID ou des alias de redirection, ainsi qu’aux URL qui incluent des paramètres de transformation, tels que la largeur, le format ou la qualité. Cette invalidation pilotée par les événements garantit que vos utilisateurs reçoivent toujours la version la plus récente de vos ressources sans intervention manuelle.

### Purge manuelle du cache {#manual-cache-purging}

Lorsqu’il est nécessaire de purger manuellement le contenu mis en cache, vous pouvez utiliser les fonctionnalités d’invalidation du cache d’AEM. Pour obtenir des instructions détaillées sur la purge d’URL de cache spécifiques, consultez la section [Invalidation du cache du réseau CDN AEM](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-cache-purge#single-purge).

## Questions fréquemment posées{#faq-cache-management}

+++**En quoi la gestion du cache affecte-t-elle les intégrations existantes ?**

Les URL des ressources restent inchangées et l’en-tête de contrôle du cache envoyé aux navigateurs (et autres intermédiaires en aval) à partir du réseau CDN géré par Adobe continue à durer 10 minutes avec un [`stale-while-revalidate directive`](https://web.dev/articles/stale-while-revalidate#whats_it_mean), ce qui garantit que les systèmes en aval continuent à exploiter leurs caches de manière optimale.

+++

+++**Qu’est-ce qui déclenche une purge du cache ?**

La purge du cache se déclenche automatiquement lorsqu’une ressource est mise à jour, modifiée, archivée ou supprimée.

<!--The cache purge triggers automatically in the following circumstances:
 
 - when an asset is updated, modified, or archived.
 - when an asset reaches `ready_for_delivery` state after approval.-->

+++

<!--
+++ **How long does it take for the cache to refresh after updating an asset?**

Any time the asset changes, the cache refreshes usually in *less than 60 seconds*.

+++

<!--
+++ **What happens if the cache purge system fails?**
The following mechanisms can be followed:
 
 - **Automatic retries:** 3 retry attempts with exponential backoff
 - **Monitoring:** Sev-2 alert fires if staleness exceeds 10 minutes
 - **Natural expiry:** Even without purge, cache expires after 10 hours maximum
 - **Manual override:** Engineers can manually purge via CLI tool

+++
-->

+++ **Quels sont les types de ressources pris en charge pour la mise en cache de longue durée ?**

La mise en cache prolongée avec invalidation de cache active pilotée par les événements s’applique à tous les types de ressources dans Dynamic Media avec les API ouvertes, quel que soit leur type ou format.

+++

+++ **Puis-je me désinscrire de la mise en cache de longue durée pour mon référentiel ?**

Pour vous exclure de la mise en cache prolongée, contactez l’assistance technique d’Adobe [](https://helpx.adobe.com/in/contact.html) et justifiez votre demande.

+++


>[!MORELIKETHIS]
>
>- [Intégration du sélecteur de ressources à diverses applications](/help/assets/integrate-asset-selector.md)
>- [URL de redirection](/help/assets/vanity-urls.md)
