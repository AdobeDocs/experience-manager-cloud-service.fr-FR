---
title: Gestion du dépassement de contenu dans l’éditeur de communication interactive
description: La gestion du débordement de contenu dans l’éditeur de communication interactive améliore le comportement du texte dans les dispositions positionnées et distribuées.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 371838c77beafa8c67259a865b25325632bea0b0
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 17%

---


# Gestion du dépassement de contenu dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## Présentation

La fonctionnalité de gestion du débordement de contenu de l’éditeur de communication interactive améliore le comportement du texte dans les mises en page Distribuées et Positionnées. Il garantit la continuité du contenu pour les mises en page fluides et fournit des alertes visuelles pour les mises en page positionnées, offrant ainsi aux auteurs un meilleur contrôle et une meilleure flexibilité lors de la conception des communications.

## Fonctionnalités essentielles

### Disposition Fluide

- **Nouvelle option :**
Ajoute une propriété **autoriser les sauts de page** dans le contenu pour contrôler le comportement de débordement. Cette option est visible uniquement lorsque le sous-formulaire parent est défini sur Distribué et que sa propriété **Autoriser les sauts de page** est activée.

- **Poursuite automatique de page :**
Lorsque le contenu dépasse l’espace disponible, une nouvelle page est automatiquement créée et la modification se poursuit de manière transparente.

- **Prise en charge du copier-coller :**
Le texte volumineux collé dans l’éditeur traverse automatiquement les pages, ce qui permet de maintenir la cohérence de la disposition.

### Disposition positionnée

- **Indicateur de débordement :**
Lorsque le contenu dépasse le conteneur (sous-formulaire ou page), l’éditeur de texte se développe pour être modifié, mais la hauteur de l’élément reste fixe.

- **Alerte visuelle :**
Une bordure rouge s’affiche au bas du conteneur pour indiquer un débordement.

- **Réglage manuel :**
Les auteurs redimensionnent manuellement le conteneur pour l’adapter au contenu supplémentaire.

>[!NOTE]
>
> Cette fonction nécessite de définir l’ensemble de la hiérarchie parente (comme les sous-formulaires) sur Distribuée. Si un sous-formulaire parent de la hiérarchie est positionné, l’option **Autoriser les sauts de page** dans le contenu ne fonctionnera pas comme prévu.

## Avantages

- Améliore l’efficacité et le contrôle de la création de contenu.

- Permet de conserver une disposition et une lisibilité cohérentes entre les pages.

- Permet d’identifier rapidement le débordement grâce à des indicateurs visuels.

- Améliore la flexibilité de la conception de communication pour les deux types de disposition.
