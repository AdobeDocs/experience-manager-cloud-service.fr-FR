---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 61a3d334e7187dcbf047d1b464d918ddf2cf9444
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 79%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 15977 {#release-15977}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 15977, rendue publique le 19 avril 2024. La version de maintenance précédente était la version 15939.

L’activation des fonctionnalités de la version 2024.4.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-15977}

* GRANITE-51335 : optimisation du contrôle d’intégrité d’AEM pour augmenter la stabilité de l’instance.

### Problèmes résolus {#fixed-issues-15977}

* CQ-4357226 : correction de la régression dans la prise en charge des configurations IMS pour les informations d’identification OAuth.
* GRANITE-51335 : mise à niveau de Ratelimit vers la version 5.0.4, avec correction des enregistrements du contrôle d’intégrité Felix.

### Problèmes connus {#known-issues-15977}

* **(Pour AEM Forms uniquement)** Après l’installation de la version de maintenance 1597 d’AEM Cloud Foundation, les champs de formulaire adaptatif sont rendus dans un ordre incorrect lors de la création du formulaire et pour les formulaires publiés. Si vous utilisez AEM Forms, pour éviter tout désagrément, il est recommandé de ne pas effectuer la mise à niveau vers cette version tant que le problème n’aura pas été résolu dans la version de maintenance à venir.

### Fonctionnalités et API obsolètes {#deprecated-15977}

* [Obsolescence des informations d’identification JWT dans Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

Consultez les [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md) pour savoir ce qui est obsolète ou supprimé dans AEM as a Cloud Service.

### Technologies intégrées {#embedded-tech-15977}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.62.0 | [API Oak 1.62.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| API SLING AEM | 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.24.6 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
