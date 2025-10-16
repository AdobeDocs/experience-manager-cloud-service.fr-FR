---
title: Bonnes pratiques pour la configuration et l’utilisation d’AEM GraphQL avec des fragments de contenu
description: Découvrez les bonnes pratiques recommandées pour la configuration et l’utilisation d’AEM GraphQL avec les fragments de contenu.
exl-id: 4d6a5aaa-c8be-4858-ad07-085dc4fb77e7
feature: Headless
role: Admin, Developer
source-git-commit: 38a4bf89e099432163163e90e08aa0f47407724f
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 40%

---

# Bonnes pratiques pour la configuration et l’utilisation d’AEM GraphQL avec des fragments de contenu{#best-practices-setup-use-aem-graphql-content-fragments}

Ces instructions résument les bonnes pratiques recommandées pour installer, configurer et utiliser AEM avec GraphQL et les fragments de contenu.

## Prise en main {#getting-started}

Pour vous aider à vous mettre à jour rapidement :

* [Qu’est-ce que le mode découplé ?](/help/headless/what-is-headless.md)
* Présentation des différents environnements d’AEM [ Architecture ](/help/headless/deployment/architecture.md)

## Configuration {#setup}

Pour configurer AEM GraphQL en toute sécurité afin de l’utiliser avec des fragments de contenu et vos applications, vous devez configurer divers composants.

### Création d’un point d’entrée GraphQL (sécurité incluse) {#graphql-endpoint-creation}

Le point d’entrée est le chemin utilisé pour accéder à GraphQL pour AEM. Ces points d’entrée doivent être créés et publiés afin d’être accessibles en toute sécurité.

#### Détails {#details-graphql-endpoint-creation}

[Gérer les points d’entrée GraphQL dans AEM](/help/headless/graphql-api/graphql-endpoint.md)

#### Environnements {#environments-graphql-endpoint-creation}

Les points d’entrée doivent être configurés dans :

* Création
* Prévisualisation
* Publication

Pour :

* Développement
* Tests
* Production

### Mise en cache d’AEM Dispatcher {#dispatcher-caching}

>[!NOTE]
>Si la mise en cache dans le Dispatcher est activée[ la configuration ](#cors-setup) CORS n’est pas nécessaire et peut donc être ignorée.

La mise en cache des requêtes persistantes n’est pas activée par défaut dans Dispatcher. L’activation par défaut n’est pas possible, car les clients ou clientes qui utilisent le partage de ressources entre origines multiples (CORS) doivent examiner et éventuellement mettre à jour la configuration de Dispatcher.

#### Détails {#details-dispatcher-caching}

[Requêtes persistantes GraphQL - Activation de la mise en cache dans Dispatcher](/help/headless/deployment/dispatcher-caching.md)

#### Environnements {#environments-dispatcher-caching}

Le Dispatcher est généralement configuré pour :

* Publication : production

### Configuration CORS {#cors-setup}

>[!NOTE]
>Si la mise en cache dans [AEM Dispatcher](#dispatcher-caching) est activée, la configuration CORS n’est pas nécessaire. Cette section peut donc être ignorée.

Pour accéder au point d’entrée GraphQL, une politique CORS doit être configurée et ajoutée à un projet AEM déployé vers AEM via Cloud Manager. Vous devez pour cela ajouter un fichier de configuration CORS OSGi approprié pour le ou les points d’entrée souhaités.

#### Détails {#details-cors-setup}

[Configuration du partage des ressources cross-origin (CORS)](/help/headless/deployment/cross-origin-resource-sharing.md)

#### Environnements {#environments-cors-setup}

La norme CORS est généralement configurée pour :

* Publication : production

### Authentification {#authentication}

Un des principaux cas d’utilisation de l’API GraphQL Adobe Experience Manager as a Cloud Service (AEM) pour la diffusion de fragments de contenu consiste à accepter les requêtes distantes provenant d’applications ou de services tiers. Ces requêtes à distance peuvent nécessiter un accès authentifié à l’API afin de sécuriser la diffusion de contenu découplé.

#### Détails {#details-authentication}

[Authentification pour les requêtes AEM GraphQL distantes sur les fragments de contenu](/help/headless/security/authentication.md)

#### Environnements {#environments-authentication}

L’authentification est généralement configurée pour :

* Prévisualisation
* Publication

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
* Publication

Pour :

* Développement
* Tests
* Production

### Utiliser un réseau de diffusion de contenu (CDN) {#cdn}

Les requêtes GraphQL et leurs réponses JSON peuvent être mises en cache si elles sont ciblées comme requêtes `GET` lors de l’utilisation d’un réseau CDN. En revanche, les requêtes non mises en cache peuvent être très coûteuses (en ressources) et lentes à traiter, avec des effets potentiellement néfastes supplémentaires sur les ressources de l’origine.

#### Détails {#details-cdn}

[Réseau CDN dans AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md)

#### Environnements {#environments-cdn}

Un réseau CDN est généralement configuré pour :

* Publication : production

### Configuration et création de fragments de contenu {#cconfigure-create-content-fragments}

AEM GraphQL est utilisé pour récupérer des informations à partir de vos fragments de contenu. Ils doivent être configurés, puis une structure et un emplacement définis, avant que vous puissiez créer le contenu.

#### Détails {#details-content-fragments}

* [Création d’une configuration](/help/headless/setup/create-configuration.md)
* [Créer un modèle de fragment de contenu](/help/headless/setup/create-content-model.md)
* [Création d’un dossier Assets](/help/headless/setup/create-assets-folder.md)
* [Créer et modifier vos fragments de contenu](/help/headless/setup/create-content-fragment.md)

#### Environnements {#eenvironments-content-fragments}

Les fragments de contenu sont définis, créés, testés, publiés et accessibles sur :

* Création
* Prévisualisation
* Publication

Pour :

* Développement
* Tests
* Production

## Utilisation d’AEM GraphQL {#use-aem-graphql}

### Optimisation de vos requêtes GraphQL {#optimize-graphql-queries}

Ces instructions sont fournies pour vous aider à éviter les problèmes de performances liés à vos requêtes GraphQL.

#### Détails {#details-optimize-graphql-queries}

[Optimisation des requêtes GraphQL](/help/headless/graphql-api/graphql-optimization.md)

>[!NOTE]
>
>Les instructions d’optimisation couvrent la configuration du cache, déjà abordée dans [Configuration](#setup).

### Accès à GraphQL à partir de vos applications {#access-graphql-from-your-apps}

AEM Headless CMS offre aux développeurs la liberté de créer et de diffuser des expériences exceptionnelles à l’aide des langages, des frameworks et des outils qu’ils connaissent déjà.

#### Détails {#details-your-apps}

* [Installer et utiliser AEM SDK pour le développement](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html?lang=fr)
* [Ressources de développement découplées AEM](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=fr)
* Par exemple, [React](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/react-app.html), [Next.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/next-js.html) et [Node.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/server-to-server-app.html).

#### Environnements {#environments-your-apps}

Les applications sont généralement développées, testées et utilisées sur :

* Prévisualisation
* Publication

Pour :

* Développement
* Tests
* Production

### Ressources supplémentaires

Pour plus d’informations sur le GraphQL AEM et les fragments de contenu, voir :

* [API AEM GraphQL pour l’utilisation des fragments de contenu](/help/headless/graphql-api/content-fragments.md)
* [Utilisation de l’IDE GraphiQL](/help/headless/graphql-api/graphiql-ide.md)
* [Ressources de développement découplées AEM](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=fr)
