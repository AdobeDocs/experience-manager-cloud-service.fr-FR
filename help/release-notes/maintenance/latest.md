---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: e035c1c27f652af231034588eb1359354182dcb0
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 62%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 25194 {#25194}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 25194, rendue publique le jeudi 1 avril 2026. La version de maintenance précédente était la version 24678.

L’activation des fonctionnalités de la version 2026.4.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

>[!NOTE]
>
>La version 24893 a été rendue privée.

### Améliorations {#enhancements-25194}

* ASSETS-65127 : métadonnées personnalisées d’événement : meilleure gestion des noms de métadonnées.
* ASSETS-63313 : création automatique de liens associés pour les ressources exportées et les parents en fonction des manifestes C2PA.
* ASSETS-10995 : limitation du nombre de ressources dans un fichier compressé de téléchargement.

### Problèmes résolus {#fixed-issues-25194}

* ASSETS-62882 : vue Administration : l’info-bulle se rompt lorsque plusieurs noms de fichier non valides sont chargés.
* ASSETS-63642 : le lien de partage ne parvient pas à effectuer le rendu de la ressource sur certains environnements de développement (SLA3).
* ASSETS-59267 : NPE lors du chargement des métadonnées d’application pour la payload de diffusion.
* ASSETS-59227 : exportation des métadonnées : les propriétés non sélectionnées ne sont plus incluses en raison d’une correspondance d’expression régulière.
* ASSETS-65187 : aperçu au format CSV dans le cloud lorsque les données de colonne contiennent des virgules d’échappement.
* ASSETS-63441 : assurez-vous que tous les utilisateurs sont autorisés à lire la configuration Assets Omnisearch.
* SITES-40095 : éditeur de métadonnées : références de fragment de contenu local au-delà de 10 entrées.

### Problèmes connus {#known-issues-25194}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-25194}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-25194}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 9 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-25194}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.90.0 | [API Oak 1.90.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.30.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
