---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 1dd2eae9201c86d2cdac78ff99634eff8ca57a05
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 94%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 15860 {#release-15860}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 15860, rendue publique le jeudi 10 avril 2024. La version de maintenance précédente était la version 15787.

L’activation des fonctionnalités de la version 2024.3.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-15860}

Aucun.

### Problèmes résolus {#fixed-issues-15860}

* Correction d’une régression pour l’affichage de la console Lancements lorsqu’un lancement fait référence à une page supprimée ou déplacée.

### Problèmes connus {#known-issues-15860}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-15860}

* [Obsolescence des informations d’identification JWT dans Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

Consultez les [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md) pour savoir ce qui est obsolète ou supprimé dans AEM as a Cloud Service.

### Avis de modification {#change-notice-15860}

**Actions requises**

#### Définir la version CM Java sur 11 {#set-java-version-11}

La nouvelle version d’aem-sdk-api contient des classes compilées avec une cible Java 11, qui n’est pas compatible avec le JDK version 1.8 par défaut de l’environnement de génération de Cloud Manager. Cette mise à jour nécessite que Maven soit exécuté à l’aide de JDK 11.

Il est conseillé aux clientes et clients d’ajouter un fichier `.cloudmanager/java-version` à la racine de leur référentiel git avec le contenu : `11`. Voir [Environnement de création/Définition de la version du JDK Maven](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#alternate-maven-jdk-version).


### Technologies intégrées {#embedded-tech-15860}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [API Oak 1.60.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.24.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
