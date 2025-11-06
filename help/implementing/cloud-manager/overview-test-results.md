---
title: Vue d’ensemble des tests Cloud Manager
description: Obtenez un aperçu des trois types de tests que Cloud Manager exécute automatiquement pour garantir la qualité de votre code personnalisé.
exl-id: 5f5c97b1-4180-4f49-af8b-257d4744766e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 62%

---


# Vue d’ensemble des tests Cloud Manager {#overview}

Il existe trois grandes catégories de tests pris en charge par le pipeline Cloud Manager pour services cloud :

1. [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md)

   * Le test de qualité du code évalue la qualité du code de votre application.
   * Le pipeline de qualité du code est exécuté immédiatement après l’étape de création dans tous les pipelines de production et hors production.
   * Les [règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md) exécutées par Cloud Manager sont créées et basées sur les bonnes pratiques en matière d’ingénierie AEM.

1. [Tests fonctionnels](/help/implementing/cloud-manager/functional-testing.md)

   * Les tests fonctionnels s’exécutent pendant la phase de test d’évaluation d’un [pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md). Il peut également s’exécuter, éventuellement, pendant la phase de test d’un [pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

1. [Tests d’audit d’expérience](/help/implementing/cloud-manager/reports/report-experience-audit.md)

   * Les tests d’audit de l’expérience sont activés dans tous les pipelines de production de Cloud Manager et ne peuvent pas être ignorés.

Ces tests peuvent être :

* écrits par le client ;
* écrits par Adobe ;
* créé avec des outils open source

>[!NOTE]
>
> Les tests écrits par le client ou la cliente et les tests écrits par Adobe sont exécutés dans une infrastructure en conteneur conçue à cet effet.
