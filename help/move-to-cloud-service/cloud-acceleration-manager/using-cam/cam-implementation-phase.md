---
title: Phase de mise en oeuvre dans Cloud Accelerated Manager
description: Cette page présente un aperçu de la phase de mise en oeuvre dans Cloud Acceleration Manager.
source-git-commit: 4041e3fd9a479a64ed38e2bf1a6251fda39e55c2
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 4%

---


# Phase de mise en oeuvre dans Cloud Accelerated Manager {#implementation-phase-cam}

La phase de mise en oeuvre comprend :

* [Développement local](#local-development)
* [Refactorisation du code](#code-refactoring)
* [AEM en tant que déploiement Cloud Service](#aem-as-a-cloud-service-deployment)
* [Transfert de contenu](#content-transfer)


Cliquez sur la carte de votre projet pour ouvrir la page d’entrée du projet et accédez à la section **Mise en oeuvre**, comme illustré dans la figure ci-dessous.

![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>Pour en savoir plus, voir [Création et gestion d’un projet dans Cloud Acceleration Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en#create-project).


## Utilisation de la carte de développement locale {#local-development}

La carte Développement local fournit tout le contenu approprié qui vous aidera à configurer votre environnement de développement AEM local au démarrage de la phase de mise en oeuvre de votre parcours de migration.

Consultez cette section pour découvrir la carte d’activité Développement local :

1. Cliquez sur le bouton **Afficher** à partir de la carte **Développement local**.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-2.png)

1. Un carrousel de contenu contenant des informations pertinentes pour cette phase du parcours de migration s’affiche.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-3.png)


## Utilisation de la carte de refactorisation du code {#code-refactoring}

La carte d’activité Refactorisation du code fournit toutes les informations pertinentes et met en évidence les zones de refactorisation du code que vous devez examiner lors du passage à AEM en tant que Cloud Service.

Consultez cette section pour découvrir la carte d’activité Refactorisation du code :

1. Cliquez sur le bouton **Réviser** à partir de la carte d’activité **Refactorisation du code** .

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-4.png)

1. La page affiche la liste des activités de refactorisation du code organisées par niveau de gravité. Pour en savoir plus, cliquez sur les deux icônes en surbrillance.

   >[!NOTE]
   >En outre, consultez le contenu des onglets de la page pour comprendre certaines zones supplémentaires qui ne sont pas couvertes par l’analyseur des bonnes pratiques.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5.png)


## Utilisation d’AEM comme carte de déploiement de Cloud Service {#aem-as-a-cloud-service-deployment}

La carte AEM as a Cloud Service Deployment fournit tout le contenu approprié qui vous aidera à déployer votre code vers AEM as a Cloud Service.

Consultez cette section pour découvrir AEM comme carte d’activité Carte de déploiement Cloud Service :

1. Cliquez sur le bouton **Afficher** de la carte d’activité **AEM en tant que Cloud Service Deployment** .

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-6.png)

1. Un carrousel de contenu contenant des informations pertinentes pour cette phase du parcours de migration s’affiche.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/aem-deployment-card.png)


## Utilisation de la carte de transfert de contenu {#content-transfer}

La carte d’activité Transfert de contenu fournit des conseils et des considérations à prendre en compte lors de l’utilisation de l’outil de transfert de contenu pour déplacer le contenu de votre instance AEM actuelle vers AEM en tant que Cloud Service.

Suivez cette section pour explorer la carte d’activité Transfert de contenu :

1. Cliquez sur le bouton **Afficher** à partir de la carte d’activité **Transfert de contenu**.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-8.png)

1. Un carrousel de contenu contenant des informations pertinentes pour cette phase du parcours de migration s’affiche.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/content-transfertool-card.png)

   >[!NOTE]
   >Veuillez consulter les [conditions préalables](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en) et les [bonnes pratiques et instructions](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=fr) avant d’utiliser l’outil de transfert de contenu.

### Estimation de l’activité de l’outil de transfert de contenu {#calculating}

Un nouveau calculateur d’outil de transfert de contenu a été fourni pour estimer le temps nécessaire à l’exécution de l’activité de transfert de contenu. Vous pouvez utiliser le curseur de taille du référentiel de contenu pour sélectionner la taille qui s’applique à votre projet. Les délais de transfert varient selon les phases d’extraction et d’ingestion.

Pour estimer la taille du référentiel AEM, vous pouvez exécuter le rapport Utilisation du disque sous `http://HOST:PORT/etc/reports/diskusage.html`.

Vous pouvez également estimer la taille des chemins de référentiel spécifiques à l’aide du paramètre `path`, par exemple `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`.

## Et après ? {#whats-next}

Une fois que vous avez appris à vous connecter à Cloud Acceleration Manager et à utiliser la phase de mise en oeuvre, vous êtes prêt à passer à l’étape suivante, [À l’aide de la phase Go Live](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-golive-phase.html?lang=en).
