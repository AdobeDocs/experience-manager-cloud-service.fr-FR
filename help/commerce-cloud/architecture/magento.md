---
title: Intégration d’AEM et de Magento à l’aide de Commerce Integration Framework
description: AEM et Magento sont intégrés de manière transparente à l’aide de Commerce Integration Framework (CIF). Le CIF permet à AEM d’accéder à une instance de Magento et de communiquer avec Magento via GraphQL. Il permet également aux auteurs AEM d’utiliser les sélecteurs de produit et de catégorie, ainsi que la console de produits pour parcourir les données de produit et de catégorie récupérées à la demande à partir de Magento. En outre, le CIF offre une vitrine prête à l’emploi qui peut accélérer les projets commerciaux.
thumbnail: aem-magento-architecture.jpg
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 88%

---


# Intégration d’AEM et de Magento à l’aide de Commerce Integration Framework {#aem-magento-framework}

AEM et Magento sont intégrés de manière transparente à l’aide de Commerce Integration Framework (CIF). Le CIF permet à AEM d’accéder à une instance de Magento et de communiquer avec Magento via GraphQL. Il permet également aux auteurs AEM d’utiliser les sélecteurs de produit et de catégorie, ainsi que la console de produits pour parcourir les données de produit et de catégorie récupérées à la demande à partir de Magento. En outre, le CIF offre une vitrine prête à l’emploi qui peut accélérer les projets commerciaux.

>[!NOTE]
>
>GraphQL est actuellement utilisé comme Cloud Service dans deux scénarios (distincts) à Adobe Experience Manager (AEM) :
>
>* AEM Commerce utilise les données d&#39;une plateforme commerciale via GraphQL.
>* [AEM Fragments de contenu fonctionnent conjointement avec l’API AEM GraphQL (une implémentation personnalisée, basée sur GraphQL standard), pour fournir du contenu structuré à utiliser dans vos applications](/help/assets/content-fragments/graphql-api-content-fragments.md).


## Aperçu de l’architecture {#overview}

L’architecture globale est la suivante :

![Aperçu de l’architecture du CIF](../assets/AEM_Magento_Architecture.JPG)

Le CIF s’appuie sur la prise en charge de GraphQL. Le principal canal de communication entre AEM et Magento réside dans l’[API GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/) de Magento. Il existe différentes manières de configurer la communication entre AEM as a Cloud Service et Magento. Pour plus d’informations, reportez-vous à [Prise en main](../getting-started.md).

Le CIF prend en charge les schémas de communication côté serveur et côté client.
Les appels d’API côté serveur sont mis en œuvre à l’aide du [client GraphQL](https://github.com/adobe/commerce-cif-graphql-client) générique intégré, en combinaison avec un [ensemble de modèles de données générés](https://github.com/adobe/commerce-cif-magento-graphql) pour le schéma GraphQL Magento. De plus, toute requête GraphQL ou mutation au format GQL peut être utilisée.

Pour les composants côté client, qui sont créés à l’aide de [React](https://reactjs.org/), le [client Apollo](https://www.apollographql.com/docs/react/) est utilisé.

## Architecture des composants principaux AEM CIF {#cif-core-components}

![Architecture des composants principaux AEM CIF](../assets/cif-component-architecture.jpg)

Les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) suivent des modèles de conception et des bonnes pratiques très similaires à ceux des [composants principaux AEM WCM](https://github.com/adobe/aem-core-wcm-components).

La logique commerciale et la communication d’arrière-plan avec Magento pour les composants principaux AEM CIF sont mises en œuvre dans les modèles Sling. Au cas où il est nécessaire de personnaliser cette logique pour répondre aux exigences spécifiques du projet, le modèle de délégation des modèles Sling peut être utilisé.

>[!TIP]
>
>La page [Personnalisation des composants principaux AEM CIF](../customizing/customize-cif-components.md) contient un exemple détaillé et des bonnes pratiques sur la personnalisation des composants principaux du CIF.

Dans les projets, les composants principaux AEM CIF et les composants de projet personnalisés peuvent facilement récupérer le client configuré pour un magasin Magento associé à une page AEM via la configuration tenant compte du contexte Sling.
