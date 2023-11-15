---
title: Notes de mise à jour de Cloud Manager 2023.11.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2023.11.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 3a9eaa162d62cd3e674f14ba39ed7c96ad271f79
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 14%

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
* Spécialisé [pipelines de configuration](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) sont désormais disponibles pour configurer les paramètres d’environnement, les tâches de maintenance, les règles CDN, etc. en quelques minutes.
* [Lors de la copie de contenu](/help/implementing/developing/tools/content-copy.md) d’un environnement supérieur à un environnement de développement, un message s’affiche maintenant pour vous avertir lorsque vous copiez des jeux de contenu volumineux, car les environnements de développement sont limités en capacité.
* [Page des détails d’exécution du pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) affiche désormais toutes les étapes d’une exécution de pipeline avec celles qui n’ont pas encore commencé en grisé.
* Sur les deux **[Activité](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity)** et **[Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines)** , un résumé de l’exécution du pipeline est désormais disponible lorsque vous cliquez sur un pipeline avec l’état en cours d’exécution.
* Une nouvelle **Durée** a été ajoutée à la section [page des détails du pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) qui inclut la durée moyenne de l’étape du pipeline en fonction de la tendance historique de ce programme.
* Sur le [page d’exécution du pipeline,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity-window) les étapes terminées affichent désormais la durée.
* Exécution de [réutilisation d’artefacts de build](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) affiche désormais le lien vers l’exécution qui a initialement créé ces artefacts.
* L’option à sélectionner **Échecs de mesures importants** peut maintenant être configuré pour [pipelines de qualité de code](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) ainsi que .


## Programme d&#39;adoption précoce {#early-adoption}

Faire partie de notre programme d’adoption précoce et avoir la possibilité de tester certaines fonctionnalités à venir.

### Apportez votre propre GitHub {#byo-github}

Si vous utilisez GitHub pour gérer vos référentiels, [vous pouvez désormais valider le code directement dans vos référentiels GitHub via Cloud Manager.](/help/implementing/cloud-manager/managing-code/byo-github.md) Cette intégration élimine la nécessité de synchroniser de manière cohérente le code avec le référentiel d’Adobe et vous permet de vérifier les requêtes d’extraction avant de les fusionner dans les branches principales.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `Grp-CloudManager_BYOG@adobe.com` de votre adresse électronique associée à votre Adobe ID.

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

## Problèmes connus {#known-issues}

Un bogue connu empêche [pipelines de configuration](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md##config-deployment-pipeline) de passer à la production.

Si la variable **Mettre en pause avant le déploiement en production** est requise pour un pipeline de configuration. Voici la solution suggérée jusqu’à ce que le bogue soit résolu.

1. Exécuter le pipeline.
1. Testez le code dans l’environnement d’évaluation.
1. Lorsque le déploiement et l’approbation sont disponibles, cliquez sur **Rejeter**.
1. Modifiez le pipeline pour désactiver la fonction **Mettre en pause avant le déploiement en production** .
1. Exécutez à nouveau le pipeline. Il s’exécute à nouveau lors de l’évaluation, puis en production.
