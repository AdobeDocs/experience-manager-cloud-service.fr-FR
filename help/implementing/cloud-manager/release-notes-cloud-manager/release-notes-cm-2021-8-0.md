---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.8.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.8.0
feature: Release Information
exl-id: cf1d5c4f-404a-4ced-90f2-273c710adc0f
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.8.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service 2021.8.0.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.8.0 est le 12 août 2021.

### Nouveautés {#what-is-new}

* Les clients Cloud Service peuvent désormais afficher les rapports de Contrat de niveau de service (SLA) dans Cloud Manager. Cette fonctionnalité sera disponible progressivement au cours des prochains mois.
Consultez [Rapport de SLA](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html?lang=fr) pour en savoir plus.

* Le type et la gravité de l’IndexType et des règles de qualité de `IndexDamAssetLucene` ont été modifiés. Ils sont maintenant tous deux répertoriés en tant que niveau de *sévérité* « bogues de blocage ».

* De nouvelles règles de qualité d’index Oak ont été introduites pour couvrir les configurations asynchrones et tika.

* Augmentez le nombre maximal de certificats SSL par programme à 50.

* Fonctionnalité de libre-service pour permettre aux utilisateurs de créer et de gérer plusieurs référentiels via l’interface utilisateur de Cloud Manager.

* SonarQube lisait inutilement les données de l’historique Git. Avec les bases de code volumineuses, cela pouvait entraîner une pénalité de performance de build inutile.

* Une API est désormais disponible pour invalider le cache de dépendance Maven par pipeline.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 29.

### Correctifs {#bug-fixes}

* Le statut Mise à jour disponible ne doit pas s’afficher lorsque la dernière version est inférieure à la version présente.

* L’intégration initiale échouait pour les nouvelles organisations dont les noms étaient très longs.

* Parfois, lorsqu’un pipeline est déclenché deux fois pour une raison quelconque, l’une ou l’autre des exécutions échoue avec l’erreur *Impossible de mettre à jour l’état d’exécution du pipeline*.
