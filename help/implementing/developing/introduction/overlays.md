---
title: Recouvrements pour Adobe Experience Manager as a Cloud Service
description: AEM as a Cloud Service applique le principe des recouvrements pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités.
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
source-git-commit: ac760e782f80ee82a9b0604ef64721405fc44ee4
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 96%

---

# Recouvrements dans AEM as a Cloud Service {#overlays-in-aem}

Adobe Experience Manager as a Cloud Service applique le principe des recouvrements pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités telles que la création de page.

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


>[!CAUTION]
>
>Le [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) et les méthodes associées ne peuvent être utilisées qu’avec [Granite](https://www.adobe.io/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html). Cela signifie que la création d’un recouvrement avec une ossature n’est appropriée que pour l’interface utilisateur (IU) tactile standard.

Il est conseillé de recourir aux recouvrements pour de nombreuses modifications ; par exemple, pour configurer vos consoles ou créer votre catégorie de sélection dans l’explorateur de ressources au niveau du panneau latéral (utilisé lors de la création de pages). Elles sont requises pour les raisons suivantes :

* Vous ***ne devez pas* effectuer de modifications dans la `/libs`branche **Les modifications que vous effectuez risquent d’être perdues, car cette branche fait l’objet de modifications chaque fois que des mises à niveau sont appliquées à votre instance.

* Elles centralisent vos modifications dans un seul emplacement ; cela facilite le suivi, la migration, la sauvegarde et/ou le débogage de vos modifications, suivant les besoins.

## Chemins de recherche {#search-paths}

AEM utilise un chemin de recherche pour trouver une ressource, en recherchant (par défaut) d’abord la branche `/apps`, puis la branche `/libs`. Ce mécanisme signifie que votre recouvrement dans `/apps` (et les personnalisations qui y sont définies) est prioritaire.

Dans le cas des recouvrements, la ressource diffusée est un regroupement des ressources et propriétés récupérées, en fonction des chemins de recherche définis dans la configuration OSGi.
