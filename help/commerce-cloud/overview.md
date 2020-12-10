---
title: Présentation d’AEM Commerce as a Cloud Service
description: Experience Manager Commerce as a Cloud Service est constitué de Commerce Integration Framework (CIF), qui est le modèle recommandé par Adobe pour intégrer et étendre les services commerciaux à partir de Magento et d’autres solutions commerciales tierces avec Experience Cloud.
thumbnail: introducing-aem-commerce.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '1357'
ht-degree: 100%

---


# Présentation d’AEM Commerce as a Cloud Service {#commerce-intro}

Experience Manager Commerce as a Cloud Service est constitué de Commerce Integration Framework (CIF), qui est le modèle recommandé par Adobe pour intégrer et étendre les services commerciaux à partir de Magento et d’autres solutions commerciales tierces avec Experience Cloud. Les clients d’Adobe peuvent ainsi offrir une expérience d’achat omnicanal personnalisée extraordinaire reposant sur une technologie de pointe.

Commerce Integration Framework est un module complémentaire d’Experience Manager as a Cloud Service qui fournit un ensemble d’outils de création, des composants et un storefront de référence afin d’accélérer le développement d’intégrations entre Experience Manager as a Cloud Service et les solutions commerciales.

## Avantages de CIF {#cif-benefits}

Les avantages principaux sont les suivants :

* L’intégration est une couche d’abstraction pour normaliser et encapsuler les intégrations avec plusieurs systèmes.

* CIF prend en charge les expériences sans interface/omnicanal :

   * Applications sur une seule page et applications de plusieurs pages
   * Points d’entrée GraphQL

* CIF fournit une couche de logique commerciale et de processus reposant sur un microservice et sans serveur pour la personnalisation et l’extension des services commerciaux.

* CIF fournit des intégrations prêtes à l’emploi avec des solutions Adobe telles que AEM et Magento.

## Éléments CIF {#cif-elements}

![Éléments CIF](/help/commerce-cloud/assets/cif-overview1.jpg)


### Module complémentaire CIF pour les outils de création {#add-on-authoring-tools}

Le module complémentaire CIF permet d’accéder à des outils de création commerciaux (par exemple, la console de produits, les sélecteurs de produits et de catégories ou la recherche de produits) qui apportent aux auteurs les moyens de créer des expériences riches avec du contenu marketing et commercial. Le module complémentaire gère également la connexion de serveur principal à Magento (ou un système commercial alternatif) via GraphQL. Une fois le module complémentaire mis en service, il est automatiquement déployé sur les environnements AEM as a Cloud Service.

### Composants principaux AEM CIF {#aem-cif-core}

Les composants principaux AEM CIF sont des composants rendus côté serveur et côté client avec la prise en charge de Magento GraphQL. Ils sont utilisés pour créer des vitrines commerciales statiques, pouvant être mises en cache et compatibles avec l’optimisation du moteur de recherche basées sur les technologies AEM.

Les composants de base fournis sont communs aux implémentations commerciales (par exemple, Détail de produit, Liste de produits, Navigation, Recherche, etc.). Ils peuvent être utilisés en l’état ou étendus.

