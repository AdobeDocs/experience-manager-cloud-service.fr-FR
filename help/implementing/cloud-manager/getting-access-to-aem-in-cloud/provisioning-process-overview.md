---
title: Processus de configuration - Présentation
description: Processus de configuration - Présentation
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: ht
source-wordcount: '330'
ht-degree: 100%

---


# AEM as a Cloud Service : intégration et accès

Cette page répertorie les ressources d’aide autonome pour le processus d’approvisionnement Experience Manager as a Cloud Service.

## Aperçu du processus d’approvisionnement d’AEM as a Cloud Service

Cette section répertorie les principaux articles sur les sujets suivants :

* l’accès à AEM as a Cloud Service ;
* le processus d’intégration et d’approvisionnement d’Adobe Experience Manager as a Cloud Service ;
* l’aide et les ressources.


### Accès à AEM as a Cloud Service

Une fois l’approvisionnement automatique terminé :

* Droits d’accès accordés : Adobe créera une organisation au sein du système Identity Management Adobe (IMS)
* Par défaut, l’administrateur désigné disposera des autorisations d’administrateur.
* L’administrateur peut ajouter des utilisateurs et des rôles pour d’autres membres de l’équipe par l’intermédiaire de l’Admin Console.
* Examinez les autorisations basées sur les rôles pour les utilisateurs afin de déterminer les affectations d’autorisations dans Cloud Manager.

![processoverview.jpg](assets/processOverview.jpg)


Pour plus d’informations, consultez [Intégration d’Experience Manager as a Cloud Service dans Experience League](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html?lang=fr).

### Ressources et liens

* [Prise en charge IMS d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=fr)
* [Autorisations basées sur les rôles dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/role-based-permissions.html?lang=fr#what-is-required)
* [Accès à Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=fr#getting-access)


## Intégration d’Adobe Experience Manager as a Cloud Service

### 1. Le bon de commande déclenche l’approvisionnement automatique.

### 2. Intégration des organisations dans l’Adobe Admin Console :

![processoverview2.jpg](assets/processOverview2.jpg)

* Administrateur système :
   * Fournissez les programmes et environnements AEM.
   * Accédez à l’Admin Console pour les tâches d’administration.
   * Demandez un domaine pour confirmer la propriété de chaque domaine.
   * Configurez les répertoires utilisateur.
   * Configurez l’IDP.
* Administrateur AEM :
   * Gérez les groupes locaux, les autorisations et les privilèges.

### 3. Intégration d’utilisateurs et gestion des accès dans l’Admin Console :

![processoverview3.jpg](assets/processOverview3.jpg)

Trois méthodes pour intégrer les utilisateurs, en fonction de la taille et des préférences :
* Création manuelle d’utilisateurs dans l’Admin Console
* Chargez le fichier .csv
* Synchronisez les utilisateurs à partir de l’Active Directory
de l’enterprise

### 4. L’administrateur configure l’organisation et accorde aux utilisateurs et aux groupes l’accès aux environnements

## l’aide et les ressources.

* [Première connexion – Cloud Service](/help/journey-onboarding/sysadmin/learning-path-aem-users.md)
* [Configuration de l’accès à AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=fr#accessing)
