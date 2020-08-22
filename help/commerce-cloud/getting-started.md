---
title: Prise en main de AEM Commerce en tant que Cloud Service
description: Prise en main de AEM Commerce en tant que Cloud Service
translation-type: tm+mt
source-git-commit: 5a90db8791dd92cceb811b9ed2beda3ecb4a974d
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 5%

---


# Prise en main de AEM Commerce en tant que Cloud Service {#start}

Pour commencer à utiliser AEM Commerce en tant que Cloud Service, votre Experience Manager Cloud Service doit être configuré avec le module complémentaire CIF (Commerce Integration Framework). Le module complémentaire CIF est un module supplémentaire ajouté à [AEM Sites en tant que Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/home.html).

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

## Intégration {#onboarding}

L&#39;intégration de AEM Commerce en tant que Cloud Service est un processus en deux étapes :

1. Activation de l&#39;AEM Commerce en tant que Cloud Service et mise en service du module complémentaire CIF
2. Connectez AEM Commerce en tant que Cloud Service à votre environnement Magento

La première étape est faite par l&#39;Adobe. Vous devrez fournir des informations telles que l’organisation IMS, l’URL du point de terminaison GraphQL de votre environnement Magento, etc. dans le cadre du processus de mise en service. Pour plus d&#39;informations sur la tarification et la mise en service, contactez votre représentant commercial.

Une fois que vous avez reçu les privilèges d’accès avec le module complémentaire CIF, il sera appliqué à tout programme Cloud Manager existant. Si vous n’avez pas de Programme Cloud Manager, vous devrez en créer un nouveau. Pour plus d&#39;informations, consultez [Configuration de votre Programme](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

La deuxième étape est le libre-service pour chaque AEM en tant qu&#39;environnement Cloud Service. Il existe d’autres configurations que vous devrez effectuer après l’approvisionnement initial du module complémentaire CIF.

## Connexion du commerce AEM avec le Magento {#magento}

Pour connecter le module complémentaire CIF et les composants [principaux CIF](https://github.com/adobe/aem-core-cif-components) AEM avec votre environnement Magento, vous devez fournir l’URL du point de terminaison GraphQL Magento via une variable d’environnement Cloud Manager. Le nom de la variable est `COMMERCE_ENDPOINT`. Une connexion sécurisée via HTTPS doit être configurée.
Une autre URL de point de terminaison GraphQL Magento peut être utilisée pour chaque AEM en tant qu’environnement Cloud Service. De cette façon, les projets peuvent relier les environnements d&#39;évaluation AEM aux systèmes d&#39;évaluation Magento et à l&#39;environnement de production AEM à un système de production Magento. Ce point de terminaison GraphQL Magento doit être accessible au public, les connexions VPN privées ou locales ne sont pas prises en charge.

Pour connecter AEM Commerce à un Magento, procédez comme suit :

1. Obtenez l&#39;interface de ligne de commande des E/S Adobe avec le module Cloud Manager

   Consultez la documentation [de](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) Adobe Cloud Manager sur la façon de télécharger, de configurer et d’utiliser l’interface de ligne de commande des E/S [Adobes avec le module](https://github.com/adobe/aio-cli) d’interface de ligne de commande [Cloud Manager](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. Authentification de l’interface de ligne de commande avec l’AEM en tant que programme Cloud Service

3. Définition de la `COMMERCE_ENDPOINT` variable dans Cloud Manager

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Pour plus d’informations, reportez-vous à la documentation [](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) CLI.

   L’URL du point de terminaison GraphQL du Magento doit pointer vers le service GraphQl du Magento et utiliser une connexion HTTPS sécurisée. Par exemple : `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>Vous pouvez liste toutes les variables de Cloud Manager à l’aide de la commande suivante pour vérifier le doublon : `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

>[!NOTE]
>
>Vous pouvez également utiliser l’API [de](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) Cloud Manager pour configurer les variables de Cloud Manager.

Vous pouvez ainsi utiliser AEM Commerce en tant que Cloud Service et déployer votre projet via Cloud Manager.

## 3rd party commerce integrations {#integrations}

Pour les intégrations de commerce tierces, une couche [de mappage](architecture/third-party.md) API est nécessaire pour connecter AEM Commerce en tant que Cloud Service et les composants principaux CIF à votre système de commerce. Cette couche de mappage d’API est généralement déployée sur Adobe I/O Runtime. Contactez votre représentant commercial pour connaître les intégrations disponibles et l’accès à Adobe I/O Runtime.
