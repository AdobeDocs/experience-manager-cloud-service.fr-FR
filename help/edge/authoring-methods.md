---
title: Choix d’une méthode de création
description: Découvrez les points importants à prendre en compte lorsque vous décidez de la manière dont vous créez votre contenu dans AEM afin de vous aider à prendre la meilleure décision pour vos auteurs de contenu.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 15eef2d3790d1c0cf5414ca55b191de5b644fed0
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---


# Choix d’une méthode de création {#authoring-methods}

Découvrez les points importants à prendre en compte lorsque vous décidez de la manière dont vous créez votre contenu dans AEM afin de vous aider à prendre la meilleure décision pour vos auteurs de contenu.

## Présentation des considérations {#overview}

La flexibilité d’AEM garantit que vos besoins de création sont pris en charge, que vous choisissiez la création basée sur un document ou la création WYSIWYG. Gardez les faits suivants à l’esprit lorsque vous commencez vos remarques.

* **Impliquez toujours les auteurs de contenu dans la décision.** - Vos auteurs de contenu sont vos experts et leurs informations sont vitales.
* **Plusieurs méthodes de création peuvent être implémentées.** - Bien qu’Adobe recommande de commencer simplement et en superposant la complexité selon les besoins, plusieurs méthodes de création peuvent fonctionner ensemble dans un seul projet.
* **Vous pouvez toujours modifier votre méthode de création après coup.** - Quoi que vous décidiez de ne pas être verrouillé. Le passage d’une méthode à une autre s’effectue directement avec l’aide des outils de migration automatisée d’Adobe.
* **Vous ne devez pas décider avant l’implémentation, mais plutôt dans le cadre de l’implémentation.** - AEM est un produit unifié, cette décision importante n’a donc pas à faire partie des négociations de contrat. Quand vous achetez des AEM, vous en avez tous. Il s’agit plutôt d’une décision lors de la mise en oeuvre.

Adobe peut vous aider à déterminer la(les) méthode(s) qui correspond le mieux à vos besoins dans le cadre de la mise en oeuvre.

## Une taille ne convient pas à tous {#one-size}

Chaque mise en oeuvre d’AEM a ses propres workflows et objectifs. Un projet peut impliquer un modèle de création simple avec des auteurs de contenu responsables de leurs propres publications. Une autre pourrait avoir un réseau complexe de contributeurs et d&#39;approbations.

![Différents workflows de création](assets/authoring-workflows.png)

Différents projets peuvent présenter des cas d’utilisation différents (et multiples).

![Cas d’utilisation](assets/use-cases.png)

L&#39;Adobe comprend cela et ne propose donc pas une approche universelle. AEM est votre solution unique qui propose différentes approches pour la diffusion de contenu ainsi que la création de contenu afin de répondre à vos besoins.

Pour déterminer la meilleure approche, vous devez prendre en compte quatre éléments.

1. [Avez-vous une préférence de diffusion de contenu ?](#content-delivery)
1. [Avez-vous une préférence de création de contenu ?](#content-authoring)
1. [Quel est l’objectif de votre projet ?](#project-goals)
1. [Quels sont les défis de création auxquels vous êtes confronté aujourd’hui ?](#authoring-challenges)

## Préférences de diffusion de contenu {#content-delivery}

La première chose à prendre en compte est la manière dont vous souhaitez diffuser votre contenu. Edge Delivery Services propose des sites éclair, mais vous vous concentrez peut-être sur la diffusion sans interface. L’arborescence de décision suivante peut vous aider à prendre en compte vos options.

![Arborescence de décision de diffusion de contenu](assets/content-delivery-decision-tree.png)

Vous pouvez ainsi décider si vous avez besoin des éléments suivants :

* [AEM en tant que CMS sans interface](/help/headless/introduction.md) à l’aide de l’éditeur de fragments de contenu et/ou de l’éditeur universel.
* AEM des Edge Delivery Services utilisant la [modification basée sur un document](/help/edge/docs/authoring.md) ou la [création WYSIWYG avec l’éditeur universel.](/help/edge/wysiwyg-authoring/authoring.md)

## Préférences de création de contenu {#content-authoring}

L’étape suivante doit être la manière dont vous souhaitez créer votre contenu. L’arborescence de décision suivante peut vous aider à prendre en compte vos options.

![Arborescence de décision de création de contenu](assets/content-authoring-decision-tree.png)

Vous pouvez ainsi décider si vous avez besoin des éléments suivants :

* AEM des Edge Delivery Services utilisant la [modification basée sur un document.](/help/edge/docs/authoring.md)
* [Création WYSIWYG avec l’éditeur universel.](/help/edge/wysiwyg-authoring/authoring.md)

## Objectifs du projet {#project-goals}

À quoi ressemble le succès de création pour vous ? Comment définissez-vous la réussite de votre projet ?

* Vous devez peut-être permettre à plus de personnes de créer du contenu, mais vous souhaitez éviter de suivre une formation sur un nouvel ensemble d’outils. (pensez à la création basée sur des documents.)
* Vous devrez peut-être augmenter la quantité de contenu que vous générez. (pensez à la création basée sur des documents.)
* Vous devez peut-être vous concentrer sur la mise en page du contenu visuel, mais minimiser le besoin de connaissances en codage. (Pensez à la création WYSIWYG.)

Les objectifs de projet clairement définis dès le début de votre mise en oeuvre vous aideront à prendre une décision éclairée sur votre méthode de création.

## Défis liés à la création {#authoring-challenges}

Examinez enfin les défis spécifiques auxquels vous êtes confronté aujourd’hui pour créer votre contenu.

* Vous êtes peut-être confronté à une duplication du travail avec du contenu créé en dehors de votre CMS, qui doit ensuite être importé ou copié-collé. (pensez à la création basée sur des documents.)
* Peut-être devez-vous réduire le temps nécessaire aux auteurs de formation sur l’utilisation d’un CMS. (pensez à la création basée sur des documents.)
* Vos auteurs doivent peut-être souvent modifier la mise en page visuelle de votre contenu, ce qui nécessite une prise en charge constante des développeurs. (Pensez à la création WYSIWYG.)
