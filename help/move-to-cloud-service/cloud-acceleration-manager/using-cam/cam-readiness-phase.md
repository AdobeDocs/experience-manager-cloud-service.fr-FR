---
title: Phase de préparation dans Cloud Accelerated Manager
description: Cette page présente un aperçu de la phase de préparation dans Cloud Acceleration Manager.
exl-id: 91a13cae-4934-42e8-9538-896fd72f5acb
source-git-commit: 7737a9e6a0182fc98bf39da97c52f120139a2cc4
workflow-type: tm+mt
source-wordcount: '1057'
ht-degree: 64%

---

# Phase de préparation dans Cloud Accelerated Manager {#readiness-phase-cam}

Une fois que vous avez créé un projet dans Cloud Acceleration Manager, vous pouvez commencer l’évaluation de votre mise en œuvre AEM actuelle dans la phase de préparation.

La phase de préparation comprend :

* [Analyse des bonnes pratiques](#best-practices-analysis)
* [Planification et configuration](#planning-setup)

Suivez les étapes ci-dessous pour accéder à la phase de préparation :

1. Cliquez sur la carte de votre projet pour ouvrir sa page d’entrée.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-landing1.png)

1. Accédez à la section **Préparation**, comme illustré dans la figure ci-dessous.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >Pour en savoir plus, voir la section Création et gestion d’un projet dans Cloud Acceleration Manager.

## Utilisation de la carte d’analyse des bonnes pratiques {#best-practices-analysis}

Suivez les étapes ci-dessous pour utiliser la carte Analyse des bonnes pratiques :

1. Cliquez sur le bouton **Réviser** de la carte **Analyse des bonnes pratiques**.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-2.png)

1. Pour télécharger l’analyseur de bonnes pratiques (BPA), procédez comme suit :

   >[!NOTE]
   >Pour éviter toute incidence sur les instances critiques de l’entreprise, il est recommandé d’exécuter BPA dans un environnement de création aussi proche que possible de l’environnement de production concernant la personnalisation, la configuration, les contenus et les applications utilisateur. Vous pouvez également l’exécuter sur un clone de l’environnement de création de production.

   1. Accédez au portail de [Distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) et téléchargez l’analyseur de bonnes pratiques sous la forme d’un fichier zip.

      >[!NOTE]
      >Consultez la section [Utilisation de l’analyseur de bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=fr#imp-considerations) pour savoir comment exécuter BPA.

   1. Exporter le rapport au format CSV

1. Cliquez sur **Charger un nouveau rapport** pour charger le rapport BPA dans CAM.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-3.png)

   >[!IMPORTANT]
   >Le rapport ne peut pas être chargé si vous êtes en mode Incognito du navigateur.

1. Une fois que vous avez chargé un nouveau rapport, le rapport Analyse des bonnes pratiques s’affiche.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

1. Consultez et explorez le tableau de bord d’analyse des bonnes pratiques dans CAM. Pour plus d’informations, reportez-vous à la section ci-dessous [Consultation du rapport d’analyse des bonnes pratiques](#analysis-report).

   >[!NOTE]
   >Le chargement d’un nouveau rapport réinitialise toutes les évaluations.

### Utilisation de l’aperçu avant impression {#print-preview-cam}

Vous pouvez sélectionner l’option d’aperçu avant impression dans Cloud Acceleration Manager pour un aperçu imprimable des rapports ou pour imprimer le rapport dans un format PDF afin d’en faciliter la partage.

Suivez les étapes ci-dessous :

1. Cliquez sur **Aperçu de l’impression** , comme illustré ci-dessous.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/bpa-printpreview1.png)

1. Cliquez sur **Aperçu de l’impression** ouvre un nouvel onglet avec le rapport affiché dans un aperçu imprimable. Cliquez sur **Imprimer** pour imprimer le rapport au format PDF.

   >[!IMPORTANT]
   >* L’option **Enregistrer en tant que PDF** est recommandé et pris en charge pour les fonctionnalités ci-dessus.
   >* Si le bouton d’impression du navigateur est utilisé, il n’imprime qu’une seule page.


   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/bpa-printpreview2.png)

### Utilisation de l’option Afficher la courbe de tendance {#trendline-view-cam}

Lorsque vous transférez plusieurs rapports Analyseur des bonnes pratiques (BPA) dans un projet, vous pouvez sélectionner la variable **Afficher la tendance** pour afficher et comparer les résultats des rapports BPA historiques.

