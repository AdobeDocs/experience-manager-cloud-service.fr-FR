---
title: Prise en main d’AEM Commerce as a Cloud Service
description: Découvrez comment déployer un projet AEM compatible avec le commerce dans un environnement AEM as a Cloud service opérationnel. Utilisez les fonctionnalités d’Adobe Cloud Manager et un pipeline CI/CD pour construire la vitrine de référence Venia dans un environnement opérationnel.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
translation-type: tm+mt
source-git-commit: e34592d24c8f6c17e6959db1d5c513feaf6381c8
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 68%

---

# Prise en main d’AEM Commerce as a Cloud Service {#start}

Pour commencer à utiliser AEM Commerce as a Cloud Service, votre instance Experience Manager Cloud Service doit être configurée avec le module complémentaire CIF (Commerce Integration Framework). Le module complémentaire CIF est un module supplémentaire ajouté à [AEM Sites as a Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/sites/home.html).

## Intégration {#onboarding}

L’intégration à AEM Commerce as a Cloud Service est un processus à deux étapes :

1. Activation d’AEM Commerce as a Cloud Service et approvisionnement du module complémentaire CIF
2. Connecter AEM Commerce en tant que Cloud Service à votre solution commerciale

La première étape de l&#39;intégration est effectuée par Adobe. Pour plus d’informations sur la tarification et l’approvisionnement, contactez votre représentant commercial.

Une fois que vous disposez du module complémentaire CIF, celui-ci est appliqué à tout programme Cloud Manager existant. Si vous n’avez pas de programme Cloud Manager, vous devrez en créer un. Pour plus d’informations, voir [Configuration de votre programme](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

La deuxième étape s’effectue en libre-service pour chaque environnement AEM as a Cloud Service. Il existe d’autres configurations que vous devrez effectuer après l’approvisionnement initial du module complémentaire CIF.

## Connexion d&#39;AEM à une solution de commerce {#magento}

Pour connecter le module complémentaire CIF et les [AEM composants principaux CIF](https://github.com/adobe/aem-core-cif-components) à une solution commerciale, vous devez fournir l’URL du point de terminaison GraphQL via une variable d’environnement Cloud Manager. Le nom de la variable est `COMMERCE_ENDPOINT`. Une connexion sécurisée via HTTPS doit être configurée.
Une autre URL de point d’entrée GraphQL peut être utilisée pour chaque environnement AEM as a Cloud Service. De cette façon, les projets peuvent relier AEM environnements d&#39;évaluation à des systèmes d&#39;évaluation de commerce et à un environnement de production AEM à un système de production de commerce. Ce point d’entrée GraphQL doit être accessible au public, et les connexions VPN privées ou locales ne sont pas prises en charge. Vous pouvez éventuellement fournir un en-tête d’authentification afin d’utiliser des fonctions CIF supplémentaires nécessitant une authentification.

Il existe deux options pour configurer le point de terminaison :

### 1) Via l’interface utilisateur de Cloud Manager (par défaut)

Pour ce faire, vous pouvez ouvrir une boîte de dialogue sur la page Détails de l’Environnement. Lors de l’affichage de cette page pour un programme compatible Commerce, un bouton s’affiche si le point de terminaison n’est pas actuellement configuré :

![Mise en œuvre finale du badge Écologique](/help/commerce-cloud/assets/commerce-cmui.png)

Cliquez sur ce bouton pour ouvrir une boîte de dialogue :

![Mise en œuvre finale du badge Écologique](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Une fois le point de terminaison (et, éventuellement, le jeton) défini, le point de terminaison s’affiche sur la page de détails. Cliquez sur l’icône Modifier pour ouvrir la même boîte de dialogue où le point de terminaison peut être modifié si nécessaire.

![Mise en œuvre finale du badge Écologique](/help/commerce-cloud/assets/commerce-cmui-done.png)

### 2) Par Adobe I/O CLI

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Pour connecter AEM à une solution commerciale via l’interface de ligne de commande Adobe I/O, procédez comme suit :

1. Procurez-vous la ligne de commande d’Adobe I/O avec le plug-in Cloud Manager.

   Consultez la [documentation d’Adobe Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) relative à la manière de télécharger, de configurer et d’utiliser la [ligne de commande d’Adobe I/O](https://github.com/adobe/aio-cli) avec le [plug-in de ligne de commande Cloud Manager](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. Authentification de l’interface de ligne de commande de l’Adobe I/O avec l’AEM en tant que programme Cloud Service

3. Définissez la variable `COMMERCE_ENDPOINT` dans Cloud Manager.

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Pour plus d’informations, voir la [documentation sur la ligne de commande](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   L’URL du point de terminaison GraphQL du commerce doit pointer vers le service GraphQl du commerce et utiliser une connexion HTTPS sécurisée. Par exemple : `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>Pour vérifier, vous pouvez répertorier toutes les variables de Cloud Manager à l’aide de la commande suivante : `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

Vous êtes ainsi prêt à utiliser AEM Commerce as a Cloud Service et vous pouvez déployer votre projet via Cloud Manager.

## Activer les fonctionnalités nécessitant une authentification (facultatif) {#staging}

>[!NOTE]
>
>Cette fonctionnalité est disponible uniquement avec Magento Enterprise Edition ou Magento Cloud.

1. Connectez-vous à Magento et créez un jeton d’intégration. Voir la section [Authentification basée sur un jeton](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens) pour en savoir plus. Assurez-vous que le jeton d’intégration a *uniquement* accès aux ressources `Content -> Staging`. Copiez la valeur `Access Token`.

1. Définissez la variable secrète `COMMERCE_AUTH_HEADER` dans Cloud Manager :

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

   Voir la section [Connexion d’AEM Commerce à Magento](#magento) pour savoir comment configurer l’interface de ligne de commande Adobe I/O pour Cloud Manager.

## Intégrations commerciales tierces {#integrations}

Pour les intégrations commerciales tierces, une [couche de mappage d’API](architecture/third-party.md) est nécessaire afin de connecter AEM Commerce as a Cloud Service et les composants principaux CIF à votre système Commerce. Cette couche de mappage d’API est généralement déployée sur Adobe I/O Runtime. Contactez votre représentant commercial pour connaître les intégrations disponibles et accéder à Adobe I/O Runtime.
