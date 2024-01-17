---
title: Tableau de bord des performances du réseau CDN
description: Découvrez comment Cloud Manager évalue les performances du réseau de diffusion de contenu et ce que vous pouvez apprendre du tableau de bord.
source-git-commit: 0d60c19638707262dab7f290f84fa873b694bc22
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 3%

---


# Tableau de bord des performances du réseau CDN {#cdn-performance}

Découvrez comment Cloud Manager évalue les performances du réseau de diffusion de contenu et ce que vous pouvez apprendre du tableau de bord.

## Vue d’ensemble {#overview}

Chaque programme Cloud Manager dispose d’un tableau de bord des performances CDN. Ce tableau de bord présente un score global des performances du réseau de diffusion de contenu, ainsi que des tendances, des alertes et des suggestions d’amélioration, le cas échéant.

![Tableau de bord des performances du réseau CDN](assets/cdn-performance-dashboard.png)

## Accès au tableau de bord {#accessing}

Le tableau de bord du réseau CDN est disponible sur la page d’aperçu de chaque programme.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** , appuyez ou cliquez sur le programme dont vous souhaitez afficher le tableau de bord CDN.

   ![Page Mes programmes](assets/my-programs.png)

1. Sur le **Aperçu du programme** de votre programme, faites défiler la page vers le bas, **Environnements** et **Pipelines** pour afficher les **Performances** carte.

   ![Performances](assets/cdn-performance-overview.png)

## Utilisation du tableau de bord {#using}

Le tableau de bord présente un score global des performances du réseau de diffusion de contenu, ainsi que des tendances, des alertes et des suggestions d’amélioration, le cas échéant.

![Tableau de bord des performances du réseau CDN](assets/cdn-performance-dashboard.png)

Pour plus d’informations sur les performances de votre réseau de diffusion de contenu et pour obtenir des suggestions sur la façon de l’améliorer, appuyez ou cliquez sur . **Afficher la tendance**.

![Tendance des performances](assets/cdn-performance-trend.png)

Appuyez ou cliquez sur **Affichage** sous le graphique pour modifier la période du graphique.

Pour obtenir des suggestions sur la façon d’améliorer les performances du réseau de diffusion de contenu, sélectionnez le **Recommendations** .

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
* **Miss** - Les données sont demandées par le cache, et elles sont introuvables.
* **Pass** - Les données sont demandées par le cache et sont définies pour ne pas les mettre en cache dans tous les cas.
* **Autre** - Toutes les requêtes de données du cache qui ne correspondent à aucun autre cas.

Les mesures du cache sont mises à jour toutes les 24 heures.

>[!TIP]
>
>Pour plus d’informations sur la façon dont Cloud Manager et le réseau de diffusion de contenu interagissent avec Dispatcher, consultez le document . [Mise en cache dans AEM as a Cloud Service.](/help/implementing/dispatcher/caching.md)
