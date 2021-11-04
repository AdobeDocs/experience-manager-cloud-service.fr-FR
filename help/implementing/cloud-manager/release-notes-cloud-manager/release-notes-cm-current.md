---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.11.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.11.0
feature: Release Information
exl-id: null
source-git-commit: 471924b2edd5e0bccd7c1eb9d6dd36ad2bd89f88
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 22%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.11.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service 2021.11.0.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.11.0 est le 04 novembre 2021.
La prochaine version est prévue pour le 9 décembre 2021.

### Nouveautés {#what-is-new}

* Les utilisateurs peuvent désormais tirer parti des nouveaux pipelines front-end pour déployer le code front-end exclusivement de manière accélérée. Voir [Pipelines front-end de Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) pour en savoir plus.

   >[!IMPORTANT]
   >Vous devez être sur AEM version `2021.10.5933.20211012T154732Z` pour tirer parti des nouveaux pipelines front-end.

* La durée du pipeline de qualité du code est considérablement réduite en exécutant l’analyse du code de manière plus efficace sans avoir à créer une image AEM entière. Cette modification sera déployée progressivement au cours des semaines qui suivront la version.

* L’identifiant de validation Git s’affiche désormais dans les détails d’exécution du pipeline, ce qui facilite le suivi du code qui a été créé.

* La création de programme est désormais disponible via l’API publiquement exposée.

* La création d’environnement est désormais disponible via l’API publiquement exposée.

* Le `x-request-id` L’en-tête de réponse est désormais visible dans le terrain de lecture de l’API sur [www.adobe.io](https://www.adobe.io/). Cet en-tête est utile lors de l’envoi de problèmes d’assistance clientèle à des fins de dépannage.

* En tant qu’utilisateur, je vois une carte Pipeline avec zéro pipeline me fournir des conseils appropriés.

* Une nouvelle page Pipelines avec une fenêtre contextuelle d’état et de survol permettant d’afficher facilement le résumé des détails est désormais disponible. Les exécutions de pipeline peuvent être visualisées avec les détails associés.

* L’API Edit Pipeline prend désormais en charge la modification de l’environnement utilisé dans les phases de déploiement.

* Une optimisation du processus d’analyse OakPal a été introduite pour les modules volumineux.

* Le fichier CSV de problème de qualité contient désormais l’horodatage de chaque problème de qualité.

### Correctifs {#bug-fixes}

* Certaines configurations de génération non orthodoxes entraînaient le stockage de fichiers inutiles dans le cache d’artefacts Maven du pipeline, ce qui entraînait des E/S réseau superflues lors du démarrage et de l’arrêt du conteneur de génération.

* L’API du PATCH de pipeline échoue si la phase de déploiement n’existe pas.

* Le `ClientlibProxyResourceCheck` la règle de qualité générait des problèmes de faux positifs lorsqu’il existait des bibliothèques clientes avec des chemins d’accès de base communs.

* Un message d’erreur indiquant que le nombre maximal de référentiels a été atteint ne précisait pas la raison de l’erreur.

* Dans de rares cas, les pipelines échouaient en raison d’une gestion inappropriée des reprises de certains codes de réponse.

