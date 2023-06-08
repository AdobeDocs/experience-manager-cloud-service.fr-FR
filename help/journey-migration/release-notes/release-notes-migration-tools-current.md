---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.06.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.06.0
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
source-git-commit: a1597e4102589dfc9b5bdb8c2a54e8e9ec3392b7
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 33%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.06.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.06.0.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v2.0.20 est le 08 juin 2023.

### Nouveautés {#what-is-new-ctt}

* Un nouvel outil de migration - Content Transformer (CT) a été intégré à l’outil de transfert de contenu (CTT) avec cette version. Le transformateur de contenu peut automatiquement détecter et corriger les problèmes liés au contenu signalés par [Analyseur des bonnes pratiques (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=fr) avant de migrer le contenu de votre mise en oeuvre AEM actuelle (On-premise ou Managed Services) vers AEM as a Cloud Service.
Les avantages du transformateur de contenu sont les suivants :
   * Fail-safe : un package est créé par Content Transformer chaque fois qu’il apporte une modification au référentiel pour résoudre les problèmes. Si nécessaire, vous pouvez revenir à l’état précédent en installant le package.
   * Faciles à utiliser : Content Transformer a été intégré à l’outil de transfert de contenu et s’accompagne d’une interface utilisateur simple et intuitive.
   * Gagne du temps : lorsque vous rencontrez un grand nombre de problèmes de contenu appartenant à une catégorie de modèle, vous pouvez tous les résoudre en quelques clics seulement à l’aide du transformateur de contenu, ce qui réduit considérablement le temps et la complexité de migration.
