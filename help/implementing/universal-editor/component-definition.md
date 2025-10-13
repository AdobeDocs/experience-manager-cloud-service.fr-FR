---
title: Définition du composant
description: Comprenez en détail le contrat JSON entre la définition du composant et l’éditeur universel.
feature: Developing
role: Admin, Architect, Developer
exl-id: e1bb1a54-50c0-412a-a8fd-8167c6f47d2b
source-git-commit: b4e61ec6abcaf73119f8963d72317759b2bd7c76
workflow-type: ht
source-wordcount: '611'
ht-degree: 100%

---

# Définition du composant {#component-definition}

Comprenez en détail le contrat JSON entre la définition du composant et l’éditeur universel.

## Vue d’ensemble {#overview}

Le fichier `component-definition.json` définit les composants disponibles pour les personnes responsables de la création du contenu dans le cadre du projet. Ce document explique en détail l’objectif de ce fichier et la manière dont l’éditeur universel l’utilise pour fournir aux personnes responsables du contenu des composants de création de pages.

>[!TIP]
>
>Pour une vue d’ensemble du processus de modélisation de contenu, consultez le document [Modélisation de contenu pour la création WYSIWYG avec des projets Edge Delivery Services](https://www.aem.live/developer/component-model-definitions).

>[!TIP]
>
>Il n’est pas nécessaire de créer un fichier `component-definition.json` à partir de zéro. Le projet modèle utilisé pour [ amorcer votre projet](https://www.aem.live/developer/ue-tutorial) contient un [fichier `component-definition.json` entièrement fonctionnel](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json) que vous pouvez adapter à vos besoins.

## Définition d’exemple de composant {#example}

Voici un exemple complet, mais simple de `component-definition.json`.

```json
{
  "groups":[
    {
      "title":"General Components",
      "id":"general",
      "components":[
        {
          "title":"Text",
          "id":"text",
          "model": "text",
          "filter": "texts",
          "plugins":{
            "aem":{
              "page":{
                "resourceType":"wknd/components/text",
                "template":{
                  "text":"Default Text",
                  "name":"Text"
                }
              }
            },
            "aem65":{
              "page":{
                "resourceType":"wknd/components/text",
                "template":{
                  "text":"Default Text",
                  "name":"Text"
                }
              }
            }
          }
        }
      ]
    }
  ]
}
```

## `groups` {#groups}

`groups` définit les groupes de composants visibles dans l’environnement auteur de l’éditeur universel lorsque l’on clique sur l’icône **Ajouter** du panneau des propriétés de l’éditeur pour [ajouter un nouveau composant](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components) à une page. Les groupes permettent d’organiser les composants. Les groupes courants peuvent être **Composants généraux** et **Composants avancés**.

* `title` définit la description textuelle du groupe affiché dans l’interface utilisateur de l’éditeur.
* `id` identifie le groupe de manière unique.

## `components` {#components}

`components` définit les composants appartenant à un groupe.

* `title` définit la description textuelle du composant affichée dans l’interface utilisateur.
* `id` identifie de manière unique le composant.
   * Le [modèle de composant](/help/implementing/universal-editor/field-types.md#model-structure) du même `id` définit les champs du composant.
   * Dans la mesure où il est unique, il peut être utilisé, par exemple, dans une [définition de filtre](/help/implementing/universal-editor/filtering.md) pour déterminer les composants qui peuvent être ajoutés à un conteneur.
* `model` définit le [modèle](/help/implementing/universal-editor/field-types.md#model-structure) utilisé avec le composant.
   * Le modèle est ainsi maintenu de manière centralisée dans la définition du composant et n’a pas besoin d’être [spécifié](/help/implementing/universal-editor/field-types.md#instrumentation) pour l’instrumentation.
   * Vous pouvez ainsi déplacer des composants entre des conteneurs.
* `filter` définit quel [ filtre](/help/implementing/universal-editor/filtering.md) doit être utilisé avec le composant.

## `plugins` {#plugins}

`plugins` définit le plug-in responsable de la conservation du composant. Les plug-ins courants incluent :

* `aem` pour [AEM as a Cloud Service.](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service)
* `aem65` pour [AEM 6.5.](https://experienceleague.adobe.com/fr/docs/experience-manager-65) et [AEM 6.5 LTS](https://experienceleague.adobe.com/fr/docs/experience-manager-65-lts)
* `xwalk` pour [Création avec AEM Sites pour Edge Delivery Services.](https://www.aem.live/developer/ue-tutorial)

## `page` ou `cf` {#page-cf}

Une fois le `plugin` défini, il faut indiquer s’il est lié à une page ou à un fragment.

* `page` indique que le composant est le contenu de la page active.
* `cf` indique que le composant est associé au contenu dans un [fragment de contenu](/help/assets/content-fragments/content-fragments.md).

### `page` {#page}

Si le composant correspond au contenu de la page, vous pouvez fournir les informations suivantes.

* `resourceType` définit le [Sling](/help/implementing/developing/introduction/sling-cheatsheet.md)`resourceType` utilisé pour le rendu du composant.
* `template` définit les valeurs clé facultatives à écrire automatiquement dans le composant nouvellement créé et précise quel filtre et/ou modèle doit être appliqué au composant.
   * Utile pour le texte explicatif, d’exemple ou d’espace réservé.

#### `template` {#template}

En fournissant des paires clé/valeur facultatives, `template` peut les écrire automatiquement dans le nouveau composant. De plus, les valeurs facultatives suivantes peuvent également être spécifiées.

### `cf` {#cf}

Si le composant est associé au contenu dans un fragment de contenu, les informations suivantes peuvent être fournies.

* `name` définit un nom facultatif enregistré dans le JCR pour le composant nouvellement créé.
   * Purement informatif et généralement non affiché dans l’interface utilisateur, contrairement au `title`.
* `cfModel` définit le modèle [ de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md) pour le composant nouvellement créé.
* `cfFolder` définit dans quel dossier le fragment de contenu doit être créé.
* `title` définit le titre du nouveau fragment de contenu.
* `description` définit une description du nouveau fragment de contenu.
* `template` définit les clés/valeurs facultatives à écrire automatiquement dans le fragment de contenu qui vient d’être créé.
   * Utile pour le texte explicatif, d’exemple ou d’espace réservé.

### `cf` peut être intégré {#cf-implied}

Si la page est [instrumentée](/help/implementing/universal-editor/getting-started.md#instrument-page) pour pointer vers un champ de référence, le `cf` est intégré automatiquement.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container" data-aue-prop="field"></div>
```

Dans ce cas, `cf` est intégré automatiquement, car le `data-aue-prop` pointe vers un champ de référence. Sans le `data-aue-prop`, l’éditeur universel intègre automatiquement `page`, car dans ce cas les composants ne sont pas liés via un champ de référence.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container"></div>
```

Les composants sont simplement des sous-nœuds sous la ressource.
