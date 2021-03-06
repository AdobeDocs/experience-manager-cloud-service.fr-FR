---
title: Présentation des tests de Cloud Manager
description: Obtenez un aperçu des trois types de tests que Cloud Manager exécute automatiquement pour garantir la qualité de votre code personnalisé.
exl-id: 5f5c97b1-4180-4f49-af8b-257d4744766e
source-git-commit: a9303c659730022b7417fc9082dedd26d7cbccca
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 9%

---


# Présentation des tests de Cloud Manager {#overview}

Il existe trois catégories de tests pris en charge par Cloud Manager pour les pipelines Cloud Services.

1. [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md)

   * Le test de qualité du code évalue la qualité du code de votre application.
   * Le pipeline de qualité du code est exécuté immédiatement après l’étape de création dans tous les pipelines de production et hors production.
   * Le [règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md) exécutées par Cloud Manager sont créées en fonction des bonnes pratiques en matière d’ingénierie AEM.

1. [Tests fonctionnels](/help/implementing/cloud-manager/functional-testing.md)

   * Les tests fonctionnels font partie de la phase de test intermédiaire d’un pipeline de production.

1. [Tests de contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md)

   * Le test d’audit d’expérience est activé dans tous les pipelines de production de Cloud Manager et ne peut pas être ignoré.

Ces tests peuvent être :

* écrits par le client ;
* écrits par Adobe ;
* Créé avec des outils open source

>[!NOTE]
>
> Les tests écrits par le client et les tests écrits par l’Adobe sont exécutés dans une infrastructure en conteneur conçue à cet effet.
