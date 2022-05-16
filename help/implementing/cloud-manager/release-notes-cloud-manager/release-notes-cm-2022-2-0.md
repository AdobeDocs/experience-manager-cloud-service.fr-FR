---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2022.02.0
description: Consultez les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2022.02.0.
feature: Release Information
exl-id: da0643a0-78f8-4e9d-9cc9-a1a17067a08c
source-git-commit: 0c4a42595800f7f1d0869bf647c3ec99023b12c5
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 32%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2022.02.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service 2022.02.0.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de la version actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM 2022.02.0 as a Cloud Service est le 10 février 2022. La prochaine version est prévue pour le 10 mars 2022.

## Nouveautés {#what-is-new}

* Nouvelle accélération [Pipelines de configuration de niveau web](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) ont été introduites pour déployer exclusivement la configuration HTTPD/dispatcher.
   * Vous devez être sur AEM version `2021.12.6151.20211217T120950Z` ou plus récent et [vous inscrire au mode flexible des outils de Dispatcher ;](/help/implementing/dispatcher/disp-overview.md#validation-debug) pour utiliser cette fonctionnalité.
   * Cette fonctionnalité sera déployée par étapes au cours des deux semaines qui suivront la version 2022.02.0.
* L’expérience de la page d’entrée de Cloud Manager a été actualisée afin d’offrir une navigation améliorée, un basculement aisé entre les vues de grille/mosaïque et des fenêtres contextuelles pour un résumé rapide du programme.
* Un nouveau seuil d’échec (`< D`) a été ajouté à la variable [mesure d’évaluation de la fiabilité.](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)
   * Les clients avec des problèmes de qualité graves qui affectent la stabilité du système, principalement liés à des index et à des processus de workflow non valides, ne pourront pas déployer tant que ces problèmes ne seront pas résolus.
* La gravité de la variable `BannedPath` [règle de qualité](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules) est passé de bloqueur à critique.
* L’assistant de pipeline informe l’utilisateur lorsqu’une mise à jour de l’environnement AEM peut être nécessaire avant de configurer une [Pipelines de configuration de niveau web](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) qui lui est associée.

## Correctifs {#bug-fixes}

* Les anciens mots de passe du référentiel Git sont désormais toujours invalidés lorsqu’un nouveau mot de passe est généré.
* La mise à jour des variables d’environnement via l’API n’interfère plus dans l’exécution d’un pipeline dans de rares cas.
