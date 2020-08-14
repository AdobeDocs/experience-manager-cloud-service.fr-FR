---
title: Notes de mise à jour de la version 2020.8.0 [!DNL Adobe Experience Manager] de Cloud Service.
description: '[ !DNL Adobe Experience Manager] en tant que notes de mise à jour Cloud Service pour la version 2020.8.0.'
translation-type: tm+mt
source-git-commit: bb5bf9527da7ed9039740ef6d0bab27cfd21b84e
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 23%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.8.0.

## [!DNL Adobe Experience Manager Assets]as a Cloud Service{#assets}

* Les nouveaux [!DNL Experience Manager Assets] déploiements sont intégrés [!DNL Adobe Developer Console] par défaut. Il permet de configurer plus rapidement la fonctionnalité des balises actives. Dans les déploiements existants, les administrateurs [configurent l’intégration](/help/assets/smart-tags-configuration.md#aio-integration) des balises actives comme auparavant.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* La fonction Console produit est désormais disponible. Cela permet aux spécialistes du marketing/auteurs d’AEM de vue et de parcourir les catégories et les produits stockés dans l’arrière-plan du commerce. La prise en charge des propriétés des catégories et des produits dans la Console produit est également fournie.

* Les sélecteur de produits et de Catégories ont été améliorés pour permettre aux spécialistes du marketing de sélectionner un produit via le SKU ou de sélectionner une catégorie via l’ID de catégorie.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de la mise à jour 2020.8.0 de [!UICONTROL Cloud Manager] est le 06 août 2020.

### Nouveautés {#what-is-new-cloud-manager}

* L’audit de contenu est une fonctionnalité activée sur les pipelines de production de sites Cloud Manager. La configuration du pipeline de production pour les programmes avec sites comprend désormais un troisième onglet nommé Audit **du** contenu. Chaque fois qu&#39;un pipeline de production est exécuté, une nouvelle étape de contrôle du contenu est incluse dans le pipeline après des tests fonctionnels personnalisés qui évaluent le site par rapport à un certain nombre de dimensions, y compris les performances, l&#39;optimisation du référencement (optimisation pour les moteurs de recherche), l&#39;accessibilité, les meilleures pratiques et le PWA (application Web progressive).

   Refer to [Content Audit Testing](/help/implementing/developing/introduction/understand-test-results.md#content-audit-testing) for more details.

* Les nouveaux environnements créés dans les programmes Ressources seront désormais automatiquement configurés avec Smart Content Services.

* Les environnements en veille prolongée peuvent être désactivés à partir de la page **Présentation** de Cloud Manager.

* Les référentiels Maven privés liés à l’authentification sont désormais pris en charge.

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

## Outil de transfert de contenu {#content-transfer-tool}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de la version 1.0.4 de l’outil de transfert de contenu.

### Nouveautés {#what-is-new-ctt}

* L’outil de transfert de contenu prend désormais en charge le magasin de données partagé S3.

### Correctifs {#ctt-bug-fixes}

* Ajout de délais d’attente supplémentaires pour que l’outil exécute les actions.

* L’interface utilisateur des versions antérieures présentait parfois une extraction réussie, même si le journal présentait des erreurs.

