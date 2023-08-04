---
title: Prise en main d’AEM Commerce as a Cloud Service
description: Découvrez comment déployer un projet de commerce AEM à l’aide d’Adobe Cloud Manager, d’un pipeline CI/CD et du storefront de référence Venia.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: Cloud Service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
source-git-commit: ba0c1e13f311f48ac138f2c3ca582835a4a83bf6
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 44%

---

# Prise en main d’AEM Commerce as a Cloud Service {#start}

Pour commencer à utiliser AEM Commerce as a Cloud Service, votre Experience Manager Cloud Service doit être configuré avec le module complémentaire CIF (Commerce Integration Framework). Le module complémentaire CIF est un module supplémentaire ajouté à la [AEM Sites as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/home.html).

## Intégration {#onboarding}

L’intégration à AEM Commerce as a Cloud Service est un processus à deux étapes :

1. Activation d’AEM Commerce as a Cloud Service et approvisionnement du module complémentaire CIF
2. Connexion d’AEM Commerce as a Cloud Service à votre solution de commerce

La première étape d’intégration est effectuée par Adobe. Pour plus d’informations sur la tarification et la mise en service, contactez votre représentant commercial.

Une fois que vous avez reçu le module complémentaire CIF, il est appliqué à tous les programmes Cloud Manager existants. Si vous ne disposez pas d’un programme Cloud Manager, vous devez en créer un. Pour plus d’informations, voir [Configuration de votre programme](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/getting-started/program-setup.html).

La deuxième étape s’effectue en libre-service pour chaque environnement AEM as a Cloud Service. Il existe d’autres configurations que vous devez effectuer après la mise en service initiale du module complémentaire CIF.

## Connexion d’AEM à une solution de commerce {#solution}

