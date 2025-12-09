---
title: Gestion du dépassement de contenu dans l’éditeur de communication interactive
description: La gestion du débordement de contenu dans l’éditeur de communication interactive améliore le comportement du texte dans les dispositions positionnées et distribuées.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 9adc7a5669d8bf1e64cc93998cb2f91ffa9d3dd6
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 11%

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

![Rechercher document IC](/help/forms/interactive-communication/assets/content-overflow.png)

## Utilisation de la gestion des débordements de contenu dans l’éditeur de communication interactive

1. Ouvrez l’éditeur de communication interactive
Ouvrez votre communication dans l’éditeur d’IC pour commencer à modifier la mise en page et le contenu.

1. Sélectionner le type de mise en page
Choisissez la disposition souhaitée pour votre sous-formulaire, Distribué ou Positionné en fonction de la façon dont vous souhaitez que le contenu se comporte.

1. Pour Les Mises En Page Fluides

   1. Assurez-vous que la hiérarchie du sous-formulaire parent est définie sur Distribuée.

   1. Dans le panneau Propriétés , activez l’option Autoriser les sauts de page dans le contenu (visible uniquement si l’option « Autoriser les sauts de page » du sous-formulaire parent est activée).

   1. Ajoutez ou collez du texte. Lorsque le contenu dépasse une page, il passe automatiquement à la page suivante.

1. Pour les dispositions positionnées

   1. Ajouter ou modifier du texte dans un conteneur fixe.

   1. Si le contenu dépasse la hauteur du conteneur, une bordure rouge s’affiche en bas pour indiquer un débordement.

   1. Redimensionnez manuellement le conteneur pour tenir compte du contenu supplémentaire.

1. Prévisualiser la communication
Utilisez l’option Aperçu de PDF pour vérifier comment le contenu s’écoule ou déborde sur les pages pour les deux types de disposition.

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
