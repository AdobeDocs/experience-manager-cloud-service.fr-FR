---
title: Prise en main d’AEM Commerce as a Cloud Service
description: Découvrez comment déployer un projet AEM compatible avec le commerce dans un environnement AEM as a Cloud service opérationnel. Utilisez les fonctionnalités d’Adobe Cloud Manager et un pipeline CI/CD pour construire la vitrine de référence Venia dans un environnement opérationnel.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
source-git-commit: d85352b93b9c793a716841523677eb710bb4577c
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 100%

---

# Prise en main d’AEM Commerce as a Cloud Service {#start}

Pour commencer à utiliser AEM Commerce as a Cloud Service, votre instance Experience Manager Cloud Service doit être configurée avec le module complémentaire CIF (Commerce Integration Framework). Le module complémentaire CIF est un module supplémentaire ajouté à [AEM Sites as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/home.html?lang=fr).

## Intégration {#onboarding}

L’intégration à AEM Commerce as a Cloud Service est un processus à deux étapes :

1. Activation d’AEM Commerce as a Cloud Service et approvisionnement du module complémentaire CIF
2. Connexion d’AEM Commerce as a Cloud Service à votre solution de commerce

La première étape d’intégration est effectuée par Adobe. Pour plus d’informations sur la tarification et l’approvisionnement, contactez votre représentant commercial.

Une fois que vous disposez du module complémentaire CIF, celui-ci est appliqué à tout programme Cloud Manager existant. Si vous n’avez pas de programme Cloud Manager, vous devrez en créer un. Pour plus d’informations, voir [Configuration de votre programme](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/setting-up-program.html?lang=fr).

La deuxième étape s’effectue en libre-service pour chaque environnement AEM as a Cloud Service. Il existe d’autres configurations que vous devrez effectuer après l’approvisionnement initial du module complémentaire CIF.

## Connexion d’AEM à une solution de commerce {#solution}

Pour connecter le module complémentaire CIF et les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) à votre environnement, vous devez fournir l’URL du point d’entrée GraphQL via une variable d’environnement Cloud Manager. Le nom de la variable est `COMMERCE_ENDPOINT`. Une connexion sécurisée via HTTPS doit être configurée.

Cette variable d’environnement est utilisée à deux endroits :

- Appels GraphQL d’AEM au serveur principal Commerce, via un client GraphQl partageable commun, utilisé par les composants principaux CIF AEM et les composants de projet client.
- Configurez une URL de proxy GraphQL sur chaque environnement AEM, la variable est définie sur `/api/graphql`. Elle est utilisée par les outils de création de commerce AEM (module complémentaire CIF) et les composants côté client CIF.

Une autre URL de point d’entrée GraphQL peut être utilisée pour chaque environnement AEM as a Cloud Service. De cette façon, les projets peuvent connecter les environnements d’évaluation AEM avec les systèmes d’évaluation de commerce et l’environnement de production AEM à un système de production de commerce. Ce point d’entrée GraphQL doit être accessible au public, et les connexions VPN privées ou locales ne sont pas prises en charge. Vous pouvez éventuellement fournir un en-tête d’authentification afin d’utiliser des fonctionnalités CIF supplémentaires nécessitant une authentification.

Facultatif et destiné uniquement à Adobe Commerce Enterprise/Cloud, le module complémentaire CIF prend en charge l’utilisation de données de catalogue intermédiaires pour les auteurs d’AEM. Pour ce faire, vous devez configurer un en-tête d’autorisation. Pour des raisons de sécurité, l’en-tête n’est disponible et utilisé que sur les instances d’auteur AEM. Les instances AEM de publication ne peuvent pas afficher de données intermédiaires.

Il existe deux options pour configurer le point d’entrée :

### Via l’interface utilisateur de Cloud Manager (par défaut) {#cm-ui}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Vous pouvez le faire à l’aide d’une boîte de dialogue sur la page Détails de l’environnement. Lorsque vous affichez cette page pour un programme compatible avec le commerce, un bouton s’affiche si le point d’entrée n’est pas actuellement configuré :

![Informations sur l’environnement de CM](/help/commerce-cloud/assets/commerce-cmui.png)

Cliquez sur ce bouton pour ouvrir une boîte de dialogue :

