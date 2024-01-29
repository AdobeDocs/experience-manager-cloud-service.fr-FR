---
title: Notes de mise à jour de Cloud Manager 2024.1.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2024.1.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 06f534e6541bd04e005f3acf1edbb3e372c1cd0d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 47%

---


# Notes de mise à jour de Cloud Manager 2024.1.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2024.1.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2024.1.0 de Cloud Manager dans AEM as a Cloud Service est le 18 janvier 2024. La prochaine version est prévue pour le 16 février 2024.

## Nouveautés {#what-is-new}

* Cloud Manager valide désormais les dates d’expiration non seulement pour la [certificat,](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) mais également pour les certificats intermédiaires.
* CDN [logs](/help/implementing/cloud-manager/manage-logs.md) sont désormais renvoyés dans un format compressé.

## Programme d’adoption précoce {#early-adoption}

Pour avoir la possibilité de tester certaines fonctionnalités à venir, participez au programme d&#39;adoption précoce de l&#39;Adobe.

### Collecte côté client via Real User Monitoring (RUM) {#rum}

Vous pouvez utiliser la variable [Service de données de surveillance des utilisateurs réels (RUM)](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) pour activer la collecte côté client pour AEM as a Cloud Service.

Le service de données de surveillance des utilisateurs réels (RUM) offre un reflet plus précis des interactions des utilisateurs, assurant une mesure fiable de l’engagement du site web. C’est une excellente opportunité d’obtenir des informations avancées sur les performances de votre page. Cela est bénéfique pour les clients qui utilisent un réseau de diffusion de contenu géré par Adobe ou un réseau de diffusion de contenu géré par non Adobe. Pour les clients qui utilisent un réseau de diffusion de contenu non géré par un Adobe, la création de rapports automatisés sur le trafic peut désormais leur être activée, ce qui évite d’avoir à partager n’importe quel rapport de trafic avec un Adobe.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-rum-adopter@adobe.com` à partir de l’adresse électronique associée à votre Adobe ID. Indiquez le nom de domaine des environnements de production, d’évaluation et de développement dans votre email.  La disponibilité du programme d’adoption précoce de cette fonctionnalité est limitée.

### Apporter votre propre GitHub {#byo-github}

Si vous utilisez GitHub pour gérer vos référentiels, [vous pouvez désormais valider le code directement dans vos référentiels GitHub via Cloud Manager.](/help/implementing/cloud-manager/managing-code/byo-github.md) Cette intégration élimine la nécessité de synchroniser de manière cohérente le code avec le référentiel Adobe et vous permet de vérifier les demandes d’extraction avant de les fusionner dans les branches principales.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `Grp-CloudManager_BYOG@adobe.com` de votre adresse électronique associée à votre Adobe ID.

### Restaurer le contenu en libre-service {#content-restore}

[Une nouvelle fonctionnalité de restauration du contenu en libre-service](/help/operations/restore.md) fournit désormais une restauration de sauvegarde pendant sept jours au maximum et est disponible pour les utilisateurs et utilisatrices précoces à des fins d’évaluation, notamment les éléments suivants :

* Restauration de sauvegarde ponctuelle des dernières 24 heures.
* Restaurations de périodes fixes pendant sept jours au maximum.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-restorefrombackup-adopter@adobe.com` de votre email associé à votre Adobe ID.

* le programme d’adoption précoce est limité aux environnements de développement uniquement.
* La disponibilité du programme d’adoption précoce de cette fonctionnalité est limitée.
* Cette fonctionnalité est destinée à la récupération du contenu supprimé accidentellement et n’est pas destinée à la restauration après sinistre.

### Tableau de bord d’audit de l’expérience {#experience-audit-dashboard}

[Le tableau de bord d’audit de l’expérience de Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) inclut une vue de tendance des scores de performances de votre page, ainsi que des informations et des recommandations pour vous aider à les améliorer. L’audit de l’expérience est inclus en tant qu’étape dans le pipeline de production de Cloud Manager.

Le tableau de bord utilise Google Lighthouse, un outil automatisé Open Source permettant d’améliorer la qualité de vos applications web. Vous pouvez l’exécuter sur n’importe quelle page web, publique ou nécessitant une authentification. Il comporte des audits des performances, de l’accessibilité, des applications web progressives, de l’optimisation du moteur de recherche et plus encore.

Vous souhaitez tester le nouveau tableau de bord ? Pour commencer, envoyez un courrier électronique à l’adresse `aem-lighthouse-pilot@adobe.com` de votre email associé à votre Adobe ID.

## Correctifs {#bug-fixes}

* Une erreur a été corrigée lorsque les pipelines de configuration échouaient à l’étape de création avec un message d’erreur non clair si l’emplacement des fichiers de configuration n’était pas correctement défini. Le message d’erreur est maintenant clair et indique que l’utilisateur doit vérifier que l’emplacement des fichiers de configuration est correct.
* Lorsqu’une étape de création se termine avec le statut `FAILED` en raison d’une `BUILD_MAVEN_TRANSFER_ARTIFACT_ERROR`, elle est désormais décrite comme une erreur due à des conflits de fusion avec la branche de destination.
