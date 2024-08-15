---
title: Notes de mise à jour des outils de migration dans AEM as a Cloud Service version 2021.10.0
description: Notes de mise à jour des outils de migration dans AEM as a Cloud Service version 2021.11.0
feature: Release Information
exl-id: 6b1caa63-dcb0-4c48-ab2c-fd72617abf13
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 94%

---

# Notes de mise à jour des outils de migration dans AEM as a Cloud Service version 2021.10.0 {#release-notes}

Cette page présente les notes de mise à jour des outils de migration dans AEM as a Cloud Service version 2021.10.0.

>[!NOTE]
>
>Voir [Notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md) pour consulter les dernières notes de mise à jour.

## Cloud Acceleration Manager {#cam-release}

### Date de publication {#release-date-cam}

La date de publication de Cloud Acceleration Manager est le 25 octobre 2021.

### Nouveautés {#what-is-new-cam}

Cloud Acceleration Manager permet désormais aux utilisateurs de visualiser les rapports historiques BPA dans un rapport de tendance. Grâce à ce rapport, les utilisateurs peuvent visualiser les progrès quʼils réalisent sous la forme dʼune représentation graphique facile à utiliser. Consultez la section [Utilisation de lʼoption Afficher la courbe de tendance](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html#trendline-view-cam) pour plus d’informations.

### Date de publication {#release-date-october-cam}

La date de publication de la mise à jour de Cloud Acceleration Manager est le 4 octobre 2021.

### Nouveautés {#what-is-new-cam-oct}

Cloud Acceleration Manager permet désormais aux utilisateurs d’afficher les rapports BPA dans un aperçu imprimable, ce qui permet d’exécuter simplement une impression ou une exportation PDF pour les partager facilement. Consultez les étapes 6 et 7 de la section [Utilisation de la carte d’analyse des bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html#best-practices-analysis).


## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu version v1.6.0 est le 4 octobre 2021.

### Nouveautés {#what-is-new-ctt-oct}

* Amélioration de l’outil de mappage des utilisateurs pour une expérience utilisateur simplifiée, notamment grâce aux fonctionnalités suivantes répertoriées ci-dessous. Pour plus d’informations, consultez la section [Utilisation de l’outil de mappage des utilisateurs et utilisatrices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html).
   * Test de la connexion à l’API User Management avant d’exécuter le mappage des utilisateurs
   * Ignorer les erreurs de manière appropriée et poursuivre l’activité de mappage des utilisateurs
   * Le mappage des utilisateurs n’échoue plus si le **Jeton d’accès** expire après 24 heures. Le mappage des utilisateurs et des utilisatrices peut être exécuté à nouveau à partir de l’endroit où il s’est arrêté pour la dernière fois.

* Pour plus de robustesse de l’outil de transfert de contenu, le contenu ne peut être ingéré que sur l’instance d’auteur ou sur l’instance de publication au même moment. Consultez [Prise en main de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr) pour plus d’informations.

* Lorsque différentes versions sont incluses, le chemin d’accès `/var/audit` est automatiquement inclus pour migrer les événements de contrôle.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa-latest}

La date de publication de l’analyseur de bonnes pratiques v2.1.20 est le 5 octobre 2021.

### Nouveautés {#what-is-new-bpa-oct}

* Capacité à détecter et à générer des rapports sur la longueur du nom de nœud.

* Capacité à détecter et à générer des rapports sur la taille totale de l’index.

* Capacité à détecter et à générer des rapports sur les ressources ne disposant pas d’un rendu d’origine.
