---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.4.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.4.0
feature: Release Information
exl-id: a11ebe0e-2872-4fde-acc0-5babc6b01e1a
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.4.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.4.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.4.0 est le 8 avril 2021.
La prochaine version est prévue pour le 6 mai 2021.

### Nouveautés {#what-is-new-april}

* Mises à jour de l’interface utilisateur des workflows Ajouter et Modifier le programme pour la rendre plus intuitive.

* Un utilisateur disposant des autorisations requises peut désormais envoyer le point d’entrée de Commerce grâce à l’interface utilisateur.

* Les variables d’environnement peuvent désormais être incluses dans un service spécifique, qu’il s’agisse de création ou de publication. Nécessite AEM version `2021.03.5104.20210328T185548Z` ou supérieure.

* Le bouton **Gérer Git** s’affiche sur la carte Pipelines même si aucun pipeline n’a été configuré.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 27.

* Il n’est plus possible de modifier ni de supprimer involontairement les projets créés par Cloud Manager dans Adobe I/O Developer Console.

* Lorsqu’un utilisateur ajoute un nouvel environnement, il est informé qu’une fois qu’un environnement est créé, il ne peut pas être déplacé vers une autre région.

* Les variables d’environnement peuvent désormais être incluses dans un service spécifique, qu’il s’agisse de création ou de publication. Nécessite AEM version 2021.03.5104.20210328T185548Z, ou ultérieure.

* Le message d’erreur, lors de la suppression d’un environnement au démarrage d’un pipeline, a été clarifié.

* Les lots OSGi fournis par les projets Eclipse sont désormais exclus de la règle `CQBP-84--dependencies`.

### Correctifs {#bug-fixes-cm-april}

* Lors de la modification de la page de contrôle de l’expérience d’un pipeline, un chemin d’entrée commençant par une barre oblique `( / )` n’entraîne plus le blocage de l’étape à l’état En attente.

* Lorsqu’un pipeline de production est créé, si aucun remplacement d’audit de contenu n’est ajouté par l’utilisateur, la page d’accueil par défaut n’a pas été contrôlée.

* La gravité des problèmes de `CloudServiceIncompatibleWorkflowProcess` était incorrecte dans le fichier CSV de problème téléchargeable.

* La vérification `Runmode` produisait des faux positifs sur les nœuds autres que des dossiers.
