---
title: Accessibilité dans Dynamic Media
description: Découvrez comment utiliser la vidéo dans Dynamic Media, notamment les bonnes pratiques pour le codage de vidéos, la publication des vidéos sur YouTube et l’affichage des rapports vidéo. Découvrez également comment ajouter des sous-titres, des sous-titres ou des marqueurs de chapitre aux vidéos.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
feature: Accessibility
role: Admin,User
exl-id: f8d2dcbf-f61a-4b27-a3fc-406e3662adcb
source-git-commit: 6ad46350906c3b8a36a8e361714fa5fffdbf8e82
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 97%

---

# Accessibilité dans Dynamic Media {#accessibility-in-dm}

{{work-with-dynamic-media}}

Dynamic Media prend en charge les technologies d’assistance et de contrôle du clavier, telles que les lecteurs d’écran JAWS et NVDA, dans l’interface utilisateur de création.

## Prise en charge de l’accessibilité du clavier dans Dynamic Media {#keyboard-support-in-dm}

Dynamic Media étant un plug-in [!DNL Experience Manager Assets], la plupart des commandes de clavier produisent le même résultat que dans [!DNL Experience Manager Assets]. Par exemple, le bouton `Cancel` de Dynamic Media a la même mise en surbrillance que dans [!DNL Experience Manager Assets]. Il réagit également à la touche `Spacebar` de la même manière que dans [!DNL Experience Manager Assets]. Consultez les [Raccourcis clavier dans Assets](/help/assets/accessibility.md#keyboard-shortcuts).

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

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (Experience Manager 6.5) or Coral Spectrum (in Skyline)) as entire Experience Manager Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Prise en charge des technologies d’assistance dans Dynamic Media {#assistive-technology=support-for-dm}

Les éléments de l’interface utilisateur de Dynamic Media fonctionnent avec des technologies d’assistance telles que les lecteurs d’écran. Elle reconnaît par exemple les repères sur une page lorsque vous naviguez entre les repères à l’aide du raccourci clavier `D` ou entre les régions à l’aide du raccourci clavier `R`. Elle décrit également la section lors de la navigation à l’aide du raccourci clavier de la section `H`.

## Prise en charge de l’accessibilité du clavier dans les visionneuses Dynamic Media {#keyboard-accessibility-for-dm-viewers}

Tous les composants prêts à l’emploi des visionneuses Dynamic Media prennent en charge l’accessibilité du clavier pour vos clients.

Consultez [Accessibilité du clavier et navigation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html?lang=fr) dans le Guide de référence des visionneuses Dynamic Media.

## Prise en charge des technologies d’assistance dans les visionneuses Dynamic Media {#assistive-technology=support-for-dm-viewers}

Tous les composants de la visionneuse Dynamic Media prennent en charge les rôles et attributs ARIA (Accessible Rich Internet Applications) afin d’améliorer l’intégration avec les technologies d’assistance telles que les lecteurs d’écran.
Consultez la rubrique d’aide **Prise en charge des technologies d’assistance** dans toute rubrique de personnalisation de la visionneuse du Guide de référence des visionneuses Dynamic Media. Par exemple, voir [Prise en charge de la technologie d’assistance](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html?lang=fr) pour la visionneuse de vidéos ou [Prise en charge de la technologie d’assistance](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=fr#viewers-for-aem-assets-only) pour la visionneuse d’images interactives.

## Prise en charge des sous-titres dans [!DNL Dynamic Media] {#closed-caption-support}

Dynamic Media prend en charge la diffusion de vidéos et de visionneuses de vidéos adaptatives avec sous-titrage. Les sous-titres doivent s’afficher au-dessus du contenu vidéo.

Consultez la section [Vidéo dans Dynamic Media - Ajouter des sous-titres à une vidéo](/help/assets/dynamic-media/video.md#adding-captions-to-video).


>[!MORELIKETHIS]
>
>* [Accessibilité pour les solutions d’Adobe](https://www.adobe.com/accessibility.html)
>* [Accessibilité dans Experience Manager Assets](/help/assets/dynamic-media/accessibility-dm.md)
