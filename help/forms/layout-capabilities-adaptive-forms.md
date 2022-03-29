---
title: Fonctions de mise en page des formulaires adaptatifs
seo-title: Layout capabilities of Adaptive Forms
description: La disposition et l’apparence des formulaires adaptatifs sur différents appareils sont déterminées par les paramètres de disposition. Comprenez les différentes dispositions et leur mode d’application.
exl-id: e30c6ff9-692b-4415-8f14-b4ef616b2d12
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 100%

---

# Fonctions de mise en page des formulaires adaptatifs {#layout-capabilities-of-adaptive-forms}

[!DNL Adobe Experience Manager] permet de créer des formulaires adaptatifs simples d’emploi, qui offrent des expériences dynamiques aux utilisateurs finaux. La disposition des formulaires détermine l’affichage des éléments et des composants dans un formulaire adaptatif.

<!-- ## Prerequisite knowledge {#prerequisite-knowledge}

Before learning about the different layout capabilities of Adaptive Forms, read [Introduction to authoring forms](introduction-forms-authoring.md) to know more about Adaptive Forms. -->

## Types de mise en page {#types-of-layouts}

Un formulaire adaptatif propose les types de disposition suivants :

**[!UICONTROL Disposition de panneau]** : contrôle l’affichage des éléments ou des composants d’un panneau sur un appareil.

**[!UICONTROL Disposition mobile]** : contrôle la navigation d’un formulaire sur un appareil mobile. Si la largeur de l’écran d’un appareil est supérieure ou égale à 768 pixels, la disposition est considérée comme étant adaptée à un appareil mobile et optimisée en conséquence.

**[!UICONTROL Disposition de barre d’outils]** : contrôle le positionnement des boutons d’action dans la barre d’outils ou la barre d’outils du panneau d’un formulaire.

Toutes ces dispositions de panneau sont définies à l’emplacement `/libs/fd/af/layouts` suivant :

Pour modifier la disposition d’un formulaire adaptatif, utilisez le mode Création dans [!DNL Experience Manager].

## [!UICONTROL Mise en page du panneau] {#panel-layout}

L’auteur d’un formulaire peut associer une disposition à chaque panneau d’un formulaire adaptatif, y compris le panneau racine.

Les dispositions de panneau sont disponibles à l’emplacement `/libs/fd/af/layouts/panel`suivant. Appuyez sur le panneau et sélectionnez ![cmppr1](assets/configure-icon.svg) pour afficher les propriétés du panneau.

![Liste des dispositions de panneau pour le panneau racine d’un formulaire adaptatif](assets/layouts.png)

### [!UICONTROL Réactif – Tout sur une page sans navigation] {#responsive-everything-on-one-page-without-navigation-br}

Utilisez cette disposition de panneau pour créer une disposition réactive, qui s’adapte à la taille d’écran de votre appareil sans avoir à recourir à une navigation spécialisée.

Cette disposition permet de placer plusieurs composants **[!UICONTROL Panneau de formulaire adaptatif]** l’un après l’autre dans le panneau.

![Formulaire avec disposition réactive, tel qu’il est affiché sur un petit écran](assets/responsive-layout.png)

### [!UICONTROL Assistant] {#wizard}

Utilisez cette disposition de panneau pour proposer une navigation guidée dans un formulaire. Vous pouvez, par exemple, l’utiliser pour capturer des informations obligatoires dans un formulaire, tout en guidant les utilisateurs pas à pas.

Utilisez le composant **[!UICONTROL Panneau de formulaire adaptatif]** pour proposer une navigation pas à pas dans un panneau. Lorsque vous utilisez cette disposition, l’utilisateur ne passe à l’étape suivante qu’après avoir terminé l’étape en cours.

```javascript
window.guideBridge.validate([], this.panel.navigationContext.currentItem.somExpression)
```

![Formulaire avec assistant](assets/wizard-layout2.png)

### [!UICONTROL Accordéon] {#layout-for-accordion-design}

Cette disposition permet de placer le composant **[!UICONTROL Panneau de formulaire adaptatif]** dans un panneau avec un style de navigation en accordéon. Cette disposition permet également de créer des panneaux reproductibles. Ces panneaux permettent d’ajouter ou de supprimer des panneaux de manière dynamique en fonction de vos besoins. Vous pouvez définir le nombre minimal et maximal de répétitions d’un panneau. Le titre du panneau peut également être déterminé de manière dynamique en fonction des informations fournies dans les éléments du panneau.

Une expression récapitulative peut être utilisée pour afficher les valeurs fournies par l’utilisateur final dans le titre du panneau réduit.

![Panneaux reproductibles utilisant une disposition de type Accordéon dans des formulaires adaptatifs](assets/accordion-layout.png)

### [!UICONTROL Disposition avec onglets – Les onglets s’affichent à gauche ] {#tabbed-layout-tabs-appear-on-the-left}

