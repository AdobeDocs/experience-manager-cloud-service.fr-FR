---
title: Configuration du conteneur de mises en page et du mode Mise en page
description: Découvrez comment configurer le conteneur de mises en page et le mode de mise en page pour activer les mises en page réactives pour vos auteurs de contenu.
exl-id: 469e8151-8231-4ccc-b7f6-855545f87440
solution: Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 7adfe0ca7fbab1f8a5bd488e524a48be62584966
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 50%

---

# Configuration du conteneur de mises en page et du mode Mise en page {#configuring-layout-container-and-layout-mode}

[La mise en page réactive](/help/sites-cloud/authoring/page-editor/responsive-layout.md) est un mécanisme permettant de réaliser une [conception web réactive.](https://fr.wikipedia.org/wiki/Site_web_réactif) Cela permet à l’auteur de contenu de créer des pages web dont la mise en page et les dimensions dépendent des appareils utilisés par leurs utilisateurs.

AEM effectue une mise en page réactive de vos pages en combinant plusieurs mécanismes :

* **[Conteneur de mises en page](/help/sites-cloud/authoring/page-editor/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)** - Ce composant fournit un système de paragraphes/grille qui vous permet d’ajouter et de positionner des composants dans une grille réactive.
   * Il peut être utilisé comme système de paragraphes (parsys) par défaut pour votre page et mis à la disposition des créateurs dans l’explorateur de composants.
   * Le composant **Conteneur de mises en page** par défaut est défini sous `/libs/wcm/foundation/components/responsivegrid`.
   * Vous pouvez définir des conteneurs de mise en page en tant que :
      * composant que l’utilisateur ou l’utilisatrice peut ajouter à une page ;
      * système de paragraphes par défaut de la page ;
      * En tant que composant et le parsys par défaut.
         * Le conteneur de dispositions peut être utilisé de manière standard pour la page, tout en permettant à l’utilisateur d’y ajouter d’autres conteneurs de mises en page, par exemple, pour contrôler les colonnes.
* **[Mode Mise en page](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector)** - Une fois que le conteneur de mises en page est positionné sur votre page, vous pouvez utiliser le mode **Mise en page** pour positionner le contenu dans la grille réactive.
* **[Émulateur](/help/sites-cloud/authoring/page-editor/responsive-layout.md#selecting-a-device-to-emulate)** : permet de créer et de modifier des sites web réactifs qui réorganisent la mise en page en fonction de la taille de l’appareil ou de la fenêtre en redimensionnant les composants de manière interactive. L’utilisateur ou l’utilisatrice peut alors voir comment le contenu est rendu à l’aide de l’émulateur.

Grâce à ces mécanismes de grille réactive, vous pouvez :

* Utilisez des points d’arrêt (qui indiquent le regroupement des appareils) pour définir différents comportements de contenu en fonction de la mise en page de l’appareil.
* Masquez les composants en fonction du groupe d’appareils (définissez sur quel point d’arrêt un composant sera masqué).
* Utilisez l’accrochage horizontal à la grille (placez les composants dans la grille, redimensionnez-les si nécessaire, définissez quand ils doivent être réduits ou déplacés pour être côte à côte ou au-dessus/en dessous).
* Contrôlez les colonnes.

>[!NOTE]
>
>Lors de la création d’un site à partir de l’[archétype de projet](#addlink) ou du [ modèle de site standard](#addlink), la mise en page réactive est généralement configurée. Sinon, vous devez [ activer le composant Conteneur de mises en page ](#enable-the-layout-container-component-for-page) pour vos pages.

## Activation de l’émulateur {#enabling-emulator}

L’ [ archétype de projet ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) et le [modèle de site standard](/help/sites-cloud/administering/site-creation/site-templates.md#standard-site-template) sont déjà activés pour utiliser l’émulateur. Si vous avez développé votre propre contenu qui n’est pas basé sur les composants principaux ou l’archétype, consultez le document [Responsive Design](/help/implementing/developing/introduction/responsive-design.md) pour plus d’informations sur la manière de développer vos composants tout en exploitant ces fonctionnalités.

## Activation du mode Disposition pour votre site {#activate-layout-mode-for-your-site}

Le mode **Mise en page** vous permet d’utiliser l’émulateur pour ajuster la mise en page de votre contenu pour différents appareils. L’exemple de site WKND est déjà activé pour le mode **Disposition**. Pour activer votre propre site, procédez comme suit.

### Configuration des points d’arrêt {#configure-breakpoints}

Les points d’arrêt sont essentiels pour la conception réactive et définissent la manière et le moment où le contenu est adapté à l’appareil cible. Soyez toutefois prudent, car chaque point d’arrêt que vous introduisez génère un travail supplémentaire pour que vos auteurs puissent s’adapter au contenu. Souvent, deux points d’arrêt peuvent suffire, y compris le point d’arrêt par défaut qui est toujours présent. Adobe recommande de ne pas créer plus de trois points d’arrêt, y compris le point par défaut, c’est-à-dire pas plus de deux noeuds sous `cq:responsive/breakpoint`.

* Les points d’arrêt ont un titre et une largeur :
   * Le titre décrit le regroupement de périphériques génériques, avec orientation si nécessaire.
      * Par exemple, `phone`, `tablet`.
   * La largeur définit la largeur maximale en pixels pour ce regroupement d’appareils générique.
      * Par exemple, si la largeur du téléphone du point d’arrêt est de 768, elle correspond à la largeur maximale de la mise en page utilisée pour un appareil téléphonique ;
* Les points d’arrêt peuvent être définis :
   * dans le modèle de page, à partir duquel les paramètres sont copiés dans les pages créées avec ce modèle ;
   * sur le nœud de page, à partir duquel les paramètres sont hérités par toutes les pages enfants.
* Les points d’arrêt sont visibles en tant que marqueurs dans la partie supérieure de l’éditeur de page lorsque vous utilisez l’émulateur.
* Les points d’arrêt sont hérités de la hiérarchie des noeuds parents et peuvent être remplacés à volonté.
* Il existe un point d’arrêt par défaut (prêt à l’emploi) qui couvre tout ce qui se trouve au-dessus du dernier point d’arrêt configuré.
* Les points d’arrêt peuvent être définis à l’aide de CRXDE Lite ou XML.

Les points d’arrêt doivent être pris en compte pour les projets nouveaux et existants.

* Si vous configurez un nouveau projet, vous devez ajouter des points d’arrêt aux modèles.
* Si vous migrez un projet existant (avec du contenu existant), vous devez :
   * Ajoutez des points d’arrêt aux modèles.
   * Ajoutez les mêmes points d’arrêt aux pages existantes.

En raison de l’héritage, vous devez effectuer cette opération uniquement pour la page racine de votre contenu.

#### Configurer des points d’arrêt à l’aide de CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

1. À l’aide de CRXDE Lite, accédez à l’une des options suivantes :

   * Votre définition de modèle
   * Nœud `jcr:content` de votre page

1. Sous `jcr:content`, créez le nœud :

   * Nom : `cq:responsive`
   * Type : `nt:unstructured`

1. En dessous, créez le nœud :

   * Nom : `breakpoints`
   * Type : `nt:unstructured`

1. Sous le nœud Points d’arrêt, vous pouvez créer un nombre illimité de points d’arrêt. Chaque définition est un nœud unique avec les propriétés suivantes :

   * Nom : `<descriptive name>`
   * Type : `nt:unstructured`
   * Titre : `String <descriptive title seen in Emulator>`.
   * Largeur : `Decimal <value of breakpoint>`

#### Configuration des points d’arrêt à l’aide de code XML {#configuring-breakpoints-using-xml}

Les points d’arrêt se trouvent à l’intérieur de la section `<jcr:content>` du fichier `.context.html` sous le dossier de modèles (ou de contenu) approprié.

Exemple de définition :

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

## Activation du redimensionnement des composants pour la page {#enable-component-resizing-for-the-page}

Le redimensionnement des composants en mode **Mise en page** est une partie importante de la conception adaptée, qui peut être utilisée dans l’exemple de site WKND. Pour activer votre propre site, procédez comme suit.

### Définir le conteneur de mise en page comme parsys (système de paragraphes) principal {#set-layout-container-as-main-parsys}

Pour définir le parsys principal de votre page comme conteneur de mise en page, définissez le parsys en tant que :

`wcm/foundation/components/responsivegrid`

Dans :

* le composant de page ;
* le modèle de page (pour une utilisation ultérieure).

Les deux exemples ci-dessous illustrent la définition :

* **HTL :**

  ```xml
  <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
  ```

* **JSP :**

  ```xml
  <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
  ```

### Inclure le fichier CSS réactif {#include-the-responsive-css}

#### CSS pour les points d’arrêt à l’aide de LESS {#css-for-breakpoints-using-less}

AEM utilise LESS pour générer des parties de la feuille de style CSS nécessaire, qui doivent être incluses pour vos projets.

Vous devez créer une [bibliothèque cliente](/help/implementing/developing/introduction/clientlibs.md) pour fournir des appels de configuration et de fonction supplémentaires. L’extrait LESS suivant est un exemple du minimum à ajouter à votre projet :

```java
@import (once) "/libs/wcm/foundation/clientlibs/grid/grid_base.less";

/* maximum amount of grid cells to be provided */
@max_col: 12;

/* default breakpoint */
.aem-Grid {
  .generate-grid(default, @max_col);
}

/* phone breakpoint */
@media (max-width: 768px) {
  .aem-Grid {
    .generate-grid(phone, @max_col);
  }
}

/* tablet breakpoint */
@media (min-width: 769px) and (max-width: 1200px) {
  .aem-Grid {
    .generate-grid(tablet, @max_col);
  }
}
```

La définition de la grille de base se trouve sous :

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

#### Observations relatives au style {#styling-considerations}

Les composants contenus dans un conteneur réactif sont redimensionnés (ainsi que les éléments DOM HTML correspondants) en fonction de la taille de la grille réactive. Par conséquent, dans ces circonstances, il est recommandé d’éviter (ou de mettre à jour) les définitions d’éléments DOM à largeur fixe (contenus).

Par exemple :

* Avant :

   * `width=100px`

* Après :

   * `max-width=100px`

#### Redimensionnement et conformité d’images adaptatives {#resizing-and-adaptive-image-compliance}

Tout redimensionnement d’un composant dans la grille déclenche les écouteurs suivants selon les besoins :

* `beforeedit`
* `beforechildedit`
* `afteredit`
* `afterchildedit`

Pour redimensionner et mettre à jour correctement le contenu d’une image adaptative incluse dans une grille responsive, vous devez ajouter un ensemble `afterEdit` au programme d’écoute `REFRESH_PAGE` dans le fichier `EditConfig` de chaque composant contenu.

Par exemple :

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

Le mécanisme d’image adaptative est disponible par le biais d’un script qui contrôle la sélection de l’image appropriée pour la taille actuelle de la fenêtre. Il est activé une fois que le modèle DOM est prêt ou lors de la réception d’un événement dédié. Actuellement, la page doit être actualisée pour refléter correctement le résultat de l’action de l’utilisateur et de l’utilisatrice.

>[!CAUTION]
>
>Pour que les bibliothèques clientes de feuilles de style personnalisées fonctionnent correctement tant dans un environnement de création que dans un environnement de publication, elles doivent être chargées dans l’en-tête.

## Activer le composant Conteneur de mise en page pour la page {#enable-the-layout-container-component-for-page}

Pour une mise en page réactive efficace, l’auteur du contenu doit pouvoir faire glisser des instances du composant Conteneur de mises en page sur la page. Cela est déjà activé pour l’exemple de site WKND. Pour activer votre propre site, procédez comme suit.

### Activer le composant Conteneur de mise en page pour la modification de pages {#enable-the-layout-container-component-for-page-editing}

Pour permettre aux créateurs d’ajouter d’autres grilles réactives dans des pages de contenu, vous devez activer le composant conteneur de mise en page pour la page. Vous pouvez effectuer cette opération à l’aide de l’une des fonctions suivantes :

* **Par l’intermédiaire de l’environnement de création** - [Modifiez vos modèles de page](/help/sites-cloud/authoring/page-editor/templates.md) pour activer le conteneur de mises en page pour une page.
* **Définition du composant** - Utilisez `allowedComponent` ou une inclusion statique lors de la définition du composant.

### Configurer la grille du Conteneur de mise en page {#configure-the-grid-of-the-layout-container}

Vous pouvez configurer le nombre de colonnes disponibles pour chaque instance spécifique du conteneur de mises en page [ en modifiant vos modèles de page.](/help/sites-cloud/authoring/page-editor/templates.md)
