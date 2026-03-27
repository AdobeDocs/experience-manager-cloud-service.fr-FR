---
title: Créer un tableau dynamique dans l’éditeur de communication interactive
description: Fonction Créer un tableau dynamique qui permet aux auteurs de créer des tableaux pilotés par les données.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
source-git-commit: 322183c28719db5b8657d9532ef234e1d18821cd
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---


# Créer un tableau dynamique dans l’éditeur de communication interactive

## Vue d’ensemble

L’éditeur de communication interactive fournit un tableau dynamique
Cette fonctionnalité permet aux auteurs de créer des tableaux pilotés par les données dont le contenu est automatiquement renseigné au moment de l’exécution à partir de sources de données structurées.

Contrairement aux tables statiques où les lignes doivent être créées manuellement, les tables dynamiques se développent ou se contractent automatiquement en fonction des enregistrements renvoyés par une source de données liée. Cela les rend utiles pour des scénarios tels que des relevés de facturation, des historiques de transactions, des listes de produits ou des plannings de politique.

Cet article explique comment insérer et configurer un tableau dynamique avec liaison de données, gérer le flux de tableau à plusieurs pages et valider le nombre de lignes.

## Insertion d’un tableau dynamique

1. Ouvrez l’**éditeur de communication interactive**.
1. Dans le panneau **Composant**, faites glisser le **composant Tableau** vers la
Zone de travail.
1. Indiquez le **nombre de colonnes** et **lignes initiales** dans la boîte de dialogue, assurez-vous que la **ligne d’en-tête** est incluse, puis cliquez sur OK pour créer le tableau.

### Liaison des données au tableau dynamique

Les tableaux dynamiques renseignent automatiquement les lignes en se liant à une source de données répétable.

![Rechercher un document IC](/help/forms/interactive-communication/assets/databinding-in-table.png)

Pour lier des données à la table :

1. Sélectionnez la **ligne du tableau** dans le panneau Hiérarchie.

1. Ouvrez la **Liaison de données** à partir du panneau latéral.

1. Assurez-vous que le schéma de données sélectionné est de type tableau.

1. Faites glisser et déposez le schéma de données du tableau sur la ligne de tableau sélectionnée pour lier les données.

### Activer le flux de page

Les tableaux dynamiques peuvent s’étendre au-delà d’une page. Pour permettre au tableau de s’agrandir et de continuer sur plusieurs pages, placez-le dans un conteneur **Contenu distribué**.

![Rechercher un document IC](/help/forms/interactive-communication/assets/table-data-binding.png)

Pour activer le flux de page :

1. Sélectionnez le **conteneur de mises en page parent** du tableau.

1. Ouvrez le panneau Propriétés et définissez le Type de contenu sur **Distribué**.

1. Sélectionnez le tableau et assurez-vous qu’il est également configuré pour prendre en charge le contenu distribué.

1. Prévisualisez la communication pour vérifier que le tableau continue sur la page suivante au fur et à mesure que des lignes supplémentaires sont rendues.

### Autoriser le saut de page dans le tableau

![Rechercher un document IC](/help/forms/interactive-communication/assets/table-data-binding.png)

Pour vous assurer que le tableau se divise correctement entre les pages :

1. Sélectionnez le **tableau** dans la zone de travail.
1. Ouvrez le panneau **Propriétés**.
1. Activez **Autoriser le saut de page dans le contenu**.

Lorsqu’il est activé, le tableau se rompt automatiquement à la fin d’une page et se poursuit sur la page suivante, avec la ligne d’en-tête répétée.

### Configurer la validation des lignes

Vous pouvez contrôler le nombre de lignes que le tableau dynamique peut rendre.

* **Nombre minimum de lignes :** garantit que le tableau effectue le rendu d’au moins le nombre de lignes spécifié.
* **Nombre maximal de lignes :** limite le nombre total de lignes générées à partir de la source de données.
* **Lignes initiales :** définit le nombre de lignes qui apparaissent dans l’éditeur lors de la prévisualisation au moment de la conception.

>[!NOTE]
>
> La définition de **Lignes initiales** aux alentours de **3 à 5** offre un aperçu de mise en page plus réaliste avant l’application des données d’exécution.

## Fonctionnalités essentielles

* Liaison des données de colonne : liez chaque colonne à un champ dans le modèle de données.

* Contenu distribué : permet au tableau de se développer et de continuer sur plusieurs pages.

* Prise en charge des sauts de page : active les sauts de page au niveau des lignes dans le tableau.

* Nombre minimum de lignes : vérifie qu’un nombre minimum de lignes est rendu.

* Nombre maximal de lignes : limite le nombre total de lignes générées à partir de la source de données.

* Lignes initiales : définit les lignes par défaut affichées lors de la prévisualisation au moment de la conception.

La fonction Tableau dynamique de l’éditeur de communication interactive permet aux auteurs de créer des tableaux flexibles pilotés par les données sans avoir à écrire de code personnalisé. En liant le tableau à un tableau de données, en activant le contenu distribué, en autorisant des sauts de page et en configurant la validation des lignes, les auteurs peuvent produire des communications structurées qui s’adaptent facilement à différents volumes de données tout en conservant une disposition cohérente.
