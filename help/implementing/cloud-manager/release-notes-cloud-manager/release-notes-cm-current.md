---
title: Notes de mise à jour de Cloud Manager 2023.1.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2024.1.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 5aabdf22a040a031a3fa2a1a9f70247cf2e38f2e
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 36%

---


# Notes de mise à jour de Cloud Manager 2023.1.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page documente les notes de mise à jour de la version 2023.1.0 de Cloud Manager en AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de la version actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2023.1.0 de Cloud Manager dans AEM as a Cloud Service est le 19 janvier 2023. La prochaine version est prévue pour le 16 février 2023.

## Nouveautés {#what-is-new}

* Des améliorations ont été apportées à la convivialité en mettant à jour les styles de curseur qui font la distinction entre l’action des utilisateurs et le pointeur par défaut.

* Les rapports de test de l’interface utilisateur personnalisée sont désormais copiés dans le stockage Cloud Manager et sont accessibles via l’appel de l’API Cloud Manager.

* Les utilisateurs peuvent désormais effectuer une transition entre les états du widget d’activation à l’aide des flèches gauche-droite.

   ![Transitions du widget d’activation](assets/go-live-transitions.gif)

* Libre-service [création de programmes compatibles avec HIPAA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) est désormais possible lorsque les droits et autorisations correspondants sont disponibles.

## Correctifs {#bug-fixes}

* Cloud Manager empêche deux exécutions de pipeline de commencer (ou presque) en même temps, évitant ainsi les échecs de pipeline.
