---
title: Recouvrements pour Adobe Experience Manager as a Cloud Service
description: AEM as a Cloud Service applique le principe des recouvrements pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités.
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 93%

---

# Recouvrements dans AEM as a Cloud Service {#overlays-in-aem}

Adobe Experience Manager as a Cloud Service applique le principe des recouvrements pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités telles que la création de page.

Recouvrement est un terme qui peut être utilisé dans de nombreux contextes. Dans ce contexte, l’extension d’AEM as a Cloud Service, le recouvrement désigne l’utilisation de la fonctionnalité prédéfinie et l’application de vos propres définitions par-dessus, afin de personnaliser la fonctionnalité standard.

Dans une instance standard, la fonctionnalité prédéfinie est conservée sous `/libs` et il est recommandé de définir votre recouvrement (vos personnalisations) sous la branche `/apps` (en utilisant un [chemin de recherche](#search-paths) pour résoudre les ressources).

* L’interface utilisateur tactile utilise des recouvrements liés à [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) :

   * Méthode

      * Recréez la structure `/libs` appropriée sous `/apps`.

        Cette restructuration ne nécessite pas de copie 1:1, car le [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) est utilisé pour effectuer des références croisées avec les définitions d’origine qui sont requises. Sling Resource Merger propose des services pour accéder à des ressources et les fusionner avec des mécanismes de différenciation (diff).

      * Sous `/apps`, effectuez des modifications.

   * Avantages

      * Plus résistant aux modifications sous `/libs`.
      * Vous ne devez redéfinir que ce qui est nécessaire.

>[!CAUTION]
>
>[Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) et les méthodes connexes ne peuvent être utilisés qu’avec [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html). Cette règle signifie que la création d’un recouvrement avec un squelette n’est appropriée que pour l’interface utilisateur tactile standard.

Les recouvrements sont la méthode recommandée pour de nombreuses modifications. Par exemple, configurer vos consoles ou créer votre catégorie de sélection dans l’explorateur de ressources du panneau latéral (utilisé lors de la création de pages). Ils sont requis pour les raisons suivantes :

* **Dans la branche `/libs`, n’effectuez *aucune* modifications**.
Les modifications que vous effectuez risquent d’être perdues, car cette branche fait l’objet de modifications chaque fois que des mises à niveau sont appliquées à votre instance.

* Ils centralisent vos modifications dans un seul emplacement ; ils facilitent le suivi, la migration, la sauvegarde ou le débogage de vos modifications, suivant les besoins.

## Chemins de recherche {#search-paths}

AEM utilise un chemin de recherche pour trouver une ressource, en recherchant, par défaut, d’abord la branche `/apps`, puis la branche `/libs`. Ce mécanisme signifie que votre recouvrement dans `/apps` (et les personnalisations qui y sont définies) est prioritaire.

Dans le cas des recouvrements, la ressource diffusée est un regroupement des ressources et propriétés récupérées, en fonction des chemins de recherche définis dans la configuration OSGi.
