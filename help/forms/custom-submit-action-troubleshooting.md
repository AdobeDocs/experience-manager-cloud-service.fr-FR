---
title: Résolution d’une erreur 502 dans l’action d’envoi personnalisée pour le Forms adaptatif
description: Découvrez comment identifier et résoudre les pages d’erreur 502 qui se produisent lors de l’utilisation d’actions d’envoi personnalisées dans le Forms adaptatif (composants principaux). Ce guide explique les causes courantes, telles que les exceptions non gérées, et fournit des étapes de résolution.
feature: Adaptive Forms, Core Components
role: Developer
level: Intermediate
source-git-commit: 03e46bb43e684a6b7057045cf298f40f9f1fe622
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 1%

---


# Dépannage : page d’erreur 502 dans l’action d’envoi personnalisée

Lorsque vous utilisez des Forms adaptatives (composants principaux), vous pouvez rencontrer une erreur **502, page HTML**, après l’envoi d’un formulaire qui utilise une action d’envoi personnalisée.

## Problème

**Erreur :** une page d’erreur 502 HTML s’affiche lorsqu’un service d’action d’envoi personnalisée échoue.

**Raison :** cela se produit si l’action d’envoi personnalisée renvoie une erreur non gérée, par exemple, un pointeur nul, une réponse d’API non valide ou un échec d’exécution.

## Résolution

Pour éviter la page d’erreur 502, encapsulez la logique d’envoi avec des blocs try-catch pour gérer les erreurs de manière appropriée.

Pour obtenir des instructions détaillées, voir [Création d’une action Envoyer personnalisée pour le Forms adaptatif (composants principaux)](/help/forms/custom-submit-action-for-adaptive-forms-based-on-core-components.md).
