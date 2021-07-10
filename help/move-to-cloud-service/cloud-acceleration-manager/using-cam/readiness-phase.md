---
title: Phase de préparation dans Cloud Accelerated Manager
description: Cette page présente un aperçu de la phase de préparation de Cloud Acceleration Manager.
hide: true
hidefromtoc: true
index: false
source-git-commit: b5b6a4a84c57805770ec1c72741c2d56d4711309
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 4%

---


# Phase de préparation dans Cloud Accelerated Manager {#readiness-phase-cam}

Une fois que vous avez créé un projet dans Cloud Acceleration Manager, vous pouvez commencer à exécuter les outils disponibles pendant la phase de préparation.

La phase de préparation comprend :

* [Analyse des bonnes pratiques](#best-practices-analysis)
* [Planification et configuration](#planning-setup)

Suivez les étapes ci-dessous pour accéder à la phase de préparation :

1. Cliquez sur la carte de votre projet pour ouvrir la page d’entrée du projet.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-landing1.png)

1. Accédez à la section **Préparation**, comme illustré dans la figure ci-dessous.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >Pour en savoir plus, voir [Création et gestion d’un projet dans Cloud Acceleration Manager](/help/move-to-cloud-service/cloud-acceleration-manager/using-cam/getting-started-cam.md).

## Utilisation de la carte d’analyse des bonnes pratiques {#best-practices-analysis}

Suivez les étapes ci-dessous pour utiliser la carte Analyse des bonnes pratiques :

1. Cliquez sur le bouton **Réviser** de la carte **Analyse des bonnes pratiques**.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-2.png)

1. Suivez ces étapes pour télécharger BPA (Best Practices Analyzer) et l’exécuter sur un clone de votre système AEM.

   1. Accédez au portail [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) et téléchargez l’analyseur des bonnes pratiques sous la forme d’un fichier zip.

      >[!NOTE]
      >Passez en revue [Utilisation de l’analyseur des bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en#imp-considerations) pour savoir comment exécuter BPA.

   1. Exporter le rapport au format CSV

1. Cliquez sur **Charger un nouveau rapport** pour charger le rapport BPA dans le CAM.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-3.png)

1. Une fois que vous avez chargé un nouveau rapport, le rapport Analyse des bonnes pratiques s’affiche.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

1. Consultez et explorez le tableau de bord de l’analyse des bonnes pratiques dans CAM. Pour plus d’informations, reportez-vous à la section ci-dessous [Examen du rapport d’analyse des bonnes pratiques](#analysis-report) .

   >[!NOTE]
   >Le téléchargement d’un nouveau rapport réinitialise toutes les évaluations.

### Rapport Analyse des bonnes pratiques {#analysis-report}

Consultez les cartes suivantes disponibles sur la page Rapport d’analyse des bonnes pratiques :

![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> Avec chaque carte, vous pouvez :
>* cliquer sur chaque carte pour ouvrir son onglet associé ;
>* mettre en signet tous les onglets du rapport (y compris le filtrage) pour le partage ou une récupération ultérieure ;
>* utiliser l’icône de détails pour afficher les détails de chaque résultat de rapport ;


#### Propriétés du rapport {#report-properties}

La carte **Propriétés du rapport** fournit des informations sur les propriétés du rapport, telles que la date du rapport, la durée, les filtres, la date de transfert et les détails d’Adobe Experience Manager (AEM).

![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-properties.png)

#### Aperçu du rapport {#report-overview}

Cette carte **Aperçu du rapport** fournit les résultats du rapport, comme illustré dans la figure ci-dessous.

![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview.png)

Cliquez sur ce rapport pour ouvrir l’onglet **Rapport**.

![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview2.png)

Vous pouvez filtrer le rapport selon son importance, son sous-type ou son nombre.

![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>Reportez-vous à la section [Interprétation du rapport Analyseur des bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en) pour en savoir plus sur les catégories de résultats et les niveaux d’importance.

#### Évaluation des bonnes pratiques {#best-practices-assessment}

L’option Évaluation des bonnes pratiques fournit une évaluation de votre instance d’AEM actuelle et fournit des conseils sur les prochaines étapes pour adopter AEM bonnes pratiques. Vous pouvez consulter les informations suivantes dans cet onglet :

* Présentation de l’instance AEM
* Composants et modèles personnalisés
* Autres résultats
* Ralentir les requêtes
* Tâches de maintenance

#### Évaluation de la complexité de la migration {#migration-complexity-assessment}

L’option Évaluation de la complexité de la migration permet d’évaluer la complexité de la migration de la mise en oeuvre d’AEM existante vers AEM en tant que Cloud Service. Vous pouvez consulter les informations suivantes dans cet onglet :

* Présentation de l’instance AEM
* Évaluation
* Considérations relatives à la migration de contenu

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/migration-complexity-1.png)

## Utilisation de la carte Planification et configuration {#planning-setup}

Consultez cette section pour découvrir la carte de l’activité Planification et configuration .

1. Cliquez sur le bouton **Afficher** de la carte **Planification et configuration** qui fournit tout le contenu approprié qui vous aidera à planifier et à configurer votre migration AEM.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-4.png)

1. Un carrousel de contenu contenant des informations pertinentes pour cette phase du parcours de migration s’affiche.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5-planning.png)

## Et après ? {#whats-next}

Une fois que vous avez appris à vous connecter à Cloud Acceleration Manager et à créer un projet, vous êtes prêt à passer à l’étape suivante, à l’aide de la phase de mise en oeuvre.
