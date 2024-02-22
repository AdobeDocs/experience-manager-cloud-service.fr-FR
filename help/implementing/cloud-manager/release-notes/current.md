---
title: Notes de mise à jour de Cloud Manager 2024.2.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2024.2.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 4a41de9da557be562bb2ff5773c7954f76a9acc7
workflow-type: ht
source-wordcount: '725'
ht-degree: 100%

---


# Notes de mise à jour de Cloud Manager 2024.2.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2024.2.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de sortie de Cloud Manager version 2024.2.0 dans AEM as a Cloud Service est le 15 février 2024. La prochaine version est prévue pour le 16 mars 2024.

## Nouveautés {#what-is-new}

* Cloud Manager prend désormais en charge la gestion en libre-service des [variables de pipeline](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) via l’interface utilisateur de Cloud Manager.
* [Le service de prévisualisation](/help/implementing/cloud-manager/manage-environments.md#access-preview-sevice) sera désormais activé pour les environnements créés avant le déploiement de la fonctionnalité du service de prévisualisation.
* Les [autorisations personnalisées de Cloud Manager](/help/implementing/cloud-manager/custom-permissions.md) vous permettent de créer des profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs et utilisatrices de Cloud Manager.
   * Cette fonctionnalité a commencé à être déployée progressivement avec la [version de décembre 2023](/help/implementing/cloud-manager/release-notes/2023/2023-12-0.md) et sera complète le 20 février 2024.
* Pour tous les nouveaux environnements, les noms du [profil du produit d’environnement](/help/onboarding/aem-cs-team-product-profiles.md) seront dans un format plus convivial basé sur une combinaison de description de profil, de type d’environnement, de numéro et de numéro de programme.
* [L’environnement de version](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) a été mis à jour vers la version Maven 3.9.4 et les versions JDK jdk-11.0.22 et jdk1.8.0_401.

## Programme d’adoption précoce {#early-adoption}

Pour avoir la possibilité de tester certaines fonctionnalités à venir, participez au programme d’adoption précoce d’Adobe.

### Collecte côté client via Real User Monitoring (RUM) {#rum}

Vous pouvez utiliser le [Service de données Real User Monitoring (RUM)](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) pour activer la collecte côté client pour AEM as a Cloud Service.

Le Service de données Real User Monitoring (RUM) offre un reflet plus précis des interactions des utilisateurs et utilisatrices, assurant une mesure fiable de l’engagement du site web. Il constitue une excellente opportunité d’obtenir des informations avancées sur les performances de votre page. Il est ainsi utile pour la clientèle qui utilise un réseau CDN géré ou non par Adobe. Pour les personnes utilisant un réseau CDN non géré par Adobe, la création de rapports automatisés sur le trafic peut désormais être activée, leur évitant ainsi d’avoir à partager n’importe quel rapport sur le trafic avec Adobe.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `aemcs-rum-adopter@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID. Indiquez le nom de domaine des environnements de production, d’évaluation et de développement dans votre e-mail.  La disponibilité du programme d’adoption précoce de cette fonctionnalité est limitée.

### Apporter votre propre GitHub {#byo-github}

Si vous utilisez GitHub pour gérer vos référentiels, [vous pouvez désormais valider le code directement dans vos référentiels GitHub via Cloud Manager.](/help/implementing/cloud-manager/managing-code/byo-github.md) Cette intégration élimine la nécessité de constamment synchroniser le code avec le référentiel Adobe et vous permet de vérifier les requêtes d’extraction avant de les fusionner dans les branches principales. Cette fonctionnalité est réservée au GitHub public. La prise en charge du GitHub auto-hébergé n’est pas disponible.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `Grp-CloudManager_BYOG@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.

### Restaurer le contenu en libre-service {#content-restore}

[Une nouvelle fonctionnalité de restauration du contenu en libre-service](/help/operations/restore.md) fournit désormais une restauration de sauvegarde pendant sept jours au maximum et est disponible pour les utilisateurs et utilisatrices précoces à des fins d’évaluation, notamment les éléments suivants :

* Restauration de sauvegarde ponctuelle des dernières 24 heures.
* Restaurations de périodes fixes pendant sept jours au maximum.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-restorefrombackup-adopter@adobe.com` à partir de votre adresse e-mail associée à votre Adobe ID.

* le programme d’adoption précoce est limité aux environnements de développement uniquement.
* La disponibilité du programme d’adoption précoce de cette fonctionnalité est limitée.
* Cette fonctionnalité est destinée à la récupération du contenu supprimé accidentellement et n’est pas destinée à la restauration après sinistre.

### Tableau de bord d’audit de l’expérience {#experience-audit-dashboard}

[Le tableau de bord d’audit de l’expérience de Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) inclut une vue de tendance des scores de performances de votre page, ainsi que des informations et des recommandations pour vous aider à les améliorer. L’audit de l’expérience est inclus en tant qu’étape dans le pipeline de production de Cloud Manager.

Le tableau de bord tire parti de Google Lighthouse, un outil automatisé et open source permettant d’améliorer la qualité de vos applications web. Vous pouvez l’exécuter sur n’importe quelle page web, publique ou nécessitant une authentification. Il comporte des audits des performances, de l’accessibilité, des applications web progressives, de l’optimisation du moteur de recherche et plus encore.

Vous souhaitez tester le nouveau tableau de bord ? Pour commencer, envoyez un e-mail à l’adresse `aem-lighthouse-pilot@adobe.com` à partir de votre adresse e-mail associée à votre Adobe ID.

## Correctifs {#bug-fixes}

* Le JDK des conteneurs de version a été mis à jour vers une version qui résout [JDK-8313765.](https://bugs.openjdk.org/browse/JDK-8313765)
