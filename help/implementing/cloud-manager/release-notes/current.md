---
title: Notes de mise à jour de Cloud Manager 2023.12.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2023.12.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: b3a338f469ea04d2c31204149d619931a55f2b24
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 17%

---


# Notes de mise à jour de Cloud Manager 2023.12.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2023.12.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2023.12.0 de Cloud Manager dans AEM as a Cloud Service est le 14 décembre 2023. La prochaine version est prévue pour le 18 janvier 2024.

## Nouveautés {#what-is-new}

* [Autorisations personnalisées de Cloud Manager](/help/implementing/cloud-manager/custom-permissions.md) vous permet de créer des profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs de Cloud Manager.
   * Cette fonctionnalité sera déployée par étapes et sera achevée avec la version de février 2024 de Cloud Manager.
   * Veuillez envoyer un e-mail à `Grp-CloudManager-custom-permissions@adobe.com` à partir de l’adresse électronique associée à votre Adobe ID, si vous souhaitez être activé plus tôt.
* Les conteneurs de génération prennent désormais en charge Node.js version 18 pour [pipelines frontend.](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md)
* Pour les programmes Cloud Manager nouvellement créés, [le sous-compte New Relic associé](/help/implementing/cloud-manager/user-access-new-relic.md) n’est pas activée par défaut.
   * Pour les programmes existants dans lesquels le sous-compte New Relic n’a pas été accessible depuis plus de 90 jours, il sera désactivé.
   * Si vous souhaitez utiliser le sous-compte New Relic, vous devez vous inscrire via Cloud Manager.
* Déploiements des versions mineures pour java 8 et 11 et mises à jour vers maven [annoncé et commencé avec la version d’octobre de Cloud Manager](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md) ont été terminées.
   * La prise en charge du noeud 18 a été ajoutée pour les pipelines front-end et de pile complète.
   * La version mineure de Java 8 a été mise à jour vers `jdk1.8.0_371`.
   * La version mineure de Java 11 a été mise à jour vers `jdk-11.0.20`.
   * Maven a été mis à jour vers la version 3.8.8.
   * L’image de base du conteneur de génération a été mise à jour vers Ubuntu 22.04.

## Programme d’adoption précoce {#early-adoption}

Pour avoir la possibilité de tester certaines fonctionnalités à venir, participez au programme d&#39;adoption précoce de l&#39;Adobe.

### Collecte côté client via Real User Monitoring (RUM) {#rum}

Vous pouvez utiliser la variable [Service de données de surveillance des utilisateurs réels (RUM)](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) pour activer la collecte côté client pour AEM as a Cloud Service.

Le service de données de surveillance des utilisateurs réels (RUM) offre un reflet plus précis des interactions des utilisateurs, assurant une mesure fiable de l’engagement du site web. C’est une excellente opportunité d’obtenir des informations avancées sur les performances de votre page. Cela est bénéfique pour les clients qui utilisent un réseau de diffusion de contenu géré par Adobe ou un réseau de diffusion de contenu géré par non Adobe. Pour les clients qui utilisent un réseau de diffusion de contenu non géré par un Adobe, la création de rapports automatisés sur le trafic peut désormais leur être activée, ce qui évite d’avoir à partager n’importe quel rapport de trafic avec un Adobe.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-rum-adopter@adobe.com` à partir de l’adresse électronique associée à votre Adobe ID. Indiquez le nom de domaine des environnements de production, d’évaluation et de développement dans votre email.  La disponibilité du programme d’adoption précoce de cette fonction est limitée.

### Apporter votre propre GitHub {#byo-github}

Si vous utilisez GitHub pour gérer vos référentiels, [vous pouvez désormais valider le code directement dans vos référentiels GitHub via Cloud Manager.](/help/implementing/cloud-manager/managing-code/byo-github.md) Cette intégration élimine la nécessité de synchroniser de manière cohérente le code avec le référentiel Adobe et vous permet de vérifier les demandes d’extraction avant de les fusionner dans les branches principales.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `Grp-CloudManager_BYOG@adobe.com` de votre adresse électronique associée à votre Adobe ID.

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
