---
title: Intégrer AEM Assets distant à AEM Sites
description: Découvrez comment configurer et connecter des sites AEM à des AEM Assets approuvées.
exl-id: 382e6166-3ad9-4d8f-be5c-55a7694508fa
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 17%

---

# Intégrer AEM Assets distant à AEM Sites  {#integrate-approved-assets}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Le guide de Dynamic Media avec fonctionnalités OpenAPI est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Dynamic Media avec fonctionnalités OpenAPI]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Une gestion efficace des ressources numériques est essentielle pour offrir des expériences de marque attrayantes et cohérentes sur différentes plateformes en ligne. Dynamic Media avec les fonctionnalités OpenAPI améliore la gestion des ressources numériques en permettant une intégration transparente entre AEM Sites et AEM Assets as a Cloud Service. Cette fonctionnalité innovante vous permet de partager et de gérer facilement différents types de ressources numériques approuvées dans plusieurs environnements AEM, ce qui simplifie les workflows pour les auteurs de sites et les éditeurs de contenu.

Dynamic Media avec les fonctionnalités OpenAPI permet aux auteurs de sites d’utiliser des ressources de gestion des ressources numériques à distance directement dans l’éditeur de page d’AEM et [fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments.html?lang=fr), ce qui simplifie la création et la gestion de contenu.

Les utilisateurs peuvent connecter plusieurs instances AEM Sites, sans restriction sur le nombre maximal, à un déploiement DAM distant, ce qui constitue un avantage notable par rapport à la fonctionnalité [Connected Assets](use-assets-across-connected-assets-instances.md).

![Image](/help/assets/assets/connected-assets-rdam.png)

Après la configuration initiale, les utilisateurs peuvent créer des pages sur l’instance AEM Sites et ajouter des ressources si nécessaire. Lors de l’ajout de ressources, ils peuvent sélectionner des ressources stockées dans leur gestion des ressources numériques (DAM) locale ou parcourir et utiliser les ressources disponibles dans la gestion des ressources numériques (DAM) distante.

Dynamic Media avec les fonctionnalités OpenAPI offre plusieurs autres avantages, tels que l’accès et l’utilisation de ressources distantes dans le fragment de contenu, la récupération des métadonnées des ressources distantes, etc. Découvrez les autres [avantages de Dynamic Media avec les fonctionnalités OpenAPI par rapport à Connected Assets](/help/assets/dynamic-media-open-apis-faqs.md).

## Avant de commencer {#pre-requisites-sites-integration}

La prise en charge des ressources distantes à l’aide de Dynamic Media avec les fonctionnalités OpenAPI nécessite :

* AEM 6.5 SP 18+ ou AEM as a Cloud Service

* La version 2.23.2 ou ultérieure des composants principaux

