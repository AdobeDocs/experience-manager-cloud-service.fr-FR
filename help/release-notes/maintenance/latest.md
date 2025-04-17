---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c5152543550b5f81bf0b79741f288b0c16648584
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 48%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 20476 {#20476}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 20476, rendue publique le mercredi 15 avril 2025. La version de maintenance précédente était la version 20133.

L’activation des fonctionnalités de la version 2025.4.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-20476}

* CNTBF-411 : ajout de la possibilité de supprimer la tâche sling au cas où elle serait supprimée par JCR.
* CQ-4359813 : Kit de traduction AEM : 20 mars.
* CQ-4359811 : Kit de traduction Granite : 20 mars.
* GRANITE-57863 : mettre à jour Filevault vers la version 3.8.4.
* GRANITE-56154 : configuration des reprises exponentielles dans oak-segment-azure.
* GRANITE-55999 : améliore les performances de UserPropertiesService.
* GRANITE-55781 : évite la reconfiguration redondante de l’appartenance des utilisateurs.
* GRANITE-53956 : mettez à niveau Azure SDK V8 vers V12 pour oak-segment-azure.
* GRANITE-50654 : dans l’onglet Autorisations principales , supprimez le chargement « Tout le monde » par défaut sur le front-end.
* SKYOPS-103444 : mise à jour vers Sling ResourceResolver 1.12.6.
* SKYOPS-101147 : mettre à jour caconfig impl.
* SKYOPS-97124 : ajout d’avertissements d’analyseur pour les versions obsolètes du lot SPIFly.
* SKYOPS-95826 : mise à jour des versions d’exécution Java vers les versions 11.0.26 et 21.0.6.
* SKYOPS-53671 : utiliser les artefacts installés par le client à partir des modèles de fonctionnalités lors des redémarrages d’AEM (RDE).

### Problèmes résolus {#fixed-issues-20476}

* ASSETS-49027 : [Régression] AemRequestEventFilter rompt les requêtes POST à la console web OSGI.
* ASSETS-44956 : impossible de sélectionner un rendu Dynamic Media. Les balises de script doivent être chargées dans le composant de niveau supérieur.
* CNTBF-410 : pointeur null CheckJob getId dans le lot ContentCopy.
* CNTBF-341 : l’index d’exportation ContentCopy est hors limites.
* CQ-4355411 : des info-bulles restent affichées dans la boîte de dialogue Préférences utilisateur.
* GRANITE-57265 : les valeurs de sélection de liste déroulante ne sont pas sélectionnées.
* GRANITE-57067 - Politiques efficaces manquantes dans l’interface utilisateur.
* SITES-30727 : le glisser-déposer peut échouer pour les sous-composants dans l’éditeur AEM.
* SKYOPS-90607 : les tâches Sling sont exécutées dans un déploiement inactif/contenu modifiable.
* SKYOPS-95722 : suppression de la taille de `MaxPermSize` des indicateurs de démarrage rapide dans AEM-SDK.
* SKYOPS-103569 : certaines images ne peuvent pas être chargées avec Java 21 : `javax.imageio.IIOException: Cannot create Sun JPEGImageReader backend`.

### Problèmes connus {#known-issues-20476}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-20476}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-20476}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 5 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-20476}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.78.0 | [API Oak 1.78.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.28.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
