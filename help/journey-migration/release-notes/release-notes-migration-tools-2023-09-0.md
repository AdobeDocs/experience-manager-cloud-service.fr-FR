---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.09.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.09.0
feature: Release Information
exl-id: 484a60d4-a439-43d6-a23e-4a3b45ef4160
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 42%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.09.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2023.09.0.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v3.0.0 est le 7 septembre 2023.

### Nouveautés {#what-is-new-ctt}

L’outil de transfert de contenu a été amélioré pour offrir les avantages suivants :

* Réduction du temps de transfert lors de la migration d’un sous-ensemble d’un référentiel de contenu en utilisant AzCopy pour copier uniquement les identifiants d’objet Blob requis au lieu de copier tous les identifiants d’objet Blob.
* Compléments de contenu différentiels plus rapides à l’aide de la mise à niveau Oak.
* Amélioration de la robustesse en séparant le processus d’indexation du processus d’ingestion de contenu. En cas d’échec de l’indexation, le contenu n’a pas à être ingéré à nouveau. Seule l’indexation redémarre automatiquement, ce qui permet de gagner du temps et de faire des efforts significatifs.
