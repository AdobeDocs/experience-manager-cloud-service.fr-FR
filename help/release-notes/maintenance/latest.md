---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 77d8ebeaa3914f4a91d2cf27ccc5b048e64d6b38
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 22%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 19352 {#19352}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 19352, rendue publique le jeudi 5 février 2025. La version de maintenance précédente était la version 19149.

L’activation des fonctionnalités de la version 2025.2.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-19352}

* FORMS-13998 : ajout d’un composant d’accordéon.
* FORMS-17913 : ajout d’une variante de cartes pour le groupe de cases d’option.
* FORMS-17333 : activation des modèles d’e-mail HTML dans l’envoi de formulaire AEM.
* FORMS-17702 : activez les PDF générés dans les API de synchronisation de sortie à charger dans le stockage Blob Azure.
* SITES-28282 : Edge Delivery avec éditeur universel : indiquez le chemin d’accès de base, le nom du site et l’organisation en tant qu’informations de page pour n’importe quelle page.
* SITES-27055 : Edge Delivery avec éditeur universel : prend en charge les paramètres de requête dans le servlet de proxy inverse.
* SITES-26796 : Edge Delivery avec éditeur universel : prend en charge les colonnes personnalisées pour la feuille de calcul Taxonomie .
* SITES-26087 : Edge Delivery avec éditeur universel : prend en charge l’exportation au format CSV pour les feuilles de calcul.
* SITES-26265 : Edge Delivery avec éditeur universel : affichez le compte TA à intégrer à Edge Delivery dans l’interface utilisateur de configuration.
* SITES-20372 : Edge Delivery avec éditeur universel : activez les cas d’utilisation de base de MSM pour les feuilles de calcul.
* SITES-26681 : Edge Delivery avec éditeur universel : prend en charge le paramètre ?sheet= pour les feuilles de calcul de taxonomie de l’auteur.
* SITES-26479 : point d’entrée du statut de publication planifiée du modèle [schéma] de fragment de contenu.
* SITES-25944 : [Présentation de Livecopy] ajoutez le statut « Live Copy à jour avec un héritage limité ».
* SITES-28713 : [V2] ajoutez la prise en charge des données structurées au scraper de contenu.
* SITES-27896 : ouverture automatique de CommentsTab sur la notification.
* SITES-26720 : l’utilisateur ne doit pas être autorisé à sélectionner une collection entière à partir du sélecteur de ressources.
* SITES-27875 : permet de modifier n’importe quel élément d’un conteneur pouvant être déplacé par défaut.
* SITES-28340 : plug-in du service d’éditeur universel Dark Alley.
* SITES-26098 : possibilité d’éviter de publier des pages référencées lors de la publication d’un fragment de contenu.
* SITES-27789 : prise en charge du composant data-aue-component d’attributs de données dans le DOM.
* SITES-25997 : améliorez les variations pour prendre en charge la date de modification.
* SITES-28023 : sortie GraphQL pour les références de ressources distantes (référentiel + ID de ressource).
* SITES-26058 : point d’entrée du statut de publication planifiée du modèle de fragment de contenu.
* SITES-25108 : migration de modèles pour les références UUID.
* SITES-26630 : point d’entrée du statut de publication planifiée de fragments de contenu pour plusieurs fragments de contenu.
* SITES-23432 : amélioration de la fonctionnalité de suppression des références.
* SITES-25797 : prise en charge des références de ressources externes - GraphQL.
* SITES-17514 : amélioration de la suppression du point d’entrée pour dépublier le fragment de contenu.
* SITES-14633 : validation du modèle de fragment de contenu pour créer des payloads avant l’installation - Exécution d’essai.

### Problèmes résolus {#fixed-issues-19352}

* SITES-28415 : Edge Delivery avec éditeur universel : correction du bouton Ouvrir les propriétés des feuilles de calcul.
* SITES-26669 : Edge Delivery avec éditeur universel : correction de problèmes lors du chargement de fichiers CSV codés en UTF-8 avec une nomenclature comme feuille de calcul.
* SITES-26543 : Edge Delivery avec l’éditeur universel : correction des blocs vides sans qu’un modèle ne génère de balisage incorrect.
* SITES-26857 : Edge Delivery avec éditeur universel : corrigez le jeton d’authentification du site visible dans l’interface utilisateur pour les configurations basées sur des fichiers.
* SITES-26662 : Edge Delivery avec l’éditeur universel : correction des problèmes liés aux métadonnées en bloc sensibles à la casse.
* SITES-28133 : Publish en « aperçu » rend le contenu disponible en production.
* SITES-27187 : l’activation de pages/ressources planifiée, y compris les références (expérimentale), ne parvient pas à publier les références.
* SITES-27264 : 2 Les tests Selenium liés à la création de fragments de contenu en direct à la création échouent de manière cohérente sur le maître.
* SITES-26559 : épinglez la requête pour les modèles de fragment de contenu à l’index cqPageLucene.
* SITES-24469 : l’élément interactif n’est pas accessible à partir du clavier.
* SITES-24518 : les boutons Nom et Modèle de la table Référence parente ne sont pas accessibles à l’aide du clavier.
* SITES-27937 : les contraintes UISchema sont définies sur null après la mise à jour du modèle.
* SITES-27852 : catégories manquantes dans le modèle UISchema.
* SITES-27904 : MetadataSchema manquant dans la liste/la recherche Modèles de fragment de contenu pour la projection complète.
* SITES-26827 : la liste des fragments se termine en boucle infinie.
* SITES-27678 : [Performance] empêcher la récupération inutile de _références.
* SITES-27589 : échec de la mise à niveau de l’UUID pour les modèles de fragment de contenu avec plusieurs champs de référence de contenu/fragment.
* SITES-26679 : dépublier les fragments de contenu Les modèles ne doivent valider que les références publiées.
* SITES-26666 : referencesTree et le point d’entrée des références renvoyant des résultats différents.
* SITES-26499 : ordre incorrect de la valeur du champ de balise dans le ou les fragments de GET et le PATCH rend l’ordre aléatoire.
* SITES-26585 : correction d’une petite erreur de description dans le schéma.
* SITES-26647 : la validation de référence Supprimer le point d’entrée et Dépublier les fragments peut échouer pour les utilisateurs non-administrateurs.
* SITES-26458 : [Rechercher un modèle de fragment de contenu] Corriger le filtrage par statut de réplication.
* SITES-23513 : échec de la validation de l’[ Éditeur de modèles de fragments de contenu ] pour la propriété « Référence de fragment » - « Modèle de fragment de contenu autorisé ».
* SITES-26575 : la dépublication d’un fragment à partir de l’aperçu doit mettre à jour previewStatus.
* SITES-26571 : impossible d’enregistrer les références de page lorsque FT_SITES-12435 est activé.
* SITES-26660 : la comparaison des versions de fragments de contenu peut être rompue lorsque @ContentType est de type « chaîne ».
* SITES-26626 : customErrorMessage manquant sur les champs numériques et booléens.
* SITES-26268 : code d’état incorrect renvoyé si une référence n’est pas valide lors de la création d’un fragment.

### Problèmes connus {#known-issues-19352}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-19352}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-19352}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 36 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-19352}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.72.0 | [API Oak 1.72.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
