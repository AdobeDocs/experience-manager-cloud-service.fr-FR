---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.5.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.5.0
feature: Release Information
exl-id: 1aa49e85-1914-44d9-bcf7-0a1b03926df0
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 97%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.5.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.5.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur des bonnes pratiques v2.1.30 est le 1 juin 2022.

### Nouveautés {#what-is-new-bpa}

* La possibilité de détecter et de générer des rapports sur l’utilisation des widgets de boîte de dialogue personnalisés à l’aide des widgets CoralUI et Classic. Il est recommandé de convertir les widgets de boîte de dialogue Classic personnalisés ExtJS en CoralUI. Les widgets de boîte de dialogue Coral personnalisés doivent être mis à jour vers CoralUI3.
* La possibilité de détecter et de générer des rapports sur l’utilisation et la version d’Assets Share Commons. Asset Share Commons 1.x n’est pas pris en charge sur AEM as a Cloud Service et doit être mis à niveau vers la version 2.x.
* La possibilité de détecter et de générer des rapports sur le nombre de nœuds des versions.
* La possibilité de détecter et de générer des rapports sur les agents de réplication personnalisés ou les agents de réplication prêts à l’emploi qui ont été modifiés.

### Correctifs {#bug-fixes-bpa}

* L’analyseur de bonnes pratiques signalait les résultats NCC (modifications non compatibles), UMI (problème de configuration de mise à niveau) et PCX (complexité de page) qui se révélaient être des faux positifs. Ces erreurs ont été corrigées.
* L’analyseur de bonnes pratiques signalait des échecs lorsqu’une longueur de nom de nœud dépassait 150 octets. Ce problème a été corrigé afin de détecter ces échecs uniquement lorsque le chemin d’accès parent du nœud est égal ou supérieur à 350 octets.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v2.0.10 est le 2 juin 2022.

### Nouveautés {#what-is-new-ctt}

* L’outil de transfert de contenu (CTT) a été développé pour travailler avec Cloud Acceleration Manager afin de rationaliser l’ensemble du processus de transfert de contenu. Le CTT se concentre désormais sur l’exécution d’extractions de contenu. Le service d’ingestion CTT est désormais intégré à Cloud Acceleration Manager. Les avantages offerts par cette évolution sont les suivants :
   * Une méthode en libre-service pour extraire une fois un jeu de migration et l’ingérer dans plusieurs environnements en parallèle
   * L’amélioration de l’expérience utilisateur grâce à une meilleure gestion des statuts de chargement, des barrières de sécurité et des erreurs
   * La conservation des journaux d’ingestion et leur constante disponibilité à des fins de dépannage

## Cloud Acceleration Manager {#cam-release}

### Date de publication {#release-date-cam}

La date de publication de Cloud Acceleration Manager est le 2 juin 2022.

### Nouveautés {#what-is-new-cam}

* Cloud Acceleration Manager permet désormais aux utilisateurs et utilisatrices de démarrer et de gérer les transferts de contenu afin de déplacer le contenu de l’instance AEM d’un(e) client(e) (On-Premise ou Adobe Managed Services) vers AEM as a Cloud Service dans le cadre d’un projet de migration. Voir [Utilisation de la carte de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=fr#content-transfer) pour plus d’informations.
