---
title: Phase de préparation dans Cloud Accelerated Manager
description: Cette page présente un aperçu de la phase de préparation dans Cloud Acceleration Manager.
exl-id: 2583985b-0358-433c-9d31-38e2c60dc3dc
source-git-commit: ecf4c06fd290d250c14386b3135250633b26c910
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 55%

---

# Phase de préparation dans Cloud Accelerated Manager {#readiness-phase-cam}

Une fois que vous avez créé un projet dans Cloud Acceleration Manager, vous pouvez commencer l’évaluation de votre mise en oeuvre Adobe Experience Manager (AEM) actuelle lors de la phase de préparation.

La phase de préparation comprend :

* [Analyse des bonnes pratiques](#best-practices-analysis)
* [Planification et configuration](#planning-setup)

Suivez les étapes ci-dessous pour accéder à la phase de préparation :

1. Cliquez sur la carte de votre projet.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/cam-landing1.png)

1. Sur la page d’entrée du projet, accédez au **Préparation** , comme illustré dans la figure ci-dessous.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >Pour en savoir plus, voir Création et gestion d’un projet dans Cloud Acceleration Manager.

## Utilisation de la carte d’analyse des bonnes pratiques {#best-practices-analysis}

1. Cliquez sur **Réviser** de la **Analyse des bonnes pratiques** carte.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-2.png)

1. Téléchargez BPA (Best Practices Analyzer).

   >[!NOTE]
   >Pour éviter tout impact sur les instances critiques de l’entreprise, Adobe vous recommande d’exécuter BPA dans un environnement de création. L’environnement doit être aussi proche que possible de l’environnement de production en ce qui concerne la personnalisation, la configuration, le contenu et les applications utilisateur. Vous pouvez également l’exécuter sur un clone de l’environnement de création de production.

   1. Accédez au [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?lang=fr) Portal et téléchargez l’analyseur des bonnes pratiques sous la forme d’un fichier zip.

      >[!NOTE]
      >Consultez la section [Utilisation de l’analyseur de bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html#imp-considerations) pour savoir comment exécuter BPA.

   1. Exporter le rapport au format CSV

1. Cliquez sur **Charger un nouveau rapport** vous pouvez donc télécharger le rapport BPA dans CAM.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-3.png)

   >[!IMPORTANT]
   >Le rapport ne peut pas être chargé si vous êtes en mode Incognito dans le navigateur.

1. Une fois que vous avez chargé un nouveau rapport, vous pouvez consulter le rapport Analyse des bonnes pratiques .

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

1. Consultez et explorez le tableau de bord d’analyse des bonnes pratiques dans CAM. Reportez-vous à la section [Affichage du rapport d’analyse des bonnes pratiques](#analysis-report) pour plus d’informations.

   >[!NOTE]
   >Le chargement d’un nouveau rapport réinitialise toutes les évaluations.

### Utilisation de l’aperçu avant impression {#print-preview-cam}

Vous pouvez sélectionner l’option d’aperçu avant impression dans Cloud Acceleration Manager pour obtenir un aperçu imprimable des rapports ou pour imprimer le rapport au format PDF afin d’en faciliter la partage.

Suivez les étapes ci-dessous :

1. Cliquez sur le bouton **Aperçu de l’impression** Icône

   ![image](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview1.png)

1. Dans le nouvel onglet du rapport affiché dans un aperçu imprimable, cliquez sur **Imprimer** pour imprimer le rapport au format PDF.

   >[!IMPORTANT]
   >
   >* L’option **Enregistrer en tant que PDF** est recommandée et prise en charge pour les fonctionnalités ci-dessus.
   >* Si le bouton d’impression du navigateur est utilisé, il n’imprime qu’une seule page.

   ![image](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview2.png)

### Utiliser l’option Afficher la tendance {#trendline-view-cam}

Lorsque vous chargez plusieurs rapports de l’analyseur de bonnes pratiques (BPA) dans un projet, vous pouvez sélectionner l’option **Afficher la tendance** pour afficher et comparer les résultats des rapports BPA historiques.

Pour afficher les rapports à partir de l’option de tendance, procédez comme suit :

>[!NOTE]
>Lorsque vous transférez plusieurs rapports d’application monopage dans un projet, le **..** Icône

1. Accédez à votre projet et cliquez sur **Réviser** de la **Analyse des bonnes pratiques** dans la **Préparation** phase.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Cliquez sur **..**.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1.png)

   >[!IMPORTANT]
   >Le rapport affiché est toujours celui dont la date de rapport est la plus récente.

