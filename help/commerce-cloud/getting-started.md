---
title: Prise en main d’AEM Commerce as a Cloud Service
description: Découvrez comment déployer un projet AEM compatible avec le commerce sur un AEM en cours d’exécution en tant qu’environnement de service Cloud. Utilisez les fonctionnalités d’Adobe Cloud Manager et un pipeline CI/CD pour construire la vitrine de référence Venia sur un environnement en cours d’exécution.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
translation-type: tm+mt
source-git-commit: 7a26596b00f276404934e467490ff79d08b0e1d0
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 80%

---


# Prise en main d’AEM Commerce as a Cloud Service {#start}

Pour commencer à utiliser AEM Commerce as a Cloud Service, votre instance Experience Manager Cloud Service doit être configurée avec le module complémentaire CIF (Commerce Integration Framework). Le module complémentaire CIF est un module supplémentaire ajouté à [AEM Sites as a Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/sites/home.html).

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

## Intégration {#onboarding}

L’intégration à AEM Commerce as a Cloud Service est un processus à deux étapes :

1. Activation d’AEM Commerce as a Cloud Service et approvisionnement du module complémentaire CIF
2. Connexion d’AEM Commerce as a Cloud Service à votre environnement Magento

La première étape est effectuée par Adobe. Vous devrez fournir des informations telles que l’organisation IMS, l’URL du point d’entrée GraphQL de votre environnement Magento, etc., dans le cadre du processus d’approvisionnement. Pour plus d’informations sur la tarification et l’approvisionnement, contactez votre représentant commercial.

Une fois que vous disposez du module complémentaire CIF, celui-ci est appliqué à tout programme Cloud Manager existant. Si vous n’avez pas de programme Cloud Manager, vous devrez en créer un. Pour plus d’informations, voir [Configuration de votre programme](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

La deuxième étape s’effectue en libre-service pour chaque environnement AEM as a Cloud Service. Il existe d’autres configurations que vous devrez effectuer après l’approvisionnement initial du module complémentaire CIF.

## Connexion d’AEM Commerce à Magento {#magento}

Pour connecter le module complémentaire CIF et les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) à votre environnement Magento, vous devez fournir l’URL du point d’entrée Magento GraphQL via une variable d’environnement Cloud Manager. Le nom de la variable est `COMMERCE_ENDPOINT`. Une connexion sécurisée via HTTPS doit être configurée.
Une autre URL de point d’entrée Magento GraphQL peut être utilisée pour chaque environnement AEM as a Cloud Service. De cette façon, les projets peuvent connecter les environnements d’évaluation AEM avec les systèmes d’évaluation Magento et l’environnement de production AEM à un système de production Magento. Ce point d’entrée Magento GraphQL doit être accessible au public, et les connexions VPN privées ou locales ne sont pas prises en charge.

Pour connecter AEM Commerce à Magento, procédez comme suit :

1. Procurez-vous la ligne de commande d’Adobe I/O avec le plug-in Cloud Manager.

   Consultez la [documentation d’Adobe Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) relative à la manière de télécharger, de configurer et d’utiliser la [ligne de commande d’Adobe I/O](https://github.com/adobe/aio-cli) avec le [plug-in de ligne de commande Cloud Manager](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. Authentifiez la ligne de commande avec le programme AEM as a Cloud Service.

3. Définissez la variable `COMMERCE_ENDPOINT` dans Cloud Manager.

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Pour plus d’informations, voir la [documentation sur la ligne de commande](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   L’URL du point d’entrée Magento GraphQL doit pointer vers le service GraphQl de Magento et utiliser une connexion HTTPS sécurisée. Par exemple : `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>Pour vérifier, vous pouvez répertorier toutes les variables de Cloud Manager à l’aide de la commande suivante : `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

>[!NOTE]
>
>Vous pouvez également utiliser l’[API Cloud Manager](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) pour configurer également les variables Cloud Manager.

Vous êtes ainsi prêt à utiliser AEM Commerce as a Cloud Service et pouvez déployer votre projet via Cloud Manager.

## Activer les fonctionnalités du catalogue intermédiaire (facultatif) {#staging}

>[!NOTE]
>
>Cette fonctionnalité est disponible uniquement avec Magento Enterprise Edition ou Magento Cloud.

1. Connectez-vous au Magento et créez un jeton d’intégration. Voir [Authentification basée sur un jeton](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens) pour plus de détails. Assurez-vous que le jeton d’intégration a *accès* uniquement aux ressources `Content -> Staging`. Copiez la valeur `Access Token`.

1. Définissez la variable secrète `COMMERCE_AUTH_HEADER` dans Cloud Manager :

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization Bearer: <Access Token>"
   ```

   Consultez [Connexion de AEM Commerce avec le Magento](#magento) pour savoir comment configurer l’interface de ligne de commande Adobe I/O pour Cloud Manager.

## Intégrations commerciales tierces {#integrations}

Pour les intégrations commerciales tierces, une [couche de mappage d’API](architecture/third-party.md) est nécessaire afin de connecter AEM Commerce as a Cloud Service et les composants principaux CIF à votre système Commerce. Cette couche de mappage d’API est généralement déployée sur Adobe I/O Runtime. Contactez votre représentant commercial pour connaître les intégrations disponibles et accéder à Adobe I/O Runtime.
