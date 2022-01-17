---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0
feature: Release Information
source-git-commit: a707968483dc1196628b737ad207bfefe63ca94b
workflow-type: ht
source-wordcount: '420'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.6.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.6.0.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.6.0 est le 10 juin 2021.

### Nouveautés {#what-is-new}

* Le service de prévisualisation sera déployé de manière progressive dans tous les programmes. Les clients seront avertis dans le produit lorsque leur programme sera activé pour le service de prévisualisation. Pour plus d’informations, voir [Accès au service de prévisualisation](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

* Les dépendances Maven téléchargées lors de l’étape de création seront désormais mises en cache entre les exécutions de pipeline. Cette fonctionnalité sera activée pour les clients au cours des prochaines semaines.

* Le nom du programme peut maintenant être modifié à partir de la boîte de dialogue de modification du programme.

* Le nom de branche par défaut utilisé lors de la création du projet et dans la commande push par défaut dans les workflows de gestion git a été remplacé par `main`.

* L’expérience de modification d’un programme dans l’interface utilisateur a été actualisée.

* La règle de qualité `ImmutableMutableMixCheck` a été mise à jour afin de classer les nœuds `/oak:index` comme étant immuables.

* Les règles de qualité `CQBP-84` et `CQBP-84--dependencies` ont été consolidées dans une seule règle. Dans le cadre de cette consolidation, l’analyse des dépendances identifie plus précisément les problèmes des dépendances tierces qui sont déployées sur l’environnement d’exécution AEM.

* Pour éviter toute confusion, les lignes de segment de l’instance de publication AEM et de l’instance de publication de Dispatcher sur la page Détails de l’environnement ont été consolidées.

   ![](/help/implementing/cloud-manager/release-notes-cloud-manager/assets/aem-dispatcher.png)

* Une nouvelle règle de qualité du code a été ajoutée pour valider la structure des index `damAssetLucene`. Pour plus d’informations, voir [Index Lucene Oak des ressources DAM personnalisées](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check).

* La page Détails de l’environnement affiche désormais plusieurs noms de domaine pour les services de publication et de prévisualisation (le cas échéant). Pour plus d’informations, voir [Détails de l’environnement](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=fr#viewing-environment).

### Correctifs {#bug-fixes}

* Les définitions de nœud JCR contenant une nouvelle ligne après le nom de l’élément racine n’étaient pas correctement analysées.

* L’API de liste des référentiels ne filtrait pas les référentiels supprimés.

* Un message d’erreur incorrect s’affichait lorsqu’une valeur non valide était fournie lors de l’étape de planification.

* Il peut arriver que l’utilisateur voit un état *actif* vert en regard d’une liste d’adresses IP autorisées même si cette configuration n’a pas été déployée.

* Certaines séquences de modification de programme peuvent empêcher la création ou la modification du pipeline de production.

* Certaines séquences de modification de programme peuvent entraîner l’affichage d’un message trompeur sur la page **Aperçu** pour exécuter à nouveau la configuration du programme.
