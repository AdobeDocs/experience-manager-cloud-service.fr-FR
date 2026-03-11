---
title: Résolution d’une erreur 502 dans l’action d’envoi personnalisée pour le Forms adaptatif
description: Découvrez comment identifier et résoudre les pages d’erreur 502 qui se produisent lors de l’utilisation d’actions d’envoi personnalisées dans le Forms adaptatif (composants principaux). Ce guide explique les causes courantes, telles que les exceptions non gérées, et fournit des étapes de résolution.
feature: Adaptive Forms, Core Components
role: Developer
level: Intermediate
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: a7469926-7059-4aca-90ff-2554d14c3944
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 2%

---

# Dépannage : page d’erreur 502 dans l’action d’envoi personnalisée

Lorsque vous utilisez des Forms adaptatives (composants principaux), vous pouvez rencontrer une erreur **502, page HTML**, après l’envoi d’un formulaire qui utilise une action d’envoi personnalisée.

## Problème

**Erreur :** une page d’erreur 502 HTML s’affiche lorsqu’un service d’action d’envoi personnalisée échoue.

**Raison :** cela se produit si l’action d’envoi personnalisée renvoie une erreur non gérée, par exemple, un pointeur nul, une réponse d’API non valide ou un échec d’exécution.

## Résolution

Pour éviter la page d’erreur 502, encapsulez la logique d’envoi avec des blocs try-catch pour gérer les erreurs de manière appropriée.

Pour obtenir des instructions détaillées, voir [Création d’une action Envoyer personnalisée pour le Forms adaptatif (composants principaux)](/help/forms/custom-submit-action-for-adaptive-forms-based-on-core-components.md).
