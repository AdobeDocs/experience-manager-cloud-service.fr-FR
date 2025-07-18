---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 2e90e40a0fe439653987a23792a4c1ec612aafd6
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 63%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 21570 {#21570}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 21570, publiée le mercredi 15 juillet 2025. La version de maintenance précédente était la version 21484.

>[!NOTE]
>
>[La version 21484](/help/release-notes/maintenance/2025/2025-7-0.md#21484) a été rendue privée et remplacée par la version 21570.

L’activation des fonctionnalités de la version 2025.7.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-21570}

* Migration vers Apache Httpd 2.4.63

### Problèmes résolus {#fixed-issues-21570}

* SKYOPS-112722 - Correction d’un problème en raison duquel la résolution des URL de redirection échouait

### Problèmes connus {#known-issues-21570}

* Le SDK AEM associé porte un ID de version différent (21575) et est disponible via le portail de distribution de logiciels .
* La version 2.4.63 du serveur HTTP Apache a introduit un changement majeur dans la façon dont `mod_rewrite` gère les points d’interrogation (`?`) dans les URL. Cette modification a été mise en œuvre pour empêcher l’utilisation de l’indicateur `UnsafeAllow3F`, qui a été considéré comme un risque pour la sécurité. Cela affecte toutes les directives `RewriteRule` qui reposent sur la détection de points d’interrogation dans les modèles d’URL.

### Fonctionnalités et API obsolètes {#deprecated-21570}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-21570}

Aucune

### Technologies intégrées {#embedded-tech-21570}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.80.0 | [API Oak 1.80.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2,4,63 | [Apache Httpd 2.4.63](https://github.com/apache/httpd/blob/2.4.63/CHANGES) |
| Composants principaux d’AEM | 2.29.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
