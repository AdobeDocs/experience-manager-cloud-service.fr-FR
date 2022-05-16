---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2022.01.0
description: Consultez les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2022.01.0.
feature: Release Information
exl-id: 2dfdc943-0518-40ea-8712-1dabb97eeaa9
source-git-commit: 6e394aaabcb123aea53fba49684aaade3e6c87a6
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 94%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2022.01.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service 2022.01.0.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de la version actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM 2022.01.0 as a Cloud Service est le 20 janvier 2022. La prochaine version est prévue pour le 10 février 2022.

## Nouveautés {#what-is-new}

* Cloud Manager [évitera de reconstruire la base de code lorsqu&#39;il détecte que la même validation Git est utilisée](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) dans plusieurs exécutions de pipeline de pile complète.
* L’accès au journal d’environnement AEM nécessite désormais le profil produit **Gestionnaire de déploiement**. Un bouton désactivé s’affiche dans l’interface utilisateur pour les utilisateurs ne disposant pas de ce profil.
* L’interface utilisateur n’autorise pas la configuration du pipeline front-end pour un programme où Sites n’est pas activé en tant que solution.
* Lors de la génération d’un mot de passe Git, la date d’expiration s’affiche.

## Correctifs {#bug-fixes}

* Les exceptions de pointeurs nuls rencontrées par certains déploiements de pipelines front-end ont été corrigées.
* Les variables d’environnement peuvent désormais être ajoutées, mises à jour et supprimées lorsqu’un environnement exécute une version obsolète d’AEM.
* L’étape de création d’image ne sera plus marquée comme ERREUR pour les pipelines qui ont utilisé l’étape planifiée dans de rares cas.
* Pour les programmes ne comportant qu’un seul référentiel, l’écran d’exécution du pipeline affiche désormais le nom du référentiel.
