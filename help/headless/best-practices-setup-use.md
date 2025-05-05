---
title: Bonnes pratiques pour la configuration et l’utilisation d’AEM GraphQL avec des fragments de contenu
description: Découvrez les bonnes pratiques recommandées pour la configuration et l’utilisation d’AEM GraphQL avec des fragments de contenu.
exl-id: 4d6a5aaa-c8be-4858-ad07-085dc4fb77e7
feature: Headless
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 40%

---

# Bonnes pratiques pour la configuration et l’utilisation d’AEM GraphQL avec des fragments de contenu{#best-practices-setup-use-aem-graphql-content-fragments}

Ces instructions résument les bonnes pratiques recommandées pour configurer, configurer et utiliser AEM avec GraphQL et les fragments de contenu.

## Commencer {#getting-started}

Pour vous aider à vous mettre à niveau :

* [Qu&#39;est-ce que l&#39;absence de tête ?](/help/headless/what-is-headless.md)
* Présentation des différents environnements dans l’AEM [Architecture](/help/headless/deployment/architecture.md)

## Configuration {#setup}

Pour configurer AEM GraphQL en toute sécurité en vue de l’utiliser avec les fragments de contenu et vos applications, vous devez configurer divers composants.

### Création de points de terminaison GraphQL (y compris la sécurité) {#graphql-endpoint-creation}

Le point d’entrée est le chemin utilisé pour accéder à GraphQL pour AEM. Ces points de terminaison doivent être créés et publiés afin qu’ils soient accessibles en toute sécurité.

#### Détails {#details-graphql-endpoint-creation}

[Gérer les points d’entrée GraphQL dans AEM](/help/headless/graphql-api/graphql-endpoint.md)

#### Environnements {#environments-graphql-endpoint-creation}

Les points de fin doivent être configurés dans :

* Création
* Prévisualisation
* Publier

Pour :

* Développement
* Tests
* Production

### Mise en cache d’AEM Dispatcher {#dispatcher-caching}

>[!NOTE]
>Si la mise en cache dans Dispatcher est activée, la [configuration CORS](#cors-setup) n’est pas nécessaire et peut donc être ignorée.

La mise en cache des requêtes persistantes n’est pas activée par défaut dans Dispatcher. L’activation par défaut n’est pas possible, car les clients ou clientes qui utilisent le partage de ressources entre origines multiples (CORS) doivent examiner et éventuellement mettre à jour la configuration de Dispatcher.

#### Détails {#details-dispatcher-caching}

[Requêtes persistantes GraphQL - Activation de la mise en cache dans Dispatcher](/help/headless/deployment/dispatcher-caching.md)

#### Environnements {#environments-dispatcher-caching}

Dispatcher est généralement configuré pour :

* Publish : production

### Configuration CORS {#cors-setup}

>[!NOTE]
>Si la mise en cache dans [Dispatcher](#dispatcher-caching) est activée, la configuration CORS n’est pas nécessaire. Cette section peut donc être ignorée.

Pour accéder au point de terminaison GraphQL, une stratégie CORS doit être configurée et ajoutée à un projet AEM déployé sur AEM via Cloud Manager. Vous devez pour cela ajouter un fichier de configuration CORS OSGi approprié pour le ou les points d’entrée souhaités.

#### Détails {#details-cors-setup}

[Configuration du partage des ressources cross-origin (CORS)](/help/headless/deployment/cross-origin-resource-sharing.md)

#### Environnements {#environments-cors-setup}

La norme CORS est généralement configurée pour :

* Publish : production

### Authentification {#authentication}

Un cas d’utilisation principal de l’API GraphQL Adobe Experience Manager as a Cloud Service (AEM) pour la diffusion de fragments de contenu consiste à accepter les requêtes distantes provenant d’applications ou de services tiers. Ces requêtes à distance peuvent nécessiter un accès authentifié à l’API afin de sécuriser la diffusion de contenu découplé.

#### Détails {#details-authentication}

[Authentification pour les requêtes AEM GraphQL distantes sur les fragments de contenu](/help/headless/security/authentication.md)

#### Environnements {#environments-authentication}

L’authentification est généralement configurée pour :

* Prévisualisation
* Publier

Pour :

* Développement
* Tests
* Production

### Autorisations {#permissions}

Avec une mise en œuvre sans interface, plusieurs domaines de sécurité et d’autorisations doivent être pris en compte. Les autorisations et les personnages peuvent être considérés de la même manière pour l’environnement AEM de **Création** ou de **Publication**. Chaque environnement contient des personnages différents et a des besoins différents.

#### Détails {#details-permissions}

[Considérations relatives aux autorisations pour le contenu découplé](/help/headless/security/permissions.md)

#### Environnements {#environments-permissions}

Les autorisations sont généralement configurées pour :

* Création
* Prévisualisation
* Publier

Pour :

* Développement
* Tests
* Production

### Utiliser un réseau de diffusion de contenu (CDN) {#cdn}

Les requêtes GraphQL et leurs réponses JSON peuvent être mises en cache si elles sont ciblées comme requêtes `GET` lors de l’utilisation d’un réseau CDN. En revanche, les requêtes non mises en cache peuvent être très coûteuses (en ressources) et lentes à traiter, avec des effets potentiellement néfastes supplémentaires sur les ressources de l’origine.

#### Détails {#details-cdn}

[Réseau CDN dans AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md)

#### Environnements {#environments-cdn}

Un réseau de diffusion de contenu est généralement configuré pour :

* Publish : production

### Configuration et création de fragments de contenu {#cconfigure-create-content-fragments}

AEM GraphQL est utilisé pour récupérer des informations de vos fragments de contenu. Ils doivent être configurés, puis une structure et un emplacement définis, avant de pouvoir créer le contenu.

#### Détails {#details-content-fragments}

* [Création d’une configuration](/help/headless/setup/create-configuration.md)
* [Création d’un modèle de fragment de contenu](/help/headless/setup/create-content-model.md)
* [Création d’un dossier Assets](/help/headless/setup/create-assets-folder.md)
* [Créer et modifier vos fragments de contenu](/help/headless/setup/create-content-fragment.md)

#### Environnements {#eenvironments-content-fragments}

Les fragments de contenu sont définis, créés, testés, publiés et accessibles sur :

* Création
* Prévisualisation
* Publier

Pour :

* Développement
* Tests
* Production

## Utilisation d’AEM GraphQL {#use-aem-graphql}

### Optimisation des requêtes GraphQL {#optimize-graphql-queries}

Ces instructions sont fournies pour vous aider à éviter les problèmes de performances liés à vos requêtes GraphQL.

#### Détails {#details-optimize-graphql-queries}

[Optimisation des requêtes GraphQL](/help/headless/graphql-api/graphql-optimization.md)

>[!NOTE]
>
>Les instructions d’optimisation couvrent la configuration du cache, déjà traitée dans [Configuration](#setup).

### Accès à GraphQL à partir de vos applications {#access-graphql-from-your-apps}

AEM CMS sans interface donne aux développeurs la liberté de créer et de proposer des expériences exceptionnelles en utilisant les langages, les structures et les outils qu’ils connaissent déjà.

#### Détails {#details-your-apps}

* [ Installez et utilisez le SDK AEM pour le développement ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html?lang=fr)
* [AEM Ressources du développeur sans tête](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=fr)
* Exemples : [React](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/react-app.html?lang=fr), [Next.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/next-js.html?lang=fr), [Node.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/server-to-server-app.html?lang=fr), etc.

#### Environnements {#environments-your-apps}

Les applications sont généralement développées, testées et utilisées sur :

* Prévisualisation
* Publier

Pour :

* Développement
* Tests
* Production

### Ressources supplémentaires

Pour plus d’informations sur AEM GraphQL et les fragments de contenu, voir :

* [API AEM GraphQL pour l’utilisation des fragments de contenu](/help/headless/graphql-api/content-fragments.md)
* [Utilisation de l’IDE GraphiQL](/help/headless/graphql-api/graphiql-ide.md)
* [AEM Ressources du développeur sans tête](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=fr)
