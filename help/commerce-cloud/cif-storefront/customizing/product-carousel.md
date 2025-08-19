---
title: Attributs personnalisés pour le carrousel de produit CIF
description: Découvrez comment étendre le composant Carrousel de produit AEM CIF en mettant à jour le modèle Sling et en personnalisant les balises.
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: 758e0e13-c4d8-4d32-bcc9-91a36b3ffa98
index: false
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 5%

---


# Attributs personnalisés pour le carrousel de produit CIF {#product-carousel}

Découvrez comment étendre le composant Carrousel de produit AEM CIF en mettant à jour le modèle Sling et en personnalisant les balises.

## Présentation {#intro}

Le composant Carrousel de produit est étendu tout au long de ce tutoriel. Dans un premier temps, ajoutez une instance du carrousel de produit à la page d’accueil pour comprendre les fonctionnalités de base :

1. Accédez à la page d’accueil du site ; par exemple, [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)
1. Insérez un nouveau composant de carrousel de produit dans le conteneur de mises en page principal de la page.

   ![Composant du carrousel de produit](/help/commerce-cloud/cif-storefront/assets/product-carousel-component.png)

1. Développez le Panneau latéral (s’il n’est pas déjà basculé) et basculez la liste déroulante de l’outil de recherche de ressources sur **Produits**.

   ![Produits du carrousel](/help/commerce-cloud/cif-storefront/assets/carousel-products.png)

1. Cela devrait afficher la liste des produits disponibles à partir d’une instance Adobe Commerce connectée.

   ![Instance connectée](/help/commerce-cloud/cif-storefront/assets/connected-instance.png)

1. Les produits s’affichent comme ci-dessous avec les propriétés par défaut :

   ![Produit affiché avec les propriétés](/help/commerce-cloud/cif-storefront/assets/discount.png)

## Mettre à jour le modèle Sling {#update-sling-model}

Vous pouvez étendre la logique commerciale du carrousel de produit en implémentant un modèle Sling :

1. Dans votre IDE, accédez au module principal pour `core/src/main/java/com/venia/core/models/commerce` et créer une interface CustomCarousel qui étend l’interface ProductCarousel de CIF :

   ```text
   package com.venia.core.models.commerce;
   import com.adobe.cq.commerce.core.components.models.productcarousel.ProductCarousel;
   public interface CustomCarousel extends ProductCarousel {
   }
   ```

1. Créez ensuite un `CustomCarouselImpl.java` de classe d’implémentation dans `core/src/main/java/com/venia/core/models/commerce/CustomCarouselImpl.java`.

   Le modèle de délégation pour les modèles Sling `CustomCarouselImpl` permet de référencer `ProductCarousel` modèle via la propriété `sling:resourceSuperType` :

   ```text
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductCarousel productCarousel;
   ```

1. L’annotation `@PostConstruct` garantit que cette méthode est appelée lorsque le modèle Sling est initialisé. La requête de GraphQL de produit a déjà été étendue à l’aide de la méthode extendProductQueryWith pour récupérer les attributs. Mettez à jour la requête GraphQL pour inclure l’attribut dans la requête partielle :

   ```javascript
   @PostConstruct
   private void initModel() {
   productsRetriever = productCarousel.getProductsRetriever();
   
   if(productCarousel.getProductsRetriever() != null)
   productCarousel.getProductsRetriever().extendProductQueryWith(p -> p
   .createdAt()
   .addCustomSimpleField("accessory_gemstone_addon")
   );
   }
   ```

   Dans le code ci-dessus, le `addCustomSimpleField` est utilisé pour récupérer l’attribut `accessory_gemstone_addon`.

## Personnalisation du balisage {#customize-markup}

Pour personnaliser davantage les balises :

1. Créez une copie de `productcard.html` à partir de `/apps/core/cif/components/commerce/productcarousel/v1/productcarousel` (le chemin d’accès crxde des composants principaux) vers le module ui.apps `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productcarousel/productcard.html`.

1. Modifiez `productcard.html` pour appeler l’attribut personnalisé, qui est mentionné dans la classe d’implémentation :

   ```xml
   ..
   <div
       data-product-sku="${product.commerceIdentifier.value}"
       data-product-base-sku="${product.combinedSku.baseSku}"
       id="${product.id}"
       data-cmp-data-layer="${product.data.json}"
       class="card product__card">
       <span>${product.product.responseData['accessory_gemstone_addon']}</span>
       <a href="${product.URL}"
           target="${productCarousel.linkTarget}"
   ..
   ```

1. Enregistrez les modifications et déployez les mises à jour sur AEM à l’aide de votre commande Maven, à partir d’un terminal de ligne de commande. Vous pourrez voir la valeur de l’`accessory_gemstone_addon` d’attribut personnalisé pour les produits sélectionnés sur la page.
