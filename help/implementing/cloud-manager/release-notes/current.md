---
title: Notes de mise à jour de Cloud Manager 2024.8.0 dans Adobe Experience Manager as a Cloud Service
description: Découvrez les notes de mise à jour de Cloud Manager 2024.8.0 dans AEM as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: bf8bab5a195dde6cf15a2fd52e51d58c0215fdf3
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 31%

---


# Notes de mise à jour de Cloud Manager 2024.8.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2024.8.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de Cloud Manager version 2024.8.0 dans AEM as a Cloud Service était le mardi 12 août 2024. La prochaine version est prévue pour le 9 septembre 2021.

## Nouveautés {#what-is-new}

* [D’autres régions de publication ](/help/operations/additional-publish-regions.md) et une [SLA 99,99 %](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla) (contrat de niveau de service) sont désormais disponibles pour AEM Forms as a Cloud Service.
   * Cette amélioration vous permet d’obtenir des contrats de niveau de service plus élevés avec une disponibilité accrue et une latence inférieure, ce qui garantit des expériences de qualité optimale à vos utilisateurs répartis dans le monde entier.

## Programme d&#39;adoption précoce {#early-adoption}

Pour avoir la possibilité de tester certaines fonctionnalités à venir, participez au programme d’adoption précoce d’Adobe.

### Prise en charge des Edge Delivery Services dans Cloud Manager {#edge-delivery-services}

Si vous possédez des Edge Delivery Services sous licence dans AEM Sites, [vous pouvez désormais embarquer sur votre site avec des Edge Delivery Services directement dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery-services.md) et passer en direct à l’aide d’une expérience de libre-service guidée.

Cette fonctionnalité offre une expérience unifiée pour toutes vos propriétés AEM. Il assure la cohérence entre les workflows critiques tels que la gestion des noms de domaine, la gestion des certificats SSL et les mappages CDN.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un email à `aemcs-cmedgedelsvs-program-adopter@adobe.com` à partir de l’adresse email associée à votre Adobe ID.

### Certificats DV (Domain Validated)

Avec Cloud Manager, vous pouvez désormais [générer et gérer en libre-service des certificats SSL (DV) validés par domaine](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md). Cette fonctionnalité vous offre la solution la plus rapide, la plus simple et la plus économique pour créer un site web sécurisé pour votre entreprise en ligne.

Si vous souhaitez tester cette nouvelle fonctionnalité et fournir vos commentaires, envoyez un email à `Grp-aemcs-dv-dert-adopter@adobe.com` à l&#39;aide de l&#39;adresse email liée à votre Adobe ID.

### Tableau de bord d’audit de l’expérience {#experience-audit-dashboard}

[Le tableau de bord d’audit de l’expérience de Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) inclut une vue de tendance des scores de performances de votre page, ainsi que des informations et des recommandations pour vous aider à les améliorer. L’audit de l’expérience est inclus en tant qu’étape dans le pipeline de production de Cloud Manager.

Le tableau de bord tire parti de Google Lighthouse, un outil automatisé et open source permettant d’améliorer la qualité de vos applications web. Vous pouvez l’utiliser pour contrôler n’importe quelle page web, qu’elle soit publique ou nécessitant une authentification. Il fournit des évaluations des performances, de l’accessibilité, des applications web progressives, de l’optimisation pour les moteurs de recherche, etc.

Vous êtes curieux d&#39;essayer le nouveau tableau de bord ? Pour commencer, envoyez un email à `aem-lighthouse-pilot@adobe.com` à l’aide de l’e-mail lié à votre Adobe ID.

## Bug Fix

* Correction d’un rare problème en raison duquel les étapes de pipeline s’exécutaient après la suppression du pipeline.
* Correction d’un problème en raison duquel les pipelines de configuration affichaient incorrectement l’état `FAILED` dans de rares cas.
