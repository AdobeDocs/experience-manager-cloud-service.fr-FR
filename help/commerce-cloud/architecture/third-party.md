---
title: Intégration commerciale AEM et tierce à l’aide du cadre d’intégration commerciale
description: Les entreprises peuvent avoir besoin de solutions commerciales tierces supplémentaires pour alimenter leur vitrine. Le cadre d'intégration commerciale (CIF) peut être utilisé dans de tels scénarios d'intégration pour connecter une solution commerciale tierce à Adobe Experience Manager à l'aide de l'exécution E/S.
thumbnail: cif-third-party-architecture.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 1%

---


# Intégration commerciale AEM et tierce à l’aide du cadre d’intégration commerciale {#aem-third-party}

Les entreprises peuvent avoir besoin de solutions commerciales tierces supplémentaires pour alimenter leur vitrine. Le cadre d&#39;intégration commerciale (CIF) peut être utilisé dans de tels scénarios d&#39;intégration où, outre le Magento, une solution commerciale tierce doit également être intégrée à AEM. CIF fournit des éléments tels qu&#39;une vitrine de référence d&#39;accélérateur, des composants principaux AEM CIF et des outils de création qui fonctionnent avec des Magento prêts à l&#39;emploi. Pour intégrer AEM et une solution de commerce tierce et réutiliser ces éléments CIF, il faut développer davantage.

## Architecture {#architecture}

L&#39;architecture générale est la suivante :

![Présentation de l&#39;architecture non Magento/tierce AEM](/help/commerce-cloud/assets/AEM_nonMagento_Architecture.JPG)

La principale différence entre l’architecture d’intégration pour AEM - Magento et AEM - commerce tiers est l’ajout d’une couche d’intégration et de transformation des données, comme illustré dans l’illustration ci-dessus. La couche d’intégration doit être hébergée sur la plateforme Adobe I/O Runtime, qui est la plateforme sans serveur du Adobe. Vous pouvez en savoir plus sur Adobe I/O Runtime [ici](https://www.adobe.io/apis/experienceplatform/runtime.html).

Cette couche d’intégration a pour but de mapper une API non Magento ou tierce avec des API de commerce d’Adobe (API GraphQL Magento). Cette mise en correspondance permet aux composants [principaux](https://github.com/adobe/aem-core-cif-components) AEM CIF et aux outils de création CIF de récupérer les données de la solution non Magento. Avec cette approche, la couche d’intégration encapsule la logique d’intégration et crée une séparation des préoccupations entre AEM et la solution tierce. Cela permet l&#39;utilisation des éléments CIF de manière indépendante avec différentes solutions tierces. Les avantages de l&#39;utilisation d&#39;éléments CIF dans votre projet ont été décrits dans l&#39; [Introduction](/help/commerce-cloud/overview.md).

## Développement d’une intégration {#develop-integration}

Pour vous aider à commencer à créer la couche d’intégration requise pour intégrer une solution tierce ou non Magento avec AEM, nous avons créé une implémentation [de](https://github.com/adobe/commerce-cif-graphql-integration-reference) référence pour le démontrer. Cette référence peut servir de point de départ à votre projet.
