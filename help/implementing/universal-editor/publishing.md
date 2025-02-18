---
title: Publication de contenu par l’éditeur universel
description: Découvrez comment l’éditeur universel publie son contenu, en quoi il diffère du processus dans la console Sites et prenez en compte des points à prendre en compte lors du développement de vos propres applications pour les utiliser.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 0ee6689460ac0ecc5c025fb6a940d69a16699c85
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 25%

---


# Publication de contenu par l’éditeur universel {#publishing}

Découvrez comment l’éditeur universel publie son contenu, en quoi il diffère du processus dans la console Sites et prenez en compte des points à prendre en compte lors du développement de vos propres applications pour les utiliser.

>[!TIP]
>
>Cet article détaille le processus de publication de l’éditeur universel pour le développeur. Pour la personne en charge de la création de contenu, [le processus de publication de votre contenu est décrit ici.](/help/sites-cloud/authoring/universal-editor/publishing.md)

## Similarités avec le processus de la console Sites {#similarities}

Pour les utilisateurs de l’[Éditeur de page d’AEM](/help/sites-cloud/authoring/page-editor/introduction.md) et de la [console Sites](/help/sites-cloud/authoring/sites-console/introduction.md) le processus de publication de contenu avec l’éditeur universel fonctionne comme vous en avez l’habitude : lors de la publication dans AEM, le contenu est répliqué du service de création vers le service de publication (ou vers [le service d’aperçu](/help/sites-cloud/authoring/sites-console/previewing-content.md) le cas échéant, et en fonction des options que l’auteur choisit lors de la publication).

## Différences {#differences}

Ce qui rend la publication avec l’éditeur universel un peu différente n’est pas tant l’éditeur lui-même, mais plutôt l’hébergement externe de l’application que l’éditeur universel rend possible.

Lorsqu’elle est hébergée en externe, l’application web s’assure que le contenu est chargé à partir du service de création lorsque l’application est ouverte par les créateurs et créatrices dans l’éditeur et qu’il est chargé à partir du service de publication lorsque les personnes accèdent à l’application.

## Détection du service dans l’application {#detecting}

Pour déterminer s’il convient d’accéder au service de création ou de publication, il suffit d’une simple instruction conditionnelle dans l’application pour choisir le point d’entrée de création ou de publication approprié lors de la détection de son ouverture dans l’éditeur.

Une autre option consiste à déployer l’application dans deux environnements différents, configurés différemment, de sorte que l’un récupère son contenu à partir du service de création et que l’autre le récupère à partir du service de publication. Pour permettre aux créateurs et créatrices d’ouvrir l’URL publiée dans l’éditeur universel, un petit script peut être créé pour « convertir » l’URL côté publication en son équivalent dans l’environnement de création (par exemple, en ajoutant un sous-domaine `author` ), de sorte que les créateurs et créatrices soient automatiquement redirigés.

## Résumé {#summary}

L’objectif de l’éditeur universel est de ne pas imposer de modèle particulier, de sorte que l’implémentation puisse atteindre ses objectifs de manière complètement découplée tout en restant la plus simple et directe possible.

De même, l’éditeur universel n’impose aucune exigence sur la manière dont un projet particulier doit déterminer à partir de quel service diffuser le contenu. Il offre plutôt plusieurs possibilités et permet au projet de déterminer la solution la mieux adaptée à ses besoins.

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur les détails techniques de l’éditeur universel, consultez ces documents de développement.

* [Présentation de l’éditeur universel](/help/implementing/universal-editor/introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect d’un contenu dans n’importe quelle implémentation afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.
* [Prise en main de l’éditeur universel dans AEM](/help/implementing/universal-editor/getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture de l’éditeur universel](/help/implementing/universal-editor/architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](/help/implementing/universal-editor/attributes-types.md) - Découvrez les attributs et les types de données requis par l’éditeur universel.
* [Authentification de l’éditeur universel](/help/implementing/universal-editor/authentication.md) - Découvrez comment l’éditeur universel s’authentifie.
