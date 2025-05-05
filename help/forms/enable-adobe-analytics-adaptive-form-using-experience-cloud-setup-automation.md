---
title: Comment activer Adobe Analytics pour une analyse rapide d’un formulaire adaptatif ?
description: L’automatisation de la configuration des Experience Cloud permet de connecter Adobe Analytics à un formulaire adaptatif pour une analyse rapide et des informations sur les interactions et l’engagement des visiteurs.
keywords: Activation d’Adobe Analytics pour un formulaire adaptatif à l’aide de l’automatisation de la configuration de l’Experience Cloud, de l’activation d’Adobe Analytics dans Forms, d’Adobe Analytics dans le Forms adaptatif, de l’intégration de Forms Analytics, de Forms et d’Adobe Analytics
feature: Adaptive Forms
role: Admin, User
exl-id: 0e1aa040-08b4-4c1a-b247-ad6fff410187
source-git-commit: a23576b5dc6d78a29fe19cd23f3c4788f2bee23e
workflow-type: tm+mt
source-wordcount: '1588'
ht-degree: 6%

---

# Activation d’Adobe Analytics pour un formulaire adaptatif à l’aide de l’automatisation de la configuration Experience Cloud {#integrate-adobe-analytics-to-aem-forms-with-experience-cloud-setup-automation}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM as a Cloud Service | Cet article |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/configure-analytics-forms-documents.html?lang=fr) |

L’automatisation de la configuration des Experience Cloud permet de connecter Adobe Analytics à Adaptive Forms, ce qui permet d’analyser rapidement l’interaction des utilisateurs avec vos formulaires et d’offrir des informations sur les interactions et l’engagement des visiteurs. L’automatisation de la configuration des Experience Cloud permet également de surveiller les performances des formulaires, ce qui implique d’évaluer des mesures telles que les temps d’achèvement et les points d’abandon. Cette analyse permet d’optimiser les formulaires pour une meilleure expérience utilisateur tout en distinguant le comportement des utilisateurs en fonction de leur état de connexion, par exemple les utilisateurs anonymes, afin d’identifier les tendances et les modèles généraux.

## Avantages de l’intégration d’Adobe Analytics à Adaptive Forms {#advantages-of-integrating-adobe-analytics-with-aem-forms}

* **Informations sur le comportement de l’utilisateur final** : Adobe Analytics permet d’obtenir des informations sur le comportement de l’utilisateur final, de révéler les actions de l’utilisateur, les abandons et les taux d’achèvement, ce qui permet de mieux comprendre comment les individus interagissent avec les formulaires.
* **Permettre aux utilisateurs non techniques d’obtenir des informations** : grâce à son interface conviviale, Adobe Analytics permet même aux utilisateurs non techniques d’accéder aux données d’utilisation de formulaire et de les interpréter, ce qui favorise les décisions pilotées par les données pour améliorer les expériences d’inscription.
* **Optimisation de l’expérience de capture de données en fonction de l’utilisation** : les entreprises identifient facilement les points douloureux de la capture de données, ce qui entraîne des améliorations ciblées qui améliorent la convivialité du formulaire et augmentent les envois réussis.

## Portée des mesures d’utilisation de Forms adaptatif {#scope-of-adaptive-forms-usage-metrics}

Adobe Analytics offre un tableau complet de mesures de performances de Forms adaptatif conçues pour fournir des informations précieuses sur l’utilisation des formulaires et offre une analyse rapide. Ces mesures sont les suivantes :

* **Rendus de formulaire, envois de formulaire, erreurs de validation et visiteurs uniques**, ce qui vous permet d’évaluer l’utilisation et l’efficacité de vos formulaires.

* **Informations sur les visiteurs** qui englobent les fréquences de visite et d’envoi et le nombre de visiteurs uniques, offrant une vue complète de l’audience de votre formulaire.

* **Données de type d’appareil** qui vous informent sur les appareils utilisés par les utilisateurs pour accéder à vos formulaires.

* **La ventilation géographique** révèle la distribution régionale des utilisateurs de vos formulaires.

* Les mesures **Sources de trafic** et **Formulaires populaires** qui se composent des principaux domaines référents et formulaires les plus consultés vous aident à comprendre d’où provient votre trafic et quels formulaires sont les plus populaires.

* **L’activité de l’utilisateur sur les principaux formulaires** fournit des informations sur les visites de champs, les rendus de formulaire, les erreurs de validation, les formulaires abandonnés et les envois de formulaire, ce qui vous permet d’analyser le comportement de l’utilisateur.

* **Chronologie de la durée de consultation des formulaires** qui offre une vue chronologique de l’engagement des utilisateurs avec vos formulaires.

