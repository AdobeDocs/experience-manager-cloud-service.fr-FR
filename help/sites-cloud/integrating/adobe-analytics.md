---
title: Intégration à Adobe Analytics
description: 'Intégration à Adobe Analytics '
translation-type: tm+mt
source-git-commit: 6754693da488b0bc44a71aa9f0402fc1308b703a

---


# Intégration à Adobe Analytics{#integrating-with-adobe-analytics}

L’intégration d’Adobe Analytics et d’AEM en tant que service Cloud vous permet d’effectuer le suivi de l’activité de votre page Web :

* Une configuration Adobe Analytics permet à AEM de s’authentifier avec Adobe Analytics.
* Une structure identifie les données envoyées à votre suite de rapports Adobe Analytics.

Les données comprennent les données de page et d’utilisateur, par exemple :

* Données collectées par les composants AEM
* Clics sur les liens
* Informations sur l’utilisation des vidéos
* Nombre de visites de pages provenant d’Adobe Analytics

Les pages répertoriées ci-dessous peuvent vous aider à configurer l’intégration. Notez que le lancement par Adobe est l’outil par défaut permettant d’instrumenter un site AEM avec des fonctionnalités Analytics (bibliothèques JS). Par conséquent, l’intégration d’AEM en tant que service Cloud avec Launch et Adobe Analytics se fait de pair.

* [Connexion à Adobe Analytics et création de cadres](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-connect.html) : notez que les &quot;cadres d’Analytics&quot; sont hérités d’AEM et que leur création ne fonctionne pas dans AEM en tant que service Cloud car elle requiert l’interface utilisateur classique. Le lancement par Adobe doit être utilisé à la place, à la fois pour le mappage des variables et pour le déploiement des bibliothèques JS sur les pages.
* [Intégrer le lancement par Adobe](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
* [Intégration d’AEM à Adobe Launch par le biais des E/S Adobe](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
* [Présentation de l’intégration d’AEM au lancement par Adobe, Analytics et Target](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)
* [Configuration du suivi des liens pour Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-link.html)
* [Mise en correspondance des données de composant avec les propriétés Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-mapping.html)
* [Configuration du suivi vidéo pour Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-video.html)
* [Classifications Adobe](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-classifications.html)

>[!CAUTION]
>
>Les clients Adobe Experience Manager en tant que clients du service Cloud qui ne disposent pas d’un compte Analytics existant peuvent demander l’accès à Analytics Foundation Pack pour Experience Cloud.  Ce module Foundation Pack offre une utilisation limitée en volume d’Analytics.

>[!NOTE]
>
>La configuration IMS (comptes techniques) pour le lancement par Adobe est préconfigurée dans AEM en tant que service Cloud. Les utilisateurs n’ont pas à créer cette configuration.

## Informations supplémentaires {#further-information}

Voir :

* [Extension de l’intégration](https://docs.adobe.com/content/help/en/experience-manager-65/developing/extending-aem/extending-analytics/extending-analytics.html) Adobe Analytics pour en savoir plus sur le développement de composants qui collectent des données utilisateur et personnalisent la structure Adobe Analytics. Notez que les &quot;structures Analytics&quot; sont héritées d’AEM et que leur création ne fonctionne pas dans AEM en tant que service Cloud car elle requiert l’interface utilisateur classique. Le lancement par Adobe doit être utilisé à la place, à la fois pour le mappage des variables et pour le déploiement des bibliothèques JS sur les pages.
* The knowledge base article, [Adobe Analytics integration - troubleshooting issues](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), for information about troubleshooting your Adobe Analytics integration.

>[!NOTE]
>
>Si vous utilisez Adobe Analytics avec une configuration de proxy personnalisée, vous devez [configurer deux lots OSGi](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/configuring-osgi.html) (par exemple, à l’aide de la console web) pour les configurations de proxy **Apache HTTP Client**. Ces deux lots sont nécessaires lorsque certaines fonctions d’AEM utilisent les API 3.x, tandis que d’autres utilisent les API 4.x. Configurez :
>
>* **Day Commons HTTP Client 3.1** pour configurer l&#39;API 3.x ;
   >  par exemple, [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **Configuration** du proxy des composants HTTP Apache pour configurer l&#39;API 4.x ;
   >  par exemple, [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>


