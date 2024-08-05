---
title: Notes de mise à jour des outils de migration dans la version 2024.07 d’AEM as a Cloud Service
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2024.07.0
feature: Release Information
exl-id: 52709511-eab2-47a7-8bea-1b707cd568a1
role: Admin
source-git-commit: 4f01ca0076248442fe93161bbc8b98bffb64551b
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 34%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2024.07.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2024.07.0.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v3.0.16 est juillet 2024.

### Nouveautés {#what-is-new-ctt}

* Chargement automatique des logs d’extraction de CTT en cas d’échec.
* Les utilisateurs peuvent désormais effectuer l’ingestion avec succès lors du renouvellement de la clé d’extraction.
* Ajout de la prise en charge des extractions CTT à l’aide d’une clé d’accès Azure et d’une clé secrète avec AzureDataStore.
* Les utilisateurs recevront désormais le message d’erreur correct lorsqu’une clé non valide est utilisée pour créer un jeu de migration.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de la version 2.1.5 de l’analyseur des bonnes pratiques est mai 2024.

### Correctifs {#bug-fixes-bpa}

* L’analyseur des bonnes pratiques détecte désormais tous les noeuds de plus de 16 Mo.
* Les conditions de race causant la correction d&#39;occurrences non-conformistes.
