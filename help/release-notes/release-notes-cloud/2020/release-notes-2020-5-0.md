---
title: Notes de mise à jour d’Adobe Experience Manager as a Cloud Service version 2020.5.0
description: Notes de mise à jour d’Experience Manager version 2020.5.0
exl-id: 8570d2c3-6d55-4914-94b2-f5d162e0c285
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 100%

---

# Notes de mise à jour d’AEM as a Cloud Service 2020.5.0 {#release-notes}

Cette page présente les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.5.0.

## Date de publication {#release-date}

La date de publication d’[!DNL Experience Manager] as a Cloud Service version 2020.5.0 est le 7 mai 2020.

## Nouveautés d’AEM Sites {#aem-sites}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour d’AEM Sites dans AEM as a Cloud Service 2020.5.0.

* Des informations détaillées sur les tâches sont désormais disponibles après le traitement des déplacements et des déploiements de pages en masse à l’aide de tâches asynchrones.
* Lors d’une opération de copier/coller d’une arborescence de page, vous pouvez désormais choisir entre coller seulement la page racine ou coller aussi les sous-pages de l’arborescence.
* Les fragments d’expérience AEM exportés vers les espaces de travail Adobe Target apparaissent désormais sous la forme de types d’offres et de sources d’offres uniques dans Target.
* MSM : l’utilisation du déclencheur de *publication* permet désormais d’appliquer les événements de suppression des composants à la source Live Copy. Cela revient à supprimer les composants d’une Live Copy qui ont été supprimés de la source de cette copie.
* MSM : les composants Live Copy sont maintenant renommés *_msm_moved* après le déploiement du même composant à partir de la source de la Live Copy.


## Nouveautés de Cloud Manager {#cloud-manager}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager dans AEM as a Cloud Service 2020.5.0.

### Nouveautés {#what-is-new}

* Six règles de qualité de code ont été ajoutées pour aider les clients à identifier les problèmes potentiels lors de la planification d’une migration vers Cloud Service.
* Une nouvelle mesure *Compatibilité Cloud Service* a été ajoutée pour résumer le nombre de problèmes de compatibilité.
* Les environnements qui n’ont pas pu être créés seront automatiquement supprimés environ 24 heures après l’échec de leur création, sauf s’ils ont déjà été supprimés.
* Les performances de la page Activité et de l’API Pipeline Executions List ont été améliorées.
* Le journal de qualité du code contient désormais des traces de pile complètes pour les exceptions.

### Correctifs  {#bug-fixes}

* Une carte erronée s’affichait sur la page d’aperçu lors de l’exécution du pipeline de production.
* La règle de qualité du code *DontImplementOrExtendProviderTypesPomCheck* pouvait parfois générer une exception de pointeur de valeur NULL.
* Certains liens de documentation de la page d’aperçu ne fonctionnaient pas correctement.
* La boîte de dialogue Créer l’environnement ne s’affichait pas correctement dans Safari.
* Certaines cartes de la page d’aperçu n’affichaient pas correctement les noms des entités.
* Dans certains cas, la création d’image ne parvenait pas à télécharger les packages clients.
