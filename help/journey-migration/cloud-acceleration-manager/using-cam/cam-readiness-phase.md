---
title: Phase de préparation dans Cloud Accelerated Manager
description: Cette page présente un aperçu de la phase de préparation dans Cloud Acceleration Manager.
exl-id: 2583985b-0358-433c-9d31-38e2c60dc3dc
feature: Migration
role: Admin
source-git-commit: 3a0576e62518240b89290a75752386128b1ab082
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 37%

---

# Phase de préparation dans Cloud Accelerated Manager {#readiness-phase-cam}

Une fois que vous avez créé un projet dans Cloud Acceleration Manager (CAM), vous pouvez commencer l’évaluation de votre implémentation Adobe Experience Manager (AEM) actuelle dans la phase de Préparation .

La phase de préparation comprend :

* [Analyse des bonnes pratiques](#best-practices-analysis)
* [Planification et configuration](#planning-setup)

Suivez les étapes ci-dessous pour accéder à la phase de préparation :

1. Cliquez sur la carte de votre projet.

   ![Carte du projet](/help/journey-migration/cloud-acceleration-manager/assets/cam-landing1.png)

1. Sur la page de destination du projet, accédez à la section **Préparation**, comme illustré dans la figure ci-dessous.

   ![Préparation](/help/journey-migration/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >Pour en savoir plus, voir Création et gestion d’un projet dans Cloud Acceleration Manager.

## Utilisation de la carte d’analyse des bonnes pratiques {#best-practices-analysis}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_bpa"
>title="Rapport d’analyse des bonnes pratiques"
>abstract="Le rapport de l’analyseur des bonnes pratiques peut être chargé vers CAM afin de fournir une analyse de celui-ci par rapport à la migration vers AEM as a Cloud Service."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer" text="Utilisation de l’analyseur des bonnes pratiques"

1. Cliquez sur **Réviser** dans la vignette **Analyse des bonnes pratiques**.

   ![Analyse des bonnes pratiques - Révision](/help/journey-migration/cloud-acceleration-manager/assets/readiness-2.png)

1. Téléchargez l’analyseur de bonnes pratiques (BPA).

   >[!NOTE]
   >Pour éviter toute incidence sur les instances critiques de l’entreprise, Adobe vous recommande d’exécuter BPA dans un environnement de création. L’environnement doit être aussi proche que possible de l’environnement de production concernant la personnalisation, la configuration, le contenu et les applications utilisateur. Vous pouvez également l’exécuter sur un clone de l’environnement de création de production.

   1. Accédez au portail [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?fulltext=best*) et téléchargez l’analyseur des bonnes pratiques sous la forme d’un fichier zip.

      >[!NOTE]
      >Consultez la section [Utilisation de l’analyseur de bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=fr#imp-considerations) pour savoir comment exécuter BPA.

1. Dans CAM, cliquez sur **Obtenir la clé de chargement** afin d’obtenir la clé utilisée pour configurer votre système pour charger automatiquement les rapports BPA directement dans CAM.

   ![Obtenir la clé de chargement](/help/journey-migration/cloud-acceleration-manager/assets/readiness-3b.png)

   >[!IMPORTANT]
   >Le rapport peut toujours être chargé manuellement, mais l’utilisation de la touche de chargement simplifie l’opération. Notez que le rapport ne peut pas être chargé manuellement si sa taille est d’environ 200MB ou supérieure. Le rapport ne peut pas non plus être chargé à l’aide du mode Incognito du navigateur.

1. Une fois qu’un nouveau rapport a été chargé, le rapport Analyse des bonnes pratiques s’affiche dans CAM.

   ![&#x200B; Rapport d’analyse des bonnes pratiques &#x200B;](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

   >[!NOTE]
   >Si plusieurs rapports différents sont chargés, le rapport qui s’affiche en détail est toujours celui qui comporte la date de création la plus récente (et non la date de chargement).

1. Consultez et explorez le tableau de bord d’analyse des bonnes pratiques dans CAM. Reportez-vous à la section [Affichage du rapport d’analyse des bonnes pratiques](#analysis-report) pour plus d’informations.

   >[!NOTE]
   >Le chargement d’un nouveau rapport réinitialise toutes les évaluations s’il est plus récent que le rapport précédemment chargé.

### Utilisation de l’aperçu avant impression {#print-preview-cam}

Vous pouvez sélectionner l’option d’aperçu avant impression dans Cloud Acceleration Manager pour obtenir un aperçu imprimable des rapports ou pour imprimer le rapport au format PDF afin d’en faciliter la partage.

Suivez les étapes ci-dessous :

1. Cliquez sur l’action **Aperçu de l’impression**.

   ![Aperçu avant impression](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview1b.png)

1. Dans le nouvel onglet avec le rapport affiché dans un aperçu imprimable, cliquez sur **Imprimer** pour imprimer le rapport au format PDF.

   >[!IMPORTANT]
   >
   >* L’option **Enregistrer en tant que PDF** est recommandée et prise en charge pour les fonctionnalités ci-dessus.
   >* Si vous utilisez le bouton d’impression du navigateur, une seule page est imprimée.

   ![Imprimer](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview2.png)

### Utiliser l’option Afficher la tendance {#trendline-view-cam}

Lorsque vous chargez plusieurs rapports distincts de l’analyseur de bonnes pratiques (BPA) dans un projet, vous pouvez sélectionner l’option **Afficher la tendance** pour afficher et comparer les résultats des rapports BPA historiques.

Pour afficher les rapports à partir de l’option de tendance, procédez comme suit :

>[!NOTE]
>Lorsque vous chargez plusieurs rapports BPA distincts dans un projet, l’icône **...** s’affiche. Les rapports sont considérés comme identiques (non distincts) si leur hôte et leur heure de création sont identiques.

1. Accédez à votre projet et cliquez sur **Révision** dans la vignette **Analyse des bonnes pratiques** de la phase **Préparation**.

   ![Analyse des bonnes pratiques - Révision](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Dans la liste déroulante **Vue**, cliquez sur **Rapport de tendances**, comme illustré dans la figure ci-dessous.

   ![Rapport de tendances](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1b.png)

1. Cliquez sur **Rapport de tendances** pour ouvrir la vue de tendance du rapport.

   ![Vue Tendance](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view3a.png)


   >[!NOTE]
   >Le Rapport de tendances affiche sous forme graphique les résultats des rapports BPA historiques.
   >
   >Deux graphiques affichent les tendances suivantes :
   > 
   >1. **Tendance des résultats du rapport**
   >1. **Tendance de modèle et de composants personnalisés**
   >
   >Vous pouvez ajouter ou modifier la vue graphique à l&#39;aide de la liste déroulante, comme dans l&#39;exemple ci-dessous :
   >![Sélectionnez la vue graphique](/help/journey-migration/cloud-acceleration-manager/assets/reports-bpa1.png)


### Consultation du rapport d’analyse des bonnes pratiques {#analysis-report}

Consultez les cartes suivantes disponibles sur la page Rapport d’analyse des bonnes pratiques :

![&#x200B; Rapport d’analyse des bonnes pratiques &#x200B;](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> Avec chaque carte, vous pouvez :
>
>* ouvrir son onglet associé
>* mettre en signet tous les onglets du rapport (y compris le filtrage) pour les partager ou les récupérer ultérieurement ;
>* utiliser l’icône de détails pour afficher les détails de chaque résultat de rapport.

#### Propriétés du rapport {#report-properties}

La carte **Propriétés du rapport** donne des informations sur les propriétés du rapport, notamment la date du rapport, la durée, les filtres, la date de chargement et les détails d’Adobe Experience Manager (AEM).

![&#x200B; Propriétés du rapport &#x200B;](/help/journey-migration/cloud-acceleration-manager/assets/report-properties.png)

#### Aperçu du rapport {#report-overview}

Cette carte **Aperçu du rapport** donne les résultats du rapport et les niveaux de gravité à appliquer lors de l’évaluation de la préparation pour une migration vers AEM as a Cloud Service, comme illustré dans la figure ci-dessous.

![Aperçu du rapport](/help/journey-migration/cloud-acceleration-manager/assets/report-overview.png)

Cliquez sur ce rapport pour ouvrir l’onglet **Rapport**.

![Onglet Rapport](/help/journey-migration/cloud-acceleration-manager/assets/report-overview2.png)

Vous pouvez filtrer le rapport par importance, sous-type ou nombre.

![Filtres de rapports](/help/journey-migration/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>Voir [Interprétation du rapport de l’analyseur de bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=fr) pour en savoir plus sur les catégories de résultats et les niveaux d’importance.

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

  ![Évaluation de la complexité de la migration](/help/journey-migration/cloud-acceleration-manager/assets/migration-complexity-1.png)

## Utilisation de la carte Planification et configuration {#planning-setup}

1. Cliquez sur **Afficher** dans la carte **Planification et configuration**. Cette carte fournit tout le contenu approprié pour vous aider à planifier et à configurer votre migration AEM.

   ![Planification Et Configuration - Affichage](/help/journey-migration/cloud-acceleration-manager/assets/readiness-view.png)

1. Un carrousel de contenu affiche toutes les informations pertinentes pour cette phase du parcours de migration.

   ![Carrousel de planification et de configuration](/help/journey-migration/cloud-acceleration-manager/assets/readiness-5-planning.png)

### Suppression d’un rapport d’analyse des bonnes pratiques de la vue Tendance {#delete-trendline}

>[!IMPORTANT]
>Un rapport peut être supprimé uniquement lorsque plusieurs rapports ont été chargés dans un projet.

1. Accédez à votre projet et cliquez sur **Révision** dans la vignette **Analyse des bonnes pratiques** de la phase **Préparation**.

   ![Analyse des bonnes pratiques - Révision](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Cliquez sur **...**.

   ![&#x200B; Ellipse &#x200B;](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1.png)

1. Dans la liste déroulante, cliquez sur **Afficher la tendance**, comme illustré dans la figure ci-dessous.

   ![Afficher la tendance](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1b.png)

1. Cliquez sur l’icône de suppression dans l’écran **Rapport de tendances**.

   ![Rapport de tendances - Supprimer](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view5a.png)

1. Cliquez sur **Supprimer** pour confirmer la suppression.

   ![Supprimer](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view6a.png)

## Prochaines étapes {#whats-next}

Une fois que vous avez appris à vous connecter à Cloud Acceleration Manager et à créer un projet, vous êtes prêt à passer à l’étape suivante de la [phase d’implémentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=fr).
