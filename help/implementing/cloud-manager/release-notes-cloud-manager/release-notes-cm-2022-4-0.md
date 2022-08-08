---
title: Notes de mise à jour de Cloud Manager 2022.4.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2022.4.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: e7ff623b-aeca-40a6-bf48-98af270a4117
source-git-commit: 458d63c27bb2ab4d09237aa3ecb96c0f6d5e67ed
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager 2022.4.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager 2022.4.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de la version actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de Cloud Manager version 2022.4.0 dans AEM as a Cloud Service est le 7 avril 2022. La prochaine version est prévue pour le 5 mai 2022.

## Nouveautés {#what-is-new}

* Des améliorations ont été apportées à la durée et au taux de succès des étapes de création de pipeline. Elles seront progressivement déployées pour tous les clients tout au long du mois d’avril.
* Vous pouvez désormais facilement trouver une branche Git en saisissant les premiers caractères du nom dans le champ de saisie de l’assistant d’ajout et de modification de pipeline, puis en sélectionnant parmi les correspondances suggérées à la fois pour les pipelines de [production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) et [hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).
* Peu après la version d’avril, l’Inde pourra être sélectionnée lors de la définition de la région cloud lors de la création de l’environnement.
* La page des **Pipelines** dispose désormais d’une pagination qui permet d’améliorer la convivialité des programmes avec un grand nombre de pipelines.
   * 50 lignes par page s’affichent dans le tableau.
* L’[archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) utilisé par Cloud Manager a été mis à jour à la version 36.
* Le JDK Oracle est désormais le JDK par défaut pour le développement et l’exécution des applications AEM. Le processus de création de Cloud Manager bascule automatiquement sur l’utilisation du JDK Oracle, même si une autre option est explicitement sélectionnée dans la chaîne d’outils Maven.
   * Pour en savoir plus sur le basculement vers le JDK Oracle, reportez-vous à la [documentation sur l’environnement de création.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support)
   * Reportez-vous à la [FAQ sur la politique de prise en charge de Java pour Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65/assets/Java_Policy_for_Adobe_Experience_Manager.pdf) pour répondre aux questions courantes sur ce changement.
* L’exécution du pipeline échoue désormais plus rapidement en détectant les anciennes versions AEM lors de l’étape de validation. Un message s’affiche dans l’interface utilisateur pour les guider.

## Correctifs {#bug-fixes}

* Le journal créé à l’étape Test de l’interface utilisateur peut désormais être téléchargé via l’interface utilisateur.
* Les pipelines de configuration de niveau web ne peuvent désormais réutiliser que les packages des exécutions de configuration de niveau web.
* Des messages plus clairs ont été ajoutés aux messages de l’interface utilisateur sur la mise à jour d’AEM dans un environnement obsolète.
