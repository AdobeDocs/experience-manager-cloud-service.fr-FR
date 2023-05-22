---
title: Publication de contenu avec l’éditeur visuel universel
description: Découvrez comment l’éditeur visuel universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 100%

---

# Publication de contenu avec l’éditeur visuel universel {#publishing}

Découvrez comment l’éditeur visuel universel publie du contenu et comment vos applications peuvent gérer le contenu publié.

## Similarités avec AEM {#similarities}

Pour les utilisateurs et utilisatrices d’AEM, le processus de publication de contenu avec l’éditeur visuel universel fonctionne comme vous en avez l’habitude : lors de la publication dans AEM, le contenu est répliqué du niveau création vers le niveau publication.

## Différences {#differences}

Ce qui rend la publication avec l’éditeur visuel universel un peu différente n’est pas tant l’éditeur lui-même, mais plutôt l’hébergement externe de l’application que celui-ci rend possible.

Lorsqu’elle est hébergée en externe, l’application web s’assure que le contenu est chargé à partir du niveau création lorsque l’application est ouverte par les créateurs et créatrices dans l’éditeur et qu’il est chargé à partir du niveau publication lorsque les personnes accèdent à l’application.

## Détection du niveau dans l’application {#detecting}

Pour déterminer s’il convient d’accéder au niveau création ou au niveau publication, il suffit d’une simple instruction conditionnelle dans l’application pour choisir le point d’entrée de création ou de publication approprié lors de la détection de son ouverture dans l’éditeur.

Une autre option consiste à déployer l’application dans deux environnements différents, configurés différemment, de sorte que l’un récupère son contenu à partir du niveau création et que l’autre le récupère à partir du niveau publication. Pour permettre aux créateurs et créatrices d’ouvrir l’URL publiée dans l’éditeur universel, un petit script peut être créé pour « convertir » l’URL côté publication en son équivalent dans l’environnement de création (par exemple, en ajoutant un sous-domaine `author`), de sorte que les créateurs et créatrices soient automatiquement redirigés.

## Résumé {#summary}

L’objectif de l’éditeur universel est de ne pas imposer de modèle particulier, de sorte que l’implémentation puisse atteindre ses objectifs de manière complètement découplée tout en restant la plus simple et directe possible.

L’éditeur universel n’impose pas non plus d’obligation quant à la manière dont un projet particulier doit déterminer à partir de quel niveau diffuser le contenu. Il ouvre plutôt un certain nombre de possibilités et permet au projet de déterminer la solution la mieux adaptée à ses besoins.
