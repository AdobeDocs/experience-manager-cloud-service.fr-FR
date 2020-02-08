---
title: Console des composants
description: La console Composants vous permet de parcourir tous les composants définis pour votre instance.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Console des composants {#components-console}

La console Composants vous permet de parcourir tous les composants définis pour votre instance et d&#39;afficher les informations clés de chaque composant.

It can be accessed from **Tools ->** **General ->** **Components**. Comme il n’existe pas de structure d’arborescence pour les composants, seule la vue Liste est disponible.

![La console Composants](/help/sites-cloud/authoring/assets/components-console.png)

>[!NOTE]
>
>La console Composants affiche tous les composants du système. L’[Explorateur de composants](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) affiche les composants qui sont disponibles pour les auteurs et masque tous les groupes de composants qui commencent par un point ( `.`).

## Recherche {#search-field}

Avec l’icône **Contenu uniquement** (en haut à gauche), vous pouvez ouvrir le panneau de **recherche** pour rechercher et/ou filtrer les composants : 

![Recherche dans la console des composants](/help/sites-cloud/authoring/assets/components-console-search.png)

### Détails des composants {#component-details}

Pour afficher les détails correspondant à un composant spécifique, appuyez/cliquez sur la ressource requise. Trois onglets fournissent :

* **Propriétés**

   ![Propriétés de la console Composants](/help/sites-cloud/authoring/assets/components-console-properties.png)

   L’onglet Propriétés vous permet d’effectuer les opérations suivantes :

   * Afficher les propriétés générales du composant.
      * Observez comment l’icône ou l’abréviation a été définie pour le composant. <!-- View how the [icon or abbreviation has been defined](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) for the component.-->
      * Cliquez sur la source de l’icône pour accéder à ce composant.
   * Affichez le **Type de ressource** et le **Type de super-ressource** (s’il est défini) du composant.
      * Cliquez sur le type de super-ressource pour accéder à ce composant.
   >[!NOTE]
   >
   >Because `/apps` is not editable at runtime, the Components Console is read-only.

* **Stratégies**

   ![Stratégies de la console de composants](/help/sites-cloud/authoring/assets/components-console-policies.png)

* **Utilisation en direct**

   ![Utilisation en direct des composants](/help/sites-cloud/authoring/assets/components-console-live-usage.png)

   >[!CAUTION]
   >
   >En raison de la nature des informations collectées pour cette vue, la collecte/l’affichage de ces informations peut nécessiter un certain temps. 

* **Documentation**

   Si le développeur a fourni la documentation du composant, elle apparaîtra dans l’onglet **Documentation**. Si aucune documentation n’est disponible, l’onglet **Documentation** n’est pas affiché. <!-- If the developer has provided [documentation for the component](/help/sites-developing/developing-components.md#documenting-your-component), it will appear on the **Documentation** tab. If there is no documentation available, the **Documentation** tab will not be shown.-->

   ![Documentation sur les composants](/help/sites-cloud/authoring/assets/components-console-documentation.png)
