---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2020.3.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2020.3.0
feature: Release Information
exl-id: 2ff62ba5-a657-4739-b646-1e948332bf79
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2020.3.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2020.3.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2020.3.0 est le 5 mars 2020.

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
