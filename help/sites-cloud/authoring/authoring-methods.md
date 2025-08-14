---
title: Méthodes de création de contenu dans AEM
description: Découvrez les différentes manières de créer du contenu dans AEM et leurs différences.
feature: Authoring
exl-id: ef482843-451b-474e-a8d0-d0bfcc17221b
solution: Experience Manager Sites
role: User
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 1%

---

# Méthodes de création de contenu dans AEM {#authoring-methods}

Découvrez les différentes manières de créer du contenu dans AEM, leurs différences et le moment où vous pouvez utiliser l’une plutôt que l’autre.

## Flexibilité de création dans AEM {#authoring-flexibility}

AEM as a Cloud Service propose plusieurs éditeurs différents pour modifier différents types de contenu et prendre en charge différents cas d’utilisation de création.

* [Création WYSIWYG à l’aide de l’éditeur universel ](#universal-editor) - L’éditeur universel est une interface utilisateur moderne permettant de créer du contenu AEM indépendamment du contenu. Il est disponible pour les projets AEM utilisant Edge Delivery Services.
* [Création WYSIWYG à l’aide de l’éditeur de page ](#page-editor) - L’éditeur de page est l’éditeur classique pour la création de contenu dans AEM. Il a fait ses preuves et a été approuvé pour des milliers et des milliers de sites web.
* [Création basée sur les documents](#document-based) - Si vous utilisez les services Edge Delivery, vous pouvez choisir de créer votre contenu en tant que documents conventionnels tels que Microsoft Word ou Google Docs entièrement en dehors des consoles AEM.
* [Éditeur de fragment de contenu AEM ](#cf-editor) - Il s’agit de l’éditeur de choix pour la création de contenu découplé.

En raison de la nature intégrée et évolutive d’AEM, ces méthodes peuvent être utilisées exclusivement ou en combinaison les unes avec les autres en fonction des besoins de votre projet.

Vérifiez auprès de votre administrateur système ou de votre gestionnaire de projet si vous n’êtes pas sûr des options de création disponibles ou si vous souhaitez explorer de nouvelles options pour créer votre contenu.

## Création WYSIWYG à l’aide de l’éditeur universel {#universal-editor}

L’éditeur universel est une interface utilisateur moderne qui vous permet de créer du contenu AEM indépendamment du contenu. Il s’agit de la première option pour les projets AEM utilisant Edge Delivery Services.

![Interface utilisateur de l’éditeur universel](assets/authoring-methods-ue.png)

L’éditeur universel est accessible via la console Sites dans AEM, mais offre la puissance et la flexibilité agnostique de créer non seulement votre contenu AEM, mais également du contenu externe correctement instrumenté.

Pour en savoir plus sur l’éditeur universel, consultez le document [Création de contenu avec l’éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md).

## Création WYSIWYG à l’aide de l’éditeur de page {#page-editor}

Il s’agit de l’éditeur classique pour la création de contenu dans les projets AEM traditionnels, éprouvé et approuvé par des milliers et des milliers de sites web.

![Éditeur de page AEM](assets/authoring-methods-page-editor.png)

L’éditeur de page d’AEM présente un environnement intégré pour la création de votre contenu à l’aide d’une interface WYSIWYG (ce que vous voyez est ce que vous obtenez). Faites glisser et déposez les composants prédéfinis pour créer votre page et modifier le contenu sur place.

Pour en savoir plus sur l’éditeur de page d’AEM, consultez le document [Éditeur de page d’AEM](/help/sites-cloud/authoring/page-editor/introduction.md).

## Création basée sur des documents  {#document-based}

Si vous utilisez les services Edge Delivery, vous pouvez choisir de créer votre contenu en tant que documents conventionnels tels que Microsoft Word ou Google Docs entièrement en dehors de la console [AEM **Sites**](/help/sites-cloud/authoring/sites-console/introduction.md).

![Modification du contenu basé sur des documents](assets/authoring-methods-document.jpg)

Grâce à la création basée sur des documents, les auteurs peuvent utiliser les outils qu’ils connaissent déjà et bénéficier de la vitesse et des performances d’AEM Edge Delivery Services pour publier leur contenu. La création basée sur des documents ne nécessite aucune utilisation de la console AEM.

Pour en savoir plus sur la création basée sur des documents, voir [Création et publication de contenu](https://www.aem.live/docs/aem-authoring).

## Éditeur de fragment de contenu AEM {#cf-editor}

L’éditeur de fragment de contenu AEM est l’éditeur de choix pour créer du contenu découplé.

![Éditeur de fragment de contenu AEM](assets/authoring-methods-cf-editor.png)

L’éditeur de fragment de contenu d’AEM présente une interface claire pour la création et la gestion de contenu structuré, idéale pour une diffusion découplée.

Pour en savoir plus sur l’éditeur de fragment de contenu d’AEM, consultez les documents [Gestion des fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md) et [Création de fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md).

>[!NOTE]
>
>L’éditeur *new* mis en surbrillance dans cette section n’est pas disponible lors du développement local pour AEM as a Cloud Service.
>
>L’éditeur de fragment de contenu [*original*](/help/assets/content-fragments/content-fragments-variations.md) est également disponible.
