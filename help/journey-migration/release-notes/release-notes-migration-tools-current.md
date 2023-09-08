---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.09.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.09.0
feature: Release Information
source-git-commit: 9abce12c396ee74d36019218dd8b4fa72f762256
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 38%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.09.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.09.0.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v3.0.0 est le 7 septembre 2023.

### Nouveautés {#what-is-new-ctt}

L’outil de transfert de contenu a été considérablement amélioré pour offrir les avantages suivants :
* Réduction du temps de transfert lors de la migration d’un sous-ensemble d’un référentiel de contenu en utilisant AzCopy pour copier uniquement les identifiants d’objets Blob requis au lieu de copier tous les identifiants d’objets Blob.
* Compléments de contenu différentiels plus rapides à l’aide de la mise à niveau Oak
* Amélioration de la robustesse en séparant le processus d’indexation du processus d’ingestion de contenu. En cas d’échec de l’indexation, le contenu n’aura pas à être ingéré à nouveau. Seule l’indexation redémarre automatiquement, ce qui permet de gagner du temps et d’économiser des efforts significatifs.



