---
title: Notes de mise à jour des outils de migration dans AEM version as a Cloud Service 2022.2.0
description: Notes de mise à jour des outils de migration dans AEM version as a Cloud Service 2022.2.0
feature: Release Information
exl-id: b1cd871d-c71e-4902-a97e-2c859f6a4da4
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 18%

---

# Notes de mise à jour des outils de migration dans AEM version as a Cloud Service 2022.2.0 {#release-notes}

Cette page présente les notes de mise à jour des outils de migration dans AEM as a Cloud Service 2022.2.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.24 est le 01 février 2022.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur le nombre de ressources avec et sans balises intelligentes.
* Possibilité de détecter et de générer des rapports sur la version du composant principal utilisé.
* Possibilité de détecter et de générer des rapports sur le type de niveau source (auteur ou publication) où l’application d’une seule page a été exécutée.

### Correctifs {#bug-fixes-bpa}

* La logique de dimensionnement des BPA a été rendue plus rapide et plus efficace.
* Dans certains scénarios, BPA n’incrémentait pas le nombre analysé lors de son exécution. Ce problème a été résolu.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.8.6 est le 03 février 2022.

### Nouveautés {#what-is-new-ctt}

* Validation du contenu : les utilisateurs peuvent déterminer de manière fiable si tout le contenu extrait par l’outil de transfert de contenu a bien été ingéré dans l’instance cible. Pour utiliser cette fonctionnalité, vous devez l’activer dans la variable `System Console` de l’environnement d’AEM source. Voir [Validation des transferts de contenu - Prise en main](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=en#getting-started) pour plus d’informations.

### Correctifs {#bug-fixes-ctt}

* Certains utilisateurs n’étaient pas mappés, car le mappage des utilisateurs était sensible à la casse. Ce problème a été résolu. Le mappage utilisateur n’est plus sensible à la casse.
