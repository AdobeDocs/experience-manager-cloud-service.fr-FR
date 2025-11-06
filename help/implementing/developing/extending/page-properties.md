---
title: Personnaliser les vues des propriétés de la page
description: Découvrez comment les propriétés de page sont affichées et modifiées par les auteurs.
exl-id: 363b3c2d-f965-485f-bdae-2ea5b4cecb83
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 58%

---

# Personnaliser les vues des propriétés de la page{#customizing-views-of-page-properties}

Chaque page comporte un ensemble de [propriétés](/help/sites-cloud/authoring/sites-console/page-properties.md) qui peuvent être affichées et modifiées par les utilisateurs. Certains sont requis lors de la création de la page (création de vue), d’autres peuvent être affichés et modifiés (modification de vue) ultérieurement. Ces propriétés de page sont définies et mises à la disposition des utilisateurs dans la boîte de dialogue (`cq:dialog`) du composant de page approprié.

Le statut par défaut de chaque propriété de la page est :

* Masqué dans la vue de création (assistant **Créer une page**, par exemple)

* Disponible dans la vue d’édition (par exemple, **Afficher les propriétés**)

Les champs doivent être configurés spécifiquement si une modification est requise. Pour ce faire, utilisez la les propriétés de nœud appropriées :

* Propriété de page qui doit être disponible en mode de création (assistant **Créer une page**, par exemple) :

   * Nom : `cq:showOnCreate`
   * Type : `Boolean`

* Propriété de page qui doit être disponible dans la vue d’édition, par exemple l’option **Vue**/**Modifier** **Propriétés** :

   * Nom : `cq:hideOnEdit`
   * Type : `Boolean`

>[!TIP]
>
>Consultez le [Tutoriel sur l’extension des propriétés de page](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html?lang=fr) pour obtenir un guide sur la personnalisation des propriétés de page.

## Configuration des propriétés de page {#configuring-your-page-properties}

Vous pouvez également configurer les champs disponibles en configurant la boîte de dialogue de votre composant de page et en appliquant les propriétés de nœud appropriées.

Par exemple, l’assistant [**Créer une page**](/help/sites-cloud/authoring/sites-console/creating-pages.md#creating-a-new-page) affiche, par défaut, les champs regroupés sous **Autres titres et description**. Pour masquer ces derniers, définissez la configuration suivante :

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

   La section **Autres titres et description** ne s’affichera plus dans l’assistant **Créer une page**.

>[!NOTE]
>
>Lors de la configuration des propriétés de page pour une utilisation avec des Live Copies, voir [&#x200B; Extension de Multi Site Manager &#x200B;](/help/implementing/developing/extending/msm.md#configuring-msm-locks-on-page-properties) pour plus d’informations.

## Exemple de configuration des propriétés de page {#sample-configuration-of-page-properties}

Cet exemple illustre la technique dialog diff de [&#x200B; Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) y compris l’utilisation de [`sling:orderBefore`](/help/implementing/developing/introduction/sling-resource-merger.md#properties). Il illustre également l’utilisation de `cq:showOnCreate` et de `cq:hideOnEdit`.

Vous trouverez le code de cette page sur [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog).
