---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0
translation-type: tm+mt
source-git-commit: 5dabb0f9f119d8c56c4b1b64e1528f03e1a92fac
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 16%

---


# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.3.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager en tant que Cloud Service 2021.3.0 dans AEM est le 11 mars 2021.
La prochaine version est prévue pour le 8 avril 2021.

## Cloud Manager {#cloud-manager}

### Nouveautés {#what-is-new}

* Les clients disposant d’environnements avec des configurations de nom de domaine personnalisé préexistantes pour [Listes autorisées IP](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) et [Noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) verront un message sur leurs configurations existantes et pourront se servir eux-mêmes via l’interface utilisateur. Les utilisateurs peuvent désormais :
   * Ajouter la solution Sites à un programme existant avec Ressources (ou inversement).
   * Supprimez des sites (ou des ressources) d’un programme existant avec des sites et des ressources.
   * Ajoutez ensuite les droits de solution inutilisés à un programme existant ou en tant que nouveau Programme.

* Les utilisateurs disposant des autorisations requises peuvent désormais modifier le Programme, ce qui leur permet d’effectuer les opérations suivantes en libre-service.

* L’étiquette &quot;Mise à jour AEM Push&quot; s’affiche désormais pour les écrans d’exécution du pipeline et d’Activité.

* Si un environnement est mis en veille prolongée mais qu’une mise à jour AEM est également disponible, l’état &quot;Hébergé&quot; prévaudra sur &quot;Mise à jour disponible&quot;.

* Les utilisateurs peuvent désormais voir leur ou leurs rôles Cloud Manager en sélectionnant l’option &quot;Rôle(s) de Vue Cloud Manager&quot; après avoir accédé à l’icône Profil utilisateur (en haut à droite) de l’environnement de travail unifié.

* L&#39;étiquette &quot;Demande d&#39;approbation&quot; a été réétiquetée &quot;Approbation de production&quot; pour plus de clarté.

* Le libellé &quot;Version&quot; a été réétiqueté en &quot;Balise Git&quot; dans l’écran d’exécution du pipeline de production.

* Les étiquettes qui définissent le comportement lorsque des mesures importantes ne respectent pas le seuil défini ont été réétiquetées pour refléter leur comportement réel : Annuler immédiatement et Approuver immédiatement.

* Les listes de classe et de méthode d’obsolescence ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK Cloud Service AEM.

* Le pipeline de production de Cloud Manager inclut désormais la fonctionnalité de test d’interface utilisateur personnalisée.

### Correctifs {#bug-fixes}

* Le contrôle de version du package a parfois été ignoré lors de la mise à niveau AEM Push.

* Certains problèmes de qualité n&#39;ont pas été correctement détectés lorsque des paquets étaient incorporés dans d&#39;autres paquets.

* Dans des situations obscures, le nom de programme par défaut généré à l&#39;ouverture de la boîte de dialogue Ajouter le Programme peut être un duplicata d&#39;un nom de programme existant.

* Parfois, si l’utilisateur quitte la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affiche indiquant que l’action a échoué, bien que l’exécution ait effectivement début.

* L’étape de création a été inutilement redémarrée lorsque les compilations de clients ont généré des packs non valides.

* Il peut arriver que l’utilisateur voit un état &quot;principal&quot; vert en regard d’une Liste autorisée IP même si cette configuration n’a pas été déployée.

* Tous les pipelines de production existants seront automatiquement activés avec l’étape Contrôle de l’expérience.