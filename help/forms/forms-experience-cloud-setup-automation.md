---
title: Activation d’Adobe Analytics pour un formulaire adaptatif à l’aide de l’automatisation de la configuration Experience Cloud
description: L’automatisation de la configuration des Experience Cloud permet de connecter Adobe Analytics à un formulaire adaptatif. Il permet d’effectuer le suivi et l’analyse des interactions utilisateur avec un formulaire adaptatif, en fournissant des informations sur les interactions et l’engagement des visiteurs.
source-git-commit: 96b3986f73ab71bad02b00ddc699aeecd498aebd
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 2%

---


# Activation d’Adobe Analytics pour un formulaire adaptatif à l’aide de l’automatisation de la configuration Experience Cloud {#integrate-adobe-analytics-to-aem-forms-with-experience-cloud-setup-automation}

L’automatisation de la configuration des Experience Cloud permet de connecter Adobe Analytics à Adaptive Forms, ce qui facilite le suivi et l’analyse des interactions utilisateur avec vos formulaires et offre des informations sur les interactions et l’engagement des visiteurs. L’automatisation de la configuration des Experience Cloud permet également de surveiller les performances des formulaires, ce qui implique d’évaluer des mesures telles que les temps d’achèvement et les points d’abandon. Cette analyse permet d’optimiser les formulaires pour une meilleure expérience utilisateur tout en distinguant le comportement des utilisateurs en fonction de leur état de connexion, par exemple les utilisateurs anonymes, afin d’identifier les tendances et les modèles généraux.

## Avantages de l’intégration d’Adobe Analytics à Adaptive Forms {#advantages-of-integrating-adobe-analytics-with-aem-forms}

* **Informations sur le comportement de l’utilisateur final**: Adobe Analytics permet d’obtenir des informations sur le comportement de l’utilisateur final, de découvrir les actions de l’utilisateur, les abandons et les taux d’achèvement, ce qui permet de mieux comprendre comment les individus interagissent avec les formulaires.
* **Permettre aux utilisateurs professionnels non techniques d’obtenir des informations**: grâce à son interface conviviale, Adobe Analytics permet même aux utilisateurs non techniques d’accéder aux données d’utilisation de formulaire et de les interpréter, ce qui favorise les décisions pilotées par les données pour améliorer les expériences d’inscription.
* **Optimisation de l’expérience de capture de données en fonction de l’utilisation**: les entreprises identifient facilement les points douloureux de la capture de données, ce qui entraîne des améliorations ciblées qui améliorent la convivialité du formulaire et augmentent les envois réussis.

## Portée des mesures d’utilisation de Forms adaptatif {#scope-of-adaptive-forms-usage-metrics}

Adobe Analytics offre un tableau complet de mesures de performances de Forms adaptatif conçues pour fournir des informations précieuses sur l’utilisation des formulaires. Ces mesures sont les suivantes :

* **Rendus de formulaire, envois de formulaire, erreurs de validation et visiteurs uniques**, ce qui vous permet d’évaluer l’utilisation et l’efficacité de vos formulaires.

* **Informations sur les visiteurs** qui englobe les fréquences de visite et d’envoi, ainsi que le nombre de visiteurs uniques, offre une vue complète de l’audience de votre formulaire.

* **Type de périphérique** données qui vous informent sur les appareils utilisés par les utilisateurs pour accéder à vos formulaires.

* **Répartition géographique** révèle la distribution régionale des utilisateurs de vos formulaires.

* **Sources de trafic** et **Formulaires populaires** les mesures qui se composent des principaux domaines référents et des formulaires les plus consultés vous aident à comprendre d’où provient votre trafic et les formulaires les plus populaires.

* **Activité de l’utilisateur sur les formulaires principaux** fournit des informations sur les visites de champs, les rendus de formulaire, les erreurs de validation, les formulaires abandonnés et les envois de formulaire, ce qui vous permet d’analyser le comportement des utilisateurs.

* **Chronologie de la durée de consultation des formulaires** qui offre une vue chronologique de l’engagement des utilisateurs avec vos formulaires.

* **Zones nécessitant une assistance visiteur** mesures qui incluent les vues d’aide, les instances d’erreur de validation et les fréquences de visite de champ, soulignant où les utilisateurs peuvent avoir besoin d’aide pour remplir les formulaires.

![Rapport Analytics](assets/analytics-report.png)


Pour obtenir des informations détaillées sur chaque mesure, consultez [Affichage et compréhension des rapports AEM Forms Analytics](/help/forms/view-understand-aem-forms-analytics-reports.md)

## Conditions préalables requises {#prerequisites}

<!--
Analytics, Data Collection (Formerly Adobe Launch), and Experience Manager (experience.adobe.com)
-->

L’automatisation de la configuration des Experience Cloud dans Adobe Experience Manager Forms nécessite une **Licence Adobe Analytics**, **Collecte de données (anciennement Adobe Launch)** pour gérer les scripts de suivi et l’intégration à la variable **Experience Platform Launch (API)** pour une agrégation et une génération simplifiées de données.

Si vous disposez d’une licence active pour l’automatisation de la configuration des Experience Cloud, Adobe Analytics et l’API Experience Platform Launch, vous devez vérifier leur disponibilité dans votre console de développement.

