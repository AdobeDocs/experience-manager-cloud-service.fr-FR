---
title: Intégration de Git
description: Intégration de Git - Cloud Services
translation-type: ht
source-git-commit: 57206e36725e28051b2468d47da726e318bd763b

---


# Intégration de Git à Adobe Cloud Manager {#git-integration}

Adobe Cloud Manager est fourni avec un référentiel Git unique utilisé pour déployer le code à l’aide des pipelines CI/CD de Cloud Manager. Ce référentiel Git de Cloud Manager est prêt à l’emploi. Les clients ont également la possibilité d’intégrer un référentiel Git sur site ou **géré par le client** à Cloud Manager.

## Présentation de l’intégration Git   {#git-integration-overview}

>[!VIDEO](https://video.tv.adobe.com/v/28710/?captions=fre_fr)

Cette série de vidéos explore plusieurs cas d’utilisation concernant l’intégration d’un référentiel Git géré par le client à Cloud Manager, notamment :

* [Synchronisation initiale](#initial-sync)
* [Stratégie d’embranchement de base](#branching-strategy)
* [Développement des branches de fonctionnalités](#feature-development)
* [Déploiement dans l’environnement de production](#production-deployment)
* [Synchronisation des balises de publication](#sync-tags)

La série vidéo suppose une connaissance de base de la gestion de Git et de la gestion de commande source. Consultez les [ressources supplémentaires ci-dessous](#additional-resources) pour en savoir plus sur Git.

>[!NOTE]
>
> Les étapes et les conventions d’attribution de noms décrites dans cette série vidéo représentent quelques bonnes pratiques pour travailler avec un référentiel Git géré par le client et Cloud Manager. On s’attend à ce que les conventions et les workflows décrits soient adaptés aux équipes de développement individuelles.

## Synchronisation initiale {#initial-sync}

Premières étapes de la synchronisation d’un référentiel Git géré par le client avec le référentiel Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12&captions=fre_fr)

## Stratégie d’embranchement de base {#branching-strategy}

Suivez la vidéo ci-dessous pour découvrir les stratégies d’embranchement de base.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12&captions=fre_fr)

## Développement des branches de fonctionnalités {#feature-development}

Utilisez une branche de fonctionnalités pour isoler les modifications de code dans un référentiel Git géré par le client et pour vous synchroniser avec le référentiel Git de Cloud Manager afin d’utiliser un pipeline hors production pour les tests de qualité du code et de validation.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12&captions=fre_fr)

## Déploiement dans l’environnement de production {#production-deployment}

Préparez le code d’une version de production dans un référentiel Git géré par le client et synchronisez-le avec le référentiel Git de Cloud Manager afin de le déployer dans des environnements intermédiaires et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12&captions=fre_fr)

## Synchronisation des balises de publication {#sync-tags}

Synchronisez les balises de publication d’un référentiel Git Cloud Manager dans un référentiel Git géré par le client afin de vous donner une idée du code déployé dans les environnements intermédiaires et de production.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12&captions=fre_fr)

## Ressources supplémentaires {#additional-resources}

* [Ressources GitHub](https://try.github.io)
* [Didacticiels Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Antisèche Git](https://education.github.com/git-cheat-sheet-education.pdf)