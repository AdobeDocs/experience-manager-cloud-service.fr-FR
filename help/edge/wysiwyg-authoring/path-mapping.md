---
title: Mappage de chemin pour les Edge Delivery Services
description: Découvrez comment mapper les chemins de page utilisés sur l’instance de création AEM aux chemins de page publics utilisés sur le site web et contrôler le contenu publié sur les Edge Delivery Services.
feature: Edge Delivery Services
role: User
source-git-commit: 2727744f276ee5facae718a987dcc6dc54d4e917
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---


# Mappage de chemin pour les Edge Delivery Services {#path-mapping}

Découvrez comment mapper les chemins de page utilisés sur l’instance de création AEM aux chemins de page publics utilisés sur le site web et contrôler le contenu publié sur les Edge Delivery Services.

## Vue d’ensemble {#overview}

Pour pouvoir créer du contenu WYSIWYG à l’aide d’AEM et le publier sur des Edge Delivery Services, vous devez configurer le mappage de chemin de votre projet. Ce mappage a deux objectifs.

* Il mappe et crée une relation entre les chemins de page utilisés sur votre instance de création AEM et les chemins de page publics utilisés sur votre site web.
* Il contrôle le contenu (pages, feuilles, ressources, etc.) sont publiés en Edge Delivery Services.

Le mappage du chemin doit être configuré individuellement pour chaque projet et en fonction du contenu et de la structure de l’URL du projet. Il est utilisé par AEM lors de la publication de contenu et de l’édition de contenu dans l’ [éditeur universel.](/help/sites-cloud/authoring/universal-editor/navigation.md)

## Format de configuration {#configuration-format}

Le format de la configuration du mappage de chemin contient deux sections (`mappings` et `includes`) similaires à l’exemple suivant.

```json
{
  "mappings": [
    "/content/aem-boilerplate/:/",
    "/content/aem-boilerplate/configuration:/.helix/config.json"
  ],
  "includes:" [
    "/content/aem-boilerplate/"
  ]
}
```

### mappings {#mappings}

La configuration `mappings` contient un tableau de chemins internes (sur l’instance de création d’AEM) et de chemins d’URL externes (sur le site web public).

Le format est `<internal paths>:<external path>`. Il se compose généralement d’un minimum de deux entrées.

1. La première entrée de l’exemple est le mappage de chemin des pages du site web.
1. La seconde entrée contrôle le mappage de `.helix/config.json` à la page de feuille de calcul correspondante dans le référentiel de création AEM.

Dans cet exemple, toutes les pages stockées sous `/content/aem-boilerplate/...` seront publiquement accessibles sur le site Edge Delivery Services directement sous `https://main--my-site--org.aem.live/....`.

>[!TIP]
>
>Toutes les données tabulaires gérées sous forme de feuilles de calcul (par exemple, métadonnées, redirections et taxonomie) sont généralement publiées sous la forme d’URL d’API `.json` sur des Edge Delivery Services. Pour ce faire, ils doivent être répertoriés individuellement dans la configuration de mappage.
>
>Pour plus d’informations, consultez le document [Utilisation de feuilles de calcul pour gérer les données tabulaires](/help/edge/wysiwyg-authoring/tabular-data.md) .

### inclut {#includes}

La configuration `includes` contrôle les chemins de contenu qui sont effectivement répliqués vers les Edge Delivery Services. Il peut également contenir n’importe quel tableau de chemins et contient généralement la page racine de niveau supérieur des sites.

Les Assets utilisées sur les pages Edge Delivery Services sont généralement publiées à côté de la page web. Ils seront automatiquement exportés de l’instance de création AEM vers les Edge Delivery Services.

>[!TIP]
>
>Si vous souhaitez que des ressources soient publiées directement sur des Edge Delivery Services (par exemple, si vous souhaitez que les images ou les PDF soient directement accessibles par leurs URL en dehors d’un contexte de page), vous devez également ajouter les chemins DAM à la section `includes` de la configuration.
>
>Par exemple, si un dossier racine de ressources tel que `/content/dam/my-site/documents` contenant un ensemble de PDF doit être accessible publiquement via `/assets/...`, une entrée doit être ajoutée à la section `includes` de la configuration.

## Configuration {#how-to-configure}

Les mappages de vos chemins d’accès peuvent être configurés de l’une des deux façons, selon la configuration de votre projet.

1. Si le projet est configuré pour `aem.live` et utilise le [service de configuration](https://www.aem.live/docs/config-service-setup) pour les configurations centralisées, le mappage des chemins pour chaque site est configuré via ce service de configuration.

   * Voici un exemple de requête cURL pour configurer les mappages de chemin.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/{org}/sites/{site}/public.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: ......' \
     --data '{
       "paths": {
       "mappings": [
         "/content/aem-boilerplate/:/",
         "/content/aem-boilerplate/configuration:/.helix/config.json"
       ],
       "includes": [
         "/content/aem-boilerplate/"
       ]
   }
   }'
   ```

1. Si le projet n’utilise pas le service de configuration, le mappage des chemins est configuré via un fichier `paths.json` dans le référentiel GitHub de vos projets.

   * Voir [`https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/paths.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/paths.json) pour un exemple.

Dans les deux cas, une fois que vous avez configuré les mappages de vos chemins, vous pouvez vérifier la configuration via l’URL de configuration accessible au public `https://<branch>--<site>--<org>.aem.page/config.json`.
