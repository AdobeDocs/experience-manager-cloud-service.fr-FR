---
title: Phase de mise en œuvre dans Cloud Acceleration Manager
description: Cette page présente un aperçu de la phase de mise en œuvre dans Cloud Acceleration Manager.
exl-id: e6ac88f0-4b3f-43a1-98bc-8c6608713784
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 41%

---

# Phase de mise en œuvre dans Cloud Acceleration Manager {#implementation-phase-cam}

La phase de mise en œuvre comprend :

* [Développement local](#local-development)
* [Refactorisation du code](#code-refactoring)
* [Déploiement d’AEM as a Cloud Service](#aem-as-a-cloud-service-deployment)
* [Transfert de contenu](#content-transfer)


Cliquez sur la carte de votre projet afin d’ouvrir la page d’entrée du projet et d’accéder au **Implémentation** , comme illustré dans la figure suivante.

![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>Pour en savoir plus, voir [Création et gestion d’un projet dans Cloud Acceleration Manager](getting-started-cam.md#create-project).


## Utilisation de la carte Développement local {#local-development}

La carte Développement local fournit tout le contenu approprié qui peut vous aider à configurer votre environnement de développement AEM local au démarrage de la phase de mise en oeuvre de votre parcours de migration.

Consultez cette section pour découvrir la carte d’activité Développement local :

1. Cliquez sur **Affichage** de la **Développement local** carte.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-2.png)

1. Un carrousel de contenu affiche les informations pertinentes pour cette phase du parcours de migration.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-3.png)


## Utilisation de la carte de refactorisation du code {#code-refactoring}

La carte d’activité Refactorisation du code fournit toutes les informations pertinentes et met en évidence les zones de refactorisation du code à examiner et à résoudre lors du passage à AEM as a Cloud Service.

Consultez cette section pour découvrir la carte d’activité Refactorisation du code :

1. Cliquez sur **Réviser** de la **Refactorisation du code** carte d’activité.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-4.png)

1. La page affiche la liste des activités de refactorisation du code organisées par niveau de gravité. Pour en savoir plus, cliquez sur les deux icônes en surbrillance.

   La page affiche les considérations relatives à la refactorisation du code dans trois onglets différents :

   * Présentation
   * Dispatcher
   * Tests

>[!NOTE]
>Passez en revue le contenu de ces onglets pour comprendre certaines zones supplémentaires qui ne sont pas couvertes par l’analyseur des bonnes pratiques.

L’onglet **Dispatcher** fournit des information sur la façon dont structurer les configurations Apache et Dispatcher d’AEM as a Cloud Service. Il explique également comment valider et exécuter le service localement avant son déploiement dans les environnements cloud. Elle présente en outre le débogage dans les environnements cloud.

![image](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-2.png)

L’onglet **Tests** fournit des informations sur les tests fonctionnels, de contrôle de l’expérience et de l’interface utilisateur.

![image](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-3.png)


## Utilisation de la carte de déploiement d’AEM as a Cloud Service {#aem-as-a-cloud-service-deployment}

AEM carte Déploiement as a Cloud Service fournit tout le contenu approprié qui vous aide à déployer votre code sur AEM as a Cloud Service.

Consultez cette section pour découvrir AEM carte d’activité Carte de déploiement as a Cloud Service :

1. Cliquez sur **Affichage** de la **AEM déploiement as a Cloud Service** carte d’activité.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-6.png)

1. Un carrousel de contenu affiche les informations pertinentes pour cette phase du parcours de migration.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/aem-deployment-card.png)


## Utilisation de la carte de transfert de contenu {#content-transfer}

La carte de transfert de contenu vous permet de démarrer et de gérer le transfert de contenu de votre instance AEM actuelle vers AEM as a Cloud Service.

Consultez cette section pour découvrir la carte de l’activité Transfert de contenu :

1. Cliquez sur **Réviser** de la **Transfert de contenu** carte d’activité.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-1.png)

1. Pour démarrer un transfert de contenu, vous devez créer un jeu de migration. Cliquez sur **Création d’un jeu de migration**. Un jeu de migration permet de transférer du contenu vers AEM as a Cloud Service.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-2.png)

   >[!NOTE]
   >Un jeu de migration expire après une longue période d’inactivité. Voir [Expiration du jeu de migration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) pour plus d’informations.

   >[!NOTE]
   >Voir [conditions préalables](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html) et le [bonnes pratiques et directives](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=fr) avant d’utiliser l’outil de transfert de contenu.

1. Téléchargez et installez l’outil de transfert de contenu pour renseigner le jeu de migration et terminer la phase Extraction du transfert de contenu. Lisez la section [Prise en main de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr) pour savoir comment utiliser l’outil de transfert de contenu.

1. Pour ingérer du contenu à partir du jeu Migration dans un environnement sur AEM as a Cloud Service, vous devez démarrer une ingestion. Accédez à **Tâches d’ingestion** et cliquez sur **Nouvelle ingestion**. Réviser [Ingestion de contenu dans Target](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html?lang=fr) afin que vous puissiez apprendre à terminer la phase d’ingestion du transfert de contenu.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-3.png)

<!--### Estimating Content Transfer Time {#calculating}

A Content Transfer Tool calculator has been provided to estimate how long it could take to complete the content transfer activity. You can use the content repository size slider to select the size that applies to your project. The transfer times vary for the extraction and ingestion phases. 

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-4.png)

   >[!NOTE]
   >These times are estimates only. Factor such as network speeds and time to scale up instances have not been accounted for in these estimates.

To estimate the size of the AEM Repository, you can run the Disk Usage report under `http://HOST:PORT/etc/reports/diskusage.html`. 

You can also estimate the size of specific repository paths by using the `path` parameter, for example, `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`. -->

## Prochaines étapes {#whats-next}

Après avoir appris à vous connecter à Cloud Acceleration Manager et à utiliser la phase de mise en oeuvre, vous êtes prêt à passer en revue l’étape suivante dans la [Phase de mise en ligne](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-golive-phase.html).
