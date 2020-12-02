---
title: Introduction à AEM Commerce en tant que Cloud Service
description: Le commerce Experience Manager en tant que Cloud Service est constitué du cadre d'intégration commerciale (CIF), qui est le modèle recommandé par le Adobe pour intégrer et étendre les services commerciaux à partir de solutions commerciales Magento et tierces avec l'Experience Cloud.
thumbnail: introducing-aem-commerce.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '1357'
ht-degree: 3%

---


# Introduction du commerce AEM en tant que Cloud Service {#commerce-intro}

Le commerce Experience Manager en tant que Cloud Service est constitué du cadre d&#39;intégration commerciale (CIF), qui est le modèle recommandé par le Adobe pour intégrer et étendre les services commerciaux à partir de solutions commerciales Magento et tierces avec l&#39;Experience Cloud. Cela permet aux clients Adobes d&#39;offrir une expérience d&#39;achat personnalisée et extraordinaire basée sur une technologie de pointe.

Le Commerce Integration Framework est un module complémentaire pour Experience Manager en tant que Cloud Service et fournit un ensemble d&#39;outils de création, de composants et une vitrine de référence pour accélérer le développement d&#39;intégrations entre Experience Manager en tant que Cloud Service et solutions commerciales.

## Avantages du CIF {#cif-benefits}

Les principaux avantages sont les suivants :

* L&#39;intégration est une couche d&#39;abstraction pour normaliser et encapsuler les intégrations avec plusieurs systèmes.

* CIF prend en charge les expériences sans tête/en manichannel :

   * Applications d’une seule page et applications de plusieurs pages
   * Points de terminaison GraphQL

* CIF fournit une couche logique de processus et d&#39;entreprise sans serveur basée sur un microservice pour la personnalisation et l&#39;extension des services de commerce.

* CIF fournit des intégrations prêtes à l&#39;emploi avec des solutions d&#39;Adobe telles que les solutions d&#39;AEM et de Magento

## Eléments CIF {#cif-elements}

![Eléments CIF](/help/commerce-cloud/assets/cif-overview1.jpg)


### Module complémentaire CIF pour les outils de création {#add-on-authoring-tools}

Le module complémentaire CIF permet d’accéder à des outils de création de commerce tels que la console de produits, les sélecteurs de produits et de Catégories ou encore la recherche de produits pour les auteurs afin de leur permettre de créer des expériences enrichissantes en matière de contenu marketing et commercial. Le module complémentaire gère également la connexion principale au Magento (ou système de commerce alternatif) via GraphQL. Une fois le module complémentaire mis en service, il est automatiquement déployé sur AEM en tant qu’environnements Cloud Service.

### aem Composants principaux CIF {#aem-cif-core}

Les composants principaux CIF AEM sont des composants rendus côté serveur et côté client avec la prise en charge de Magento GraphQL. Ils sont utilisés pour créer des magasins de commerce statiques, pouvant être mis en cache et compatibles avec les moteurs de recherche SEO, basés sur les technologies AEM.

Les composants de base sont fournis, communs aux implémentations commerciales telles que les détails du produit, la Liste de produit, la navigation, la recherche, etc. Ils peuvent être utilisés en l&#39;état ou étendus.

