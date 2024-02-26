---
title: Méthodes de création de contenu dans AEM
description: Découvrez les différentes manières de créer du contenu dans AEM et de les différencier.
feature: Authoring
source-git-commit: f6162dcbc5b7937d55922e8c963a402697110329
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Méthodes de création de contenu dans AEM {#authoring-methods}

Découvrez les différentes manières de créer du contenu dans AEM, les différences entre ces éléments et le moment où vous pouvez les utiliser.

## AEM Flexibilité de création {#authoring-flexibility}

AEM as a Cloud Service propose plusieurs éditeurs afin de modifier différents types de contenu et de prendre en charge différents cas pratiques de création.

* [Éditeur de page AEM](#page-editor) - Il s’agit de l’éditeur classique pour la création de contenu dans AEM, testé et approuvé par milliers sur des milliers de sites web.
* [AEM Éditeur de fragments de contenu](#cf-editor) - Il s’agit de l’éditeur de choix pour la création de contenu sans interface utilisateur.
* [Éditeur universel](#universal-editor) - Cette interface utilisateur moderne vous permet de créer AEM contenu de manière indépendante du contenu. C’est le premier choix pour AEM projets exploitant des Edge Delivery Services.
* [Création basée sur des documents](#document-based) - Si vous utilisez les services Edge Delivery, vous pouvez choisir de créer votre contenu en tant que documents conventionnels tels que Microsoft Word ou Google Docs entièrement en dehors des consoles d’AEM.

En raison de la nature intégrée et évolutive de l’AEM, ces méthodes peuvent être utilisées exclusivement ou en combinaison les unes avec les autres selon les besoins de votre projet.

Contactez votre administrateur système ou votre chef de projet si vous ne savez pas quelles options de création vous avez disponibles ou si vous souhaitez explorer de nouvelles options pour créer votre contenu.

## Éditeur de page AEM {#page-editor}

Il s’agit de l’éditeur classique pour la création de contenu dans AEM, testé et approuvé par milliers sur des milliers de sites web.

![Éditeur de page d’AEM](assets/authoring-methods-page-editor.png)

L’éditeur de page d’AEM présente un environnement intégré pour la création de votre contenu à l’aide d’une interface WYSIWYG (What-you-see-c-you-get). Faites glisser des composants prédéfinis pour créer votre page et modifier le contenu sur place.

Pour en savoir plus sur l’éditeur de page d’AEM, consultez le document [Éditeur de page d’AEM.](/help/sites-cloud/authoring/page-editor/introduction.md)

## AEM Éditeur de fragments de contenu {#cf-editor}

L’éditeur de fragment de contenu AEM est l’éditeur de choix pour la création de contenu sans interface utilisateur.

![Éditeur de fragment de contenu AEM](assets/authoring-methods-cf-editor.png)

L’éditeur de fragment de contenu d’AEM présente et présente une interface claire pour la création et la gestion de contenu structuré, idéal pour une diffusion sans interface.

Pour en savoir plus sur l’éditeur de fragment de contenu AEM, consultez le document . [Gestion des fragments de contenu.](/help/assets/content-fragments/content-fragments-managing.md)

## Éditeur universel {#universal-editor}

Universal Editor est une interface utilisateur moderne qui vous permet de créer AEM contenu de manière indépendante du contenu. C’est le premier choix pour AEM projets exploitant des Edge Delivery Services.

![Interface utilisateur de l’éditeur universel](assets/authoring-methods-ue.png)

L’éditeur universel est accessible par le biais de la console Sites dans AEM, mais offre la puissance et la flexibilité agnostique du contenu pour créer non seulement votre contenu AEM, mais également du contenu externe correctement instrumenté.

Pour en savoir plus sur Universal Editor, consultez le document [Création de contenu avec l’éditeur universel.](/help/implementing/universal-editor/authoring.md)

## Création basée sur des documents {#document-based}

Si vous utilisez les services de diffusion Edge, vous pouvez choisir de créer votre contenu en tant que documents conventionnels tels que Microsoft Word ou Google Docs entièrement en dehors de la console AEM.

![Modification de contenu basé sur un document](assets/authoring-methods-document.jpg)

Avec la création basée sur des documents, les auteurs peuvent utiliser les outils qu’ils connaissent déjà et bénéficier de la vitesse et des performances des Edge Delivery Services AEM pour publier leur contenu. La création basée sur des documents ne nécessite aucune utilisation de la console AEM.

Pour en savoir plus sur la création basée sur des documents, consultez le document . [Création de contenu pour les Edge Delivery Services.](/help/edge/authoring.md)
