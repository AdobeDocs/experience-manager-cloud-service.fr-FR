---
title: Intégration de Edge Delivery Services au réseau CDN géré par Adobe dans Cloud Manager
description: null
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: 2d2a206fea14d7e786a98e848bc2f2592ac65429
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# Intégration de Edge Delivery Services au réseau CDN géré par Adobe dans Cloud Manager {#integrate-adbe-cdn-with-edservices-in-cm}

Le réseau CDN géré par Adobe (AMC-D) s’intègre de manière native à Edge Delivery Services pour vous offrir des expériences performantes distribuées dans le monde entier pour les sites Adobe Experience Manager (AEM).

Ensemble, ils vous offrent les avantages suivants :

* Un réseau CDN d’entreprise clé en main géré par Adobe.
* Couche de diffusion Edge moderne qui accélère les requêtes, optimise la mise en cache et protège contre les attaques courantes.
* Workflow Cloud Manager unifié pour la gestion des domaines, les certificats SSL et les déploiements pilotés par pipeline.

<!--
Adobe's Edge Delivery Services (EDS) can take advantage of an Adobe managed CDN. EDS is a framework that optimizes website delivery for speed, simplicity, and scalability by pushing content closer to the user through edge nodes. It is not a replacement for a CDN, but rather a way to enhance content delivery, especially when you use the Adobe managed CDN. It offers you the following benefits:

* Adobe-Managed CDN: EDS can use an Adobe-managed CDN, offering features like self-service CDN management and automatic certificate renewal. 
* EDS and AEM: EDS is a feature of AEM as a Cloud Service and works alongside the AEM authoring environment. 
* Performance enhancement: EDS, in conjunction with an Adobe Managed CDN, improves website performance by caching content at edge locations closer to users, reducing latency. 
* Flexibility: EDS provides flexibility in content delivery, allowing your organization to choose between the Adobe-managed CDN or their own CDN setup, based on their needs and existing infrastructure. 
Self-Service CDN Management:
Adobe-managed CDN within EDS enables self-service configuration and management tasks like SSL certificate setup. 
 
Use Cases:
EDS with CDN integration is beneficial for various scenarios, including e-commerce storefronts and websites requiring high performance and scalability. -->

## Options de déploiement de Edge Delivery Services dans le réseau CDN géré par Adobe dans Cloud Manager {#deployment-options}

Cette rubrique explique les deux manières dont vous pouvez déployer Edge Delivery Services sur le réseau CDN géré par Adobe dans Cloud Manager et, tout aussi important, vous aide à choisir l’option la mieux adaptée à votre cas d’utilisation.

Edge Delivery Services peut être configuré à l’aide de l’une des deux options suivantes. Chacun possède des fonctionnalités différentes.

|  | Option de déploiement | Document clé | Fonction | Idéal pour |
| --- | --- | --- | --- | --- |
| Option 1 | *avec* un environnement AEM as a Cloud Service (AEMaaCS) existant ; | [Configurer un proxy à partir d’un environnement existant](https://www.aem.live/docs/byo-cdn-adobe-managed#option-1-setup-a-proxy-from-an-existing-environment) | Le pipeline de configuration est généralement disponible pour les environnements AEMaaCS | Les équipes qui exécutent déjà Sites dans Cloud Manager et qui souhaitent une amélioration rapide et à faible risque des performances. |
| Option 2 | *Sans* un environnement AEMaaCS existant, connu sous le nom d’« environnement Edge » autonome. | [Configuration d’un site Edge Delivery sans environnement existant](https://www.aem.live/docs/byo-cdn-adobe-managed#option-2-setup-an-edge-delivery-site-without-an-existing-environment) | Le pipeline de configuration est actuellement disponible uniquement pour les environnements Edge par le biais du programme Beta limité.<br>Voir [Ajouter le pipeline de configuration Edge Delivery](help/implementing/cloud-manager/release-notes/current.md##add-eds-pipeline). | Nouvelles versions ou migrations qui souhaitent adopter l’architecture Edge Delivery complète et le routage granulaire. |

<!-- Ultimately this URL above will need to be updated on GA -->

| Option | Résumé | Idéal pour | Documents clés |
| --- | --- | --- | --- |
| Proxy CDN géré par Adobe | Le réseau CDN géré par Adobe fait face à un environnement AEM Sites existant. Votre pipeline Sites actuel reste l’« origine », tandis qu’AMC-D gère la mise en cache Edge et la terminaison TLS. | Les équipes qui exécutent déjà Sites dans Cloud Manager et qui souhaitent une amélioration rapide et à faible risque des performances. | Configurer un proxy AMC-D |
| Configuration du pipeline avec originSelectors | Un pipeline de configuration Edge Delivery dédié publie du contenu statique et dynamique directement sur Edge. `originSelectors` acheminer le trafic entre AMC-D et votre niveau de création/publication AEM. | Nouvelles versions ou migrations qui souhaitent adopter l’architecture Edge Delivery complète et le routage granulaire. | Configuration du pipeline Edge Delivery |

>[!TIP]
>
>Vous ne savez pas quel chemin choisir ? Consultez [Choisir un modèle de déploiement](#choose-deployment-model) ci-dessous pour obtenir des instructions relatives aux décisions.

## Choisir un modèle de déploiement {#choose-deployment-model}

Les deux modèles peuvent coexister au sein du même programme Cloud Manager, ce qui permet des migrations échelonnées.

| Si vous... | Alors, utilisez... |
| :--- | :--- |
| Besoin d’un déploiement rapide et à modification minimale et d’héberger déjà Sites dans Cloud Manager | Proxy AMC-D |
| Prévoyez de restructurer le contenu pour Edge Delivery ou souhaitez un routage affiné entre plusieurs origines | Configurer le pipeline de diffusion Edge + `originSelectors` |

## Prérequis {#prerequisites}

1. Intégration de votre site dans Cloud Manager
&#x200B;- Requis pour les deux modèles de déploiement. Suivez la section Intégration d’un site AEM.

2. Apportez votre propre Git (BYOG) (facultatif)
&#x200B;- Si vous stockez le code du site en dehors d’Adobe Git, effectuez l’intégration BYOG.

3. Licence Edge Delivery
&#x200B;- Vérifiez que votre programme dispose d’une licence pour Edge Delivery Services.


