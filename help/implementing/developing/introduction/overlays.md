---
title: Recouvrements pour Adobe Experience Manager as a Cloud Service
description: AEM as a Cloud Service applique le principe des recouvrements pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités.
translation-type: tm+mt
source-git-commit: 8028682f19ba6ba7db6b60a2e5e5f5843f7ac11f
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 100%

---


# Recouvrements dans AEM as a Cloud Service {#overlays-in-aem}

Adobe Experience Manager as a Cloud Service applique le principe des recouvrements pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités telles que la création de page.

<!--
Adobe Experience Manager as a Cloud Service uses the principle of overlays to allow you to extend and customize the [consoles](/help/sites-developing/customizing-consoles-touch.md) and other functionality (for example, [page authoring](/help/sites-developing/customizing-page-authoring-touch.md)).
-->

Recouvrement est un terme qui peut être utilisé dans de nombreux contextes. Dans ce contexte (extension d’AEM as a Cloud Service), le recouvrement désigne l’utilisation de la fonctionnalité prédéfinie et l’application de vos propres définitions par-dessus (afin de personnaliser la fonctionnalité standard).

Dans une instance standard, la fonctionnalité prédéfinie est conservée sous `/libs` et il est recommandé de définir votre recouvrement (vos personnalisations) sous la branche `/apps` (en utilisant un [chemin de recherche](#search-paths) pour résoudre les ressources).

* L’interface utilisateur tactile utilise des recouvrements liés à [Granite](https://helpx.adobe.com/fr/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html) :

   * Méthode

      * Recréez la structure `/libs` appropriée sous `/apps`.

         Cela ne nécessite aucune copie 1:1, car [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) est utilisé pour effectuer des références croisées avec les définitions d’origine qui sont requises. Sling Resource Merger propose des services pour accéder à des ressources et les fusionner par le biais de mécanismes de différenciation (diff).

      * Le cas échéant, effectuez des modifications sous `/apps`.
   * Avantages

      * Plus résistant aux modifications sous `/libs`.
      * Vous ne devez redéfinir que ce qui est réellement nécessaire.


<!-- Still links to reference material in 6.5 -->

>[!CAUTION]
>
>[Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) et les méthodes connexes ne peuvent être utilisées qu’avec [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html). Cela signifie que la création d’un recouvrement avec une ossature n’est appropriée que pour l’interface utilisateur (IU) tactile standard.

Il est conseillé de recourir aux recouvrements pour de nombreuses modifications ; par exemple, pour configurer vos consoles ou créer votre catégorie de sélection dans l’explorateur de ressources au niveau du panneau latéral (utilisé lors de la création de pages). Elles sont requises pour les raisons suivantes :

<!--
Overlays are the recommended method for many changes, such as [configuring your consoles](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) or [creating your selection category to the asset browser in the side panel](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (used when authoring pages). They are required as:
-->

* Vous ***ne devez pas* effectuer de modifications dans la `/libs`branche **Les modifications que vous effectuez risquent d’être perdues, car cette branche fait l’objet de modifications chaque fois que des mises à niveau sont appliquées à votre instance.

* Elles centralisent vos modifications dans un seul emplacement ; cela facilite le suivi, la migration, la sauvegarde et/ou le débogage de vos modifications, suivant les besoins.

## Chemins de recherche {#search-paths}

AEM utilise un chemin de recherche pour trouver une ressource, en recherchant (par défaut) d’abord la branche `/apps`, puis la branche `/libs`. Ce mécanisme signifie que votre recouvrement dans `/apps` (et les personnalisations qui y sont définies) est prioritaire.

Dans le cas des recouvrements, la ressource diffusée est un regroupement des ressources et propriétés récupérées, en fonction des chemins de recherche définis dans la configuration OSGi.

<!--
## Example of Usage {#example-of-usage}

Some examples are covered when:

* [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
* [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)
-->