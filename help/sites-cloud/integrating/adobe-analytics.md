---
title: 'Intégration à Adobe Analytics '
description: 'Intégration à Adobe Analytics '
translation-type: tm+mt
source-git-commit: ec747361935b94a729cdd5b6712aee6d3ce1b8a2
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 100%

---


# Intégration à Adobe Analytics{#integrating-with-adobe-analytics}

L’intégration d’Adobe Analytics et d’AEM as a Cloud Service vous permet de suivre l’activité de vos pages web :

* Une configuration Adobe Analytics permet à AEM de s’authentifier avec Adobe Analytics.
* Une structure identifie les données envoyées à votre suite de rapports Adobe Analytics.

Les données incluent les données sur les pages et sur l’utilisateur, par exemple :

* Données collectées par les composants AEM
* Clics sur les liens
* Informations sur l’utilisation des vidéos
* Nombre de visites de pages provenant d’Adobe Analytics

Les pages répertoriées ci-dessous peuvent vous aider à configurer l’intégration. Il est à noter qu’Experience Platform Launch constitue de facto l’outil par défaut pour instrumenter un site AEM avec des fonctionnalités Analytics (bibliothèques JS). Par conséquent, l’intégration d’AEM as a Cloud Service avec Launch et Adobe Analytics se fait de pair.

* [Connexion à Adobe Analytics et création de frameworks](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/integration/adobeanalytics-connect.html) : notez que les « frameworks Analytics » sont hérités d’AEM et que leur création ne fonctionne pas dans AEM as a Cloud Service, car elle requiert l’interface utilisateur classique. L’utilisation d’Experience Platform Launch doit être privilégiée, à la fois pour le mappage des variables et pour le déploiement des bibliothèques JS sur les pages.
* [Intégrer Experience Platform Launch](https://docs.adobe.com/content/help/fr-FR/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
* [Intégration d’AEM à Adobe Launch par le biais d’Adobe I/O](https://helpx.adobe.com/fr/experience-manager/using/aem_launch_adobeio_integration.html)
* [Présentation de l’intégration d’AEM à Experience Platform Launch, Analytics et Target](https://helpx.adobe.com/fr/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)
* [Configuration du suivi des liens pour Adobe Analytics](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/integration/adobeanalytics-link.html)
* [Mise en correspondance des données de composant avec les propriétés Adobe Analytics](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/integration/adobeanalytics-mapping.html)
* [Configuration du suivi vidéo pour Adobe Analytics](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/integration/adobeanalytics-video.html)
* [Classifications Adobe](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/integration/adobeanalytics-classifications.html)

>[!CAUTION]
>
>Les clients Adobe Experience Manager as a Cloud Service qui ne disposent pas d’un compte Analytics existant peuvent demander l’accès au package Analytics Foundation pour Experience Cloud.  Ce package Foundation offre une utilisation limitée en volume d’Analytics.

>[!NOTE]
>
>La configuration IMS (comptes techniques) pour Experience Platform Launch est préconfigurée dans AEM as a Cloud Service. Les utilisateurs n’ont pas à créer cette configuration.

## Informations supplémentaires {#further-information}

Voir :

* [Extension de l’intégration à Adobe Analytics](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/developing/extending-aem/extending-analytics/extending-analytics.html) pour plus d’informations sur le développement de composants qui collectent des données utilisateur et la personnalisation de la structure d’Adobe Analytics. Notez que les « frameworks Analytics » sont hérités d’AEM et que leur création ne fonctionne pas dans AEM as a Cloud Service, car ils requièrent l’interface utilisateur Classic. L’utilisation d’Experience Platform Launch doit être privilégiée, à la fois pour le mappage des variables et pour le déploiement des bibliothèques JS sur les pages.
* L’article de la base de connaissances, [Intégration Adobe Analytics : résolution des incidents ](https://helpx.adobe.com/fr/experience-manager/kb/sitecatalystintegrationtroubleshooting.html) pour plus d’informations concernant le dépannage de votre intégration Adobe Analytics.

>[!NOTE]
>
>Si vous utilisez Adobe Analytics avec une configuration de proxy personnalisée, vous devez [configurer deux lots OSGi](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/deploying/configuring/configuring-osgi.html) (par exemple, avec la console web) requis pour les configurations de proxy **Apache HTTP Client**. Les deux lots sont requis, car certaines fonctionnalités d’AEM utilisent les API 3.x, tandis que d’autres utilisent les API 4.x. Configurer :
>
>* **Day Commons HTTP Client 3.1** pour configurer l’API 3.x ;
>  par exemple, [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Apache HTTP Components Proxy Configuration** pour configurer l’API 4.x ;
>  par exemple, [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>


