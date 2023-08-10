---
title: Notes de mise à jour de Cloud Manager 2023.8.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2023.8.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: d1640c14c796d7b7b6a7b236b38077e360559966
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 27%

---


# Notes de mise à jour de Cloud Manager 2023.8.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2023.8.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Voir [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de Cloud Manager version 2023.8.0 dans AEM as a Cloud Service est le 10 août 2023. La prochaine version est prévue pour le 7 septembre 2023.

## Nouveautés {#what-is-new}

* Lors de la configuration d’un jeu de contenu sur [copier le contenu,](/help/implementing/developing/tools/content-copy.md) [configurations basées sur le contexte](/help/implementing/developing/introduction/configurations.md) sont désormais autorisées dans les jeux de contenu de l’interface utilisateur.
* Des améliorations ont été apportées pour améliorer la lisibilité et l’affichage des messages d’erreur dans l’interface utilisateur de Cloud Manager.

## Programme d’adoption anticipée de la restauration de contenu en libre-service {#early-adoption}

[Nouvelle fonctionnalité de restauration de contenu en libre-service](/help/operations/restore.md) fournit désormais une restauration de sauvegarde pendant sept jours au maximum et est disponible pour les utilisateurs précoces à des fins d’évaluation, notamment :

* Restauration de sauvegarde ponctuelle des dernières 24 heures
* Restauration de la période fixe pendant sept jours au maximum

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-restorefrombackup-adopter@adobe.com` de votre email associé à votre Adobe ID. Remarque :

* Le programme d’adoption précoce est limité aux environnements de développement uniquement.
* La disponibilité du programme d’adoption précoce est limitée.
* Cette fonctionnalité est destinée à la récupération de contenu supprimé accidentellement et n’est pas destinée à la reprise après sinistre.

## Correctifs {#bug-fixes}

* La variable **Environnements** se ferme maintenant après avoir déclenché la **[Copier le contenu](/help/implementing/developing/tools/content-copy.md)** modale.
* [Réexécution d’un pipeline](/help/implementing/cloud-manager/deploy-code.md#reexecute-deployment) n’est plus autorisé si l’exécution précédente n’a pas de `commitId` défini sur l’état de la phase de création.
* Un message plus compréhensible s’affiche désormais pour les erreurs rares lorsqu’un utilisateur clique sur un pipeline dans **Activité** ou **Pipeline** screens.
* La variable `contentSetName` n’est plus manquante dans les journaux et est désormais fournie dans les entrées lors du démarrage d’une [copie de contenu](/help/implementing/developing/tools/content-copy.md) opération.
* Il n’est plus possible, dans de rares circonstances, de démarrer deux exécutions à partir du même pipeline menant à un état &quot;bloqué&quot;.
* Lorsqu’un certificat expire, les noms de domaine et les listes autorisées IP associés au certificat ne sont plus supprimés du réseau de diffusion de contenu.
   * Dans ce cas, le site reste accessible.
   * [](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)L’interface utilisateur de Cloud Manager fournit des avertissements avancés plus visibles indiquant que le certificat SSL est sur le point d’expirer.
* Correction d’un problème en raison duquel AEM perdait l’accès à un point de terminaison de publication dans les situations où Sites était ajouté en tant que solution à un programme Assets uniquement.
