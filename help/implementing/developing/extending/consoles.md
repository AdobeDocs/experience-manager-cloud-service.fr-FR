---
title: Personnalisation des consoles
description: Découvrez les différentes options fournies par AEM pour personnaliser les consoles de votre instance de création.
exl-id: 832f9a86-07c4-4229-a0dc-8ad50a8195b0
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 27%

---

# Personnalisation des consoles {#customizing-consoles}

AEM fournit des options pour personnaliser les consoles (et la [fonctionnalité de création de page](/help/implementing/developing/extending/page-authoring.md)) de votre instance de création.

## Clientlibs {#clientlibs}

Les bibliothèques côté client vous permettent d’étendre l’implémentation par défaut afin d’offrir de nouvelles fonctionnalités, tout en réutilisant les fonctions, objets et méthodes standard. Lors de la personnalisation avec clientlibs, vous pouvez créer votre propre clientlib sous `/apps.`. Par exemple, il peut contenir le code requis pour votre composant personnalisé.

Voir [Utilisation de bibliothèques côté client sur AEM as a Cloud Service](/help/implementing/developing/introduction/clientlibs.md).

## Recouvrements {#overlays}

Les superpositions sont basées sur des définitions de noeud et vous permettent de superposer la fonctionnalité standard trouvée sous `/libs` avec votre propre fonctionnalité personnalisée sous `/apps`. Lors de la création d’une superposition, une copie 1:1 de l’original n’est pas nécessaire, car [Sling resource merge](/help/implementing/developing/introduction/sling-resource-merger.md) permet l’héritage.

Les incrustations peuvent être utilisées de différentes manières pour étendre vos consoles AEM. Plusieurs exemples sont présentés dans les sections suivantes.

Voir aussi [Recouvrements pour Adobe Experience Manager as a Cloud Service](/help/implementing/developing/introduction/overlays.md).

>[!TIP]
>
>Si les options de personnalisation de l’expérience de création vous intéressent, reportez-vous à la section [Personnalisation de la création de page](/help/implementing/developing/extending/page-authoring.md).

## Personnaliser l’affichage par défaut d’une console {#customizing-the-default-view-for-a-console}

Vous pouvez personnaliser l’affichage par défaut (colonne, carte, liste) d’une console :

* Vous pouvez réorganiser les vues en recouvrant l’entrée requise sous :

   * `/libs/wcm/core/content/sites/jcr:content/views`

   * La première entrée est la valeur par défaut.

   * Les nœuds disponibles correspondent aux options d’affichage disponibles :

      * `column`
      * `card`
      * `list`

* Par exemple, dans une superposition pour une liste :

   * `/apps/wcm/core/content/sites/jcr:content/views/list`

   * Définissez la propriété suivante :

      * **Nom** : `sling:orderBefore`
      * **Type** : `String`
      * **Valeur** : `column`

### Ajouter une nouvelle action à la barre d’outils {#add-a-new-action-to-the-toolbar}

Vous pouvez créer vos propres composants et inclure les bibliothèques clientes correspondantes pour les actions personnalisées.

* Par exemple, vous pouvez créer une action **Convertir en médias sociaux** à l’adresse :

   * `/apps/wcm/core/clientlibs/sites/js/socialmedia.js`

   * Elle peut ensuite être connectée à un élément de la barre d’outils sur la console :

   * `/apps/<yourProject>/admin/ext/launches`

   * Par exemple, en mode de sélection :

   * `content/jcr:content/body/content/header/items/selection/items/socialmedia`

### Limitation d’une action de barre d’outils à un groupe spécifique {#restrict-a-toolbar-action-to-a-specific-group}

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

### Personnalisation des colonnes en mode Liste {#customizing-columns-in-list-view}

Pour personnaliser les colonnes dans la vue Liste :

1. Recouvrez la liste des colonnes disponibles.

   * Sur le nœud :

     `/apps/wcm/core/content/common/availablecolumns`

1. Ajoutez vos nouvelles colonnes ou supprimez celles existantes.

Si vous souhaitez insérer des données supplémentaires, vous devez écrire un [PageInfoProvider](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) avec une propriété `pageInfoProviderType`.

>[!NOTE]
>
>Cette fonctionnalité est optimisée pour les colonnes de champs de texte. Pour les autres types de données, il est possible de superposer `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` dans `/apps`.

### Filtrer les ressources {#filtering-resources}

Lors de l’utilisation d’une console, l’utilisateur doit souvent effectuer une sélection dans des ressources telles que des pages, des composants ou des ressources. Cela peut prendre la forme d’une liste à partir de laquelle l’auteur doit choisir un élément.

Pour maintenir la liste à une taille raisonnable et adaptée au cas d’utilisation, un filtre peut être mis en œuvre sous la forme d’un prédicat personnalisé. Pour plus d’informations, voir [Personnalisation de la création de page](/help/implementing/developing/extending/page-authoring.md#filtering-resources) .
