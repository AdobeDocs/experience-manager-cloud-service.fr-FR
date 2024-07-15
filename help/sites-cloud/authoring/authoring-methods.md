---
title: Méthodes de création de contenu dans AEM
description: Découvrez les différentes manières de créer du contenu dans AEM et de les différencier.
feature: Authoring
exl-id: ef482843-451b-474e-a8d0-d0bfcc17221b
solution: Experience Manager Sites
role: User
source-git-commit: 7ad9a959592f1e8cebbcad9a67d280d5b2119866
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Méthodes de création de contenu dans AEM {#authoring-methods}

Découvrez les différentes manières de créer du contenu dans AEM, les différences entre ces éléments et le moment où vous pouvez les utiliser.

## AEM&#39; la flexibilité de création {#authoring-flexibility}

AEM as a Cloud Service propose plusieurs éditeurs pour modifier différents types de contenu et prendre en charge différents cas pratiques de création.

* [Création WYSIWYG à l’aide de l’éditeur de page](#page-editor) - L’éditeur de page est l’éditeur classique pour la création de contenu dans AEM, qui a fait l’objet de plusieurs tentatives et qui a reçu la confiance de milliers de sites web.
* [Création WYSIWYG à l’aide de l’éditeur universel](#universal-editor) - L’éditeur universel est une interface utilisateur moderne qui vous permet de créer AEM contenu de manière indépendante du contenu. Elle est disponible pour AEM projets exploitant des Edge Delivery Services.
* [Création basée sur des documents](#document-based) - Si vous utilisez les services Edge Delivery, vous pouvez choisir de créer votre contenu en tant que documents standard tels que Microsoft Word ou les documents Google entièrement en dehors des consoles d’AEM.
* [AEM Éditeur de fragment de contenu](#cf-editor) : il s’agit de l’éditeur de choix pour la création de contenu sans en-tête.

En raison de la nature intégrée et évolutive de l’AEM, ces méthodes peuvent être utilisées exclusivement ou en combinaison les unes avec les autres selon les besoins de votre projet.

Contactez votre administrateur système ou votre chef de projet si vous ne savez pas quelles options de création vous avez disponibles ou si vous souhaitez explorer de nouvelles options pour créer votre contenu.

## WYSIWYG Création à l’aide de l’éditeur de page {#page-editor}

Il s’agit de l’éditeur classique pour la création de contenu dans AEM, testé et approuvé par milliers sur des milliers de sites web.

![Éditeur de page d’AEM](assets/authoring-methods-page-editor.png)

L’éditeur de page d’AEM présente un environnement intégré pour la création de votre contenu à l’aide d’une interface WYSIWYG (What-you-see-c-you-get). Faites glisser des composants prédéfinis pour créer votre page et modifier le contenu sur place.

Pour en savoir plus sur l’éditeur de page d’AEM, consultez le document [L’éditeur de page d’AEM.](/help/sites-cloud/authoring/page-editor/introduction.md)

## WYSIWYG Création à l’aide de l’éditeur universel {#universal-editor}

Universal Editor est une interface utilisateur moderne qui vous permet de créer AEM contenu de manière indépendante du contenu. C’est le premier choix pour AEM projets exploitant des Edge Delivery Services.

![Interface utilisateur de l’éditeur universel](assets/authoring-methods-ue.png)

L’éditeur universel est accessible par le biais de la console Sites dans AEM, mais offre la puissance et la flexibilité agnostique du contenu pour créer non seulement votre contenu AEM, mais également du contenu externe correctement instrumenté.

Pour en savoir plus sur Universal Editor, consultez le document [Création de contenu avec Universal Editor.](/help/sites-cloud/authoring/universal-editor/authoring.md)

## Création basée sur des documents  {#document-based}

Si vous utilisez les services Edge Delivery, vous pouvez choisir de créer votre contenu en tant que documents conventionnels tels que Microsoft Word ou Google Docs entièrement en dehors de la console [AEM **Sites**.](/help/sites-cloud/authoring/sites-console/introduction.md)

![Modification de contenu basé sur un document](assets/authoring-methods-document.jpg)

Avec la création basée sur des documents, les auteurs peuvent utiliser les outils qu’ils connaissent déjà et bénéficier de la vitesse et des performances d’AEM Edge Delivery Services à publier leur contenu. La création basée sur des documents ne nécessite aucune utilisation de la console AEM.

Pour en savoir plus sur la création basée sur des documents, consultez le document [Création et publication de contenu.](/help/edge/docs/authoring.md)

## AEM Éditeur de fragments de contenu {#cf-editor}

L’éditeur de fragment de contenu AEM est l’éditeur de choix pour la création de contenu sans interface utilisateur.

![Éditeur de fragment de contenu AEM](assets/authoring-methods-cf-editor.png)

L’éditeur de fragment de contenu d’AEM présente une interface claire pour la création et la gestion de contenu structuré, idéal pour une diffusion sans interface.

Pour en savoir plus sur l’éditeur de fragments de contenu AEM, consultez les documents [Gestion des fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md) et [Création de fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md).

>[!NOTE]
>
>L’éditeur *new* surligné dans cette section n’est pas disponible lors du développement local pour AEM as a Cloud Service.
>
>L’ [*éditeur de fragment de contenu* d’origine](/help/assets/content-fragments/content-fragments-variations.md) est également disponible.
