---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.2.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.2.0
exl-id: 281f9523-dec2-44f1-9459-5a45d48489d9
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.2.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.2.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.2.0 est le 11 février 2021.

## Cloud Manager {#cloud-manager}

### Nouveautés {#what-is-new}

* Les clients Assets peuvent désormais choisir quand et où déployer leur instance de Brand Portal en libre-service via l’interface utilisateur de Cloud Manager. Pour un programme standard (autre que l’environnement de test – Sandbox) avec la solution Assets, Brand Portal peut désormais être mis en service sur l’environnement de production. L’approvisionnement ne peut être effectué qu’une seule fois sur l’environnement de production.

* L’archétype de projet AEM utilisé dans la création de projet et de sandbox a été mis à jour à la version 25.

* La liste des API obsolètes identifiées lors de l’analyse du code a été affinée afin d’inclure d’autres classes et méthodes obsolètes dans les dernières versions du SDK Cloud Service.

* Le profil SonarQube pour Cloud Manager a été mis à jour pour supprimer la règle Sonar squid:S2142. Il n’y aura plus de conflit avec les contrôles d’interruption de thread.

* L’interface utilisateur de Cloud Manager informe un utilisateur qui ne pourrait pas temporairement ajouter/mettre à jour le nom de domaine, car l’environnement associé dispose soit d’un pipeline en cours d’exécution qui lui est associé, soit une étape d’approbation en attente.

* Les propriétés définies dans les fichiers `pom.xml` clients précédés d’un préfixe sonar seront désormais supprimées dynamiquement afin d’éviter les échecs d’analyse de la génération et de la qualité.

* L’interface utilisateur de Cloud Manager informe un utilisateur qui ne peut pas temporairement sélectionner un certificat SSL s’il est utilisé par un nom de domaine en cours de déploiement.

* Des règles de qualité de code supplémentaires ont été ajoutées pour résoudre les problèmes de compatibilité de Cloud Service.

### Correctifs  {#bug-fixes}

* La correspondance entre un certificat SSL et un nom de domaine n’est plus sensible à la casse.

* L’interface utilisateur de Cloud Manager informe désormais un utilisateur si les clés privées du certificat ne respectent pas la limite de 2 048 bits avec un message d’erreur approprié.

* L’interface utilisateur de Cloud Manager informe un utilisateur qui ne peut pas temporairement sélectionner un certificat SSL s’il est utilisé par un nom de domaine en cours de déploiement.

* Dans certains cas, un problème interne peut bloquer la suppression d’un environnement.

* Certains échecs de pipeline étaient incorrectement signalés comme des erreurs de pipeline.
