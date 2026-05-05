---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 82b3b4bdcd09aa86974518f4f62e73c9f377c83f
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 30%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## 25821 de publication {#release-25821}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 25821, rendue publique le 5 mai 2026. La version de maintenance précédente était la version 25520.

L’activation de la fonctionnalité 2026.5.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-25821}

* CQ-4362304 : Création de directives pour l’interface utilisateur frontale et mise à jour de la configuration LLM.
* GRANITE-39546 : mise à niveau d’Apache Tika vers 3.x.
* GRANITE-53957 : mettre à niveau Azure SDK V8 vers V12 pour oak-blob-azure.
* GRANITE-61245 : supprimer toute utilisation de commons-lang (remplacer par commons-lang3).
* GRANITE-64748 : gestionnaire d’authentification OIDC en bloc.
* GRANITE-64764 : mise à jour du texte Apache Commons vers la version 1.15.0.
* GRANITE-64963 : mise à jour de Filevault vers la version 4.2.0.
* GRANITE-66197 : ajout de la prise en charge de l’API Microsoft Graph pour les clients M365.
* GRANITE-66449 : mise à jour des modules externes Maven pour la prise en charge de l’API Java 17.
* GRANITE-66473 : ajout de la bibliothèque de cache de caféine à base-granite.
* GRANITE-66836 : mise à jour de Quickstart vers Oak 2.0.0.
* SKYOPS-129301 : définition du niveau de conformité Jar Javadoc des API sur Java 17.
* SKYOPS-129351 : Mise à jour des flux réactifs et du cœur du réacteur pour la compatibilité avec MCP SDK.
* SKYOPS-131412 : mettre à jour Apache Commons Exec vers la dernière version.
* SKYOPS-131432 : mise à jour de Felix SCR vers la version 2.2.14.
* SKYOPS-131907 : mise à jour des régions API Sling vers la version 1.1.10.
* SKYOPS-131938 : mettre à jour GSON vers la dernière version.
* SKYOPS-132173 : mise à jour du codec Apache Commons vers la dernière version.
* SKYOPS-132182 : mise à jour du lot de client Sling.
* SKYOPS-132267 : mise à jour de l’annotation `org.osgi.service.component`.
* SKYOPS-132272 : mise à jour du lot de modèle de fonctionnalité Sling.
* SKYOPS-132525 : ajout d’un analyseur de démarrage rapide pour empêcher les nouvelles suppressions d’API.
* SKYOPS-134408 : mise à jour de la `com.adobe.granite.asset.core` vers la version 2.2.82.
* SKYOPS-137750 : mise à jour de la `com.adobe.granite.comments` vers la version 1.0.40.
* SKYOPS-137759 : mise à jour d’`com.adobe.granite.jobs.async.ui.commons` vers la version 3.2.4.
* SKYOPS-138356 : mise à jour de la `com.adobe.granite.oauth.server` vers la version 1.1.36.
* SKYOPS-138739 : mise à jour de SnakeYAML vers la version 2.6.

### Problèmes résolus {#fixed-issues-25821}

* ASSETS-59546 : suppression des dépendances sur la bibliothèque commons-lang obsolète.
* ASSETS-64831 : la réinitialisation du nombre de tentatives de traitement par AssetProcessorProcess entraîne le blocage des ressources.
* ASSETS-66683 : boucle d’approbation provoquée par l’échec de uploadBlob.
* CNTBF-613 : correction de l’accès refusé (JCR-101) lors de l’enregistrement des types de nœuds.
* GRANITE-44537 : chaîne dans « Country/Region » non localisée dans AEM.
* GRANITE-61760 : correction de l’échec d’activation d’AdminUserInitializer.
* GRANITE-64543 : la réponse des restrictions d’autorisation ne suit pas la structure de l’API.
* GRANITE-66692 : chargeur de classe interne non sensible aux actualisations de package.
* GRANITE-66732 : utilisez des activateurs au lieu des composants de service pour les lots de niveau 1 de départ.
* GRANITE-66846 : l’API Autorisations AEM n’affiche pas la restriction `rep:ntNames`.
* SITES-39267 : restaurez pagePath dans les entrées de chaîne de relation.
* SITES-43715 : la validation des autorisations échoue lors de la lecture du statut de la ressource.

#### AEM Guides {#guides-25821}

* GUIDES-45110 : lors de la sélection d’une image dans l’éditeur à l’aide de la boîte de dialogue **Sélectionner un fichier**, seuls les formats de trame (tels que JPG, PNG et GIF) s’affichent. Les fichiers vectoriels (tels que `.ai` et `.eps`) ne sont pas affichés et ne peuvent pas être sélectionnés.
* GUIDES-41938 : La création d’une rubrique dans un dossier dont le nom contient des espaces crée un dossier en double dans lequel les espaces sont remplacés par des tirets et la rubrique y est enregistrée au lieu du dossier d’origine.
* GUIDES-38377 : lorsque des modifications apportées à un paramètre prédéfini de sortie dans un profil de dossier sont appliquées à des mappages existants, le **contexte de publication** enregistré pour le paramètre prédéfini AEM Sites est réinitialisé.
* GUIDES-43547 : lorsque des rubriques ou des mappages volumineux sont ouverts, l’instance de création ne répond plus, ce qui nécessite un redémarrage dans certains cas.
* GUIDES-32520 : lorsque la touche Retour arrière est utilisée sur des éléments, l’éditeur fait défiler l’écran jusqu’en haut de la rubrique, quelle que soit la position du curseur (Editor 2.0).

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-25821}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-25821}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-25821}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 19 vulnérabilités identifiées, renforçant ainsi notre engagement en faveur d’une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-25821}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 2.0.0 | [API Oak 2.0.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/2.0.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.30.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
