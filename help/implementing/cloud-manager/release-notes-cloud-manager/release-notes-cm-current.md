---
title: Notes de mise à jour de Cloud Manager 2022.12.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2022.12.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: aa7f2175e2a43a318a6171e622d292ed3a8e958b
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 38%

---


# Notes de mise à jour de Cloud Manager 2022.12.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager 2022.12.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de la version actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2022.12.0 de Cloud Manager dans AEM as a Cloud Service est le 29 novembre 2022. La prochaine version est prévue pour le 19 janvier 2023.

## Nouveautés {#what-is-new}

* Notifications pour [Mises à jour de maintenance AEM](/help/overview/what-is-new-and-different.md#aem-updates) apparaît dans l’interface utilisateur de Cloud Manager. Cette modification sera introduite progressivement dans les semaines qui suivront la version 2022.12.0.
* Lorsqu’une ingestion via la variable [Outil de transfert de contenu (CTT)](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md) est en cours, l’état de l’environnement dans Developer Console et dans Cloud Manager s’affiche comme `Ingestion in Progress`.
* Amélioration de la disponibilité et de la fiabilité de [Pipelines Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) ont été faites.

## Correctifs {#bug-fixes}

* Une modification a été apportée pour empêcher [pipelines front-end](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) de s’exécuter pendant l’exécution d’un pipeline sur le même environnement.
* Une modification a été apportée pour empêcher une `PATCH /program//environment//variables` requête pour les environnements avec la propriété `FAILED` statut.
