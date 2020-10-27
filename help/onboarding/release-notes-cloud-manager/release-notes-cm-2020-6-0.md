---
title: Notes de mise à jour de Cloud Manager en AEM version 2020.6.0 du Cloud Service
description: Notes de mise à jour de Cloud Manager en AEM version 2020.6.0 du Cloud Service
translation-type: tm+mt
source-git-commit: ca690144a8254d5ffba354f0f96d9ef1c5202533
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 89%

---


# Release Notes for Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.6.0 {#release-notes}

Cette page présente les Notes de mise à jour de Cloud Manager en AEM en tant que Cloud Service 2020.6.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager en tant que Cloud Service 2020.6.0 est le 4 juin 2020.

## Nouveautés {#whats-new-cloud-manager}

* Un utilisateur possédant le rôle *Propriétaire de l’entreprise* dans Cloud Manager peut désormais supprimer un programme Sandbox depuis la landing page (par le biais d’un bouton d’action rapide sur la carte Programme) ou depuis le programme.

   Pour plus d’informations, voir [Suppression d’un programme Sandbox](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html).

* Un utilisateur du programme Sandbox possédant le rôle *Propriétaire d’entreprise* ou *Responsable de déploiement* dans Cloud Manager peut désormais supprimer ses jeux d’environnements de production et d’évaluation via l’interface utilisateur de Cloud Manager. L’option de suppression est désormais disponible à partir de la carte Environnement dans la page **Aperçu du programme**, mais aussi dans la page **Environnements**. La sélection de l’option de suppression dans l’environnement de production ou d’évaluation supprime également l’autre dans le jeu d’environnements.

   Pour plus d’informations, voir [Suppression d’un programme Sandbox](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html).

* Repères sur la landing page pour informer l’utilisateur sur la navigation de base.

* Assistants graphiques sur la page **Aperçu du programme** afin d’informer l’utilisateur sur la navigation de base dans Cloud Manager pour la prise en main.

* Une page **APPRENDRE** est désormais disponible dans Cloud Manager, accessible par le biais de la navigation supérieure. Cette page comprend des ressources destinées à aider les utilisateurs à en savoir plus sur les workflows les plus fréquemment utilisés en fonction du rôle qui leur est attribué dans Cloud Manager.

* Les programmes Sandbox sont maintenant identifiés au moyen d’un badge **Sandbox**, affiché dans la carte du programme sur la landing page, ainsi qu’en regard du nom du programme sur la page **Aperçu du Programme**.

* Un utilisateur possédant le rôle SysAdmin dispose désormais d’un accès d’un simple clic à l’emplacement d’Admin Console d’où peuvent être gérés les rôles des utilisateurs ou les autorisations d’accès à Cloud Manager. Un bouton **Gérer l’accès** est désormais disponible dans la landing page en regard du bouton **Ajouter le programme**.

   Pour plus d’informations, voir [Tâches SysAdmin](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks).

* Un utilisateur possédant le rôle SysAdmin dispose désormais d’un accès en un clic à l’instance d’auteur directement à partir de Cloud Manager.

   Pour plus d’informations, voir [Gestion de l’accès à l’instance d’auteur](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem).

* Le journal de génération inclut désormais la liste des artefacts détectés, y compris les packages de contenu ignorés.

* L’étape de création valide désormais que tous les packages de contenu générés comprennent toutes les propriétés obligatoires : nom, groupe et version.

* L’étape de génération confirme désormais qu’elle a produit au moins un module de contenu.

### Correctifs {#bug-fixes-cm}

* Dans certains cas, les icônes de la boîte de dialogue **Créer un Programme** n’étaient pas alignées.

* L’identifiant de version d’AEM n’était pas affiché de manière cohérente sur la page **Aperçu du programme**.

* Lors de la configuration du pipeline de production, l’option **Déploiement planifié** n’était pas visible pour certains clients.

### Problèmes connus {#known-issues-cm}

* Les environnements d’un programme Sandbox sont mis en veille prolongée lorsqu’aucune activité n’est détectée pendant une certaine durée. Cet état ne sera pas appliqué dans Cloud Manager. Il peut toutefois être appliqué par le biais de Developer Console. Ce problème sera traité dans une prochaine version.

* Le lien vers Developer Console directement à partir de Cloud Manager n’affiche pas l’option permettant de mettre en veille/réactiver un environnement de programme Sandbox. Pour résoudre ce problème, une fois dans Developer Console, ajoutez le motif `#release-cm-p1234-e5678` à la fin de l’URL, où *1234* correspond à l’identifiant de programme et *5678* à l’identifiant d’environnement. Ce problème sera traité dans une prochaine version.
