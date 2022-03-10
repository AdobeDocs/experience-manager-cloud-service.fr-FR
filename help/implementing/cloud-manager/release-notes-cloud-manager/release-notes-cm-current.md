---
title: Notes de mise à jour de Cloud Manager 2022.3.0 dans Adobe Experience Manager as a Cloud Service
description: Il s’agit des notes de mise à jour de Cloud Manager 2022.3.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 428bba062fcfb44ebfbbf3c1d05ce1a4634fb429
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 2%

---


# Notes de mise à jour de Cloud Manager 2022.3.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page documente les notes de mise à jour de Cloud Manager 2022.3.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Voir [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

Date de publication de la version 2022.3.0 de Cloud Manager dans AEM as a Cloud Service 10 mars 2022. La prochaine version est prévue pour le 7 avril 2022.

## Nouveautés {#what-is-new}

* Un utilisateur avec la variable **Développeur** peut maintenant accéder au journal de l’environnement AEM.
* [Le `reliability_rating` mesure critique](/help/implementing/cloud-manager/code-quality-testing.md) a été désactivé.
* Un utilisateur peut désormais trier les colonnes de la variable **Pipelines** dans Cloud Manager.

## Correctifs {#bug-fixes}

* Un sous-ensemble de référentiels Git créés manuellement avait des valeurs de nom incorrectes qui affectaient [la fonction de réutilisation des artefacts de création.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) Les noms de ces référentiels ont été modifiés et les utilisateurs verront le nom corrigé dans l’API/interface utilisateur de Cloud Manager.
* [Lors de l’ajout ou de la modification d’un pipeline de qualité du code,](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) la valeur **Comportement des échecs de mesure importants** ne s’affichent plus.
* Les configurations de variable de pipeline inattendues ne provoquent plus d’erreurs lors de l’étape de création.
