---
title: Présentation des résultats des tests - Cloud Services
description: Présentation des résultats des tests - Cloud Services
translation-type: tm+mt
source-git-commit: d03ef0afe91760e35ef4e8fb3e3f2c833cbf945c
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 2%

---


# Présentation {#overview}

Il existe trois grandes catégories de tests pris en charge par Cloud Manager pour le gazoduc Cloud Services :

1. [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md)

   Le test de qualité du code évalue la qualité du code de votre application. Le pipeline Code-Qualité est exécuté immédiatement après l’étape de création dans tous les pipelines de non-production et de production.

   The [Custom Code Quality Rules](/help/implementing/cloud-manager/custom-code-quality-rules.md) executed by Cloud Manager are created based on best practices from AEM Engineering.

1. [Tests fonctionnels](/help/implementing/cloud-manager/functional-testing.md)

   Les essais fonctionnels font partie de la phase d&#39;essai en phase d&#39;un pipeline de production.

1. [Test d’audit d’expérience](/help/implementing/cloud-manager/experience-audit-testing.md)

   Le test d’audit d’expérience est activé dans tous les tuyaux de production de Cloud Manager et ne peut pas être ignoré.

Ces tests peuvent être :

* Écrit par le client
* adobe écrit
* Outil Open Source

   >[!NOTE]
   > Les tests écrits par le client et les tests écrits par Adobe sont exécutés dans une infrastructure conteneurisée conçue pour exécuter ces types de tests.

