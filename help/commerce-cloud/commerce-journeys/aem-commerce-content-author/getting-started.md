---
title: Prise en main de la création CIF
description: Prise en main de la création CIF
source-git-commit: e497b5b4439cf91ec7ea698d9bedcb4210802414
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 1%

---

# Prise en main de la création AEM CIF {#getting-started}

Découvrez AEM création CIF.

## Un peu d’histoire...  {#story-so-far}

Dans le document précédent de ce parcours de contenu et de commerce AEM, [En savoir plus sur AEM Content and Commerce](/help/commerce-cloud/introduction.md), vous avez appris la théorie de base de ce qu’est un CMS sans interface et vous devez maintenant comprendre les concepts de base d’AEM Content and Commerce.

Cet article s&#39;appuie sur ces principes fondamentaux.

## Objectif {#objective}

Ce document vous aide à comprendre comment utiliser CIF pour la création spécifique à Content and Commerce. Après lecture, vous devez :

* Présentation des concepts de création CIF à l’aide d’Universal Editor
* Accès aux données du catalogue de produits dans AEM à l’aide de sélecteurs de produits et de catégories
* Comment accéder aux données de contenu et de commerce à l’aide du cockpit du produit et de l’omni-recherche AEM

## Création CIF dans l’éditeur universel {#cif-authoring}

CIF étend l’éditeur universel avec des fonctionnalités permettant d’accéder aux données de produit en temps réel sans quitter le contexte :

Ouvrez le panneau latéral et sélectionnez &quot;Produits&quot; dans la liste déroulante.
![Sélectionner le type de produit](assets/asset-finder-overview.png)

Vous pouvez parcourir le catalogue de produits ou utiliser le champ de recherche de texte intégral pour rechercher des produits.
![type de produit](assets/asset-finder-search.png)

Les produits peuvent être déposés sur des composants qui prennent en charge les pertes de produits (par exemple, le teaser de produit, le carrousel de produit) directement sur la page qui crée automatiquement un composant de teaser de produit.

## Sélecteurs de produits et de catégories {#pickers}

Si des données de produit et de catégorie sont requises dans les composants commerciaux ou les boîtes de dialogue AEM back-office, AEM auteurs peuvent utiliser des sélecteurs qui sont des éléments de l’interface utilisateur pour rechercher et sélectionner facilement des données de catalogue de produits.

### Sélecteur de produits

Cliquez sur l’icône de dossier pour ouvrir l’interface utilisateur modale du sélecteur (par exemple, le teaser de produit).
![sélecteur de produits](assets/product-picker-open.png)

Les produits peuvent être trouvés en parcourant la structure du catalogue sur la gauche ou en effectuant une recherche. La recherche en texte intégral respecte la catégorie sélectionnée et limite les résultats de la recherche à cette catégorie.
![dossier de sélecteur de produits](assets/product-picker-folders.png)

Les produits avec des variations sont marqués par une icône de dossier sur laquelle vous pouvez cliquer pour afficher toutes les variations.
![variantes du sélecteur de produits](assets/product-picker-variants.png)
![les variantes du sélecteur de produits s’ouvrent](assets/product-picker-variants-open.png)

### Sélecteur de catégories

Fonctionne comme un sélecteur de produits. Cliquez sur l’icône de dossier pour ouvrir l’interface utilisateur modale du sélecteur (carrousel de catégorie, par exemple).
![sélecteur de catégorie](assets/category-picker-open.png)

Parcourez la structure du catalogue à gauche et sélectionnez la catégorie.
![sélecteur de catégorie](assets/category-picker-folders.png)

## Product Cockpit {#cockpit}

Le cockpit du produit est un endroit central pour accéder rapidement au catalogue de produits avec tout son contenu enrichi. Dans l’un des modules suivants, vous apprendrez à enrichir les données de produit avec du contenu. Pour l’instant, concentrons-nous sur l’accès aux données de produit.

Dans le menu principal, cliquez sur Commerce pour afficher la liste de tous les catalogues de produits associés.
![élément de menu Commerce](assets/commerce-menu-item.png)

Vous affichez ainsi une liste de tous les catalogues de produits connectés.
![catalogues intégrés du cockpit](assets/cockpit-Integrated-catalogs.png)

Le catalogue de produits affiche par défaut toutes les catégories de premier niveau avec tous les produits. Cliquer sur une catégorie ouvre cette catégorie avec tous les produits et sous-catégories associés, y compris leurs produits.
![catalogue de produits cockpit](assets/cockpit-product-catalog.png)

Vous pouvez ouvrir les propriétés du produit en cliquant sur l’icône de propriété. L’icône s’affiche en pointant sur une mosaïque de produit.
![Propriétés du produit cockpit](assets/cockpit-properties.png)

Toutes les propriétés du produit sont en lecture seule, car les données sont chargées en temps réel à partir du serveur principal connecté. La modification des propriétés du produit doit être effectuée dans le système principal qui est le système d’enregistrement. Onglet **Variantes** s’affiche uniquement si le produit comporte des variations. Cliquez sur l’onglet pour afficher toutes les variations avec leurs attributs.
![variantes du produit cockpit](assets/cockpit-properties-variants.png)

Les onglets restants affichent tout le contenu AEM associé au produit. Ces onglets seront discutés dans l’un des modules suivants.

## AEM Omnisearch {#omnisearch}

L’utilisation de l’omni-recherche est un moyen facile de trouver AEM contenu à l’aide de la recherche de texte intégral. CIF étend l’omni-recherche à la recherche de texte intégral de catalogues de produits avec son contenu d’AEM associé.
![élément de menu Commerce](assets/omnisearch.png)

Omnisearch exécute une recherche de texte intégral dans le serveur principal du commerce pour trouver tous les produits associés. Le résultat est répertorié sous **Afficher tous les produits**. L’omni-recherche recherche recherche également AEM contenu associé au produit recherché. Les résultats seront répertoriés sous les catégories AEM respectives. Dans cet exemple, un fragment de contenu est lié au produit.

## Et après ? {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours, vous devez :

* Présentation des concepts de création CIF à l’aide d’Universal Editor
* Accès au catalogue de produits dans AEM à l’aide des sélecteurs de produits et de catégories
* Comment accéder aux données de contenu et de commerce à l’aide du cockpit du produit et de l’omni-recherche AEM

Tirez parti de ces connaissances et poursuivez votre parcours en consultant le document. [Gestion des pages et des modèles de catalogue de produits](catalog-templates.md), où vous apprendrez à créer et personnaliser votre première expérience de catalogue de produits.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours en consultant le document [Gestion des pages et des modèles de catalogue de produits](catalog-templates.md), voici quelques autres ressources facultatives qui approfondissent certains concepts mentionnés dans ce document, mais qui ne sont pas nécessaires pour continuer sur le parcours.

* [Configuration de magasins et de catalogues](/help/commerce-cloud/getting-started.md#catalog)
