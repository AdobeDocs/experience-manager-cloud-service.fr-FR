---
title: Notes de mise à jour de Cloud Manager en AEM version 2020.8.0 du Cloud Service
description: Notes de mise à jour de Cloud Manager en AEM version 2020.8.0 du Cloud Service
translation-type: tm+mt
source-git-commit: ca690144a8254d5ffba354f0f96d9ef1c5202533
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 18%

---


# Release Notes for Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.8.0 {#release-notes}

Cette page présente les Notes de mise à jour de Cloud Manager en AEM en tant que Cloud Service 2020.8.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager en tant que Cloud Service 2020.8.0 est le 6 août 2020.

## Nouveautés {#whats-new-cloud-manager}

* L’audit de contenu est une fonctionnalité activée sur les pipelines de production de sites Cloud Manager. La configuration du pipeline de production pour les programmes avec sites comprend désormais un troisième onglet nommé Audit **du** contenu. Chaque fois qu&#39;un pipeline de production est exécuté, une nouvelle étape de contrôle du contenu est incluse dans le pipeline après des tests fonctionnels personnalisés qui évaluent le site par rapport à un certain nombre de dimensions, y compris les performances, l&#39;optimisation du référencement (optimisation pour les moteurs de recherche), l&#39;accessibilité, les meilleures pratiques et le PWA (application Web progressive).


   >[!NOTE]
   >L’audit de contenu a depuis été renommé Audit d’expérience.

   Refer to [Experience Audit Testing](/help/implementing/cloud-manager/experience-audit-testing.md) for more details.

* Les nouveaux environnements créés dans les programmes Ressources seront désormais automatiquement configurés avec Smart Content Services.

* Les environnements en veille prolongée peuvent être désactivés à partir de la page **Présentation** de Cloud Manager.

* Possibilité d’effectuer des vérifications d’expérience sur les pages, optimisées par Google Lighthouse. Dans le cadre du pipeline de Cloud Manager, jusqu’à 25 pages peuvent être vérifiées et validées par rapport aux IPC d’expérience et les scores s’affichent dans l’interface utilisateur de Cloud Manager.

### Correctifs {#bug-fixes-cm}

* Certains plug-ins SonarQube inutiles et indésirables étaient exécutés dans le cadre de l’analyse de la qualité du code.

* Sur la page d’exécution du pipeline, le nom de la branche n’était pas correctement formaté.

* Dans certains cas, les exécutions de pipeline achevées n’étaient pas été enregistrées comme ayant été achevées, ce qui empêchait de nouvelles exécutions de pipeline.

* Les exécutions de pipelines étaient parfois *bloquées* en raison de problèmes de communication interne.

* Lors de la mise en service d’une nouvelle organisation, certains utilisateurs ayant des rôles d’administration autres que les administrateurs système ont reçu par erreur l’accès à Cloud Manager.

* Dans certaines conditions, la tâche de mise à jour des index a été lancée plusieurs fois en parallèle, ce qui a entraîné un échec du déploiement.

* Les info-bulles des cartes de programme n’étaient pas toujours correctes.

* L’interface utilisateur permettait par erreur de tenter une opération sur un environnement alors qu’elle était en cours de suppression.

* There was a color mismatch on the Cloud Manager&#39;s **Overview** page.

### Problèmes connus {#known-issues-cm}

* Les pages non valides sont incluses en plaçant la note moyenne d’audit du contenu en dessous de ce qu’elle devrait être.

* L’onglet Audit de contenu affiche incorrectement l’URL de base à l’aide du domaine d’auteur et non du domaine de publication.

* Pour activer l’étape de contrôle du contenu, les utilisateurs doivent modifier le pipeline et, éventuellement, ajouter des pages. Si aucune page n&#39;est ajoutée, la page d&#39;accueil fera l&#39;objet d&#39;un audit.