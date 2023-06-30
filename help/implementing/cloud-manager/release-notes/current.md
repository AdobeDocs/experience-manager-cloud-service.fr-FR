---
title: Notes de mise à jour de Cloud Manager 2023.7.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2023.7.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 1b46f763903a1b103837ed7e8cc498ad08ce64f1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 29%

---


# Notes de mise à jour de Cloud Manager 2023.7.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2023.7.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Voir [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2023.7.0 de Cloud Manager dans AEM as a Cloud Service est le 29 juin 2023. La prochaine version est prévue pour le 10 août 2023.

## Nouveautés {#what-is-new}

* Les cartes de la page d’entrée de Cloud Manager indiquent désormais si [sécurité renforcée](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) est activé pour leurs programmes.
* Si un développement [pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) ne contient aucune étape de test, les utilisateurs ont désormais la possibilité d’inclure des étapes de test lorsqu’ils [démarrez le pipeline.](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines)
   * Ce processus sera mis en oeuvre par étapes.
* When [annulation de l&#39;exécution,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) l’étape de validation de l’exécution du pipeline demande maintenant à l’utilisateur de fournir une raison d’annuler.
   * Ce processus sera mis en oeuvre par étapes.

## Correctifs {#bug-fixes}

* L’accès à l’interface utilisateur de création à partir de Cloud Manager n’échoue plus à rediriger vers le Shell unifié après connexion.
* La modification de la date d’activation via le widget d’activation permet désormais d’accéder au **Go Live** au lieu de l’onglet **Sécurité renforcée** .
* Lors du démarrage d’une opération de copie, un utilisateur ne pourra plus sélectionner un environnement dans lequel une opération de copie est déjà appelée.
