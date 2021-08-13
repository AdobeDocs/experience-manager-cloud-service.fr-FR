---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.8.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.8.0
feature: Informations sur la version
exl-id: 42cc9cab-6e66-4976-a3b1-ecb9dbaaabf4
source-git-commit: d04194bd83ced844dffc94da35c996d363c5ba30
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 32%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.8.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.8.0.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.8.0 est le 12 août 2021.
La prochaine version est prévue pour le 9 septembre 2021.

### Nouveautés {#what-is-new}

* Les clients Cloud Service peuvent désormais afficher les rapports Contrat de niveau de service (SLA) dans Cloud Manager. Elle sera disponible progressivement au cours des prochains mois.
Voir [Rapports SLA](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html) pour en savoir plus.

* Le type et la gravité des règles de qualité IndexType et `IndexDamAssetLucene` ont été modifiés. Il s’agit désormais des deux bogues du bloqueur *serverity*.

* De nouvelles règles de qualité d’index Oak ont été introduites pour couvrir les configurations asynchrones et tika.

* Augmentez le nombre maximal de certificats SSL par programme à 50.

* Fonctionnalité de libre-service permettant aux utilisateurs de créer et de gérer plusieurs référentiels via l’interface utilisateur de Cloud Manager.

* SonarQube lisait inutilement les données de l’historique Git. Sur les bases de code volumineuses, cela peut entraîner une pénalité de performance de build inutile.

* Une API est désormais disponible pour invalider le cache de dépendance Maven par pipeline.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 29.

### Correctifs {#bug-fixes}

* Mettre à jour L’état Disponible ne doit pas s’afficher lorsque la dernière version est inférieure à la version actuelle.

* L’intégration initiale échouait pour les nouvelles organisations dont les noms étaient très longs.

* Parfois, lorsqu’un pipeline est déclenché deux fois pour une raison quelconque, l’une des exécutions échoue avec l’erreur *impossible de mettre à jour l’état d’exécution du pipeline*.


