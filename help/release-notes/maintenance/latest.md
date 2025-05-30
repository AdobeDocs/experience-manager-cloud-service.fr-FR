---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 6884e33a922a7147e3a6a3f3ddb3dd3b2da85fbf
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 50%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 21005 {#21005}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 21005, rendue publique le mercredi 27 mai 2025. La version de maintenance précédente était la version 20626.

L’activation des fonctionnalités de la version 2025.5.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-21005}

* GRANITE-58927 : améliorations du bouton bascule Recherche sémantique .
* GRANITE-58800 : mise à jour des collections Apache Commons vers la version 4.5.0.
* GRANITE-58866 : mise à jour d’Oak vers la version 1.80.0.
* SKYOPS-106509 : compatibilité GSON améliorée via l’accès réfléchissant dans Java 21.
* SKYOPS-107761 : mise à jour des modèles Sling Jackson Exporter vers la version 1.1.6.
* SKYOPS-107813 : mise à jour vers Sling ResourceResolver 1.12.8.

### Problèmes résolus {#fixed-issues-21005}

* CNTBF-443 : correction de la propriété `EVENT_JOB_TOPIC` SearchSlingJob.
* GRANITE-57853 : correction des problèmes d’alignement des listes déroulantes dans l’interface utilisateur.
* GRANITE-58107 : correction des erreurs 404 sur l’instance de publication en désactivant l’affinité pod basée sur l’utilisateur dans le gestionnaire OAuth.
* GRANITE-58276, SLING-12755 : correction des cycles de dépendance OSGi qui empêchaient le démarrage correct de la fabrique de moteurs de scripts HTL, provoquant des erreurs de rendu côté serveur intermittentes.
* SKYOPS-105151 : correction du NPE lors de l’accès à la liste de lots.
* SKYOPS-83910, SKYOPS-82371 - Correction des problèmes de simultanéité de la compilation JSP.

#### Guides AEM {#guides}

* GUIDES-26919 : lors de l&#39;ouverture d&#39;un plan DITA avec Unified Shell activé, l&#39;éditeur s&#39;actualise par intermittence.
* GUIDES-26282 : si vous ne fermez pas les connexions de session JCR lors de la mise à jour ou de la création de rubriques, des fuites de mémoire et des temps d’arrêt du service se produisent.
* GUIDES-26434 : la publication native de PDF se poursuit indéfiniment, si le contenu DITA comporte un lien web sans portée comme `external`.
* GUIDES-26516 : la publication des PDF natifs et des sites AEM est bloquée et mise en file d’attente en cas d’erreur dans le contenu.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-21005}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-21005}

* GRANITE-54164 : `org.apache.jackrabbit.oak.plugins.blob` supprimé de l’API publique.
* GRANITE-54280 : `org.apache.jackrabbit.oak.cache` supprimé de l’API publique.
* GRANITE-58332 : `org.apache.jackrabbit.oak.plugins.memory` obsolète dans l’API publique.
* Le compresseur YUI pour JavaScript est obsolète.
* La fonctionnalité [Automatisation de la configuration d’Experience Cloud](/help/sites-cloud/integrating/adobe-analytics-exc-setup-automation.md) est obsolète.

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-21005}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 5 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Avis de modification {#change-notice-21005}

* Cette version contient les nouvelles versions de l’index de produit suivantes :
   * **damAssetLucene-12**

Les versions personnalisées des versions d’index précédentes seront automatiquement fusionnées avec la nouvelle version de l’index de produit. Appliquez d’autres mises à jour personnalisées à la version fusionnée.

#### Mettre à jour aem-cloud-testing-clients {#update-aem-cloud-testing-clients-21005}

Les modifications à venir nécessiteront que la bibliothèque [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) utilisée dans vos tests fonctionnels personnalisés soit mise à jour vers au moins la version **1.2.1** (Recommandé : dernière version 1.2.9)

Assurez-vous que votre dépendance dans `it.tests/pom.xml` a été mis à jour.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.9</version>
</dependency>
```

Cette modification doit être effectuée avant le 15 juin 2025.
Si vous ne mettez pas à jour la bibliothèque de dépendances, des échecs de pipeline se produiront à l’étape « Tests fonctionnels personnalisés ».

### Technologies intégrées {#embedded-tech-21005}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1,80,0 | [API Oak 1.80.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.29.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
