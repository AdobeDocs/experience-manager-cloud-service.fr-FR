---
title: Cockpit de produits
description: Découvrez comment utiliser le cockpit de produits, qui fournit un aperçu unifié des catalogues de produits liés et du contenu associé.
exl-id: 6dbf039c-e040-48f1-88f3-ebbd70cdf94d
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 95%

---

# Console du produit {#product-cockpit}

## Vue d’ensemble {#overview}

Le cockpit de produits fournit une vue d’ensemble unifiée des catalogues de produits liés et du contenu associé. Tous les contenus associés comportent des liens pour y accéder rapidement à partir du cockpit.

Les données des produits intermédiaires incluent toute mutation future telle que de nouvelles catégories, de nouveaux produits ou des propriétés mises à jour.

>[!NOTE]
>
>Le terme catalogue de produits est interchangeable avec magasin Commerce, vue de magasin et autres expressions similaires.

## Configuration {#configuration}

Les catalogues de produits doivent être configurés dans AEM. Pour plus d’informations, consultez la section [Configurer un magasin et des catalogues](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/storefront/getting-started.html?lang=fr#catalog).

L’activation des fonctionnalités de catalogue intermédiaire nécessite une authentification. Pour plus d’informations, consultez la section [Prise en main](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/storefront/getting-started.html?lang=fr).

>[!NOTE]
>
>Les fonctionnalités de catalogue intermédiaire ne sont disponibles qu’avec Adobe Commerce et les connecteurs tiers qui prennent en charge l’authentification basée sur les jetons.

## Ouvrir le cockpit de produits {#opening-product-cockpit}

Le moyen le plus simple d’accéder au cockpit de produits est via le menu « Commerce » dans le menu principal d’AEM. Il est également possible d’utiliser l’omni-recherche (pour rechercher Commerce) ou d’ouvrir `https://<yourAEMInstance>/commerce.html`.

![Menu AEM](../assets/aem-menu.png)

## Naviguer dans les catalogues de produits {#browsing-product-catalogs}

Le cockpit de produits est organisé de manière hiérarchique selon la structure du catalogue de produits. Le premier niveau affiche le niveau racine du catalogue de tous les catalogues de produits configurés, y compris les métadonnées du serveur principal de Commerce.

![Catalogues configurés](../assets/catalog-overview.png)

Cliquez sur une catégorie pour charger les enfants de la catégorie sur laquelle vous avez cliqué.

![Enfants de catégorie](../assets/catalog-category-children.png)

Cliquez sur un produit pour charger les variations du produit si elles sont disponibles.

![Variations de produit](../assets/catalog-product-variation.png)

>[!NOTE]
>
>Les données du catalogue de produits dans AEM sont des données récupérées en temps réel via le point d’entrée de commerce configuré. Aucune donnée de catalogue de produits n’est stockée dans AEM.

## Effectuer une recherche dans les catalogues de produits {#searching-product-catalog}

Une recherche en texte intégral sur le catalogue de produits complet est proposée dans l’onglet de filtre de gauche pour rechercher rapidement des produits.

![recherche](../assets/search-cockpit.png)

## Naviguer dans le catalogue de produits intermédiaires {#staged-product-catalogs}

Par défaut, le cockpit de produits affiche les données du catalogue de produits actives. L’utilisation de l’option « CATALOGUE INTERMÉDIAIRE » dans l’onglet de filtre de gauche charge le catalogue de produits pour toute date sélectionnée.

![catalogue intermédiaire](../assets/staged-cockpit.png)

## Propriétés du catalogue de produits {#catalog-properties}

Cliquez sur l’icône des propriétés d’un produit ou d’une catégorie pour ouvrir l’affichage des propriétés de l’objet sélectionné. Ouvrir les propriétés d’une variante de produit revient à ouvrir les propriétés du produit principal.

### Onglets Commerce {#tabs}

Les onglets Général et Variante affichent les propriétés commerciales prédéfinies provenant du serveur principal de Commerce. Ces données (y compris les variantes) est en lecture seule dans AEM, car le système d’enregistrement est le serveur principal de Commerce. L’onglet Variante ne s’affiche que pour les produits comportant des variantes et présente une liste de toutes les variantes.

![propriétés de catalogue](../assets/catalog-properties.png)

### Onglets AEM Content {#content-tabs}

Ces onglets, regroupés par type de contenu AEM (Fragments d’expérience, Fragments de contenu, Ressources associées), affichent le contenu AEM associé à l’objet commercial. L’action « Afficher les détails » ouvre un nouvel onglet de navigateur avec le contenu sélectionné.

![propriétés de contenu](../assets/content-properties.png)