1. Dans la liste déroulante, cliquez sur **Afficher la tendance**, comme illustré dans la figure ci-dessous.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view2.png)

1. Cliquer **Afficher la tendance** ouvre la vue de tendance du rapport.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view3a.png)


   >[!NOTE]
   >Le Rapport de tendances affiche sous forme graphique les résultats des rapports BPA historiques.
   >
   >Deux graphiques s’affichent avec la tendance de :
   > 
   >1. **Tendance des résultats du rapport**
   >1. **Tendance de modèle et de composants personnalisés**
   >
   >Vous pouvez ajouter ou modifier la vue graphique par le biais de la liste déroulante, comme illustré dans la figure ci-dessous :
   >![image](/help/journey-migration/cloud-acceleration-manager/assets/reports-bpa1.png)


### Consultation du rapport d’analyse des bonnes pratiques {#analysis-report}

Consultez les cartes suivantes disponibles sur la page Rapport d’analyse des bonnes pratiques :

![image](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> Avec chaque carte, vous pouvez :
>
>* ouvrir l’onglet associé ;
>* mettre en signet tous les onglets du rapport (y compris le filtrage) pour les partager ou les récupérer ultérieurement ;
>* utiliser l’icône de détails pour afficher les détails de chaque résultat de rapport.

#### Propriétés du rapport {#report-properties}

La carte **Propriétés du rapport** donne des informations sur les propriétés du rapport, notamment la date du rapport, la durée, les filtres, la date de chargement et les détails d’Adobe Experience Manager (AEM).

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-properties.png)

#### Aperçu du rapport {#report-overview}

Cette carte **Aperçu du rapport** donne les résultats du rapport et les niveaux de gravité à appliquer lors de l’évaluation de la préparation pour une migration vers AEM as a Cloud Service, comme illustré dans la figure ci-dessous.

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-overview.png)

Cliquez sur ce rapport pour ouvrir la **Rapport** .

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-overview2.png)

Vous pouvez filtrer le rapport selon son importance, son sous-type ou son nombre.

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>Voir [Interprétation du rapport de l’analyseur de bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html) pour en savoir plus sur les catégories de résultats et les niveaux d’importance.

#### Évaluation des bonnes pratiques {#best-practices-assessment}

L’option Évaluation des bonnes pratiques donne une évaluation de votre instance AEM actuelle mais aussi des conseils à propos des étapes nécessaires pour adopter les bonnes pratiques AEM. Vous pouvez consulter les informations suivantes grâce à cet onglet :

* Présentation de l’instance AEM
* Composants et modèles personnalisés
* Autres résultats
* Requêtes lentes
* Tâches de maintenance

#### Évaluation de la complexité de la migration {#migration-complexity-assessment}

L’option Évaluation de la complexité de la migration permet d’évaluer la complexité de la migration entre l’implémentation existante d’AEM et AEM as a Cloud Service.

Vous pouvez consulter les informations suivantes grâce à cet onglet :

* Présentation de l’instance AEM
* Évaluation
* Considérations relatives à la migration de contenu

  ![image](/help/journey-migration/cloud-acceleration-manager/assets/migration-complexity-1.png)

## Utilisation de la carte Planification et configuration {#planning-setup}

1. Cliquez sur **Affichage** de la **Planification Et Configuration** carte. Cette carte fournit tout le contenu approprié qui vous aide à planifier et à configurer votre migration AEM.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-view.png)

1. Un carrousel de contenu affiche toutes les informations pertinentes pour cette phase du parcours de migration.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-5-planning.png)

### Suppression d’un rapport d’analyse des bonnes pratiques de la vue de tendance {#delete-trendline}

>[!IMPORTANT]
>Un rapport peut être supprimé uniquement lorsque plusieurs rapports ont été chargés dans un projet.

1. Accédez à votre projet et cliquez sur **Réviser** de la **Analyse des bonnes pratiques** dans la **Préparation** phase.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Cliquez sur **..**.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1.png)

1. Dans la liste déroulante, cliquez sur **Afficher la tendance**, comme illustré dans la figure ci-dessous.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view2.png)

1. Cliquez sur l’icône de suppression dans la **Rapport de tendance** écran.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view5a.png)

1. Cliquez sur **Supprimer** pour confirmer la suppression.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view6a.png)

## Prochaines étapes {#whats-next}

Une fois que vous avez appris à vous connecter à Cloud Acceleration Manager et à créer un projet, vous êtes prêt à passer en revue l’étape suivante dans la [Phase de mise en oeuvre](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html).
