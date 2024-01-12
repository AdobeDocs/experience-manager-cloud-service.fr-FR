---
title: AEM et Edge Delivery Services
description: Comprendre comment AEM as a Cloud Service peut bénéficier des performances et des bons scores Lighthouse proposés par Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 03a1aa93-d2e6-4175-9cf3-c7ae25c0d24e
source-git-commit: 9d26a4835dc331f2ff8b741a4c14847ead611874
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 43%

---


# AEM et Edge Delivery Services {#aem-edge}

Avec Edge Delivery Services, AEM offre des expériences exceptionnelles qui favorisent l’engagement et les conversions. AEM le fait en proposant des expériences à fort impact qui sont rapides à créer et à développer. C’est un ensemble de services composable qui permet un environnement de développement rapide où les personnes créant le contenu peuvent rapidement effectuer des mises à jour et des publications, et où de nouveaux sites sont lancés rapidement. Ainsi, avec Edge Delivery Services, vous pouvez améliorer la conversion, réduire les coûts et offrir une vitesse de contenu extrême.

En utilisant des Edge Delivery Services, vous pouvez :

* Créer des sites rapides avec un score Lighthouse parfait et surveiller en permanence les performances de votre site grâce à la surveillance des utilisateurs et utilisatrices réels (RUM).
* Augmenter l’efficacité de la création en découplant les sources de contenu. Vous pouvez utiliser nativement les instances de création AEM et la création basée sur des documents. Ainsi, vous pouvez utiliser plusieurs sources de contenu sur le même site web.
* Utiliser un framework d’expérimentation intégré qui permet la création rapide de tests, l’exécution sans impact sur les performances et la mise en production rapide de la meilleure version.

## Présentation des Edge Delivery Services {#edge-overview}

Le diagramme suivant illustre comment modifier du contenu dans Microsoft Word (modification basée sur des documents) et le publier dans des Edge Delivery Services. Il affiche également la méthode de publication AEM à l’aide d’Universal Editor.

![Architecture d’Edge Delivery.](assets/AEM-with-EDS-publishing-simple2.png)

Les services de diffusion Edge sont un ensemble de services composables qui offre une grande flexibilité quant à la manière dont vous créez du contenu sur votre site web. Comme mentionné précédemment, vous pouvez utiliser les deux [Gestion de contenu AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/getting-started/concepts.html?lang=fr) avec [Création Universal Editor](/help/implementing/universal-editor/introduction.md) ainsi que [création basée sur des documents.](https://www.aem.live/docs/authoring)

Par exemple, vous pouvez utiliser du contenu directement à partir de documents Microsoft Word ou Google Docs. Cela signifie que les documents provenant de ces sources peuvent devenir des pages de votre site web. De plus, les en-têtes, listes, images et éléments de police peuvent tous être transférés de la source initiale vers le site web. Le nouveau contenu est ajouté instantanément sans processus de reconstruction.

Edge Delivery Services utilise GitHub pour permettre aux clients de gérer et déployer le code directement à partir de leur référentiel GitHub. Par exemple, vous pouvez écrire du contenu dans Google Docs ou Microsoft Word et les fonctionnalités de votre site peuvent être développées à l’aide de CSS et de JavaScript dans GitHub. Lorsque tout est prêt, vous pouvez utiliser l’extension de navigateur Sidekick pour prévisualiser et publier les mises à jour de contenu.

Pour plus d’informations, consultez la documentation Edge Delivery Services :

* Pour plus d’informations sur la prise en main d’Edge Delivery, voir le [Créer .](https://www.aem.live/docs/#build)
* Pour comprendre comment créer et publier du contenu à l’aide d’Edge Delivery, voir [Publier .](https://www.aem.live/docs/authoring)
* Pour comprendre comment lancer correctement votre projet de site web, voir [section Lancement .](https://www.aem.live/docs/#launch)

## Edge Delivery Services et autres produits Adobe Experience Cloud {#edge-other-products}

Les Edge Delivery Services font partie de Adobe Experience Manager et, de ce fait, les Edge Delivery Services et les sites AEM peuvent coexister sur le même domaine. Il s’agit d’un cas d’utilisation courant pour les sites web plus volumineux. De plus, le contenu des Edge Delivery Services peut être facilement utilisé dans vos pages AEM Sites et inversement.

Vous pouvez également utiliser des Edge Delivery Services avec Adobe Target, Analytics et Launch.

## Accéder à Edge Delivery Services {#getting-access}

Il est facile de commencer à utiliser des Edge Delivery Services. Commencez en suivant les [Prise en main - Tutoriel du développeur.](https://www.aem.live/developer/tutorial)

## Obtenir de l’aide à partir d’Adobe {#adobe-gethelp}

Vous pouvez interagir avec les équipes produit d’Adobe via votre canal de collaboration de produit configuré (voir ci-dessous pour plus d’informations sur l’accès) afin de répondre à des questions sur l’utilisation du produit ou les bonnes pratiques. Aucun SLT (Service Level Targets) n’est associé aux conversations via le canal de collaboration des produits. Si un problème de produit nécessite une enquête et un dépannage supplémentaires et doit répondre aux tests SLT, vous pouvez envoyer un ticket d’assistance à la suite de la [processus d’assistance.](https://experienceleague.adobe.com/?support-tab=home&amp;lang=fr#support)

Adobe fournit trois canaux pour vous aider avec Edge Delivery Services :

* Interagir avec les ressources de la communauté pour des questions générales
* Accéder à votre canal de collaboration de produits pour des questions spécifiques
* Enregistrer un ticket d’assistance pour résoudre les problèmes majeurs et critiques

### Accéder aux ressources de la communauté {#community-resource}

Adobe s’engage à vous donner les moyens d’engager et de soutenir la communauté au mieux pour les Edge Delivery Services et la création basée sur les documents.

* Participez à [Communauté Experience League](https://adobe.ly/3Q6kTKl) pour poser des questions, partager vos commentaires, lancer des discussions, demander l’aide d’experts en Adobe et d’AEM conseillers/Champs, et communiquer en temps réel avec des personnes partageant les mêmes opinions.
* Rejoignez notre [Canal de discorde,](https://discord.gg/aem-live) une plateforme plus informelle pour les interactions en temps réel et les échanges d&#39;idées rapides.

### Accès à votre canal de collaboration de produit {#collab-channel}

Compte tenu de la valeur du canal de communication directe avec les clients, tous les clients AEM au lancement établiront un canal Slack pour la vitesse, les mises à jour critiques et la création de rapports à l’échelle sur la qualité de l’expérience. Vous recevez une invitation d’Adobe à rejoindre un canal de Slack spécifique à votre entreprise.

Pour plus d’informations, consultez le document [Utilisation du robot Slack](https://www.aem.live/docs/slack) pour obtenir plus de détails.

### Consigner un ticket d’assistance {#support-ticket}

Étapes pour consigner un ticket d’assistance via Admin Console :

1. [suivre le processus de prise en charge standard,](https://experienceleague.adobe.com/?support-tab=home&amp;lang=fr#support) créez un ticket.
1. Ajoutez **Edge Delivery** dans le titre du ticket.
1. Dans la description, fournissez les détails suivants :

   * URL du site web actif. Par exemple : `www.mydomain.com`.
   * URL du site web d&#39;origine (`.hlx` URL).

## Prochaines étapes {#whats-next}

Prise en main de la révision [Utilisation d’Edge Delivery Services](/help/edge/using.md).
