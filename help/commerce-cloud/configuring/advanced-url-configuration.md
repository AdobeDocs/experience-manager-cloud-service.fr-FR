---
title: Configurations d’URL avancées
description: Découvrez comment personnaliser les URL des pages de produits et de catégories. La personnalisation permet aux implémentations d’optimiser les URL pour les moteurs de recherche et de promouvoir la découverte.
sub-product: Commerce
version: Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '2172'
ht-degree: 48%

---

# Configurations d’URL avancées {#url}

>[!NOTE]
>
> L’optimisation pour les moteurs de recherche est devenue une préoccupation essentielle pour de nombreux spécialistes du marketing. Par conséquent, les préoccupations relatives à l’optimisation pour les moteurs de recherche doivent être prises en compte pour de nombreux projets sur Adobe Experience Manager (AEM) as a Cloud Service. Voir [Bonnes pratiques de gestion des URL et de l’optimisation pour les moteurs de recherche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/seo-and-url-management.html) pour plus d’informations.

Les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) offrent des configurations avancées pour personnaliser les URL des pages de produits et de catégories. De nombreuses implémentations personnalisent ces URL à des fins d’optimisation du moteur de recherche (SEO). La vidéo suivante explique comment configurer le `UrlProvider` service et les fonctionnalités du [mappage Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) pour personnaliser les URL des pages de produits et de catégories.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuration {#configuration}

Pour configurer la variable `UrlProvider` en fonction des exigences et des besoins du SEO, un projet doit fournir une configuration OSGI pour la fonction _Configuration du fournisseur d’URL CIF_.

>[!NOTE]
>
> Depuis la version 2.0.0 des composants principaux CIF d’AEM, la configuration du fournisseur d’URL fournit uniquement des formats d’URL prédéfinis, au lieu des formats configurables en texte libre connus des versions 1.x. De plus, l’utilisation de sélecteurs pour transmettre des données dans des URL a été remplacée par des suffixes.

### Format d’URL de page de produits {#product}

Configure les URL des pages de produits et prend en charge les options suivantes :

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (par défaut)
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`

Si la variable [Magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` est remplacé par `/content/venia/us/en/products/product-page`
* `{{sku}}` est remplacé par le SKU du produit, par exemple : `VP09`
* `{{url_key}}` est remplacé par le `url_key` par exemple, `lenora-crochet-shorts`
* `{{url_path}}` est remplacé par le `url_path`, par exemple : `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` est remplacé par la variante actuellement sélectionnée, par exemple : `VP09-KH-S`

Depuis la variable `url_path` obsolètes, les formats d’URL de produit prédéfinis utilisent la variable `url_rewrites` et sélectionnez celle qui contient le plus de segments de chemin comme alternative si la variable `url_path` n’est pas disponible.

Avec les données d’exemple ci-dessus, une URL de variante de produit formatée à l’aide du format d’URL par défaut ressemble à ce qui suit : `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### Format d’URL de page de catégorie {#product-list}

Configure les URL des pages de liste de catégories ou de produits et prend en charge les options suivantes :

* `{{page}}.html/{{url_path}}.html` (par défaut)
* `{{page}}.html/{{url_key}}.html`

Si la variable [Magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` est remplacé par `/content/venia/us/en/products/category-page`
* `{{url_key}}` est remplacé par le `url_key` property
* `{{url_path}}` est remplacé par le `url_path`

Avec les données d’exemple ci-dessus, une URL de page de catégorie formatée à l’aide du format d’URL par défaut ressemble à ce qui suit : `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`.

>[!NOTE]
> 
> L’`url_path` est une concaténation des `url_keys`, des ancêtres d’un produit ou d’une catégorie et de l’`url_key` du produit ou de la catégorie, séparés par une barre oblique `/`. Chaque `url_key` est considéré comme unique dans un magasin donné.

### Configuration spécifique au magasin {#store-specific-urlformats}

Formats d’URL de catégorie et de page de produits à l’échelle du système définis par la variable _Configuration du fournisseur d’URL CIF_ peut être modifié pour chaque magasin.

Dans la configuration du CIF, un éditeur peut sélectionner un autre format d’URL de page de catégorie ou de produit. Si rien n’est sélectionné, l’implémentation revient à la configuration à l’échelle du système.

La modification du format de l’URL d’un site Web actif peut avoir un impact négatif sur le trafic organique de votre site. Voir [Bonnes pratiques](#best-practices) ci-dessous et planifiez soigneusement le changement du format de l&#39;URL à l&#39;avance.

![Formats d’URL dans la configuration CIF](assets/store-specific-url-formats.png)

>[!NOTE]
>
> La configuration spécifique au magasin des formats d’URL nécessite [Composants principaux CIF 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) et la dernière version du module complémentaire Adobe Experience Manager Content and Commerce.

## URL de pages de produits prenant en compte les catégories {#context-aware-pdps}

Comme il est possible d’encoder des informations sur les catégories dans l’URL d’un produit, les produits appartenant à plusieurs catégories peuvent également être adressés avec plusieurs URL de produit.

Les formats d’URL par défaut sélectionnent l’une des alternatives possibles à l’aide du schéma suivant :

* si l’`url_path` est défini par le serveur principal de commerce électronique, utilisez-le (obsolète).
* à partir des `url_rewrites` utilisez les URL qui se terminent par l’`url_key` comme alternatives
* parmi ces alternatives, utilisez celle qui a le plus de segments de chemin d’accès
* s’il y en a plusieurs, prenez la première dans l’ordre indiqué par le serveur principal de commerce électronique.

Ce modèle sélectionne la variable `url_path` avec la plupart des ancêtres, en partant du principe qu’une catégorie enfant est plus spécifique que sa catégorie parent. Le `url_path` est considéré _canonique_ et est toujours utilisé comme lien canonique sur les pages de produits ou dans le plan de site du produit.

Cependant, lorsqu’un acheteur navigue d’une page de catégorie à une page de produit, ou d’une page de produit à une autre page de produit associée dans la même catégorie, il est utile de conserver le contexte actuel de la catégorie. Dans ce cas, la variable `url_path` la sélection doit préférer les alternatives qui se trouvent dans le contexte de catégorie actuel à la _canonique_ sélection décrite ci-dessus.

Cette fonction doit être activée dans la variable _Configuration du fournisseur d’URL CIF_. Si l’option est activée, la sélection obtient des scores de remplacement plus élevés, lorsque

* elles correspondent à des parties d’`url_path` d’une catégorie donnée depuis le début (correspondance de préfixe floue)
* ou lorsqu’elles correspondent à l’`url_key` d’une catégorie donnée n’importe où (correspondance partielle exacte).

Prenons l’exemple de la réponse à une [requête de produits](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) ci-dessous. Compte tenu des éléments suivants :

* l’utilisateur se trouve sur la page de catégorie &quot;Nouveaux produits/Nouveautés de l’été 2022&quot;.
* le magasin utilise le format d’URL de page de catégorie par défaut.

L’alternative &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot; correspond à deux des segments de chemin du contexte depuis le début. Autrement dit, &quot;nouveaux produits&quot; et &quot;nouveaux en été 2022&quot;. Si le magasin utilise un format d’URL de page de catégorie contenant uniquement l’`url_key`, la même alternative est toujours sélectionnée, car elle correspond à l’`url_key` du contexte. Dans les deux cas, l’URL de la page de produits est créée pour le &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;. `url_path`.

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

Il est possible de créer des [pages multi-catégories et de produits](../authoring/multi-template-usage.md) pour un sous-ensemble spécifique de catégories ou de produits d’un catalogue.

### Critères de sélection {#specific-pages-selection}

La sélection d’une page de catégorie spécifique est directe, basée sur l’`url_path` ou l’`url_key` de la catégorie. La correspondance de sous-catégories n’est prise en charge que pour les formats d’URL contenant la catégorie complète `url_path`. Sinon, seule une correspondance exacte de l’`url_key` est possible.

Les pages de produit spécifiques sont sélectionnées par le SKU ou la catégorie du produit. Dans ce dernier cas, certaines informations de catégorie doivent être codées dans l’URL du produit. Cette fonctionnalité n’est disponible que pour certains formats d’URL par défaut. Consultez le tableau suivant pour une comparaison du format d’URL qui prend en charge la sélection de pages spécifiques par SKU ou catégorie.


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

Le `UrlProvider` est préconfiguré pour générer des liens profonds vers des pages de catégories et de produits spécifiques sur les instances dʼauteur. Cette fonctionnalité est utile pour les éditeurs qui parcourent un site en mode Aperçu, accèdent à une page de produit ou de catégorie spécifique et passent en mode d’édition pour modifier la page.

Dans les instances de publication, en revanche, les adresses URL des pages de catalogue doivent rester stables pour ne pas perdre les gains de classement dans les moteurs de recherche, par exemple. En raison de ce niveau de publication, les instances ne rendent pas par défaut les liens profonds vers des pages de catalogue spécifiques. Pour modifier ce comportement, la variable _Stratégie de page spécifique au fournisseur d’URL CIF_ peut être configuré pour toujours générer des URL de page spécifiques.

### Plusieurs pages de catalogue {#multiple-product-pages}

Lorsque les éditeurs souhaitent avoir un contrôle total de la navigation de niveau supérieur d’un site, l’utilisation d’une seule page de catalogue pour effectuer le rendu des catégories de niveau supérieur d’un catalogue peut ne pas être souhaitée. Au lieu de cela, les éditeurs peuvent créer plusieurs pages de catalogue, une pour chaque catégorie du catalogue qu’ils souhaitent inclure dans la navigation de niveau supérieur.

Pour ce cas d’utilisation, chacune des pages du catalogue peut avoir une référence à une page de produit et de catégorie spécifique à la catégorie configurée pour la page du catalogue. Le `UrlProvider` utilise ces connexions pour créer des liens pour les pages et les catégories de la catégorie configurée. Toutefois, pour des raisons de performances, seules les pages enfants directes du catalogue de la racine de navigation / page de destination d’un site sont prises en compte.

Il est recommandé que les pages de produit et de catégorie d’une page de catalogue soient des pages descendantes de cette page de catalogue, sinon les composants tels que Navigation ou Chemin de navigation risquent de ne pas fonctionner correctement.

>[!NOTE]
>
> La prise en charge complète de plusieurs pages de catalogue nécessite la version [2.10.0 des composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.10.0), ou une version plus récente.

## Personnalisations {#customization}

### Formats d’URL personnalisés {#custom-url-format}

Pour fournir un format d’URL personnalisé, un projet peut mettre en oeuvre l’une des options suivantes : [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) ou le [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) et enregistrez l’implémentation en tant que service OSGI. Si elles sont disponibles, ces implémentations remplacent le format prédéfini configuré. Si plusieurs mises en oeuvre sont enregistrées, celle qui a le rang de service supérieur remplace celle qui a le rang de service inférieur.

Les implémentations de format dʼURL personnalisé doivent implémenter une paire de méthodes pour créer une adresse URL à partir de paramètres donnés, et pour analyser une URL afin de renvoyer les mêmes paramètres, respectivement.

### Combinaison avec des mappages Sling {#sling-mapping}

En plus de la variable `UrlProvider`, il est également possible de configurer [Mappages Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) pour réécrire et traiter les URL. Le projet AEM Archetype fournit également [un exemple de configuration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) pour configurer certaines mappages Sling pour le port 4503 (publication) et 80 (Dispatcher).

### Combinaison avec AEM Dispatcher {#dispatcher}

Les réécritures d’URL peuvent également être obtenues en utilisant le serveur HTTP AEM Dispatcher avec le module `mod_rewrite`. L’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) fournit une configuration de Dispatcher AEM de référence qui inclut déjà des [règles de réécriture](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) de base pour la taille générée.

## Bonnes pratiques {#best-practices}

### Choix du meilleur format dʼURL {#choose-url-format}

Comme indiqué précédemment, la sélection dʼun des formats par défaut disponibles, ou même lʼimplémentation dʼun format personnalisé, dépendent fortement des besoins et des exigences dʼun magasin. Les suggestions suivantes peuvent aider à prendre une décision éclairée.

_**Utilisez un format d’URL de page de produit qui contient le SKU.**_

Les composants principaux CIF utilisent le SKU comme identifiant Principal dans tous les composants. Si le format d’URL de la page de produits ne contient pas le SKU, une requête GraphQL est nécessaire pour le résoudre. Cette résolution peut avoir une incidence sur le délai d’expiration du premier octet. En outre, il peut être souhaitable que les acheteurs puissent trouver des produits par SKU à l’aide de moteurs de recherche.

_**Utilisez un format dʼURL de page produit qui contient le contexte de la catégorie.**_

Certaines fonctionnalités du fournisseur d’URL CIF ne sont disponibles que lors de l’utilisation de formats d’URL de produit, qui encodent le contexte de catégorie, comme la catégorie `url_key` ou la catégorie `url_path`. Même si ces fonctionnalités sont facultatives pour un nouveau magasin, lʼutilisation de lʼun de ces formats dʼURL dès le départ permet de réduire les efforts de migration à lʼavenir.

_**Compromis entre la longueur de lʼURL et les informations codées.**_

En fonction de la taille du catalogue, en particulier de la taille et de la profondeur de lʼarbre des catégories, il peut ne pas être raisonnable dʼencoder lʼ`url_path` complet des catégories dans lʼadresse URL. Dans ce cas, la longueur de l’URL peut être réduite en incluant uniquement le `url_key` au lieu de . Cette méthode prend en charge la plupart des fonctionnalités disponibles lors de l’utilisation de la catégorie `url_path`.

Utilisez également [Mappages Sling](#sling-mapping) combiner le SKU avec le produit `url_key`. Dans la plupart des systèmes d’e-commerce, le SKU suit un format particulier et sépare le SKU de la variable `url_key` pour les requêtes entrantes doivent être facilement possibles. Dans ce contexte, il devrait être possible de réécrire une URL de page de produit en `/p/{{category}}/{{sku}}-{{url_key}}.html`et une URL de catégorie à `/c/{{url_key}}.html` respectivement. Le `/p` et `/c` Un préfixe est toujours nécessaire pour distinguer les pages de produits et de catégories des autres pages de contenu.

### Migrer vers un nouveau format d’URL {#migrate-url-formats}

De nombreux formats d’URL par défaut sont d’une manière ou d’une autre compatibles, ce qui signifie que les URL formatées par l’un peuvent être analysées par un autre. Cela permet la migration entre les formats d’URL.

D’un autre côté, les moteurs de recherche ont besoin de temps pour analyser toutes les pages du catalogue avec le nouveau format d’URL. Pour prendre en charge ce processus et améliorer l’expérience de l’utilisateur final, il est recommandé de fournir des redirections qui redirigent l’utilisateur des anciennes URL vers les nouvelles.

Une approche pour cela pourrait être de connecter un environnement d’évaluation au serveur principal de commerce électronique de production et de le configurer pour utiliser le nouveau format d’URL. Ensuite, obtenez le [plan du site du produit généré par le générateur de plan du site des produits CIF](../../overview/seo-and-url-management.md) pour les environnements d’évaluation et de production et utilisez-les pour créer une [carte de réécriture Apache httpd](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html). Cette carte de réécriture peut ensuite être déployée sur Dispatcher avec le déploiement du nouveau format d’URL.

## Exemple {#example}

Le projet de [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) comprend des exemples de configuration afin de démontrer l’utilisation d’URL personnalisées pour les pages de produits et de catégories. Cette configuration permet à chaque projet de configurer des modèles d’URL individuels pour les pages de produits et de catégories en fonction de leurs besoins SEO. Une combinaison de mappages `UrlProvider` et Sling CIF telle que décrite ci-dessus est utilisée.

>[!NOTE]
>
>Cette configuration doit être ajustée avec le domaine externe utilisé par le projet. Les mappages Sling fonctionnent en fonction du nom d’hôte et du domaine. Par conséquent, cette configuration est désactivée par défaut et doit être activée avant le déploiement. Pour ce faire, renommez le mappage Sling. `hostname.adobeaemcloud.com` dossier dans `ui.content/src/main/content/jcr_root/etc/map.publish/https` en fonction du nom de domaine utilisé et activez cette configuration en ajoutant `resource.resolver.map.location="/etc/map.publish"` au `JcrResourceResolver` de la configuration du projet.

## Ressources supplémentaires {#additional}

* [Magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia)
* [Mappage des ressources AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=fr)
* [Mappages Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
