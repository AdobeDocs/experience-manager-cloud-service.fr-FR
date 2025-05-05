---
title: Attributs personnalisés pour le carrousel de produit CIF
description: Découvrez comment étendre le composant AEM Carrousel de produit CIF en mettant à jour le modèle Sling et en personnalisant le balisage.
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 594f0e6ec88851c86134be8d5d7f1719f74ddf4f
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 4%

---

# Attributs personnalisés pour le carrousel de produit CIF {#product-carousel}

## Présentation {#intro}

Le composant du carrousel de produit est étendu tout au long de ce tutoriel. Pour commencer, ajoutez une instance du carrousel de produit à la page d’accueil afin de comprendre les fonctionnalités de base :

1. Accédez à la page d’accueil du site, par exemple [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)
1. Insérez un nouveau composant du carrousel de produit dans le conteneur de mises en page principal de la page.
   ![Composant du carrousel de produit](/help/commerce-cloud/assets/product-carousel-component.png)
1. Développez le panneau latéral (s’il n’est pas déjà activé) et basculez la liste déroulante de l’outil de recherche de ressources sur **Produits**.
     ![Produits du carrousel](/help/commerce-cloud/assets/carousel-products.png)    
1. Cela doit afficher une liste des produits disponibles à partir d’une instance Adobe Commerce connectée.
   ![Instance connectée](/help/commerce-cloud/assets/connected-instance.png)
1. Les produits s’affichent comme ci-dessous avec les propriétés par défaut :
   ![Produit affiché avec propriétés](/help/commerce-cloud/assets/discount.png)

## Mise à jour du modèle Sling {#update-sling-model}

Vous pouvez étendre la logique métier du carrousel de produit en mettant en oeuvre un modèle Sling :

1. Dans votre IDE, accédez à `core/src/main/java/com/venia/core/models/commerce` sous le module principal et créez une interface CustomCarousel qui étend l’interface CIF ProductCarousel :

   ```
   package com.venia.core.models.commerce;
   import com.adobe.cq.commerce.core.components.models.productcarousel.ProductCarousel;
   public interface CustomCarousel extends ProductCarousel {
   }
   ```

1. Créez ensuite une classe d’implémentation `CustomCarouselImpl.java` sur `core/src/main/java/com/venia/core/models/commerce/CustomCarouselImpl.java`.
Le motif de délégation des modèles Sling permet à `CustomCarouselImpl` de référencer le modèle `ProductCarousel` via la propriété `sling:resourceSuperType` :

   ```
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductCarousel productCarousel;
   ```

1. L’annotation @PostConstruct garantit que cette méthode est appelée lorsque le modèle Sling est initialisé. La requête GraphQL du produit a déjà été étendue à l’aide de la méthode extendedProductQueryWith pour récupérer les attributs. Mettez à jour la requête GraphQL pour inclure la variable  dans la requête partielle :

   ```
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

   Dans le code ci-dessus, `addCustomSimpleField` est utilisé pour récupérer l’attribut `accessory_gemstone_addon`.

## Personnalisation du balisage {#customize-markup}

Pour personnaliser davantage les balises :

1. Créez une copie de `productcard.html` de `/apps/core/cif/components/commerce/productcarousel/v1/productcarousel` (le chemin d’accès principal du composant) vers le module ui.apps `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productcarousel/productcard.html`.

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

1. Enregistrez les modifications et déployez les mises à jour vers AEM à l’aide de la commande Maven, à partir d’un terminal de ligne de commande. Vous pourrez voir la valeur de l’attribut personnalisé `accessory_gemstone_addon` pour les produits sélectionnés sur la page.