Les [AEM composants principaux du FIC](https://github.com/adobe/aem-core-cif-components) fonctionnent comme les [composants principaux de AEM Sites](https://github.com/adobe/aem-core-wcm-components) mais sont dédiés à des cas d&#39;utilisation spécifiques au commerce.

Les principaux avantages de ces éléments sont les suivants :

* Ils sont faciles à utiliser dans vos projets.
* Ils peuvent être utilisés en l&#39;état ou avec des modifications très minimes.
* Ils fournissent les meilleures pratiques de connexion avec les Magento via les API GraphQL ou les API REST.

Des composants tels que Produit Teaser et Carrousel sont fournis pour permettre aux auteurs AEM de créer des pages d’expérience dans AEM, en combinant du contenu marketing et commercial. Ces composants peuvent être facilement glissés et déposés sur une page de contenu créée dans AEM et liée à des produits ou catégories spécifiques à l’aide des outils de création CIF tels que le produit ou le sélecteur de Catégories en Cloud Service.

Tous les composants sont open-source sur [GitHub](https://github.com/adobe/aem-core-cif-components). Cela permet une transparence totale sur les modifications à venir et vous permet d&#39;obtenir la dernière version très facilement. Vous pouvez également fournir des demandes d’extraction pour des améliorations et des correctifs de bogues qui peuvent être incorporés.

### aem Venia Storefront {#aem-venia-storefront}

Le [AEM Venia Storefront](https://github.com/adobe/aem-cif-guides-venia) est une vitrine de référence moderne prête à la production qui présente un parcours commercial B2C de base. Il peut être utilisé pour lancer des projets commerciaux et accélérer des projets à l&#39;aide d&#39;AEM, de CIF et de Magento. Il présente les meilleures pratiques d’intégration des AEM et des Magento et montre comment utiliser les [composants de base ](https://github.com/adobe/aem-core-cif-components)AEM CIF&lt;a1/> et [composants de base AEM Sites](https://github.com/adobe/aem-core-wcm-components) et prend en charge les points de terminaison GraphQL de Adobe Commerce. Il fournit également des ventes anticipées avec un site de référence pour démontrer l&#39;intégration entre AEM et Magento.

L&#39;AEM Venia Storefront est une application de pages mixtes dans laquelle AEM possède le verre et le Magento alimente le commerce sans tête. Le rendu côté serveur et le rendu côté client sont utilisés dans la vitrine. Le rendu côté serveur est utilisé pour diffuser du contenu statique et le rendu côté client est utilisé pour diffuser du contenu dynamique.

Les pages de produit et de catalogue sont relativement statiques et sont générées côté serveur à l’aide des composants de base AEM CIF tels que les détails du produit et la Liste du produit sur les modèles génériques créés dans AEM. Ces composants obtiennent des données du Magento via les API GraphQL.
Ces pages sont créées dynamiquement, rendues sur le serveur, mises en cache sur le répartiteur d’AEM, puis diffusées dans le navigateur.
Pour des attributs plus dynamiques tels que le stock ou le prix, en revanche, les composants côté client sont utilisés. Les composants côté client ou les composants Web récupèrent directement les données du Magento via les API GraphQL et le contenu est rendu dans le navigateur.

#### Passage en caisse {#checkout}

Cette vitrine de référence utilise le composant Panier côté client qui effectue le rendu du panier et du formulaire de passage en caisse pour démontrer un modèle d&#39;intégration d&#39;expérience complète dans lequel vous pouvez offrir des expériences commerciales avec un Magento s&#39;exécutant de manière totalement insouciante et AEM possédant le verre. Il est recommandé d&#39;utiliser les méthodes de paiement abstrait fournies. Le client du navigateur est ainsi en communication directe avec le fournisseur de passerelle de paiement, de sorte que ni les clouds d&#39;Adobe ni les clouds de Magento ne contiennent ni ne transmettent de données sensibles PCI.

#### Gestion de compte {#account-management}

La gestion de compte est gérée par le Magento et la vitrine de référence utilise des composants React côté client pour permettre AEM de rendre l&#39;expérience pour les fonctionnalités suivantes : Créez un compte, une connexion et un mot de passe oublié.

Le projet  Venia Storefront est open source et pour plus de détails, consultez [AEM Venia Storefront](https://github.com/adobe/aem-cif-guides-venia).

### Archétype de projet AEM {#aem-project-archtype}

L&#39;[AEM Archétype de projet](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/developing/archetype/overview.html) peut être utilisé pour créer un projet Adobe Experience Manager minimal fondé sur les meilleures pratiques comme point de départ pour vos propres projets AEM. Si vous le souhaitez, [AEM les composants principaux du FIC](https://github.com/adobe/aem-core-cif-components) peuvent être inclus dans un projet nouvellement généré.

### Couche d&#39;extension CIF {#cif-extension}

La couche d&#39;extension CIF est une couche intermédiaire qui héberge une logique métier complexe. Il s&#39;exécute sur la plateforme Adobe I/O Runtime, qui est la plateforme sans serveur de l&#39;Adobe. Il vous permet d’étendre les appels de service de bout en bout en injectant une logique métier et de processus à un niveau de microservice. La logique métier consisterait par exemple à utiliser l&#39;emplacement et le canal pour déterminer une stratégie d&#39;inventaire. La logique de processus serait par exemple de récupérer des informations personnalisées.

### Couche d&#39;intégration CIF {#cif-integration-layer}

La couche d&#39;intégration CIF est utilisée pour normaliser les intégrations avec d&#39;autres solutions commerciales. Il s’exécute sur la plate-forme Adobe I/O Runtime, qui est une plate-forme sans serveur d’Adobe, et permet les intégrations au niveau des microservices en mappant les API tierces avec les API Commerce d’Adobe. Pour vous aider à commencer à créer des intégrations tierces avec l&#39;AEM, nous avons créé une [implémentation de référence](https://github.com/adobe/commerce-cif-graphql-integration-reference) pour montrer comment un serveur principal de commerce non Magento peut être intégré via les API de commerce d&#39;Adobe (API Magento GraphQL).

##  Modèles d&#39;intégration commerciale {#aem-commerce-integration}

Certains des modèles d’intégration de commerce AEM couramment mis en oeuvre sont présentés ci-dessous.

![Modèles d’intégration AEM CIF](/help/commerce-cloud/assets/aem-cif-integration-patterns-updated.JPG)


### Modèle d’intégration 1 {#integration-pattern-one}

Il s&#39;agit du modèle d&#39;intégration recommandé dans lequel AEM possède la totalité de la vitre et intègre les services de commerce via les API GraphQL de Commerce Adobe. Ce modèle offre AEM la plus grande flexibilité possible pour adapter les conceptions de sites de médias enrichis à l’ensemble des périphériques. Ce modèle d’intégration est pris en charge par CIF en tant que solution prête à l’emploi.


### Modèle d’intégration 2 {#integration-pattern-two}

Ce modèle illustre une manière totalement inutile de fournir du contenu et du commerce. La diffusion est entièrement côté client. Dans ce modèle, le contenu est diffusé par API et les données HTML et Commerce sont diffusées par GraphQL. Ce modèle n’est actuellement pas pris en charge par CIF prêt à l’emploi.


### Modèle d’intégration 3 {#integration-pattern-three}

Dans ce schéma, le Magento possède la vitre et incorpore AEM contenu écrit. Le contenu créé AEM peut être diffusé par le biais de fragments d’expérience ou de fragments de contenu. Ce modèle d&#39;intégration exigera des travaux spécifiques à un projet et ne peut pas être mis en oeuvre de façon autonome avec le FIC.


### Modèle d’intégration 4 {#integration-pattern-four}

Il s’agit d’un modèle d’intégration commun où la couche de verre ou de présentation est fractionnée entre l’AEM et une solution Commerce. En général, la solution Commerce fournit les pages non marketing telles que le passage en caisse et mon compte et mon AEM fournit les pages marketing et l&#39;expérience de catalogue de vitrine. Dans ce modèle, vous devez vous assurer que les paniers et les sessions utilisateur sont gérés correctement entre les deux systèmes afin d’éviter une expérience utilisateur disjointe. Par exemple, Magento stocke le panier et la session utilisateur dans un cookie, qui peut être partagé entre AEM et Magento. Ce modèle exigera des travaux spécifiques à chaque projet et ne peut pas être mis en oeuvre de façon autonome avec le FIC.
