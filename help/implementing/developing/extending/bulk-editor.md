---
title: Configuration de la modification en bloc des propriétés de page
description: Découvrez comment configurer la modification en masse afin de pouvoir modifier les propriétés de plusieurs pages à la fois.
exl-id: 0d10c6b9-8643-479d-adc1-4066d227e83d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 43%

---

# Configuration de la modification en bloc des propriétés de page {#configuring-bulk-editing-of-page-properties}

La [modification en masse des propriétés de page](/help/sites-cloud/authoring/sites-console/page-properties.md#from-the-sites-console-multiple-pages) permet de modifier les propriétés de plusieurs pages à la fois.

## Considérations {#considerations}

Par défaut, les propriétés de page ne sont pas activées pour la modification en masse. Ils doivent être explicitement activés. Lorsque vous définissez les propriétés de la page qui seront disponibles pour la modification en masse, vous devez tenir compte de certaines implications, comme :

* Certains champs sont généralement uniques. Vous devez décider s’il est utile d’activer ces champs pour la modification en masse, lorsqu’une valeur sera appliquée.
   * Par exemple, les titres de page sont presque toujours uniques.
* Certains champs peuvent avoir plusieurs valeurs qui nécessitent une représentation significative lors du rendu.
   * Par exemple, une liste déroulante d’état intitulée **Prêt pour publication**. Il peut y avoir plusieurs valeurs avant la modification en masse, telles que **ready**, **in-review**, **in-progress**, etc.

En raison de la possibilité de plusieurs valeurs, il est recommandé de n’activer que les types de champ suivants pour la modification en masse.

* `/libs/granite/ui/components/foundation/form/textfield`
* `/libs/granite/ui/components/foundation/form/textarea`
* `/libs/granite/ui/components/foundation/form/tagspicker`
* `/libs/granite/ui/components/foundation/form/datepicker`
* `/libs/granite/ui/components/foundation/form/pathbrowser`
* `/libs/granite/ui/components/foundation/form/checkbox`

## Activer un champ {#enabling-a-field}

Ces étapes utilisent `/apps/core/wcm/components/page/v1/page` de l’ [exemple de contenu WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) comme exemple pour activer la modification en masse d’un champ dans un environnement de développement.

1. À l’aide de CRXDE, ouvrez votre composant de page.
1. Accédez au champ requis dans la définition de `cq:dialog`.
1. Définissez la propriété suivante sur le nœud de champ :

   * **Nom** : `allowBulkEdit`
   * **Type** : `Boolean`
   * **Valeur** : `true`

1. Sélectionnez **Enregistrer tout** pour conserver vos mises à jour.

## Limites {#limitations}

La modification en masse des propriétés de page est :

* Non disponible pour les pages d’une Live Copy.
* Uniquement disponible pour les pages avec le même type de ressource.
