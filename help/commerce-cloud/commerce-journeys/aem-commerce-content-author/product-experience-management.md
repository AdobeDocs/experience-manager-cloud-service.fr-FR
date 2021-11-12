---
title: Création d’expériences de produit
description: Découvrez comment créer des expériences produit.
source-git-commit: cadb903c08bd491db12c5d0ad24acc7f65396825
workflow-type: tm+mt
source-wordcount: '1155'
ht-degree: 1%

---

# Création d’expériences de produit {#building-experiences}

Découvrez comment gérer les expériences produit.

## Un peu d’histoire...  {#story-so-far}

Dans le document précédent du parcours Contenu et commerce AEM, [Gestion des expériences de catalogue de produits étape par étape](staged-catalog.md), vous avez appris à gérer des expériences de catalogue de produits intermédiaires.

## Objectif {#objective}

Ce document vous aide à comprendre comment créer du contenu et des expériences produit.

## Gestion de l’expérience du produit {#management}

La gestion de l’expérience du produit est la discipline pour décorer les données de produit (détenues par une solution PIM ou commerciale) avec du contenu marketing dans AEM. Ces données enrichies de produit avec du contenu peuvent ensuite être utilisées dans divers canaux pour créer une expérience d’achat immersive.

Dans AEM, vous pouvez créer différents types de contenu et les lier au catalogue de produits. Le contenu associé peut être facilement découvert et utilisé, ce qui entraîne une productivité élevée.

### Ressources {#assets}

À un niveau général, il existe deux types de ressources liées aux produits : produit et marketing. Les ressources de produit sont généralement gérées par des commerçants et se concentrent sur l’affichage du produit (principalement devant un arrière-plan neutre). Les ressources sont gérées dans la solution de commerce ou dans AEM Assets (avec une intégration Assets à la solution commerce/pim).

Les ressources marketing sont liées à la promotion et à l’utilisation du produit qui appartient généralement au marketing. Par exemple, plusieurs produits (&quot;shop the look&quot;), dans un contexte spécifique (&quot;collection d’automne en plein air&quot;) ou des fichiers PDF pratiques. CIF permet de lier facilement toute ressource AEM à un objet de catalogue de produits.

Ouvrez les propriétés de la ressource et passez à la propriété **Commerce** . Cet onglet vous permet de gérer l’association avec des produits. Le tableau sous le sélecteur fournit des informations supplémentaires sur les objets liés (visibles uniquement avec une sélection). Cliquez sur l’icône de détails pour obtenir une vue complète du cockpit du produit. Pour associer un nouvel objet, cliquez sur l’icône du sélecteur de produits (icône de dossier), sélectionnez un objet et fermez le sélecteur.

![ressources pem](assets/pem-assets.png)

### Fragments d’expérience {#experience-fragments}

Les fragments d’expérience sont un excellent moyen de créer du contenu de produit réutilisable ou individuel à grande échelle. L’association fonctionne de la même manière qu’une ressource. Ouvrez les propriétés et passez à la propriété **Commerce** . Cet onglet vous permet de gérer l’association avec les produits et les catégories. Les tableaux situés sous les sélecteurs fournissent des informations supplémentaires sur les objets liés (visibles uniquement avec une sélection). Cliquez sur l’icône de détails pour obtenir une vue complète du cockpit du produit. Pour associer un nouvel objet, cliquez sur l’icône du sélecteur de produits (icône de dossier), sélectionnez un objet et fermez le sélecteur.

![pem xf](assets/pem-xf.png)

### Fragments de contenu {#content-fragments}

Les fragments de contenu sont le meilleur type de contenu pour tout contenu structuré. Vous pouvez l’utiliser pour agrémenter les données de produit externes de données marketing supplémentaires ou pour créer du contenu sans interface. L’association d’un fragment de contenu à un objet de catalogue de produits se produit par le biais des types de référence de produit ou de catégorie dans l’éditeur de modèle de fragment de contenu. Il vous suffit de faire glisser et de déposer le type de référence droit sur le modèle et de configurer le champ. Ces types prennent en charge la sélection unique ou multiple.

![modèle pem cf](assets/pem-cf-model.png)

Si vous créez un fragment de contenu basé sur ce modèle, ces types de référence vous permettent de sélectionner facilement l’objet approprié à l’aide du sélecteur correspondant.

![pem cf](assets/pem-cf.png)

### Product Cockpit {#product-cockpit}

Nous avons introduit le cockpit du produit (ou la console) dans l’un des modules précédents. Le cockpit est un moyen facile non seulement de parcourir le catalogue de produits, mais aussi de voir tout le contenu AEM associé à un seul endroit. Accédez à la console du produit et ouvrez les propriétés d’un produit auquel est associé du contenu. Passez à l’onglet correspondant pour afficher le contenu associé.

