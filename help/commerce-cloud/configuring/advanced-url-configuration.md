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
source-git-commit: 8c3a1366d076c009262eeab8129e4e589dc4f7c5
workflow-type: tm+mt
source-wordcount: '2046'
ht-degree: 29%

---

# Configurations d’URL avancées {#url}

>[!NOTE]
>
> L’optimisation pour les moteurs de recherche est devenue une préoccupation essentielle pour de nombreux spécialistes du marketing. Par conséquent, l’optimisation pour les moteurs de recherche doit être prise en compte dans de nombreux projets Adobe Experience Manager (AEM) as a Cloud Service. Consultez les [Bonnes pratiques de gestion des URL et de l’optimisation pour les moteurs de recherche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/seo-and-url-management.html?lang=fr) pour plus d’informations.

Les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) fournissent des configurations avancées pour personnaliser les URL des pages de produits et de catégories. De nombreuses mises en œuvre personnalisent ces URL à des fins d’optimisation du moteur de recherche (SEO). La vidéo suivante explique comment configurer les services et les fonctionnalités `UrlProvider` du [mappage Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) pour personnaliser les URL des pages de produits et de catégories.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuration {#configuration}

Pour configurer la variable `UrlProvider` Le service en fonction des exigences d’optimisation pour les moteurs de recherche et a besoin d’un projet doit fournir une configuration OSGI pour le _Configuration du fournisseur d’URL CIF_.

>[!NOTE]
>
> Depuis la version 2.0.0 des composants principaux CIF AEM, la configuration du fournisseur d’URL fournit uniquement des formats d’URL prédéfinis, au lieu des formats de texte libre configurables connus des versions 1.x. De plus, l’utilisation de sélecteurs pour transmettre des données dans des URL a été remplacée par des suffixes.

### Format d’URL de page de produits {#product}

Celui-ci configure les URL des pages de produits et prend en charge les options suivantes :

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (par défaut)
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`

Dans le cas du [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) :

* `{{page}}` sera remplacé par `/content/venia/us/en/products/product-page`
* `{{sku}}` sera remplacé par le SKU du produit, par exemple `VP09`
* `{{url_key}}` sera remplacé par la propriété `url_key` du produit, par exemple `lenora-crochet-shorts`
* `{{url_path}}` sera remplacé par le `url_path` du produit, par exemple `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` sera remplacé par la variante actuellement sélectionnée, par exemple `VP09-KH-S`

Depuis la variable `url_path` obsolètes, les formats d’URL de produit prédéfinis utilisent la variable `url_rewrites` et sélectionnez celle qui contient le plus de segments de chemin comme alternative si la variable `url_path` n’est pas disponible.

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
> `url_path` est une concaténation de `url_keys` des ancêtres d’un produit ou d’une catégorie et de `url_key` du produit ou de la catégorie séparés par une barre oblique `/`. Chaque `url_key` est considéré comme unique dans un magasin donné.

### Configuration spécifique au magasin {#store-specific-urlformats}

Formats d’URL de catégorie et de page de produits à l’échelle du système définis par la variable _Configuration du fournisseur d’URL CIF_ peut être modifié pour chaque magasin.

Dans la configuration CIF, un éditeur peut sélectionner un autre format d’URL de page de catégorie ou de produit. Si rien n’est sélectionné, l’implémentation revient à la configuration à l’échelle du système.

La modification du format d’URL d’un site web actif peut avoir un impact négatif sur le trafic organique de votre site. Reportez-vous à la section [Bonnes pratiques](#best-practices) ci-dessous et planifiez soigneusement le changement du format de l&#39;URL à l&#39;avance.

![Formats d’URL dans la configuration CIF](assets/store-specific-url-formats.png)

>[!NOTE]
>
> La configuration spécifique au magasin des formats d’URL nécessite [Composants principaux CIF 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) et la dernière version du module complémentaire Adobe Experience Manager Content and Commerce.

## URL de produit prenant en compte les catégories {#context-aware-pdps}

Comme il est possible de coder des informations de catégorie dans une URL de produit, les produits qui se trouvent dans plusieurs catégories peuvent également être adressés avec plusieurs URL de produit.

Dans la configuration par défaut, les formats d’URL par défaut sélectionnent l’une des alternatives possibles à l’aide du schéma suivant :

* si la variable `url_path` est défini par le serveur principal de commerce électronique qui l’utilise (obsolète).
* de la `url_rewrites` utiliser les URL qui se terminent par le `url_key` comme alternatives
* de ces alternatives utilisent celle qui contient le plus de segments de chemin.
* s’il y en a plusieurs, prenez la première dans l’ordre indiqué par le serveur principal de commerce électronique.

Ce schéma sélectionne la variable `url_path` qui a le plus d’ancêtres, en partant du principe qu’une catégorie enfant est plus spécifique que sa catégorie parent. Ainsi sélectionné `url_path` est considéré _canonique_ et sera toujours utilisé pour le lien canonique sur les pages de produits ou dans le plan de site du produit.

Cependant, lorsqu’un acheteur navigue d’une page de catégorie à une page de produit ou d’une page de produit à une autre page de produit associée dans la même catégorie, il est utile de conserver le contexte de catégorie actuel. Dans ce cas, la variable `url_path` la sélection doit préférer les alternatives qui se trouvent dans le contexte de catégorie actuel plutôt que le _canonique_ sélection décrite ci-dessus.

Cette fonctionnalité doit être activée dans la variable _Configuration du fournisseur d’URL CIF_. Si cette option est activée, la sélection obtient un score d’alternative plus élevé, lorsque

* elles correspondent à des parties d’une catégorie donnée `url_paths` depuis le début (correspondance approximative des préfixes)
* ou correspondent à une catégorie donnée `url_key` n’importe où (correspondance partielle exacte)

Prenons l’exemple de la réponse pour un [requête products](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) ci-dessous. Étant donné que l’utilisateur se trouve sur la page de catégorie &quot;Nouveaux produits/Nouveaux produits en été 2022&quot; et que le magasin utilise le format d’URL de la page de catégorie par défaut, l’alternative &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot; correspondrait à 2 des segments de chemin du contexte dès le début : &quot;nouveaux-produits&quot; et &quot;nouveaux-en-été-2022&quot;. Si le magasin utilise un format d’URL de page de catégorie contenant uniquement le `url_key`, la même alternative est toujours sélectionnée, car elle correspond à la variable `url_key` n’importe où. Dans les deux cas, l’URL de la page de produits est créée pour &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;. `url_path`.

```
{
  "data": {
    "products": {
      "items": [
        {
          "sku": "VA18-GO-NA",
          "url_key": "gold-cirque-earrings",
          "url_rewrites": [
            {
              "url": "gold-cirque-earrings.html"
            },
            {
              "url": "venia-accessories/gold-cirque-earrings.html"
            },
            {
              "url": "venia-accessories/venia-jewelry/gold-cirque-earrings.html"
            },
            {
              "url": "new-products/gold-cirque-earrings.html"
            },
            {
              "url": "new-products/new-in-summer-2022/gold-cirque-earrings.html"
            }
          ]
        }
      ]
    }
  }
}
```

>[!NOTE]
>
> Les URL de produit prenant en compte les catégories requises [Composants principaux CIF 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) ou plus récent.

## Catégories spécifiques et pages de produits {#specific-pages}

Il est possible de créer des [pages de catégories et de produits multiples](../authoring/multi-template-usage.md) pour un sous-ensemble spécifique de catégories ou de produits d’un catalogue.

### Critères de sélection {#specific-pages-selection}

La sélection d’une page de catégorie spécifique est directe, en fonction du `url_path` ou `url_key`. La correspondance de sous-catégories n’est prise en charge que pour les formats d’URL contenant la catégorie complète `url_path`. Sinon, seule une correspondance exacte de la variable `url_key` est possible.

Les pages de produit spécifiques sont sélectionnées par le SKU ou la catégorie du produit. La version ultérieure nécessite que certaines informations de catégorie soient codées dans l’URL du produit. Cette option n’est disponible que pour certains formats d’URL par défaut. Reportez-vous au tableau ci-dessous pour une comparaison du format d’URL qui prend en charge la sélection de pages par SKU ou catégorie.


| Format d’URL | par sku | par catégorie |
| ----------------------------------------------------- | ------ | ---------------- |
| `{{page}}.html/{{url_key}}.html` | non | non |
| `{{page}}.html/{{category}}/{{url_key}}.html` | non | correspondance exacte uniquement |
| `{{page}}.html/{{url_path}}.html` | non | yes |
| `{{page}}.html/{{sku}}.html` | oui | non |
| `{{page}}.html/{{sku}}/{{url_key}}.html` | oui | non |
| `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html` | oui | correspondance exacte uniquement |
| `{{page}}.html/{{sku}}/{{url_path}}.html` | oui | oui |

{style=&quot;table-layout:auto&quot;}

>[!NOTE]
>
> La sélection de pages de produits spécifiques par catégorie nécessite [Composants principaux CIF 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) ou plus récent.

### Lien profond {#specific-pages-deep-linking}

Le `UrlProvider` est préconfiguré pour générer des liens profonds vers des pages de catégories et de produits spécifiques sur des instances de niveau auteur. Cela s’avère utile pour les éditeurs qui parcourent un site en mode Aperçu, accèdent à une page de produit ou de catégorie spécifique et passent en mode d’édition pour modifier la page.

En revanche, sur les instances de niveau publication, les URL de page de catalogue doivent rester stables pour ne pas perdre, par exemple, les gains sur les classements des moteurs de recherche. En raison de cette situation, les instances de niveau publication n’afficheront pas par défaut les liens profonds vers des pages de catalogue spécifiques. Pour modifier ce comportement, la variable _Stratégie de page spécifique au fournisseur d’URL CIF_ peut être configuré pour toujours générer des URL de page spécifiques.

## Personnalisations {#customization}

### Formats d’URL personnalisés {#custom-url-format}

Pour fournir un format d’URL personnalisé, un projet peut mettre en oeuvre l’une ou l’autre des options [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) ou le [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) et enregistrez l’implémentation en tant que service OSGI. Si elles sont disponibles, ces mises en oeuvre remplaceront le format prédéfini configuré. Si plusieurs implémentations sont enregistrées, celle qui a le rang de service supérieur remplace celle qui a le rang de service inférieur.

Les implémentations de format d’URL personnalisé doivent mettre en oeuvre une paire de méthodes pour créer une URL à partir de paramètres donnés et pour analyser une URL afin de renvoyer les mêmes paramètres respectivement.

### Combinaison avec des mappages Sling {#sling-mapping}

En plus du `UrlProvider`, il est également possible de configurer des [mappages Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) afin de réécrire et de traiter les URL. Le projet AEM Archetype fournit également [un exemple de configuration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) afin de configurer des mappages Sling pour le port 4503 (publication) et 80 (Dispatcher).

### Combinaison avec AEM Dispatcher {#dispatcher}

Les réécritures d’URL peuvent également être obtenues en utilisant AEM serveur HTTP Dispatcher avec `mod_rewrite` module . L’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) fournit une configuration de Dispatcher AEM de référence qui inclut déjà des [règles de réécriture](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) de base pour la taille générée.

## Bonnes pratiques {#best-practices}

### Choisir le meilleur format d&#39;URL {#choose-url-format}

Comme mentionné avant de sélectionner l’un des formats par défaut disponibles, ou même de mettre en oeuvre un format personnalisé, cela dépend fortement des besoins et des exigences d’un magasin. Les suggestions suivantes peuvent aider à faire une description instruite.

_**Utilisez un format d’URL de page de produit qui contient le SKU.**_

Les composants principaux CIF utilisent le SKU comme identifiant Principal dans tous les composants. Si le format d’URL de la page de produits ne contient pas le SKU, une requête GraphQL est nécessaire pour le résoudre à partir de la variable `url_key`, ce qui peut avoir un impact sur la mesure du temps jusqu’au premier octet. En outre, il peut être souhaitable que les acheteurs trouvent des produits de sku dans des moteurs de recherche.

_**Utilisez un format d’URL de page de produit qui contient le contexte de catégorie.**_

Certaines fonctionnalités du fournisseur d’URL CIF ne sont disponibles que lors de l’utilisation de formats d’URL de produit qui encodent le contexte de catégorie, comme la catégorie `url_key` ou la catégorie `url_path`. Même si ces fonctionnalités ne sont pas nécessaires pour un nouveau magasin, l’utilisation de l’un de ces formats d’URL au début contribue à réduire les efforts de migration à l’avenir.

_**Équilibre entre la longueur de l’URL et les informations codées.**_

En fonction de la taille du catalogue, notamment de la taille et de la profondeur de l’arborescence des catégories, il peut ne pas être raisonnable de coder l’intégralité `url_path` de catégories dans l’URL. Dans ce cas, la longueur de l’URL peut être réduite en incluant le `url_key` au lieu de . Cela permet d’activer presque toutes les fonctionnalités disponibles lors de l’utilisation de la catégorie `url_path`.

En outre, utilisez [Mappages Sling](#sling-mapping) afin de combiner le SKU avec le produit `url_key`. Dans la plupart des systèmes d’e-commerce, le SKU suit un format particulier et sépare le SKU de `url_key` pour les requêtes entrantes doivent être facilement possibles. Dans ce contexte, il devrait être possible de réécrire une URL de page de produit en `/p/{{category}}/{{sku}}-{{url_key}}.html`et une URL de catégorie à `/c/{{url_key}}.html` de manière respectueuse. Le `/p` et `/c` Un préfixe est toujours nécessaire pour distinguer les pages de produits et de catégories des autres pages de contenu.

### Migration d’un format d’URL vers un autre {#migrate-url-formats}

De nombreux formats d’URL par défaut sont d’une manière ou d’une autre compatibles, ce qui signifie que les URL formatées par l’un peuvent être analysées par un autre. Cela permet la migration entre les formats d’URL.

D’un autre côté, les moteurs de recherche auront besoin de temps pour analyser à nouveau toutes les pages du catalogue avec le nouveau format d’URL. Pour prendre en charge ce processus et améliorer l’expérience de l’utilisateur final, il est recommandé de fournir des redirections qui redirigent l’utilisateur des anciennes URL vers les nouvelles.

Une approche serait de connecter un environnement intermédiaire au serveur principal de commerce électronique de production et de le configurer pour utiliser le nouveau format d’URL. Ensuite, obtenez la variable [plan de site du produit généré par le générateur de plan de site des produits CIF](../../overview/seo-and-url-management.md) pour les environnements d’évaluation et de production et utilisez-les pour créer un [Carte de réécriture Apache httpd](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html). Cette carte de réécriture ne peut pas être déployée sur le Dispatcher avec le déploiement du nouveau format d’URL.

## Exemple {#example}

Le projet de [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) comprend des exemples de configuration afin de démontrer l’utilisation d’URL personnalisées pour les pages de produits et de catégories. Cela permet à chaque projet de configurer des modèles d’URL individuels pour les pages de produits et de catégories en fonction de leurs besoins SEO. Une combinaison de mappages `UrlProvider` et Sling CIF telle que décrite ci-dessus est utilisée.

>[!NOTE]
>
>Cette configuration doit être ajustée avec le domaine externe utilisé par le projet. Les mappages Sling fonctionnent en fonction du nom d’hôte et du domaine. Par conséquent, cette configuration est désactivée par défaut et doit être activée avant le déploiement. Pour ce faire, renommez le dossier `hostname.adobeaemcloud.com` de mappage Sling dans `ui.content/src/main/content/jcr_root/etc/map.publish/https` en fonction du nom de domaine utilisé et activez cette configuration en ajoutant `resource.resolver.map.location="/etc/map.publish"` à la configuration `JcrResourceResolver` du projet.

## Ressources supplémentaires {#additional}

* [Magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia)
* [Mappage des ressources AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=fr)
* [Mappages Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
