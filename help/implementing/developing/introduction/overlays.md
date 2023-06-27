---
title: Recouvrements pour Adobe Experience Manager as a Cloud Service
description: AEM as a Cloud Service applique le principe des recouvrements pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités.
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 29%

---

# Recouvrements dans AEM as a Cloud Service {#overlays-in-aem}

Adobe Experience Manager as a Cloud Service applique le principe des recouvrements pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités telles que la création de page.

Recouvrement est un terme qui peut être utilisé dans de nombreux contextes. Dans ce contexte, l’extension d’AEM as a Cloud Service signifie qu’une superposition prend la fonctionnalité prédéfinie et impose vos propres définitions sur celle-ci pour personnaliser la fonctionnalité standard.

Dans une instance standard, la fonctionnalité prédéfinie est conservée sous `/libs` et il est recommandé de définir votre recouvrement (vos personnalisations) sous le `/apps` (à l’aide d’une [chemin de recherche](#search-paths) pour résoudre les ressources).

* L’interface utilisateur tactile utilise [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)Superpositions liées :

   * Méthode

      * Recréez la structure `/libs` appropriée sous `/apps`.

        Cette restructuration ne nécessite pas de copie 1:1, car la variable [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) sert à effectuer des références croisées avec les définitions d’origine qui sont requises. Sling Resource Merger fournit des services pour accéder aux ressources et les fusionner avec des mécanismes de différenciation.

      * Sous `/apps`, effectuez des modifications.

   * Avantages

      * Plus résistant aux modifications sous `/libs`.
      * Ne redéfinissez que ce qui est nécessaire.

>[!CAUTION]
>
>Le [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) et les méthodes associées ne peuvent être utilisées qu’avec [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html). Cette règle signifie que la création d’une superposition avec une ossature n’est appropriée que pour l’interface utilisateur tactile standard.

Les superpositions sont la méthode recommandée pour de nombreuses modifications. Par exemple, lors de la configuration de vos consoles ou de la création de votre catégorie de sélection dans l’explorateur de ressources du panneau latéral (utilisé lors de la création de pages). Ils sont requis pour les raisons suivantes :

* **Dans le `/libs` branche, *ne pas* effectuer des modifications**
Toute modification que vous apportez peut être perdue, car cette branche est sujette à des modifications chaque fois que des mises à niveau sont appliquées à votre instance.

* Ils centralisent vos modifications dans un seul emplacement, ce qui facilite le suivi, la migration, la sauvegarde ou le débogage de vos modifications, le cas échéant.

## Chemins de recherche {#search-paths}

AEM utilise un chemin de recherche pour trouver une ressource. Par défaut, la fonction `/apps` puis la branche `/libs` branche. Ce mécanisme signifie que votre incrustation dans `/apps` (et les personnalisations qui y sont définies) ont la priorité.

Dans le cas des recouvrements, la ressource diffusée est un regroupement des ressources et propriétés récupérées, en fonction des chemins de recherche définis dans la configuration OSGi.
