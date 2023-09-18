---
title: Notes de mise à jour de Cloud Manager 2023.9.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2023.9.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 8bf2ffe8b1d3780f4ad3f6972fea4f8281945abb
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 19%

---


# Notes de mise à jour de Cloud Manager 2023.9.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2023.9.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Voir [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de Cloud Manager version 2023.9.0 dans AEM as a Cloud Service est le 14 septembre 2023. La prochaine version est prévue pour le 5 octobre 2023.

## Nouveautés {#what-is-new}

* Les journaux CDN, lorsqu’ils sont disponibles, peuvent être téléchargés via l’interface utilisateur de Cloud Manager.
* Les utilisateurs peuvent désormais s’inscrire aux tests de contrôle de l’expérience optimisés par Google LightHouse dans des pipelines de pile complets hors production.

## Programme d&#39;adoption précoce {#early-adoption}

Faire partie de notre programme d’adoption précoce et avoir la possibilité de tester certaines fonctionnalités à venir.

### Restauration de contenu en libre-service {#content-restore}

[Nouvelle fonctionnalité de restauration de contenu en libre-service](/help/operations/restore.md) fournit désormais une restauration de sauvegarde pendant sept jours au maximum et est disponible pour les utilisateurs précoces à des fins d’évaluation, notamment :

* Restauration de sauvegarde ponctuelle des dernières 24 heures
* Restauration de la période fixe pendant sept jours au maximum

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-restorefrombackup-adopter@adobe.com` de votre email associé à votre Adobe ID. Remarque :

* Le programme d’adoption précoce est limité aux environnements de développement uniquement.
* La disponibilité du programme d’adoption précoce de cette fonction est limitée.
* Cette fonctionnalité est destinée à la récupération de contenu supprimé accidentellement et n’est pas destinée à la reprise après sinistre.

### Tableau de bord du contrôle de l’expérience {#experience-audit-dashboard}

[Tableau de bord du contrôle de l’expérience de Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) inclut une vue de tendance des scores de performances de votre page, ainsi que des informations et des recommandations pour vous aider à les améliorer. Le contrôle de l’expérience est inclus en tant qu’étape dans le pipeline de production de Cloud Manager.

Le tableau de bord tire parti de Google Lighthouse, un outil automatisé et open source permettant d’améliorer la qualité de vos applications web. Vous pouvez l’exécuter sur n’importe quelle page web, publique ou nécessitant une authentification. Il comporte des audits des performances, de l’accessibilité, des applications web progressives, de l’optimisation pour les moteurs de recherche, etc.

Vous souhaitez tester le nouveau tableau de bord ? Veuillez envoyer un e-mail à `aem-lighthouse-pilot@adobe.com` à partir de votre email associé à votre Adobe ID et nous pouvons vous aider à démarrer.

## Correctifs {#bug-fixes}

* Lorsqu’un programme est supprimé, tout pipeline associé en cours d’exécution est également supprimé, en s’assurant que le pipeline n’est pas incorrectement désigné comme état d’échec.
* Le bouton Terminer la mise en service est désactivé et informe l’utilisateur de la raison pour laquelle un pipeline est en cours.
* Parfois, lorsque toutes les étapes d’exécution d’un pipeline sont &quot;terminées&quot;, l’état du pipeline est considéré comme &quot;en cours d’exécution&quot;, ce qui donne l’impression qu’il est en état de blocage. Il est maintenant considéré comme &quot;terminé&quot;.
