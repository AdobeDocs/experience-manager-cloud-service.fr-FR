---
title: Organisation des pages
description: Découvrez comment organiser votre site web avec AEM.
exl-id: c57096ca-34fe-4b19-98e0-8f3cd43cf24e
source-git-commit: 1a4c5e618adaef99d82a00e1118d1a0f8536fc14
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 67%

---


# Organisation des pages {#creating-and-organizing-pages}

Découvrez comment organiser votre site web avec AEM. Une fois que vous avez compris comment organiser vos pages, vous pouvez [créer des pages ;](/help/sites-cloud/authoring/sites-console/creating-pages.md) et [gérer les pages de sortie.](/help/sites-cloud/authoring/sites-console/managing-pages.md)

{{edge-delivery-authoring}}

## Organisation du site {#organizing-your-site}

En tant qu’auteur, vous devez organiser votre site dans AEM. Cela implique de créer et de nommer vos pages de contenu de façon à ce que :

* vous puissiez les trouver facilement dans l’environnement de création ;
* les visiteurs sur votre site puissent facilement les parcourir dans l’environnement de publication.

Vous pouvez également vous aider de [dossiers](#creating-a-new-folder) pour organiser votre contenu.

La structure d’un site web est construite comme une arborescence qui contient vos pages de contenu. Les noms de ces pages de contenu sont utilisés pour former les URL, tandis que les titres sont affichés lorsque le contenu de la page est affiché.

Vous trouverez ci-dessous un exemple tiré de la fonction [Tutoriel WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=fr) site, où un article sur les skateparks (`la-skateparks`) est accessible :

`http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

```xml
 /content
 /wknd
  /en
   /music
    /...
   /sports
    /la-skateparks
    /five-gyms-la
    /mountain-bike-routes
   /shopping
    /...
   /art
    /...
   /...
```

Cette structure peut être visualisée à partir du [**Sites** console,](/help/sites-cloud/authoring/sites-console/introduction.md) où vous pouvez parcourir les pages de votre site web et effectuer des actions sur les pages.

## Conventions de dénomination des pages {#page-naming-conventions}

Lors de la création d’une page, il existe deux champs clés :

* **[Titre](#title)** :
   * Il s’affiche pour l’utilisateur dans la console et dans la partie supérieure du contenu de la page lors de la modification.
   * Ce champ est obligatoire.
* **[Nom](#name)** :
   * Il est utilisé pour générer l’URI.
   * L’entrée utilisateur pour ce champ est facultative. S’il n’est pas spécifié, le nom est dérivé du titre. Consultez la section [Restrictions de nom de page et bonnes pratiques](#page-name-restrictions-and-best-practices) pour plus d’informations.

### Restrictions de nom de page et bonnes pratiques {#page-name-restrictions-and-best-practices}

Le **Titre** et le **Nom** de la page peuvent être créés séparément, mais ils sont associés :

* lors de la création d’une page, seul le champ **Titre** est requis. Si aucun **nom** n’est indiqué lors de la création de la page, AEM génère un nom à partir des 64 premiers caractères du titre (examinez la validation présentée ci-dessous). Seuls les 64 premiers caractères sont utilisés dans le cadre de la bonne pratique définie pour les noms de pages courts.
* Si un nom de page est spécifié manuellement par l’auteur, la limite de 64 caractères ne s’applique pas, mais d’autres limitations techniques sur la longueur du nom de la page peuvent s’appliquer.

>[!TIP]
>
>Lorsque vous définissez un nom de page, une règle de base à respecter consiste à faire en sorte que le nom de la page reste court, mais aussi significatif que possible pour faciliter la compréhension du lecteur. Consultez le [Guide de style W3C](https://www.w3.org/Provider/Style/TITLE.html) sur l’élément `title` pour obtenir des informations supplémentaires.
>
>N’oubliez pas que certains navigateurs (par exemple, les anciennes versions d’IE) n’acceptent que les URL n’excédant pas une certaine longueur. C’est pourquoi il existe également une raison technique à garder les noms de pages courts.

Lors de la création d’une page AEM [valide le nom de la page en fonction des conventions ;](/help/implementing/developing/introduction/naming-conventions.md) imposé par AEM et le JCR.

Les caractères minimum autorisés sont :

* `a` à `z`
* `A` à `Z`
* `0` à `9`
* `_` (trait de soulignement)
* `-` (tiret/signe moins)

Vous trouverez la liste complète et détaillée des caractères autorisés dans les [conventions de dénomination](/help/implementing/developing/introduction/naming-conventions.md).

>[!NOTE]
>
>Les noms de pages sont limités à 150 caractères.

### Titre {#title}

Si vous n’indiquez qu’une page **Titre** lors de la création d’une page, AEM délivre la page **Nom** de cette chaîne et [valider le nom en fonction des conventions ;](/help/implementing/developing/introduction/naming-conventions.md) imposé par AEM et JCR.

Un champ **Titre** contenant des caractères non valides sera accepté, mais les caractères non valides seront remplacés pour le nom dérivé. Par exemple :

| Titre | Nom dérivé |
|---|---|
| Schön | `schoen.html` |
| SC%&amp;&#42;ç+ | `sc---c-.html` |

### Nom {#name}

Lorsque vous fournissez une page **Nom** lors de la création d’une page, AEM [valide le nom en fonction des conventions ;](/help/implementing/developing/introduction/naming-conventions.md) imposé par AEM et JCR. Vous ne pouvez pas utiliser de caractères non valides dans le champ **Nom**. Lorsque AEM détecte des caractères non valides, le champ est mis en surbrillance avec un message d’explication.

![Exemple de saisie d’un nom de page non valide](/help/sites-cloud/authoring/assets/organizing-invalid-name.png)

>[!TIP]
>
>Vous devez éviter d’utiliser un code à deux lettres tel que défini par la norme ISO-639-1 comme nom de page, sauf s’il s’agit d’une racine de langue.
>
>Pour plus d’informations, voir [Préparation du contenu pour la traduction](/help/sites-cloud/administering/translation/preparation.md).

## Modèles {#templates}

Dans AEM, une [modèle](/help/sites-cloud/authoring/sites-console/templates.md) est un type spécialisé de page utilisé comme base pour toute nouvelle page en cours de création.

Le modèle définit la structure d’une page, y compris une miniature et d’autres propriétés. Par exemple, vous pouvez avoir des modèles distincts pour les pages de produits, les plans de site et les coordonnées. Les modèles sont constitués de [composants](#components).

AEM comporte plusieurs modèles prêts à l’emploi. Les modèles disponibles dépendent du site web individuel. Les champs clés sont les suivants :

* **Titre** : titre affiché sur la page web obtenue.
* **Nom** - Utilisé lors de l’attribution du nom de la page
* **Modèle** - Liste des modèles utilisables lors de la génération de la nouvelle page

## Composants {#components}

[Composants](/help/implementing/developing/components/overview.md) sont les éléments fournis par AEM afin que vous puissiez ajouter des types de contenu spécifiques. AEM est fourni avec une gamme de composants prêts à l’emploi, appelés [les composants principaux,](/help/implementing/developing/components/overview.md#core-components) qui offrent des fonctionnalités complètes. Voici quelques exemples de composants :

* Texte
* Image
* Titre
* Carrousel
* Et bien plus encore

Une fois que vous avez créé et ouvert une page, vous pouvez [ajouter du contenu à l’aide de composants](/help/sites-cloud/authoring/page-editor/edit-content.md#inserting-a-component), disponibles dans le [navigateur de composants](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser).

>[!TIP]
>
>La [console Composants](/help/sites-cloud/authoring/components-console.md) affiche un aperçu des composants sur votre instance.
