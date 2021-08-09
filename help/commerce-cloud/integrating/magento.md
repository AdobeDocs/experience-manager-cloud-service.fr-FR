---
title: Intégration d’AEM et de Adobe Commerce (Magento) à l’aide de Commerce Integration Framework
description: AEM et Adobe Commerce (Magento) sont intégrés de manière transparente à l’aide de Commerce Integration Framework (CIF). Le CIF permet à AEM d’accéder à une instance de Magento et de communiquer avec Magento via GraphQL. Il permet également aux auteurs AEM d’utiliser les sélecteurs de produit et de catégorie, ainsi que la console de produits pour parcourir les données de produit et de catégorie récupérées à la demande à partir de Magento. En outre, le CIF offre une vitrine prête à l’emploi qui peut accélérer les projets commerciaux.
thumbnail: aem-magento-architecture.jpg
exl-id: 110ceef5-2c35-4b81-8e89-26929c0da91b,1cdfda88-a728-432f-b24a-f81347572bcf
source-git-commit: ef4abc74b90da80bfe556306f8ac93078b4958c7
workflow-type: ht
source-wordcount: '392'
ht-degree: 100%

---

# Intégration d’AEM et d’Adobe Commerce (Magento) à l’aide de Commerce Integration Framework {#aem-magento-framework}

Les composants Experience Manager et Adobe Commerce (Magento) sont intégrés de manière transparente à l’aide de Commerce Integration Framework (CIF). CIF permet à AEM d’accéder directement à l’instance de commerce et de communiquer avec cette dernière à l’aide des [API GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/) d’Adobe Commerce.

>[!NOTE]
>
>GraphQL est actuellement utilisé dans deux scénarios (distincts) dans Adobe Experience Manager (AEM) as a Cloud Service :
>
>* Ce scénario, dans lequel CIF communique avec l’instance commerce par le biais de GraphQL.
>* [AEM Content Fragments de contenu fonctionnent conjointement avec l’API AEM GraphQL (une implémentation personnalisée, basée sur GraphQL standard) pour fournir un contenu structuré à utiliser dans vos applications](/help/assets/content-fragments/graphql-api-content-fragments.md).


## Aperçu de l’architecture {#overview}

L’architecture globale est la suivante :

![Aperçu de l’architecture du CIF](../assets/AEM_Magento_Architecture.png)

Le CIF prend en charge les schémas de communication côté serveur et côté client.
Les appels d’API côté serveur sont implémentés à l’aide du [client GraphQL](https://github.com/adobe/commerce-cif-graphql-client) générique intégré, associé à un [jeu de modèles de données générés](https://github.com/adobe/commerce-cif-magento-graphql) pour le schéma GraphQL de commerce. De plus, toute requête GraphQL ou mutation au format GQL peut être utilisée.

Pour les composants côté client, qui sont créés à l’aide de [React](https://reactjs.org/), le [client Apollo](https://www.apollographql.com/docs/react/) est utilisé.

## Architecture des composants principaux AEM CIF {#cif-core-components}

![Architecture des composants principaux AEM CIF](../assets/cif-component-architecture.jpg)

Les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) suivent des modèles de conception et des bonnes pratiques très similaires à ceux des [composants principaux AEM WCM](https://github.com/adobe/aem-core-wcm-components).

La logique commerciale et la communication d’arrière-plan avec Adobe Commerce pour les composants principaux AEM CIF sont mises en œuvre dans les modèles Sling. Au cas où il est nécessaire de personnaliser cette logique pour répondre aux exigences spécifiques du projet, le modèle de délégation des modèles Sling peut être utilisé.

>[!TIP]
>
>La page [Personnalisation des composants principaux AEM CIF](../customizing/customize-cif-components.md) contient un exemple détaillé et des bonnes pratiques sur la personnalisation des composants principaux du CIF.

Dans les projets, les composants principaux AEM CIF et les composants de projet personnalisés peuvent facilement récupérer le client configuré pour un magasin Adobe Commerce lié à une page AEM via la configuration tenant compte du contexte Sling.
