---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: b83d8736d47778ed133e0cc07207e02e581bbc69
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 36%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 24893 {#release-24893}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 24893, publiée le mercredi 17 mars 2026. La version de maintenance précédente était la version 24678.

L’activation des fonctionnalités de la version 2026.3.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-24893}

* CNTBF-613 : correctif d’accès refusé (JCR-101) - échec de l’enregistrement des types de nœuds.
* GRANITE-53957 : mettre à niveau Azure SDK V8 vers V12 pour oak-blob-azure.
* GRANITE-57035 : utilisez Bouncy Castle comme fournisseur de sécurité par défaut.
* GRANITE-59249 : évitez d’enregistrer un fournisseur de sécurité dans la JVM.
* GRANITE-61564 : l’ouverture des paramètres d’affichage sur `/security/users.html` échoue pour les administrateurs.
* GRANITE-64748 : OIDC : configurable `sling.oauth-request-key` l’expiration du cookie.
* SITES-39767 : prend en charge la valeur à usage unique via l’attribut de requête (CSP).
* SKYOPS-129301 : définition du niveau de conformité jar javadoc des API sur 17.
* GRANITE-64962 : mettre à jour Apache Jackrabbit Oak vers la version 1.92.0.
* GRANITE-64963 : mettre à jour Apache Jackrabbit Filevault vers la version 4.2.0.
* GRANITE-64764 : mise à jour du texte Apache Commons vers la version 1.15.0.
* SKYOPS-131412 : mettre à jour Apache Commons Exec vers la version 1.6.0.
* SKYOPS-131432 : mise à jour de Felix SCR vers la version 2.2.14.
* SKYOPS-131907 : mise à jour de la région API Sling vers la version 1.1.10.
* SKYOPS-131938 : mise à jour de GSON vers la version 2.13.2.
* SKYOPS-132173 : mise à jour du codec Apache Commons vers la version 1.21.0.
* SKYOPS-132182 : mise à jour du client Sling vers la version 1.1.8.
* SKYOPS-132267 : mettre à jour org.osgi.service.component vers la version 1.5.1.
* SKYOPS-132272 : mise à jour du modèle de fonctionnalité Sling vers la version 2.0.4.
* SKYOPS-133689 : mise à jour de Dispatcher pour utiliser Apache httpd 2.4.66.

### Problèmes résolus {#fixed-issues-24893}

* GRANITE-64443 : `workflow.core` les exportations obsolètes de `log4j`.
* GRANITE-64543 : la réponse des restrictions d’autorisation doit correspondre au contrat d’API.

#### AEM Guides {#guides-24893}

* GUIDES-38412 : lors de la modification d’un fichier de `(*.sch)` Schematron et de l’utilisation de la fonction de recherche et de remplacement, le panneau de recherche et de remplacement s’affiche partiellement hors écran en bas, empêchant l’accès à ses champs et contrôles de saisie.
* GUIDES-37806 : lorsque la même rubrique est réutilisée sur plusieurs mappages avec des paramètres prédéfinis conditionnels différents, la publication du dernier mappage sur Salesforce remplace le contenu de la rubrique, ce qui entraîne l&#39;affichage de données incorrectes aux utilisateurs de mappages précédemment publiés.
* GUIDES-39394 : lorsqu’une image initialement gérée en tant que ressource spécifique à la langue avec une version spécifique (par exemple, sous `/en/`) est déplacée vers un dossier global avec une version mise à jour et que l’exportation de la ligne de base est effectuée, la nouvelle ligne de base continue à référencer des versions obsolètes spécifiques à la langue de cette image, ce qui entraîne l’échec de l’exportation de la ligne de base.
* GUIDES-39054 : lors de la création d’une ligne de base dynamique, l’éditeur ne répond parfois plus en raison de plusieurs requêtes d’API simultanées, ce qui interrompt toutes les autres opérations.
* GUIDES-37781 : lors de l’affectation d’un utilisateur à une tâche de révision, la liste déroulante répertorie tous les utilisateurs au lieu de seulement ceux associés aux projets sélectionnés, ce qui entraîne la non-validité des options utilisateur.
* GUIDES-39385 : Lors de l’ouverture d’un rapport pour une carte, le chargement du panneau Filtres est retardé.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-24893}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-24893}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-24893}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 9 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-24893}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.92.0 | [API Oak 1.92.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.92.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2,4,66 | [Apache Httpd 2.4.66](https://apache.googlesource.com/httpd/+/refs/tags/2.4.66/CHANGES) |
| Composants principaux AEM | 2.30.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
