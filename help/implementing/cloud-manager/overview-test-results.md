---
title: Présentation des résultats des tests - Cloud Services
description: Présentation des résultats des tests - Cloud Services
translation-type: tm+mt
source-git-commit: 25ba5798de175b71be442d909ee5c9c37dcf10d4
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 41%

---


# Présentation {#overview}

Les exécutions du pipeline Cloud Manager for Cloud Services prennent en charge l’exécution de tests sur l’environnement d’évaluation. Cela contraste avec les tests exécutés dans le cadre de l’étape Test de création et d’unité, qui sont réalisés hors ligne, sans aucun accès à un environnement AEM actif.

Il existe trois grandes catégories de tests pris en charge par Cloud Manager pour le gazoduc Cloud Services :

1. [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md)
1. [Tests fonctionnels](/help/implementing/cloud-manager/functional-testing.md)
1. [Test de l’audit du contenu](/help/implementing/cloud-manager/content-audit-testing.md)

Ces tests peuvent être :

* Écrit par le client
* adobe écrit
* Outil Open Source (optimisé par Lighthouse depuis Google)

   >[!NOTE]
   > Les tests écrits par le client et les tests écrits par Adobe sont exécutés dans une infrastructure conteneurisée conçue pour exécuter ces types de tests.

