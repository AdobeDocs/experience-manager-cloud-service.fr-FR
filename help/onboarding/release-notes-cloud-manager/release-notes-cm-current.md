---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.2.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.2.0
translation-type: tm+mt
source-git-commit: d20a729712c1dbd48150f813419b57c49074b492
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 19%

---


# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.2.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.2.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.2.0 est le 11 février 2021.

## Cloud Manager {#cloud-manager}

### Nouveautés {#what-is-new}

* Le pipeline de production de Cloud Manager inclut désormais la fonctionnalité de test d’interface utilisateur personnalisée.

* Les clients du module Ressources peuvent désormais choisir quand et où déployer leur instance de portail de marque en libre-service via l’interface utilisateur de Cloud Manager. Pour un programme standard (non sandbox) avec la solution Ressources, le portail de marque peut désormais être mis en service sur l’environnement de production. L’approvisionnement ne peut être effectué qu’une seule fois sur l’environnement Production.

* L&#39;archétype de projet AEM utilisé dans Project and Sandbox Creation a été mis à jour vers la version 25.

* La liste des API obsolètes identifiées lors de l’analyse du code a été affinée afin d’inclure d’autres classes et méthodes obsolètes dans les dernières versions du SDK Cloud Service.

* Profil SonarQube pour Cloud Manager mis à jour pour supprimer la règle Sonar squid:S2142. Ceci ne sera plus en conflit avec les contrôles Interruption du thread.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas temporairement ajouter/mettre à jour le nom de domaine car l’environnement associé dispose soit d’un pipeline en cours d’exécution qui lui est associé, soit de l’étape d’approbation en attente.

* Les propriétés définies dans les fichiers `pom.xml` client précédés du préfixe Sonar seront désormais supprimées dynamiquement afin d’éviter les échecs d’analyse de la génération et de la qualité.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas sélectionner de certificat SSL pour le moment s’il est utilisé par un nom de domaine en cours de déploiement.


### Correctifs {#bug-fixes}

* La correspondance d’un certificat SSL avec un nom de domaine n’est plus sensible à la casse.

* L’interface utilisateur de Cloud Manager informe désormais un utilisateur si les clés privées du certificat ne respectent pas la limite de 2 048 bits avec un message d’erreur approprié.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas sélectionner de certificat SSL pour le moment s’il est utilisé par un nom de domaine en cours de déploiement.

* Dans certains cas, un problème interne peut bloquer la suppression d’environnement.

* Certains échecs de pipeline étaient incorrectement signalés comme des erreurs de pipeline.
