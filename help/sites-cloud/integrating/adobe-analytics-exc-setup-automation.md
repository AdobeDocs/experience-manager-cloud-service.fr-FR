---
title: Intégration à Adobe Analytics
description: 'Intégration à Adobe Analytics '
feature: Administering
role: Admin
source-git-commit: 4bf5ee1218f775efdc7829b790360033ad756c9a
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 5%

---


# Intégration d’Adobe Analytics à l’automatisation de la configuration des Experience Cloud {#integrate-adobe-analytics-automation-setup}

>[!CAUTION]
>
> Cette fonctionnalité est actuellement en version bêta interne. La version cible date du 1er trimestre 2022.

L’automatisation de la configuration des Experience Cloud offre un moyen simple et automatisé d’intégrer et d’instrumenter Experience Manager Sites avec Experience Platform Launch et Adobe Analytics à l’aide d’une interface simple d’assistant de l’interface utilisateur.

Il n’a jamais été aussi simple d’intégrer Adobe Analytics à AEM Sites. Avec l’automatisation de la configuration des Experience Cloud, la configuration, l’intégration et l’instrumentalisation de votre site pour capturer les analyses de performances afin de comprendre à quel point vos clients interagissent et convertissent sont entièrement pris en charge en quelques clics seulement.

Cette vidéo explore la manière dont un site AEM est intégré à Experience Platform Launch et Analytics à l’aide de l’automatisation de la configuration d’Experience Cloud :

>[!VIDEO](https://video.tv.adobe.com/v/339605/?quality=12)

## Conditions requises

La configuration de l’automatisation est conçue pour fonctionner de manière prête à l’emploi avec un site AEM créé à l’aide de [Composants principaux AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) avec le [Adobe de la couche de données client](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html?lang=fr) activée. Vous pouvez générer un nouveau site pour lequel ces fonctionnalités sont activées automatiquement à l’aide de la variable [AEM Archétype de projet](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) ou en créant un site à l’aide d’une [Modèle de site](/help/journey-sites/quick-site/create-site.md).

## Configuration

1. Accédez à **Sites** et sélectionnez la racine du site à intégrer à Adobe Analytics.
1. Développez le menu du rail latéral et appuyez sur **Configuration d’Analytics**.

   Il s’agit d’une nouvelle option du rail latéral qui ouvre un panneau qui fournit des contrôles et un état pour l’automatisation de la configuration de l’Experience Cloud.
1. Appuyez sur le bouton **Intégration d’Analytics** bouton .
1. Dans la boîte de dialogue qui s’affiche, donnez un nom au **Identifiant de suite de rapports**.

   Cette chaîne sera utilisée pour créer une [Identifiant de suite de rapports](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=en) dans Adobe Analytics comme entrepôt de données pour les données d’analyse du site AEM sélectionné. La chaîne fournie sera ajoutée avec les identifiants d’environnement et de niveau pour garantir l’unicité.

1. Actualisez la page et le panneau, puis appuyez sur **Vérification de l’état d’intégration** pour vérifier l’état de l’automatisation.

   La configuration de l’automatisation se produit de manière asynchrone. Le **Vérification de l’état d’intégration** affiche l’état actuel de l’intégration.

   * **En cours** - indique que la tâche est en cours d’exécution.
   * **Intégration terminée** : indique que la tâche a terminé l’intégration d’Analytics et de Launch, la configuration des extensions de Launch et des règles de Launch, ainsi que la création d’une suite de rapports dans Adobe Analytics.
   * **Échec** : indique que la tâche automatisée n’a pas pu se terminer correctement. Vérifiez les fichiers journaux de cette tâche en cliquant sur le lien Journaux .

## Validation de la configuration AEM

Une fois l’automatisation terminée, vérifiez que votre site déclenche désormais les événements Analytics.

1. Ouvrez une page de votre site à l’aide de la fonction **Éditeur de sites**.
1. Utilisez la variable **Afficher comme publié(e)** pour charger une version publiée de la page.
1. Utilisez les outils de développement du navigateur pour examiner le trafic réseau et que **Launch** et `AppMeasurement.js` Les fichiers sont maintenant chargés.
1. Inspect dans la console du navigateur pour voir que les événements au niveau de la page et du composant sont déclenchés et collectés par la couche de données client Adobe.

## Validation de la configuration d’Analytics

Ensuite, accédez à Adobe Analytics pour afficher les données provenant des événements sur le site d’AEM.

1. Accédez à Adobe Analytics dans la même organisation IMS que votre site AEM.
1. Création d’un rapport d’aperçu pour AEM Sites en accédant à **Rapports** > **Engagement** > **Adobe Experience Manager** > **Aperçu des performances du site**.
1. Appuyer **Ouvrir le rapport**.
1. Sélectionnez la **Identifiant de suite de rapports** qui correspond au nom de la suite de rapports utilisé dans l’exercice précédent.
1. Affichez le flux de données d’analyse dans le nouveau modèle au fil du temps.

   >[!NOTE]
   >
   > Avec une nouvelle intégration, il peut s’écouler quelques heures avant que le rapport ne soit rempli de données.
