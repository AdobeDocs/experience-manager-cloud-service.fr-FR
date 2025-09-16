---
title: Publication de contenu par l’éditeur universel
description: Découvrez comment l’éditeur universel publie son contenu, en quoi cela diffère du processus dans la console Sites et les points à prendre en compte lors du développement d’applications destinées à fonctionner avec lui.
feature: Developing
role: Admin, Architect, Developer
exl-id: 60f0bb4a-ee60-4f73-83ae-8568735474ad
source-git-commit: b967a09df7c2e0f5094a6836fcf5311008081dc0
workflow-type: ht
source-wordcount: '564'
ht-degree: 100%

---

# Publication de contenu par l’éditeur universel {#publishing}

Découvrez comment l’éditeur universel publie son contenu, en quoi cela diffère du processus dans la console Sites et les points à prendre en compte lors du développement d’applications destinées à fonctionner avec lui.

>[!TIP]
>
>Cet article présente les détails du processus de publication de l’éditeur universel pour le développeur ou la développeuse. Pour la personne en charge de la création de contenu, [le processus de publication du contenu est décrit ici.](/help/sites-cloud/authoring/universal-editor/publishing.md)

## Similarités avec le processus de la console Sites {#similarities}

Pour les utilisateurs ou les utilisatrices de l’[ éditeur de pages AEM](/help/sites-cloud/authoring/page-editor/introduction.md) et de la [console Sites](/help/sites-cloud/authoring/sites-console/introduction.md), le processus de publication de contenu avec l’éditeur universel fonctionne comme d’habitude : lors de la publication dans AEM, le contenu est répliqué du service auteur vers le service de publication (ou vers le [service d’aperçu](/help/sites-cloud/authoring/sites-console/previewing-content.md) s’il est disponible, en fonction des options choisies par l’auteur ou l’autrice lors de la publication).

## Différences {#differences}

Ce qui rend la publication avec l’éditeur universel légèrement différente n’est pas tant l’éditeur lui-même que l’hébergement externe de l’application rendu possible par l’éditeur universel.

Lorsqu’elle est hébergée en externe, l’application web doit veiller à ce que le contenu soit chargé depuis le service auteur lorsque l’application est ouverte dans l’éditeur, et depuis le service de publication lorsque les personnes accèdent à l’application.

## Détection du service dans l’application {#detecting}

La détermination du service à utiliser (auteur ou publication) peut être réalisée à l’aide d’une simple instruction conditionnelle dans l’application pour choisir le point de terminaison approprié (auteur ou publication) lorsqu’il est détecté que l’application est ouverte dans l’éditeur.

Une autre option consiste à déployer l’application dans deux environnements distincts configurés différemment, afin que l’un récupère son contenu depuis le service auteur et l’autre depuis le service de publication. Pour permettre l’ouverture de l’URL publiée dans l’éditeur universel, il est possible de créer un petit script afin de « convertir » l’URL côté publication en son équivalent dans l’environnement auteur (par exemple, en ajoutant un sous-domaine `author`), de sorte que les personnes soient automatiquement redirigées.

## Résumé {#summary}

L’objectif de l’éditeur universel est de ne pas imposer de modèle particulier, de sorte que l’implémentation puisse atteindre ses objectifs de manière complètement découplée tout en restant la plus simple et directe possible.

De même, l’éditeur universel n’impose aucune exigence sur la manière dont un projet particulier doit déterminer à partir de quel service le contenu doit être diffusé. Il offre plutôt plusieurs possibilités et permet au projet de déterminer quelle solution répond le mieux à ses propres besoins.

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur les détails techniques de l’éditeur universel, consultez ces documents destinés au développeur ou à la développeuse.

* [Présentation de l’éditeur universel](/help/implementing/universal-editor/introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect d’un contenu dans n’importe quelle implémentation afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.
* [Prise en main de l’éditeur universel dans AEM](/help/implementing/universal-editor/getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture de l’éditeur universel](/help/implementing/universal-editor/architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](/help/implementing/universal-editor/attributes-types.md) - Découvrez les attributs et les types de données requis par l’éditeur universel.
* [Authentification de l’éditeur universel](/help/implementing/universal-editor/authentication.md) - Découvrez comment l’éditeur universel s’authentifie.
