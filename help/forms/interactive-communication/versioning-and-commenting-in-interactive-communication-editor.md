---
title: Contrôle de version et commentaires dans l’éditeur de communication interactive
description: Le contrôle de version et les commentaires dans l’éditeur de communication interactive d’AEM Forms permettent aux entreprises de créer des documents dynamiques pilotés par les données pour une communication personnalisée avec les clients.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: ca9917c0-d8bb-4381-afab-7ab888d992e8
source-git-commit: b817bcb02c4ff6ac369973ef658d9fcbdce95c51
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 1%

---

# Contrôle de version et commentaires dans l’éditeur de communication interactive


Les communications interactives permettent aux entreprises de créer des documents dynamiques pilotés par les données pour une communication personnalisée avec les clients. Pour prendre en charge une meilleure collaboration, gouvernance et publication contrôlée, l’éditeur de communication interactive fournit des fonctionnalités de contrôle de version, de révision et de commentaires.

Ces fonctionnalités aident les auteurs à gérer plusieurs itérations d’une communication interactive, à capturer les commentaires des réviseurs et réviseuses, à revenir à des versions antérieures et à maintenir un journal d’audit clair tout au long du cycle de vie du contenu.

## Contrôle de version de la communication interactive

Le contrôle de version dans l’éditeur de communication interactive permet aux auteurs :

- Créer plusieurs versions d’une communication interactive

- Enregistrez les modifications incrémentielles avec des libellés et des commentaires pertinents.

- Rétablir une version précédente

- Comparer visuellement les différences

- Maintenir une gouvernance propre pour les cycles de révision, d’approbation et de publication

Cela permet aux auteurs et autrices de tester, d’itérer et d’affiner les conceptions de communication interactive tout en préservant le contexte historique complet.

## Créer une version d’une communication interactive

Utilisez le contrôle de version lorsque vous souhaitez conserver l’état actuel d’une communication interactive avant d’effectuer des mises à jour.

Pour créer une version :

1. Accédez à **Forms et documents** et sélectionnez la communication interactive dont vous souhaitez modifier la version.

1. Dans le coin supérieur gauche de l’affichage de la ressource, sélectionnez le bouton (bascule) du rail, puis choisissez **Chronologie** dans les options du panneau.

   ![Créer la version 1](/help/forms/interactive-communication/assets/create-version1.png)

1. Le panneau **Chronologie** s’ouvre à gauche et affiche l’historique des activités de la communication interactive sélectionnée, y compris les annotations et les versions précédentes.

   Par exemple, après un cycle de révision, la chronologie peut afficher des annotations telles que **mettre à jour l’adresse** et **Mettre à jour le modèle de voiture** avec d’autres entrées d’activité.

   ![Créer la version 2](/help/forms/interactive-communication/assets/create-version2.png)

1. Au bas du panneau **Chronologie**, cliquez sur **Enregistrer comme version**.

1. Dans la boîte de dialogue **Créer une version**, saisissez un libellé de version et un commentaire facultatif décrivant l’objectif ou les modifications apportées à cette version.

   Par exemple, saisissez **comprend le nouveau logo de la banque** comme commentaire de version.

   ![Créer la version 3](/help/forms/interactive-communication/assets/create-version3.png)

1. Cliquez sur **Créer**.

   La nouvelle entrée de version apparaît dans le journal et un message de réussite confirme la création de la version.

   ![Créer la version 4](/help/forms/interactive-communication/assets/create-version4.png)

Une nouvelle entrée de version est ajoutée à la liste des versions, capturant votre état actuel de communication interactive.

## Mettre à jour une version

Chaque fois que vous modifiez et enregistrez la communication interactive, vous pouvez créer une version pour capturer l’état mis à jour.

Pour ajouter une nouvelle version après modification :

1. Ouvrez **Forms et documents** puis sélectionnez la communication interactive.

1. Ouvrez le panneau **Chronologie** dans le rail de gauche.

1. Suivez les étapes de la section [Créer une version d’une communication interactive](#create-a-version-of-an-interactive-communication) pour enregistrer l’état actuel avec un nouveau libellé et un nouveau commentaire.

Cela permet aux équipes de suivre les progrès et d’assurer la transparence du cycle de vie.

## Rétablir une version précédente

Si une communication interactive doit revenir à une configuration antérieure :

1. Accédez à **Forms et documents** et sélectionnez la communication interactive.

1. Ouvrez le panneau **Chronologie** dans le rail de gauche.

1. Dans la chronologie, sélectionnez la version à restaurer. Par exemple, sélectionnez **Communication interactive bancaire V1** avec le commentaire **Inclut le nouveau logo de la banque**.

   ![Rétablir la version 1](/help/forms/interactive-communication/assets/create-version5.png)

1. Cliquez sur **Revenir à cette version**.

   Un message de réussite confirme que la communication interactive a été restaurée à la version sélectionnée. La chronologie enregistre une entrée **Page restaurée**.

   ![Rétablir la version 2](/help/forms/interactive-communication/assets/create-version6.png)

La communication interactive est restaurée à la version sélectionnée, ce qui permet aux auteurs d’annuler les modifications indésirables ou de récupérer en cas d’erreur.

## Comparer deux versions

Vous pouvez comparer deux versions d’une communication interactive côte à côte lors des aperçus PDF, ce qui permet de repérer facilement les différences de disposition et de contenu statique sans ouvrir chaque version individuellement.

Pour obtenir des instructions détaillées, voir [Comparer les versions de la communication interactive](/help/forms/interactive-communication/howto/compare-interactive-communication-versions.md).

## Ajouter des commentaires à une communication interactive

Les commentaires permettent aux réviseurs et aux auteurs d’ajouter des notes générales directement à partir du panneau **Chronologie** dans **Forms et documents**.

Pour ajouter un commentaire :

1. Accédez à **Forms et documents** et sélectionnez la communication interactive.

1. Ouvrez le panneau **Chronologie** dans le rail de gauche.

1. Saisissez votre note dans le champ **Commentaire** au bas du panneau **Chronologie** et enregistrez-la.

   Les commentaires apparaissent dans la chronologie à côté des annotations, des entrées de version et d’autres activités. Par exemple, après un cycle de révision, la chronologie peut répertorier des annotations telles que **mettre à jour l’adresse** et **Mettre à jour le modèle de voiture** au-dessus des commentaires généraux et de l’historique des versions.

Pour les commentaires de révision positionnés au niveau du composant (où un réviseur épingle un commentaire à un champ ou une section spécifique sur la zone de travail), utilisez plutôt la fonction Annotations . Voir [Vérifier et annoter une communication interactive](/help/forms/interactive-communication/howto/review-and-annotate-interactive-communication.md).

## Voir également

- [Comparer les versions de la communication interactive](/help/forms/interactive-communication/howto/compare-interactive-communication-versions.md)
- [Vérifier et annoter une communication interactive](/help/forms/interactive-communication/howto/review-and-annotate-interactive-communication.md)
- [Créer une communication interactive](/help/forms/interactive-communication/create-interactive-communication.md)

