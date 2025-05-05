---
title: Utilisation de Git avec Cloud Manager
description: Découvrez comment utiliser les référentiels Git de Cloud Manager et comment intégrer votre propre référentiel Git On-Premise géré par le client ou la cliente avec Cloud Manager.
exl-id: 57e71b8a-4546-4d7f-825c-a1637d08e608
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 80206fc1396896fe45e2c959c78a0bf30eba71c5
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 91%

---

# Utilisation de Git avec Cloud Manager {#git-integration}

Adobe Cloud Manager est fourni avec un référentiel Git unique utilisé pour déployer le code à l’aide des pipelines CI/CD de Cloud Manager.

Vous pouvez utiliser le référentiel Git de Cloud Manager prêt à l’emploi ou vous avez également la possibilité d’intégrer un référentiel Git géré par le client ou la cliente avec Cloud Manager.

## Présentation de l’intégration Git {#git-integration-overview}

Cette série de vidéos explore plusieurs cas d’utilisation lors de l’intégration d’un référentiel Git géré par le client ou la cliente avec Cloud Manager, notamment :

* [Synchronisation initiale](#initial-sync)
* [Stratégie d’embranchement de base](#branching-strategy)
* [Développement des branches de fonctionnalités](#feature-development)
* [Déploiement dans l’environnement de production](#production-deployment)
* [Synchronisation des balises de publication](#sync-tags)

La série vidéo suppose une connaissance de base de la gestion de Git et de la gestion de commande source. Consultez les [ressources supplémentaires ci-dessous](#additional-resources) pour en savoir plus sur Git.

>[!VIDEO](https://video.tv.adobe.com/v/31135?captions=fre_fr)

Les étapes et les conventions de nommage décrites dans cette série de vidéos représentent quelques bonnes pratiques pour travailler avec un référentiel Git géré par le client ou la cliente dans Cloud Manager. Les conventions et les workflows décrits sont adaptés aux cas d’utilisation individuels.

## Synchronisation initiale {#initial-sync}

Dans cette vidéo, découvrez les premières étapes de synchronisation d’un référentiel Git géré par le client ou la cliente avec le référentiel Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/31134/?quality=12&captions=fre_fr)

## Stratégie d’embranchement de base {#branching-strategy}

Dans cette vidéo, découvrez les politiques d’embranchement de base.

>[!VIDEO](https://video.tv.adobe.com/v/31133/?quality=12&captions=fre_fr)

## Développement des branches de fonctionnalités {#feature-development}

Utilisez une branche de fonctionnalités pour isoler les modifications de code dans un référentiel Git géré par le client ou la cliente et pour vous synchroniser avec le référentiel Git de Cloud Manager afin d’utiliser un pipeline hors production pour les tests de qualité du code et de validation.

>[!VIDEO](https://video.tv.adobe.com/v/31132/?quality=12&captions=fre_fr)

## Déploiement en production {#production-deployment}

Préparez le code d’une mise à jour de production dans un référentiel Git géré par le client ou la cliente et synchronisez-le avec le référentiel Git de Cloud Manager afin de le déployer dans des environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/31131/?quality=12&captions=fre_fr)

## Synchronisation des balises de publication {#sync-tags}

Synchronisez les balises de mise à jour d’un référentiel Git Cloud Manager dans un référentiel Git géré par le client ou la cliente afin d’obtenir une visibilité sur le code déployé dans les environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/31130/?quality=12&captions=fre_fr)

## Ressources supplémentaires {#additional-resources}

* [Ressources GitHub](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Didacticiels Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Antisèche Git](https://education.github.com/git-cheat-sheet-education.pdf)
