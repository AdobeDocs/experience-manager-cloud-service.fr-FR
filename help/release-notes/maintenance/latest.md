---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: d73ccc454c89c7e06752de694af97ac26694be17
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 24%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 22450 {#22450}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 22450, publiée le mercredi 16 septembre 2025. La version de maintenance précédente était la version 22171.

L’activation des fonctionnalités de la version 2025.9.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Consultez [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Nouvelles fonctionnalités {#new-features-22450}

* SITES-32595 : les workflows qui se terminent par des fragments ignorés ou rejetés peuvent désormais être identifiés. Une nouvelle propriété est disponible dans la réponse de l’API de workflow, répertoriant les fragments qui ont été exclus en raison de leur non-validité ou de leurs références non valides.
* SITES-33642 : un nouvel événement d’API est désormais produit et utilisé pour les fragments de contenu modifiés.
* SITES-33320 : il est désormais possible de rechercher un modèle de fragment de contenu à l’aide de son `technicalName` via l’API de recherche.

### Améliorations {#enhancements-22450}

* SITES-34023 : le champ `technicalName` a été ajouté aux réponses des points d’entrée du modèle de fragment de contenu pour une meilleure identification.
* SITES-32766 : les références de ressources de contenu dans les modèles de fragment de contenu prennent désormais en charge un large éventail de types de fichiers binaires.
* SITES-33974 : amélioration de la documentation OpenAPI pour la rendre plus précise et plus conviviale.
* SITES-9173 : `ContentPolicyStatus` du cache.
* SITES-9290 : amélioration de la mise en cache des `TouchEditContext`.
* SITES-33355 : ouvrez le nouvel éditeur CF sur « Afficher la payload » dans la console de workflow.
* SITES-33356 : ouvrez le nouvel éditeur CF sur Créer un CF → Ouvrir dans l’interface utilisateur d’administration de l’IU tactile.
* SITES-32952 : gestion incohérente des valeurs par défaut des champs CFM lors de l’utilisation de l’API de diffusion.
* SITES-31539 : Edge Delivery avec l’éditeur universel : ajoutez la prise en charge des balises de métadonnées de configuration de l’éditeur universel dans `head.html`.
* SITES-20672 : Edge Delivery avec éditeur universel : ajoutez la prise en charge de feuilles de calcul de métadonnées en bloc supplémentaires dans la création.
* SITES-32963 : Edge Delivery avec éditeur universel : ajoutez de nouvelles métadonnées d’expérimentation pour la cible d’optimisation, l’affectation automatique et l’auto-apprentissage.
* SITES-30847 : version 2.30.0 des composants principaux.
* SITES-29617 : le point d’entrée referenceBy a été mis à jour pour utiliser la classe ReferenceSearch, ce qui améliore ses performances et sa fiabilité.
* SITES-19308 : amélioration des performances du processus de suppression de page en optimisant l’étape de validation de référence.
* SITES-34293 : chargement différé implémenté pour les ressources modélisées afin d’améliorer les performances.
* SITES-33892 : ajout d’un bouton (bascule) de fonctionnalité pour ignorer les vérifications de référence pour les pseudo-pages, ce qui peut améliorer les performances.

### Problèmes résolus {#fixed-issues-22450}

* CQ-4360550 : correction d’une disparition inattendue de la copie de langue après l’annulation du déplacement de page dans AEM Cloud Service.
* SITES-25232 : les liens Définir la date et Quitter Timewarp ne disposent pas d’un indicateur de focus visible.
* SITES-25258 : le focus n’est pas géré à l’aide de la boîte de dialogue modale Supprimer l’annotation.
* SITES-25305 : la barre d’outils démographique ne reçoit pas le focus dans un ordre logique.
* SITES-25366 : l’état de chargement de la fenêtre modale de teaser n’est pas annoncé par le lecteur d’écran.
* SITES-34276 : Edge Delivery avec éditeur universel : correction de la politique CORS créée automatiquement qui n’est pas appliquée au niveau publication.
* SITES-34811 : Edge Delivery avec éditeur universel : correction du sélecteur hlx qui n’est pas ajouté aux liens vers les feuilles de calcul en cours de création.
* SITES-31669 : chaînes non localisées « Cette page redirige vers » dans Outils > Sites > Lancements.
* SITES-30879 : chaînes non localisées dans Sites > Éditeur de page > Composant Recherche.
* SITES-30959 : chaînes non localisées dans l’éditeur de page > composant Image.
* SITES-21743 : « Veuillez sélectionner un document à afficher » non localisé. chaîne dans Éditeur de page > Visionneuse PDF
* SITES-19785 : les chaînes ne sont pas localisées dans le site des composants principaux > Onglets.
* SITES-22059 : chaîne « Aperçu du fichier non disponible » non localisée dans site des composants principaux > Visionneuse PDF.
* SITES-33360 : erreur « » non localisée pendant l’opération. Le chemin d’accès fourni n’est pas une chaîne « launch » dans Lancements > Modifier.
* SITES-32975 : format de date non localisé dans l’interface utilisateur découplée > Lancements > Comparer Launch à Source.
* SITES-32973 : chaînes codées en dur dans l’interface utilisateur découplée > Lancements > Rebase.
* SITES-13540 : chaînes non localisées dans Lancements > Promotion.
* SITES-13085 : chaînes d’erreur non localisées dans la page Sites > Création de Launch.
* SITES-21499 : la chaîne non localisée est Sites > Lancements > Modifier.
* SITES-14961 : troncature du champ de date dans la boîte de dialogue Sites > Propriétés > Plan directeur > Déploiement .
* SITES-33764 : les filtres de lancement (chemin Source/lancements créés par un workflow) ne fonctionnent pas.
* SITES-33884 : « Promouvoir la page active et les sous-pages » favorise involontairement les pages hors de portée.
* SITES-33611 : l’aperçu de la Live Copy ne fonctionne pas pour les marchés à volume élevé.
* SITES-34331 : expiration du délai d’expiration de 503 lors du chargement du recouvrement de déploiement pour les utilisateurs non administrateurs.
* SITES-34403 : `NullPointerException` en `GraphqlClientImpl deactivate()` lors de l’arrêt.
* SITES-33817 : résolution des problèmes de synchronisation entre le schéma d’interface utilisateur et le modèle JCR pour garantir la cohérence.
* SITES-31141 : les références de contenu qui ne sont pas représentées par un chemin d’accès sont désormais correctement renvoyées dans la réponse de l’API.
* SITES-34080 : le processus de création de fragments de contenu est désormais plus robuste et n’échouera pas si aucun champ n’est fourni à la requête.
* SITES-30773 : l’expression régulière permettant de rechercher des mots à l’aide de « Rechercher et remplacer » a été améliorée afin de correspondre correctement aux caractères UTF-8.
* SITES-33742 : résolution d’un bug qui empêchait le déplacement réussi d’un fragment de contenu lors de l’utilisation de l’API de workflow.

### Problèmes connus {#known-issues-22450}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-22450}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-22450}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 18 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-22450}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.84.0 | [API Oak 1.84.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.84/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.29.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
