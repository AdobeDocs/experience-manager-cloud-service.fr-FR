---
title: Personnalisation des consoles
description: Découvrez les différentes options fournies par AEM pour personnaliser les consoles de votre instance de création.
exl-id: 832f9a86-07c4-4229-a0dc-8ad50a8195b0
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 27%

---

# Personnalisation des consoles {#customizing-consoles}

AEM fournit des options pour personnaliser les consoles (et la [fonctionnalité de création de pages](/help/implementing/developing/extending/page-authoring.md)) de votre instance de création.

## Clientlibs {#clientlibs}

Clientlibs vous permet d’étendre l’implémentation par défaut afin d’offrir de nouvelles fonctionnalités, tout en réutilisant des fonctions, des objets et des méthodes standard. Lors de la personnalisation avec clientlibs, vous pouvez créer votre propre bibliothèque cliente sous `/apps.` Par exemple, il peut contenir le code requis pour votre composant personnalisé.

Voir [Utilisation de bibliothèques côté client sur AEM as a Cloud Service](/help/implementing/developing/introduction/clientlibs.md).

## Recouvrements {#overlays}

Les recouvrements reposent sur des définitions de nœud et vous permettent de recouvrir la fonctionnalité standard disponible sous `/libs` avec votre propre fonctionnalité personnalisée sous `/apps`. Lors de la création d’une superposition, une copie 1:1 de l’original n’est pas nécessaire, car [&#x200B; fusion de ressources Sling &#x200B;](/help/implementing/developing/introduction/sling-resource-merger.md) permet l’héritage.

Les recouvrements peuvent être utilisés de différentes manières pour étendre vos consoles AEM. Vous trouverez plusieurs exemples dans les sections suivantes.

Voir aussi [Recouvrements pour Adobe Experience Manager as a Cloud Service](/help/implementing/developing/introduction/overlays.md).

>[!TIP]
>
>Si vous souhaitez personnaliser l’expérience de création, consultez [Personnalisation de la création de pages](/help/implementing/developing/extending/page-authoring.md).

## Personnaliser l’affichage par défaut d’une console {#customizing-the-default-view-for-a-console}

Vous pouvez personnaliser l’affichage par défaut (colonne, carte, liste) d’une console :

* Vous pouvez réorganiser les vues en superposant l’entrée requise sous :

   * `/libs/wcm/core/content/sites/jcr:content/views`

   * La première entrée est la valeur par défaut.

   * Les nœuds disponibles correspondent aux options d’affichage disponibles :

      * `column`
      * `card`
      * `list`

* Par exemple, dans un recouvrement pour une liste :

   * `/apps/wcm/core/content/sites/jcr:content/views/list`

   * Définissez la propriété suivante :

      * **Nom** : `sling:orderBefore`
      * **Type** : `String`
      * **Valeur** : `column`

### Ajouter une nouvelle action à la barre d’outils {#add-a-new-action-to-the-toolbar}

Vous pouvez créer vos propres composants et inclure les bibliothèques clientes correspondantes pour les actions personnalisées.

* Par exemple, vous pouvez créer une action **Promouvoir sur les médias sociaux** à l’adresse :

   * `/apps/wcm/core/clientlibs/sites/js/socialmedia.js`

   * Elle peut ensuite être connectée à un élément de la barre d’outils sur la console :

   * `/apps/<yourProject>/admin/ext/launches`

   * Par exemple, en mode de sélection :

   * `content/jcr:content/body/content/header/items/selection/items/socialmedia`

### Restreindre une action de barre d’outils à un groupe spécifique {#restrict-a-toolbar-action-to-a-specific-group}

Vous pouvez utiliser une condition de rendu personnalisée pour superposer l’action standard et imposer des conditions spécifiques qui doivent être remplies avant son rendu.

Par exemple, vous pouvez créer un composant pour contrôler les conditions de rendu en fonction d’un groupe :

* `/apps/myapp/components/renderconditions/group`

Pour les appliquer à l’action **Créer un site** sur la console Sites :

* `/libs/wcm/core/content/sites`

1. Créez le recouvrement :

   * `/apps/wcm/core/content/sites`

1. Ajoutez ensuite la condition de rendu pour l’action :

   * `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

En utilisant des propriétés sur ce nœud, vous pouvez définir les `groups` autorisés à effectuer l’action spécifique ; par exemple, les `administrators`.

### Personnalisation des colonnes dans la vue Liste {#customizing-columns-in-list-view}

Pour personnaliser les colonnes dans la vue Liste :

1. Recouvrez la liste des colonnes disponibles.

   * Sur le nœud :

     `/apps/wcm/core/content/common/availablecolumns`

1. Ajoutez des colonnes ou supprimez des colonnes existantes.

Si vous souhaitez insérer des données supplémentaires, vous devez écrire un [PageInfoProvider](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) avec une propriété `pageInfoProviderType`.

>[!NOTE]
>
>Cette fonctionnalité est optimisée pour les colonnes de champs de texte. Pour d’autres types de données, il est possible de superposer des `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` dans `/apps`.

### Filtrer les ressources {#filtering-resources}

Lors de l’utilisation d’une console, un utilisateur doit souvent effectuer un choix parmi des ressources telles que des pages, des composants ou des ressources. Il peut s’agir d’une liste dans laquelle l’auteur doit choisir un élément.

Pour maintenir la liste à une taille raisonnable et adaptée au cas d’utilisation, un filtre peut être mis en œuvre sous la forme d’un prédicat personnalisé. Voir [Personnalisation de la création de pages](/help/implementing/developing/extending/page-authoring.md#filtering-resources) pour plus d’informations.
