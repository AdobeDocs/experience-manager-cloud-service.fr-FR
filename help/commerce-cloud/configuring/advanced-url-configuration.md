---
title: Configurations d’URL avancées
description: Configurations d’URL avancées
translation-type: tm+mt
source-git-commit: 3a235e3d8e2d97e413f445df1f0bfe52e97024b3
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 4%

---


# Configurations d’URL avancées {#url}

[AEM CIF Core Components](https://github.com/adobe/aem-core-cif-components) fournit des configurations avancées pour personnaliser les URL des pages de produits et de catégories. De nombreuses implémentations personnalisent ces URL à des fins d&#39;optimisation du référencement (SEO).  La vidéo suivante explique comment configurer le `UrlProvider` service et les fonctionnalités de la mise en correspondance [](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) Sling pour personnaliser les URL des pages de produits et de catégories.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuration {#configuration}

Pour configurer le `UrlProvider` service en fonction des exigences d’optimisation du référencement et des besoins, un projet doit fournir une configuration OSGI pour la configuration &quot;CIF URL Provider configuration&quot; et configurer le service comme décrit ci-dessous.

>[!NOTE]
>
> Le projet de magasin [de référence](https://github.com/adobe/aem-cif-guides-venia) Venia, voir ci-dessous, comprend des exemples de configuration pour démontrer l’utilisation d’URL personnalisées pour les pages de produits et de catégories.

### Modèle d’URL de page de produit {#product}

Cette opération configure les URL des pages de produits avec les propriétés suivantes :

* **Modèle** d’URL du produit : définit le format des URL avec un ensemble d’espaces réservés. La valeur par défaut est `{{page}}.{{url_key}}.html#{{variant_sku}}`, ce qui génère des URL, par exemple `/content/venia/us/en/products/product-page.chaz-kangeroo-hoodie.html#MH01-M-Orange` où
   * `{{page}}` a été remplacé par `/content/venia/us/en/products/product-page`
   * `{{url_key}}` a été remplacé par la propriété `url_key` du Magento du produit, ici `chaz-kangeroo-hoodie`
   * `{{variant_sku}}` a été remplacé par la variante actuellement sélectionnée, ici `MH01-M-Orange`
* **Emplacement** de l&#39;identifiant du produit : définit l’emplacement de l’identifiant qui sera utilisé pour récupérer les données du produit. La valeur par défaut est `SELECTOR`, l’autre valeur possible est `SUFFIX`. Dans l’exemple d’URL précédent, cela signifie que l’identifiant `chaz-kangeroo-hoodie` sera utilisé pour récupérer les données du produit.
* **Type** d&#39;identificateur de produit : définit le type de l’identifiant à utiliser lors de la récupération des données de produit. La valeur par défaut est `URL_KEY`, l’autre valeur possible est `SKU`. Avec l’exemple d’URL précédent, cela signifie que les données du produit seront récupérées avec un filtre GraphQL Magento comme `filter:{url_key:{eq:"chaz-kangeroo-hoodie"}}`.

### Modèle d’URL de la page liste de produits {#product-list}

Cette opération configure les URL des pages de catégorie ou de liste de produits avec les propriétés suivantes :

* **Modèle** d’URL de Catégorie : définit le format des URL avec un ensemble d’espaces réservés. La valeur par défaut est `{{page}}.{{id}}.html`, ce qui génère des URL, par exemple `/content/venia/us/en/products/category-page.3.html` où
   * `{{page}}` a été remplacé par `/content/venia/us/en/products/category-page`
   * `{{id}}` a été remplacé par la propriété `id` du Magento de la catégorie, ici `3`
* **Emplacement** de l&#39;identifiant de Catégorie : définit l’emplacement de l’identifiant qui sera utilisé pour récupérer les données du produit. La valeur par défaut est `SELECTOR`, l’autre valeur possible est `SUFFIX`. Dans l’exemple d’URL précédent, cela signifie que l’identifiant `3` sera utilisé pour récupérer les données du produit.
* **Type** d&#39;identificateur de Catégorie : définit le type de l’identifiant à utiliser lors de la récupération des données de produit. La valeur par défaut et actuellement la seule valeur prise en charge est `ID`. Avec l’exemple d’URL précédent, cela signifie que les données de catégorie seront extraites avec un filtre GraphQL Magento comme `category(id:3)`.

Il est possible d’ajouter des propriétés personnalisées pour chaque modèle, à condition que les données correspondantes soient définies par les composants qui utilisent le modèle `UrlProvider`. Vérifiez par exemple le code de la `ProductListItemImpl` classe pour savoir comment cela est implémenté.

Il est également possible de remplacer le `UrlProvider` service par un service OSGi entièrement personnalisé. Dans ce cas, il faut mettre en oeuvre l&#39; `UrlProvider` interface et l&#39;enregistrer avec un niveau de service supérieur afin de remplacer l&#39;implémentation par défaut.

## Combinaison avec des mappages Sling {#sling-mapping}

En plus de la `UrlProvider`, il est également possible de configurer des mappages [](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) Sling afin de réécrire et de traiter les URL. Le projet Archétype AEM fournit également [un exemple de configuration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) pour configurer quelques mappages Sling pour le port 4503 (publication) et 80 (répartiteur).

## Combiner avec AEM Dispatcher {#dispatcher}

Les réécritures d’URL peuvent également être enregistrées en utilisant AEM serveur HTTP Dispatcher avec `mod_rewrite` module. L&#39;archétype [de projet](https://github.com/adobe/aem-project-archetype) AEM fournit une configuration Dispatcher de référence qui inclut déjà des règles [de](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) réécriture de base pour la taille générée.

## Exemple

Le projet de magasin [de référence](https://github.com/adobe/aem-cif-guides-venia) Venia comprend des exemples de configurations pour démontrer l’utilisation d’URL personnalisées pour les pages de produits et de catégories. Cela permet à chaque projet de configurer des modèles d’URL individuels pour les pages de produits et de catégories en fonction de leurs besoins en termes d’optimisation du référencement. Une combinaison de mappages CIF `UrlProvider` et Sling décrite ci-dessus est utilisée.

>[!NOTE]
>
>Cette configuration doit être ajustée avec le domaine externe utilisé par le projet. Les mappages Sling fonctionnent en fonction du nom d’hôte et du domaine. Par conséquent, cette configuration est désactivée par défaut et doit être activée avant le déploiement. Pour ce faire, renommez le `hostname.adobeaemcloud.com` dossier de mappage Sling en `ui.content/src/main/content/jcr_root/etc/map.publish/https` fonction du nom de domaine utilisé et activez cette configuration en ajoutant `resource.resolver.map.location="/etc/map.publish"` à la `JcrResourceResolver` configuration du projet.

## Ressources supplémentaires

* [Magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia)
* [Mappage des ressources AEM](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Correspondances Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
