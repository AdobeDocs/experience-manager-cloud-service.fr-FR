---
title: Configurations d’URL avancées
description: Découvrez comment personnaliser les URL des pages de produits et de catégories. Cela permet aux implémentations d’optimiser les URL pour les moteurs de recherche et de promouvoir la découverte.
sub-product: Commerce
version: cloud-service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7,363cb465-c50a-422f-b149-b3f41c2ebc0f
source-git-commit: c956aab4dbbbb7daede3e115616ae923f7a68b90
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 97%

---

# Configurations d’URL avancées {#url}

>[!NOTE]
>
> L’optimisation pour les moteurs de recherche est devenue une préoccupation essentielle pour de nombreux spécialistes du marketing. Par conséquent, l’optimisation pour les moteurs de recherche doit être prise en compte dans de nombreux projets Adobe Experience Manager (AEM) as a Cloud Service. Veuillez lire [Bonnes pratiques de gestion des URL et de l’optimisation pour les moteurs de recherche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/seo-and-url-management.html) pour plus d’informations.

Les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) fournissent des configurations avancées pour personnaliser les URL des pages de produits et de catégories. De nombreuses mises en œuvre personnalisent ces URL à des fins d’optimisation du moteur de recherche (SEO). La vidéo suivante explique comment configurer les services et les fonctionnalités `UrlProvider` du [mappage Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) pour personnaliser les URL des pages de produits et de catégories.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuration {#configuration}

Pour configurer le service `UrlProvider` en fonction des exigences SEO et des besoins, un projet doit fournir une configuration OSGI pour la « configuration du fournisseur d’URL CIF ».

>[!NOTE]
>
> Depuis la version 2.0.0 des composants principaux CIF d’AEM, la configuration du fournisseur d’URL fournit uniquement des formats d’URL prédéfinis, au lieu des formats configurables en texte libre connus des versions 1.x. De plus, l’utilisation de sélecteurs pour transmettre des données dans des URL a été remplacée par des suffixes.

### Format d’URL de page de produits {#product}

Celui-ci configure les URL des pages de produits et prend en charge les options suivantes :

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (par défaut)
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`

Dans le cas du [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) :

* `{{page}}` sera remplacé par `/content/venia/us/en/products/product-page`
* `{{sku}}` sera remplacé par le SKU du produit, par exemple `VP09`
* `{{url_key}}` sera remplacé par la propriété `url_key` du produit, par exemple `lenora-crochet-shorts`
* `{{url_path}}` sera remplacé par le `url_path` du produit, par exemple `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` sera remplacé par la variante actuellement sélectionnée, par exemple `VP09-KH-S`

Avec les données d’exemple ci-dessus, une URL de variante de produit formatée à l’aide du format d’URL par défaut ressemblera à `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### Format d’URL de page de catégorie {#product-list}

Celui-ci configure les URL des pages de listes de catégories ou de produits et prend en charge les options suivantes :

* `{{page}}.html/{{url_path}}.html` (par défaut)
* `{{page}}.html/{{url_key}}.html`

Dans le cas du [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) :

* `{{page}}` sera remplacé par `/content/venia/us/en/products/category-page`
* `{{url_key}}` sera remplacé par la propriété `url_key` de la catégorie.
* `{{url_path}}` sera remplacé par le `url_path` de la catégorie

Avec les données d’exemple ci-dessus, une URL de page de catégorie formatée à l’aide du format d’URL par défaut ressemblera à `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`.

>[!NOTE]
> 
> `url_path` est une concaténation de `url_keys` des ancêtres d’un produit ou d’une catégorie et de `url_key` du produit ou de la catégorie séparés par une barre oblique `/`.

## Formats d’URL personnalisés {#custom-url-format}

Pour fournir un format d’URL personnalisé, un projet peut implémenter l’interface [`UrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/UrlFormat.html) et enregistrer l’implémentation comme service OSGI, en l’utilisant comme page de catégorie ou format d’URL de page de produit. La propriété de service `UrlFormat#PROP_USE_AS` indique lequel des formats prédéfinis configurés à remplacer :

* `useAs=productPageUrlFormat`, remplacera le format d’URL de page de produit configuré.
* `useAs=categoryPageUrlFormat`, remplacera le format d’URL de page de catégorie configuré.

S’il existe plusieurs mises en œuvre de `UrlFormat` enregistrées en tant que services OSGI, celle qui a le rang de service supérieur remplace celle qui a le rang de service inférieur.

`UrlFormat` doit mettre en œuvre une paire de méthodes pour créer une URL à partir d’un mappage de paramètres donné et analyser une URL pour renvoyer le même Mappage de paramètres. Les paramètres sont identiques à ceux décrits ci-dessus. Seul le paramètre `{{uid}}` supplémentaire est fourni au `UrlFormat` pour les catégories.

## Combinaison avec des mappages Sling {#sling-mapping}

En plus du `UrlProvider`, il est également possible de configurer des [mappages Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) afin de réécrire et de traiter les URL. Le projet AEM Archetype fournit également [un exemple de configuration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) afin de configurer des mappages Sling pour le port 4503 (publication) et 80 (Dispatcher).

## Combinaison avec AEM Dispatcher {#dispatcher}

Les réécritures d’URL peuvent également être archivées en utilisant le serveur HTTP AEM Dispatcher avec le module `mod_rewrite`. L’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) fournit une configuration de Dispatcher AEM de référence qui inclut déjà des [règles de réécriture](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) de base pour la taille générée.

## Exemple

Le projet de [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) comprend des exemples de configuration afin de démontrer l’utilisation d’URL personnalisées pour les pages de produits et de catégories. Cela permet à chaque projet de configurer des modèles d’URL individuels pour les pages de produits et de catégories en fonction de leurs besoins SEO. Une combinaison de mappages `UrlProvider` et Sling CIF telle que décrite ci-dessus est utilisée.

>[!NOTE]
>
>Cette configuration doit être ajustée avec le domaine externe utilisé par le projet. Les mappages Sling fonctionnent en fonction du nom d’hôte et du domaine. Par conséquent, cette configuration est désactivée par défaut et doit être activée avant le déploiement. Pour ce faire, renommez le dossier `hostname.adobeaemcloud.com` de mappage Sling dans `ui.content/src/main/content/jcr_root/etc/map.publish/https` en fonction du nom de domaine utilisé et activez cette configuration en ajoutant `resource.resolver.map.location="/etc/map.publish"` à la configuration `JcrResourceResolver` du projet.

## Ressources supplémentaires

* [Magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia)
* [Mappage des ressources AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=fr)
* [Mappages Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
