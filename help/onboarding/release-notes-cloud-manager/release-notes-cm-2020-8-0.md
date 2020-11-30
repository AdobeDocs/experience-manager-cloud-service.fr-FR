---
title: Notes de mise à jour de Cloud Manager en AEM version 2020.8.0 du Cloud Service
description: Notes de mise à jour de Cloud Manager en AEM version 2020.8.0 du Cloud Service
translation-type: tm+mt
source-git-commit: ca690144a8254d5ffba354f0f96d9ef1c5202533
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 84%

---


# Release Notes for Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.8.0 {#release-notes}

Cette page présente les Notes de mise à jour de Cloud Manager en AEM en tant que Cloud Service 2020.8.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager en tant que Cloud Service 2020.8.0 est le 6 août 2020.

## Nouveautés {#whats-new-cloud-manager}

* L’audit de contenu est une fonctionnalité activée sur les pipelines de production de sites Cloud Manager. La configuration du pipeline de production pour les programmes utilisant Sites comprend désormais un troisième onglet nommé **Audit de contenu**. Chaque fois qu’un pipeline de production est exécuté, une nouvelle étape de contrôle du contenu est incluse dans le pipeline suite à des tests fonctionnels personnalisés qui évaluent le site par rapport à un certain nombre de dimensions, notamment les performances, l’optimisation du référencement (SEO), l’accessibilité, les bonnes pratiques et les applications web progressives (PWA).


   >[!NOTE]
   >L’audit de contenu a depuis été renommé audit d’expérience.

   Pour plus d’informations, voir [Tests d’audit d’expérience](/help/implementing/cloud-manager/experience-audit-testing.md).

* Les nouveaux environnements créés dans les programmes Assets seront désormais automatiquement configurés avec le service de contenu dynamique.

* Il est possible de désactiver les environnements placés en veille prolongée à l’aide de la page **Aperçu** de Cloud Manager.

* Possibilité d’effectuer des vérifications d’expérience sur les pages, optimisées par Google Lighthouse. Dans le cadre du pipeline de Cloud Manager, il est possible de vérifier et valider jusqu’à 25 pages concernant les indicateurs de performances clés d’expérience et les scores s’affichent dans l’interface utilisateur de Cloud Manager.

### Correctifs {#bug-fixes-cm}

* Certains plug-ins SonarQube inutiles et indésirables étaient exécutés dans le cadre de l’analyse de la qualité du code.

* Sur la page d’exécution du pipeline, le nom de la branche n’était pas correctement formaté.

* Dans certains cas, les exécutions de pipeline achevées n’étaient pas été enregistrées comme ayant été achevées, ce qui empêchait de nouvelles exécutions de pipeline.

* Les exécutions de pipelines étaient parfois *bloquées* en raison de problèmes de communication interne.

* Lors de la mise en service d’une nouvelle organisation, certains utilisateurs exerçant des rôles d’administration autres que ceux des administrateurs système recevaient par erreur l’accès à Cloud Manager.

* Dans certaines conditions, le traitement de mise à jour des index était lancé plusieurs fois en parallèle, ce qui entraînait l’échec du déploiement.

* Les info-bulles des cartes de programme n’étaient pas toujours correctes.

* L’interface utilisateur permettait par erreur de tenter une opération sur un environnement alors qu’elle était en cours de suppression.

* Les couleurs n’étaient pas cohérentes sur la page **Aperçu** de Cloud Manager.

### Problèmes connus {#known-issues-cm}

* Les pages non valides sont incluses, ce qui amène la note moyenne d’audit de contenu au-dessous de ce qu’elle devrait être.

* L’onglet Audit du contenu affiche incorrectement l’URL de base en utilisant le domaine d’auteur au lieu du domaine de publication.

* Pour activer l’étape de contrôle du contenu, les utilisateurs doivent modifier le pipeline et éventuellement ajouter des pages. Si aucune page n’est ajoutée, la page d’accueil fera l’objet d’un audit.