Pour afficher les rapports à partir de l’option de tendance, procédez comme suit :

>[!NOTE]
>Lorsque vous transférez plusieurs rapports d’application d’une seule page dans un projet, la variable **...** icône .

1. Accédez à votre projet et cliquez sur **Réviser** de la **Analyse des bonnes pratiques** dans la **Préparation** phase.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Cliquez sur le bouton **...** pour afficher la liste déroulante.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1.png)

   >[!IMPORTANT]
   >Le rapport affiché est toujours celui dont la date de rapport est la plus récente.

1. Cliquez sur **Afficher la tendance**, comme illustré dans la figure ci-dessous.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view2.png)

1. Cliquez sur **Afficher la tendance** ouvre la vue de tendance du rapport, comme illustré dans la figure ci-dessous.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view3a.png)


   >[!NOTE]
   >Le rapport de tendance affiche sous forme graphique les résultats des rapports BPA historiques.
   >
   >Deux graphiques affichent la tendance de :
   >1. **Tendance des résultats du rapport**
   >1. **Composants personnalisés et tendance de modèle**

   >
   >Vous pouvez ajouter ou modifier la vue graphique à partir de la liste déroulante, comme illustré dans la figure ci-dessous :
   >![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/reports-bpa1.png)


### Consultation du rapport d’analyse des bonnes pratiques {#analysis-report}

Consultez les cartes suivantes disponibles sur la page Rapport d’analyse des bonnes pratiques :

![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> Avec chaque carte, vous pouvez :
>* cliquer sur la carte pour ouvrir son onglet associé ;
>* mettre en signet tous les onglets du rapport (y compris le filtrage) pour les partager ou les récupérer ultérieurement ;
>* utiliser l’icône de détails pour afficher les détails de chaque résultat de rapport.


#### Propriétés du rapport {#report-properties}

La carte **Propriétés du rapport** donne des informations sur les propriétés du rapport, notamment la date du rapport, la durée, les filtres, la date de transfert et les détails d’Adobe Experience Manager (AEM).

![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-properties.png)

#### Aperçu du rapport {#report-overview}

Cette carte **Aperçu du rapport** donne les résultats du rapport et les niveaux de gravité à appliquer lors de l’évaluation de la préparation pour une migration vers AEM as a Cloud Service, comme illustré dans la figure ci-dessous.

![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview.png)

Cliquez sur ce rapport pour ouvrir l’onglet **Rapport**.

![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview2.png)

Vous pouvez filtrer le rapport par critère d’importance, de sous-type ou de nombre.

![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>Voir [Interprétation du rapport de l’analyseur de bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=fr) pour en savoir plus sur les catégories de résultats et les niveaux d’importance.

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

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/migration-complexity-1.png)

## Utilisation de la carte Planification et configuration {#planning-setup}

Consultez cette section pour découvrir la carte de l’activité Planification et configuration.

1. Cliquez sur le bouton **Afficher** dans la carte **Planification et configuration**. Cette carte fournit tout le contenu approprié pour vous aider à planifier et à configurer votre migration AEM.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-view.png)

1. Un carrousel de contenu affiche toutes les informations pertinentes pour cette phase du parcours de migration.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5-planning.png)

### Suppression d’un rapport d’analyse des bonnes pratiques {#delete-trendline}

Pour supprimer un rapport de la vue Trendline, procédez comme suit :

>[!IMPORTANT]
>Un rapport ne peut être supprimé que lorsque plusieurs rapports ont été chargés dans un projet.

1. Accédez à votre projet et cliquez sur **Réviser** de la **Analyse des bonnes pratiques** dans la **Préparation** phase.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Cliquez sur le bouton **...** pour afficher la liste déroulante.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1.png)

1. Cliquez sur **Afficher la tendance**, comme illustré dans la figure ci-dessous.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view2.png)

1. Cliquez sur l’icône de suppression dans la **Rapport de tendance** écran.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view5a.png)

1. Cliquez sur **Supprimer** pour confirmer la suppression.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view6a.png)

## Et après ? {#whats-next}

Une fois que vous avez appris à vous connecter à Cloud Acceleration Manager et à créer un projet, vous êtes prêt à passer à l’étape suivante de la [phase d’implémentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=fr).
