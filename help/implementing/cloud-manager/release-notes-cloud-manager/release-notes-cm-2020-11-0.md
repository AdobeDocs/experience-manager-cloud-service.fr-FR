---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2020.11.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2020.11.0
feature: Release Information
exl-id: e2acf515-d339-4d2b-9b62-09c1dab1ffac
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2020.11.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2020.11.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2020.11.0 est le 12 novembre 2020.

## Cloud Manager {#cloud-manager}

### Nouveautés {#what-is-new}

* Une nouvelle option de menu **Connexion locale** est désormais disponible pour les utilisateurs à partir des options du menu environnement dans la carte Environnement et les pages de résumé des environnements.
Pour plus d’informations, consultez [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md#login-locally).

* L’onglet **Apprendre** de Cloud Manager est actualisé avec de nouvelles images dans l’interface utilisateur.

### Correctifs {#bug-fixes-cloud-manager}

* Le chargement des dépendances effectué avant l’exécution du build nécessitait le téléchargement d’un module externe Maven.
* Le lien du pied de page de Cloud Manager destiné à sélectionner une langue dirige désormais vers l’emplacement approprié.
* Parfois, pendant la numérisation du code, le processus SonarQube ne démarrait pas. Désormais, il sera automatiquement détecté et un redémarrage sera tenté.
* Tous les pipelines de production existants seront automatiquement activés avec l’étape Contrôle de l’expérience.
