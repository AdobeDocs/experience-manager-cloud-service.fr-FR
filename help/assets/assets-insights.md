---
title: Assets Insights
description: Effectuez le suivi des évaluations des utilisateurs et des statistiques d’utilisation des images utilisées dans les sites web tiers, les campagnes marketing et les solutions de création d’Adobe.
contentOwner: AG
feature: Statistiques sur les ressources, rapports sur les ressources
role: User,Leader
exl-id: e268453b-e7c0-4aa4-bd29-2686edb5f99a
source-git-commit: def144cecaa7672e7af1807a5157730014c550b2
workflow-type: ht
source-wordcount: '813'
ht-degree: 100%

---

# Assets Insights {#asset-insights}

La fonctionnalité Statistiques sur les ressources effectue le suivi des évaluations des utilisateurs et des statistiques d’utilisation des images utilisées dans les sites web tiers, les campagnes marketing et les solutions de création d’Adobe. Elle permet d’obtenir des informations sur les performances et la popularité des images.

La fonction Statistiques sur les ressources capture les détails de l’activité des utilisateurs, comme le nombre de fois où une image est évaluée et a fait l’objet d’un clic, ainsi que le nombre d’impressions (nombre de fois où une image est chargée sur le site web). Elle attribue des scores aux images en fonction de ces statistiques. Vous pouvez utiliser les scores et les statistiques de performances pour sélectionner les images populaires à inclure dans les catalogues, les campagnes marketing et ainsi de suite. Vous pouvez même formuler des stratégies de renouvellement de licence et d’archivage en fonction de ces statistiques.

Pour que la fonction Statistiques sur les ressources capture les statistiques d’utilisation des images à partir d’un site web, vous devez inclure le code intégré de l’image dans celui du site web.

Pour afficher les statistiques d’utilisation des ressources, commencez par configurer la fonction afin qu’elle récupère les données de rapports d’[!DNL Adobe Analytics]. Pour plus d’informations, consultez la section [Configuration des statistiques sur les ressources](#configure-asset-insights). Pour utiliser cette fonctionnalité, achetez la licence [!DNL Adobe Analytics] séparément.

>[!NOTE]
>
>Les statistiques sont uniquement prises en charge et fournies pour les images.

## Affichage des statistiques pour une image {#viewing-statistics-for-an-image}

Vous pouvez afficher les scores de statistiques sur les ressources à partir de la page des métadonnées.

1. Dans l’interface utilisateur d’Assets, sélectionnez l’image, puis appuyez sur **[!UICONTROL Propriétés]** dans la barre d’outils.
1. Sur la page Propriétés, appuyez sur **[!UICONTROL Statistiques]**.
1. Consultez les détails d’utilisation de la ressource dans l’onglet **[!UICONTROL Statistiques]**. La section **[!UICONTROL Score]** indique les scores totaux d’utilisation et de performances d’une ressource.

   Le score d’utilisation indique le nombre de fois que la ressource est utilisée dans diverses solutions.

   Le score **[!UICONTROL Impressions]** correspond au nombre de fois que la ressource est chargée sur le site web. Le nombre affiché sous **[!UICONTROL Clics]** représente le nombre de fois que la ressource est cliquée.

1. Passez en revue la section **[!UICONTROL Statistiques d’utilisation]** pour savoir de quelles entités la ressource faisait partie et dans quelles solutions de création elle a récemment été utilisée. Plus l’utilisation est élevée, plus la ressource a de chances d’être populaire auprès des utilisateurs. Les données d’utilisation s’affichent sous les sections suivantes :

   * **[!UICONTROL Ressource]** : nombre de fois où la ressource faisait partie d’une collection ou d’une ressource composite.
   * **[!UICONTROL Web et mobile]** : nombre de fois où la ressource faisait partie de sites web et d’applications.
   * **[!UICONTROL Social]** : nombre de fois où la ressource a été utilisée dans d’autres solutions, telles qu’[!DNL Adobe Campaign].
   * **[!UICONTROL Email]** : nombre de fois où la ressource a été utilisée dans des campagnes par email.

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Parce que la fonction Statistiques sur les ressources récupère les données de solutions d’[!DNL Adobe Analytics] de manière périodique, la section Solutions peut ne pas afficher les données les plus récentes. La période pendant laquelle les données sont affichées dépend de la planification de l’opération de récupération que la fonction Statistiques sur les ressources exécute pour récupérer les données d’Analytics.

1. Pour afficher les statistiques de performances de l’actif sous forme graphique sur une période donnée, sélectionnez une période dans la section **[!UICONTROL Statistiques de performances]**. Les détails, y compris les clics et les impressions, sont affichés sous forme de lignes de tendance dans un graphique.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >Contrairement à la section Solutions, la section Statistiques de performances affiche les données les plus récentes.

1. Pour obtenir le code intégré de la ressource que vous incluez sur les sites web afin d’obtenir les données de performances, cliquez sur **[!UICONTROL Obtenir le code intégré]** au-dessous de la vignette de la ressource. <!-- For more information on how to include your Embed code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

   ![chlimage_1-98](assets/chlimage_1-98.png)

## Affichage des statistiques générales pour les images {#viewing-aggregate-statistics-for-images}

Vous pouvez afficher les scores de toutes les ressources d’un dossier simultanément à l’aide du **[!UICONTROL mode Statistiques]**.

1. Dans l’interface utilisateur d’Assets, accédez au dossier contenant les ressources dont vous souhaitez consulter les statistiques.
1. Cliquez sur l’option **[!UICONTROL Mise en page]** de la barre d’outils, puis sélectionnez **[!UICONTROL Mode Statistiques]**.
1. La page affiche les scores d’utilisation pour les ressources. Comparez les évaluations des différentes ressources et tirez-en des conclusions.

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.

## Schedule background job {#scheduling-background-job}

Assets Insights fetches usage data for assets from Adobe Analytics report suites in a periodic manner. By default, Assets Insights runs a background job every 24 hours at 2 AM to the fetch data. However, you can modify both the frequency and the time by configuring the **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** service from the web console.

1. Click the [!DNL Experience Manager] logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open the **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** service configuration.

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Specify the desired scheduler frequency and the start time for the job in the property scheduler expression. Save the changes.
-->

## Configuration des statistiques sur les ressources {#configure-asset-insights}

[!DNL Experience Manager Assets] récupère les données d’utilisation des ressources numériques utilisées par des sites web tiers à partir de [!DNL Adobe Analytics]. Pour permettre à la fonction Statistiques sur les ressources de récupérer ces données et de générer des informations, commencez par la configurer afin qu’elle s’intègre à [!DNL Adobe Analytics].

>[!NOTE]
>
>Les statistiques sont uniquement prises en charge et fournies pour les images.

1. Dans [!DNL Experience Manager], cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Ressources]**.

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. Cliquez sur la carte **[!UICONTROL Configuration des statistiques]**.
1. Dans l’assistant, sélectionnez un centre de données et fournissez vos informations d’identification, notamment le nom de votre société, votre nom d’utilisateur et votre secret partagé.

   ![Configuration d’Adobe Analytics pour les statistiques sur les ressources dans [!DNL Experience Manager]](assets/insights_config2.png)

   *Figure : Configuration d’Adobe Analytics pour les statistiques sur les ressources dans[!DNL Experience Manager]*