Pour connecter le module complémentaire CIF et le [AEM Composants principaux CIF](https://github.com/adobe/aem-core-cif-components) avec une solution commerciale, vous devez fournir l’URL du point de terminaison GraphQL au moyen d’une variable d’environnement Cloud Manager. Le nom de la variable est `COMMERCE_ENDPOINT`. Une connexion sécurisée par le biais de HTTPS doit être configurée.

Cette variable d’environnement est utilisée à deux endroits :

- Les appels GraphQL d’AEM au serveur principal Commerce, par le biais d’un client GraphQl partageable commun, utilisé par les composants principaux CIF AEM et les composants de projet client.
- Configurez une URL de proxy GraphQL sur chaque environnement AEM la variable est disponible à l’adresse `/api/graphql`. Cette URL est utilisée par les outils de création de commerce AEM (module complémentaire CIF) et les composants côté client CIF.

Une autre URL de point d’entrée GraphQL peut être utilisée pour chaque environnement AEM as a Cloud Service. De cette façon, les projets peuvent connecter les environnements d’évaluation AEM avec les systèmes d’évaluation de commerce et l’environnement de production AEM à un système de production de commerce. Ce point d’entrée GraphQL doit être accessible au public, et les connexions VPN privées ou locales ne sont pas prises en charge. Vous pouvez éventuellement fournir un en-tête d’authentification pour utiliser des fonctionnalités CIF supplémentaires nécessitant une authentification.

Si vous le souhaitez, et uniquement pour Adobe Commerce Enterprise/Cloud, le module complémentaire CIF prend en charge l’utilisation de données de catalogue intermédiaires pour les auteurs AEM. Ces données nécessitent que vous configuriez un en-tête d’autorisation. Pour des raisons de sécurité, l’en-tête n’est disponible et utilisé que sur les instances d’auteur AEM. Les instances AEM de publication ne peuvent pas afficher de données intermédiaires.

Il existe deux options pour configurer le point d’entrée :

### Par le biais de l’interface utilisateur de Cloud Manager (par défaut) {#cm-ui}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Cette configuration peut être effectuée à l’aide d’une boîte de dialogue sur la page Détails de l’environnement . Lorsque vous affichez cette page pour un programme compatible Commerce, un bouton s’affiche si le point de terminaison n’est pas actuellement configuré :

![Informations sur l’environnement de CM](/help/commerce-cloud/assets/commerce-cmui.png)

Cliquez sur ce bouton pour ouvrir une boîte de dialogue :

![Point d’entrée CM Commerce](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Une fois le point de terminaison défini et éventuellement un en-tête d’autorisation pour la prise en charge d’un catalogue intermédiaire, le point de terminaison s’affiche sur la page de détails. Cliquez sur l’icône Modifier pour ouvrir la boîte de dialogue dans laquelle vous pouvez modifier le point de fin, si nécessaire.

![Informations sur l’environnement de CM](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Par Adobe I/O, interface de ligne de commande  {#adobe-cli}

Pour connecter AEM à une solution de commerce par le biais de l’interface de ligne de commande d’Adobe I/O, procédez comme suit :

1. Procurez-vous l’interface de ligne de commande d’Adobe I/O avec le plug-in Cloud Manager.

   Vérifiez les [Documentation d’Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=fr) sur la procédure de téléchargement, de configuration et d’utilisation de la variable [Interface de ligne de commande Adobe I/O](https://github.com/adobe/aio-cli) avec la propriété [Module d’interface de ligne de commande de Cloud Manager](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. Authentifiez l’interface de ligne de commande Adobe I/O avec le programme AEM as a Cloud Service.

3. Définissez la variable `COMMERCE_ENDPOINT` dans Cloud Manager.

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Pour plus d’informations, voir la [documentation sur la ligne de commande](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   L’URL du point d’entrée commerce GraphQL doit pointer vers le service GraphQl de commerce et utiliser une connexion HTTPS sécurisée. Par exemple : `https://<yourcommercesystem>/graphql`.

4. Activation des fonctionnalités de catalogue intermédiaire nécessitant une authentification (facultatif)

   >[!NOTE]
   >
   >Cette fonctionnalité est disponible uniquement avec Adobe Commerce Enterprise ou Cloud Edition. Voir la section [Authentification basée sur un jeton](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens) pour en savoir plus.

   Définissez la variable secrète `COMMERCE_AUTH_HEADER` dans Cloud Manager :

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>Pour vérifier, vous pouvez répertorier toutes les variables de Cloud Manager à l’aide de la commande suivante : `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

Vous êtes prêt à utiliser AEM Commerce as a Cloud Service et pouvez déployer votre projet à l’aide de Cloud Manager.

## Configuration des magasins et des catalogues {#catalog}

Le module complémentaire CIF et la variable [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components) peut être utilisé sur plusieurs structures de site AEM connectées à différents magasins de commerce (ou vues de magasin, etc.). Par défaut, le module complémentaire CIF est déployé avec une configuration par défaut se connectant au magasin et au catalogue par défaut d’Adobe Commerce.

Cette configuration peut être ajustée pour le projet au moyen de la configuration du Cloud Service CIF en procédant comme suit :

1. Dans AEM, accédez à Outils -> Cloud Services -> Configuration CIF.

2. Sélectionnez la configuration commerciale à modifier.

3. Ouvrez les propriétés de configuration à l’aide de la barre d’actions.

![Configuration des Cloud Services CIF](/help/commerce-cloud/assets/cif-cloud-service-config.png)

Les propriétés suivantes peuvent être configurées :

- Client GraphQL : sélectionnez le client GraphQL configuré pour la communication du serveur principal Commerce. Ce client doit généralement rester par défaut.
- Affichage de magasin : identifiant d’affichage du magasin. Si cette valeur est vide, la vue de magasin par défaut est utilisée.
- Chemin du proxy GraphQL : chemin d’URL du proxy GraphQL dans AEM utilisé pour les requêtes proxy vers le point d’entrée GraphQL principal de commerce.
  >[!NOTE]
  >
  > Dans la plupart des configurations, la valeur par défaut `/api/graphql` ne doit pas être modifié. Seule une configuration avancée n’utilisant pas le proxy GraphQL fourni doit modifier ce paramètre.
- Activer la prise en charge de l’UID du catalogue : activez la prise en charge de l’UID au lieu de l’ID dans les appels GraphQL du serveur principal de commerce.
  >[!NOTE]
  >
  > Prise en charge des UID dans Adobe Commerce 2.4.2. Activez les UID uniquement si votre serveur principal Commerce prend en charge un schéma GraphQL de la version 2.4.2 ou ultérieure.
- Identifiant de catégorie racine du catalogue : l’identifiant (UID ou ID) de la racine du catalogue du magasin.
  >[!CAUTION]
  >
  > À compter de la version 2.0.0 des composants principaux CIF, la prise en charge de `id` a été supprimée et remplacée par `uid`. Si votre projet utilise la version 2.0.0 des composants principaux CIF, vous devez activer la prise en charge de l’UID de catalogue et utiliser un UID de catégorie valide comme « identifiant de catégorie racine de catalogue ».

La configuration illustrée ci-dessus est fournie à titre de référence. Les projets doivent fournir leurs propres configurations.

Pour les configurations plus complexes, l’utilisation de plusieurs structures de site AEM combinées à différents catalogues commerciaux, voir la section [Configuration multi-magasin Commerce](configuring/multi-store-setup.md) tutoriel .

## Ressources supplémentaires {#additional-resources}

- [Archétype de projet AEM](https://github.com/adobe/aem-project-archetype)
- [Magasin de référence Venia AEM](https://github.com/adobe/aem-cif-guides-venia)
- [Configuration multi-magasin Commerce](configuring/multi-store-setup.md)
- [Plusieurs configurations de systèmes de commerce](configuring/multiple-commerce-systems-setup.md)

