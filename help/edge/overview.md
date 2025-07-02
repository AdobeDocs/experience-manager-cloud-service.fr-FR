---
title: Vue d’ensemble d’Edge Delivery Services
description: Découvrez comment AEM as a Cloud Service peut bénéficier des performances et des scores Lighthouse parfaits proposés par Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 03a1aa93-d2e6-4175-9cf3-c7ae25c0d24e
role: Admin, Architect, Developer
source-git-commit: 9829709a4558a2d0fd479c7c0fed979ee43937ea
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 37%

---


# Vue d’ensemble d’Edge Delivery Services {#edge-delivery-services}

## Qu’est-ce que Edge Delivery Services ? {#what-is-edge}

Edge Delivery Services est un cadre de diffusion de contenu moderne qui repense la création et la diffusion de sites web, en optimisant la vitesse, la simplicité et l’évolutivité. Il s’agit d’une partie essentielle de Adobe Experience Manager qui permet des expériences digitales plus rapides en rapprochant le rendu et la diffusion de l’utilisateur ou de l’utilisatrice, aux limites du réseau.

Il ne remplace pas un réseau de diffusion de contenu (CDN), mais il s’intègre de manière transparente à votre propre réseau de diffusion de contenu ou au réseau de diffusion de contenu [géré par Adobe inclus.](/help/implementing/dispatcher/cdn.md)

