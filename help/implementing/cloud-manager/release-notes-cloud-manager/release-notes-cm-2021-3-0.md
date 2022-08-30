---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0
feature: Release Information
exl-id: f826e0c6-3b1d-44f5-99a2-f792f5df3a55
source-git-commit: 575be022704e998e63162f19c37ece877efef627
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 96%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.3.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.3.0 est le 11 mars 2021.

## Cloud Manager {#cloud-manager}

### Nouveautés {#what-is-new}

* Les clients disposant d’environnements avec des configurations de nom de domaine personnalisé préexistantes pour les [listes autorisées d’adresses IP](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn), les [certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn) et les [Noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) verront un message sur leurs configurations existantes et pourront se servir eux-mêmes via l’interface utilisateur.

* Les utilisateurs disposant des autorisations requises peuvent désormais modifier un programme, ce qui leur permet d’effectuer les opérations suivantes en libre-service :
   * Ajouter la solution Sites à un programme existant avec Assets, ou inversement.
   * Supprimer Sites ou Assets d’un programme existant contenant à la fois Sites et Assets.
   * Ajouter un deuxième droit non utilisé sur une solution à un programme existant ou à titre de nouveau programme.

* **Mise à jour AEM maintenance** Le libellé s’affiche désormais pour les écrans Exécution du pipeline et Activité .

* Si un environnement est mis en veille prolongée, mais qu’une mise à jour AEM est également disponible, l’état **En veille** prévaudra sur **Mise à jour disponible**.

* Les utilisateurs peuvent désormais voir leur(s) rôle(s) Cloud Manager en sélectionnant l’option Afficher les rôles de Cloud Manager après avoir accédé à l’icône de Profil utilisateur (en haut à droite) du shell unifié.

* Pour plus de clarté, l’étiquette **Application à approuver** a été réétiquetée à **Approbation de production**.

* Le libellé **Version** a été renommé **Balise Git** dans l’écran d’exécution du pipeline de production.

* Les libellés qui définissent le comportement lorsque des mesures importantes ne respectent pas le seuil défini ont été réétiquetées afin de refléter leur comportement réel : **Annuler immédiatement** et **Approuver immédiatement**.

* Les listes de classe et de méthode d’obsolescence ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK AEM Cloud Service.

* Le pipeline de production de Cloud Manager inclut désormais la fonctionnalité de [test d’interface utilisateur personnalisée](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

### Correctifs  {#bug-fixes}

* Le contrôle de version du package était parfois ignoré lors d’une mise à niveau Push d’AEM.

* Certains problèmes de qualité n’étaient pas été correctement détectés lorsque des packages étaient incorporés dans d’autres packages.

* Dans des situations obscures, le nom de programme par défaut généré à l’ouverture de la boîte de dialogue Ajouter le programme pouvait être un doublon d’un nom de programme existant.

* Parfois, si l’utilisateur quitte la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affiche indiquant que l’action a échoué, bien que l’exécution ait effectivement démarré.

* L’étape de création était inutilement redémarrée lorsque les compilations de clients généraient des packages non valides.

* Il peut arriver que l’utilisateur voit un état « actif » vert en regard d’une liste d’adresses IP autorisées même si cette configuration n’a pas été déployée.

* Tous les pipelines de production existants seront automatiquement activés avec l’étape Contrôle de l’expérience.
