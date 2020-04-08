---
title: Notes de mise à jour de la version 2020.3.0
description: Notes de mise à jour de la version 2020.3.0
translation-type: tm+mt
source-git-commit: 27225bf4b918f39892ac9ab6f46deb97479f08e8

---


# Notes de mise à jour d’AEM as a Cloud Service 2020.3.0 {#release-notes}

La section suivante décrit les Notes de mise à jour générales d’Experience Manager en tant que service Cloud 2020.3.0.


## Date de publication {#release-date}

La date de publication pour Experience Manager en tant que service Cloud 2020.3.0 est le 05 mars 2020.

## Cloud Manager {#cloud-manager}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager dans AEM as a Cloud Service Release 2020.3.0.

### Nouveautés {#what-is-new}

* Le journal de l’étape de création est désormais disponible pendant l’exécution de l’étape.
* Certains messages de la page des détails d’exécution de pipeline ont été modifiés pour plus de clarté.

### Correctifs  {#bug-fixes}

* Les fichiers journaux des étapes de test personnalisé et fonctionnel du produit n’ont pas pu être téléchargés via l’interface utilisateur.
* Lorsque le référentiel git d’un de service Cloud n’a pas  être créé, les utilisateurs du rôle Deployment Manager n’ont parfois pas pu récupérer de cet échec.
* Certains utilisateurs   lors de la création d’un de sandbox peuvent entraîner l’échec de la création de l’avant la création du canal de non-production.
* Le démarrage de l’instance éphémère SonarQube utilisée lors de l’étape de création échouait parfois au cours du délai d’expiration configuré.
* La création simultanée d’un de développement   dans le même de service Cloud peut rencontrer une condition dans laquelle seul un utilisateur a pu être créé avec succès.
* Les notifications Experience Cloud pour les du service Cloud n’ont pas été reçues de manière cohérente.
* Dans le cas de projets spécifiques, la règle *Les objets ResourceResolver doivent toujours être fermés* entraînait une exception de pointeur nul ; cela n’avait toutefois pas d’incidence sur l’exécution du pipeline.

