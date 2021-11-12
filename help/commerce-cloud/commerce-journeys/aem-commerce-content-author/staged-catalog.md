---
title: Gestion des expériences de catalogue de produits étape par étape
description: Découvrez comment gérer des expériences de catalogue de produits étape par étape.
source-git-commit: a98d525512dcba790d002d6a4042558962c36c97
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# Création d’expériences de catalogue de produits étape par étape {#building-experiences}

Découvrez comment gérer des expériences de catalogue de produits étape par étape.

## Un peu d’histoire...  {#story-so-far}

Dans le document précédent du parcours Contenu et commerce AEM, [Gestion des pages et des modèles de catalogue de produits](catalog-templates.md), vous avez appris à gérer et à créer des expériences de catalogue de produits à partir de modèles.

Cet article s&#39;appuie sur ces principes fondamentaux.

## Objectif {#objective}

Ce document vous aide à comprendre comment gérer l’expérience du catalogue de produits en fonction des données de produits intermédiaires et des lancements AEM. Souvent, les auteurs doivent préparer en parallèle un lancement de produit à venir (comme une nouvelle collection de vêtements). Cela nécessite l’accès aux données de produit intermédiaire (pas encore actives) et la possibilité de préparer le contenu. Ce nouveau contenu sera mis en ligne avec le lancement du produit.

    >[!REMARQUE]
    >
    >Cette fonctionnalité est disponible uniquement avec Adobe Commerce ou Cloud Edition et les connecteurs tiers qui prennent en charge l’authentification par jeton. Voir [Prise en main](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content-and-commerce/storefront/getting-started.html) pour plus d’informations.

Tout d’abord, voyons comment les auteurs peuvent accéder aux données de produit intermédiaire avec CIF.

## Utilisation des données de produit intermédiaires {#staged-product-data}

L’utilisation du cockpit du produit constitue une méthode d’accès aux données de produit étape par étape. Ouvrez le catalogue de produits en cliquant sur l’icône Commerce dans le menu AEM principal. Vous aurez ainsi accès aux données de produit actives. Ouvrez l’onglet Filtre à gauche et développez **CATALOGUE ENREGISTRÉ**. Grâce aux données d’aperçu, vous pouvez désormais accéder aux données de produit intermédiaire à tout moment. Les données intermédiaires incluent de nouvelles catégories, de nouveaux produits ou des champs mis à jour comme le prix.

![cockpit](assets/staged-cockpit.png)

La prévisualisation d’un storefront avec des données intermédiaires est possible à l’aide de la vue timewarp. Ouvrez l’éditeur et basculez le mode sur Timewarp. Sélectionnez une date ultérieure. Notez les informations en haut de l’éditeur que vous affichez la page pour une certaine date.

![stage timewarp](assets/staged-timewarp.png)

Vous pouvez désormais parcourir le catalogue avec les données intermédiaires. Si vous ouvrez une page de catégorie ou de produit intermédiaire, l’éditeur affiche un indicateur visuel.

![plan](assets/staged-plp.png)

    >[!REMARQUE]
    >
    >L’omni-recherche n’a pas de contexte et ne renvoie donc que des données de catalogue de produits en direct.

## Lancements AEM {#launches}

AEM Lancements vous permet de créer du contenu pour les données de produits intermédiaires. Si vous ne connaissez pas les lancements, suivez le lien de la documentation sous la section [Section Ressources supplémentaires](#additional-resources). La date de lancement est ensuite utilisée pour accéder aux données de produit intermédiaire.

![lancement de l’étape](assets/staged-launch.png)

Notez que les sélecteurs respectent la date de lancement avec l’indicateur intermédiaire sur le côté droit.

![sélecteur d’étape](assets/staged-picker.png)

## Et après ? {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours, vous devez :

* comprendre les concepts du catalogue de produits étape par étape et du contenu avec Launches ;
* être en mesure d’accéder aux données du catalogue de produits étape par le biais du cockpit du produit et de l’éditeur ;

Vous êtes maintenant prêt à gérer [expériences produit](product-experience-management.md). Toutefois, AEM Content et Commerce disposent de nombreuses options supplémentaires. Extrayez certaines des ressources supplémentaires disponibles dans le [Section Ressources supplémentaires](#additional-resources) pour en savoir plus sur les fonctionnalités que vous avez vues dans ce parcours.

## Ressources supplémentaires {#additional-resources}

* [Product Cockpit](/help/commerce-cloud/authoring/product-cockpit.md)
* [Prise en main](/help/commerce-cloud/getting-started.md)
* [Lancements](/help/sites-cloud/authoring/launches/overview.md)
