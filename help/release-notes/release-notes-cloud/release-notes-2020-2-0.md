---
title: Notes de mise à jour de la version 2020.2.0
description: Notes de mise à jour de la version 2020.2.0
translation-type: tm+mt
source-git-commit: 157809fb4aacf45358db6412dea04398a7f12495

---


# Notes de mise à jour d’AEM en tant que service Cloud 2020.2.0 {#release-notes}

La section suivante décrit les Notes de mise à jour générales d’Experience Manager en tant que service Cloud 2020.2.0.

La date de publication est le 13 février 2020.

## Cloud Manager {#cloud-manager}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager version 2020.2.0.

### Nouveautés {#what-is-new}

* La version de l’archétype d’Adobe Experience Manager a été mise à jour vers la version 22.
* Les environnements Stage et Production des programmes Sandbox/Demo peuvent désormais être mis à jour via l’interface utilisateur de Cloud Manager.
* Les URL utilisées dans les notifications Experience Cloud ont été optimisées afin d’éviter une redirection supplémentaire.
* Les étapes d’exécution du pipeline qui ont expiré indiquent maintenant explicitement ceci.
* L’étape d’analyse du code comporte désormais un journal téléchargeable.
* La feuille de calcul contenant les problèmes détectés lors de l’analyse du code comporte désormais une colonne avec un lien vers la documentation de la règle spécifique.

### Correctifs  {#bug-fixes}

* Les stratégies de sécurité du navigateur empêchaient parfois certains boutons de l’écran d’exécution du pipeline de fonctionner correctement.
* Les liens Aperçu, Environnements et Activité étaient parfois disponibles sur la page d’entrée de Cloud Manager.
* Certaines défaillances lors du déploiement peuvent empêcher la création de nouveaux pipelines.