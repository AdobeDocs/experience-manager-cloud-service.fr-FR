---
title: Notes de mise à jour de la version 2020.8.0 [!DNL Adobe Experience Manager] de Cloud Service.
description: '[ !DNL Adobe Experience Manager] en tant que notes de mise à jour Cloud Service pour la version 2020.8.0.'
translation-type: tm+mt
source-git-commit: fe2439e506f84a191922416e9c99b496fd90016c
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 9%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.8.0.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de la mise à jour 2020.8.0 de [!UICONTROL Cloud Manager] est le 06 août 2020.

### Nouveautés {#what-is-new-cloud-manager}

* L’audit de contenu est une fonctionnalité activée sur les pipelines de production de sites Cloud Manager. La configuration du pipeline de production pour les programmes avec sites comprend désormais un troisième onglet nommé Audit **du** contenu. Chaque fois qu&#39;un pipeline de production est exécuté, une nouvelle étape de contrôle du contenu est incluse dans le pipeline après des tests fonctionnels personnalisés qui évaluent le site par rapport à un certain nombre de dimensions, y compris les performances, l&#39;optimisation du référencement (optimisation pour les moteurs de recherche), l&#39;accessibilité, les meilleures pratiques et le PWA (application Web progressive).

   Refer to [Content Audit Testing](/help/implementing/developing/introduction/understand-test-results.md#content-audit-testing) for more details.

* Les nouveaux environnements créés dans les programmes Ressources seront désormais automatiquement configurés avec Smart Content Services.

* Les environnements en veille prolongée peuvent être désactivés à partir de la page d’aperçu de Cloud Manager.

* Les référentiels Maven privés liés à l’authentification sont désormais pris en charge.

### Correctifs {#bug-fixes-cm}

* Certains modules externes SonarQube inutiles et indésirables étaient exécutés dans le cadre de l’analyse de la qualité du code.

* Sur la page d&#39;exécution du pipeline, le nom de la branche n&#39;était pas correctement formaté.

* Dans certains cas, les exécutions de pipeline achevées n&#39;ont pas été enregistrées comme ayant été achevées, ce qui a empêché de nouvelles exécutions de pipeline.

* Les exécutions de pipelines se retrouveraient parfois &quot;bloquées&quot; en raison de problèmes de communication interne.

* Lors de la mise en service d’une nouvelle organisation, certains utilisateurs ayant des rôles d’administration autres que les administrateurs système ont reçu par erreur l’accès à Cloud Manager.

* Dans certaines conditions, la tâche de mise à jour des index a été lancée plusieurs fois en parallèle, ce qui a entraîné un échec du déploiement.

* L’info-bulle des cartes de programme n’était pas toujours correcte.

* L’interface utilisateur permettait par erreur de tenter une opération sur un environnement alors qu’elle était en cours de suppression.

* Il y avait une incohérence de couleur sur la page d&#39;aperçu.

### Problèmes connus {#known-issues}

* Les pages non valides sont incluses en plaçant la note moyenne d’audit du contenu en dessous de ce qu’elle devrait être.

* L’onglet Audit de contenu affiche incorrectement l’URL de base à l’aide du domaine d’auteur et non du domaine de publication.

* Pour activer l’étape de contrôle du contenu, les utilisateurs doivent modifier le pipeline et, éventuellement, ajouter des pages. Si aucune page n&#39;est ajoutée, la page d&#39;accueil fera l&#39;objet d&#39;un audit.

