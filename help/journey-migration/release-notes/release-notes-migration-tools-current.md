---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.6.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.6.0
feature: Release Information
source-git-commit: 666635fc951ceb10e1a4a9a90a042d60da9f463a
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 23%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.6.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.6.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur des bonnes pratiques v2.1.30 est le 1 juin 2022.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur l’utilisation des widgets de boîte de dialogue personnalisés à l’aide des widgets CoralUI et Classic. Il est recommandé de convertir les widgets de boîte de dialogue Classic personnalisés d’ExtJS en CoralUI. Les widgets de boîte de dialogue Coral personnalisés doivent être mis à jour vers CoralUI3.
* Possibilité de détecter et de générer des rapports sur l’utilisation et la version d’Assets Share Commons. Asset Share Commons 1.x n’est pas pris en charge sur AEM as a Cloud Service et doit être mis à niveau vers la version 2.x.
* Possibilité de détecter et de générer des rapports sur le nombre de noeuds des versions.
* Possibilité de détecter et de générer des rapports sur les agents de réplication personnalisés ou les agents de réplication prêts à l’emploi qui ont été modifiés.

### Correctifs {#bug-fixes-bpa}

* BPA signalait les résultats NCC (modifications non compatibles), UMI (problème de configuration de mise à niveau) et PCX (complexité de page) qui sont des faux positifs. Ils ont été corrigés.
* BPA signalait des échecs lorsqu’une longueur de nom de noeud dépassait 150 octets. Ce problème a été corrigé afin de détecter ces échecs uniquement lorsque le chemin d’accès parent du noeud est égal ou supérieur à 350 octets.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v2.0.10 est le 2 juin 2022.

### Nouveautés {#what-is-new-ctt}

* L’outil de transfert de contenu (CTT) a été développé pour travailler avec Cloud Acceleration Manager afin de rationaliser l’ensemble du processus de transfert de contenu. Le CTT se concentre désormais sur l’exécution d’extractions de contenu. Le service d’ingestion CTT est désormais intégré à Cloud Acceleration Manager. Les avantages offerts par cette évolution sont les suivants :
   * Méthode en libre-service pour extraire une fois un jeu de migration et l’ingérer dans plusieurs environnements en parallèle.
   * Amélioration de l’expérience utilisateur grâce à une meilleure gestion des états de chargement, des barrières de sécurité et des erreurs.
   * Les journaux d’ingestion sont conservés et sont toujours disponibles pour le dépannage.

## Cloud Acceleration Manager {#cam-release}

### Date de publication {#release-date-cam}

La date de publication de Cloud Acceleration Manager est le 2 juin 2022.

### Nouveautés {#what-is-new-cam}

* Cloud Acceleration Manager permet désormais aux utilisateurs de démarrer et de gérer les transferts de contenu afin de déplacer le contenu d’une instance AEM client (On-Premise ou Adobe Managed Services) vers AEM as a Cloud Service dans le cadre d’un projet de migration. Voir [Utilisation de la carte de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html#content-transfer) pour plus d’informations.
