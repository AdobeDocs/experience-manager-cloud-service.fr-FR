---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2022.01.0
description: Il s’agit des notes de mise à jour de Cloud Manager dans AEM version as a Cloud Service 2022.01.0.
feature: Release Information
source-git-commit: 8da3976250c94d5858d07a83b0eb395fab9a3eda
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 12%

---


# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2022.01.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM 2022.01.0 as a Cloud Service.

>[!NOTE]
>
>Voir [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM 2022.01.0 as a Cloud Service est le 20 janvier 2022. La prochaine version est prévue pour le 10 février 2022.

## Nouveautés {#what-is-new}

* Cloud Manager [évitez de reconstruire la base de code lorsqu’il détecte que la même validation git est utilisée.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) dans plusieurs exécutions de pipeline de pile complète.
* L’accès au journal de l’environnement AEM requiert désormais le **Responsable de déploiement** profil de produit. Un bouton désactivé s’affiche dans l’interface utilisateur pour les utilisateurs ne disposant pas de ce profil.
* L’interface utilisateur n’autorise pas la configuration du pipeline frontal pour un programme où Sites n’est pas activé en tant que solution.
* Lors de la génération d’un mot de passe Git, la date d’expiration s’affiche.

## Correctifs {#bug-fixes}

* Les exceptions null pointer rencontrées par certains déploiements de pipeline front-end ont été corrigées.
* Les variables d’environnement peuvent désormais être ajoutées, mises à jour et supprimées lorsqu’un environnement exécute une version obsolète d’AEM.
* L’étape de création d’image ne sera plus marquée comme ERREUR pour les pipelines qui ont utilisé l’étape planifiée dans de rares cas.
* Pour les programmes ne comportant qu’un seul référentiel, l’écran d’exécution du pipeline affiche désormais le nom du référentiel.
