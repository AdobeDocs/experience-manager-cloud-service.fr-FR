---
title: Accessibilité dans Dynamic Media
description: Découvrez l’accessibilité dans Dynamic Media et dans les visionneuses Dynamic Media.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
feature: Accessibilité
role: Admin,User
source-git-commit: 00bea8b6a32bab358dae6a8c30aa807cf4586d84
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 95%

---


# Accessibilité dans Dynamic Media {#accessibility-in-dm}

Dynamic Media prend en charge les technologies d’assistance et de contrôle du clavier, telles que les lecteurs d’écran JAWS et NVDA, dans l’interface utilisateur de création.

## Prise en charge de l’accessibilité du clavier dans Dynamic Media  {#keyboard-support-in-dm}

Comme Dynamic Media est un plug-in de [!DNL Experience Manager Assets], la plupart des commandes au clavier sont identiques à celles de [!DNL Experience Manager Assets]. Par exemple, le bouton `Cancel` de Dynamic Media a la même mise en surbrillance que dans [!DNL Experience Manager Assets]. Il réagit également à la clé `Spacebar` comme dans [!DNL Experience Manager Assets]. Consultez les [Raccourcis clavier dans Assets](/help/assets/accessibility.md#keyboard-shortcuts).

Les raccourcis de touches prises en charge par des éléments personnalisés de l’interface utilisateur dans Dynamic Media sont, dans la plupart des cas, évidents et faciles à trouver. Voici ce que permet le contrôle clavier dans Dynamic Media :

* Possibilité d’utiliser les touches `Tab` et `Shift+Tab` pour naviguer entre les éléments interactifs de la page.
`Tab` permet d’activer le focus d’entrée sur l’élément d’interface utilisateur suivant dans l’ordre de tabulation ; `Shift+Tab` rétablit le focus d’entrée sur l’élément d’interface utilisateur précédent.
Le parcours du focus suit l’emplacement naturel des éléments de l’interface utilisateur à l’écran et se déplace de gauche à droite, puis de haut en bas. En outre, si un champ comporte une erreur, vous pouvez appuyer sur `Tab` pour y placer le focus.
* Possibilité d’utiliser les touches `Spacebar` et `Enter` pour activer les éléments standard de l’interface utilisateur, tels que les boutons et les listes déroulantes.
* Possibilité de voir la mise en surbrillance du clavier sur l’élément actif. L’élément d’interface utilisateur avec le focus recevait une indication de focus visuelle sous la forme d’une bordure.
* Dans l’éditeur de zones réactives, vous pouvez utiliser des touches personnalisées, telles que les touches fléchées, pour interagir avec des éléments complexes de l’interface utilisateur afin de repositionner les zones réactives.
* Dans l’éditeur de vidéo interactive, vous pouvez utiliser `Spacebar` pour sélectionner une image et l’ajouter à un segment. De plus, vous pouvez utiliser la touche `Backspace` pour supprimer l’élément sélectionné de l’onglet **[!UICONTROL Contenu]**. La touche `Tab` permet par ailleurs de naviguer entre les éléments interactifs de la page.
* Dans l’éditeur Recadrage d’image/Recadrage d’image intelligent, vous pouvez effectuer les opérations suivantes :
   * Vous pouvez utiliser les touches fléchées pour recadrer la taille du cadre ou repositionner l’image, ou les deux.
   * Le premier arrêt `Tab` met en surbrillance l’ensemble du cadre d’image. Vous pouvez ensuite utiliser les touches fléchées du clavier pour repositionner le cadre.
   * Les quatre arrêts `Tab` suivants sont les quatre coins du cadre. Lorsque la cible d’action est placée sur un angle de cadre, le coin est mis en surbrillance. Encore une fois, vous pouvez utiliser les touches fléchées du clavier pour déplacer le coin ciblé.
Voir [Modification du recadrage intelligent ou de l’échantillon intelligent d’une seule image](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Prise en charge des technologies d’assistance dans Dynamic Media {#assistive-technology=support-for-dm}

Les éléments de l’interface utilisateur de Dynamic Media fonctionnent avec des technologies d’assistance telles que les lecteurs d’écran. Elle reconnaît par exemple les repères sur une page lorsque vous naviguez entre les repères à l’aide du raccourci clavier `D` ou entre les régions à l’aide du raccourci clavier `R`. Elle décrit également la section lors de la navigation à l’aide du raccourci clavier de la section `H`.

## Prise en charge de l’accessibilité du clavier dans les visionneuses Dynamic Media {#keyboard-accessibility-for-dm-viewers}

Tous les composants prêts à l’emploi des visionneuses Dynamic Media prennent en charge l’accessibilité du clavier pour vos clients.

Consultez [Accessibilité du clavier et navigation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html?lang=fr) dans le Guide de référence des visionneuses Dynamic Media.

## Prise en charge des technologies d’assistance dans les visionneuses Dynamic Media {#assistive-technology=support-for-dm-viewers}

Tous les composants de la visionneuse Dynamic Media prennent en charge les rôles et attributs ARIA (Accessible Rich Internet Applications) afin d’améliorer l’intégration avec les technologies d’assistance telles que les lecteurs d’écran.
Consultez la rubrique d’aide **Prise en charge des technologies d’assistance** dans toute rubrique de personnalisation de la visionneuse du Guide de référence des visionneuses Dynamic Media. Par exemple, voir [Prise en charge de la technologie d’assistance](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html?lang=fr) pour la visionneuse de vidéos ou [Prise en charge de la technologie d’assistance](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=fr-FR#viewers-for-aem-assets-only) pour la visionneuse d’images interactives.

>[!MORELIKETHIS]
>
>* [Accessibilité pour les solutions d’Adobe](https://www.adobe.com/accessibility.html)
>* [Accessibilité dans Experience Manager Assets](/help/assets/dynamic-media/accessibility-dm.md)

