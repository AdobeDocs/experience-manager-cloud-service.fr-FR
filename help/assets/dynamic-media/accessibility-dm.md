---
title: Accessibilité dans [!DNL Dynamic Media]
description: En savoir plus sur l’accessibilité dans Contenu multimédia dynamique et Visionneuses de contenu multimédia dynamique
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: 97c53ec4317657beeb3619b2f56915a1e649dd9b
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 1%

---


# Accessibility in Dynamic Media {#working-with-three-d-assets-dm}

Contenu multimédia dynamique prend en charge les technologies d’assistance et de contrôle du clavier, telles que les lecteurs d’écran JAWS et NVDA, dans l’interface utilisateur de création.

## Prise en charge de l’accessibilité du clavier dans Contenu multimédia dynamique

Dans la mesure où Contenu multimédia dynamique est un module externe d’AEM Assets, la plupart des commandes de clavier se comportent exactement de la même manière qu’en AEM Assets. Par exemple, le `Cancel` bouton dans Contenu multimédia dynamique a la même mise en surbrillance que dans AEM Assets et réagit à la `Spacebar` clé que dans AEM Assets. Voir Raccourcis [clavier dans Ressources](/help/assets/accessibility.md#keyboard-shortcuts).

Les touches prises en charge par les éléments d’interface utilisateur individuels dans Contenu multimédia dynamique sont, dans la plupart des cas, évidentes et faciles à découvrir. Le contrôle du clavier dans Contenu multimédia dynamique porte sur les éléments suivants :

* Possibilité d’utiliser des `Tab` `Shift+Tab` touches et des éléments interactifs pour naviguer entre les éléments interactifs de la page.
L’utilisation de la fonction `Tab` avance la mise au point des entrées sur l’élément d’interface utilisateur suivant dans l’ordre de tabulation ; l’utilisation `Shift+Tab` rétablit la cible d’action sur l’élément d’interface utilisateur précédent.
La traversée de la cible d’action suit l’emplacement de l’élément d’interface utilisateur naturel à l’écran et se déplace de gauche à droite, puis de haut en bas. En outre, si un champ comporte une erreur, vous pouvez appuyer `Tab` sur pour déplacer la cible d’action.
* Possibilité d’utiliser la `Spacebar` touche et la `Enter` touche pour activer les éléments standard de l’interface utilisateur, tels que les boutons, les listes déroulantes, etc.
* Possibilité de voir la mise en surbrillance du clavier sur l’élément principal. L’élément d’interface utilisateur qui a le focus d’entrée peut recevoir une indication de focus visuel sous la forme d’une bordure rendue autour de l’élément d’interface utilisateur.
* Dans l’éditeur de zones réactives, vous pouvez utiliser des touches personnalisées, telles que des touches fléchées, pour interagir avec des éléments complexes de l’interface utilisateur afin de repositionner les zones réactives.
* Dans l’éditeur de vidéos interactives, vous pouvez utiliser le `Spacebar` pour sélectionner une image et l’ajouter à un segment. En outre, vous pouvez utiliser la `Backspace` clé pour supprimer l’élément sélectionné de l’onglet **[!UICONTROL Contenu]** . En outre, vous pouvez appuyer sur `Tab` des fonctions si vous le souhaitez pour naviguer entre les éléments interactifs de la page.
* Dans l’éditeur Recadrage d’image/Recadrage dynamique, vous pouvez effectuer les opérations suivantes :
   * Utilisez les touches fléchées pour recadrer la taille du cadre ou repositionner l’image, ou les deux.
   * La première `Tab` étape met en surbrillance l’ensemble du cadre d’image. Vous pouvez ensuite utiliser les touches fléchées du clavier pour repositionner le cadre.
   * Les quatre `Tab` arrêts suivants sont les quatre coins du cadre. Lorsque la cible d’action est placée sur un angle de cadre, le coin est mis en surbrillance. Encore une fois, vous pouvez utiliser les touches fléchées du clavier pour déplacer le coin ciblé.
See [Editing the smart crop or smart swatch of a single image](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Prise en charge des technologies d’assistance dans les médias dynamiques {#assistive-technology=support-for-dm}

Les éléments de l’interface utilisateur Contenu multimédia dynamique fonctionnent avec les technologies d’assistance, telles que les lecteurs d’écran. Par exemple, il reconnaît les repères sur une page lorsque vous naviguez entre les repères à l’aide d’un raccourci clavier `D` ou de régions à l’aide d’un raccourci clavier `R`. Il décrit également l’en-tête lors de la navigation à l’aide du raccourci clavier de l’en-tête `H`.

## Prise en charge de l’accessibilité des claviers dans les visionneuses Contenu multimédia dynamique {#keyboard-accessibility-for-dm-viewers}

Tous les composants prêts à l’emploi des visionneuses de médias dynamiques prennent en charge l’accessibilité du clavier pour vos clients.

Reportez-vous à la section Accessibilité et navigation [du](https://docs.adobe.com/content/help/fr-FR/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) clavier dans le guide de référence des visionneuses de médias dynamiques.

## Prise en charge des technologies d’assistance dans les visionneuses de contenu Contenu multimédia dynamique {#assistive-technology=support-for-dm-viewers}

Tous les composants du lecteur Contenu multimédia dynamique prennent en charge les rôles et attributs ARIA (Applications Internet enrichies accessibles) afin d’améliorer l’intégration avec les technologies d’assistance telles que les lecteurs d’écran.
Reportez-vous à la rubrique d’aide sur la prise en charge **de la technologie d’** assistance dans n’importe quelle rubrique de personnalisation de la visionneuse du Guide de référence des visionneuses de médias dynamiques. Par exemple, voir Prise en charge [de la technologie](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) d’assistance pour la visionneuse de vidéos ou Prise en charge [de la technologie d’](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=en#viewers-for-aem-assets-only) assistance pour la visionneuse d’images interactives.

>[!MORELIKETHIS]
>
>* [Accessibilité pour les solutions d&#39;Adobe](https://www.adobe.com/accessibility.html)
>* [Accessibilité dans les ressources du Experience Manager](/help/assets/dynamic-media/accessibility-dm.md)

