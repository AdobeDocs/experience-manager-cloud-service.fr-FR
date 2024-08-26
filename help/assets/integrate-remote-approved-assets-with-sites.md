---
title: Intégrer AEM Assets distant à AEM Sites
description: Découvrez comment configurer et connecter AEM sites à l’AEM Assets approuvé.
exl-id: 382e6166-3ad9-4d8f-be5c-55a7694508fa
source-git-commit: e2c0c848c886dc770846d064e45dcc52523ed8e3
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 14%

---

# Intégrer AEM Assets distant à AEM Sites  {#integrate-approved-assets}

La gestion efficace des ressources numériques est essentielle pour offrir des expériences de marque attrayantes et cohérentes sur différentes plateformes en ligne. Dynamic Media avec les fonctionnalités OpenAPI améliore la gestion des ressources numériques en permettant une intégration transparente entre AEM Sites et AEM Assets as a Cloud Service. Cette fonctionnalité innovante vous permet de partager et de gérer facilement différents types de ressources numériques approuvées dans plusieurs environnements d’AEM, ce qui simplifie les workflows pour les auteurs de sites et les éditeurs de contenu.

Les fonctionnalités Dynamic Media avec OpenAPI permettent aux auteurs de sites d’utiliser des ressources de DAM distant directement dans l’éditeur de page d’AEM et le [fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments.html?lang=fr), ce qui simplifie les processus de création et de gestion de contenu.

Les utilisateurs peuvent connecter plusieurs instances AEM Sites, sans restriction sur le nombre maximal, à un déploiement DAM distant, un avantage notable par rapport à la fonction [Assets connecté](use-assets-across-connected-assets-instances.md).

![Image](/help/assets/assets/connected-assets-rdam.png)

Après la configuration initiale, les utilisateurs peuvent créer des pages sur l’instance AEM Sites et ajouter des ressources selon les besoins. Lors de l’ajout de ressources, elles peuvent sélectionner des ressources stockées dans leur gestion des ressources numériques locale ou parcourir et utiliser les ressources disponibles dans la gestion des ressources numériques distantes.

Les fonctionnalités Dynamic Media avec OpenAPI offrent plusieurs autres avantages, tels que l’accès et l’utilisation de ressources distantes dans le fragment de contenu, la récupération des métadonnées des ressources distantes, etc. En savoir plus sur les autres [avantages de Dynamic Media avec les fonctionnalités OpenAPI par rapport à l’Assets connecté](/help/assets/dynamic-media-open-apis-faqs.md).

## Avant de commencer {#pre-requisites-sites-integration}

La prise en charge des ressources distantes à l’aide de Dynamic Media avec les fonctionnalités OpenAPI requiert :

* AEM 6.5 SP 18+ ou AEM as a Cloud Service

* La version 2.23.2 ou ultérieure des composants principaux

