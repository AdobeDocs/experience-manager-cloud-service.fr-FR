---
title: Incrustations pour Adobe Experience Manager en tant que Cloud Service
description: AEM en tant que Cloud Service utilise le principe des incrustations pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités.
translation-type: tm+mt
source-git-commit: 8028682f19ba6ba7db6b60a2e5e5f5843f7ac11f
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 32%

---


# Overlays in AEM as a Cloud Service {#overlays-in-aem}

L’Adobe Experience Manager en tant que Cloud Service utilise le principe des incrustations pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités (par exemple, la création de pages).

<!--
Adobe Experience Manager as a Cloud Service uses the principle of overlays to allow you to extend and customize the [consoles](/help/sites-developing/customizing-consoles-touch.md) and other functionality (for example, [page authoring](/help/sites-developing/customizing-page-authoring-touch.md)).
-->

Incrustation est un terme qui peut être utilisé dans de nombreux contextes. Dans ce contexte (extension d’AEM en tant que Cloud Service), une incrustation signifie prendre la fonctionnalité prédéfinie et imposer vos propres définitions sur celle-ci (pour personnaliser la fonctionnalité standard).

Dans une instance standard, la fonctionnalité prédéfinie est conservée sous `/libs` et il est recommandé de définir votre incrustation (personnalisations) sous la `/apps` branche (en utilisant un chemin [de](#search-paths) recherche pour résoudre les ressources).

* L’interface utilisateur tactile utilise des incrustations liées à [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html):

   * Méthode

      * Reconstruct the appropriate `/libs` structure under `/apps`.

         This does not require a 1:1 copy, as the [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) is used to cross-reference the original definitions that are required. Sling Resource Merger propose des services pour accéder à des ressources et les fusionner par le biais de mécanismes de différenciation (diff).

      * Make any changes under `/apps`.
   * Avantages

      * Plus résistant aux modifications sous `/libs`.
      * Vous ne devez redéfinir que ce qui est réellement nécessaire.


<!-- Still links to reference material in 6.5 -->

>[!CAUTION]
>
>[Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) et les méthodes connexes ne peuvent être utilisées qu’avec [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html). Cela signifie que la création d’une incrustation avec une ossature n’est appropriée que pour l’interface utilisateur (IU) tactile standard.

Il est conseillé de recourir aux incrustations pour de nombreuses modifications ; par exemple, pour configurer vos consoles ou créer votre catégorie de sélection dans l’explorateur de ressources dans le panneau latéral (utilisé lors de la création de pages). Elles sont requises pour les raisons suivantes :

<!--
Overlays are the recommended method for many changes, such as [configuring your consoles](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) or [creating your selection category to the asset browser in the side panel](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (used when authoring pages). They are required as:
-->

* You ***must not *make changes in the`/libs`branch **Any changes you do make may be lost, because this branch is liable to changes whenever upgrades are applied to your instance.

* Elles centralisent vos modifications dans un seul emplacement ; cela facilite le suivi, la migration, la sauvegarde et/ou le débogage de vos modifications, suivant les besoins.

## Chemins de recherche {#search-paths}

AEM utilise un chemin de recherche pour trouver une ressource, en recherchant (par défaut) d’abord la `/apps` branche, puis la `/libs` branche. This mechanism means that your overlay in `/apps` (and the customizations defined there) will have priority.

Pour les incrustations, la ressource livrée est un agrégat des ressources et des propriétés récupérées, selon les chemins de recherche définis dans la configuration OSGi.

<!--
## Example of Usage {#example-of-usage}

Some examples are covered when:

* [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
* [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)
-->