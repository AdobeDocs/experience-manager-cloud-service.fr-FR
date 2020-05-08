---
title: Présentation d’Adobe Experience Manager as a Cloud Service - Terminologie
description: 'Présentation d’Adobe Experience Manager as a Cloud Service - Terminologie. '
translation-type: ht
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Adobe Experience Manager as a Cloud Service - Terminologie {#adobe-experience-manager-as-a-cloud-service-terminology}

Les termes suivants sont utilisés par rapport à Adobe Experience Manager (AEM) as a Cloud Service :

## Produits {#products}

| Produit | Description |
|---|---|
| AEM as a Cloud Service | Méthode d’exploitation native dans le cloud des applications AEM |
| AEM Assets as a Cloud Service | Capacités de gestion des ressources numériques (DAM) en tant que solution évolutive native de cloud pour assimiler, traiter et gérer vos ressources numériques, tout en s’intégrant à l’écosystème Adobe Experience Cloud et Adobe Creative Cloud au sens large. |
| AEM Sites as a Cloud Service | Une instance d’AEM as a Cloud Service avec l’application AEM Sites. |

## Instances et pipelines {#instances-and-pipelines}

| Instance | Description |
|---|---|
| Pipeline Adobe | Mécanisme de publication pour la publication de contenu de l’auteur. |
| Niveau de création AEM | Décrit l’environnement de création pour Sites et Assets. |
| Niveau de publication AEM | Décrit l’environnement de publication pour Sites. |


<!-- This section of the table must be alphabetic -->

## Terminologie {#terminology}

| Terme | Description |
|---|---|
| Image AEM | Artefact déployable contenant le code de produit AEM, ainsi que le code du client. |
| Microservices de ressources | Services de traitement des ressources numériques basés sur le cloud qui prennent en charge divers cas d’utilisation du traitement des ressources, tels que la génération de rendus, les workflows PDF, la gestion des sous-ressources, l’extraction de texte, etc. Pour plus d’informations, consultez l’[Aperçu sur les microservices de ressources](/help/assets/asset-microservices-overview.md). |
| Référentiel Git de Cloud Manager | Emplacement où les clients stockent leur code et leurs paramètres de configuration. |
| Fournisseur de cloud | AEM as a Cloud Service prend en charge Azure et AWS en tant que fournisseurs de cloud. |
| CDN (Content Delivery Network) | AEM as Cloud Service est fourni avec un réseau CDN par défaut. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des nœuds CDN en périphérie, près du navigateur. Il est entièrement géré et configuré afin de permettre des performances optimales des applications AEM. |
| Référentiel de contenu | Emplacement où le contenu persiste. |
| Isolation d’entreprise | Chaque instance du service AEM as a Cloud Service est isolée des autres instances. |
| Golden Master | Niveau de publication AEM. |
| Moteur d’orchestration | AEM as a Cloud Service utilise un moteur d’orchestration pour s’assurer que tous les services de création et de publication sont mis à l’échelle selon les besoins. |
