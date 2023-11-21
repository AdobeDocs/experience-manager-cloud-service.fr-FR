---
title: Notes de mise à jour de Cloud Manager 2023.11.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2023.11.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: be38ca5bf79d401fc12c1422c270a2ee84bbbad2
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 25%

---


# Notes de mise à jour de Cloud Manager 2023.11.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2023.11.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de Cloud Manager version 2023.11.0 dans AEM as a Cloud Service est le 14 novembre 2023. La prochaine version est prévue pour le 7 décembre 2023.

## Nouveautés {#what-is-new}

* La protection DOS (WAF-DDOS) du pare-feu d’applications web est désormais disponible à l’achat dans le cadre de vos droits as a Cloud Service et [peut être configuré en libre-service.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* Spécialisé [pipelines de configuration](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) sont désormais disponibles pour configurer et déployer des règles de filtrage du trafic, y compris des règles WAF, en quelques minutes.
* [Lors de la copie de contenu](/help/implementing/developing/tools/content-copy.md) d’un environnement supérieur à un environnement de développement, un message s’affiche maintenant pour vous avertir lorsque vous copiez des jeux de contenu volumineux, car les environnements de développement sont limités en capacité.
* [Page des détails d’exécution du pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) affiche maintenant toutes les étapes d’une exécution de pipeline avec celles qui n’ont pas encore commencé en grisé.
* Sur les deux **[Activité](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity)** et **[Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines)** , un résumé de l’exécution du pipeline est désormais disponible lors de la sélection d’un pipeline avec l’état en cours d’exécution.
* Une nouvelle section **Durée** a été ajoutée à la [page des détails du pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) qui inclut la durée moyenne de l’étape du pipeline en fonction de la tendance historique de ce programme.
* Sur le [page d’exécution du pipeline,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity-window) les étapes terminées affichent désormais la durée.
* Exécution de [réutilisation d’artefacts de build](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) affiche maintenant le lien vers l’exécution qui a initialement créé ces artefacts.
* L’option à sélectionner **Échecs de mesures importants** peut maintenant être configuré pour [pipelines de qualité de code](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) ainsi que .


## Programme d’adoption précoce {#early-adoption}

Pour avoir la possibilité de tester certaines fonctionnalités à venir, participez au programme d&#39;adoption précoce de l&#39;Adobe.

### Apporter votre propre GitHub {#byo-github}

Si vous utilisez GitHub pour gérer vos référentiels, [vous pouvez désormais valider le code directement dans vos référentiels GitHub via Cloud Manager.](/help/implementing/cloud-manager/managing-code/byo-github.md) Cette intégration élimine la nécessité de synchroniser de manière cohérente le code avec le référentiel Adobe et vous permet de vérifier les demandes d’extraction avant de les fusionner dans les branches principales.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `Grp-CloudManager_BYOG@adobe.com` de votre adresse électronique associée à votre Adobe ID.

### Autorisations personnalisées {#custom-permissions}

[Autorisations personnalisées de Cloud Manager](/help/implementing/cloud-manager/custom-permissions.md) vous permet de créer des profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs de Cloud Manager.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `Grp-CloudManager-custom-permissions@adobe.com` de votre adresse électronique associée à votre Adobe ID.

### Restauration de contenu en libre-service {#content-restore}

[Nouvelle fonctionnalité de restauration de contenu en libre-service](/help/operations/restore.md) fournit désormais une restauration de sauvegarde pendant sept jours au maximum et est disponible pour les utilisateurs précoces à des fins d’évaluation, notamment :

* Restauration de sauvegarde ponctuelle des dernières 24 heures
* Restauration de la période fixe pendant sept jours au maximum

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-restorefrombackup-adopter@adobe.com` de votre email associé à votre Adobe ID.

* Le programme d’adoption précoce est limité aux environnements de développement uniquement.
* La disponibilité du programme d’adoption précoce de cette fonction est limitée.
* Cette fonctionnalité est destinée à la récupération de contenu supprimé accidentellement et n’est pas destinée à la reprise après sinistre.

### Tableau de bord du contrôle de l’expérience {#experience-audit-dashboard}

[Tableau de bord du contrôle de l’expérience de Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) inclut une vue de tendance des scores de performances de votre page, ainsi que des informations et des recommandations pour vous aider à les améliorer. Le contrôle de l’expérience est inclus en tant qu’étape dans le pipeline de production de Cloud Manager.

Le tableau de bord utilise Google Lighthouse, un outil automatisé Open Source permettant d’améliorer la qualité de vos applications web. Vous pouvez l’exécuter sur n’importe quelle page web, publique ou nécessitant une authentification. Il comporte des audits des performances, de l’accessibilité, des applications web progressives, de l’optimisation pour les moteurs de recherche, etc.

Vous souhaitez tester le nouveau tableau de bord ? Pour commencer, envoyez un courrier électronique à l’adresse `aem-lighthouse-pilot@adobe.com` de votre email associé à votre Adobe ID.

## Problèmes connus {#known-issues}

Il existe un bogue connu qui empêche [pipelines de configuration](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md##config-deployment-pipeline) de passer à la production.

Si la variable **Mettre en pause avant le déploiement en production** est requise pour un pipeline de configuration. Voici la solution suggérée jusqu’à ce que le bogue soit résolu.

1. Exécuter le pipeline.
1. Testez le code dans l’environnement d’évaluation.
1. Lorsque le déploiement et l’approbation sont disponibles, cliquez sur **Rejeter**.
1. Modifiez le pipeline afin que vous puissiez désactiver la variable **Mettre en pause avant le déploiement en production** .
1. Exécutez à nouveau le pipeline afin qu’il puisse s’exécuter à nouveau lors de l’évaluation, puis en production.
