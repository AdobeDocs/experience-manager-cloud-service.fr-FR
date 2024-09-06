---
title: Tableau de bord des performances du réseau CDN
description: Découvrez comment Cloud Manager évalue les performances du réseau de diffusion de contenu et ce que vous pouvez apprendre du tableau de bord.
exl-id: ecd8c1ca-873f-4e73-ad73-b5f7561eb109
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 5%

---

# Tableau de bord des performances du réseau CDN {#cdn-performance}

Découvrez comment Cloud Manager évalue les performances du réseau de diffusion de contenu et ce que vous pouvez apprendre du tableau de bord.

## Vue d’ensemble {#overview}

Chaque programme Cloud Manager dispose d’un tableau de bord des performances CDN. Ce tableau de bord présente un score global des performances du réseau de diffusion de contenu, ainsi que des tendances, des alertes et des suggestions d’amélioration, le cas échéant.

![Tableau de bord des performances CDN](assets/cdn-performance-dashboard.png)

## Accès au tableau de bord {#accessing}

Le tableau de bord du réseau CDN est disponible sur la page d’aperçu de chaque programme.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, appuyez ou cliquez sur le programme dont vous souhaitez afficher le tableau de bord CDN.

   ![Ma page de programmes](assets/my-programs.png)

1. Sur la page **Aperçu du programme** de votre programme, faites défiler la page sous les cartes **Environnements** et **Pipelines** pour afficher la carte **Performance**.

   ![Performances](assets/cdn-performance-overview.png)

## Utilisation du tableau de bord {#using}

Le tableau de bord présente un score global des performances du réseau de diffusion de contenu, ainsi que des tendances, des alertes et des suggestions d’amélioration, le cas échéant.

![Tableau de bord des performances CDN](assets/cdn-performance-dashboard.png)

Pour plus d’informations sur les performances de votre réseau de diffusion de contenu et pour obtenir des suggestions pour l’améliorer, appuyez ou cliquez sur **Afficher la tendance**.

![Tendance de performances](assets/cdn-performance-trend.png)

Appuyez ou cliquez sur **Afficher** sous le graphique pour modifier la période du graphique.

Pour obtenir des suggestions sur la façon d’améliorer les performances de votre réseau de diffusion de contenu, sélectionnez l’onglet **Recommendations** .

![Recommandations CDN](assets/cdn-performance-recommendations.png)

Appuyez ou cliquez sur le chevron en regard d’une recommandation dans la liste pour afficher les détails sur les étapes à suivre pour améliorer et la cause du problème.

## Définition des accès au cache {#cache-hit}

Le taux d’accès au cache est une mesure du nombre de requêtes de contenu qu’un cache peut remplir avec succès, par rapport au nombre de requêtes qu’il reçoit. Plus le taux d’accès au cache est élevé, plus le réseau de diffusion de contenu est performant.

>[!TIP]
>
>Adobe recommande que les utilisateurs visent un taux d’accès au cache de 99 %.

```text
Cache Hit Ratio = Cache Hits / (Hits + Misses + Passes + Other)
```

* **Accès** - Les données sont demandées par le cache, et elles ont été trouvées.
* **Miss** - Les données sont demandées par le cache et sont introuvables.
* **Pass** - Les données sont demandées par le cache et sont définies pour ne pas mettre ces données en cache dans tous les cas.
* **Autre** - Toutes les requêtes de données du cache qui ne correspondent à aucun autre cas.

Les mesures du cache sont mises à jour toutes les 24 heures.

>[!TIP]
>
>Pour plus d’informations sur la façon dont Cloud Manager et le réseau de diffusion de contenu interagissent avec Dispatcher, consultez le document [Mise en cache dans AEM as a Cloud Service](/help/implementing/dispatcher/caching.md).