>[!TIP]
>
>**Vous voulez passer à la pratique tout de suite ?**
>
>Si vous voulez passer à la pratique tout de suite, vous pouvez démarrer votre propre projet Edge DeliveryServices avec la création AEM en moins de 30 minutes en [consultant le tutoriel sur aem.live.](https://www.aem.live/developer/ue-tutorial)


## Pourquoi Edge Delivery Services ? {#why-edge}

### Augmente la visibilité et le trafic {#increase-traffic}

Les sites web Edge Delivery sont optimisés pour les moteurs de recherche (SEO) et optimisés pour les moteurs génératifs (GEO) pour les LLM. Cela garantit une visibilité et une découvrabilité élevées sur toutes les sources existantes et à venir pour le trafic organique. L’**architecture de bout en bout performante** garantit une expérience client agréable qui aura un impact positif sur l’engagement.

### Efficacité des développeurs {#developer-efficientcy}

Effectuez la mise en ligne en jours et en semaines au lieu de mois et d’années ! Edge Delivery offre tous les outils **les développeurs web modernes** adorent : GitHub, le développement local avec rechargement automatique, la performance, la simplicité et aucune des complications : aucune transpilation, aucun bundler, aucune configuration, aucune surcharge.

La simplicité d’Edge Delivery ne nécessite pas l’utilisation de frameworks, d’outils ou de processus complexes, ce qui est idéal pour la création de code d’IA. Utilisez des HTML simples, des CSS modernes et des JavaScript classiques pour créer des expériences exceptionnelles plus rapidement que jamais. Concentrez-vous sur le travail et consacrez moins de temps à la formation et à l’apprentissage de nouveaux outils.

Edge Delivery permet à chaque développeur d’atteindre un score de 100 lighthouse.

### Prise en charge de plusieurs sources de contenu {#multiple-content-sources}

Le contenu de diverses solutions peut s’intégrer directement à Edge Delivery, **y compris toutes vos instances AEM existantes**. Les auteurs peuvent gérer et **publier du contenu à partir de n’importe quel système, tel que SharePoint vers Edge Delivery** pour gagner en vitesse grâce à des outils qu’ils connaissent déjà.

### Architecture composable {#composable-architeture}

Qu’il soit découplé ou couplé, vous pouvez diffuser le contenu approprié au bon format et ajouter la décoration appropriée pour en faire une expérience qui se démarque sur n’importe quel canal.

## Comment cela fonctionne-t-il {#how-does-it-work}

Edge Delivery Services est un ensemble de services composable qui offre une grande flexibilité quant à la manière dont vous créez du contenu sur votre site web. Il remplace l’instance de publication/Dispatcher d’AEM et la méthode traditionnelle de création d’expériences avec les composants principaux d’AEM par une solution SaaS multi-cloud et une approche de développement front-end pure.

![Architecture d’Edge Delivery](assets/aem-with-eds-architecture.png)

Edge Delivery Services utilise GitHub pour vous permettre de gérer et de déployer du code directement à partir de votre référentiel GitHub. Le nouveau contenu est ajouté instantanément sans nouveau processus de création.

## Création {#authoring}

### Modification dans le contexte {#in-context-editing}

[L’éditeur universel](/help/implementing/universal-editor/introduction.md) est un emplacement unique personnalisable et ce que vous voyez est ce que vous obtenez (WYSIWYG) pour modifier du contenu en direct et en contexte avec un aperçu visuel.

* Avec la création AEM et l’éditeur universel, vous augmentez l’efficacité de la création, qu’elle soit découplée ou couplée.
* Vous pouvez tirer parti des fonctionnalités complètes de gestion de contenu AEM, notamment de workflow et de gouvernance.
* Vous pouvez tirer parti de nombreux points d’extension pour prendre en charge vos propres processus et intégrations.
* Les fonctionnalités de votre site peuvent être développées à l’aide de CSS et JavaScript dans GitHub.

![Création AEM avec l’éditeur universel](assets/wysiwyg-authoring.png)

### Modification basée sur des documents {#document-based-editing}

[Une autre approche est la création basée sur des documents](https://www.aem.live/docs/authoring) où le contenu est géré en tant que documents. Microsoft Word est un choix populaire car de nombreuses entreprises ont mis en place SharePoint où le contenu initial est créé. Plus besoin d’apprendre à utiliser un nouvel outil et publier du contenu directement depuis SharePoint et Word supprime les problèmes de copier et coller du contenu dans AEM. Les clients qui ne disposent pas de SharePoint peuvent également utiliser Google Drive comme alternative.

## Télémétrie opérationnelle {#telemetry}

Adobe Experience Manager utilise la [télémétrie opérationnelle](https://www.aem.live/docs/operational-telemetry) pour collecter les données d’opération strictement nécessaires pour découvrir et résoudre les problèmes fonctionnels et de performance sur les sites gérés par Adobe Experience Manager. Les données de télémétrie opérationnelle peuvent être utilisées pour diagnostiquer les problèmes de performance et pour mesurer l’efficacité des expériences. La télémétrie opérationnelle préserve la confidentialité des visiteurs par le biais de [échantillonnage](https://www.aem.live/docs/operational-telemetry#operational-telemetry-data-is-sampled) (seule une petite partie de toutes les pages vues sera surveillée) et [exclusion judicieuse des informations d’identification personnelle](https://www.aem.live/docs/operational-telemetry#what-data-is-being-collected) (PII).

## Commencer l’exploration {#start-exploring}

Commencez à utiliser la création AEM avec l’éditeur universel et Edge Delivery Services :

* Documentation Edge Delivery Services [Edge Delivery Services](https://www.aem.live)
* Pour une vue d’ensemble de la création AEM avec l’éditeur universel, consultez le document [Création avec AEM pour Edge Delivery Services](https://www.aem.live/docs/aem-authoring) dans la documentation aem.live.
* Pour obtenir une vue d’ensemble du développement, consultez le document [Commencer - Tutoriel de développement de l’éditeur universel](https://www.aem.live/developer/ue-tutorial) dans la documentation aem.live.

## Edge Delivery Services et autres produits Adobe Experience Cloud {#edge-other-products}

Les Edge Delivery Services font partie d’Adobe Experience Manager. Ainsi, les Edge Delivery Services et AEM Sites peuvent coexister sur le même domaine, ce qui est un cas d’utilisation courant pour les sites web plus volumineux. De plus, vos pages AEM Sites peuvent facilement consommer du contenu des Edge Delivery Services, et l’inverse est également vrai.

Vous pouvez également utiliser Edge Delivery Services avec [Adobe Target](https://www.aem.live/developer/target-integration) et [Launch.](https://experienceleague.adobe.com/fr/docs/experience-platform/tags/home)

## Obtenir de l’aide à partir d’Adobe {#getting-help}

Adobe propose trois couches pour vous aider avec Edge Delivery Services :

* Interagissez avec les [ressources de la communauté](#community-resources) pour des questions générales.
* Accédez à votre [canal de collaboration de produits](#collaboration-channel) pour des questions spécifiques.
* [Enregistrez un ticket d’assistance](#support-ticket) pour résoudre les problèmes majeurs et critiques **dans le SLA d’assistance contractuelle**.

### Accéder aux ressources de la communauté {#community-resources}

Adobe s’engage à vous donner les moyens d’engager et de soutenir la communauté au mieux pour Edge Delivery Services, la création AEM avec l’éditeur universel et la création basée sur des documents.

* Participez à la [Communauté Experience League](https://adobe.ly/3Q6kTKl) pour poser des questions, partager vos commentaires, lancer des discussions, demander l’aide de personnes spécialisées d’Adobe et de personnes conseillères/championnes AEM, et communiquer en temps réel avec des personnes partageant les mêmes opinions.
* Rejoignez également notre [canal Discord](https://discord.gg/aem-live), une plateforme plus décontractée pour des interactions en temps réel et des échanges d’idées rapides.

### Consigner un ticket d’assistance {#support-ticket}

{{support-ticket}}
