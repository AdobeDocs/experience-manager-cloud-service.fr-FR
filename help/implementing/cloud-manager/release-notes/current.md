---
title: Notes de mise à jour de Cloud Manager 2023.5.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2023.5.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 4340b957cea86452f916ab615b383aabacc21676
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 41%

---


# Notes de mise à jour de Cloud Manager 2023.5.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2023.5.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de la version actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2023.5.0 de Cloud Manager dans AEM as a Cloud Service est le 11 mai 2023. La prochaine version est prévue pour le 8 juin 2023.

## Nouveautés {#what-is-new}

* La prise en charge des tests de produit, fonctionnels et de l’interface utilisateur a été étendue à [test de pipeline hors production.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
* En plus d’activer les tests en amont, [La prise en charge des tests de l’interface utilisateur a été étendue aux tests Cypress.](/help/implementing/cloud-manager/ui-testing.md)
* [Copie de contenu en libre-service](/help/implementing/developing/tools/content-copy.md) est désormais disponible d’un environnement supérieur à un environnement inférieur via l’interface utilisateur de Cloud Manager.
* L’étape de validation de l’exécution du pipeline a été améliorée afin de valider l’état des files d’attente de réplication plus tôt dans le processus d’exécution. Cela permet de s’assurer que les étapes de déploiement ne sont pas affectées par les files d’attente bloquées qui doivent être gérées par AEM utilisateurs administrateurs directement dans l’environnement de création.

## Correctifs {#bug-fixes}

* La création d’environnement n’échoue plus lorsque des caractères multi-octets sont utilisés dans le nom de l’environnement.
