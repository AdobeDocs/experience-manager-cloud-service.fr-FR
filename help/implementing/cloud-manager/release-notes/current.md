---
title: Notes de mise à jour de Cloud Manager 2023.10.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2023.10.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: b760b3a65d89b0b4f924379fc460015a58e2ed3e
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 16%

---


# Notes de mise à jour de Cloud Manager 2023.10.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2023.10.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Voir [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2023.10.0 de Cloud Manager dans AEM as a Cloud Service était le 5 octobre 2023. La prochaine version est prévue pour le 2 novembre 2023.

## Nouveautés {#what-is-new}

* Améliorations apportées à [indexation](/help/operations/indexing.md) ont réduit la durée du pipeline lors du déploiement de nouveaux index.
   * Les améliorations varient en fonction du profil de contenu.
* Automatique [mises à jour des environnements de développement](/help/implementing/cloud-manager/manage-environments.md#updating-environments) sont activés par défaut pour les nouveaux programmes, ce qui vous évite d’avoir à exécuter les mises à jour manuellement.
   * Cette mise à jour sera mise en oeuvre par étapes.
* Avec la version d’octobre 2023 de Cloud Manager, les versions Java sont mises à jour par le biais d’un déploiement progressif.
   * Les versions mineures de Java 8, 11 et Maven ont été mises à jour et seront déployées par étapes au cours des deux prochains mois. La nouvelle version comporte plusieurs correctifs de sécurité et correctifs. Les nouvelles versions sont les suivantes :
   * *Maven : 3.8.8*
   * *Version Java 8 : /usr/lib/jvm/jdk1.8.0_371*
   * *Version Java 11 : /usr/lib/jvm/jdk-11.0.20*
   * [Voir l’avis d’OpenJDK](https://openjdk.org/groups/vulnerability/advisories/) pour plus d’informations sur la sécurité et les correctifs de bogues dans ces mises à jour JDK.

## Programme d&#39;adoption précoce {#early-adoption}

Faire partie de notre programme d’adoption précoce et avoir la possibilité de tester certaines fonctionnalités à venir.

### Autorisations personnalisées {#custom-permissions}

[Autorisations personnalisées de Cloud Manager](/help/implementing/cloud-manager/custom-permissions.md) vous permet de créer des profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs de Cloud Manager.

si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail. `Grp-CloudManager-custom-permissions@adobe.com` de votre adresse électronique associée à votre Adobe ID.

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
