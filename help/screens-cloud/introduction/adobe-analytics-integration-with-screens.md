---
title: Intégration d’Adobe Analytics à AEM Screens Cloud
description: Consultez cette page pour en savoir plus sur l’intégration immédiate d’AEM Screens avec Adobe Analytics. AEM Screens vous fournit également une preuve de lecture.
contentOwner: trushton
content-type: reference
products: SG_EXPERIENCEMANAGER/Cloud/SCREENS
topic-tags: administering
docset: aem65
role: Admin, Developer
level: Intermediate
exl-id: e22242ce-e5ce-4486-bba4-e6a89ac4fb5e
feature: Screens Deployments
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 75%

---

# Intégration d’Adobe Analytics à AEM Screens Cloud {#adobe-analytics-integration-with-aem-screens}

Cette section couvre les sujets suivants :

* **Présentation**
* **Particularités architecturales**

## Vue d’ensemble {#overview}

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

Un client AEM Screens souhaite connaître les données affichées, ainsi que leurs durée et date et/ou heure d’affichage (affichage global). Il s’agit d’une fonctionnalité courante de la solution d’affichage numérique. Au lieu de créer nos propres analyses, AEM Screens utilise Adobe Analytics. Avec cette solution, vous pouvez obtenir un résultat unique sur le marché : des analyses cross-canal qui permettent de mettre en relation le contenu affiché à l’emplacement avec d’autres sources de données.

Le diagramme architectural suivant explique comment Adobe Analytics s’intègre avec AEM Screens :

![Intégration à Adobe Analytics](/help/screens-cloud/assets/analytics-architecture.png)

## Activation d’Adobe Analytics dans AEM Screens Cloud {#enabling-adobe-analytics-in-aem-screens-cloud}

Contactez votre gestionnaire de relations d’Adobe pour activer Adobe Analytics dans Screens Cloud.

## Utilisation du service Adobe Analytics dans AEM Screens Cloud {#using-adobe-analytics-service-in-aem-screens}

Ce scénario appelle l’API Analytics en lançant des appels REST depuis un service d’analyse des principaux composants Screens de microprogramme et d’instrument pour créer et envoyer explicitement des événements propres à un cas d’utilisation donné, tout en autorisant l’extensibilité si un message personnalisé peut être envoyé à Analytics depuis un canal développé et personnalisé.

Les événements Analytics sont stockés hors ligne dans indexedDB, puis segmentés et envoyés ultérieurement vers le cloud.

>[!NOTE]
>Pour en savoir plus sur le séquencement et le modèle de données standard pour les événements, voir [Configuration d’Adobe Analytics pour AEM Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/analytics-integration/configuring-adobe-analytics-aem-screens.html?lang=fr) pour plus d’informations.
