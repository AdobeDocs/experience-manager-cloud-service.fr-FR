---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0
feature: Informations sur la version
exl-id: 8ae3cf2f-1865-427a-b612-bdf56e2f0304
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: ht
source-wordcount: '379'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.5.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.5.0 est le 6 mai 2021.

### Nouveautés {#what-is-new}

* La règle de qualité PackageOverlaps détecte désormais les cas où le même package a été déployé plusieurs fois, c’est-à-dire dans plusieurs emplacements incorporés, dans le même ensemble de packages déployé.

* Le point d’entrée du référentiel dans l’API publique inclut désormais l’URL de Git.

* Le journal de déploiement téléchargé par un utilisateur de Cloud Manager sera plus informatif et comprendra désormais des détails sur les échecs et les scénarios de succès.

* Les échecs intermittents rencontrés lors de la publication du code vers le git d’Adobe ont maintenant été résolus.

* Le module complémentaire Commerce peut désormais être appliqué aux programmes Sandbox pendant le workflow Modifier le programme.

* L’expérience *Modifier le programme* a été actualisée.

* Le tableau Noms de domaine de la page Détails de l’environnement affiche jusqu’à 250 noms de domaine par pagination.

* L’onglet **Solutions et modules complémentaires** dans les workflows **Ajouter un programme** et **Modifier le programme** affichera la solution, même si une seule solution est disponible pour le programme.

* Le message d’erreur dans le journal de l’étape de génération lorsque la version ne produisait aucun module de contenu déployé n’était pas clair.

### Correctifs {#bug-fixes}

* Il peut arriver que l’utilisateur voit un état « actif » vert en regard d’une liste d’adresses IP autorisées même si cette configuration n’a pas été déployée.

* Au lieu de supprimer des variables marquées comme « deleted », l’API des variables de pipelines se contentait de les marquer avec le statut **DELETED**.

* Certains problèmes de qualité de type Code Smell (conception inappropriée du logiciel) affectaient incorrectement l’évaluation de fiabilité.

* Comme les domaines génériques ne sont pas pris en charge, l’interface utilisateur ne permet pas à l’utilisateur d’envoyer un domaine de caractères génériques.

* Lorsqu’une exécution de pipeline était lancée entre minuit et 1 h du matin (UTC), il n’était pas garanti que la version d’artefact générée par Cloud Manager était supérieure à une version créée le jour précédent.

* Lors de la configuration du programme Sandbox, une fois que le projet doté d’un exemple de code a été créé, Gérer Git s’affiche sous la forme d’un lien à partir de la carte principale de la page Aperçu.
