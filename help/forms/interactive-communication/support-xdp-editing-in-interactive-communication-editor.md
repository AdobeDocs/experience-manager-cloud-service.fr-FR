---
title: Prise en charge de l’édition XDP dans l’éditeur de communication interactive
description: La prise en charge de l’édition XDP dans l’éditeur de communication interactive permet de modifier les fichiers XDP existants dans l’éditeur de communication interactive.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 957944da363b506c34c2630aeedbe984442f34b8
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 13%

---


# Prise en charge de l’édition XDP dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## Présentation

L’éditeur de communication interactive (IC) offre désormais une prise en charge transparente **pour la modification des fichiers XDP (XML Data Package)** dans l’environnement de création. Cette amélioration permet aux créateurs et aux créatrices de gérer, modifier et gérer les modèles XDP en toute facilité, sans recourir à des outils externes. Grâce à cette fonctionnalité, les utilisateurs peuvent charger, afficher et modifier des fichiers XDP directement dans l’éditeur IC, ce qui permet d’obtenir un workflow de conception à diffusion unifié et efficace.

## Comment utiliser la prise en charge de l’édition XDP dans l’éditeur de communication interactive

![Rechercher document IC](/help/forms/interactive-communication/assets/support-xdp.png)

1. Accédez à **Forms > Forms et documents**.

1. Chargez votre fichier .xdp à l’aide de l’option **Créer > Chargement de fichier**.

1. Ouvrez le fichier XDP dans **Éditeur de communication interactive**.

1. Apportez les modifications **de conception ou de liaison de données** nécessaires.

1. Enregistrez vos modifications. Les mises à jour sont automatiquement répercutées dans le fichier XDP source.

## Fonctionnalités essentielles

- **Télécharger et gérer des fichiers XDP :**
Chargez des modèles XDP via **Forms Manager**. Une fois chargés, ils peuvent être modifiés directement dans l’éditeur de communication interactive.

- **Modifier à l’aide de l’éditeur IC :**
Ouvrez et modifiez des fichiers XDP à l’aide de l’éditeur IC avec un accès complet aux fonctionnalités d’édition existantes, y compris les ajustements de disposition, la liaison de données, le style et la configuration des composants.

- **Enregistrer à nouveau dans Source :**
Toutes les modifications apportées par l’intermédiaire de l’éditeur IC sont enregistrées directement dans le fichier XDP d’origine, tout en préservant l’intégrité de la version et en simplifiant le processus de conception.

## Prise en charge des fragments

- **Références de fragment :**
Si un fichier XDP fait référence à un fragment, ce fragment doit exister dans **AEM au même chemin d’accès relatif** tel que défini dans le fichier XDP.
Si un fragment est manquant, l’éditeur affiche un **message d’avertissement** indiquant que le fragment requis n’est pas présent.

- **Réutilisation de fragment dans l’éditeur :**
Tous les fragments XDP existants apparaissent dans le **panneau Fragments** de l’éditeur IC.
Les auteurs peuvent **glisser-déposer** ces fragments directement sur la zone de travail. Les références sont conservées, ce qui garantit que les mises à jour des fragments se propagent sur tous les XDP qui les utilisent.

## Avantages

- Élimine la dépendance aux outils externes pour la modification de XDP.

- Préserve les liaisons de données et les relations de fragment existantes.

- Permet une conception cohérente et des cycles d’itération plus rapides.

## Bonnes pratiques

- Assurez-vous que tous les fragments référencés existent dans le bon chemin d’accès relatif avant de les modifier.

- Utilisez le contrôle de version pour gérer les mises à jour dans les dépendances XDP et des fragments.

- Validez les liaisons de données après modification pour confirmer un rendu correct.

