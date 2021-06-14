---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0
feature: Informations sur la version
source-git-commit: 04195582602c0cb4cc6d359dff6abfc8dbc24614
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 15%

---


# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.6.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.6.0.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.6.0 est le 10 juin 2021.
La prochaine version est prévue pour le 15 juillet 2021.

### Nouveautés {#what-is-new}

* Le service Preview sera déployé de manière progressive dans tous les programmes. Les clients seront avertis dans le produit lorsque leur programme sera activé pour le service de prévisualisation. Pour plus d’informations, voir [Accès au service d’aperçu](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

* Les dépendances Maven téléchargées lors de l’étape de création seront désormais mises en cache entre les exécutions de pipeline. Cette fonctionnalité sera activée pour les clients au cours des prochaines semaines.

* Le nom du programme peut maintenant être modifié à partir de la boîte de dialogue de modification du programme.

* Le nom de branche par défaut utilisé lors de la création du projet et dans la commande push par défaut via la gestion des workflows git a été remplacé par `main`.

* La modification de l’expérience du programme dans l’interface utilisateur a été actualisée.

* La règle de qualité `ImmutableMutableMixCheck` a été mise à jour afin de classer les noeuds `/oak:index` comme étant immuables.

* Les règles de qualité `CQBP-84` et `CQBP-84--dependencies` ont été consolidées dans une seule règle. Dans le cadre de cette consolidation, l’analyse des dépendances identifie plus précisément les problèmes des dépendances tierces qui sont déployés sur le runtime AEM.

* Pour éviter toute confusion, les lignes de segment AEM de publication et Publier Dispatcher sur la page Détails de l’environnement ont été consolidées.

   ![](/help/onboarding/release-notes-cloud-manager/assets/aem-dispatcher.png)

* Une nouvelle règle de qualité du code a été ajoutée pour valider la structure des index `damAssetLucene`. Pour plus d’informations, voir [Index Lucene Oak des ressources DAM personnalisées](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check) .

* La page Détails de l’environnement affiche désormais plusieurs noms de domaine pour les services de publication et de prévisualisation (le cas échéant). Pour plus d’informations, voir [Détails de l’environnement](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) .

### Correctifs {#bug-fixes}

* Les définitions de noeud JCR contenant une nouvelle ligne après le nom de l’élément racine n’étaient pas correctement analysées.

* L’API de liste des référentiels ne filtre pas les référentiels supprimés.

* Un message d’erreur incorrect s’affichait lorsqu’une valeur non valide était fournie pour l’étape de planification.

* Parfois, l’utilisateur peut voir un état *principal* en regard d’une Liste autorisée IP même lorsque cette configuration n’a pas été déployée.

* Certaines séquences de modification de programme peuvent empêcher la création ou la modification du pipeline de production.

* Certaines séquences de modification de programme peuvent entraîner l’affichage d’un message trompeur sur la page **Aperçu** pour exécuter à nouveau la configuration du programme.