![cockpit pem](assets/pem-cockpit.png)

Cliquez sur l’icône d’action pour ouvrir ce contenu dans un nouvel onglet du navigateur.

## Enrichissement de pages de produits et de catégories individuelles {#enrich}

Dans les modules précédents, vous avez appris à utiliser plusieurs modèles de catalogue de produits. Les modèles multiples sont un excellent moyen de créer des modèles différents, mais ils ne sont pas nécessaires dans de nombreux cas. Dans de nombreux cas, le même modèle peut être utilisé en combinaison avec des espaces réservés pour un contenu individuel. CIF prend en charge les espaces réservés pour les fragments de contenu et les fragments d’expérience.

Commençons par l’espace réservé du fragment d’expérience. Ouvrez un modèle de produit dans l’éditeur d’AEM. Faites glisser et déposez le **Fragment d’expérience de commerce** sur le modèle, puis ouvrez la boîte de dialogue de configuration.

![espace réservé pem](assets/pem-placeholder.png)

Ouvrez la boîte de dialogue du composant et saisissez un nom pour cet espace réservé. Le nom de l’espace réservé est requis et vous permet d’ajouter autant d’espaces réservés que nécessaire.

![boîte de dialogue pem XF](assets/pem-dialog-xf.png)

Ouvrez le fragment d’expérience que vous avez associé à un produit à l’étape précédente. Ouvrez les propriétés et accédez à l’onglet Commerce. Saisissez le même nom d’espace réservé sous **Emplacement de l’espace réservé du catalogue**.

![pem xf](assets/pem-xf.png)

Déposez maintenant le **Fragment de contenu commercial** sur le modèle, puis ouvrez la boîte de dialogue de configuration.

![boîte de dialogue pem CF](assets/pem-dialog-cf.png)

Cette boîte de dialogue réutilise la boîte de dialogue Fragment de contenu des composants principaux. Pour plus d’informations, voir Ressources supplémentaires. La seule différence est que **Elément Lien** qui configure le champ d’identifiant (SKU du produit ou UID de catégorie) dans le modèle de fragment de contenu.

Prévisualisez maintenant une page de produit qui est associée à un fragment de contenu et/ou un fragment d’expérience. AEM effectue une recherche pour chaque espace réservé en fonction du type (Contenu ou Fragment d’expérience), de l’identifiant et du nom de l’espace réservé des fragments d’expérience. AEM utilise un résolveur d’URL pour obtenir l’identifiant (SKU pour les produits, UID pour les catégories). Si une expérience ou un fragment de contenu est renvoyé, il est rendu à l’emplacement de l’espace réservé, sinon l’espace réservé est ignoré.

![résultat pem](assets/pem-result.png)

## Rendre le contenu Shoppable {#making-shoppable}

Il est également possible de rendre une page d’AEM standard Shoppable en ajoutant des composants commerciaux. Créez une page de contenu dans AEM et ouvrez la page vide dans l’éditeur.

![page vide pem](assets/pem-page-empty.png)

Tout d’abord, faites glisser et déposez un composant Détails du produit sur la page. Passez ensuite à la barre latérale Ressources, passez à Produits et sélectionnez un produit. Faites glisser et déposez ce produit sur le composant de produit. Un composant de produit standard s’affiche alors sur une page de contenu.

![page produit pem](assets/pem-page-product.png)

Si vous avez créé du contenu associé pour ce produit, basculez dans la barre latérale Ressources sur **Contenu commercial associé**. Cet onglet vous présente tous AEM contenu associé à ce produit. Cela vous permet désormais d’embellir rapidement les pages avec tout contenu associé.

![page enrichie pem](assets/pem-page-enriched.png)

## Fin du Parcours ? {#end-of-journey}

Félicitations ! Vous avez terminé le parcours du développeur de contenu et de commerce d’AEM ! Vous devez maintenant :

* comprendre comment associer n’importe quel contenu AEM à des objets de catalogue de produits ;
* utiliser des espaces réservés pour enrichir individuellement les pages de produits et de catégories ;
* savoir comment rendre le contenu Shoppable et utiliser l’onglet de contenu associé ;

Vous êtes maintenant prêt à gérer les expériences de produits à l’aide d’AEM Content and Commerce. Toutefois, AEM contenu et commerce disposent de nombreuses options supplémentaires. Extrayez certaines des ressources supplémentaires disponibles dans le [Section Ressources supplémentaires](#additional-resources) pour en savoir plus sur les fonctionnalités que vous avez vues dans ce parcours.

## Ressources supplémentaires {#additional-resources}

* [Création d’expériences commerciales](/help/commerce-cloud/authoring/authoring-commerce-experiences.md)
* [Product Cockpit](/help/commerce-cloud/authoring/product-cockpit.md)
* [Composant Fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=en)
