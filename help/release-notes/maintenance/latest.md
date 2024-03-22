---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: dbdc63db9a9ac954ce6359d3643231d6e195fd53
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 92%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 15575 {#release-15575}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 15575, publiée le mercredi 19 mars 2024. La version de maintenance précédente était la version 15262.

L’activation des fonctionnalités de la version 2024.3.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-15575}

Aucun.

### Problèmes résolus {#fixed-issues-15575}

* ASSETS-36358 : le rapport de chargement ne peut pas être rendu.
* GRANITE-50774 : GraniteContent doit utiliser l’ordre déterministe des valeurs de propriété au moment de l’initialisation.

### Problèmes connus {#known-issues-15575}

Aucun.

### Avis de modification {#change-notice-15575}

**Actions requises**

#### Définir la version CM Java sur 11 {#set-java-version-11}

La nouvelle version d’aem-sdk-api contient des classes compilées avec une cible Java 11, qui n’est pas compatible avec le JDK version 1.8 par défaut de l’environnement de génération de Cloud Manager. Cette mise à jour nécessite que Maven soit exécuté à l’aide de JDK 11.

Il est conseillé aux clientes et clients d’ajouter un fichier `.cloudmanager/java-version` à la racine de leur référentiel git avec le contenu : `11`. Voir [Environnement de création / Définition de la version du JDK Maven](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#alternate-maven-jdk-version).

#### Mise à jour d’aem-cloud-testing-clients vers 1.2.1 {#update-aem-cloud-testing-clients}

Les modifications à venir nécessiteront la bibliothèque [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) utilisée dans vos tests fonctionnels personnalisés pour les mettre à jour vers au moins la version **1.2.1**

Assurez-vous que votre dépendance dans `it.tests/pom.xml` a été mis à jour.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

Cette modification doit être effectuée avant le 6 avril 2024.

Si vous ne mettez pas à jour la bibliothèque de dépendances, des échecs de pipeline se produiront à l’étape « Tests fonctionnels personnalisés ».

### Technologies intégrées {#embedded-tech-15575}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [API Oak 1.60.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
