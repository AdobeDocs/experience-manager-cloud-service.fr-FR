---
title: Tableau de bord des performances du réseau CDN
description: Découvrez comment Cloud Manager évalue les performances du réseau de diffusion de contenu (CDN) et ce que vous pouvez apprendre à partir du tableau de bord.
exl-id: ecd8c1ca-873f-4e73-ad73-b5f7561eb109
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 2f02b9d70e56f4aafd802e986974533197f7d7a5
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Tableau de bord des performances du réseau CDN {#cdn-performance}

Découvrez comment Cloud Manager évalue les performances du réseau de diffusion de contenu (CDN) et ce que vous pouvez apprendre à partir du tableau de bord.

## Vue d’ensemble {#overview}

Chaque programme Cloud Manager comporte un tableau de bord des performances du réseau CDN. Ce tableau de bord présente le score global des performances du réseau CDN, ainsi que les tendances, les alertes et des suggestions d’amélioration, si nécessaire.

![ Tableau de bord des performances du réseau CDN ](assets/cdn-performance-dashboard.png)

## Accès au tableau de bord {#accessing}

Le tableau de bord du réseau CDN est disponible sur la page d’aperçu de chaque programme.

{{sign-in-to-cloud-manager}}

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, cliquez sur le programme dont vous souhaitez afficher le tableau de bord CDN.

   ![Page Mes programmes](assets/my-programs.png)

1. Pour afficher la carte **Performances**, faites défiler l’écran vers le bas en dessous des cartes **Environnements** et **Pipelines** sur la page **Aperçu du programme** de votre programme.

   ![Performances](assets/cdn-performance-overview.png)

## Utiliser le tableau de bord {#using}

Le tableau de bord présente un score global des performances du réseau CDN, ainsi que des tendances, des alertes et des suggestions d’amélioration, si nécessaire.

![ Tableau de bord des performances du réseau CDN ](assets/cdn-performance-dashboard.png)

Pour plus d’informations sur les performances de votre réseau CDN et pour obtenir des suggestions sur la manière de les améliorer, cliquez sur **Afficher la tendance**.

![Tendance des performances](assets/cdn-performance-trend.png)

Cliquez sur **Afficher** sous le graphique pour modifier la période du graphique.

Pour obtenir des suggestions sur la manière d’améliorer les performances de votre réseau CDN, sélectionnez l’onglet **Recommendations**.

![Recommandations relatives au réseau CDN](assets/cdn-performance-recommendations.png)

Cliquez sur le chevron en regard d’une recommandation de la liste pour afficher les détails sur les étapes d’amélioration requises et la cause du problème.

## Définition de l’accès au cache {#cache-hit}

Le taux d’accès au cache est une mesure du nombre de requêtes de contenu qu’un cache peut remplir avec succès, par rapport au nombre de requêtes qu’il reçoit. Un taux d’accès au cache plus élevé indique de meilleures performances du réseau CDN.

>[!TIP]
>
>Adobe recommande aux utilisateurs d’atteindre un taux d’accès au cache de 99 %.

```text
Cache Hit Ratio = Cache Hits / (Hits + Misses + Passes + Other)
```

* **Accès** - Les données sont demandées à partir du cache et sont trouvées.
* **Mlle** - Les données sont demandées à partir du cache et sont introuvables.
* **Transmettre** - Les données sont demandées à partir du cache et sont définies pour ne pas être mises en cache.
* **Autre** - Toutes les demandes de données du cache qui ne correspondent à aucune autre casse.

Les mesures du cache sont actualisées toutes les 24 heures.

>[!TIP]
>
>Pour plus d’informations sur la façon dont Cloud Manager et le réseau CDN interagissent avec le Dispatcher, consultez [ Mise en cache dans AEM as a Cloud Service](/help/implementing/dispatcher/caching.md).

