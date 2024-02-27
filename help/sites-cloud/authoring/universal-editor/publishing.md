---
title: Publication de contenu avec l’éditeur universel
description: Découvrez comment l’éditeur universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
source-git-commit: 58d85886ef04b548c09e3ef9308fe596dd3eda38
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 69%

---


# Publication de contenu avec l’éditeur universel {#publishing}

Découvrez comment l’éditeur universel publie du contenu et comment vos applications peuvent gérer le contenu publié.

{{universal-editor-status}}

## Similarités avec AEM {#similarities}

Pour les utilisateurs d’AEM, le processus de publication de contenu avec l’éditeur universel fonctionne comme vous le faites habituellement : lors de la publication dans AEM, le contenu est répliqué du niveau Auteur au niveau Publication.

## Différences {#differences}

Ce qui rend la publication avec l’éditeur universel un peu différente n’est pas tant l’éditeur lui-même, mais plutôt l’hébergement externe de l’application que l’éditeur universel rend possible.

Lorsqu’elle est hébergée en externe, l’application web s’assure que le contenu est chargé à partir du niveau création lorsque l’application est ouverte par les créateurs et créatrices dans l’éditeur et qu’il est chargé à partir du niveau publication lorsque les personnes accèdent à l’application.

## Détection du niveau dans l’application {#detecting}

Pour déterminer s’il convient d’accéder au niveau création ou au niveau publication, il suffit d’une simple instruction conditionnelle dans l’application pour choisir le point d’entrée de création ou de publication approprié lors de la détection de son ouverture dans l’éditeur.

Une autre option consiste à déployer l’application dans deux environnements différents, configurés différemment, de sorte que l’un récupère son contenu à partir du niveau création et que l’autre le récupère à partir du niveau publication. Pour permettre aux auteurs d’ouvrir l’URL publiée dans l’éditeur universel, un petit script peut être créé pour &quot;convertir&quot; l’URL côté publication en son équivalent dans l’environnement de création (par exemple, en ajoutant un `author` sous-domaine), de sorte que les auteurs soient automatiquement redirigés.

## Résumé {#summary}

L’objectif de l’éditeur universel est de ne pas imposer de modèle particulier, de sorte que l’implémentation puisse atteindre ses objectifs de manière complètement découplée tout en restant la plus simple et directe possible.

L’éditeur universel n’impose pas non plus d’obligation quant à la manière dont un projet particulier doit déterminer à partir de quel niveau diffuser le contenu. Il active plutôt plusieurs possibilités et permet au projet de déterminer la solution qui convient le mieux à ses propres besoins.

## Ressources supplémentaires {#additional-resources}

Pour savoir comment créer du contenu avec l’éditeur universel, consultez ce document.

* [Création de contenu avec l’éditeur universel](authoring.md) - Découvrez à quel point il est facile et intuitif pour les créateurs et les créatrices de contenu de créer du contenu à l’aide de l’éditeur universel.

Pour en savoir plus sur les détails techniques d’Universal Editor, consultez ces documents de développement.

* [Présentation de l’éditeur universel](/help/implementing/universal-editor/introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect d’un contenu dans n’importe quelle implémentation afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.
* [Prise en main de l’éditeur universel dans AEM](/help/implementing/universal-editor/getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture de l’éditeur universel](/help/implementing/universal-editor/architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](/help/implementing/universal-editor/attributes-types.md) - Découvrez les attributs et les types de données requis par l’éditeur universel.
* [Authentification de l’éditeur universel](/help/implementing/universal-editor/authentication.md) - Découvrez comment l’éditeur universel s’authentifie.