![Point d’entrée CM Commerce](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Une fois le point d’entrée défini (et éventuellement l’en-tête d’authentification pour la prise en charge d’un catalogue intermédiaire), il s’affiche sur la page de détails. Cliquez sur l’icône Modifier pour ouvrir la boîte de dialogue dans laquelle le point d’entrée peut être modifié, si nécessaire.

![Informations sur l’environnement de CM](/help/commerce-cloud/assets/commerce-cmui-done.png)

### via l’interface de ligne de commande Adobe I/O   {#adobe-cli}

Pour connecter AEM à une solution de commerce via l’interface de ligne de commande d’Adobe I/O, procédez comme suit :

1. Procurez-vous l’interface de ligne de commande d’Adobe I/O avec le plug-in Cloud Manager.

   Consultez la [documentation d’Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=fr) relative à la manière de télécharger, de configurer et d’utiliser l’[interface de ligne de commande d’Adobe I/O](https://github.com/adobe/aio-cli) avec le [plug-in de ligne de commande Cloud Manager](https://github.com/adobe/aio-cli-plugin-cloudmanager).

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

Vous êtes ainsi prêt à utiliser AEM Commerce as a Cloud Service et vous pouvez déployer votre projet via Cloud Manager

## Configuration des magasins et des catalogues {#catalog}

Le module complémentaire CIF et les [composants principaux CIF](https://github.com/adobe/aem-core-cif-components) peuvent être utilisés sur plusieurs structures de site AEM connectées à différents magasins commerciaux (ou vues de magasin, etc.). Par défaut, le module complémentaire CIF est déployé avec une configuration par défaut se connectant au magasin et au catalogue par défaut d’Adobe Commerce.

Cette configuration peut être ajustée pour le projet par le biais de la configuration de Cloud Service CIF en procédant comme suit :

1. Dans AEM, accédez à Outils -> Cloud Services -> Configuration CIF.

2. Sélectionnez la configuration commerciale à modifier.

3. Ouvrez les propriétés de configuration via la barre d’actions.

![Configuration des Cloud Services CIF](/help/commerce-cloud/assets/cif-cloud-service-config.png)

Les propriétés suivantes peuvent être configurées :

- Client GraphQL : sélectionnez le client GraphQL configuré pour la communication du serveur principal Commerce. Cette sélection doit généralement être maintenue par défaut.
- Affichage de magasin : identifiant d’affichage du magasin. Si cette valeur est vide, la vue de magasin par défaut est utilisée.
- Chemin du proxy GraphQL : chemin d’URL du proxy GraphQL dans AEM utilisé pour les requêtes proxy vers le point d’entrée GraphQL principal de commerce.
   >[!NOTE]
   >
   > Dans la plupart des configurations, la valeur par défaut `/api/graphql` ne doit pas être modifiée. Seule une configuration avancée n’utilisant pas le proxy GraphQL fourni doit modifier ce paramètre.
- Activer la prise en charge de l’UID du catalogue : activez la prise en charge de l’UID au lieu de l’ID dans les appels GraphQL du serveur principal de commerce.
   >[!NOTE]
   >
   > La prise en charge des UID a été introduite dans Adobe Commerce version 2.4.2. Activez cette option uniquement si votre serveur principal Commerce prend en charge un schéma GraphQL de la version 2.4.2 ou ultérieure.
- Identifiant de catégorie racine du catalogue : l’identifiant (UID ou ID) de la racine du catalogue du magasin.
   >[!CAUTION]
   >
   > À compter de la version 2.0.0 des composants principaux CIF, la prise en charge de `id` a été supprimée et remplacée par `uid`. Si votre projet utilise la version 2.0.0 des composants principaux CIF, vous devez activer la prise en charge de l’UID de catalogue et utiliser un UID de catégorie valide comme « identifiant de catégorie racine de catalogue ».

La configuration illustrée ci-dessus est à titre de référence. Les projets doivent fournir leurs propres configurations.

Pour des configurations plus complexes à l’aide de plusieurs structures de site AEM combinées à différents catalogues commerciaux, consultez le tutoriel [Configuration multi-magasin Commerce](configuring/multi-store-setup.md).

## Ressources supplémentaires {#additional-resources}

- [Archétype de projet AEM](https://github.com/adobe/aem-project-archetype)
- [Magasin de référence Venia AEM](https://github.com/adobe/aem-cif-guides-venia)
- [Configuration multi-magasin Commerce](configuring/multi-store-setup.md)
