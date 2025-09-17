---
title: Vue d’ensemble d’Edge Delivery Services
description: Découvrez comment AEM as a Cloud Service peut bénéficier des performances et des scores Lighthouse parfaits proposés par Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 03a1aa93-d2e6-4175-9cf3-c7ae25c0d24e
role: Admin, Architect, Developer
source-git-commit: 8cbcfbc074c69396980ba930339563d5437d5f17
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 94%

---


# Vue d’ensemble d’Edge Delivery Services {#edge-delivery-services}

>[!TIP]
>
>**Vous voulez passer à la pratique tout de suite ?**
>
>Si vous souhaitez vous familiariser immédiatement avec Edge Delivery Services, vous disposez de deux options.
>* [Commencez immédiatement la création avec un environnement de tutoriel préconfiguré, entièrement configuré et prêt à l’emploi.](https://www.aem.live/developer/ue-trial)
>* Découvrez plus de détails et configurez votre propre environnement en moins de 30 minutes en [consultez le tutoriel sur aem.live.](https://www.aem.live/developer/ue-tutorial)

## Qu’est-ce qu’Edge Delivery Services ? {#what-is-edge}

Edge Delivery Services est un framework de diffusion de contenu moderne qui repense la création et la diffusion des sites web, en optimisant la vitesse, la simplicité et l’évolutivité. Il s’agit d’un élément essentiel d’Adobe Experience Manager qui offre des expériences numériques plus rapides en rapprochant le rendu et la diffusion de l’utilisateur ou de l’utilisatrice, au niveau de la périphérie (edge) du réseau.

Il ne remplace pas un réseau de diffusion de contenu (CDN), mais il s’intègre de manière transparente à votre propre CDN ou au CDN inclus [géré par Adobe.](/help/implementing/dispatcher/cdn.md)

## Pourquoi utiliser Edge Delivery Services ? {#why-edge}

### Augmente la visibilité et le trafic. {#increase-traffic}

Les sites web Edge Delivery sont optimisés pour les moteurs de recherche (SEO) et optimisés pour les moteurs génératifs (GEO) pour les LLM. Cela garantit une visibilité et une découvrabilité élevées sur toutes les sources existantes et à venir pour le trafic organique. L’**architecture de bout en bout privilégiant les performances** garantit une expérience client agréable, ce qui aura un impact positif sur l’engagement.

### Pour un développement efficace {#developer-efficientcy}

Effectuez votre mise en ligne en quelques jours à quelques semaines au lieu de plusieurs mois voire plusieurs années ! Edge Delivery fournit tous les outils que **les développeurs et développeuses web modernes** adorent : GitHub, un développement local avec rechargement automatique, de la performance, de la simplicité sans aucune des complications : aucune transpilation, aucun bundler, aucune configuration, aucune surcharge.

La simplicité d’Edge Delivery ne requiert pas l’utilisation de frameworks, d’outils ou de processus complexes, ce qui est idéal pour la création de code d’IA. Utilisez du HTML brut, du CSS moderne et du JavaScript classique pour créer des expériences exceptionnelles plus rapidement que jamais. Concentrez-vous sur votre travail et consacrez moins de temps à vous former et à apprendre à utiliser de nouveaux outils.

Edge Delivery permet à chaque développeur et développeuse d’atteindre un score Lighthouse de 100.

### Prise en charge de plusieurs sources de contenu {#multiple-content-sources}

Le contenu de diverses solutions peut s’intégrer directement à Edge Delivery, **y compris toutes vos instances AEM existantes**. Les créateurs et créatrices peuvent gérer et **publier du contenu à partir de n’importe quel système, tel que SharePoint vers Edge Delivery** pour aller encore plus vite avec les outils qu’ils connaissent déjà.

### Architecture composable {#composable-architeture}

Qu’il soit découplé ou couplé, vous pouvez diffuser le contenu approprié au bon format et ajouter une apparence appropriée pour en faire une expérience qui se démarque sur n’importe quel canal.

## Comment fonctionne-t-il ? {#how-does-it-work}

Edge Delivery Services est un ensemble de services composable qui offre une grande flexibilité quant à la manière dont vous créez du contenu sur votre site web. Il remplace l’instance de publication/le Dispatcher AEM et la méthode traditionnelle de création d’expériences avec les composants principaux d’AEM par une solution SaaS multicloud et une approche de développement front-end pure.

![Architecture d’Edge Delivery](assets/aem-with-eds-architecture.png)

Edge Delivery Services utilise GitHub pour vous permettre de gérer et de déployer du code directement à partir de votre référentiel GitHub. Le nouveau contenu est ajouté instantanément sans nouveau processus de création.

## Création {#authoring}

### Modification dans le contexte {#in-context-editing}

L’[éditeur universel](/help/implementing/universal-editor/introduction.md) est un outil multifonction personnalisable WYSIWYG qui vous permet de modifier du contenu en direct et en contexte à l’aide d’un aperçu visuel.

* Avec la création AEM et l’éditeur universel, vous augmentez l’efficacité de la création, qu’elle soit découplée ou couplée.
* Vous pouvez tirer parti des fonctionnalités complètes de gestion de contenu d’AEM, notamment de workflow et de gouvernance.
* Tirez parti de nombreux points d’extension pour prendre en charge vos propres processus et intégrations.
* Les fonctionnalités de votre site peuvent être développées à l’aide de CSS et JavaScript dans GitHub.

![Création AEM avec l’éditeur universel](assets/wysiwyg-authoring.png)

### Modification basée sur des documents {#document-based-editing}

[Une autre approche est la création basée sur des documents](https://www.aem.live/docs/authoring) où le contenu est géré en tant que documents. Microsoft Word est un choix populaire car de nombreuses entreprises possèdent SharePoint, où le contenu d’origine est créé. Plus besoin d’apprendre à utiliser un nouvel outil ! Publier du contenu directement à partir de SharePoint et Word supprime également les problèmes liés à la copie de contenu vers AEM. Les clientes et les clients qui ne disposent pas de SharePoint peuvent également utiliser Google Drive comme alternative.

## Télémétrie opérationnelle {#telemetry}

Adobe Experience Manager utilise la [télémétrie opérationnelle](https://www.aem.live/docs/operational-telemetry) pour collecter les données opérationnelles strictement nécessaires pour découvrir et résoudre les problèmes fonctionnels et les problèmes de performance sur les sites gérés par Adobe Experience Manager. Les données de télémétrie opérationnelle peuvent être utilisées pour diagnostiquer les problèmes de performance et pour mesurer l’efficacité des expériences. La télémétrie opérationnelle préserve la vie privée des visiteurs et des visiteuses par le biais de [l’échantillonnage](https://www.aem.live/docs/operational-telemetry#operational-telemetry-data-is-sampled) (seule une petite partie de toutes les visites des pages est surveillée) et de l’[exclusion judicieuse des informations d’identification personnelle](https://www.aem.live/docs/operational-telemetry#what-data-is-being-collected).

## Commencez à explorer {#start-exploring}

Commencez la création dans AEM avec l’éditeur universel et Edge Delivery Services :

* Documentation Edge Delivery Services [Edge Delivery Services](https://www.aem.live)
* Pour une vue d’ensemble de la création AEM avec l’éditeur universel, consultez le document [Création avec AEM pour Edge Delivery Services](https://www.aem.live/docs/aem-authoring) dans la documentation aem.live.
* Pour obtenir une vue d’ensemble du développement, consultez le document [Commencer - Tutoriel de développement de l’éditeur universel](https://www.aem.live/developer/ue-tutorial) dans la documentation aem.live.

## Edge Delivery Services et autres produits Adobe Experience Cloud {#edge-other-products}

Les Edge Delivery Services font partie d’Adobe Experience Manager. Ainsi, les Edge Delivery Services et AEM Sites peuvent coexister sur le même domaine, ce qui est un cas d’utilisation courant pour les sites web plus volumineux. De plus, vos pages AEM Sites peuvent facilement consommer du contenu des Edge Delivery Services, et l’inverse est également vrai.

Vous pouvez également utiliser Edge Delivery Services avec [Adobe Target](https://www.aem.live/developer/target-integration) et [Launch](https://experienceleague.adobe.com/fr/docs/experience-platform/tags/home).

## Obtention d’aide à partir d’Adobe {#getting-help}

Adobe met à disposition trois canaux pour vous aider avec Edge Delivery Services :

* Interagissez avec les [ressources de la communauté](#community-resources) pour des questions générales.
* Accédez à votre [canal de collaboration de produits](#collaboration-channel) pour des questions spécifiques.
* [Soumettez un ticket d’assistance](#support-ticket) pour résoudre les problèmes majeurs et critiques **dans le cadre du SLA d’assistance contractuel**.

### Accéder aux ressources de la communauté {#community-resources}

Adobe s’engage à vous donner les moyens d’engager et de soutenir la communauté au mieux pour Edge Delivery Services, la création AEM avec l’éditeur universel et la création basée sur des documents.

* Participez à la [Communauté Experience League](https://adobe.ly/3Q6kTKl) pour poser des questions, partager vos commentaires, lancer des discussions, demander l’aide de personnes spécialisées d’Adobe et de personnes conseillères/championnes AEM, et communiquer en temps réel avec des personnes partageant les mêmes opinions.
* Rejoignez également notre [canal Discord](https://discord.gg/aem-live), une plateforme plus décontractée pour des interactions en temps réel et des échanges d’idées rapides.

### Consigner un ticket d’assistance {#support-ticket}

{{support-ticket}}
