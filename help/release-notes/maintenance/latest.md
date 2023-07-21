---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 704f4e250975d8c0cbcfdc5e49b9c03d3a3e2939
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 62%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 12790 {#release-12790}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 12790, publiée publiquement le 21 juillet 2023. Cette mise à jour de maintenance est une mise à jour de la version de maintenance 12697 précédente.

L’activation des fonctionnalités de la version 2023.7.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-12790}

Aucun.

### Problèmes résolus {#fixed-issues-112790}

- SLING-11974 - Correction d’une régression dans SlingHttpServletRequest#getUserPrincipal pour les requêtes non authentifiées. Le correctif garantit qu’une entité de sécurité est renvoyée même pour les requêtes non authentifiées.

### Problèmes connus {#known-issues-12790}

- GRANITE-46601 - Le SDK de démarrage rapide ne démarre pas sur jdk 11.0.20 sans `-Djdk.util.zip.disableZip64ExtraFieldValidation=true` option java

### Technologies intégrées {#embedded-tech-12790}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.52-T20230629133256-25c01b8 | [API Oak 1.52.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
