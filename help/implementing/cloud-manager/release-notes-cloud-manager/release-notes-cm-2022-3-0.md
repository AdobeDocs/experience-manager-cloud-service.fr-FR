---
title: Notes de mise à jour de Cloud Manager 2022.3.0 dans Adobe Experience Manager as a Cloud Service
description: Il s’agit des notes de mise à jour de Cloud Manager 2022.3.0 dans AEM as a Cloud Service.
feature: Release Information
source-git-commit: 437be8c82a4dee6c9e56af09afa7e9048c8cb3c0
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 58%

---


# Notes de mise à jour de Cloud Manager 2022.3.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page documente les notes de mise à jour de Cloud Manager 2022.3.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de la version actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

Date de publication de la version 2022.3.0 de Cloud Manager dans AEM as a Cloud Service 10 mars 2022. La prochaine version est prévue pour le 7 avril 2022.

## Nouveautés {#what-is-new}

* Vous pouvez accéder au journal AEM environnement à l’aide du rôle Développeur .

## Correctifs {#bug-fixes}

* Un sous-ensemble de référentiels Git créés manuellement avait une valeur de nom incorrecte qui empêchait la fonction de réutilisation des artefacts de build d’être efficace. Les noms de ces référentiels ont été modifiés et les utilisateurs verront le nom corrigé dans l’API/interface utilisateur de Cloud Manager.
* Les artefacts de build des pipelines hors production ont été réutilisés de manière inappropriée sur les pipelines de production de pile pleine.
* Lors de l’ajout ou de la modification d’un pipeline de qualité du code, les options permettant de gérer les échecs de mesures ne s’affichent plus.
* Certaines configurations de variable de pipeline inattendues peuvent se présenter dans l’étape de création.
