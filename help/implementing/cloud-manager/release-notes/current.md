---
title: Notes de mise à jour de Cloud Manager 2024.9.0 dans Adobe Experience Manager as a Cloud Service
description: Découvrez les notes de mise à jour de Cloud Manager 2024.9.0 dans AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 610ae004b6da2f7fc0dae2baa613cb363fe9fb00
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 20%

---

# Notes de mise à jour de Cloud Manager 2024.9.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2024.9.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Voir les [notes de mise à jour actuelles pour Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Date de publication {#release-date}

La date de publication de Cloud Manager version 2024.9.0 dans AEM as a Cloud Service est le vendredi 5 septembre 2024. La prochaine version est prévue pour le vendredi 3 octobre 2024.

## Nouveautés {#what-is-new}

* **Tableau de bord du contrôle de l’expérience :**

  Le [ tableau de bord amélioré du contrôle de l’expérience ](/help/implementing/cloud-manager/experience-audit-dashboard.md) d’Adobe Cloud Manager, optimisé par Google Lighthouse, permet d’obtenir des informations sur la qualité et les performances d’AEM Sites en évaluant les principales mesures de performances web, d’optimisation pour les moteurs de recherche et d’accessibilité. Il permet aux utilisateurs d’identifier les domaines à améliorer en leur offrant des recommandations pratiques, ce qui permet aux équipes d’améliorer l’expérience utilisateur, les temps de chargement des pages et la conformité au site. Ce tableau de bord simplifie la surveillance des mesures critiques du site et garantit que les applications AEM répondent aux normes de performances et d’accessibilité élevées.

* **Adobe des certificats de validation de domaine générés et gérés :**

  Avec Cloud Manager, vous pouvez désormais [ certificats SSL DV (Domain Validation) générés et gérés par l’Adobe libre-service ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). Cette fonctionnalité vous offre la solution la plus rapide, la plus simple et la plus économique pour créer un site web sécurisé pour votre entreprise ou organisation en ligne. <!-- CMGR-52403 -->

  >[!NOTE]
  >
  >Les clients de [Content Hub](/help/assets/product-overview.md) doivent recevoir cette fonctionnalité par phases dans le cadre d’un déploiement progressif.

* **Prise en charge des Edge Delivery Services dans Cloud Manager :**

  Si vous possédez une licence Edge Delivery Services dans le cadre d’AEM Sites, [vous pouvez désormais embarquer sur votre site avec des Edge Delivery Services directement via Cloud Manager](/help/implementing/cloud-manager/edge-delivery-services.md). Cette fonctionnalité permet une expérience d’activation en libre-service et guidée. Il unifie également les processus essentiels tels que la gestion des noms de domaine, les certificats SSL et les mappages CDN sur toutes vos propriétés AEM, assurant ainsi cohérence et efficacité. <!-- CMGR-49859 -->

  >[!NOTE]
  >
  >Les clients de [Content Hub](/help/assets/product-overview.md) doivent recevoir cette fonctionnalité par phases dans le cadre d’un déploiement progressif.

* Les clients qui utilisent des référentiels GitHub peuvent désormais créer et utiliser des pipelines de configuration de niveau web. <!--( KEEP IN? SP: YES CMGR-59046 and Slack https://cq-dev.slack.com/archives/C07LFP5BZ2L/p1725407057847379 ) -->

<!--
## Early adoption program {#early-adoption}

For a chance to test some upcoming features, be a part of Adobe's early adoption program. -->


## Correctifs

* La pagination pour la vue de tableau des certificats SSL fonctionne désormais comme prévu. <!-- (CMGR-60804 - [UI] Pagination doesn't work for ssl certificates) -->
* La version d’artefact incorrecte a été promue lors de l’utilisation du bouton **Convertir le build** à partir d’une exécution. <!-- ( KEEP IN? SP: YES CMGR-59519 and Slack https://cq-dev.slack.com/archives/C07LFPN2R08/p1725408253474129 ) -->

<!-- * Slack message says next release? SP: REMOVE (Leave in for now) SSL Certificates table in Cloud Manager now enables pagination in the user experience. ( https://jira.corp.adobe.com/browse/CMGR-61041 and Slack https://cq-dev.slack.com/archives/C07LFRE9QJU/p1725408553760009 ) --<>
