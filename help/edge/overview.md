---
title: Vue d’ensemble d’Edge Delivery Services
description: Découvrez comment AEM as a Cloud Service peut bénéficier des performances et des scores Lighthouse parfaits proposés par Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 03a1aa93-d2e6-4175-9cf3-c7ae25c0d24e
role: Admin, Architect, Developer
source-git-commit: 7ad9a959592f1e8cebbcad9a67d280d5b2119866
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 89%

---


# Vue d’ensemble d’Edge Delivery Services {#edge-delivery-services}

Avec Edge Delivery Services, AEM offre des expériences exceptionnelles qui favorisent l’engagement et les conversions. AEM le fait en proposant des expériences à fort impact qui sont rapides à créer et à développer. C’est un ensemble de services composable qui permet un environnement de développement rapide où les personnes créant le contenu peuvent rapidement effectuer des mises à jour et des publications, et où de nouveaux sites sont lancés rapidement. Ainsi, avec Edge Delivery Services, vous pouvez améliorer la conversion, réduire les coûts et offrir une vitesse de contenu extrême.

En utilisant Edge Delivery Services, vous pouvez accomplir ce qui suit :

* Créer des sites rapides avec un score Lighthouse parfait et surveiller en permanence les performances de votre site grâce à la surveillance de l’utilisation en temps réel (RUM).
* Augmenter l’efficacité de la création en découplant les sources de contenu. Vous pouvez utiliser WYSIWYG et la création basée sur les documents prêts à l’emploi . Ainsi, vous pouvez utiliser plusieurs sources de contenu sur le même site web.
* Utiliser un framework d’expérimentation intégré qui permet la création rapide de tests, l’exécution sans impact sur les performances et la mise en production rapide de la meilleure version.

## Vue d’ensemble {#overview}

