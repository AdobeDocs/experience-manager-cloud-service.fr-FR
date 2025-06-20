---
title: Configuration de la modification en bloc des propriétés de page
description: Découvrez comment configurer la modification en bloc afin de pouvoir modifier les propriétés de plusieurs pages à la fois.
exl-id: 0d10c6b9-8643-479d-adc1-4066d227e83d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 3238b11cdd891cf18048199d4103397e3af75edf
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 43%

---

# Configuration de la modification en bloc des propriétés de page {#configuring-bulk-editing-of-page-properties}

La [modification en masse des propriétés de page](/help/sites-cloud/authoring/sites-console/edit-page-properties.md#from-the-sites-console-multiple-pages) permet de modifier les propriétés de plusieurs pages à la fois.

## Considérations {#considerations}

Par défaut, les propriétés de page ne sont pas activées pour la modification en bloc. Ils doivent être activés explicitement. Lorsque vous définissez les propriétés de la page qui seront disponibles pour la modification en masse, vous devez tenir compte de certaines implications, comme :

* Certains champs sont généralement uniques. Vous devez décider s’il est utile d’activer ces champs pour la modification en masse, lorsqu’une valeur sera appliquée.
   * Par exemple, les titres de page sont presque toujours uniques.
* Certains champs peuvent avoir plusieurs valeurs, ce qui nécessite une représentation significative lors du rendu.
   * Par exemple, une liste déroulante de statut intitulée **Prêt pour publication**. Ce champ peut avoir plusieurs valeurs avant la modification en masse, telles que **prêt**, **en cours de révision**, **en cours**, etc.

En raison du risque de valeurs multiples, il est recommandé d’activer uniquement les types de champ suivants pour la modification en bloc.

* `/libs/granite/ui/components/foundation/form/textfield`
* `/libs/granite/ui/components/foundation/form/textarea`
* `/libs/granite/ui/components/foundation/form/tagspicker`
* `/libs/granite/ui/components/foundation/form/datepicker`
* `/libs/granite/ui/components/foundation/form/pathbrowser`
* `/libs/granite/ui/components/foundation/form/checkbox`

## Activer un champ {#enabling-a-field}

Ces étapes utilisent les `/apps/core/wcm/components/page/v1/page` de l’exemple de contenu [WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) comme exemple pour activer la modification en masse sur un champ dans un environnement de développement.

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
