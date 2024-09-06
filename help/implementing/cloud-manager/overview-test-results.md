---
title: Vue d’ensemble des tests Cloud Manager
description: Obtenez une vue d’ensemble des trois types de tests que Cloud Manager exécute automatiquement pour garantir la qualité de votre code personnalisé.
exl-id: 5f5c97b1-4180-4f49-af8b-257d4744766e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: cfaa3be31195929b80310610120a779a20537c61
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 91%

---


# Vue d’ensemble des tests Cloud Manager {#overview}

Il existe trois grandes catégories de tests pris en charge par le pipeline Cloud Manager pour services cloud :

1. [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md)

   * Le test de qualité du code évalue la qualité du code de votre application.
   * Le pipeline de qualité du code est exécuté immédiatement après l’étape de création dans tous les pipelines de production et hors production.
   * Les [règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md) exécutées par Cloud Manager sont créées et basées sur les bonnes pratiques en matière d’ingénierie AEM.

1. [Tests fonctionnels](/help/implementing/cloud-manager/functional-testing.md)

   * Les tests fonctionnels font partie de la phase de test d’un [pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) et font éventuellement partie de la phase de test d’un [pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

1. [Tests d’audit de l’expérience](/help/implementing/cloud-manager/experience-audit-dashboard.md)

   * Le test de contrôle de l’expérience est activé dans tous les pipelines de production Cloud Manager et ne peut pas être ignoré.

Ces tests peuvent être :

* écrits par le client ;
* écrits par Adobe ;
* créé avec des outils open source

>[!NOTE]
>
> Les tests écrits par le client ou la cliente et les tests écrits par Adobe sont exécutés dans une infrastructure en conteneur conçue à cet effet.
