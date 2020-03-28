---
title: Présentation d’Adobe Experience Manager en tant que service Cloud - Terminologie
description: 'Présentation d’Adobe Experience Manager as a Cloud Service - Terminologie. '
translation-type: tm+mt
source-git-commit: bdda0ab15fa2cac40aefa5f60809ca96302fcabb

---


# Adobe Experience Manager as a Cloud Service - Terminology {#adobe-experience-manager-as-a-cloud-service-terminology}

Les termes suivants sont utilisés par rapport à Adobe Experience Manager (AEM) en tant que service Cloud :

## Produits {#products}

| Produit | Description |
|---|---|
| AEM as a Cloud Service | Méthode native du cloud pour exploiter les applications AEM |
| AEM Assets as a Cloud Service | Gestion des actifs numériques (DAM) en tant que solution évolutive native de cloud, permet d’assimiler, de traiter et de gérer vos actifs numériques, tout en s’intégrant à l’écosystème Adobe Experience Cloud et Adobe Creative Cloud au sens large. |
| AEM Sites as a Cloud Service | Une instance d’AEM en tant que service Cloud avec l’application Sites AEM. |

## Instances et pipelines {#instances-and-pipelines}

| Instance | Description |
|---|---|
| Adobe Pipeline | Mécanisme de publication de contenu de l’auteur à la publication. |
| Niveau Auteur AEM | Décrit le  de création  pour les sites et les ressources. |
| Niveau de publication AEM | Décrit le  de publication  pour les sites. |


<!-- This section of the table must be alphabetic -->

## Terminologie {#terminology}

| Term | Description |
|---|---|
| Image AEM | Artefact déployable qui contient le code de produit AEM ainsi que le code du client. |
| Microservices de ressources | Services de traitement des ressources numériques basés sur le cloud qui prennent en charge divers cas d’utilisation du traitement des ressources, tels que la génération de rendus, les processus PDF, la gestion des sous-ressources, les  de texte , etc. Pour plus d’informations, voir Présentation [des microservices](/help/assets/asset-microservices-overview.md)de fichiers. |
| Référentiel Git De Cloud Manager | Emplacement où les clients stockent leur code et leurs paramètres de configuration. |
| Fournisseur de cloud | AEM en tant que service Cloud prend en charge Azure et AWS en tant que fournisseurs de cloud. |
| CDN (Content Network) | Le service AEM as Cloud est fourni avec un CDN par défaut. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des noeuds CDN au bord, près du navigateur. Il est entièrement géré et configuré pour des performances optimales des applications AEM. |
| Référentiel de contenu | Emplacement où le contenu est conservé. |
| Isolation d’entreprise | Chaque instance du service AEM en tant que service Cloud est isolée des autres instances. |
| Maître d&#39;or | Niveau de publication AEM. |
| Moteur d’orchestration | AEM en tant que service Cloud utilise un moteur d’orchestration pour s’assurer que tous les services d’auteur et de publication sont mis à l’échelle selon les besoins. |