* **Zones nécessitant une assistance visiteur** qui comprennent des vues d’aide, des instances d’erreur de validation et des fréquences de visite de champ, soulignant où les utilisateurs peuvent avoir besoin d’aide pour remplir les formulaires.

![Rapport Analytics](assets/analytics-report.png){width="100%"}


Pour obtenir des informations détaillées sur chaque mesure, consultez la page [Affichage et compréhension des rapports AEM Forms Analytics](/help/forms/view-understand-aem-forms-analytics-reports.md)

## Conditions préalables {#prerequisites}

<!--
Analytics, Data Collection (Formerly Adobe Launch), and Experience Manager (experience.adobe.com)
-->

L’automatisation de la configuration de l’Experience Cloud nécessite une **licence Adobe Analytics**, une **collecte de données (anciennement Adobe Launch)** pour gérer les scripts de suivi et une **licence Experience Manager Forms** pour une agrégation et une génération d’informations simplifiées.

Si vous disposez d’une licence active pour **Adobe Analytics** et **Experience Manager Forms**, et que vous disposez d’une intégration à la **collecte de données (anciennement Adobe Launch)**, vous devez vérifier leur disponibilité dans votre console de développement.

Pour vérifier que les éléments ci-dessus sont disponibles pour votre environnement Forms as a Cloud Service, consultez la [console de développement](https://developer.adobe.com/console/projects), accédez au projet et recherchez votre projet avec l’ID de programme - l’ID d’environnement, par exemple, pour l’environnement avec l’URL `https://author-p45913-e175111-cmstg.adobeaemcloud.com/index.html`, l’ID de programme - l’ID d’environnement est `p45913-e175111`. Assurez-vous que l’Experience Cloud Setup Automation, Adobe Analytics et l’API Experience Platform Launch sont répertoriés. Si elles sont répertoriées, vous pouvez activer Adobe Analytics pour une analyse rapide de votre Forms adaptatif.

![Intégration Forms Analytics préalable](assets/analytics-aem.png){width="100%"}

<!-- 
>[!NOTE]
> If you have an active licenses for Experience Cloud Setup Automation, Adobe Analytics, and Experience Platform Launch API, you should verify their availability within your developer console.
-->

<!-- For more information about your available integrations, see [troubleshooting Adaptive Forms with Analytics Integration](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/view-understand-aem-forms-analytics-reports.html?lang=fr)
-->

## Configuration d’Adobe Analytics {#configure-adobe-analytics}

Pour activer et configurer Adobe Analytics pour une analyse rapide de votre Forms adaptatif, procédez comme suit :

* [Activation d’Adobe Analytics pour Forms adaptatif en fonction des composants de base](#integrate-adobe-analytics-with-aem-forms-for-foundation-component)
* [Activation d’Adobe Analytics pour Forms adaptatif en fonction des composants principaux](#integrate-adobe-analytics-with-aem-forms-for-core-components)

>[!VIDEO](https://video.tv.adobe.com/v/3424577/enable-adobe-analytics/?quality=12&learn=on)


<!--
>[!NOTE]
>
> This is the demo video for **Foundation Component**. In **Core Component** you are required to perform similar steps but the container is not chosen for forms.
-->

### Activation d’Adobe Analytics avec Forms adaptatif pour le composant Foundation {#integrate-adobe-analytics-with-aem-forms-for-foundation-component}

1. Créez un conteneur de configuration pour les services cloud :
   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
   1. Sélectionnez ou créez un conteneur de configuration et activez le dossier pour les **[!UICONTROL Configurations cloud]**.
   1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.
1. Sur votre instance AEM, accédez à **[Forms]** &quot; **[Forms and Document]**.
1. Sélectionnez votre **[!UICONTROL formulaire]** &quot; **[!UICONTROL Propriétés]**, Dans le **[!UICONTROL conteneur de configuration]**, sélectionnez le conteneur de configuration que vous avez créé ou sélectionné dans le **[!UICONTROL navigateur de configuration]** de l’étape 1.
1. Sélectionnez le panneau Tâche sur le rail de gauche et cliquez sur **Configurer Analytics** et **Activer Adobe Analytics**.
1. Indiquez le nom que vous préférez pour la suite de rapports, cliquez sur **[!UICONTROL Suivant]** et **[!UICONTROL Enregistrer]**.
1. Une fois le projet enregistré, la configuration s’exécute pendant un certain temps jusqu’à l’intégration d’Adobe Analytics à votre formulaire adaptatif. Vous pouvez également vérifier l’ **état d’intégration**.

   >[!NOTE]
   >
   >Si votre configuration dure plus de 15 minutes, réessayez d’activer les analyses pour vos formulaires.

1. Sur votre instance d’AEM, accédez à **[!UICONTROL Forms]** &quot; **[Forms and Document]** et sélectionnez votre **[!UICONTROL formulaire]**. Vous pouvez constater qu’Adobe Analytics est intégré à votre formulaire comme illustré dans l’image ci-dessous.
1. Vous pouvez maintenant afficher votre [rapport Adobe Analytics de formulaire adaptatif](#view-adobe-analytics-report).

![Analytics AEM intégré](assets/analytics-aem-integrated.png){width="100%"}


### Activation d’Adobe Analytics avec Forms adaptatif pour les composants principaux {#integrate-adobe-analytics-with-aem-forms-for-core-components}

1. Sur votre instance d’AEM, accédez à **[!UICONTROL Forms]** &quot; **[!UICONTROL Forms and Document]** et sélectionnez votre **[!UICONTROL formulaire]**.
1. Sélectionnez le panneau Tâche à gauche et cliquez sur **Configurer Analytics** et **Activer Adobe Analytics**.
1. Indiquez le nom que vous préférez pour la suite de rapports, cliquez sur **[!UICONTROL Suivant]** et **[!UICONTROL Enregistrer]**.
1. Une fois le projet enregistré, la configuration s’exécute pendant un certain temps jusqu’à l’intégration d’Adobe Analytics à votre formulaire adaptatif. Vous pouvez également vérifier l’ **état d’intégration**.

   >[!NOTE]
   >
   >Si votre configuration dure plus de 15 minutes, réessayez d’activer les analyses pour vos formulaires.

1. Sur votre instance d’AEM, accédez à **[!UICONTROL Forms]** &quot; **[!UICONTROL Forms and Document]** et sélectionnez votre **[!UICONTROL formulaire]**. Vous pouvez constater qu’Adobe Analytics est intégré à votre formulaire.
1. Vous pouvez maintenant afficher votre [rapport Adobe Analytics de formulaire adaptatif](#view-adobe-analytics-report).

## Afficher le rapport Adobe Analytics d’Forms adaptatif {#view-adobe-analytics-report}

1. Sur votre instance AEM, accédez à **[!UICONTROL Forms]** &quot; **[!UICONTROL Forms and Document]**.
1. Sélectionnez votre formulaire. Vous pouvez constater qu’Adobe Analytics est intégré, comme illustré à gauche, au Forms activé pour Adobe Analytics.

   ![Afficher le rapport](assets/activ-aa.png){width="100%"}

1. Cliquez sur **Adobe Analytics** pour afficher votre rapport et analyser les données de performances.

Pour connecter un formulaire adaptatif à Adobe Analytics à l’aide de la méthode manuelle, consultez la page [Intégrer AEM Forms à Adobe Analytics](/help/forms/integrate-aem-forms-with-adobe-analytics.md).

## Activation d’Analytics vers Forms adaptatif dans Sites {#Connect-Analytics-to-Adaptive-Forms-in-Sites}

La configuration des analyses rapides pour votre formulaire adaptatif dans AEM Sites vous permet de suivre les interactions des utilisateurs et les envois de formulaire sur votre formulaire sur la page Sites. En intégrant facilement les analyses dans votre Forms Sites, vous obtenez des informations précieuses sur le comportement des utilisateurs, les taux de conversion et les domaines à améliorer dans votre formulaire.

### Conditions préalables {#Prerequisites-to-connect-forms-analytics-to-sites}

Pour connecter et activer les analyses dans Adaptive Forms pour AEM Sites, vous devez vous assurer que votre AEM Sites dispose d’une Adobe Analytics active.

### Connexion de Forms adaptatif à Sites pour activer Analytics {#Connect-analytics-to-adaptive-forms}

Pour connecter le formulaire adaptatif dans une page AEM Sites afin d’activer Analytics pour une analyse rapide, incluez la bibliothèque cliente `customfooterlibs` à la page AEM Sites à l’aide du référentiel d’AEM archétype/Git et du pipeline de déploiement.

1. Ouvrez votre projet [Archétype AEM Forms ou référentiel Git cloné](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) dans un éditeur de texte. Par exemple, Visual Studio Code.

1. Accédez à la page de vos sites où se trouve votre formulaire adaptatif, par exemple, Dans ce projet de démonstration, nous avons `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.

1. Copiez la valeur de `sling:resourceSuperType`. Par exemple, la valeur est `core/wcm/components/page/v3/page`.

   ![ressource sling](/help/forms/assets/slingresource.png){width="100%"}

1. Créez la structure similaire à l’emplacement `ui.apps/src/main/content/jcr_root/apps` identique à `core/wcm/components/page/v3/page`.

   ![structure de recouvrement](/help/forms/assets/overlaystructure.png){width="100%"}

1. Ajoutez un fichier `customfooterlibs.html`.

   ```
   // customheaderlibs.html
   <sly data-sly-use.page="com.adobe.cq.wcm.core.components.models.Page">
   <sly data-sly-test="${page.data && page.dataLayerClientlibIncluded}" data-sly-call="${clientlib.js @ categories='core.forms.components.commons.v1.datalayer', async=true}"></sly>
   </sly>
   ```

   `customfooterlibs.html` est utilisé pour JavaScript.

1. [Exécutez le pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=fr) pour déployer les modifications.

### Activation des règles Form Analytics vers Forms dans Sites {#bind-forms-analytics-rules-to-forms-in-sites}

1. Visitez la **collecte de données Adobe Experience Platform**.
1. Cliquez sur **Balises** sur le côté gauche.
1. Recherchez votre projet avec l’ID de programme comme illustré dans l’image ci-dessous, par exemple, pour l’environnement avec l’URL `https://author-p45921-e175111-cmstg.adobeaemcloud.com/index.html`, l’ID de programme est `45921`.

   ![Rechercher votre formulaire-dans-collection-données](/help/forms/assets/aep-data-collection.png){width="100%"}

1. Ajoutez une configuration pour les **règles de formulaire** et les **éléments de données** comme indiqué ci-dessous :

#### Ajouter des règles de formulaire {#form-rules}

1. Sélectionnez votre formulaire et ajoutez **Nouvelle propriété** située dans l’angle supérieur droit ou cliquez sur votre formulaire.
1. Sur la page des propriétés, cliquez sur **Règles** et sélectionnez des événements pour votre formulaire. Dans l’exemple d’image ci-dessous, il s’agit des **événements de formulaire**.

   ![Rechercher votre formulaire-dans-collection-données](/help/forms/assets/aep-form-event-properties.png){width="100%"}

1. Sélectionnez tous les événements de votre formulaire et **copy** situé dans le rail supérieur droit.
1. Une fois que vous avez copié, une fenêtre contextuelle **Copier la règle** s’affiche à l’emplacement où vous recherchez votre page Sites avec l’ID de projet, pour coller les règles de formulaire.

   ![Copier-formulaire-règles](/help/forms/assets/copy-form-rules.png){width="100%"}

1. Cliquez sur **copier** pour coller les règles de formulaire sur la page Sites.

#### Ajout d’éléments de données {#data-elements}

1. Sélectionnez votre formulaire et ajoutez **Nouvelle propriété** située dans l’angle supérieur droit ou cliquez sur votre formulaire.
1. Sur la page des propriétés, cliquez sur **Data Elements** et sélectionnez des événements pour votre formulaire.
1. Sélectionnez tous les événements de votre formulaire et **copy** situé dans le rail supérieur droit.
1. Une fois que vous avez copié, une fenêtre contextuelle **Copier la règle** s’affiche à l’emplacement où vous recherchez votre page Sites avec l’ID de projet, pour coller les règles de formulaire.
1. Cliquez sur **copier** pour coller les règles de formulaire sur la page Sites.

   ![Form-data-elements](/help/forms/assets/form-data-elements.png){width="100%"}

Une fois que vous avez lié les règles de formulaire et de sites par le biais des étapes ci-dessus, effectuez les étapes suivantes pour activer Analytics dans votre formulaire adaptatif sur la page Sites :

1. Cliquez sur **Flux de publication** à gauche.
1. Cliquez sur **Ajouter une bibliothèque** et saisissez le nom que vous préférez.
1. Dans la liste déroulante **Environnement** à droite, sélectionnez **development**.
1. Cliquez sur **Add All Changed Resources** (Ajouter toutes les ressources modifiées).
1. Cliquez sur **Enregistrer et créer dans le développement**.

![publish-to-development](/help/forms/assets/publish-to-dev.png){width="100%"}


<!--

## Best Practices

1.    Verify that Adobe Analytics is enabled on all the forms activated for Adobe Analytics.

1.    Check the Adobe Analytics report periodically to gain insights into user behavior and form performance. For instance, you may set the cadence to 15 days or the period you prefer to choose for report analysis. This enables you to improve the forms enrollment experience.

1.    Enable Analytics for all or most of your forms for tracking and analyzing user interaction with your forms and to gain insights into visitor interactions and engagement.

1. Check your forms performance after you update your form fields or components.

1.    Share Analytics report with your peer groups for review, you can schedule your report for a later time.

-->

## Voir également {#see-also}

* [Affichage et compréhension des rapports d’analyse Forms adaptatif](/help/forms/view-understand-aem-forms-analytics-reports.md)
* [Ajouter un formulaire adaptatif à une page AEM Sites ou un fragment d’expérience](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Intégration d’AEM Forms à Adobe Analytics](/help/forms/integrate-aem-forms-with-adobe-analytics.md)
