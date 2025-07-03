---
title: Configurations d’URL avancées
description: Découvrez comment personnaliser les URL des pages de produits et de catégories. Cela permet aux implémentations d’optimiser les URL pour les moteurs de recherche et de promouvoir la découverte.
sub-product: Commerce
version: Experience Manager as a Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configurations d’URL avancées {#url}

>[!NOTE]
>
> L’optimisation pour les moteurs de recherche est devenue une préoccupation essentielle pour de nombreux spécialistes du marketing. Par conséquent, l’optimisation du moteur de recherche doit être prise en compte dans de nombreux projets Adobe Experience Manager (AEM) as a Cloud Service. Consultez les [Bonnes pratiques de gestion des URL et d’optimisation du moteur de recherche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/seo-and-url-management.html?lang=fr) pour plus d’informations.

Les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) offrent des configurations avancées pour personnaliser les URL des pages de produits et de catégories. De nombreuses mises en œuvre personnalisent ces URL à des fins d’optimisation pour les moteurs de recherche (SEO). La vidéo suivante explique comment configurer le `UrlProvider` service et les fonctionnalités du [mappage Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) pour personnaliser les URL des pages de produits et de catégories.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuration {#configuration}

Pour configurer le service `UrlProvider` en fonction des exigences et des besoins de SEO, un projet doit fournir une configuration OSGI pour la _configuration du fournisseur d’URL CIF_.

>[!NOTE]
>
> Depuis la version 2.0.0 des composants principaux CIF d’AEM, la configuration du fournisseur d’URL fournit uniquement des formats d’URL prédéfinis, au lieu des formats configurables en texte libre connus des versions 1.x. De plus, l’utilisation de sélecteurs pour transmettre des données dans des URL a été remplacée par des suffixes.

### Format d’URL de page de produits {#product}

Celui-ci configure les URL des pages de produits et prend en charge les options suivantes :

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (par défaut)
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`

Si le [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) est disponible :

* `{{page}}` est remplacé par `/content/venia/us/en/products/product-page` ;
* `{{sku}}` est remplacé par le SKU du produit, par exemple `VP09`
* `{{url_key}}` est remplacé par la propriété `url_key` du produit, par exemple `lenora-crochet-shorts`
* `{{url_path}}` est remplacé par le `url_path` du produit, par exemple `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` est remplacé par la variante actuellement sélectionnée, par exemple `VP09-KH-S`

Depuis que `url_path` a été abandonné, les formats d’URL de produit prédéfinis utilisent les `url_rewrites` d’un produit et choisissent celui qui contient le plus de segments de chemin comme alternative si `url_path` n’est pas disponible.

Avec les données d’exemple ci-dessus, une URL de variante de produit formatée à l’aide du format d’URL par défaut ressemblera à `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### Format d’URL de page de catégorie {#product-list}

Il configure les URL des pages de listes de catégories ou de produits et prend en charge les options suivantes :

* `{{page}}.html/{{url_path}}.html` (par défaut)
* `{{page}}.html/{{url_key}}.html`

Si le [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) est disponible :

* `{{page}}` est remplacé par `/content/venia/us/en/products/category-page` ;
* `{{url_key}}` est remplacé par la propriété `url_key` de la catégorie
* `{{url_path}}` est remplacé par le `url_path` de la catégorie.

Avec les exemples de données ci-dessus, une URL de page de catégorie formatée à l’aide du format d’URL par défaut ressemble à `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`.

>[!NOTE]
> 
> L’`url_path` est une concaténation des `url_keys`, des ancêtres d’un produit ou d’une catégorie et de l’`url_key` du produit ou de la catégorie, séparés par une barre oblique `/`. Chaque `url_key` est considéré comme unique dans un magasin donné.

### Configuration spécifique au magasin {#store-specific-urlformats}

Les formats d’URL de catégories et de pages produits définis par la _configuration du fournisseur d’URL CIF_ peuvent être modifiés pour chaque magasin.

Dans la configuration CIF, un éditeur peut sélectionner un autre format d’URL de page de catégorie ou de produit. Si rien n’est sélectionné à cet endroit, l’implémentation revient à la configuration de l’ensemble du système.

La modification du format de l’URL d’un site web actif peut avoir un impact négatif sur le trafic organique de votre site. Veuillez vous référer aux [Bonnes pratiques](#best-practices) ci-dessous et planifier soigneusement le changement du format de l’URL à l’avance.

![Formats d’URL dans la configuration CIF](assets/store-specific-url-formats.png)

>[!NOTE]
>
> La configuration spécifique des formats d’URL pour les magasins nécessite les [composants principaux CIF 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) et la dernière version du module complémentaire Adobe Experience Manager Content and Commerce.

## URL de pages de produits prenant en compte les catégories {#context-aware-pdps}

Comme il est possible d’encoder des informations sur les catégories dans l’URL d’un produit, les produits appartenant à plusieurs catégories peuvent également être adressés avec plusieurs URL de produit.

Les formats d’URL par défaut sélectionnent l’une des alternatives possibles en utilisant le schéma suivant :

* si l’`url_path` est défini par le serveur principal de commerce électronique, utilisez-le (obsolète).
* à partir des `url_rewrites` utilisez les URL qui se terminent par l’`url_key` comme alternatives
* parmi ces alternatives, utilisez celle qui a le plus de segments de chemin d’accès
* s’il y en a plusieurs, prenez la première dans l’ordre indiqué par le serveur principal de commerce électronique.

Ce schéma sélectionne l’`url_path` qui a le plus d’ancêtres, en partant du principe qu’une catégorie enfant est plus spécifique que sa catégorie parent. L’`url_path` sélectionnée est considérée comme _canonique_ et sera toujours utilisée comme lien canonique sur les pages de produits ou dans le plan du site du produit.

Cependant, lorsqu’un acheteur ou une acheteuse navigue d’une page de catégorie à une page de produit, ou d’une page de produit à une autre page de produit associée dans la même catégorie, il est utile de conserver le contexte actuel de la catégorie. Dans ce cas, la sélection d’`url_path` doit préférer les alternatives qui se trouvent dans le contexte de la catégorie actuelle à la sélection _canonique_ décrite ci-dessus.

Cette fonctionnalité doit être activée dans la _configuration du fournisseur d’URL CIF_. Si elle est activée, la sélection donnera un score plus élevé aux alternatives, quand

* elles correspondent à des parties d’`url_path` d’une catégorie donnée depuis le début (correspondance de préfixe floue)
* ou lorsqu’elles correspondent à l’`url_key` d’une catégorie donnée n’importe où (correspondance partielle exacte).

Prenons l’exemple de la réponse à une [requête de produits](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) ci-dessous. Compte tenu des éléments suivants :

* l’utilisateur ou l’utilisatrice se trouve sur la page de la catégorie « Nouveaux produits/Nouveautés de l’été 2022 » ;
* le magasin utilise le format d’URL de page de la catégorie par défaut

L’alternative « nouveaux-produits/nouveautes-de-lete-2022/boucles-doreilles-cirque-dor.html » correspond à deux des segments de chemin du contexte depuis le début. Autrement dit, « nouveaux produits » et « nouveautés de l’été 2022 ». Si le magasin utilise un format d’URL de page de catégorie contenant uniquement l’`url_key`, la même alternative est toujours sélectionnée, car elle correspond à l’`url_key` du contexte. Dans les deux cas, l’URL de la page produit est créée pour « nouveaux-produits/nouveautes-de-lete-2022/boucles-doreilles-cirque-dor.html » `url_path`.

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
> Les URL de produits prenant en compte les catégories nécessitent les [composants principaux CIF 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) ou plus récents.

## Pages de catégories et de produits spécifiques {#specific-pages}

Il est possible de créer des [pages multi-catégories et multi-produits](../authoring/multi-template-usage.md) pour un sous-ensemble spécifique de catégories ou de produits d’un catalogue.

### Critères de sélection {#specific-pages-selection}

La sélection d’une page de catégorie spécifique est directe, basée sur l’`url_path` ou l’`url_key` de la catégorie. La correspondance de sous-catégories n’est prise en charge que pour les formats d’URL contenant l’`url_path` complète de la catégorie. Sinon, seule une correspondance exacte de l’`url_key` est possible.

Les pages produits spécifiques sont sélectionnées soit par le SKU du produit, soit par sa catégorie. Dans ce dernier cas, certaines informations sur la catégorie doivent être encodées dans l’URL du produit. Cette fonctionnalité n’est disponible que pour certains formats d’URL par défaut. Consultez le tableau suivant pour comparer les formats d’URL qui prennent en charge la sélection de pages spécifiques par SKU ou catégorie.


| Format d’URL | par SKU | par catégorie |
| ----------------------------------------------------- | ------ | ---------------- |
| `{{page}}.html/{{url_key}}.html` | non | non |
| `{{page}}.html/{{category}}/{{url_key}}.html` | non | correspondance exacte uniquement |
| `{{page}}.html/{{url_path}}.html` | non | oui |
| `{{page}}.html/{{sku}}.html` | oui | non |
| `{{page}}.html/{{sku}}/{{url_key}}.html` | oui | non |
| `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html` | oui | correspondance exacte uniquement |
| `{{page}}.html/{{sku}}/{{url_path}}.html` | oui | oui |

{style="table-layout:auto"}

>[!NOTE]
>
> Pour sélectionner des pages produits spécifiques en fonction de la catégorie, vous devez disposer de lʼextension [CIF Core Components 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) ou version ultérieure.

### Lien profond {#specific-pages-deep-linking}

Le `UrlProvider` est préconfiguré pour générer des liens profonds vers des pages de catégories et de produits spécifiques sur les instances dʼauteur. Cette fonctionnalité est utile pour les éditeurs et éditrices qui parcourent un site en mode Aperçu, se rendent sur une page produit ou de catégorie spécifique, puis repassent en mode Édition pour modifier la page.

Dans les instances de publication, en revanche, les adresses URL des pages de catalogue doivent rester stables pour ne pas perdre les gains de classement dans les moteurs de recherche, par exemple. Pour cette raison, les instances de publication ne génèrent pas de liens profonds vers des pages de catalogue spécifiques par défaut. Pour modifier ce comportement, la _stratégie de page spécifique du fournisseur d’URL CIF_ peut être configurée pour générer toujours des adresses URL de page spécifiques.

### Plusieurs pages de catalogue {#multiple-product-pages}

Lorsque les éditeurs et les éditrices souhaitent avoir un contrôle total sur la navigation de niveau supérieur d’un site, l’utilisation d’une seule page de catalogue pour effectuer le rendu des catégories de niveau supérieur d’un catalogue peut s’avérer contre-productive. Pour y remédier, les éditeurs et les éditrices peuvent créer plusieurs pages de catalogue, une pour chaque catégorie du catalogue qu’ils souhaitent inclure dans la navigation de niveau supérieur.

Pour ce cas d’utilisation, chacune des pages du catalogue peut avoir une référence à une page de produit et de catégorie spécifique à la catégorie configurée pour la page du catalogue. Le `UrlProvider` les utilise pour créer des liens pour les pages et les catégories de la catégorie configurée. Toutefois, pour des raisons de performances, seules les pages enfants directes du catalogue de la racine de navigation / page de destination d’un site sont prises en compte.

Il est recommandé que les pages de produit et de catégorie d’une page de catalogue soient des pages descendantes de cette page de catalogue, sinon les composants tels que Navigation ou Chemin de navigation risquent de ne pas fonctionner correctement.

>[!NOTE]
>
> La prise en charge complète de plusieurs pages de catalogue nécessite la version [2.10.0 des composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.10.0), ou une version plus récente.

## Personnalisations {#customization}

### Formats d’URL personnalisés {#custom-url-format}

Pour fournir un format dʼURL personnalisé, un projet peut implémenter lʼinterface de service [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) ou [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) et enregistrer lʼimplémentation en tant que service OSGI. Ces implémentations, si elles sont disponibles, remplacent le format configuré et prédéfini. S’il existe plusieurs implémentations enregistrées, celle qui a le rang de service supérieur remplace celles qui ont le rang de service inférieur.

Les implémentations de format dʼURL personnalisé doivent implémenter une paire de méthodes pour créer une adresse URL à partir de paramètres donnés, et pour analyser une URL afin de renvoyer les mêmes paramètres, respectivement.

### Combinaison avec des mappages Sling {#sling-mapping}

En plus du `UrlProvider`, il est également possible de configurer des [mappages Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) afin de réécrire et de traiter les URL. Le projet AEM Archetype fournit également [un exemple de configuration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) afin de configurer des mappages Sling pour les ports 4503 (publication) et 80 (Dispatcher).

### Combinaison avec AEM Dispatcher {#dispatcher}

Les réécritures d’URL peuvent également être obtenues en utilisant le serveur HTTP AEM Dispatcher avec le module `mod_rewrite`. L’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) fournit une configuration de Dispatcher AEM de référence qui inclut déjà des [règles de réécriture](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) de base pour la taille générée.

## Bonnes pratiques {#best-practices}

### Choix du meilleur format dʼURL {#choose-url-format}

Comme indiqué précédemment, la sélection dʼun des formats par défaut disponibles, ou même lʼimplémentation dʼun format personnalisé, dépendent fortement des besoins et des exigences dʼun magasin. Les suggestions suivantes peuvent vous aider à prendre la bonne décision.

_&#x200B;**Utilisez un format d’URL de page produit qui contient le SKU.**&#x200B;_

Les composants principaux CIF utilisent le SKU comme identifiant principal dans tous les composants. Si le format d’URL de la page produit ne contient pas le SKU, une requête GraphQL est nécessaire pour le résoudre. Cette résolution peut avoir une incidence sur le temps de chargement du premier octet (TTFB). Il peut également être souhaitable que les nouveaux acheteurs et acheteuses puissent trouver des produits par SKU en utilisant des moteurs de recherche.

_&#x200B;**Utilisez un format dʼURL de page produit qui contient le contexte de la catégorie.**&#x200B;_

Certaines fonctionnalités du fournisseur dʼURL CIF ne sont disponibles que lors de lʼutilisation de formats dʼURL de produits qui codent le contexte de la catégorie, comme la `url_key` ou l’`url_path` de la catégorie. Même si ces fonctionnalités sont facultatives pour un nouveau magasin, lʼutilisation de lʼun de ces formats dʼURL dès le départ permet de réduire les efforts de migration à lʼavenir.

_&#x200B;**Compromis entre la longueur de lʼURL et les informations codées.**&#x200B;_

En fonction de la taille du catalogue, en particulier de la taille et de la profondeur de lʼarbre des catégories, il peut ne pas être raisonnable dʼencoder lʼ`url_path` complet des catégories dans lʼadresse URL. Dans ce cas, la longueur de lʼURL peut être réduite en incluant uniquement la `url_key` de la catégorie. Cette méthode permet de prendre en charge presque toutes les fonctionnalités disponibles lors de l’utilisation de l’`url_path` de la catégorie.

Utilisez également les [mappages Sling](#sling-mapping) pour combiner le SKU avec la `url_key` du produit. Dans la plupart des systèmes d’e-commerce, le SKU a un format particulier. La séparation du SKU de la `url_key` pour les requêtes entrantes ne devrait pas poser de problème. Dans cette optique, il devrait être possible de réécrire lʼadresse URL dʼune page produit en `/p/{{category}}/{{sku}}-{{url_key}}.html`, et lʼURL dʼune catégorie en `/c/{{url_key}}.html`, respectivement. Les préfixes `/p` et `/c` sont toujours nécessaires pour distinguer les pages de produits et de catégories des autres pages de contenu.

### Migrer vers un nouveau format d’URL {#migrate-url-formats}

De nombreux formats d’URL par défaut sont d’une manière ou d’une autre compatibles entre eux, ce qui signifie que les URL formatées par l’un peuvent être analysées par un autre. Cela permet la migration entre les formats d’URL.

D’un autre côté, les moteurs de recherche ont besoin d’un certain temps pour analyser à nouveau toutes les pages du catalogue avec le nouveau format d’URL. Pour prendre en charge ce processus et améliorer l’expérience de la personne utilisatrice finale, il est recommandé de fournir des redirections qui redirigent la personne utilisatrice des anciennes URL vers les nouvelles.

Une approche pour cela pourrait être de connecter un environnement d’évaluation au serveur principal de commerce électronique de production et de le configurer pour utiliser le nouveau format d’URL. Ensuite, obtenez le [plan du site du produit généré par le générateur de plan du site des produits CIF](../../overview/seo-and-url-management.md) pour les environnements d’évaluation et de production et utilisez-les pour créer une [carte de réécriture Apache httpd](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html). Cette carte de réécriture peut ensuite être déployée sur le Dispatcher en même temps que le déploiement du nouveau format d’URL.

## Exemple {#example}

Le projet de [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) comprend des exemples de configuration afin de démontrer l’utilisation d’URL personnalisées pour les pages de produits et de catégories. Cette configuration permet à chaque projet de configurer des modèles d’URL individuels pour les pages de produits et de catégories en fonction de leurs besoins d’optimisation du moteur de recherche. Une combinaison de mappages `UrlProvider` et Sling CIF telle que décrite ci-dessus est utilisée.

>[!NOTE]
>
>Cette configuration doit être ajustée avec le domaine externe utilisé par le projet. Les mappages Sling fonctionnent en fonction du nom d’hôte et du domaine. Par conséquent, cette configuration est désactivée par défaut et doit être activée avant le déploiement. Pour ce faire, renommez le dossier `hostname.adobeaemcloud.com` de mappage Sling dans `ui.content/src/main/content/jcr_root/etc/map.publish/https` en fonction du nom de domaine utilisé et activez cette configuration en ajoutant `resource.resolver.map.location="/etc/map.publish"` à la configuration `JcrResourceResolver` du projet.

## Ressources supplémentaires {#additional}

* [Magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia)
* [Mappage des ressources AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=fr)
* [Mappages Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
