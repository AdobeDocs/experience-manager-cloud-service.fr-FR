---
title: Personnaliser la création de pages
description: Découvrez les mécanismes fournis par AEM as a Cloud Service pour personnaliser la fonctionnalité de création de pages.
exl-id: 98d3c7ab-46d2-4e8d-b0da-5c8a7b398135
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 55%

---

# Personnaliser la création de pages {#customizing-page-authoring}

Adobe Experience Manager as a Cloud Service fournit des mécanismes pour vous permettre de personnaliser la fonctionnalité de création de pages (et les [consoles](/help/implementing/developing/extending/consoles.md)) de votre instance de création.

## Clientlibs {#clientlibs}

Les bibliothèques clientes (clientlibs) vous permettent d’étendre l’implémentation par défaut afin d’activer de nouvelles fonctionnalités, tout en réutilisant les fonctions, objets et méthodes standard.

Lors de la personnalisation, vous pouvez créer votre propre bibliothèque cliente sous `/apps.` La nouvelle bibliothèque cliente doit :

* Dépendent de l’`cq.authoring.editor.sites.page` de la bibliothèque cliente de création.
* Faire partie de la catégorie de `cq.authoring.editor.sites.page.hook` appropriée.

Voir [Utilisation de bibliothèques côté client sur AEM as a Cloud Service](/help/implementing/developing/introduction/clientlibs.md).

## Recouvrements {#overlays}

Les recouvrements reposent sur des définitions de nœud et vous permettent de recouvrir la fonctionnalité standard en `/libs` avec votre propre fonctionnalité personnalisée dans `/apps`.

Lors de la création d’une superposition, une copie 1:1 de l’original n’est pas nécessaire, car la [fusion de ressources sling](/help/implementing/developing/introduction/sling-resource-merger.md) permet l’héritage.

Pour plus d’informations, voir la documentation [JS](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html?lang=fr).

Pour plus d’informations sur les recouvrements, voir [Recouvrements pour Adobe Experience Manager as a Cloud Service](/help/implementing/developing/introduction/overlays.md).

## Ajouter un nouveau calque (mode) {#add-new-layer-mode}

