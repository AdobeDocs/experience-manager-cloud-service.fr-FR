---
title: Notes de mise à jour de la version 2020.3.0
description: Notes de mise à jour de la version 2020.3.0
translation-type: tm+mt
source-git-commit: bcbb50f467a0e3b3047e2bb872a8fe39a9f02a1a

---


# Notes de mise à jour d’AEM as a Cloud Service 2020.3.0 {#release-notes}

La section suivante décrit les Notes de mise à jour générales d’Experience Manager en tant que service Cloud 2020.3.0.

## Cloud Manager {#cloud-manager}

La date de publication de la version 2020.3.0 de Cloud Manager est le 05 mars 2020.

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager version 2020.3.0.

### Nouveautés {#what-is-new}

* Le journal de l’étape de création est désormais disponible pendant l’exécution de l’étape de création.
* Certains messages de la page des détails de l&#39;exécution du pipeline ont été modifiés pour plus de clarté.

### Correctifs  {#bug-fixes}

* Les fichiers journaux des étapes de test personnalisé et fonctionnel du produit n’ont pas pu être téléchargés via l’interface utilisateur.
* Lorsque le référentiel git pour un programme de service Cloud n’a pas pu être créé, les utilisateurs du rôle Deployment Manager n’ont parfois pas pu récupérer de cet échec.
* Certaines activités des utilisateurs pendant la création d&#39;un programme sandbox peuvent entraîner l&#39;échec de la création du programme avant la création du pipeline de non-production.
* L’instance éphémère SonarQube utilisée dans l’étape de création échouait parfois à démarrer dans le délai d’attente configuré.
* La création simultanée d’environnements de développement dans le même programme de service Cloud peut rencontrer une condition dans laquelle seul un environnement a pu être créé avec succès.
* Les notifications Experience Cloud pour les programmes de service Cloud n’ont pas été reçues de manière cohérente.
* Dans le cas de projets spécifiques, les objets *ResourceResolver doivent toujours être fermés* pour générer une exception de pointeur nul ; cela n&#39; a toutefois pas eu d&#39; incidence sur l&#39; exécution du pipeline.

