---
title: Notes de mise à jour de Cloud Manager 2022.6.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2022.6.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 0a348836-74cd-4fd4-aef4-6ffbd6483c24
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 52%

---

# Notes de mise à jour de Cloud Manager 2022.6.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager 2022.6.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de la version actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2022.6.0 de Cloud Manager dans AEM as a Cloud Service est le 9 juin 2022. La prochaine version est prévue pour le 30 juin 2022.

## Nouveautés {#what-is-new}

* L’interface utilisateur de Cloud Manager permet désormais [restauration de contenu en libre-service](/help/operations/backup.md) à un état connu de l’environnement cloud AEM.
   * Cette fonctionnalité sera déployée par étapes au cours des semaines qui suivront la version 2022.06.0.
* Une nouvelle carte de bienvenue sur la page de destination de Cloud Manager permet aux utilisateurs d’accéder rapidement aux tutoriels d’intégration et aux mesures de progression liées au client.
   * Cette fonctionnalité sera déployée progressivement au cours de la semaine suivant la publication de la version 2022.06.0.
* Les utilisateurs disposant des autorisations requises peuvent accéder à une nouvelle [Tableau de bord des licences](/help/implementing/cloud-manager/license-dashboard.md) sur la page d’entrée de Cloud Manager pour afficher les détails des droits disponibles pour le client.
   * AEM Sites est la première solution pour laquelle la disponibilité et la consommation d’utilisation sont diffusées via le tableau de bord Cloud Manager.
   * Cette fonctionnalité sera déployée par étapes au cours des semaines qui suivront la version 2022.06.0.
* [Nouvelle gestion des sous-comptes relatifs et des utilisateurs en libre-service](/help/implementing/cloud-manager/user-access-new-relic.md) est désormais disponible via l’interface utilisateur de Cloud Manager.
   * Cette fonctionnalité sera déployée par étapes au cours des semaines qui suivront la version 2022.06.0.
* Un nouveau widget GoLive sur la page d’accueil des programmes de production de Cloud Service fournit désormais des conseils pour préparer une expérience de mise en ligne réussie.
* [Les artefacts de build peuvent désormais être réutilisés](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) lors de l’utilisation de la mise en miroir git.

## Modifications d’API {#api-changes}

* L’API [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms) a été abandonnée et [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) doit être utilisé à la place.
   * `List Programs` continue de fonctionner, mais son utilisation génère des messages d’avertissement dans les journaux.
   * Il ne sera plus pris en charge au bout de trois mois.
