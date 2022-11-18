---
title: Intégration d’Adobe Analytics à l’automatisation de la configuration des Experience Cloud
description: L’automatisation de la configuration des Experience Cloud offre un moyen simple et automatisé d’intégrer et d’instrumenter Experience Manager Sites avec les balises Experience Platform et Adobe Analytics à l’aide d’une interface d’assistant de l’interface utilisateur simple. Découvrez comment utiliser la configuration automatisée avec votre propre site.
feature: Administering
role: Admin
exl-id: 351ead2c-7b0d-4bd9-a020-47516948d467
source-git-commit: 539d3947964652dd92620ce0b0b057754742be96
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 66%

---

# Intégration d’Adobe Analytics à l’automatisation de la configuration des Experience Cloud {#integrate-adobe-analytics-automation-setup}

L’automatisation de la configuration des Experience Cloud offre un moyen simple et automatisé d’intégrer et d’instrumenter Experience Manager Sites avec les balises Experience Platform et Adobe Analytics à l’aide d’une interface d’assistant de l’interface utilisateur simple.

Il n’a jamais été aussi simple d’intégrer Adobe Analytics à AEM Sites. Grâce à l’automatisation de la configuration d’Experience Cloud, la configuration, l’intégration et l’instrumentation de votre site pour capturer les analyses de performance afin de comprendre à quel point vos clients s’engagent et convertissent sont prises en charge en quelques clics.

Cette vidéo explore la manière dont un site AEM est intégré à Experience Platform Tags and Analytics à l’aide de l’automatisation de la configuration de l’Experience Cloud :

>[!VIDEO](https://video.tv.adobe.com/v/345372/?quality=12)

## Conditions requises

La configuration de l’automatisation est conçue pour fonctionner d’emblée avec un site AEM créé à l’aide de [composants principaux AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) avec la [couche de données client Adobe](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html?lang=fr) activée. Vous pouvez générer un nouveau site sur lequel ces fonctionnalités sont activées automatiquement à l’aide de l’[archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) ou en créant un site à l’aide d’un [modèle de site](/help/journey-sites/quick-site/create-site.md).

## Prérequis {#prerequisites}

Avant d’utiliser cette fonctionnalité, il est important de suivre ces instructions pour vous assurer que les services prérequis ont été correctement configurés dans votre environnement :

1. Connectez-vous à Adobe Admin Console (https://adminconsole.adobe.com/).
1. Assurez-vous que l’identifiant de l’organisation IMS approprié est sélectionné dans le coin supérieur droit.
1. Cliquez sur l’option de navigation Produits .
1. Vérifiez que &quot;Adobe Experience Manager as a Cloud Service&quot; a été configuré pour l’organisation IMS.
1. Vérifiez que &quot;Adobe Analytics&quot; a été configuré pour l’organisation IMS.
1. Accédez à Cloud Manager (https://experience.adobe.com/cloud-manager).
1. Sélectionnez le programme approprié.
1. Vérifiez que l’environnement se trouve sur la dernière version de Cloud Service (dans le cas contraire, sélectionnez Mettre à jour dans les options de menu).
1. Exécutez un pipeline de pile complète dans Cloud Manager.

L’environnement doit maintenant être prêt pour l’automatisation de la configuration des Experience Cloud.

## Configuration

1. Accédez à **Sites** et sélectionnez la racine du site à intégrer à Adobe Analytics.
1. Développez le menu du rail latéral et appuyez sur **Configuration d’Analytics**.

   Il s’agit d’une nouvelle option du rail latéral qui ouvre un panneau qui fournit des contrôles et un état pour l’automatisation de la configuration de l’Experience Cloud.
1. Appuyez sur le bouton **Intégration d’Analytics**.
1. Dans la boîte de dialogue qui s’affiche, fournissez un nom au **Identifiant de suite de rapports**.

   Cette chaîne sera utilisée pour créer un nouvel [identifiant de suite de rapports](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=fr) dans Adobe Analytics comme magasin de données pour les données d’analyse du site AEM sélectionné. La chaîne fournie sera ajoutée avec les identifiants d’environnement et de niveau pour garantir l’unicité.

1. Actualisez la page et le panneau, puis appuyez sur **Vérification de l’état d’intégration** pour vérifier l’état de l’automatisation.

   La configuration de l’automatisation se produit de manière asynchrone. La **Vérification de l’état d’intégration** affiche l’état actuel de l’intégration.

   * **En cours** - indique que la tâche est en cours d’exécution.
   * **Intégration terminée** : indique que la tâche a terminé l’intégration d’Analytics et de Balises, la configuration des extensions Balises et des règles Balises et la création d’une suite de rapports dans Adobe Analytics.
   * **Échec** : indique que la tâche automatisée n’a pas pu se terminer correctement. Vérifiez les fichiers journaux de cette tâche en cliquant sur le lien Journaux.

## Validation de la configuration AEM

Une fois l’automatisation terminée, vérifiez que votre site déclenche désormais les événements Analytics.

1. Ouvrez une page de votre site à l’aide de l’**éditeur Sites**.
1. Utilisez l’option **Afficher comme publié(e)** pour charger une version publiée de la page.
1. Utilisez les outils de développement du navigateur pour examiner le trafic réseau et que **Balises** et `AppMeasurement.js` Les fichiers sont maintenant chargés.
1. Inspectez la console du navigateur pour voir que les événements au niveau de la page et du composant sont déclenchés et collectés par la couche de données client Adobe.

## Validation de la configuration d’Analytics

Ensuite, accédez à Adobe Analytics pour afficher les données provenant des événements sur le site d’AEM.

1. Accédez à Adobe Analytics dans la même organisation IMS que votre site AEM.
1. Création d’un rapport d’aperçu pour AEM Sites en accédant à **Rapports** > **Engagement** > **Adobe Experience Manager** > **Aperçu des performances du site**.
1. Appuyer sur **Ouvrir le rapport**.
1. Sélectionnez l’**Identifiant de suite de rapports** qui correspond au nom de la suite de rapports utilisé dans l’exercice précédent.
1. Affichez le flux de données d’analyse dans le nouveau modèle au fil du temps.

   >[!NOTE]
   >
   > Avec une nouvelle intégration, il peut s’écouler quelques heures avant que le rapport ne soit rempli de données.