Les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) fonctionnent comme les [composants principaux AEM Sites](https://github.com/adobe/aem-core-wcm-components), mais sont dédiés à des cas d’utilisation spécifiques au commerce.

Les principaux avantages de ces composants sont les suivants :

* Ils sont faciles à utiliser dans vos projets.
* Ils peuvent être utilisés en l’état ou avec des modifications très minimes.
* Ils fournissent les bonnes pratiques de connexion à Magento via les API GraphQL ou REST.

Des composants tels que Teaser de produit et Carrousel de produit sont fournis pour permettre aux auteurs AEM de créer des pages Experience dans AEM, en combinant du contenu marketing et commercial. Vous pouvez facilement faire glisser et déposer ces composants sur une page de contenu créée dans AEM et les relier à des produits ou à des catégories spécifiques à l’aide des outils de création CIF tels que le sélecteur de produits ou de catégories dans Cloud Service.

Tous les composants sont Open Source sur [GitHub](https://github.com/adobe/aem-core-cif-components). Cela apporte une transparence totale au niveau des modifications à venir et vous permet d’obtenir la dernière version très facilement. Vous pouvez également fournir des requêtes d’extraction en vue d’améliorations et de correctifs qui peuvent être incorporées.

### AEM Venia Storefront {#aem-venia-storefront}

[AEM Venia Storefront](https://github.com/adobe/aem-cif-guides-venia) est un storefront de référence moderne prêt pour la production et présentant un parcours commercial B2C de base. Il peut être utilisé pour lancer des projets commerciaux et accélérer des projets à l’aide d’AEM, de CIF et de Magento. Il présente les bonnes pratiques d’intégration d’AEM et de Magento, indique comment utiliser les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) et les [composants principaux AEM Sites](https://github.com/adobe/aem-core-wcm-components) et prend en charge les points d’entrée GraphQL Adobe Commerce. Il assure également des ventes anticipées avec un site de référence pour démontrer l’intégration entre AEM et Magento.

AEM Venia Storefront est une application de pages mixtes dans laquelle AEM gère la vitrine et Magento alimente le serveur principal Commerce sans interface. Les rendus côtés serveur et client sont utilisés dans le storefront. Le rendu côté serveur est utilisé pour diffuser du contenu statique et le rendu côté client pour diffuser du contenu dynamique.

Les pages de produits et de catalogues sont relativement statiques et sont rendues côté serveur à l’aide de composants principaux AEM CIF tels que Détail de produit et Liste de produits sur les modèles génériques créés dans AEM. Ces composants obtiennent des données de Magento via les API GraphQL.
Ces pages sont créées dynamiquement, rendues sur le serveur, mises en cache dans le Dispatcher AEM, puis fournies au navigateur.
Pour les attributs plus dynamiques tels que le stock ou le prix, en revanche, les composants côté client sont utilisés. Les composants côté client ou les composants web récupèrent directement les données de Magento via les API GraphQL et le contenu est alors rendu dans le navigateur.

#### Passage en caisse {#checkout}

Ce storefront de référence utilise le composant Panier côté client qui effectue le rendu du panier et du formulaire de passage en caisse pour démontrer un modèle d’intégration d’expérience complète qui vous permet de diffuser des expériences commerciales avec Magento s’exécutant intégralement sans serveur et AEM gérant la vitrine. Il est recommandé d’utiliser les méthodes de paiement abstraites fournies. Le client du navigateur est ainsi en communication directe avec le fournisseur de passerelle de paiement, de sorte que ni les clouds Adobe ni les clouds Magento ne contiennent ni ne transmettent de données sensibles PCI.

#### Gestion de compte {#account-management}

La gestion de compte est réalisée par Magento et le storefront de référence utilise des composants React côté client afin de permettre à AEM de rendre l’expérience pour les fonctionnalités suivantes : Créer un compte, Se connecter et Mot de passe oublié.

Le projet AEM Venia Storefront est un projet open source ; pour plus de détails, voir [AEM Venia Storefront](https://github.com/adobe/aem-cif-guides-venia).

### Archétype de projet AEM {#aem-project-archtype}

L’[archétype de projet AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/developing/archetype/overview.html) peut être utilisé pour créer un projet Adobe Experience Manager minimal basé sur les bonnes pratiques comme point de départ de vos propres projets AEM. Le cas échéant, l’[archétype de projet AEM](https://github.com/adobe/aem-core-cif-components) peut être inclus dans un nouveau projet généré.

### Couche d’extension CIF {#cif-extension}

La couche d’extension CIF est une couche intermédiaire qui héberge la logique commerciale complexe. Elle s’exécute sur la plate-forme Adobe I/O Runtime, qui est la plate-forme sans serveur d’Adobe. Cette plate-forme vous permet d’étendre les appels de service de bout en bout en injectant une logique commerciale et de processus à un niveau de microservice. La logique commerciale consiste par exemple à utiliser l’emplacement et le canal pour déterminer une stratégie d’inventaire. La logique de processus consiste par exemple à récupérer des informations personnalisées.

### Couche d’intégration CIF {#cif-integration-layer}

La couche d’intégration CIF est utilisée pour normaliser les intégrations avec d’autres solutions commerciales. Elle s’exécute sur la plate-forme Adobe I/O Runtime, qui est la plate-forme sans serveur d’Adobe, et permet les intégrations au niveau des microservices en mappant les API tierces sur les API Adobe Commerce. Pour vous aider à commencer à créer des intégrations tierces avec AEM, nous avons créé une [implémentation de référence](https://github.com/adobe/commerce-cif-graphql-integration-reference) afin de démontrer comment un serveur principal Commerce non Magento peut être intégré via les API Adobe Commerce (API Magento GraphQL).

## Modèles d’intégration AEM Commerce {#aem-commerce-integration}

Certains des modèles d’intégration AEM Commerce couramment mis en œuvre sont présentés ci-dessous.

![Modèles d’intégration AEM CIF](/help/commerce-cloud/assets/aem-cif-integration-patterns-updated.JPG)


### Modèle d’intégration 1 {#integration-pattern-one}

Il s’agit de notre modèle d’intégration recommandé dans lequel AEM gère la totalité de la vitrine et intègre les services commerciaux via les API Adobe Commerce GraphQL. Ce modèle confère à AEM une flexibilité totale permettant de personnaliser des conceptions de site multimédia sophistiquées sur les appareils. Ce modèle d’intégration est pris en charge par CIF en tant que solution prête à l’emploi.


### Modèle d’intégration 2 {#integration-pattern-two}

Ce modèle illustre une manière intégralement sans serveur de diffuser du contenu et des transactions commerciales. La diffusion s’effectue entièrement côté client. Dans ce modèle, le contenu est diffusé via API et HTML et les données commerciales sont fournies via GraphQL. Ce modèle n’est actuellement pas pris en charge par CIF prêt à l’emploi.


### Modèle d’intégration 3 {#integration-pattern-three}

Dans ce schéma, Magento gère la vitrine et incorpore le contenu créé AEM. Le contenu créé AEM peut être diffusé par le biais de fragments d’expérience ou de fragments de contenu. Ce modèle d’intégration exige un travail spécifique à un projet et ne peut pas être mis en œuvre clé en main avec CIF.


### Modèle d’intégration 4 {#integration-pattern-four}

Il s’agit d’un modèle d’intégration courant dans lequel la vitrine, ou la couche de présentation, est divisée entre AEM et une solution Commerce. En général, la solution Commerce diffuse les pages non marketing (par exemple, passage en caisse et mon compte) et AEM diffuse les pages marketing et l’expérience de catalogue de storefront. Dans ce modèle, vous devez vous assurer que les paniers et les sessions utilisateur sont gérés correctement entre les deux systèmes afin d’éviter une expérience utilisateur discontinue. Par exemple, Magento stocke le panier et la session utilisateur dans un cookie, qui peut être partagé entre AEM et Magento. Ce modèle exige un travail spécifique à un projet et ne peut pas être mis en œuvre clé en main avec CIF.
