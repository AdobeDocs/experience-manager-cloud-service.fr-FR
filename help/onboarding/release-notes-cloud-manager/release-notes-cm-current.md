---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0
feature: Informations sur la version
translation-type: tm+mt
source-git-commit: 29bc3d02295fb04f3aacda41c43d1733092e1f27
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 17%

---


# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.5.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles de Adobe Experience Manager en tant que Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de Cloud Manager en AEM Cloud Service 2021.5.0 est le 06 mai 2021.
La prochaine version est prévue pour le 3 juin 2021.

### Nouveautés {#what-is-new}

* La règle de qualité PackageOverlaps détecte désormais les cas où le même package a été déployé plusieurs fois, c’est-à-dire dans plusieurs emplacements incorporés, dans le même jeu de packages déployé.

* Le point de terminaison du référentiel dans l’API publique inclut désormais l’URL Git.

* Le journal de déploiement téléchargé par un utilisateur de Cloud Manager sera plus instructif et comprendra désormais des détails sur les échecs et les scénarios de réussite.

* Les échecs intermittents rencontrés lors de la publication du code à l&#39;Adobe git ont maintenant été résolus.

* Le module complémentaire Commerce peut désormais être appliqué aux programmes Sandbox pendant le processus de modification du programme.

* L’expérience *Modifier le programme* a été actualisée.

* Le tableau Noms de domaine de la page Détails de l&#39;Environnement affiche jusqu&#39;à 250 noms de domaine par pagination.

* L&#39;onglet **Solutions &amp; Ajoutes-ons** de **Programme d&#39;Ajoute** et **Programme d&#39;édition** affichera la solution, même si une seule solution est disponible pour le Programme.

* Le message d’erreur dans le journal des étapes de génération lorsque la génération n’a pas produit de packages de contenu déployés n’était pas clair.

### Correctifs {#bug-fixes}

* Il arrive que l’utilisateur voit un état &quot;principal&quot; vert en regard d’une Liste autorisée IP, même si cette configuration n’a pas été déployée.

* Au lieu de supprimer les variables &quot;supprimées&quot;, l&#39;API des variables de pipeline les marquerait uniquement avec l&#39;état **DELETED**.

* Certains problèmes de qualité du type de code ont eu une incidence incorrecte sur la cote de fiabilité.

* Comme les domaines génériques ne sont pas pris en charge, l’interface utilisateur empêche l’utilisateur d’envoyer un domaine générique.

* Lorsqu’une exécution de pipeline a été démarrée entre minuit et 1h heure UTC, la version d’artefact générée par Cloud Manager n’était pas garantie supérieure à une version créée le jour précédent.

* Lors de la configuration du programme Sandbox, une fois que le projet avec un exemple de code a été créé, Gérer Git s&#39;affiche comme un lien à partir de la carte de héros dans la page Aperçu.