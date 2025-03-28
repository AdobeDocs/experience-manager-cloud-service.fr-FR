---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 67b9a5f73f1f8c599e902a0ac0d8efbc614c7f75
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 32%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version X {#X}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance X, rendue publique le 1er avril 2025. La version de maintenance précédente était la version 19823.

L’activation des fonctionnalités de la version 2025.4.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-X}

FORMS-19068 : ajout de la prise en charge des actions d’envoi du connecteur AEP dans les API Forms Manager pour améliorer les fonctionnalités d’intégration des données de formulaire.

FORMS-18513 : prise en charge de la transformation de l’arbre de données implémentée dans le connecteur AEP pour améliorer les fonctionnalités de l’assistant et les fonctionnalités de gestion des données.

FORMS-18432 : implémentation d’une configuration de préremplissage côté client spécifique au formulaire (basée sur la regex) pour activer la fonctionnalité de préremplissage sélectif sans modifications au niveau OSGI.

FORMS-17551 : ajout de la prise en charge du document d’enregistrement pour les intégrations de listes SharePoint.

### Problèmes résolus {#fixed-issues-X}

FORMS-19028 : la fonctionnalité de préremplissage côté client interrompt la gestion des événements de formulaire, ce qui empêche le déclenchement correct des événements Validation de valeur et DOMContentLoaded au chargement du formulaire.

FORMS-18360 : amélioration de la gestion de la portée de la liste SharePoint pour les sites des équipes dans la gestion des documents Forms afin d’améliorer l’organisation des données et le contrôle d’accès.

FORMS-18325 : ajout de la configuration cloud de Adobe Experience Platform (AEP) pour améliorer l’intégration et les fonctionnalités de traitement des données de formulaire.

FORMS-18213 : fonctionnalité implémentée pour masquer/exclure les champs désactivés du document d’enregistrement (DE) afin d’améliorer la clarté du document et l’expérience utilisateur.

FORMS-18189 : modification de la gestion des fonctions personnalisées pour empêcher la journalisation des erreurs pour les bibliothèques clientes vides et améliorer l’affichage des erreurs dans l’interface utilisateur.

FORMS-18426 : la fonctionnalité de recherche de liste SharePoint échoue lorsque les noms de liste contiennent des caractères spéciaux (par exemple, « - »), ce qui affecte l’intégration des formulaires aux listes SharePoint.

FORMS-18375 : les formulaires basés sur les composants de base sélectionnent incorrectement les configurations Recaptcha `conf/global` dossier lorsqu’aucun conteneur de configuration spécifique n’est sélectionné.

FORMS-18304 : les documents PDF/A-1b qui réussissent la validation dans Acrobat et LiveCycle ES4 sont incorrectement marqués comme non conformes dans AEM 6.5 Forms en raison d’erreurs de couleur dépendantes de l’appareil.

FORMS-18271 : l’éditeur de thèmes Forms affiche des messages d’erreur non localisés, ce qui affecte l’expérience utilisateur dans la configuration des formulaires et la personnalisation des thèmes.

FORMS-18068 : problèmes de rendu de texte en gras dans le document d’enregistrement pour les groupes de boutons radio et de cases à cocher utilisant des champs de texte enrichi.

FORMS-7016 : l’ordre de focus au clavier dans l’éditeur de formulaire ne suit pas la navigation logique.

FORMS-6950 : ajout des rôles et attributs ARIA requis aux composants d’aperçu de l’arborescence du navigateur du système de fichiers pour améliorer l’accessibilité du lecteur d’écran et se conformer à la norme WCAG 4.1.2 Nom, rôle, valeur (niveau A).

### Problèmes connus {#known-issues-X}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-X}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-X}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige X vulnérabilités identifiées, renforçant ainsi notre engagement en faveur d’une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-X}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.76.0 | [API Oak 1.76.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
