---
title: Métadonnées JSON+ID
description: Découvrez comment activer et vérifier la fonctionnalité JSON+LD dans AEM CIF.
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: 547d3721-e094-4a42-8a7c-27e4ef97ea9c
index: false
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 5%

---


# Métadonnées JSON+ID {#json-ld}

Ce guide explique comment activer et vérifier la fonctionnalité JSON+LD dans AEM CIF.

>[!NOTE]
>
> Cette fonctionnalité est expérimentale.

## Activation de JSON+LD dans la configuration CIF {#enabling}

Par défaut, la case à cocher **Activer JSON+LD** n’est pas visible dans la configuration de CIF. Pour activer cette fonctionnalité, le projet doit inclure la configuration OSGi nécessaire, qui permet d’afficher la case à cocher. Cette configuration permet aux utilisateurs d’activer/désactiver la prise en charge des scripts JSON+LD sur les pages de produits.

Pour que la case à cocher **Activer JSON+LD** soit disponible dans la configuration CIF, ajoutez la configuration OSGi suivante à votre projet :

`com.adobe.cq.cif.components.models.JsonLdFeatureEnable`.

Pour plus d’informations sur l’ajout de cette configuration, reportez-vous à la section [Ajoute une configuration pour Json-Ld](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.cif.components.models.JsonLdFeatureEnable.cfg.json) dans le référentiel public aem-cif-guides-venia.

Une fois cette configuration ajoutée et déployée, la case à cocher devient visible dans les paramètres de configuration de CIF et voici les étapes pour activer **JSON+LD** :

1. Accédez à la configuration CIF dans AEM.
1. Annulez l’héritage.
1. Cochez la case **Activer JSON+LD**.
1. Enregistrez la configuration.

## Vérification de JSON+LD sur une page de détails du produit (PDP) {#verify}

Pour illustrer les étapes de vérification de JSON+LD, le projet Venia est utilisé comme exemple, où la configuration JSON+LD requise est déjà ajoutée pour activer la fonctionnalité. Procédez comme suit :

1. Accédez à votre instance AEM locale et ouvrez la page des détails du produit (PDP) : `http://localhost:4502/editor.html/content/venia/us/en/products/product-page.html`
1. Créez un produit sur la page Détails du produit (PDP).
1. Basculez vers le mode **Afficher comme publication**.
1. Ouvrez le **Source d’affichage de page** dans votre navigateur.
1. Recherchez JSON+ID dans la source de la page.

Si elle est configurée correctement, le script JSON+LD associé au produit injecté dans la page s’affiche.

## Exemple de structure JSON+LD pour un produit {#sample}

Vous trouverez ci-dessous un exemple de structure **JSON+LD** pour la jupe Agatha, créée sur la page PDP du projet Venia :

```html
<script type="application/ld+json">
{
  "@context": "http://schema.org",
  "@type": "Product",
  "sku": "VSK05",
  "name": "Agatha Skirt",
  "image": "https://mcstaging.catalogservice4commerce.fun/media/catalog/product/cache/926ea6fc2ad48a7202ff4587b6c2768e/v/s/vsk05-pe_main_2.jpg",
  "description": "The Agatha Skirt has a large circumference that lends itself to all sorts of drama...",
  "@id": "product-ef4fa1dc72",
  "offers": [
    {
      "@type": "Offer",
      "sku": "VSK05-KH-S",
      "url": "/content/venia/us/en/products/product-page.html/agatha-skirt.html",
      "priceCurrency": "USD",
      "price": 78.0
    },
    {
      "@type": "Offer",
      "sku": "VSK05-RN-XS",
      "availability": "InStock",
      "priceSpecification": {
        "@type": "UnitPriceSpecification",
        "priceType": "https://schema.org/ListPrice",
        "price": 18.0,
        "priceCurrency": "USD"
      },
      "price": 46.0
    }
  ]
}
</script>
```

## Mappage des attributs JSON+LD vers GraphQL {#mapping}

Les attributs JSON+LD peuvent être mappés aux requêtes GraphQL dans AEM CIF, ce qui garantit que les données structurées reflètent dynamiquement les informations sur les produits récupérées via GraphQL.

### Exemple de mappage de produit {#example}

| Attribut JSON+ID | Attribut Magento GraphQL | Obligatoire (O/N) |
|---------------------------------|-------------------|---|
| sku | sku | N |
| offers.url | Logique personnalisée | N |
| offers.SpecialPricedate | special_to_date | N |
| offers.sku | sku | N |
| offers.priceSpecification.priceCurrency | monnaie | Y |
| offers.priceSpecification.price | prix_normal | N |
| offers.priceCurrency | monnaie | Y |
| offers.price | special_price | Y |
| offers.image | media_galerie.url | N |
| offers.availability | stock_status | N |
| name | name | Y |
| image | media_galerie.url | Y |
| Description | Description | N |
| aggregateRating.reviewCount | review_count | N |
| aggregateRating.ratingValue | rating_summary | N |
| @id | id | N |

Ce mappage garantit que le script JSON+LD est renseigné dynamiquement en fonction des données de produit récupérées par le biais de requêtes GraphQL.

Pour tester votre structure JSON+LD, vous pouvez utiliser la console de recherche [Test avec résultats enrichis - Google.](https://search.google.com/test/rich-results/result?id=wtU3LVIEM8H7Aaf5qqK9qw) Cet outil fournit des commentaires détaillés, notamment sur la présence ou l’absence des attributs requis, et permet de s’assurer que vos données structurées sont correctement implémentées.
