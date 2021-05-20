---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0
feature: Informations sur la version
exl-id: 42cc9cab-6e66-4976-a3b1-ecb9dbaaabf4
source-git-commit: 84a97f09402602df33c8f0494feed57fdb510add
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 16%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.3.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.3.0 est le 11 mars 2021.

## Cloud Manager {#cloud-manager}

### Nouveautés {#what-is-new}

* Les clients avec des environnements avec des configurations de nom de domaine personnalisé préexistantes pour les [Listes autorisées IP](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) et [Noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) verront un message sur leurs configurations existantes précédemment et pourront se mettre en libre-service via l’interface utilisateur.

* Les utilisateurs disposant des autorisations requises peuvent désormais modifier un programme, ce qui leur permet d’effectuer les opérations suivantes en libre-service :
   * Ajoutez la solution Sites à un programme existant avec Assets ou inversement.
   * Supprimez Sites ou Assets d’un programme existant avec Sites et Assets.
   * Ajoutez le deuxième droit de solution inutilisé à un programme existant ou en tant que nouveau programme.

* **Le** libellé de mise à jour push AEM s’affiche désormais pour les écrans Exécution du pipeline et Activité.

* Si un environnement est mis en veille, mais qu’une mise à jour d’AEM est également disponible, l’état **Hibernated** prévaudra sur **Mettre à jour disponible**.

* Les utilisateurs peuvent désormais voir leurs rôles Cloud Manager en sélectionnant l’option &quot;Afficher les rôles Cloud Manager&quot; après avoir accédé à l’icône Profil utilisateur (en haut à droite) de Shell unifié.

* Le libellé **Demande d’approbation** a été renommé **Approbation de production** pour plus de clarté.

* Le libellé **Version** a été renommé **Balise Git** dans l’écran d’exécution du pipeline de production.

* Les étiquettes qui définissent le comportement lorsque des mesures importantes ne correspondent pas au seuil défini ont été réétiquetées afin de refléter leur comportement réel : **Annuler immédiatement** et **Approuver immédiatement**.

* Les listes d’obsolescence des classes et des méthodes ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK Cloud Service AEM.

* Le pipeline de production de Cloud Manager comprend désormais la fonctionnalité [Tests d’interface utilisateur personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) .

### Correctifs {#bug-fixes}

* Le contrôle de version des packages a été parfois ignoré lors de la mise à niveau AEM push.

* Certains problèmes de qualité n’ont pas été correctement découverts lorsque des modules étaient incorporés dans d’autres modules.

* Dans des cas obscurs, le nom de programme par défaut généré lors de l’ouverture de la boîte de dialogue Ajouter un programme peut être un doublon d’un nom de programme existant.

* Parfois, si l’utilisateur quitte la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affiche indiquant que l’action a échoué, bien que l’exécution ait réellement commencé.

* L’étape de création a été inutilement redémarrée lorsque les compilations de clients ont entraîné des packages non valides.

* Parfois, l’utilisateur peut voir un état &quot;principal&quot; vert en regard d’une Liste autorisée IP même lorsque cette configuration n’a pas été déployée.

* Tous les pipelines de production existants seront automatiquement activés avec l’étape Contrôle de l’expérience.
