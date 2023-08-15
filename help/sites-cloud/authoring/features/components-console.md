---
title: Console des composants
description: La console Composants vous permet de parcourir tous les composants définis pour votre instance.
exl-id: f4949331-5302-46d3-a004-b813bb95ec2f
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 68%

---

# Console des composants {#components-console}

La console Composants vous permet de parcourir tous les composants définis pour votre instance et d’afficher les informations clés de chaque composant.

Elle est accessible via **Outils** -> **Général** -> **Composants**. En l’absence d’arborescence, seul la vue Liste est disponible.

![Console Composants](/help/sites-cloud/authoring/assets/components-console.png)

>[!NOTE]
>
>La console des composants affiche tous les composants du système. L’[Explorateur de composants](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) affiche les composants qui sont disponibles pour les auteurs et masque tous les groupes de composants qui commencent par un point (`.`).

## Rechercher {#search-field}

Avec l’icône **Contenu uniquement** (en haut à gauche), vous pouvez ouvrir le panneau de **recherche** pour rechercher et/ou filtrer les composants :

![Recherche dans la console des composants](/help/sites-cloud/authoring/assets/components-console-search.png)

### Détails des composants {#component-details}

Pour afficher des détails sur un composant spécifique, appuyez/cliquez sur la ressource requise. Trois onglets sont proposés :

* **Propriétés**

  ![Propriétés de la console Composants](/help/sites-cloud/authoring/assets/components-console-properties.png)

  L’onglet Propriétés vous permet d’effectuer les opérations suivantes :

   * Afficher les propriétés générales du composant.
      * Observez comment l’icône ou l’abréviation a été définie pour le composant. <!-- View how the [icon or abbreviation has been defined](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) for the component.-->
      * Cliquez sur la source de l’icône pour accéder à ce composant.
   * Afficher la variable **Type de ressource** et **Resource Super Type** (s’il est défini) pour le composant.
      * Cliquez sur le type de super-ressource pour accéder à ce composant.

  >[!NOTE]
  >
  >Étant donné que les `/apps` ne sont pas modifiables à l’exécution, la console Composants est en lecture seule.

* **Politiques**

  ![Politiques de la console de composants](/help/sites-cloud/authoring/assets/components-console-policies.png)

* **Utilisation en direct**

  ![Utilisation en direct des composants](/help/sites-cloud/authoring/assets/components-console-live-usage.png)

  >[!CAUTION]
  >
  >En raison de la nature des informations collectées pour cette vue, la collecte/l’affichage de ces informations peut nécessiter un certain temps.

* **Documentation**

  Si le développeur a fourni la documentation du composant, elle apparaîtra dans l’onglet **Documentation**. Si aucune documentation n’est disponible, l’onglet **Documentation** n’est pas affiché. <!-- If the developer has provided [documentation for the component](/help/sites-developing/developing-components.md#documenting-your-component), it will appear on the **Documentation** tab. If there is no documentation available, the **Documentation** tab will not be shown.-->

  ![Documentation sur les composants](/help/sites-cloud/authoring/assets/components-console-documentation.png)
