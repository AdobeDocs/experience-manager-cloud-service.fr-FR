---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9d081b468e42306c56238bee6117d92c6afd48d4
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 25%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 23122 {#23122}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 23122, publiée le jeudi 29 octobre 2025. La version de maintenance précédente était la version 22943.

L’activation des fonctionnalités de la version 2025.11.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-23122}

* FORMS-21594 : permet d’activer le verrouillage du contenu et de la disposition du modèle de communications interactives pour les auteurs de contenu.
* FORMS-20385 : prise en charge de l’édition XDP dans l’éditeur de communications interactives.
* FORMS-10883 : prise en charge de JSON avec les balises d’espace de noms XHTML dans la génération du document d’enregistrement pour assurer le rendu précis des données de texte enrichi envoyées via les API.
* FORMS-21751 : fonctions de zone de travail - débordement de texte, interface utilisateur pour le saut de page.
* FORMS-22049 : éditeur de communications interactives - Migration vers le spectre 2.
* FORMS-22050 : prise en charge de la numérotation dynamique des pages dans l’éditeur de communications interactives.
* FORMS-21606 : SPI de rendu OSGi publiques pour les communications interactives.
* FORMS-21613 : rapport de transaction et journalisation des performances pour le rendu des SPI de communications interactives.
* SITES-35092 : fragments de contenu - Nouvelle procédure de mixin et de mise à niveau pour la recherche sémantique.
* SITES-32319 : OpenAPI de diffusion - Références de page de support.
* SITES-20123 : GraphQL : prend en charge les éléments d’exposant dans la réponse JSON.
* SITES-34744 : nouvelle propriété « card » dans la réponse de fragment de contenu, qui contient des données qui peuvent être utilisées pour le rendu d’une miniature.
* SITES-34571 : permet aux champs d’énumération d’être vides.
* SITES-34812 : possibilité supplémentaire de récupérer un fragment de contenu sans ses références, à l’aide du paramètre « references » avec la valeur « none ».
* SITES-35176 : l’extraction d’un fragment de contenu via l’interface utilisateur tactile empêche désormais la modification du fragment de contenu dans le nouvel éditeur par d’autres utilisateurs.
* SITES-30371 : ajout de la prise en charge des champs de référence basés sur l’uuid.
* SITES-19309 : récupérez un maximum de 150 références lors de l’ouverture de l’assistant de déplacement de page.
* SITES-32515 : Edge Delivery avec éditeur universel - Ajoutez la prise en charge de plusieurs champs et de plusieurs champs composites (accès anticipé).
* SITES-33784 : Edge Delivery avec éditeur universel - Ajoutez la prise en charge de ld-json dans les métadonnées de page.
* SITES-34832 : Edge Delivery avec éditeur universel - Ajoutez le chemin d’accès public d’une page à la réponse du servlet d’informations sur la page.
* SITES-25893 : Edge Delivery avec éditeur universel - Ajoutez la prise en charge de forts et de mettent l’accent sur le rendu de texte par blocs.
* SITES-26158 : Edge Delivery avec éditeur universel - Ajouter la prise en charge du balisage de tableau en blocs et en colonnes (accès anticipé).
* SITES-27949 : Edge Delivery avec éditeur universel - Rendez le mappage de chemin facultatif.

### Problèmes résolus {#fixed-issues-23122}

* CQ-4361144 : correction d’un problème en raison duquel les fragments de contenu étaient ignorés des tâches de traduction.
* CQ-4355446 : correction d’une chaîne non localisée dans le projet de traduction qui se produisait dans la boîte de dialogue Annuler la tâche de traduction .
* SITES-34555 : GraphQL - QueryValidationError après les déploiements.
* SITES-35077 : fragments de contenu - La dépublication échoue pour les fragments entre parenthèses en raison d’un codage d’URL incorrect.
* SITES-35374 : fragments de contenu - Le fragment de contenu modifié disparaît après avoir renavigué.
* SITES-36130 : NPE en `EditorRestrictionsStatusImpl`.
* SITES-35810 : NullPointerException dans Launches bloque la file d’attente publishEdgeDeliverySubscriber.
* SITES-34368 : AEM CIF génère 12 alias GraphQL - dépasse la limite de 10 dans la version 2.4.6-P12 de Magento.
* SITES-36193 : correctifs du connecteur CCS.
* SITES-35169 : résolution d’un problème qui entraînait une pagination incorrecte lorsque des ressources de fragment non valides étaient renvoyées par la recherche.
* SITES-34574 : correction d’un problème en raison duquel le curseur n’était pas renvoyé par l’API de recherche de fragments de contenu dans certains cas.
* SITES-35520 : correction d’un problème qui provoquait une ClassCastException ou des délais d’expiration lors de la tentative de publication de contenu.
* SITES-35210 : correction d’une exception NullPointerException qui se produisait lors de la tentative de publication d’un fragment rompu avec un filtre de références vide.
* SITES-35933 : correction d’un bug en raison duquel des workflows « Demande d’activation » vides étaient déclenchés après la publication du fragment de contenu.
* SITES-35925 : correction d’un bug lié à l’application de correctifs aux modèles de fragment de contenu qui supprimait les propriétés « traduisible » et « showThumbnail » du modèle.
* SITES-35409 : correction d’un bug qui empêchait la republication des fragments ajustés lors du déplacement d’une page.
* SITES-15757 : correction d’un bug qui empêchait la republication des pages modifiées lors du déplacement d’une page.
* SITES-34638 : correction d’un bug en raison duquel les propriétés des pages grands-parents n’étaient pas incluses lors de la création de nouvelles versions.
* SITES-35071 : l’exportation CSV renvoie des résultats non filtrés lorsque l’omni-recherche utilise une expression entre guillemets.
* SITES-32182 : Edge Delivery avec éditeur universel - correction des problèmes de codage avec les URL contenant des paramètres de requête déjà codés.
* SITES-34324 : Edge Delivery avec éditeur universel - correction du rendu des liens avec un tel : protocole.
* SITES-35333 : Edge Delivery avec éditeur universel - correction de la sélection du rendu de ressource pour les images dans les métadonnées de page.
* SITES-35549 : Edge Delivery avec éditeur universel - correction des entités html codées en double dans les métadonnées de page.

### Problèmes connus {#known-issues-23122}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-23122}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-23122}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 18 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-23122}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.86.0 | [API Oak 1.86.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.86/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.30.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
