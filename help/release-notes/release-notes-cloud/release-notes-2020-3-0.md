---
title: Notes de mise à jour de la version 2020.3.0
description: Notes de mise à jour de la version 2020.3.0
translation-type: tm+mt
source-git-commit: 3dc0d1d77595f7b3e890fb4b390eef5bcf84ecd8
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 100%

---


# Notes de mise à jour d’AEM as a Cloud Service 2020.3.0 {#release-notes}

Cette page décrit les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.3.0.

## Date de publication {#release-date}

La date de publication d’Experience Manager as a Cloud Service 2020.3.0 est le 5 mars 2020.

## Cloud Manager {#cloud-manager}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager dans AEM as a Cloud Service 2020.3.0.

### Nouveautés {#what-is-new}

* Le journal de l’étape de création est désormais disponible pendant l’exécution de l’étape.
* Certains messages de la page des détails d’exécution de pipeline ont été modifiés pour plus de clarté.

### Correctifs  {#bug-fixes}

* Les fichiers journaux des étapes de test fonctionnel personnalisé et de produit ne pouvaient pas être téléchargés via l’interface utilisateur.
* Lorsque la création du référentiel git d’un programme Cloud Service échouait, les utilisateurs ayant le rôle Gestionnaire de déploiement ne pouvaient parfois pas récupérer de cet échec.
* Certaines activités d’utilisateur lors de la création d’un programme sandbox pouvaient entraîner l’échec de la création du programme avant la création du pipeline hors production.
* Le démarrage de l’instance éphémère SonarQube utilisée lors de l’étape de création échouait parfois au cours du délai d’expiration configuré.
* La création simultanée d’environnements de développement dans le même programme Cloud Service pouvait rencontrer une condition dans laquelle un seul environnement avait pu être créé.
* Les notifications Experience Cloud pour les programmes Cloud Service n’ont pas été systématiquement reçues.
* Dans le cas de projets spécifiques, la règle *Les objets ResourceResolver doivent toujours être fermés* entraînait une exception de pointeur nul ; cela n’avait toutefois pas d’incidence sur l’exécution du pipeline.