* Configurez les [variables d’environnement](/help/implementing/cloud-manager/environment-variables.md#add-variables) suivantes pour AEM as a Cloud Service :

   * ASSET_DELIVERY_REPOSITORY_ID= « delivery-pxxxxx-eyyyyyy.adobeaemcloud.com » <br>
     `pXXXX` fait référence à l’ID de programme <br>
     `eYYYY` fait référence à l’identifiant d’environnement

  Ces variables sont définies à l’aide de l’interface utilisateur Cloud Manager de l’environnement AEM as a Cloud Service qui agit comme votre instance Sites locale.

   * ASSET_DELIVERY_IMS_CLIENT= [IMSClientId] : vous devez envoyer un ticket d’assistance Adobe pour obtenir l’identifiant du client IMS.

     ou configurez les paramètres [OSGi](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi.html) pour AEM 6.5 dans l’instance AEM Sites en procédant comme suit :

   1. Connectez-vous à la console et cliquez sur **[!UICONTROL OSGi] >** ou
Utilisez l’URL directe, par exemple : `https://localhost:4502/system/console/configMgr`.

   1. Configurez la configuration OSGi **Configuration Dynamic Media de nouvelle génération** (`NextGenDynamicMediaConfigImpl`) comme suit, en remplaçant les valeurs par celles de votre environnement de ressources distant.

      ```text
        imsClient="<ims-client-ID>"
        enabled=B"true"
        imsOrg="<ims-org>@AdobeOrg"
        repositoryId="<repo-id>.adobeaemcloud.com"
      ```

      `imsOrg` n’est pas une entrée obligatoire.
      `repositoryId` = « delivery-pxxxxx-eyyyyy.adobeaemcloud.com »
où `pXXXX` fait référence à l’ID de programme
      `eYYYY` fait référence à l’identifiant d’environnement

      ![Fenêtre de configuration OSGi de la configuration Dynamic Media de nouvelle génération](/help/assets/assets/remote-assets-osgi.png)

  En savoir plus sur l’authentification [IMS](https://experienceleague.adobe.com/docs/experience-manager-65/content/security/ims-config-and-admin-console.html).

  Pour plus d’informations sur la configuration d’OSGi, consultez les documents suivants :

   * [Configuration d’OSGi pour Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html) pour AEM as a Cloud Service
   * [Configuration d’OSGi](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-osgi.html?lang=fr) pour AEM 6.5

* Accès IMS pour vous connecter à une instance AEM as a Cloud Service de gestion des ressources numériques distante. Il fait référence à l’auteur Sites qui dispose d’un accès IMS à l’environnement DAM distant.

* Configurez le composant Image v3 dans l’instance AEM Sites. Si le composant n’est pas présent, téléchargez et installez le [package de contenu](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.23.0).

## Configurer le HTTPS {#https}

Il est généralement recommandé d’exécuter toutes vos instances AEM de production avec HTTPS. Toutefois, vos environnements de développement locaux ne sont peut-être pas configurés avec ce protocole. Cependant, les ressources distantes utilisant Dynamic Media avec OpenAPI nécessitent HTTPS pour fonctionner.

[Suivez ce guide](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html?lang=fr) pour configurer HTTPS partout où vous souhaitez utiliser des ressources distantes, y compris les environnements de développement.

## Accès aux ressources à partir de la gestion des ressources numériques à distance {#fetch-assets}

Dynamic Media avec les fonctionnalités OpenAPI vous permet d’accéder aux ressources disponibles dans votre instance DAM distante sur votre éditeur de page AEM Sites local et votre fragment de contenu AEM.

![Image](/help/assets/assets/open-APIs.png)

### Accès aux ressources distantes dans l’éditeur de page AEM {#access-assets-page-editor}

Suivez les étapes ci-dessous pour utiliser des ressources distantes dans l’éditeur de page d’AEM sur votre instance AEM Sites. Vous pouvez effectuer cette intégration dans AEM as a Cloud Service et AEM 6.5.

1. Accédez à **[!UICONTROL Sites]** > _votre site web_ où se trouve la page AEM **[!UICONTROL Page]** dans laquelle vous devez ajouter la ressource distante.
1. Sélectionnez la page et cliquez sur **[!UICONTROL Modifier (_par ex_)]**. AEM **[!UICONTROL Éditeur de page]** s’ouvre.
1. Cliquez sur le conteneur de disposition et ajoutez un composant **[!UICONTROL Image]**.
1. Cliquez sur le composant **[!UICONTROL Image]**, puis sur l’icône ![paramètres](/help/assets/assets/do-not-localize/settings-icon.svg).
1. Désélectionnez l’option **[!UICONTROL Hériter l’image en vedette de la page]**.
1. Cliquez sur **[!UICONTROL Choisir]** et sélectionnez **[!UICONTROL À distance]**.
   ![Image](/help/assets/assets/uncheck-inherit-option.jpg)

   Vous êtes invité à vous connecter.
1. Sélectionnez la ressource et cliquez sur **[!UICONTROL Sélectionner]**.
1. Ajoutez un Texte secondaire et cliquez sur **[!UICONTROL Terminé]**.
   <br> La ressource distante s’affiche dans le composant d’image. Vous pouvez également vérifier l’URL de diffusion de la ressource lors de son chargement sur la page ou à l’aide de l’onglet « Prévisualisation ». L’URL de diffusion indique que la ressource est accessible à distance.

Vous pouvez accéder aux ressources distantes dans l’éditeur de page d’AEM prêt à l’emploi uniquement pour les composants principaux Image v3 et Teaser v2. Pour d’autres composants, y compris les composants personnalisés, des personnalisations sont requises pour intégrer le sélecteur de ressources à ces composants.

#### Vidéo : accès aux ressources distantes dans l’éditeur de page d’AEM

>[!VIDEO](https://video.tv.adobe.com/v/3427666)

### Accès aux ressources distantes dans le fragment de contenu AEM {#access-assets-content-fragment}

Suivez les étapes ci-dessous pour utiliser des ressources distantes dans un fragment de contenu AEM sur votre instance AEM Sites. Vous pouvez effectuer cette intégration dans AEM 6.5 et non dans AEM as a Cloud Service.

1. Accédez à **[!UICONTROL Assets]** > **[!UICONTROL Fichiers]**.
1. Sélectionnez le dossier de ressources où se trouve le fragment de contenu.
1. Sélectionnez le fragment de contenu et cliquez sur **[!UICONTROL Modifier (_par ex_)]**.

   >[!NOTE]
   >
   Si vous ne disposez pas d’un modèle de fragment de contenu AEM, vous devrez peut-être en [créer un](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments-models.html?lang=en).

1. Cliquez sur l’icône ![icône en forme de coche](/help/assets/assets/do-not-localize/checkmark-icon.svg) en regard du composant de texte.
1. Sélectionnez **[!UICONTROL Distant]** pour récupérer la ressource à partir du DAM distant. <br>
Vous pouvez choisir le référentiel de gestion des ressources numériques **[!UICONTROL local]** ou **[!UICONTROL distant]** en fonction de vos besoins.

   ![image](/help/assets/assets/cf-pick.jpg)
Vous êtes invité à vous connecter.
1. Sélectionnez la ressource et cliquez sur **[!UICONTROL Sélectionner]**.
   <br> L’URL de la ressource distante s’affiche dans le composant de texte.

#### Vidéo : accès aux ressources distantes dans le fragment de contenu AEM

>[!VIDEO](https://video.tv.adobe.com/v/3427667)

### Accès aux ressources distantes en Edge Delivery Services {#access-assets-eds}

Vous pouvez également accéder aux ressources distantes en Edge Delivery Services. Pour plus d’informations, voir [ Utilisation des ressources d’Assets as a Cloud Service diffusées à l’aide de Dynamic Media avec les fonctionnalités OpenAPI ](https://www.aem.live/docs/aem-assets-sidekick-plugin#utilizing-assets-from-assets-cloud-services-delivered-via-dynamic-media-with-openapi).
