---
title: Contrôle de version et commentaires dans l’éditeur de communication interactive
description: Le contrôle de version et les commentaires dans l’éditeur de communication interactive d’AEM Forms permettent aux entreprises de créer des documents dynamiques pilotés par les données pour une communication personnalisée avec les clients.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: 7f366823e1baeda8eacd8c92fe23300d10ec828a
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 8%

---


# Contrôle de version et commentaires dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

Les communications interactives (CI) permettent aux entreprises de créer des documents dynamiques pilotés par les données pour une communication personnalisée avec les clients. Pour prendre en charge une meilleure collaboration, gouvernance et publication contrôlée, l’éditeur de communication interactive fournit des fonctionnalités de contrôle de version, de révision et de commentaires.

Ces fonctionnalités aident les auteurs à gérer plusieurs itérations d’un CI, à capturer les commentaires des réviseurs et réviseuses, à revenir à des versions antérieures et à maintenir un journal d’audit clair tout au long du cycle de vie du contenu.

## Contrôle de version de la communication interactive

Le contrôle de version dans l’éditeur de communication interactive permet aux auteurs :

- Création de plusieurs versions d’un IC

- Enregistrez les modifications incrémentielles avec des libellés et des commentaires pertinents.

- Rétablir une version précédente

- Comparer visuellement les différences

- Maintenir une gouvernance propre pour les cycles de révision, d’approbation et de publication

Cela permet aux auteurs d’expérimenter, d’itérer et d’affiner les conceptions IC tout en préservant le contexte historique complet.

## Créer une version d’une communication interactive

Utilisez le contrôle de version lorsque vous souhaitez conserver l’état actuel d’un IC avant d’effectuer des mises à jour.

Pour créer une version :

1. Ouvrez AEM et accédez à Forms → Forms et documents.

1. Sélectionnez la communication interactive dont vous souhaitez modifier la version.

1. Dans le volet de gauche, choisissez Versions.

1. Dans le menu d’actions (points de suspension), sélectionnez Enregistrer comme version.

1. Saisissez un libellé de version et un commentaire facultatif décrivant l’objectif ou les modifications apportées à cette version.

1. Enregistrez la version.

Une nouvelle entrée de version est ajoutée à la liste des versions, capturant votre état IC actuel.

## Mettre à jour une version

Chaque fois que vous modifiez et enregistrez la communication interactive, vous pouvez créer une version pour capturer l’état mis à jour.

Pour ajouter une nouvelle version après modification :

1. Ouvrez l’ID dans l’éditeur et effectuez vos mises à jour.

1. Suivez les étapes de la section Créer une version d’une communication interactive.

1. Ajoutez un libellé et un commentaire expliquant ce qui a changé.

Cela permet aux équipes de suivre les progrès et d’assurer la transparence du cycle de vie.

## Rétablir une version précédente

Si un CI doit revenir à une configuration antérieure :

1. Ouvrez Forms &amp; Documents et sélectionnez l’ID.

1. Accédez au panneau Versions .

1. Sélectionnez la version antérieure à restaurer.

1. Cliquez sur Revenir à cette version.

L’IC sera restauré à la version sélectionnée, ce qui permettra aux auteurs d’annuler les modifications indésirables ou de récupérer après une erreur.

## Comparer deux versions

Les auteurs peuvent comparer visuellement deux versions pour comprendre les modifications apportées aux mises à jour. Cela s’avère utile pour les révisions liées à l’interface utilisateur, à la disposition ou au contenu.

Pour comparer :

1. Accédez à Versions pour l’ID sélectionné.

1. Sélectionnez une version dans la liste.

1. Sélectionnez Comparer avec la version actuelle.

Un aperçu côte à côte affiche les différences entre les deux versions.

## Ajouter des commentaires à une communication interactive

Les commentaires permettent aux réviseurs et aux auteurs de collaborer directement dans l’éditeur de communication interactive.

Pour ajouter un commentaire :

1. Sélectionnez la communication interactive dans Forms et documents.

1. Accédez au panneau Commentaires .

1. Saisissez vos commentaires ou vos notes, puis cliquez sur Ajouter un commentaire.

Les commentaires permettent de rationaliser les workflows entre les auteurs, les réviseurs et les parties prenantes.

>[!NOTE]
>
>Lors de l’utilisation de commentaires dans les communications interactives, le workflow autonome « Révision et approbation » pour les formulaires est automatiquement désactivé.

Le contrôle de version et les commentaires dans l’éditeur de communication interactive fournissent les éléments suivants :

- Gouvernance structurée du contenu

- Collaboration simplifiée

- Historique des modifications traçable

- Fonctionnalités de restauration et de comparaison simples

Ces fonctionnalités prennent en charge la création, la conformité et l’itération contrôlées tout au long du cycle de vie des communications client.