Edge Delivery Services est un ensemble de services composable qui offre une grande flexibilité quant à la manière dont vous créez du contenu sur votre site web. Vous pouvez utiliser les [Gestion de contenu AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/getting-started/concepts.html?lang=fr) et WYSIWYG en utilisant la méthode [Éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md) ainsi que [création basée sur des documents.](https://www.aem.live/docs/authoring)

Le diagramme suivant illustre comment modifier du contenu dans Microsoft Word (création basée sur des documents) et le publier sur Edge Delivery Services. Il affiche également la modification WYSIWYG à l’aide de l’éditeur universel.

![Architecture d’Edge Delivery](assets/AEM-with-EDS-publishing-simple2.png)

Vous pouvez utiliser du contenu directement à partir de Microsoft Word ou de Google Docs de sorte que ces sources deviennent des pages de votre site web. De plus, les en-têtes, listes, images et éléments de police peuvent tous être transférés de la source initiale vers le site web. Le nouveau contenu est ajouté instantanément sans nouveau processus de création.

Edge Delivery Services utilise GitHub pour vous permettre de gérer et de déployer du code directement à partir de votre référentiel GitHub. Par exemple, vous écrivez du contenu dans Google Docs ou Microsoft Word et les fonctionnalités de votre site peuvent être développées à l’aide de CSS et de JavaScript dans GitHub. Lorsque tout est prêt, vous utilisez l’extension de navigateur Sidekick pour prévisualiser et publier les mises à jour de contenu.

Pour plus d’informations, consultez la documentation Edge Delivery Services :

* Pour plus d’informations sur la prise en main d’Edge Delivery, consultez la [section Créer](https://www.aem.live/docs/#build).
* Pour comprendre comment créer et publier du contenu à l’aide d’Edge Delivery, consultez la [section Publier](https://www.aem.live/docs/authoring).
* Pour comprendre comment lancer correctement votre projet de site web, consultez la [section Démarrer](https://www.aem.live/docs/#launch).

## Edge Delivery Services et autres produits Adobe Experience Cloud {#edge-other-products}

Edge Delivery Services fait partie d’Adobe Experience Manager. De ce fait, Edge Delivery Services et AEM Sites peuvent coexister sur le même domaine, ce qui est un cas d’utilisation courant pour les sites web plus volumineux. De plus, le contenu d’Edge Delivery Services peut être facilement utilisé par vos pages AEM Sites et vice versa.

Veuillez consulter la [Guide de prise en main du développeur pour WYSIWYG avec des Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) pour savoir comment démarrer votre propre projet pour créer avec des Edge Delivery Services et des AEM.

Vous pouvez également utiliser Edge Delivery Services avec [Adobe Target](https://www.aem.live/developer/target-integration) et la [surveillance de l’utilisation en temps réel (RUM)](https://www.aem.live/developer/rum) pour diagnostiquer l’utilisation et les performances de vos sites, ainsi que [Launch.](https://experienceleague.adobe.com/fr/docs/experience-platform/tags/home)

## Commencer avec Edge Delivery Services {#getting-started}

Il est facile de commencer à utiliser Edge Delivery Services en suivant le tutoriel [Commencer - Tutoriel de développement.](https://www.aem.live/developer/tutorial)

## Obtenir de l’aide à partir d’Adobe {#getting-help}

Adobe fournit trois canaux pour vous aider avec Edge Delivery Services :

* Interagissez avec les [ressources de la communauté](#community-resources) pour des questions générales.
* Accédez à votre [canal de collaboration de produits](#collaboration-channel) pour des questions spécifiques.
* [Consignez un ticket d’assistance](#support-ticket) pour résoudre les problèmes majeurs et critiques.

### Accéder aux ressources de la communauté {#community-resources}

Adobe s’engage à vous donner les moyens d’engager et de soutenir la communauté au mieux pour les Edge Delivery Services, WYSIWYG et la création basée sur des documents.

* Participez à la [Communauté Experience League](https://adobe.ly/3Q6kTKl) pour poser des questions, partager vos commentaires, lancer des discussions, demander l’aide de personnes spécialisées d’Adobe et de personnes conseillères/championnes AEM, et communiquer en temps réel avec des personnes partageant les mêmes opinions.
* Rejoignez également notre [canal Discord](https://discord.gg/aem-live), une plateforme plus décontractée pour des interactions en temps réel et des échanges d’idées rapides.

### Comment accéder à votre canal de collaboration de produit {#collaboration-channel}

Compte tenu de la valeur du canal de communication directe avec les utilisateurs et utilisatrices, tous les projets AEM établiront au lancement un canal Slack dans le but d’accélérer les mises à jour critiques et de développer des rapports sur la qualité de l’expérience. Vous recevrez une invitation d’Adobe à rejoindre un canal Slack spécifique à votre organisation.

Pour plus d’informations, consultez le document [Utilisation du robot Slack](https://www.aem.live/docs/slack) pour obtenir plus de détails.

Vous pouvez interagir avec les équipes produit Adobe via votre canal de collaboration de produit configuré afin de répondre à des questions sur l’utilisation du produit ou les bonnes pratiques. Veuillez noter qu’aucun objectif de niveau de service (Service Level Target, SLT) n’est associé aux conversations via le canal de collaboration du produit.

### Consigner un ticket d’assistance {#support-ticket}

Si un problème de produit nécessite une enquête et un dépannage supplémentaires et doit répondre aux tests SLT, vous pouvez envoyer un ticket d’assistance à la suite du processus à l’aide d’Admin Console :

1. [Suivez le processus de prise en charge standard](https://experienceleague.adobe.com/?support-tab=home#support) et créez un ticket.
1. Ajoutez **Edge Delivery** dans le titre du ticket.
1. Dans la description, fournissez les détails suivants en plus de la description du problème :

   * URL du site web actif. Par exemple : `www.mydomain.com`.
   * URL du site web d’origine (URL `.hlx`).

## Prochaines étapes {#whats-next}

Commencez en consultant [Utilisation d’Edge Delivery Services](/help/edge/using.md).
