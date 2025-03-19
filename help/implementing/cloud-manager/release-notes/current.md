---
title: Notes de mise à jour de Cloud Manager 2025.3.0 dans Adobe Experience Manager as a Cloud Service
description: En savoir plus sur la version 2025.3.0 de Cloud Manager dans AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 663234640f16e6aa653251399751abf5daa17f82
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 31%

---

# Notes de mise à jour de Cloud Manager 2025.3.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

En savoir plus sur la version 2025.3.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.


Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.3.0 de Cloud Manager dans AEM as a Cloud Service est le vendredi 13 mars 2025.

La prochaine version est prévue le vendredi 10 avril 2025.

## Nouveautés {#what-is-new}

* **Exécution de plusieurs pipelines**

  La possibilité d’exécuter plusieurs pipelines simultanément a été introduite dans la page Pipelines . Les utilisateurs doivent sélectionner au moins un pipeline, mais pas plus de dix. Dans le coin supérieur droit de la page Pipelines, cliquez sur **Exécuter la sélection (x)**. Une boîte de dialogue modale s’affiche, répertoriant les pipelines qui ne peuvent pas être démarrés. Cliquez sur **Exécuter** pour lancer tous les pipelines valides.

  ![Boîte de dialogue Exécuter les pipelines sélectionnés](/help/implementing/cloud-manager/release-notes/assets/run-selected-pipelines.png)

  Voir aussi [Exécution de plusieurs pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#run-multiple-pipelines)

* **Prise en charge étendue des versions de Node.js**

  L’environnement de création front-end prend désormais en charge les versions `Node.js` suivantes :

   * 23
   * 22
   * 20

  Voir aussi [Développement de sites avec le pipeline front-end](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md#node-versions). <!-- CMGR-65307 -->

<!--
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


## Correctifs

* Correctif **(interface utilisateur) pour les mises à jour de la « Configuration réseau avancée » dans Cloud Manager**

  Un problème rare qui empêchait les mises à jour de la **Configuration réseau avancée** lorsqu&#39;une notification « Mise à jour disponible » était présente a été résolu. Auparavant, Cloud Manager verrouillait les modifications de configuration, y compris les paramètres de mise en réseau avancés, pour éviter les conflits lors d’une mise à jour. Les clients peuvent désormais déclencher manuellement la mise à jour en attente pour appliquer les modifications nécessaires sans restriction. <!-- CMGR-65913 and CMGR-65788 -->

* Correctif **(interface utilisateur) pour les mises à jour des listes autorisées IP bloquées à l’état « Mise à jour en cours »**

  Un rare problème en raison duquel les mises à jour des listes autorisées IP dans Cloud Manager étaient bloquées en mode « Mise à jour en cours » en raison de la configuration de domaines actifs en double pour un environnement a été résolu. Auparavant, les clients subissaient des retards de traitement indéfinis lors de la mise à jour des listes autorisées IP, empêchant les ajustements d’accès réseau nécessaires. Ce correctif permet de s’assurer que les mises à jour des listes autorisées IP peuvent désormais être effectuées sans être bloquées. <!-- CMGR-65786 -->




<!-- ## Known issues {#known-issues} -->
