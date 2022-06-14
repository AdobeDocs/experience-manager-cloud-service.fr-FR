---
title: Utilisation de git avec Cloud Manager
description: Découvrez comment utiliser les référentiels Git de Cloud Manager et comment intégrer votre propre référentiel Git géré par le client sur site à Cloud Manager.
exl-id: 57e71b8a-4546-4d7f-825c-a1637d08e608
source-git-commit: a9303c659730022b7417fc9082dedd26d7cbccca
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 50%

---

# Utilisation de git avec Cloud Manager {#git-integration}

Adobe Cloud Manager est fourni avec un référentiel Git unique utilisé pour déployer le code à l’aide des pipelines CI/CD de Cloud Manager.

Vous pouvez utiliser le référentiel git de Cloud Manager prêt à l’emploi, mais vous avez également la possibilité d’intégrer un référentiel git géré par le client à Cloud Manager.

## Présentation de l’intégration Git {#git-integration-overview}

Cette série de vidéos explore plusieurs cas d’utilisation lors de l’intégration d’un référentiel Git géré par le client à Cloud Manager, notamment :

* [Synchronisation initiale](#initial-sync)
* [Stratégie d’embranchement de base](#branching-strategy)
* [Développement des branches de fonctionnalités](#feature-development)
* [Déploiement dans l’environnement de production](#production-deployment)
* [Synchronisation des balises de publication](#sync-tags)

La série vidéo suppose une connaissance de base de la gestion de Git et de la gestion de commande source. Consultez les [ressources supplémentaires ci-dessous](#additional-resources) pour en savoir plus sur Git.

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Les étapes et les conventions de dénomination décrites dans cette série vidéo représentent quelques bonnes pratiques pour travailler avec un référentiel Git géré par le client dans Cloud Manager. Il est prévu que les conventions et les workflows décrits soient adaptés aux cas d’utilisation individuels.

## Synchronisation initiale {#initial-sync}

Dans cette vidéo, découvrez les premières étapes de synchronisation d’un référentiel Git géré par le client avec le référentiel Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Stratégie d’embranchement de base {#branching-strategy}

Dans cette vidéo, découvrez les stratégies d’embranchement de base.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Développement des branches de fonctionnalités {#feature-development}

Utilisez une branche de fonctionnalités pour isoler les modifications de code dans un référentiel Git géré par le client et pour vous synchroniser avec le référentiel Git de Cloud Manager afin d’utiliser un pipeline hors production pour les tests de qualité du code et de validation.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Déploiement dans l’environnement de production {#production-deployment}

Préparez le code d’une version de production dans un référentiel Git géré par le client et synchronisez-le avec le référentiel Git de Cloud Manager afin de le déployer dans des environnements intermédiaires et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronisation des balises de publication {#sync-tags}

Synchronisez les balises de publication d’un référentiel Git Cloud Manager dans un référentiel Git géré par le client afin de fournir une visibilité du code qui a été déployé dans les environnements d’évaluation et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Ressources supplémentaires {#additional-resources}

* [Ressources GitHub](https://try.github.io)
* [Didacticiels Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Antisèche Git](https://education.github.com/git-cheat-sheet-education.pdf)
