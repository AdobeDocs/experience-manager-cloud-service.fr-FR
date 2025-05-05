---
title: Notes de mise à jour des outils de migration dans AEM as a Cloud Service version 2021.11.0
description: Notes de mise à jour des outils de migration dans AEM as a Cloud Service version 2021.11.0
feature: Release Information
exl-id: 668c0c66-88f5-4d74-9a2a-3bdc63b0bba7
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 87%

---

# Notes de mise à jour des outils de migration dans AEM as a Cloud Service version 2021.11.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2021.11.0.

>[!NOTE]
>
>Voir [Notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md) pour consulter les dernières notes de mise à jour.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.7.2 est le 01 novembre 2021.

### Nouveautés {#what-is-new-ctt}

* Prise en charge d’une étape facultative de [pré-copie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr) ajoutée à utiliser avec l’outil de transfert de contenu lorsque l’instance AEM source est configurée pour utiliser le File Data Store afin d’accélérer considérablement la phase d’extraction.

* Ajout de messages descriptifs supplémentaires à la phase d’ingestion dans l’interface utilisateur de l’outil de transfert de contenu pour indiquer le moment où les étapes d’indexation et de récupération Mongo sont en cours.
