---
title: Notes de mise à jour d’Adobe Experience Manager as a Cloud Service version 2020.5.0
description: Notes de mise à jour d’Experience Manager version 2020.5.0
translation-type: tm+mt
source-git-commit: 94a732f56929ad4af23855152e258f82ad61ee2c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 29%

---


# Notes de mise à jour d’AEM as a Cloud Service 2020.5.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager Sites as a Cloud Service 2020.5.0.

## Cloud Manager {#cloud-manager}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager dans AEM as a Cloud Service 2020.5.0.

### Nouveautés {#what-is-new}

* Six autres règles de qualité du code ont été ajoutées pour aider les clients à identifier les problèmes potentiels lors de la planification d’une migration vers le service Cloud.
* Une nouvelle mesure Compatibilité *des services* Cloud a été ajoutée pour résumer le nombre de problèmes de compatibilité.
* Les Environnements qui n&#39;ont pas été créés seront automatiquement supprimés environ 24 heures après l&#39;échec de leur création, sauf s&#39;ils ont déjà été supprimés.
* Les performances de la page Activité et de l&#39;API de Liste Pipeline Executions ont été améliorées.
* Le journal de la qualité du code contient désormais des traces de pile complètes pour les exceptions.

### Correctifs  {#bug-fixes}

* Une carte trompeuse s’affichait sur la page d’aperçu pendant l’exécution du pipeline de production.
* La règle de qualité du code *DontImplementOrExtendProviderTypesPomCheck* peut parfois générer une exception de pointeur de valeur NULL.
* Certains liens de documentation de la page d’aperçu ne fonctionnaient pas correctement.
* La boîte de dialogue Créer un Environnement ne s’affichait pas correctement dans Safari.
* Certaines cartes de la page d&#39;aperçu n&#39;affichaient pas correctement les noms d&#39;entité.
* Dans certains cas, l’image de création ne parvient pas à télécharger les packs clients.

