---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.2.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.2.0
exl-id: 281f9523-dec2-44f1-9459-5a45d48489d9
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 19%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.2.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.2.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.2.0 est le 11 février 2021.

## Cloud Manager {#cloud-manager}

### Nouveautés {#what-is-new}

* Les clients Assets pourront désormais choisir quand et où déployer leur instance Brand Portal en libre-service via l’interface utilisateur de Cloud Manager. Pour un programme ordinaire (autre qu’un environnement de test) avec la solution Assets, Brand Portal peut désormais être configuré dans l’environnement de production. La mise en service ne peut être effectuée qu’une seule fois dans l’environnement de production.

* L’archétype de projet AEM utilisé dans Project et Sandbox Creation a été mis à jour vers la version 25.

* La liste des API obsolètes identifiées lors de l’analyse du code a été affinée afin d’inclure d’autres classes et méthodes obsolètes dans les dernières versions du SDK Cloud Service.

* Profil SonarQube pour Cloud Manager mis à jour afin de supprimer la règle Sonar squid:S2142. Cela n’entre plus en conflit avec les contrôles d’interruption de threads.

* L’interface utilisateur de Cloud Manager informera l’utilisateur qui ne pourra pas ajouter/mettre à jour temporairement le nom de domaine, car l’environnement associé est associé à un pipeline en cours d’exécution ou est actuellement en attente de l’étape d’approbation.

* Les propriétés définies dans les fichiers `pom.xml` clients avec le préfixe sonar seront désormais supprimées dynamiquement afin d’éviter les échecs d’analyse de génération et de qualité.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas sélectionner de certificat SSL pour le moment s’il est utilisé par un nom de domaine en cours de déploiement.

* Des règles de qualité du code supplémentaires ont été ajoutées pour couvrir les problèmes de compatibilité du Cloud Service.

### Correctifs {#bug-fixes}

* La correspondance d’un certificat SSL avec un nom de domaine n’est plus sensible à la casse.

* L’interface utilisateur de Cloud Manager informe désormais un utilisateur si le certificat de clés privées ne respecte pas la limite de 2 048 bits avec un message d’erreur approprié.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas sélectionner de certificat SSL pour le moment s’il est utilisé par un nom de domaine en cours de déploiement.

* Dans certains cas, un problème interne peut entraîner le blocage de la suppression de l’environnement.

* Certains échecs de pipeline étaient incorrectement signalés comme des erreurs de pipeline.
