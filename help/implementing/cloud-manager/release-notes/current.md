---
title: Notes de mise à jour de Cloud Manager 2023.6.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2023.6.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: deef27dd90be22669b2328f6e394b8d3df99b4b9
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 33%

---


# Notes de mise à jour de Cloud Manager 2023.6.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2023.6.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de la version actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2023.6.0 de Cloud Manager dans AEM as a Cloud Service est le 8 juin 2023. La prochaine version est prévue pour le 6 juillet 2023.

## Nouveautés {#what-is-new}

* Les clients peuvent acheter d’autres régions de publication secondaires en plus de la région Principale, ce qui se traduit par des avantages liés à une latence réduite et à une disponibilité accrue. Remarque : Certaines restrictions peuvent s&#39;appliquer.
* Lors de la création d’une [programme ou environnement,](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) le nom est désormais limité à l’acceptation de caractères alphanumériques et d’un ensemble limité de caractères spéciaux.
* Lors de la reprise d’une [pipeline de production,](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) une boîte de dialogue de confirmation s’affiche maintenant à l’étape d’approbation.
* Pour le **[Tests fonctionnels du client](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)** et **[Tests de l’interface utilisateur personnalisée](/help/implementing/cloud-manager/ui-testing.md)** étapes de pipeline, nouvelle `INCOMPLETE` est désormais possible, ce qui indique que ces tests n’étaient pas présents et donc pas effectués.
   * Dans ce cas, le pipeline n’échoue pas et passe à l’étape suivante.

## Correctifs {#bug-fixes}

* Le [pipeline de configuration de niveau web](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) ne sont plus incorrectement activés pour les programmes Assets uniquement.
* Une validation plus robuste a été ajoutée pour empêcher certains types d’échecs lors de la mise en service de l’environnement.