Lorsque vous modifiez une page, plusieurs [modes](/help/sites-cloud/authoring/page-editor/introduction.md#page-modes) sont disponibles. Ces modes sont implémentés à l’aide de [calques](/help/implementing/developing/introduction/ui-structure.md#layer). Ils permettent d’accéder à différents types de fonctionnalités pour le même contenu de page. Les modes AEM standard incluent la modification, la mise en page, le développement, la distorsion du temps, le statut de Live Copy et le ciblage.

### Exemple de calque : statut de Live Copy {#layer-example-live-copy-status}

Une instance AEM standard fournit la couche MSM. Cela permet d’accéder aux données relatives à la [gestion multisite](/help/sites-cloud/administering/msm/overview.md) et de les mettre en évidence dans le calque.

Pour obtenir une démonstration, vous pouvez modifier n’importe quelle copie de langue dans l’exemple de contenu [WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) et sélectionner le mode **Statut de la Live Copy**.

Vous trouverez la définition du calque MSM (pour référence) à l’emplacement suivant :

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### Exemple de code {#code-sample}

Voici un exemple de package qui montre comment créer un calque (mode) pour la vue MSM.

Vous trouverez le code de cette page sur [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode).

## Ajouter une nouvelle catégorie de sélection à l’explorateur de ressources {#add-new-selection-category-to-asset-browser}

L’explorateur de ressources affiche des ressources de différents types/catégories (par exemple, des images et des documents). Les ressources peuvent également être filtrées par ces catégories.

### Exemple de code {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr` est un exemple de package qui montre comment ajouter un groupe à l’outil de recherche de ressources. Cet exemple se connecte au flux public de [Flickr](https://www.flickr.com) et l’affiche dans le panneau latéral.

Vous trouverez le code de cette page sur [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr).

## Filtrer les ressources {#filtering-resources}

Lors de la création de pages, l’utilisateur doit souvent effectuer une sélection parmi les ressources d’une liste.

Pour maintenir la liste à une taille raisonnable et adaptée au cas d’utilisation, un filtre peut être mis en œuvre sous la forme d’un prédicat personnalisé. Par exemple, si le composant Granite `pathbrowser` est utilisé pour permettre à l’utilisateur de sélectionner le chemin d’accès à une ressource particulière, les chemins d’accès présentés peuvent être filtrés comme suit :

* Mettez en œuvre le prédicat personnalisé en implémentant l’interface [`com.day.cq.commons.predicate.AbstractNodePredicate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/predicate/package-summary.html).
* Spécifiez un nom pour le prédicat et faites-y référence lors de l’utilisation de `pathbrowser`.

Pour plus d’informations sur la création d’un prédicat personnalisé, consultez [cet article](/help/implementing/developing/introduction/query-builder-custom-predicate.md).

## Ajouter une nouvelle action à une barre d’outils de composant {#add-new-action-to-a-component-toolbar}

Chaque composant comporte généralement une barre d’outils qui permet d’accéder à un éventail d’actions pouvant être entreprises sur ce composant.

### Exemple de code {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot` est un exemple de package qui montre comment créer une action de barre d’outils personnalisée pour effectuer le rendu de composants.

Vous trouverez le code de cette page sur [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot).

## Ajouter un nouvel éditeur statique {#add-new-in-place-editor}

### Éditeur statique standard {#standard-in-place-editor}

Dans une installation AEM standard :

1. `/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js` contient les définitions des différents éditeurs disponibles.

1. Il existe une connexion entre l’éditeur et chaque type de ressource (comme dans le composant) qui peut l’utiliser :

   * `cq:inplaceEditing`

     par exemple :

      * `/libs/foundation/components/text/cq:editConfig`
      * `/libs/foundation/components/image/cq:editConfig`

         * property : `editorType`

           Définit le type d’éditeur en ligne utilisé lorsqu’une édition statique est déclenchée pour ce composant ; par exemple, `text`, `textimage`, `image`, `title`.

1. Les informations de configuration supplémentaires de l’éditeur peuvent être configurées à l’aide d’un nœud `config` contenant des configurations et d’un nœud `plugin` pour contenir les informations de configuration du plug-in nécessaire.


Voici un exemple de définition des proportions pour le module externe de recadrage d’image du composant d’image.

```xml
   <cq:inplaceEditing
           jcr:primaryType="cq:InplaceEditingConfig"
           active="{Boolean}true"
           editorType="image">
           <config jcr:primaryType="nt:unstructured">
               <plugins jcr:primaryType="nt:unstructured">
                   <crop jcr:primaryType="nt:unstructured">
                       <aspectRatios jcr:primaryType="nt:unstructured">
                           <_x0031_6-10
                               jcr:primaryType="nt:unstructured"
                               name="16 : 10"
                               ratio="0.625"/>
                       </aspectRatios>
                   </crop>
               </plugins>
           </config>
   </cq:inplaceEditing>
```

>[!NOTE]
>
>Dans AEM, les rapports de recadrage, tels qu’ils sont définis par la propriété `ratio`, sont définis sous la forme **hauteur/largeur**.  Cela diffère de la définition conventionnelle de la largeur/hauteur. Cela a été créée pour des raisons de compatibilité héritée. Les utilisateurs chargés de la création ne percevront aucune différence, à condition que vous définissiez clairement la propriété `name`, car c’est cette dernière qui s’affiche dans l’interface utilisateur.

#### Création d’un éditeur statique {#creating-a-new-in-place-editor}

Pour mettre en œuvre un nouvel éditeur statique (au sein de votre bibliothèque cliente) :

1. Implémentez les éléments suivants :

   * `setUp`
   * `tearDown`

1. Enregistrez l’éditeur (comprend le constructeur) :

   * `editor.register`

1. Fournissez la connexion entre l’éditeur et chaque type de ressource (comme dans le composant) qui peut l’utiliser.

#### Exemple de code pour la création d’un éditeur statique {#code-sample-for-creating-a-new-in-place-editor}

`aem-authoring-extension-inplace-editor` est un exemple de package qui montre comment créer un éditeur statique dans AEM.

Vous trouverez le code de cette page sur [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor).

## Ajouter une nouvelle action de page {#add-a-new-page-action}

Pour ajouter une nouvelle action de page à la barre d’outils de la page, par exemple une action **Retour à Sites** (console).

### Exemple de code {#code-sample-3}

`aem-authoring-extension-header-backtosites` est un exemple de package qui montre comment créer une action de barre d’en-tête personnalisée pour revenir à la console Sites.

Vous trouverez le code de cette page sur [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites).

## Personnalisation du workflow Demander l’activation {#customizing-the-request-for-activation-workflow}

Le workflow d’usine, **Demande d’activation** :

* apparaît automatiquement dans le menu approprié lorsqu’un auteur de contenu **n’a pas** les droits de réplication appropriés, mais **dispose** de l’abonnement des utilisateurs et auteurs de la gestion des ressources numériques ;

* sinon, rien ne s’affiche, car les droits de réplication ont été supprimés.

Pour bénéficier d’un comportement personnalisé lors d’une telle activation, vous pouvez incruster le workflow **Demande d’activation** :

1. Dans `/apps`, recouvrez l’`/libs/wcm/core/content/common/managepublicationwizard` de l’assistant **Sites**

   * Cela a pour effet de remplacer l’instance commune de `/libs/cq/gui/content/common/managepublicationwizard`.

1. Mettez à jour le modèle de workflow et les configurations/scripts associés selon les besoins.
1. Retirez à tous les utilisateurs appropriés le droit dont ils disposent sur l’action `replicate` pour toutes les pages pertinentes. Pour déclencher ce workflow en tant qu’action par défaut lorsque l’un des utilisateurs tente de publier (ou de répliquer) une page.
