---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0
translation-type: tm+mt
source-git-commit: 7059f0868fec3bbc665725c9ad2cc252805d8916
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 16%

---


# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.3.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager en tant que Cloud Service 2021.3.0 dans AEM est le 11 mars 2021.
La prochaine version est prévue pour le 8 avril 2021.

## Cloud Manager {#cloud-manager}

### Nouveautés {#what-is-new}

* Les clients disposant d’environnements avec des configurations de nom de domaine personnalisé préexistantes pour [Listes autorisées IP](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) et [Noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) verront un message sur leurs configurations existantes et pourront se servir eux-mêmes via l’interface utilisateur.

* Les utilisateurs disposant des autorisations requises peuvent désormais modifier un Programme, ce qui leur permet d’effectuer les opérations suivantes en libre-service :
   * Ajouter la solution Sites à un programme existant avec Ressources ou inversement.
   * Supprimez des sites ou des ressources d’un programme existant avec des sites et des ressources.
   * Ajoutez ensuite les droits de solution inutilisés à un programme existant ou en tant que nouveau Programme.

* **Le** libellé de mise à jour Push AEM sera désormais affiché pour les écrans Exécution du pipeline et Activité.

* Si un environnement est mis en veille prolongée, mais qu&#39;une mise à jour AEM est également disponible, l&#39;état **Hibernated** prévaudra sur **Mise à jour disponible**.

* Les utilisateurs peuvent désormais voir leur ou leurs rôles Cloud Manager en sélectionnant l’option &quot;Rôle(s) de Vue Cloud Manager&quot; après avoir accédé à l’icône Profil utilisateur (en haut à droite) de l’environnement de travail unifié.

* Pour plus de clarté, l&#39;étiquette **Demande d&#39;approbation** a été réétiquetée à **Approbation de production**.

* Le libellé **Version** a été réétiqueté en **Balise Git** dans l&#39;écran d&#39;exécution du pipeline de production.

* Les étiquettes qui définissent le comportement lorsque des mesures importantes ne respectent pas le seuil défini ont été réétiquetées pour refléter leur comportement réel : **Annuler immédiatement** et **Approuver immédiatement**.

* Les listes de classe et de méthode d’obsolescence ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK Cloud Service AEM.

* Le pipeline de production de Cloud Manager inclut désormais la fonctionnalité [Tests d’interface utilisateur personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

### Correctifs {#bug-fixes}

* Le contrôle de version du package a parfois été ignoré lors de la mise à niveau AEM Push.

* Certains problèmes de qualité n&#39;ont pas été correctement détectés lorsque des paquets étaient incorporés dans d&#39;autres paquets.

* Dans des situations obscures, le nom de programme par défaut généré à l&#39;ouverture de la boîte de dialogue Ajouter le Programme peut être un duplicata d&#39;un nom de programme existant.

* Parfois, si l’utilisateur quitte la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affiche indiquant que l’action a échoué, bien que l’exécution ait effectivement début.

* L’étape de création a été inutilement redémarrée lorsque les compilations de clients ont généré des packs non valides.

* Il peut arriver que l’utilisateur voit un état &quot;principal&quot; vert en regard d’une Liste autorisée IP même si cette configuration n’a pas été déployée.

* Tous les pipelines de production existants seront automatiquement activés avec l’étape Contrôle de l’expérience.