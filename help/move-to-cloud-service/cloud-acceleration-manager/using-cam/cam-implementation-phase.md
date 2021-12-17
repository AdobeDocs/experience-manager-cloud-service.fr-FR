---
title: Phase de mise en œuvre dans Cloud Acceleration Manager
description: Cette page présente un aperçu de la phase de mise en œuvre dans Cloud Acceleration Manager.
exl-id: 4ea13f12-7251-448f-9f54-c8d710aef2ba
source-git-commit: bcbf4e4ba1330bef9f2c8c473419903e40ac0e58
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 96%

---

# Phase de mise en œuvre dans Cloud Acceleration Manager {#implementation-phase-cam}

La phase de mise en œuvre comprend :

* [Développement local](#local-development)
* [Refactorisation du code](#code-refactoring)
* [Déploiement d’AEM as a Cloud Service](#aem-as-a-cloud-service-deployment)
* [Transfert de contenu](#content-transfer)


Cliquez sur la carte de votre projet pour ouvrir la page d’entrée du projet et accédez à la section **Mise en œuvre**, comme illustré dans la figure ci-dessous.

![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>Pour en savoir plus, voir [Création et gestion d’un projet dans Cloud Acceleration Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=fr#create-project).


## Utilisation de la carte Développement local {#local-development}

La carte Développement local fournit tout le contenu approprié qui vous aidera à configurer votre environnement de développement AEM local au démarrage de la phase de mise en œuvre de votre parcours de migration.

Consultez cette section pour découvrir la carte d’activité Développement local :

1. Cliquez sur le bouton **Afficher** à partir de la carte **Développement local**.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-2.png)

1. Un carrousel de contenu affiche les informations pertinentes pour cette phase du parcours de migration.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-3.png)


## Utilisation de la carte de refactorisation du code {#code-refactoring}

La carte d’activité Refactorisation du code fournit toutes les informations pertinentes et met en évidence les zones de refactorisation du code que vous devez examiner et résoudre lorsque vous passez à AEM as a Cloud Service.

Consultez cette section pour découvrir la carte d’activité Refactorisation du code :

1. Cliquez sur le bouton **Réviser** à partir de la carte d’activité **Refactorisation du code**.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-4.png)

1. La page affiche la liste des activités de refactorisation du code organisées par niveau de gravité. Pour en savoir plus, cliquez sur les deux icônes en surbrillance.

   La page affiche les considérations relatives à la refactorisation du code dans trois onglets différents :

   * Présentation
   * Dispatcher
   * Tests

>[!NOTE]
>Consultez le contenu de ces onglets pour comprendre certaines zones supplémentaires qui ne sont pas couvertes par l’analyseur des bonnes pratiques.

L’onglet **Dispatcher** fournit des information sur la façon dont structurer les configurations Apache et Dispatcher d’AEM as a Cloud Service. Il explique également comment valider et exécuter le service localement avant son déploiement dans les environnements cloud. Elle présente en outre le débogage dans les environnements cloud.

![image](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-2.png)

L’onglet **Tests** fournit des informations sur les tests fonctionnels, de contrôle de l’expérience et de l’interface utilisateur.

![image](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-3.png)


## Utilisation de la carte de déploiement d’AEM as a Cloud Service {#aem-as-a-cloud-service-deployment}

La carte de déploiement d’AEM as a Cloud Service fournit tout le contenu approprié qui vous aidera à déployer votre code vers AEM as a Cloud Service.

Consultez cette section pour découvrir la carte d’activité Carte de déploiement d’AEM as a Cloud Service :

1. Cliquez sur le bouton **Afficher** de la carte d’activité **Déploiement d’AEM as a Cloud Service**.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-6.png)

1. Un carrousel de contenu affiche les informations pertinentes pour cette phase du parcours de migration.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/aem-deployment-card.png)


## Utilisation de la carte de transfert de contenu {#content-transfer}

La carte d’activité Transfert de contenu fournit des conseils et des considérations à prendre en compte lors de l’utilisation de l’outil de transfert de contenu pour déplacer le contenu de votre instance AEM actuelle vers AEM as a Cloud Service.

Suivez cette section pour explorer la carte d’activité Transfert de contenu :

1. Cliquez sur le bouton **Afficher** à partir de la carte d’activité **Transfert de contenu**.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-8.png)

1. Un carrousel de contenu affiche les informations pertinentes pour cette phase du parcours de migration.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/content-transfertool-card.png)

   >[!NOTE]
   >Veuillez consulter les [conditions préalables](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=fr) et les [bonnes pratiques et instructions](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=fr) avant d’utiliser l’outil de transfert de contenu.

### Estimation du temps de transfert de contenu {#calculating}

Un nouveau calculateur d’outil de transfert de contenu a été fourni pour estimer le temps nécessaire à l’exécution de l’activité de transfert de contenu. Vous pouvez utiliser le curseur de taille du référentiel de contenu pour sélectionner la taille qui s’applique à votre projet. Les délais de transfert varient selon les phases d’extraction et d’ingestion.

>[!NOTE]
>Ces délais ne sont que des estimations. Des facteurs tels que la vitesse du réseau et le temps nécessaire pour augmenter les instances n’ont pas été pris en compte dans ces estimations.

Pour estimer la taille du référentiel AEM, vous pouvez exécuter le rapport Utilisation du disque sous `http://HOST:PORT/etc/reports/diskusage.html`.

Vous pouvez également estimer la taille des chemins de référentiel spécifiques à l’aide du paramètre `path`, par exemple `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`.

## Et après ? {#whats-next}

Une fois que vous avez appris à vous connecter à Cloud Acceleration Manager et à utiliser la phase de mise en œuvre, vous êtes prêt à passer en revue l’étape suivante de la [phase d’activation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-golive-phase.html?lang=fr).
