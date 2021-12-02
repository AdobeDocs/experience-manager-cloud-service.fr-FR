---
title: Notes de mise à jour des outils de migration dans AEM version 2021.10.0 as a Cloud Service
description: Notes de mise à jour des outils de migration dans AEM version 2021.11.0 as a Cloud Service
feature: Release Information
source-git-commit: 587258a831fb5cd3b3a23d1f891db8c2254a8d6b
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 12%

---


# Notes de mise à jour des outils de migration dans AEM version 2021.10.0 as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour des outils de migration dans AEM 2021.10.0 as a Cloud Service.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Cloud Acceleration Manager {#cam-release}

### Date de publication {#release-date-cam}

La date de publication de Cloud Acceleration Manager est le 25 octobre 2021.

### Nouveautés {#what-is-new-cam}

Cloud Acceleration Manager permet désormais aux utilisateurs d’afficher les rapports BPA historiques dans un rapport de tendance. Grâce à ce rapport, les utilisateurs peuvent visualiser l’état d’avancement qu’ils font dans une représentation graphique facile à consommer. Voir [Utilisation de l’option Afficher la courbe de tendance](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#trendline-view-cam) pour plus d’informations.

### Date de publication {#release-date-october-cam}

La date de publication de Cloud Acceleration Manager est le 4 octobre 2021.

### Nouveautés {#what-is-new-cam-oct}

Cloud Acceleration Manager permet désormais aux utilisateurs d’afficher les rapports BPA dans un aperçu imprimable, ce qui permet une impression ou une impression simples à PDF pour une partageabilité facile. Reportez-vous aux étapes 6 et 7 de la section [Utilisation de la carte d’analyse des bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#best-practices-analysis).


## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu v1.6.0 est le 4 octobre 2021.

### Nouveautés {#what-is-new-ctt-oct}

* Amélioration de l’outil de mappage des utilisateurs avec une expérience utilisateur simplifiée, y compris les fonctionnalités suivantes répertoriées ci-dessous. Pour plus d’informations, reportez-vous à la section [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html).
   * Tester la connexion à l’API User Management avant d’exécuter le mappage utilisateur
   * Ignorer les erreurs et poursuivre avec élégance l’activité Mappage des utilisateurs
   * Le mappage utilisateur n’échoue plus si **Jeton d’accès** expire après 24 heures. Le mappage utilisateur peut être exécuté à nouveau à partir de l’endroit où il s’est arrêté pour la dernière fois.

* Pour accroître la robustesse de l’outil de transfert de contenu, le contenu peut être ingéré simultanément sur l’instance d’auteur ou l’instance de publication. Voir [Prise en main de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) pour plus d’informations.

* Lorsque des versions sont incluses, le chemin d’accès `/var/audit` est automatiquement inclus pour migrer les événements de contrôle.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa-latest}

La date de publication de la version 2.1.20 de l’analyseur des bonnes pratiques est le 5 octobre 2021.

### Nouveautés {#what-is-new-bpa-oct}

* Possibilité de détecter et de générer des rapports sur la longueur du nom de noeud.

* Capacité à détecter et à générer des rapports sur la taille totale de l’index.

* Possibilité de détecter et de générer des rapports sur les ressources dont le rendu d’origine manque.