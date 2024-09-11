---
title: Notes de mise à jour des outils de migration dans la version 2024.09 d’AEM as a Cloud Service
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2024.09.0
feature: Release Information
exl-id: 52709511-eab2-47a7-8bea-1b707cd568a1
role: Admin
source-git-commit: 0c16f264826a46907afc33c91a021e7696f5b7a8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 27%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2024.09.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2024.09.0.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v3.0.20 est le 28 août 2024.

### Nouveautés {#what-is-new-ctt}

* Les utilisateurs ne seront plus ingérés dans cette version et, pour cette raison, la fonctionnalité facultative Mappage d’utilisateurs a été supprimée.
* Une option de configuration OSGI a été ajoutée pour désactiver ou activer la migration des entités lors de l’extraction et de l’ingestion (le paramètre par défaut est de l’activer).

### Correctifs {#bug-fixes-ctt}

* CTT a été amélioré afin d’éviter une erreur lors de la non-protection d’une clé secrète dans la configuration azcopy.
* CTT gère désormais avec élégance toute erreur lors de la copie des journaux AzCopy dans la phase de validation.
* Modification du répertoire du journal azcopy créé lors du processus d’extraction

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de la version 2.1.5 de l’analyseur des bonnes pratiques est le 4 septembre 2024.

### Nouveautés {#what-is-new-bpa}

* Un nouveau modèle a été introduit pour détecter les événements basés sur JCR dans AEM

### Correctifs {#bug-fixes-bpa}

* Correction de faux positifs
* Amélioration de la robustesse pour gérer la réponse redirigée du Dispatcher.
* Correction d’un problème de non-reporting du résultat NCC pour toutes les langues sous /apps/wcm/core/resources/languages/
* ajout d’une vérification pour détecter si une propriété multiple d’un noeud ne comporte aucune valeur

