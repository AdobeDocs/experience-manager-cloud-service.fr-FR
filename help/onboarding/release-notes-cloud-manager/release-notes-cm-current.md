---
title: Notes de mise à jour de Cloud Manager en AEM version 2020.11.0 du Cloud Service
description: Notes de mise à jour de Cloud Manager en AEM version 2020.11.0 du Cloud Service
translation-type: tm+mt
source-git-commit: 727dfd1d16a80620fba6db00289021ee5efae0fc
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 36%

---


# Release Notes for Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.11.0 {#release-notes}

Cette page présente les Notes de mise à jour de Cloud Manager en AEM en tant que Cloud Service 2020.11.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager en tant que Cloud Service 2020.11.0 est le 12 novembre 2020.

## Cloud Manager {#cloud-manager}

### Nouveautés {#what-is-new}

* Une nouvelle option de menu Connexion **locale** est désormais disponible pour les utilisateurs à partir des options du menu environnement sur les pages Carte d&#39;Environnements et Résumé d&#39;Environnements.
Pour plus d’informations, consultez [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md##login-locally).

* The **Learn** tab in Cloud Manager has been refreshed with new images in the UI.

### Correctifs {#bug-fixes-cloud-manager}

* Le chargement des dépendances effectué avant l’exécution du build nécessitait le téléchargement d’un module externe Maven.
* Le lien du pied de page de Cloud Manager destiné à sélectionner une langue dirige désormais vers l’emplacement approprié.
* Parfois, pendant la numérisation du code, le processus SonarQube ne démarrait pas. Désormais, il sera automatiquement détecté et un redémarrage sera tenté.
* Tous les pipelines de production existants seront automatiquement activés avec l’étape Audit d’expérience.