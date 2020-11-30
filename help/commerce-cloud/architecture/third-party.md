---
title: Intégration d’AEM et de solutions commerciales tierces à l’aide de Commerce Integration Framework
description: Les entreprises peuvent avoir besoin de solutions commerciales tierces supplémentaires pour alimenter leur vitrine. Le cadre d'intégration commerciale (CIF) peut être utilisé dans de tels scénarios d'intégration pour connecter une solution commerciale tierce à Adobe Experience Manager à l'aide de l'exécution E/S.
thumbnail: cif-third-party-architecture.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 92%

---


# Intégration d’AEM et de solutions commerciales tierces à l’aide de Commerce Integration Framework {#aem-third-party}

Les entreprises peuvent avoir besoin de solutions commerciales tierces supplémentaires pour alimenter leur vitrine. Il est possible d’utiliser Commerce Integration Framework (CIF) dans des scénarios d’intégration de ce type dans lesquels, outre Magento, la solution commerciale tierce doit également être intégrée avec AEM. CIF fournit un certain nombre d’éléments comme une vitrine de référence d’accélérateur, des composants principaux AEM CIF et des outils de création prêts à l’emploi en association avec Magento. Pour intégrer AEM et une solution de commerce tierce et réutiliser ces éléments CIF, d’autres développements sont nécessaires.

## Architecture {#architecture}

L’architecture globale se présente comme suit :

![Présentation de l’architecture d’AEM non Magento/solutions tierces](/help/commerce-cloud/assets/AEM_nonMagento_Architecture.JPG)

La principale différence entre l’architecture d’intégration pour AEM avec Magento, et AEM avec des solutions de commerce tierces, est l’ajout d’une couche d’intégration et de transformation des données, représentée dans l’illustration ci-dessus. La couche d’intégration doit être hébergée sur la plateforme Adobe I/O Runtime, qui est la plateforme sans serveur d’Adobe. Pour en savoir plus à propos d’Adobe I/O Runtime, voir [ici](https://www.adobe.io/apis/experienceplatform/runtime.html).

Cette couche d’intégration a pour but de mapper une API non Magento ou tierce avec des API de commerce d’Adobe (API GraphQL Magento). Ce mappage permet aux [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) et aux outils de création CIF de récupérer les données de la solution non Magento. Dans cette approche, la couche d’intégration encapsule la logique d’intégration et crée une séparation des responsabilités entre AEM et la solution tierce. Cette démarche permet l’utilisation des éléments CIF de manière indépendante avec différentes solutions tierces. Les avantages de l’utilisation d’éléments CIF dans votre projet ont été décrits dans l’[Introduction](/help/commerce-cloud/overview.md).

## Développement d’une intégration {#develop-integration}

Pour vous aider à prendre en main la création de la couche d’intégration requise pour intégrer une solution tierce ou non Magento avec AEM, nous avons créé une [implémentation de référence](https://github.com/adobe/commerce-cif-graphql-integration-reference) à des fins de démonstration. Cette référence peut servir de point de départ pour votre projet.
