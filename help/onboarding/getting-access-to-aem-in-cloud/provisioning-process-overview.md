---
title: Processus de configuration - Aperçu
description: Processus de configuration - Aperçu
source-git-commit: bb5a84c915e9b94bed021dacefd75b4e18fa9eb3
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 12%

---


# AEM en tant que Cloud Service : Intégration et accès

Cette page répertorie les ressources d’aide autonome sur le processus d’approvisionnement de Experience Manager en tant que Cloud Service.

## Présentation du processus d’attribution des privilèges d’accès AEM as a Cloud Service

Cette section répertorie les principaux articles sur les sujets suivants :

* Accès à AEM en tant que Cloud Service
* Processus d’intégration et de configuration d’Adobe Experience Manager as a Cloud Service
* Aide et ressources


### Accès à AEM en tant que Cloud Service

Une fois la mise en service automatique terminée :

* Droits d’accès accordés : Adobe crée une organisation dans Adobe Identity Management System (IMS).
* Par défaut, un administrateur désigné disposera des autorisations d’administrateur.
* L’administrateur peut ajouter des utilisateurs et des rôles pour d’autres membres de l’équipe via le Admin Console
* Vérification des autorisations basées sur les rôles pour les utilisateurs afin de déterminer les affectations d’autorisations dans Cloud Manager

> ![processsouveraineté.jpg](./assets/processOverview.jpg)


Pour plus d’informations, voir [Intégration à Experience Manager en tant que Cloud Service sur Experience League](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html?lang=en)

### Ressources et liens

• [Prise en charge IMS d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=fr)\
・ [Autorisations basées sur les rôles dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/role-based-permissions.html?lang=en#what-is-required)\
• [Accès à Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=en#getting-access)


## Processus d’intégration d’Adobe Experience Manager as a Cloud Service

### 1. Le bon de commande déclenche la mise en service automatique.

### 2. Organisations intégrées à Adobe Admin Console :

>   ![processsview2.jpg](./assets/processOverview2.jpg)
* Administrateur système :
   * Configuration des programmes et des environnements AEM.
   * Accédez à Admin Console pour les tâches administratives.
   * Demande à un domaine de confirmer la propriété du domaine respectif
   * Configuration des annuaires utilisateur.
   * Configuration IDP.
* Administrateur AEM:
   * Gérez les groupes locaux, les autorisations et les privilèges.

### 3. Utilisateurs intégrés et gérer l’accès dans Admin Console :

>   ![processsview3.jpg](./assets/processOverview3.jpg)

Trois méthodes d’intégration des utilisateurs, selon la taille et la préférence :
* Création manuelle d’utilisateurs dans Admin Console
* Téléchargement du fichier .csv
* Synchronisation des utilisateurs à partir d’Enterprise Principal
Répertoire

### 4. L’administrateur configure l’organisation et accorde aux utilisateurs et aux groupes l’accès aux environnements.

## Aide et ressources

* [Première connexion – Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/first-time-login.html#getting-access)
* [Configuration de l’accès à AEM en tant que Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=en#accessing)
