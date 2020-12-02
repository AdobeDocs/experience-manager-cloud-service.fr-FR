---
title: Prise en main de AEM Commerce en tant que Cloud Service
description: Découvrez comment déployer un projet AEM compatible avec le commerce sur un AEM en cours d’exécution en tant qu’environnement de service Cloud. Utilisez les fonctionnalités d’Adobe Cloud Manager et un pipeline CI/CD pour construire la vitrine de référence Venia sur un environnement en cours d’exécution.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
translation-type: tm+mt
source-git-commit: b3abefb2953080443e220a248dd4484d23c09a0e
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 7%

---


# Prise en main de AEM Commerce en tant que Cloud Service {#start}

Pour commencer à utiliser AEM Commerce en tant que Cloud Service, votre Experience Manager Cloud Service doit être configuré avec le module complémentaire CIF (Commerce Integration Framework). Le module complémentaire CIF est un module supplémentaire ajouté à [AEM Sites en tant que Cloud Service](https://docs.adobe.com/content/help/fr/experience-manager-cloud-service/sites/home.html).

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

## Intégration {#onboarding}

L&#39;intégration de AEM Commerce en tant que Cloud Service est un processus en deux étapes :

1. Activation de l&#39;AEM Commerce en tant que Cloud Service et mise en service du module complémentaire CIF
2. Connectez AEM Commerce en tant que Cloud Service à votre environnement Magento

La première étape est faite par l&#39;Adobe. Vous devrez fournir des informations telles que l’organisation IMS, l’URL du point de terminaison GraphQL de votre environnement Magento, etc. dans le cadre du processus de mise en service. Pour plus d&#39;informations sur la tarification et la mise en service, contactez votre représentant commercial.

Une fois que vous avez reçu les privilèges d’accès avec le module complémentaire CIF, il sera appliqué à tout programme Cloud Manager existant. Si vous n’avez pas de Programme Cloud Manager, vous devrez en créer un nouveau. Pour plus d&#39;informations, reportez-vous à la section [Configuration de votre Programme](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

La deuxième étape est le libre-service pour chaque AEM en tant qu&#39;environnement Cloud Service. Il existe d’autres configurations que vous devrez effectuer après l’approvisionnement initial du module complémentaire CIF.

## Connexion du commerce AEM avec le Magento {#magento}

Pour connecter le module complémentaire CIF et les [AEM composants principaux CIF](https://github.com/adobe/aem-core-cif-components) avec votre environnement Magento, vous devez fournir l’URL du point de terminaison GraphQL Magento via une variable d’environnement Cloud Manager. Le nom de la variable est `COMMERCE_ENDPOINT`. Une connexion sécurisée via HTTPS doit être configurée.
Une autre URL de point de terminaison GraphQL Magento peut être utilisée pour chaque AEM en tant qu’environnement Cloud Service. De cette façon, les projets peuvent relier les environnements d&#39;évaluation AEM aux systèmes d&#39;évaluation Magento et à l&#39;environnement de production AEM à un système de production Magento. Ce point de terminaison GraphQL Magento doit être accessible au public, les connexions VPN privées ou locales ne sont pas prises en charge.

Pour connecter AEM Commerce à un Magento, procédez comme suit :

1. Obtenez l’interface de ligne de commande Adobe I/O avec le module externe Cloud Manager

   Consultez la documentation [Adobe Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) pour savoir comment télécharger, configurer et utiliser [l’interface de ligne de commande Adobe I/O](https://github.com/adobe/aio-cli) avec le [module d’interface de ligne de commande Cloud Manager](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. Authentification de l’interface de ligne de commande avec l’AEM en tant que programme Cloud Service

3. Définir la variable `COMMERCE_ENDPOINT` dans Cloud Manager

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Voir [Documentation sur l’interface de ligne de commande](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) pour plus de détails.

   L’URL du point de terminaison GraphQL du Magento doit pointer vers le service GraphQl du Magento et utiliser une connexion HTTPS sécurisée. Par exemple : `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>Vous pouvez liste toutes les variables de Cloud Manager à l’aide de la commande suivante pour vérifier le doublon : `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

>[!NOTE]
>
>Vous pouvez également utiliser l’[API Cloud Manager](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) pour configurer également les variables Cloud Manager.

Vous pouvez ainsi utiliser AEM Commerce en tant que Cloud Service et déployer votre projet via Cloud Manager.

## Intégrations commerciales tierces {#integrations}

Pour les intégrations de commerce tierces, une [couche de mappage d’API](architecture/third-party.md) est nécessaire pour connecter AEM Commerce en tant que Cloud Service et composants principaux CIF à votre système de commerce. Cette couche de mappage d’API est généralement déployée sur Adobe I/O Runtime. Contactez votre représentant commercial pour connaître les intégrations disponibles et l’accès à Adobe I/O Runtime.
