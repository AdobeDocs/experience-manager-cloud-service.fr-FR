---
title: Intégration d’Adobe Analytics avec AEM Screens
seo-title: Adobe Analytics Integration with AEM Screens
description: Consultez cette page pour en savoir plus sur l’intégration immédiate d’AEM Screens avec Adobe Analytics. AEM Screens vous fournit également une preuve de lecture.
seo-description: Follow this page to learn about out of the box integration of AEM Screens with Adobe Analytics and provides you with a proof of play.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: trushton
content-type: reference
products: SG_EXPERIENCEMANAGER/Cloud/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
role: Admin, Developer
level: Intermediate
source-git-commit: bf0a841a5cd5eb278fd3d59484c84d1cee172b4e
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 95%

---

# Intégration d’Adobe Analytics avec AEM Screens {#adobe-analytics-integration-with-aem-screens}

Cette section couvre les sujets suivants :

* **Présentation**
* **Particularités architecturales**

## Présentation {#overview}

***AEM Screens*** tire parti d’Adobe Analytics ; vous obtenez ainsi une solution unique sur le marché : des analyses multicanaux permettant de mettre le contenu affiché à l’emplacement concerné en corrélation avec d’autres sources de données.

AEM Screens permet une intégration immédiate avec Adobe Analytics et vous fournit une preuve de lecture.

Cette section décrit les fonctionnalités suivantes liées à la connexion d’un projet AEM Screens avec Adobe Analytics :

* Permet de créer des rapports de preuve de lecture par appareil
* Permet de créer des rapports de preuve de lecture par ressource
* Veille à ce que tous les événements du lecteur soient capturés et horodatés
* Veille à ce que tous les événements du lecteur soient stockés localement s’il n’est pas connecté à un réseau
* Permet de créer des boucles de rétroaction pour suivre les événements de lecture à long terme
* Permet au système de modifier le contenu et les dispositions selon les critères de réussite définis par l’auteur du contenu

Ainsi, l’intégration d’Adobe Analytics avec AEM Screens permet de réaliser les *objectifs* suivants :

* Obtenir un retour sur investissement des implémentations d’affichage numérique
* Intégrer Analytics comme support employé pour collecter et analyser ultérieurement les informations d’utilisation

## Particularités architecturales {#architectural-details}

Un client AEM Screens souhaite connaître les données affichées, ainsi que leurs durée et date et/ou heure d’affichage (affichage global). Il s’agit d’une fonctionnalité courante de la solution d’affichage numérique. AEM Screens tire parti d’Adobe Analytics au lieu d’élaborer vos analyses ; vous obtenez ainsi une solution unique sur le marché : des analyses multicanaux permettant de mettre le contenu affiché à l’emplacement concerné en corrélation avec d’autres sources de données.

Le diagramme architectural suivant explique comment Adobe Analytics s’intègre avec AEM Screens :

![Intégration à Adobe Analytics](/help/screens-cloud/assets/analytics-architecture.png)

## Activation d’Adobe Analytics dans AEM Screens Cloud {#enabling-adobe-analytics-in-aem-screens-cloud}

Contactez votre responsable de relations avec les Adobes pour activer les analyses d’Adobe dans Screens Cloud.

## Screens Analytics : flux d’activation {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Avant de configurer les propriétés, contactez le responsable des relations Adobe pour créer un ticket et obtenir une **clé d’API Analytics**, ainsi qu’un **projet Analytics** afin de l’utiliser avec AEM Screens.

## Utilisation d’Adobe Analytics Service dans AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Ce scénario appelle l’API Analytics en lançant des appels REST depuis un service d’analyse des principaux composants Screens de microprogramme et d’instrument pour créer et envoyer explicitement des événements propres à un cas d’utilisation donné, tout en autorisant l’extensibilité si un message personnalisé peut être envoyé à Analytics depuis un canal développé et personnalisé.

Les événements Analytics sont stockés hors ligne dans indexedDB, puis segmentés et envoyés ultérieurement vers le cloud.
