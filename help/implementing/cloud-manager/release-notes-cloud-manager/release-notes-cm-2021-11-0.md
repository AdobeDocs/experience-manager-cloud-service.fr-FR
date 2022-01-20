---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.11.0
description: Il s’agit des notes de mise à jour de Cloud Manager dans AEM version as a Cloud Service 2021.11.0
feature: Release Information
source-git-commit: e402578fc95fd97f808fde01a860d4c583af4c9b
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 67%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.11.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service 2021.11.0.

>[!NOTE]
>
>Voir [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM 2021.11.0 as a Cloud Service est le 4 novembre 2021.
La prochaine version est prévue pour le 16 décembre 2021.

## Nouveautés {#what-is-new}

* Les utilisateurs peuvent désormais tirer parti des nouveaux pipelines front-end pour déployer le code front-end exclusivement de manière accélérée. Voir [Pipelines front-end de Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) pour en savoir plus.

   >[!IMPORTANT]
   >Vous devez être sur AEM version `2021.10.5933.20211012T154732Z` pour tirer parti des nouveaux pipelines front-end.

* La durée du pipeline de qualité du code est considérablement réduite en exécutant l’analyse du code de manière plus efficace sans avoir à créer une image AEM entière. Cette modification sera déployée progressivement au cours des semaines qui suivront la version.

* L’ID d’enregistrement Git s’affiche désormais dans les détails d’exécution du pipeline, ce qui facilite le suivi du code créé.

* La création de programme est désormais disponible via l’API publiquement exposée.

* La création d’environnement est désormais disponible via l’API publiquement exposée.

* L’en-tête de réponse `x-request-id` est désormais visible dans le laboratoire de l’API sur [www.adobe.io](https://www.adobe.io/). Cet en-tête est utile pour signaler des problèmes à l’assistance clientèle à des fins de dépannage.

* En tant qu’utilisateur, je vois une carte Pipeline sans pipeline. Pouvez-vous me fournir des conseils appropriés ?

* Une nouvelle page d’activité est désormais disponible. Vous pouvez y afficher des activités telles que les exécutions de pipeline et de code, ainsi que les détails associés. Au fil du temps, les activités répertoriées dans cette page s’étendront, de même que les détails fournis.

* Une nouvelle page Pipelines avec une fenêtre contextuelle d’état et de survol permettant d’afficher facilement le résumé des détails est désormais disponible. Il est possible de visualiser les exécutions de pipelines avec les détails associés.

* L’API Modifier un pipeline prend désormais en charge la modification de l’environnement utilisé lors des phases de déploiement.

* Une optimisation du processus d’analyse OakPal a été introduite pour les modules volumineux.

* Le fichier CSV de problème de qualité contient désormais l’horodatage de chaque problème.

## Correctifs {#bug-fixes}

* Certaines configurations de génération non orthodoxes entraînaient le stockage de fichiers inutiles dans le cache d’artefacts Maven du pipeline, ce qui entraînait des E/S réseau superflues lors du démarrage et de l’arrêt du conteneur de génération.

* L’API Pipeline PATCH échoue en l’absence de phase de déploiement.

* La règle de qualité `ClientlibProxyResourceCheck` générait des faux positifs en présence de bibliothèques clientes avec des chemins d’accès de base communs.

* Un message d’erreur indiquant que le nombre maximal de référentiels a été atteint ne précisait pas la raison de l’erreur.

* Dans de rares cas, les pipelines échouaient en raison d’une gestion inappropriée des reprises de certains codes de réponse.
