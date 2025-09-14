---
title: Liste déroulante en cascade
description: Utilisez des expressions de formulaires adaptatifs pour ajouter la validation et le calcul automatiques ainsi que pour activer ou désactiver la visibilité d’une section.
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 17%

---

# Description du cas d’utilisation

Lors de la création de formulaires ou d’applications, il est souvent utile de guider les utilisateurs et les utilisatrices dans la sélection de l’emplacement de manière structurée. Une liste déroulante en cascade rend cette opération simple et conviviale : l’utilisateur sélectionne d’abord un pays, puis filtre la liste des États/provinces disponibles, et effectue ensuite un choix final des villes en fonction de l’État. Cette approche permet non seulement de garder les formulaires plus propres, mais également d’éviter les combinaisons non valides (comme choisir une ville qui n’existe pas dans un état choisi).

Les étapes suivantes sont nécessaires pour réaliser ce cas d’utilisation

- Créer une intégration d’API
- Créez un formulaire avec des champs pour capturer le pays/l’État/la ville
- Créer une règle pour remplir les listes déroulantes à l’aide de l’intégration d’API