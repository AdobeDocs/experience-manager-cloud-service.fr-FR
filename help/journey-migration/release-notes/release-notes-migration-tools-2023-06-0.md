---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.06.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.06.0
feature: Release Information
exl-id: 021b7472-d1e4-4ef6-a040-c612fed8d3c3
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 84%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.06.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2023.06.0.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v2.0.20 est le 8 juin 2023.

### Nouveautés {#what-is-new-ctt}

* Un nouvel outil de migration, le Transformateur de contenu (CT) a été intégré à l’outil de transfert de contenu (CTT) dans cette version. Le Transformateur de contenu peut détecter et corriger automatiquement les problèmes liés au contenu tels que signalés par l’[Analyseur des bonnes pratiques (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=fr) avant de migrer le contenu de votre mise en œuvre AEM actuelle (On-premise ou Managed Services) vers AEM as a Cloud Service.
Les avantages du Transformateur de contenu sont les suivants :
   * Sûr : un package est créé par le Transformateur de contenu chaque fois qu’il apporte une modification au référentiel pour résoudre les problèmes. Si nécessaire, vous pouvez revenir à l’état précédent en installant le package.
   * Facile à utiliser : le Transformateur de contenu a été intégré à l’outil de transfert de contenu et s’accompagne d’une interface utilisateur simple et intuitive.
   * Gagne du temps : lorsque vous rencontrez un grand nombre de problèmes de contenu qui relèvent d’une catégorie de modèle, vous pouvez tous les résoudre en plusieurs clics à l’aide du transformateur de contenu, ce qui réduit considérablement le temps et la complexité de la migration.
