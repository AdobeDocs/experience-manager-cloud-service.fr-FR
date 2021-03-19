---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2020.5.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2020.5.0
feature: Informations sur la version
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 100%

---


# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2020.5.0 {#release-notes}

Cette page contient les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2020.5.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2020.5.0 est le 7 mai 2020.

## Nouveautés {#whats-new-cloud-manager}

* Six règles de qualité de code ont été ajoutées pour aider les clients à identifier les problèmes potentiels lors de la planification d’une migration vers Cloud Service.
* Une nouvelle mesure *Compatibilité Cloud Service* a été ajoutée pour résumer le nombre de problèmes de compatibilité.
* Les environnements qui n’ont pas pu être créés seront automatiquement supprimés environ 24 heures après l’échec de leur création, sauf s’ils ont déjà été supprimés.
* Les performances de la page Activité et de l’API Pipeline Executions List ont été améliorées.
* Le journal de qualité du code contient désormais des traces de pile complètes pour les exceptions.

### Correctifs {#bug-fixes}

* Une carte erronée s’affichait sur la page d’aperçu lors de l’exécution du pipeline de production.
* La règle de qualité du code *DontImplementOrExtendProviderTypesPomCheck* pouvait parfois générer une exception de pointeur de valeur NULL.
* Certains liens de documentation de la page d’aperçu ne fonctionnaient pas correctement.
* La boîte de dialogue Créer l’environnement ne s’affichait pas correctement dans Safari.
* Certaines cartes de la page d’aperçu n’affichaient pas correctement les noms des entités.
* Dans certains cas, la création d’image ne parvenait pas à télécharger les modules client.
