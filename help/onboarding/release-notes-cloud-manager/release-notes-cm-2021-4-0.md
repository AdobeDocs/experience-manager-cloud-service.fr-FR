---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.4.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.4.0
feature: Informations sur la version
translation-type: tm+mt
source-git-commit: e2d4bb7649fad3ee172c6f049ecfdedc71417ee2
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 18%

---


# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.4.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.4.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager en tant que Cloud Service 2021.4.0 est le 08 avril 2021.
La prochaine version est prévue pour le 6 mai 2021.

### Nouveautés {#what-is-new-april}

* L’interface utilisateur met à jour les workflows d’Ajoute et de modification de Programme pour les rendre plus intuitifs.

* Un utilisateur disposant des autorisations requises peut désormais envoyer le point de terminaison du commerce via l’interface utilisateur.

* Les variables d’Environnement peuvent désormais être étendues à un service spécifique, qu’il s’agisse de l’auteur ou de la publication. Requiert AEM version `2021.03.5104.20210328T185548Z` ou supérieure.

* Le bouton **Gérer Git** s&#39;affiche sur la carte Pipelines même si aucun pipeline n&#39;a été configuré.

* La version de l’archétype de projet AEM utilisée par Cloud Manager a été mise à jour vers la version 27.

* Les projets de la console de développement des Adobes I/O créés par Cloud Manager ne peuvent plus être modifiés ou supprimés involontairement.

* Lorsqu’un utilisateur ajoute un nouvel environnement, il est informé qu’une fois qu’un environnement est créé, il ne peut plus être déplacé dans une autre région.

* Les variables d’Environnement peuvent désormais être étendues à un service spécifique, qu’il s’agisse de l’auteur ou de la publication. Requiert AEM version 2021.03.5104.20210328T185548Z ou supérieure.

* Le message d&#39;erreur lors du démarrage d&#39;un pipeline lorsqu&#39;un environnement a été supprimé a été clarifié.

* Les lots OSGi fournis par les projets Eclipse sont maintenant exclus de la règle `CQBP-84--dependencies`.

### Correctifs {#bug-fixes-cm-april}

* Lors de la modification de la page de contrôle d’expérience d’un pipeline, un chemin d’entrée commençant par une barre oblique `( / )` n’entraîne plus l’blocage de l’étape dans l’état en attente.

* Lors de la création d&#39;un nouveau pipeline de production, si aucun remplacement de contrôle du contenu n&#39;est ajouté par l&#39;utilisateur, la page d&#39;accueil par défaut n&#39;a pas été contrôlée.

* La gravité des problèmes de `CloudServiceIncompatibleWorkflowProcess` était incorrecte dans le fichier CSV de publication téléchargeable.

* La vérification `Runmode` produisait des faux positifs sur les noeuds non-dossiers.