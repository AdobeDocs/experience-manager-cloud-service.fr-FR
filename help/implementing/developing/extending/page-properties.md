---
title: Personnaliser les vues des propriétés de la page
description: Découvrez comment les propriétés de page sont affichées et modifiées par les auteurs.
source-git-commit: f159f0ef86c2b82da4e7308a0892b4947b6e43fb
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 43%

---


# Personnaliser les vues des propriétés de la page{#customizing-views-of-page-properties}

Chaque page comporte un ensemble de [properties](/help/sites-cloud/authoring/fundamentals/page-properties.md) qui peuvent être affichés et modifiés par les utilisateurs. Certaines sont requises lors de la création de la page (création d’une vue), d’autres peuvent être affichées et modifiées ultérieurement (modification d’une vue). Ces propriétés de page sont définies et mises à la disposition des utilisateurs dans la boîte de dialogue (`cq:dialog`) du composant de page approprié.

Le statut par défaut de chaque propriété de la page est :

* Masqué dans la vue de création (par exemple : **Créer une page** assistant)

* Disponible dans la vue d’édition (par exemple, **Afficher les propriétés**)

Les champs doivent être configurés spécifiquement si une modification est requise. Pour ce faire, utilisez les propriétés de noeud appropriées :

* Propriété de page à rendre disponible dans la vue de création (par exemple : **Créer une page** assistant) :

   * Nom : `cq:showOnCreate`
   * Type : `Boolean`

* Propriété de page à afficher dans la vue d’édition, telle que **Affichage**/**Modifier**  **Propriétés** option :

   * Nom : `cq:hideOnEdit`
   * Type : `Boolean`

>[!TIP]
>
>Consultez le [Tutoriel sur l’extension des propriétés de page](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html?lang=fr) pour obtenir un guide sur la personnalisation des propriétés de page.

## Configuration des propriétés de page {#configuring-your-page-properties}

Vous pouvez également configurer les champs disponibles en configurant la boîte de dialogue de votre composant de page et en appliquant les propriétés de noeud appropriées.

Par exemple, l’assistant [**Créer une page**](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) affiche, par défaut, les champs regroupés sous **Autres titres et description**. Pour masquer ces derniers, définissez la configuration suivante :

1. Créez votre composant de page sous `/apps`.
1. Créez un remplacement (à l’aide de la méthode *dialog diff* fournie par [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md)) pour la section `basic` de votre composant de page ; par exemple :

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

1. Définissez la propriété `path` sur `basic` pour pointer vers le remplacement de l’onglet de base (voir également l’étape suivante). Par exemple :

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Créez un remplacement de la section `basic` - `moretitles` à l’emplacement correspondant ; par exemple :

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Appliquez la propriété de nœud appropriée :

   * **Nom** : `cq:showOnCreate`
   * **Type** : `Boolean`
   * **Valeur** : `false`

   La variable **Autres titres et description** ne s’affichera plus dans la section **Créer une page** assistant.

>[!NOTE]
>
>Lors de la configuration des propriétés de page à utiliser avec des Live Copies, consultez le document . [Extension du Multi Site Manager](/help/implementing/developing/extending/msm.md#configuring-msm-locks-on-page-properties) pour plus d’informations.

## Exemple de configuration des propriétés de page {#sample-configuration-of-page-properties}

Cet exemple illustre la technique de comparaison des boîtes de dialogue de [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) y compris l’utilisation de [`sling:orderBefore`](/help/implementing/developing/introduction/sling-resource-merger.md#properties). Il illustre également l’utilisation de `cq:showOnCreate` et de `cq:hideOnEdit`.

Vous trouverez le code de cette page sur [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
