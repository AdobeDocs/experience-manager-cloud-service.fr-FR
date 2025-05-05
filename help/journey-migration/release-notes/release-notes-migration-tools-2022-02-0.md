---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.2.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.2.0
feature: Release Information
exl-id: b1cd871d-c71e-4902-a97e-2c859f6a4da4
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 83%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.2.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.2.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.24 est le 1er février 2022.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur le nombre de ressources avec et sans balises intelligentes.
* Possibilité de détecter et de générer des rapports sur la version de composant principal couramment utilisée.
* Possibilité de détecter et de générer des rapports sur le type de niveau source (création ou publication) où l’analyseur de bonne pratique a été exécuté.

### Correctifs {#bug-fixes-bpa}

* La logique de dimensionnement de l’analyseur de bonne pratique a été rendue plus rapide et plus efficace.
* Dans certains scénarios, l’analyseur de bonne pratique n’incrémentait pas le nombre analysé lors de son exécution. Ce problème a été résolu.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.8.6 est le 03 février 2022.

### Nouveautés {#what-is-new-ctt}

* Validation du contenu : les utilisateurs peuvent déterminer de manière fiable si tout le contenu extrait par l’outil de transfert de contenu a bien été ingéré dans l’instance cible. Pour utiliser cette fonctionnalité, activez-la dans l’ `System Console` de l’environnement d’AEM source. Consultez [Validation des transferts de contenu - Prise en main](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=fr#getting-started) pour plus d’informations.

### Correctifs {#bug-fixes-ctt}

* Certains utilisateurs n’étaient pas mappés, car le mappage des utilisateurs était sensible à la casse. Ce problème a été résolu. Le mappage utilisateur n’est plus sensible à la casse.