1. Cliquez sur **[!UICONTROL Authentifier]**. Une fois que [!DNL Experience Manager] a authentifié vos identifiants, dans la liste **[!UICONTROL Suite de rapports]**, sélectionnez une suite de rapports Adobe Analytics à partir de laquelle la fonction Statistiques sur les ressources doit récupérer les données. Cliquez sur **[!UICONTROL Ajouter]**.
1. Une fois qu’[!DNL Experience Manager] a configuré votre suite de rapports, appuyez sur **[!UICONTROL Terminé]**.

### Suivi de page {#page-tracker}

Une fois que vous avez configuré votre compte Adobe Analytics, le code de suivi de page est généré pour vous. Pour permettre à la fonction Statistiques sur les ressources de surveiller les ressources [!DNL Experience Manager] utilisées sur les sites web tiers, incluez le code de suivi de page dans le code du site web. Utilisez l’utilitaire de suivi de page dans Assets pour générer le code de suivi de page. <!--  For more information on how to include your Page Tracker code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

1. Dans [!DNL Experience Manager], cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Ressources]**.

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. Sur la page **[!UICONTROL Navigation]**, cliquez sur la carte **[!UICONTROL Dispositif de suivi de la page de statistiques]**.
1. Cliquez sur **[!UICONTROL Télécharger]** pour télécharger le code de suivi de page.

<!--
Add page tracker code, CQDOC-18045, 30/07/2021
-->
Le fragment d’exemple code suivant présente le code de suivi de page inclus dans un exemple de page web :

```xml
 <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/foundation/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in millis
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","abc.net","bee","list1","eVar3","event8","event7");
            </script>

 </head>
```



<!--

## Using demo package for Assets Insights {#using-demo-package-for-asset-insights}

Using the demo package, you can enable Adobe Assets Insights to capture data from and generate insights for a sample web page.

1. Configure Assets Insights using the instructions in [Configure Assets Insights](#configure-asset-insights).
1. Download the sample [!DNL Experience Manager Assets] package from below and install the package from CRXDE package manager.

   [Get File](assets/insightsdemo.zip)

1. Download the ZIP file containing the sample web page from below and extract on your local file system.

   [Get File](assets/demosite.zip)

1. Click the web page to open it in the web browser.

   >[!CAUTION]
   >
   >Web Page is configured to load asset from the localhost server . In case your server is running somewhere else change server address from localhost to server address in the HTML content of the web page.

   >[!NOTE]
   >
   >The external web page can be in [!DNL Experience Manager] itself.

-->