Cette disposition permet de placer le composant **[!UICONTROL Panneau de formulaire adaptatif]** dans un panneau avec une navigation par onglets. Les onglets sont placés à gauche du contenu du panneau.

![Dans la disposition avec onglets, les onglets sont affichés à gauche.](assets/tabs-on-left.png)

Onglets affichés à gauche d’un panneau

### [!UICONTROL Mises en page avec onglets – Les onglets s’affichent en haut] {#tabbed-layout-tabs-appear-on-the-top}

Cette disposition permet de placer le composant **[!UICONTROL Panneau de formulaire adaptatif]** dans un panneau avec une navigation à onglets. Les onglets sont placés au-dessus du contenu du panneau.

![Disposition à onglets dans des formulaires adaptatifs, avec affichage des onglets en haut](assets/tabs-on-top.png)

## Mises en page pour appareils mobiles {#mobile-layouts}

Ces dispositions permettent de naviguer de manière conviviale sur les appareils mobiles équipés d’écrans relativement petits. Les styles Avec onglets ou Assistant sont utilisés pour naviguer dans les formulaires. L’application d’une telle disposition permet de bénéficier d’une disposition unique pour l’ensemble du formulaire.

Avec cette disposition, le contrôle de la navigation s’effectue à l’aide d’une barre de navigation et d’un menu de navigation. La barre de navigation affiche des icônes **&lt;** et **>** pour indiquer les étapes de navigation **[!UICONTROL suivante]** et **[!UICONTROL précédente]** dans le formulaire.

Les dispositions pour appareils mobiles sont disponibles à l’emplacement `/libs/fd/af/layouts/mobile/`. Les dispositions pour appareils mobiles ci-dessous sont disponibles par défaut dans les formulaires adaptatifs.

![Liste de dispositions pour appareils mobiles dans les formulaires adaptatifs](assets/mobile-navigation.png)

Sélectionnez l’option **[!UICONTROL Ajouter des éléments du menu Disposition réactive pour les appareils mobiles]** pour afficher les options de navigation disponibles pour un panneau dans la disposition pour appareils mobiles. Les options de navigation ne sont visibles que si vous sélectionnez la disposition **[!UICONTROL Réactive]** pour un panneau.

Lorsque vous utilisez une disposition pour appareils mobiles, le menu de formulaire qui permet d’accéder aux différents panneaux de formulaire est disponible en appuyant sur l’icône ![aem6forms_form_menu](assets/rail-icon.svg).

### [!UICONTROL Mise en page avec titres de panneau dans l’en-tête de formulaire] {#layout-with-panel-titles-in-the-form-header}

Cette disposition, comme son nom l’indique, affiche les titres du panneau avec la barre et le menu de navigation. Les icônes Suivant et Précédent sont également disponibles à des fins de navigation.

![Dispositions pour appareils mobiles avec affichage du titre du panneau dans les en-têtes de formulaire](assets/mobile-layout1.png)

### [!UICONTROL Disposition sans titres de panneau dans l’en-tête de formulaire ] {#layout-without-panel-titles-in-the-form-header}

Cette disposition, comme son nom l’indique, affiche uniquement le menu et la barre de navigation, sans les titres de panneau. Les icônes Suivant et Précédent sont également disponibles à des fins de navigation.

![Dispositions pour appareils mobiles sans affichage du titre du panneau dans les en-têtes de formulaire](assets/mobile-layout2.png)

<!-- ## Toolbar layouts {#toolbar-layouts}

A Toolbar Layout controls positioning and display of any action buttons that you add to your Adaptive Forms. The layout can be added at a form level or at a panel level.

![A list of Toolbar Layouts in Adaptive Forms to control layout of buttons](assets/toolbar-layouts.png)

A list of Toolbar Layouts in Adaptive Forms

Toolbar layouts are available at `/libs/fd/af/layouts/toolbar` location. Adaptive Forms provide the following Toolbar Layouts, by default.

### [!UICONTROL Default layout for toolbar] {#default-layout-for-toolbar}

This layout is selected as the default layout when you add any action buttons in an Adaptive Form. Selecting this layout displays the same layout for both, desktop and mobile devices.

Also, you can add multiple toolbars containing action buttons configured with this layout. An action button is associated with a form control. You can configure the toolbars to be before or after a panel.

![Default view for toolbar](assets/toolbar_layout_default.png)

Default view for toolbar

### [!UICONTROL Mobile fixed layout for toolbar] {#mobile-fixed-layout-for-toolbar}

Select this layout to provide alternate layouts for desktop and mobile devices.

For the desktop layout, you can add Action buttons using some specific labels. Only one toolbar can be configured with this layout. If more than one toolbar is configured with this layout, there is an overlap for mobile devices and only one toolbar is visible. For example, you can have a toolbar at the bottom or the top of the form, or, after or before panels in the form.

For the Mobile layout, you can add action buttons using icons.

![Mobile fixed layout for toolbar](assets/toolbar_layout_mobile_fixed.png)

Mobile fixed layout for toolbar-->
