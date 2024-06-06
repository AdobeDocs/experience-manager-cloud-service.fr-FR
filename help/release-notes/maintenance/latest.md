---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: de06178f66c95baef15de19296a654f1ed4a0387
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 92%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 16544 {#release-16544}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 16544, publiée le 4 juin 2024. La version de maintenance précédente était la version 16461.

L’activation des fonctionnalités de la version 2024.6.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-16544}

* GRANITE-41133 : prise en charge de l’API Servlet Jakarta 5 et de l’API OSGi Servlet Whiteboard.
* GRANITE-51355 : org.slf4j.event est obsolète.
* GRANITE-51565 : AEM perd la relation de groupe local avec un groupe externe lorsque le groupe local est publié à partir d’AEM.
* GRANITE-51707 : définition du cookie saml_request_path lors de la redirection http pour l’authentification.
* GRANITE-52010 : mise à jour de la version Jackrabbit vers 2.20.16.
* GRANITE-52057 : mise à jour de Filevault vers la version 3.7.3-T20240514105118-694f6aea avec correction de JCRVLT-745.
* SKYOPS-35998 : mise à jour des dépendances Sling RepoInit : Repoinit Parser 1.9.0, Repoinit JCR 1.1.46.

### Problèmes résolus {#fixed-issues-16544}

* GRANITE-51375 : idp-sync renvoie NPE si aucun chemin intermédiaire n’est spécifié.
* GUIDES-17171 : l’opération de copier-coller de rubriques de plus de 15 Ko échoue avec une erreur inattendue.
* GUIDES-17088 : la fonctionnalité permettant de modifier l’état du document à partir du panneau **Propriétés du fichier** ne fonctionne pas correctement et passe à l’état *Brouillon*.
* GUIDES-16931 : les images liées des rubriques ne s’affichent pas dans la référence après la création de la version.
* GUIDES-16896 : les panneaux de contenu réutilisables ne répertorient pas d’éléments lorsque les **Préférences utilisateur** sont définies pour afficher les fichiers par **Nom de fichier**.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans Experience Manager Guides, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-16544}

Aucun.

### Avis de modification {#change-notice-16544}

À compter de septembre 2024, AEM as a Cloud Service désactivera la sérialisation des résolveurs de ressources via la structure de l’exportateur de modèle Sling. Voir [la documentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) pour plus d’informations.

### Fonctionnalités et API obsolètes {#deprecated-16544}

Pour savoir ce qui est obsolète ou supprimé dans AEM as a Cloud Service, voir [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Technologies intégrées {#embedded-tech-16544}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.64.0 | [API Oak 1.64.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| API SLING AEM | 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.25.4 | [Composants principaux de la gestion de contenu Web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
