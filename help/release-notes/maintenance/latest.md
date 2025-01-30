---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a3c414f9b5e575856a942e02661e8c70a7083495
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 89%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 19149 {#19149}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 19149, publiée le 21 janvier 2025. La version de maintenance précédente était la version 18751.

L’activation des fonctionnalités de la version 2025.1.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-19149}

* ASSETS-45286 : affiche la progression granulaire du traitement asynchrone d’archivage des téléchargements.
* ASSETS-46296 : prend en charge des modèles Dynamic Media dans le sélecteur de ressources.
* ASSETS-44796 : déclenche les événements de ressources pour les traitements de ressources asynchrones de gestion des ressources numériques.

### Problèmes résolus {#fixed-issues-19149}

* GRANITE-55074 : garantit que les en-têtes de réponse CORS sont définis sur les réponses d’erreur.
* ASSETS-43755 : améliorations de l’évolutivité pour la mise en relation des ressources en bloc.
* ASSETS-45399 : redirige vers la console des ressources après la création d’une Live Copy de ressource.
* ASSETS-45462 : problèmes de mise en cache par le navigateur avec les miniatures de dossiers personnalisées.
* ASSETS-46398 : masque les actions de téléchargement et de retraitement pour les modèles DM.
* ASSETS-44484 : problèmes lors du réenregistrement de la configuration des ressources connectées.
* ASSETS-44122 : le traitement de copie asynchrone des ressources ne renomme pas le dossier de destination lors de la copie dans le dossier actif.
* ASSETS-44463 : le bouton de téléchargement CSV n’est pas visible lors de l’export réussi des métadonnées.
* ASSETS-45134 : le déplacement du traitement avec le titre de destination remplace tous les titres de dossier.
* ASSETS-45137 : génère des conflits avec les chargements en bloc via la vue Assets.
* ASSETS-45758 : les relations entre ressources reçoivent une animation infinie de type « en cours de chargement/occupé » après l’ajout d’une relation.
* ASSETS-44148 : l’événement NODE_MOVED dans AEM peut provoquer des NPE parasites dans les journaux.
* ASSETS-28607 : erreur JS lors de la définition de la miniature vidéo personnalisée.
* GRANITE-55781 : améliore la synchronisation des groupes entre Adobe Developer Console et AEM. Pour en savoir plus, voir la section [Modifications concernant la synchronisation des groupes d’utilisateurs et d’utilisatrices et des profils de produits](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization).
* GRANITE-55754 : assurez-vous que les scripts de démarrage de SDK prennent en charge Java 21.
* GRANITE-54248 : impossible de faire défiler tous les éléments du dossier des ressources volumineuses.
* SCRNS-4597 : améliorations de la vue de la liste des résultats de recherche.


### Problèmes connus {#known-issues-19149}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-19149}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées ](/help/release-notes/deprecated-removed-features.md).

#### Modifications concernant la synchronisation des groupes d’utilisateurs et d’utilisatrices et des profils de produits

Lors de l’utilisation d’Adobe Admin Console pour la gestion des autorisations, les groupes suivants NE DOIVENT PAS être utilisés car ils ne seront plus synchronisés avec AEM :
* Groupes AEM se terminant par _GROUP_NAME_SUFFIX.
* Profils de produit provenant d’autres environnements, programmes ou produits.

Pour plus d’informations, consultez la section [Modifications dans la synchronisation des groupes d’utilisateurs et d’utilisatrices et des profils de produit](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization).

#### Obsolescence de l’éditeur SPA {#deprecate-spa-editor}

[L’éditeur SPA](/help/implementing/developing/hybrid/introduction.md) a été abandonné pour les nouveaux projets à partir de la version 2025.1.0. L’éditeur SPA reste pris en charge pour les projets existants, mais ne doit pas être utilisé pour de nouveaux projets.

Les éditeurs recommandés pour gérer le contenu découplé dans AEM sont les suivants :

* [Éditeur universel](/help/edge/wysiwyg-authoring/authoring.md) pour la modification visuelle.
* [Éditeur de fragment de contenu](/help/assets/content-fragments/content-fragments-managing.md) pour la modification basée sur des formulaires.

### Correctifs de sécurité {#security-19149}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige quatre vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-19149}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.72.0 | [API Oak 1.72.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
