---
title: Notes de mise à jour d’Adobe Experience Manager as a Cloud Service version 2020.5.0
description: Notes de mise à jour d’Experience Manager version 2020.5.0
translation-type: tm+mt
source-git-commit: 06a56b0ca8000a41fe4e492206459b1525aae59d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 49%

---


# Notes de mise à jour d’AEM as a Cloud Service 2020.5.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager Sites as a Cloud Service 2020.5.0.

## Date de publication {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.5.0 is May 07, 2020.

## What&#39;s New in AEM Sites {#aem-sites}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour des sites AEM dans AEM as a Cloud Service Release 2020.5.0.

* Des informations détaillées sur la tâche sont désormais disponibles après le traitement des déplacements et déploiements de pages en vrac en tant que tâches asynchrones.
* Lors de la copie/collage d’une arborescence de page, vous pouvez désormais choisir entre coller uniquement la page racine ou les sous-pages de l’arborescence.
* Les fragments d’expérience AEM exportés vers les espaces de travail Cible Adobe apparaissent désormais sous la forme de types d’offre uniques et de sources d’offre dans Cible.
* MSM : l’utilisation du déclencheur de *publication* permet désormais d’annuler les événements de suppression des composants de la source de copie dynamique, c’est-à-dire la suppression des composants d’une copie dynamique qui ont été supprimés de la source de copie dynamique.
* MSM - Les composants de la copie dynamique sont maintenant renommés en *_msm_move* après le déploiement du même composant à partir de la source de la copie dynamique.


## Nouveautés de Cloud Manager {#cloud-manager}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager dans AEM as a Cloud Service 2020.5.0.

### Nouveautés {#what-is-new}

* Six autres règles de qualité du code ont été ajoutées afin d’aider les clients à identifier les problèmes potentiels lors de la planification d’une migration vers Cloud Service.
* Une nouvelle mesure *Compatibilité Cloud Service* a été ajoutée pour résumer le nombre de problèmes de compatibilité.
* Les Environnements qui n&#39;ont pas été créés seront automatiquement supprimés environ 24 heures après l&#39;échec de leur création, sauf s&#39;ils ont déjà été supprimés.
* Les performances de la page Activité et de l’API de liste des exécutions de pipeline ont été améliorées.
* Le journal de la qualité du code contient désormais des traces de pile complètes pour les exceptions.

### Correctifs  {#bug-fixes}

* Une carte trompeuse s’affichait sur la page d’aperçu pendant l’exécution du pipeline de production.
* La règle de qualité du code *DontImplementOrExtendProviderTypesPomCheck* générait parfois une exception de pointeur nul.
* Certains liens de documentation de la page d’aperçu ne fonctionnaient pas correctement.
* La boîte de dialogue Créer un Environnement ne s’affichait pas correctement dans Safari.
* Certaines cartes de la page d’aperçu n’affichaient pas correctement les noms d’entité.
* Dans certains cas, l’image de création ne parvient pas à télécharger les packs clients.


