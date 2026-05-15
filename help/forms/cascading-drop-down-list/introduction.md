---
title: Listes déroulantes en cascade
description: Utilisez des expressions de formulaires adaptatifs pour ajouter la validation et le calcul automatiques ainsi que pour activer ou désactiver la visibilité d’une section.
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
source-git-commit: cc3cd74ad87f4213a200f36745ab3d335edca02d
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 100%

---

# Description du cas d’utilisation

Lors de la création de formulaires ou d’applications, il est souvent utile de guider les utilisateurs et les utilisatrices dans la sélection de l’emplacement de manière structurée. Une liste déroulante en cascade rend cette opération simple et conviviale : l’utilisateur ou l’utilisatrice sélectionne d’abord un pays, puis filtre la liste des états/provinces disponibles, et effectue ensuite un choix final des villes en fonction de l’état. Cette approche permet non seulement de rendre les formulaires plus clairs, mais également d’éviter les combinaisons non valides (comme choisir une ville qui n’existe pas dans un état choisi).

Les étapes suivantes sont nécessaires pour réaliser ce cas d’utilisation :

- Créer une intégration d’API
- Créez un formulaire avec des champs pour capturer le pays/l’état/la ville.
- Créez une règle pour renseigner les listes déroulantes à l’aide de l’intégration d’API.