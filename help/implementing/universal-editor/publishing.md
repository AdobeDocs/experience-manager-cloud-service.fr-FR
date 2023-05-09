---
title: Publication de contenu avec l’éditeur visuel universel
description: Découvrez comment l’éditeur visuel universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Publication de contenu avec l’éditeur visuel universel {#publishing}

Découvrez comment l’éditeur visuel universel publie du contenu et comment vos applications peuvent gérer le contenu publié.

## Similarités avec les AEM {#similarities}

Pour les utilisateurs d’AEM, le processus de publication de contenu avec l’éditeur visuel universel fonctionne comme vous le faites habituellement : lors de la publication dans AEM, le contenu est répliqué du niveau auteur au niveau publication.

## Différences {#differences}

Ce qui rend la publication avec l’éditeur visuel universel un peu différente n’est pas tant l’éditeur lui-même, mais plutôt l’hébergement externe de l’application que l’éditeur universel rend possible.

Lorsqu’elle est hébergée en externe, l’application web se préoccupe de s’assurer que le contenu est chargé à partir du niveau Auteur lorsque l’application est ouverte par les auteurs au sein de l’éditeur et qu’il est chargé à partir du niveau Publication lorsque les visiteurs accèdent à l’application.

## Détection du niveau dans l’application {#detecting}

Pour déterminer si le niveau de création ou de publication doit être accessible, il suffit d’une simple instruction conditionnelle dans l’application pour choisir le point de terminaison de création ou de publication approprié lors de la détection de son ouverture dans l’éditeur.

Une autre option consiste à déployer l’application dans deux environnements différents, configurés différemment, de sorte qu’un récupère son contenu à partir du niveau Auteur et un autre l’extrait du niveau Publication. Pour permettre aux auteurs d’ouvrir l’URL publiée dans l’éditeur universel, un petit script peut être créé pour &quot;convertir&quot; l’URL côté publication en son équivalent dans l’environnement de création (par exemple, en ajoutant un `author` sous-domaine), de sorte que les auteurs soient automatiquement redirigés.

## Résumé {#summary}

L’objectif de l’éditeur universel est de ne pas imposer de schéma particulier, de sorte que l’implémentation puisse atteindre ses objectifs de manière complètement découplée tout en gardant tout simplement et directement en avance pour l’implémentation.

De même, Universal Editor n’impose aucune exigence quant à la manière dont un projet particulier doit déterminer à partir de quel niveau diffuser le contenu. Il permet plutôt un certain nombre de possibilités et permet au projet de déterminer la solution la mieux adaptée à ses besoins.
