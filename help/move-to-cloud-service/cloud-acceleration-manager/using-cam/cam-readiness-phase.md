---
title: Phase de préparation dans Cloud Accelerated Manager
description: Cette page présente un aperçu de la phase de préparation de Cloud Acceleration Manager.
exl-id: 91a13cae-4934-42e8-9538-896fd72f5acb
source-git-commit: 3fea3da263216c8250fd1ba3e3b1edd73b5c8940
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 11%

---

# Phase de préparation dans Cloud Accelerated Manager {#readiness-phase-cam}

Une fois que vous avez créé un projet dans Cloud Acceleration Manager, vous pouvez commencer l’évaluation de votre mise en oeuvre AEM actuelle dans la phase de préparation.

La phase de préparation comprend :

* [Analyse des bonnes pratiques](#best-practices-analysis)
* [Planification et configuration](#planning-setup)

Suivez les étapes ci-dessous pour accéder à la phase de préparation :

1. Cliquez sur la carte de votre projet pour ouvrir la page d’entrée du projet.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-landing1.png)

1. Accédez à la section **Préparation**, comme illustré dans la figure ci-dessous.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >Pour en savoir plus, voir Création et gestion d’un projet dans Cloud Acceleration Manager .

## Utilisation de la carte d’analyse des bonnes pratiques {#best-practices-analysis}

Suivez les étapes ci-dessous pour utiliser la carte Analyse des bonnes pratiques :

1. Cliquez sur le bouton **Réviser** de la carte **Analyse des bonnes pratiques**.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-2.png)

1. Pour télécharger BPA (Best Practices Analyzer), procédez comme suit :

   >[!NOTE]
   >Pour éviter toute incidence sur les instances critiques de l’entreprise, il est recommandé d’exécuter BPA dans un environnement de création aussi proche que possible de l’environnement de production concernant la personnalisation, la configuration, les contenus et les applications utilisateur. Vous pouvez également l’exécuter sur un clone de l’environnement de création de production.

   1. Accédez au portail [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) et téléchargez l’analyseur des bonnes pratiques sous la forme d’un fichier zip.

      >[!NOTE]
      >Passez en revue [Utilisation de l’analyseur des bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en#imp-considerations) pour savoir comment exécuter BPA.

   1. Exporter le rapport au format CSV

1. Cliquez sur **Charger un nouveau rapport** pour charger le rapport BPA dans le CAM.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-3.png)

   >[!IMPORTANT]
   >Le rapport ne peut pas être chargé si vous êtes en mode Incognito du navigateur.

1. Une fois que vous avez chargé un nouveau rapport, le rapport Analyse des bonnes pratiques s’affiche.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

1. Consultez et explorez le tableau de bord de l’analyse des bonnes pratiques dans CAM. Pour plus d’informations, reportez-vous à la section ci-dessous [Examen du rapport d’analyse des bonnes pratiques](#analysis-report) .

   >[!NOTE]
   >Le téléchargement d’un nouveau rapport réinitialise toutes les évaluations.

1. Cliquez sur l’icône **Aperçu de l’impression**, comme illustré ci-dessous.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/bpa-printpreview1.png)

1. Cliquez sur **Aperçu de l’impression** pour ouvrir un nouvel onglet avec le rapport affiché dans un aperçu imprimable. Cliquez sur **Imprimer** pour imprimer le rapport dans un format PDF afin d’en faciliter la partage.

   >[!IMPORTANT]
   >* L’option **Enregistrer en tant que PDF** est recommandée et prise en charge pour les fonctionnalités ci-dessus.
   >* Si le bouton d’impression du navigateur est utilisé, il n’imprime qu’une seule page.


   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/bpa-printpreview2.png)

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

Cette carte **Aperçu du rapport** fournit les résultats du rapport et les niveaux de gravité qui s’appliquent lors de l’évaluation de la préparation à AEM as a Cloud Service, comme illustré dans la figure ci-dessous.

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

L’option Évaluation de la complexité de la migration permet d’évaluer la complexité de la migration de la mise en oeuvre AEM existante vers AEM as a Cloud Service.

Vous pouvez consulter les informations suivantes dans cet onglet :

* Présentation de l’instance AEM
* Évaluation
* Considérations relatives à la migration de contenu

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/migration-complexity-1.png)

## Utilisation de la carte Planification et configuration {#planning-setup}

Consultez cette section pour découvrir la carte de l’activité Planification et configuration .

1. Cliquez sur le bouton **Afficher** à partir de la carte **Planification et configuration**. Cette carte fournit tout le contenu approprié qui vous aidera à planifier et à configurer votre migration AEM.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-view.png)

1. Un carrousel de contenu affiche toutes les informations pertinentes pour cette phase du parcours de migration.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5-planning.png)

## Et après ? {#whats-next}

Une fois que vous avez appris à vous connecter à Cloud Acceleration Manager et à créer un projet, vous êtes prêt à passer à l’étape suivante de la [phase d’implémentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=en).
