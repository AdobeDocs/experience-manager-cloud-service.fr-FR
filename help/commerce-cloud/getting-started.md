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
source-git-commit: 08e258d4e9cd67de3da2aa57c058036bd104472d
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 37%

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

## Connexion d&#39;AEM à une solution commerciale {#magento}

Pour connecter le module complémentaire CIF et les [AEM composants principaux CIF](https://github.com/adobe/aem-core-cif-components) à une solution commerciale, vous devez fournir l’URL du point de terminaison GraphQL via une variable d’environnement Cloud Manager. Le nom de la variable est `COMMERCE_ENDPOINT`. Une connexion sécurisée via HTTPS doit être configurée.

Cette variable d’environnement est utilisée à deux endroits :

- Appels GraphQL de AEM vers le serveur principal de commerce, via un client GraphQl partagé commun, utilisé par les composants principaux CIF AEM et les composants de projet client.
- Configurez une URL de proxy GraphQL sur chaque environnement AEM la variable est définie sur `/api/graphql`. Il est utilisé par les outils de création de commerce AEM (module complémentaire CIF) et les composants côté client CIF.

Une autre URL de point d’entrée GraphQL peut être utilisée pour chaque environnement AEM as a Cloud Service. De cette façon, les projets peuvent relier AEM environnements d&#39;évaluation à des systèmes d&#39;évaluation de commerce et à un environnement de production AEM à un système de production de commerce. Ce point d’entrée GraphQL doit être accessible au public, et les connexions VPN privées ou locales ne sont pas prises en charge. Vous pouvez éventuellement fournir un en-tête d’authentification afin d’utiliser des fonctions CIF supplémentaires nécessitant une authentification.

Facultatif et uniquement pour Adobe Commerce Enterprise / Cloud, le module complémentaire CIF prend en charge l’utilisation de données de catalogue intermédiaire pour les auteurs d’AEM. Pour ce faire, vous devez configurer un jeton d’autorisation. Le jeton d’autorisation configuré n’est disponible et utilisé que sur les instances d’auteur AEM pour des raisons de sécurité. AEM instances de publication ne peuvent pas afficher les données par étapes.

Il existe deux options pour configurer le point de terminaison :

### Via l’interface utilisateur de Cloud Manager (par défaut) {#cm-ui}

Pour ce faire, vous pouvez ouvrir une boîte de dialogue sur la page Détails de l’Environnement. Lors de l’affichage de cette page pour un programme compatible Commerce, un bouton s’affiche si le point de terminaison n’est pas actuellement configuré :

![Informations sur l&#39;environnement CM](/help/commerce-cloud/assets/commerce-cmui.png)

Cliquez sur ce bouton pour ouvrir une boîte de dialogue :

![CM Commerce Endpoint](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Une fois le point de terminaison (éventuellement un jeton d’authentification pour la prise en charge de catalogue intermédiaire) défini, le point de terminaison s’affiche dans la page de détails. Cliquez sur l’icône Modifier pour ouvrir la même boîte de dialogue où le point de terminaison peut être modifié si nécessaire.

![Informations sur l&#39;environnement CM](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Par Adobe I/O CLI {#adobe-cli}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Pour connecter AEM à une solution commerciale via l’interface de ligne de commande Adobe I/O, procédez comme suit :

1. Procurez-vous la ligne de commande d’Adobe I/O avec le plug-in Cloud Manager.

   Consultez la [documentation de Adobe Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) pour savoir comment télécharger, configurer et utiliser l’[interface de ligne de commande de l’Adobe I/O ](https://github.com/adobe/aio-cli) avec le [module d’interface de ligne de commande Cloud Manager](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. Authentification de l’interface de ligne de commande de l’Adobe I/O avec l’AEM en tant que programme Cloud Service

3. Définissez la variable `COMMERCE_ENDPOINT` dans Cloud Manager.

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Pour plus d’informations, voir la [documentation sur la ligne de commande](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   L’URL du point de terminaison GraphQL du commerce doit pointer vers le service GraphQl du commerce et utiliser une connexion HTTPS sécurisée. Par exemple : `https://demo.magentosite.cloud/graphql`.

4. Activer les fonctionnalités de catalogue intermédiaire qui nécessitent une authentification (facultatif)

   >[!NOTE]
   >
   >Cette fonctionnalité est disponible uniquement avec Adobe Commerce Enterprise ou Cloud Edition. Voir la section [Authentification basée sur un jeton](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens) pour en savoir plus.

   Définissez la variable secrète `COMMERCE_AUTH_HEADER` dans Cloud Manager :

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>Pour vérifier, vous pouvez répertorier toutes les variables de Cloud Manager à l’aide de la commande suivante : `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

Vous êtes ainsi prêt à utiliser AEM Commerce as a Cloud Service et vous pouvez déployer votre projet via Cloud Manager.

## Configuration des magasins et des catalogues {#catalog}

Le module complémentaire CIF et les [composants principaux CIF](https://github.com/adobe/aem-core-cif-components) peuvent être utilisés sur plusieurs structures de site AEM connectées à différents magasins de commerce (ou vues de stockage, etc.). Par défaut, le module complémentaire CIF est déployé avec une configuration par défaut se connectant au magasin et catalogue par défaut d&#39;Adobe Commerce (Magento).

Cette configuration peut être ajustée pour le projet via la configuration du Cloud Service CIF en procédant comme suit :

1. Dans AEM accédez à Outils -> Cloud Services -> Configuration CIF

2. Sélectionnez la configuration commerciale à modifier.

3. Ouvrez les propriétés de configuration via la barre d’actions.

![Configuration des Cloud Services CIF](/help/commerce-cloud/assets/cif-cloud-service-config.png)

Les propriétés suivantes peuvent être configurées :

- Client GraphQL : sélectionnez le client GraphQL configuré pour la communication d&#39;arrière-plan de commerce. En règle générale, cette option doit rester par défaut.
- Vue de stockage : identifiant (Magento) de vue de stockage. Si elle est vide, la vue de stockage par défaut est utilisée.
- Chemin d&#39;accès du proxy GraphQL : chemin d&#39;accès de l&#39;URL Proxy GraphQL dans AEM utilisé pour les demandes de proxy au point de terminaison GraphQL principal du commerce.
   >[!NOTE]
   >
   > Dans la plupart des configurations, la valeur par défaut `/api/graphql` ne doit pas être modifiée. Seule une configuration avancée n&#39;utilisant pas le proxy GraphQL fourni doit modifier ce paramètre.
- Activer la prise en charge de l&#39;UID du catalogue : activez la prise en charge de l&#39;UID plutôt que de l&#39;ID dans les appels GraphQL d&#39;arrière-plan du commerce.
   >[!NOTE]
   >
   > La prise en charge des UID a été introduite dans Adobe Commerce (Magento) 2.4.2. Activez cette option uniquement si votre serveur principal de commerce prend en charge un schéma GraphQL de la version 2.4.2 ou ultérieure.
- Identifiant de Catégorie racine du catalogue - identifiant (UID ou ID) de la racine du catalogue de stockage

La configuration illustrée ci-dessus est à titre de référence. Les projets doivent fournir leurs propres configurations.

Pour des configurations plus complexes à l’aide de plusieurs structures de site AEM associées à différents catalogues commerciaux, consultez le [didacticiel Configuration de plusieurs magasins de commerce](configuring/multi-store-setup.md).

## Ressources supplémentaires {#additional-resources}

- [Archétype de projet AEM](https://github.com/adobe/aem-project-archetype)
- [Magasin de référence Venia AEM](https://github.com/adobe/aem-cif-guides-venia)
- [Configuration de plusieurs magasins commerciaux](configuring/multi-store-setup.md)
