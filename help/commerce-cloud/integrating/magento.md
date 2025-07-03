---
title: Intégration d’AEM et d’Adobe Commerce à l’aide de Commerce Integration Framework
description: AEM et Adobe Commerce sont intégrés de manière transparente à l’aide de Commerce Integration Framework (CIF). CIF permet à AEM d’accéder à une instance Adobe Commerce et de communiquer avec Adobe Commerce via GraphQL. Il permet également aux auteurs AEM d’utiliser les sélecteurs de produit et de catégorie, ainsi que la console de produits pour parcourir les données de produit et de catégorie récupérées à la demande à partir d’Adobe Commerce. En outre, le CIF offre une vitrine prête à l’emploi qui peut accélérer les projets commerciaux.
thumbnail: aem-magento-architecture.jpg
exl-id: 110ceef5-2c35-4b81-8e89-26929c0da91b
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 87%

---

# Intégration d’AEM et d’Adobe Commerce à l’aide de Commerce Integration Framework {#aem-framework}

Experience Manager et Adobe Commerce sont intégrés de manière transparente à l’aide de Commerce Integration Framework (CIF). CIF permet à AEM d’accéder directement à l’instance de Commerce et de communiquer avec cette dernière à l’aide des [API GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/) d’Adobe Commerce.

>[!NOTE]
>
> La version minimale de l’API GraphQL prise en charge est la version 2.3.5. Certaines fonctionnalités ne sont prises en charge que dans les versions plus récentes ou uniquement dans l’édition Adobe Commerce.

>[!NOTE]
>
>GraphQL est actuellement utilisé dans deux scénarios (distincts) dans Adobe Experience Manager (AEM) as a Cloud Service :
>
>* Ce scénario, dans lequel CIF communique avec l’instance commerce par le biais de GraphQL.
>* [AEM Content Fragments de contenu fonctionnent conjointement avec l’API AEM GraphQL (une implémentation personnalisée, basée sur GraphQL standard) pour fournir un contenu structuré à utiliser dans vos applications](/help/headless/graphql-api/content-fragments.md).

## Aperçu de l’architecture {#overview}

L’architecture globale est la suivante :

![Aperçu de l’architecture du CIF](../assets/AEM_Magento_Architecture.png)

CIF prend en charge les modèles de communication côté serveur et côté client.
Les appels d’API côté serveur sont implémentés à l’aide du [client GraphQL](https://github.com/adobe/commerce-cif-graphql-client) générique intégré, en combinaison avec un [ensemble de modèles de données générés](https://github.com/adobe/commerce-cif-magento-graphql) pour le schéma GraphQL de Commerce. En outre, toute requête ou mutation GraphQL au format GQL peut être utilisée.

Pour les composants côté client, qui sont créés à l’aide de [React](https://reactjs.org/), le [client Apollo](https://www.apollographql.com/docs/react/) est utilisé.

## Architecture des composants principaux AEM CIF {#cif-core-components}

![Architecture des composants principaux AEM CIF](../assets/cif-component-architecture.jpg)

Les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) suivent des modèles de conception et des bonnes pratiques très similaires à ceux des [composants principaux AEM WCM](https://github.com/adobe/aem-core-wcm-components).

La logique commerciale et la communication d’arrière-plan avec Adobe Commerce pour les composants principaux AEM CIF sont mises en œuvre dans les modèles Sling. Au cas où il est nécessaire de personnaliser cette logique pour répondre aux exigences spécifiques du projet, le modèle de délégation des modèles Sling peut être utilisé.

>[!TIP]
>
>La page [Personnalisation des composants principaux AEM CIF](../customizing/customize-cif-components.md) contient un exemple détaillé et des bonnes pratiques sur la personnalisation des composants principaux du CIF.

Dans les projets, les composants principaux AEM CIF et les composants de projet personnalisés peuvent facilement récupérer le client configuré pour un magasin Adobe Commerce lié à une page AEM via la configuration tenant compte du contexte Sling.

## Recherche {#search}

CIF fournit un [composant principal de recherche](https://www.aemcomponents.dev/content/core-components-examples/library/commerce/search.html) prêt à l’emploi qui est une expérience de recherche générée côté serveur basée sur [l’API Commerce GraphQL](https://developer.adobe.com/commerce/webapi/graphql/). Les clients Commerce ont la possibilité d’utiliser [recherche en direct](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/guide-overview.html?lang=fr) à la place. Suivez ce [lien](/help/commerce-cloud/integrating/live-search-plp.md) pour en savoir plus sur l’intégration CIF - Live Search.