Pour vérifier que les éléments ci-dessus sont disponibles pour votre environnement Forms as a Cloud Service, consultez la page [console de développement](https://developer.adobe.com/console/projects), accédez au projet et recherchez votre projet avec l’ID de programme, par exemple, pour l’environnement avec l’URL . `https://author-p45913-e175111-cmstg.adobeaemcloud.com/index.html`, l’ID de programme est `p45913-e175111`. Assurez-vous que l’Experience Cloud Setup Automation, Adobe Analytics et l’API Experience Platform Launch sont répertoriés. Si elles sont répertoriées, vous pouvez activer Adobe Analytics pour votre Forms adaptatif.

![Intégration de Forms Analytics requise](assets/analytics-aem.png)

<!-- 
>[!NOTE]
> If you have an active licenses for Experience Cloud Setup Automation, Adobe Analytics, and Experience Platform Launch API, you should verify their availability within your developer console.
-->

<!-- For more information about your available integrations, see [troubleshooting Adaptive Forms with Analytics Integration](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/view-understand-aem-forms-analytics-reports.html)
-->

## Configuration d’Adobe Analytics {#configure-adobe-analytics}

Pour activer et configurer Adobe Analytics pour votre Forms adaptatif, procédez comme suit :

* [Activation d’Adobe Analytics pour Forms adaptatif en fonction des composants de base](#integrate-adobe-analytics-with-aem-forms-for-foundation-component)
* [Activation d’Adobe Analytics pour Forms adaptatif en fonction des composants principaux](#integrate-adobe-analytics-with-aem-forms-for-core-components)

### Activation d’Adobe Analytics avec Forms adaptatif pour le composant Foundation {#integrate-adobe-analytics-with-aem-forms-for-foundation-component}

1. Créez un conteneur de configuration pour les services cloud :
   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
   1. Sélectionnez ou créez un conteneur de configuration, puis activez le dossier pour **[!UICONTROL Configurations du cloud]**.
   1. Appuyez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.
1. Sur votre instance AEM, accédez à **[Forms]** &quot; **[Forms et document]**.
1. Sélectionnez votre **[!UICONTROL Formulaire]** &quot; **[!UICONTROL Propriétés]**, dans la variable **[!UICONTROL Conteneur de configuration]**, sélectionnez le conteneur de configuration que vous avez créé ou sélectionné dans le **[!UICONTROL Explorateur de configuration]** à l’étape 1.
1. Sélectionnez le panneau Tâche sur le rail de gauche, puis cliquez sur **Configuration d’Analytics** et **Activer Adobe Analytics**.
1. Indiquez le nom que vous préférez pour la suite de rapports, puis cliquez sur **[!UICONTROL Suivant]** et **[!UICONTROL Enregistrer]**.
1. Une fois le projet enregistré, la configuration s’exécute pendant un certain temps jusqu’à l’intégration d’Adobe Analytics à votre formulaire adaptatif. Vous pouvez également vérifier la variable **état d’intégration**.

   >[!NOTE]
   >
   >Si votre configuration dure plus de 15 minutes, réessayez d’activer les analyses pour vos formulaires.

1. Sur votre instance AEM, accédez à **[!UICONTROL Forms]** &quot; **[Forms et document]** et sélectionnez votre **[!UICONTROL Formulaire]**, vous voyez qu’Adobe Analytics est intégré à votre formulaire, comme illustré dans l’image ci-dessous.
1. Maintenant, vous pouvez afficher votre [Rapport Adobe Analytics de formulaire adaptatif](#view-adobe-analytics-report).

![Analyses d’AEM intégrées](assets/analytics-aem-integrated.png)

### Activation d’Adobe Analytics avec Forms adaptatif pour les composants principaux {#integrate-adobe-analytics-with-aem-forms-for-core-components}

1. Sur votre instance AEM, accédez à **[!UICONTROL Forms]** &quot; **[!UICONTROL Forms et document]** et sélectionnez votre **[!UICONTROL Formulaire]**.
1. Sélectionnez le panneau Tâche à gauche, puis cliquez sur **Configuration d’Analytics** et **Activer Adobe Analytics**.
1. Indiquez le nom que vous préférez pour la suite de rapports, puis cliquez sur **[!UICONTROL Suivant]** et **[!UICONTROL Enregistrer]**.
1. Une fois le projet enregistré, la configuration s’exécute pendant un certain temps jusqu’à l’intégration d’Adobe Analytics à votre formulaire adaptatif. Vous pouvez également vérifier la variable **état d’intégration**.

   >[!NOTE]
   >
   >Si votre configuration dure plus de 15 minutes, réessayez d’activer les analyses pour vos formulaires.

1. Sur votre instance AEM, accédez à **[!UICONTROL Forms]** &quot; **[!UICONTROL Forms et document]** et sélectionnez votre **[!UICONTROL Formulaire]**, vous voyez qu’Adobe Analytics est intégré à votre formulaire.
1. Maintenant, vous pouvez afficher votre [Rapport Adobe Analytics de formulaire adaptatif](#view-adobe-analytics-report).

## Afficher le rapport Adobe Analytics d’Forms adaptatif {#view-adobe-analytics-report}

1. Sur votre instance AEM, accédez à **[!UICONTROL Forms]** &quot; **[!UICONTROL Forms et document]**.
1. Sélectionnez votre formulaire. Vous pouvez constater qu’Adobe Analytics est intégré, comme illustré à gauche, au Forms activé pour Adobe Analytics.

   ![Afficher le rapport](assets/activ-aa.png)

1. Cliquez sur **Adobe Analytics** pour afficher votre rapport et analyser les données de performances.

