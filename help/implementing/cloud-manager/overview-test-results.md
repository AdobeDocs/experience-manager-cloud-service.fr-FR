---
title: Aperçu des résultats des tests – Cloud Services
description: Aperçu des résultats des tests – Cloud Services
translation-type: tm+mt
source-git-commit: d03ef0afe91760e35ef4e8fb3e3f2c833cbf945c
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 100%

---


# Présentation {#overview}

Il existe trois grandes catégories de tests pris en charge par le pipeline Cloud Manager pour Cloud Services :

1. [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md)

   Le test de qualité du code évalue la qualité du code de votre application. Le pipeline de qualité du code est exécuté immédiatement après l’étape de création dans tous les pipelines de production et hors production.

   Les [règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md) exécutées par Cloud Manager sont créées et basées sur les bonnes pratiques en matière d’ingénierie AEM.

1. [Tests fonctionnels](/help/implementing/cloud-manager/functional-testing.md)

   Les tests fonctionnels font partie de la phase de tests d’évaluation d’un pipeline de production.

1. [Tests de contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md)

   Les tests de contrôle de l’expérience sont activés dans tous les pipelines de production de Cloud Manager et ne peuvent pas être ignorés.

Ces tests peuvent être :

* écrits par le client ;
* écrits par Adobe ;
* un outil open source.

   >[!NOTE]
   > Les tests écrits par le client et les tests écrits par Adobe sont exécutés dans une infrastructure en conteneur conçue à cet effet.

