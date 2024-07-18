---
title: Notes de mise à jour de Cloud Manager 2024.7.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2024.7.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
role: Admin
source-git-commit: a5cd55bcdc6044dd8db26f009b955216cda5daee
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 58%

---


# Notes de mise à jour de Cloud Manager 2024.7.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2024.7.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2024.7.0 de Cloud Manager dans AEM as a Cloud Service est le 18 juillet 2024. La prochaine version est prévue pour le 8 août 2024.

## Nouveautés {#what-is-new}

* Le [pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline) et le [pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline) déclenchent **Lors des modifications Git** pour démarrer le pipeline sur une validation est désormais disponible pour les [référentiels privés.](/help/implementing/cloud-manager/managing-code/private-repositories.md)
   * Ce processus sera mis en oeuvre progressivement et sera achevé d&#39;ici la mi-août.
* Lors de l’ajout d’un certificat DV [géré par l’Adobe,](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) vous pouvez désormais ajouter un seul certificat qui couvre plusieurs domaines au lieu de créer un certificat pour chaque domaine.
* Les solutions qui n’ont pas [d’autres régions de publication](/help/operations/additional-publish-regions.md) peuvent désormais être ajoutées à un programme tant que le programme comporte au moins une solution Sites ou Forms qui s’y applique.
* Les solutions qui n’ont pas [99,99 % SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla) peuvent désormais être ajoutées à un programme tant que le programme comporte au moins une solution Sites ou Forms s’y applique.
* Le [tableau de bord du contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-dashboard.md) a été amélioré de plusieurs façons.
   * Les audits s&#39;exécutent désormais sur les points de terminaison `.com` via CDN, en remplaçant l&#39;approche précédente de `.net`.
      * Ce changement simule plus précisément les expériences utilisateur réelles et vous permet de prendre des décisions plus éclairées concernant la gestion et l’optimisation de votre site web.
   * Plusieurs améliorations ont été apportées à l’interface utilisateur du contrôle de l’expérience, notamment :
      * Ajout d’une vue de tendance des performances, des bonnes pratiques, de l’optimisation pour les moteurs de recherche et de l’accessibilité.
      * Le lien du rapport brut Lighthouse est désormais visible de manière plus intuitive, directement dans le panneau des détails des instantanés d’analyse.
      * La section Recommandations pour Lighthouse a été améliorée.
   * La mesure du PWA a été supprimée conformément à la version 12.0.0 de Lighthouse, ce qui a éliminé cette mesure.

## Programme d’adoption précoce {#early-adoption}

Pour avoir la possibilité de tester certaines fonctionnalités à venir, participez au programme d’adoption précoce d’Adobe.

### Assistance Edge Delivery Services dans Cloud Manager {#edge-delivery-services}

Si vous disposez d’Edge Delivery Services sous licence avec Adobe Experience Manager Sites, [vous pouvez désormais créer votre site avec Edge Delivery Services directement dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery-services.md) et publier à l’aide d’une expérience guidée en libre-service.

Vous bénéficiez ainsi d’une expérience unifiée pour toutes vos propriétés AEM, ce qui garantit la cohérence avec tous les workflows critiques, notamment la gestion des noms de domaine, la gestion des certificats SSL et les mappages CDN.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `aemcs-cmedgedelsvs-program-adopter@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.

### Certificats de domaine validés (DV)

Cloud Manager vous permet désormais de [générer et gérer en libre-service des certificats SSL (DV) validés par domaine.](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) Vous bénéficiez ainsi de la solution la plus rapide, la plus simple et la plus économique pour créer un site web sécurisé destiné à votre entreprise en ligne.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `Grp-aemcs-dv-dert-adopter@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.

### Tableau de bord d’audit de l’expérience {#experience-audit-dashboard}

[Le tableau de bord d’audit de l’expérience de Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) inclut une vue de tendance des scores de performances de votre page, ainsi que des informations et des recommandations pour vous aider à les améliorer. L’audit de l’expérience est inclus en tant qu’étape dans le pipeline de production de Cloud Manager.

Le tableau de bord tire parti de Google Lighthouse, un outil automatisé et open source permettant d’améliorer la qualité de vos applications web. Vous pouvez l’exécuter sur n’importe quelle page web, publique ou nécessitant une authentification. Il comporte des audits des performances, de l’accessibilité, des applications web progressives, de l’optimisation du moteur de recherche et plus encore.

Vous souhaitez tester le nouveau tableau de bord ? Pour commencer, envoyez un e-mail à l’adresse `aem-lighthouse-pilot@adobe.com` à partir de votre adresse e-mail associée à votre Adobe ID.