* Configurez les [variables d’environnement](/help/implementing/cloud-manager/environment-variables.md#add-variables) suivantes pour AEM as a Cloud Service :

   * ASSET_DELIVERY_REPOSITORY_ID= &quot;delivery-pxxxxx-eyyyy.adobeaemcloud.com&quot; <br>
     `pXXXX` fait référence à l’ID de programme <br>
     `eYYYY` fait référence à l’ID d’environnement

  Ces variables sont définies à l’aide de l’interface utilisateur Cloud Manager de l’environnement AEM as a Cloud Service agissant comme votre instance Sites locale.

   * ASSET_DELIVERY_IMS_CLIENT= [IMSClientId] : vous devez envoyer un ticket de support d’Adobe pour obtenir l’identifiant du client IMS.

     ou configurez les [paramètres OSGi](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi.html) pour AEM 6.5 dans l’instance AEM Sites en procédant comme suit :

   1. Connectez-vous à la console et cliquez sur **[!UICONTROL OSGi] >** ou
utiliser l’URL directe ; par exemple : `https://localhost:4502/system/console/configMgr`

   1. Configurez la configuration OSGi **Configuration Dynamic Media de génération suivante** (`NextGenDynamicMediaConfigImpl`) comme suit, en remplaçant les valeurs par celles de votre environnement de ressources distantes.

      ```text
        imsClient="<ims-client-ID>"
        enabled=B"true"
        imsOrg="<ims-org>@AdobeOrg"
        repositoryId="<repo-id>.adobeaemcloud.com"
      ```

      `imsOrg` n’est pas une entrée obligatoire.
      `repositoryId` = &quot;delivery-pxxxxx-eyyyyy.adobeaemcloud.com&quot;
où `pXXXX` fait référence à l’ID de programme
      `eYYYY` fait référence à l’ID d’environnement

      ![Fenêtre de configuration OSGi de la configuration Dynamic Media de nouvelle génération](/help/assets/assets/remote-assets-osgi.png)

  En savoir plus sur [l&#39;authentification IMS](https://experienceleague.adobe.com/docs/experience-manager-65/content/security/ims-config-and-admin-console.html).

  Pour plus d’informations sur la configuration d’OSGi, consultez les documents suivants :

   * [Configuration d’OSGi pour Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html) pour AEM as a Cloud Service
   * [Configuration d’OSGi](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-osgi.html?lang=fr) pour AEM 6.5

* Accès IMS pour se connecter à une instance DAM distante AEM as a Cloud Service. Il fait référence à l’auteur Sites disposant d’un accès IMS à l’environnement DAM distant.

* Configurez le composant Image v3 dans l’instance AEM Sites. Si le composant n’est pas présent, téléchargez et installez le [module de contenu](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.23.0).

## Configurer le HTTPS {#https}

Il est généralement recommandé d’exécuter toutes vos instances AEM de production avec HTTPS. Toutefois, vos environnements de développement locaux ne sont peut-être pas configurés avec ce protocole. Cependant, les ressources distantes utilisant Dynamic Media avec OpenAPI nécessitent HTTPS pour fonctionner.

[Suivez ce guide](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html?lang=fr) pour configurer HTTPS partout où vous souhaitez utiliser des ressources distantes, y compris les environnements de développement.

## Accès aux ressources à partir de DAM distant {#fetch-assets}

Dynamic Media avec les fonctionnalités OpenAPI vous permet d’accéder aux ressources disponibles dans votre instance DAM distante sur votre éditeur de page AEM Sites local et le fragment de contenu AEM.

![Image](/help/assets/assets/open-APIs.png)

### Accès aux ressources distantes dans AEM éditeur de page {#access-assets-page-editor}

Suivez les étapes ci-dessous pour utiliser des ressources distantes dans AEM éditeur de page sur votre instance AEM Sites. Vous pouvez effectuer cette intégration dans AEM as a Cloud Service et AEM 6.5.

1. Accédez à **[!UICONTROL Sites]** > _votre site web_ où se trouve l’AEM **[!UICONTROL Page]** dans laquelle vous devez ajouter la ressource distante.
1. Sélectionnez la page et cliquez sur **[!UICONTROL Modifier (_e_)]**. L’AEM **[!UICONTROL Éditeur de page]** s’ouvre.
1. Cliquez sur le conteneur de mises en page et ajoutez un composant **[!UICONTROL Image]** .
1. Cliquez sur le composant **[!UICONTROL Image]** et cliquez sur l&#39;icône ![settings](/help/assets/assets/do-not-localize/settings-icon.svg) .
1. Décochez l&#39;option **[!UICONTROL Hériter de l&#39;image en vedette de la page]** .
1. Cliquez sur **[!UICONTROL Pick]** et sélectionnez **[!UICONTROL Remote]**.
   ![Image](/help/assets/assets/uncheck-inherit-option.jpg)

   Vous êtes invité à vous connecter.
1. Sélectionnez la ressource et cliquez sur **[!UICONTROL Sélectionner]**.
1. Ajoutez un texte de remplacement et cliquez sur **[!UICONTROL Terminé]**.
   <br> La ressource distante apparaît dans le composant d’image. Vous pouvez également vérifier l’URL de diffusion de la ressource lors de son chargement sur la page ou à l’aide de l’onglet &quot;Aperçu&quot;. L’URL de diffusion indique que la ressource est accessible à distance.

Vous pouvez accéder aux ressources distantes dans AEM éditeur de page prêt à l’emploi uniquement pour le composant principal Image v3 et le composant principal Teaser v2. Pour d’autres composants, y compris les composants personnalisés, des personnalisations sont nécessaires pour intégrer le sélecteur de ressources à ces composants.

#### Vidéo : Accès aux ressources distantes dans AEM Éditeur de page

>[!VIDEO](https://video.tv.adobe.com/v/3427666)

### Accès aux ressources distantes dans AEM fragment de contenu {#access-assets-content-fragment}

Suivez les étapes ci-dessous pour utiliser des ressources distantes dans AEM fragment de contenu sur votre instance AEM Sites. Vous pouvez effectuer cette intégration dans AEM 6.5 et non dans AEM as a Cloud Service.

1. Accédez à **[!UICONTROL Assets]** > **[!UICONTROL Fichiers]**.
1. Sélectionnez le dossier de ressources où se trouve le fragment de contenu.
1. Sélectionnez le fragment de contenu et cliquez sur **[!UICONTROL Modifier (_e_)]**.

   >[!NOTE]
   >
   >Si vous n’avez pas AEM modèle de fragment de contenu, vous devrez peut-être [en créer un](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments-models.html?lang=en).

1. Cliquez sur l’icône ![coche](/help/assets/assets/do-not-localize/checkmark-icon.svg) en regard du composant de texte.
1. Sélectionnez **[!UICONTROL Remote]** pour récupérer la ressource à partir du DAM distant. <br>
Vous pouvez choisir le référentiel DAM **[!UICONTROL Local]** ou **[!UICONTROL Remote]** selon vos besoins.

   ![image](/help/assets/assets/cf-pick.jpg)
Vous êtes invité à vous connecter.
1. Sélectionnez la ressource et cliquez sur **[!UICONTROL Sélectionner]**.
   <br> L’URL de ressource distante apparaît dans le composant de texte.

#### Vidéo : Accès aux ressources distantes dans AEM fragment de contenu

>[!VIDEO](https://video.tv.adobe.com/v/3427667)

### Accès aux ressources distantes en Edge Delivery Services {#access-assets-eds}

Vous pouvez également accéder aux ressources distantes en Edge Delivery Services. Pour plus d’informations, voir [Utilisation des ressources d’Assets as a Cloud Service fournies à l’aide de Dynamic Media avec des fonctionnalités OpenAPI](https://www.aem.live/docs/aem-assets-sidekick-plugin#utilizing-assets-from-assets-cloud-services-delivered-via-dynamic-media-with-openapi).
