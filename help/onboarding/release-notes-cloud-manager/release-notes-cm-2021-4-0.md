---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.4.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.4.0
feature: Informations sur la version
source-git-commit: e2d4bb7649fad3ee172c6f049ecfdedc71417ee2
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 18%

---


# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.4.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.4.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.4.0 est le 8 avril 2021.
La prochaine version est prévue pour le 6 mai 2021.

### Nouveautés {#what-is-new-april}

* Mises à jour de l’interface utilisateur des workflows Ajouter et modifier le programme pour le rendre plus intuitif.

* Un utilisateur disposant des autorisations requises peut désormais envoyer le point de terminaison du commerce via l’interface utilisateur.

* Les variables d’environnement peuvent désormais être incluses dans un service spécifique, qu’il s’agisse de création ou de publication. Nécessite AEM version `2021.03.5104.20210328T185548Z` ou supérieure.

* Le bouton **Gérer Git** s’affiche sur la carte Pipelines même si aucun pipeline n’a été configuré.

* La version de l’archétype de projet AEM utilisé par Cloud Manager a été mise à jour vers la version 27.

* Les projets dans Adobe I/O Developer Console créés par Cloud Manager ne peuvent plus être modifiés ou supprimés involontairement.

* Lorsqu’un utilisateur ajoute un nouvel environnement, il est informé qu’une fois qu’un environnement est créé, il ne peut pas être déplacé vers une autre région.

* Les variables d’environnement peuvent désormais être incluses dans un service spécifique, qu’il s’agisse de création ou de publication. Nécessite AEM version 2021.03.5104.20210328T185548Z ou ultérieure.

* Le message d’erreur lors du démarrage d’un pipeline lorsqu’un environnement a été supprimé a été clarifié.

* Les lots OSGi fournis par les projets Eclipse sont désormais exclus de la règle `CQBP-84--dependencies`.

### Correctifs {#bug-fixes-cm-april}

* Lors de la modification de la page de contrôle de l’expérience d’un pipeline, un chemin d’entrée commençant par une barre oblique `( / )` n’entraîne plus le blocage de l’étape à l’état en attente.

* Lorsqu’un nouveau pipeline de production est créé, si aucun remplacement d’audit de contenu n’est ajouté par l’utilisateur, la page d’accueil par défaut n’a pas été contrôlée.

* Les problèmes pour `CloudServiceIncompatibleWorkflowProcess` étaient de gravité incorrecte dans le fichier CSV de problème téléchargeable.

* La vérification `Runmode` produisait des faux positifs sur les noeuds non-dossiers.