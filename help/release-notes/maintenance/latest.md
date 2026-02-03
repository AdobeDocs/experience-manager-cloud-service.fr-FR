---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a842a5f0bd5561563a86f6f0b6e8abf8cfd679ec
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 24%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 24222 {#24222}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 24222, rendue publique le mercredi 3 février 2026. La version de maintenance précédente était la version 23963.

L’activation des fonctionnalités de la version 2026.2.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-24222}

* CNTBF-604 : créer une version de lot contentbackflow.
* CQ-4361592 : ajoutez la prise en charge de TypeHint pour la création et la mise à jour de projets.
* CQ-4362198 : dernières traductions de packages AEM et Granite.
* GRANITE-36205 : mettez à jour la version interne d’Oak vers la dernière version.
* GRANITE-59211 : OPTEL : ajout de la prise en charge à usage unique et de la configuration en libre-service.
* GRANITE-62166 : mettez à jour le lot de migration pour réutiliser les états de migration de l’outil de migration.
* GRANITE-62598 : suppression de la propriété redondante exclue du filtre du package de contenu.
* GRANITE-62684 : rendre le délai d’expiration du socket client configurable via skyline-ops.
* GRANITE-62702 : remplacez la découverte Sling par une implémentation autonome pour la migration en ligne.
* GRANITE-62763 : met à jour la liste des exceptions d’obsolescence de Guava en fonction de l’outil rotatif ASSETS.
* GRANITE-62771 : échec des builds de démarrage rapide lorsque de nouvelles dépendances Commons-Lang obsolètes sont introduites.
* GRANITE-62987 : mettez à jour la console web Felix vers la version 5.0.18.
* GRANITE-63339 : amélioration du mécanisme de bail pour l’objet Blob Azure Migration-State.
* GRANITE-63343 : ajoutez la prise en charge de la dernière version du lot d’API Sling dans workflow.core.
* GRANITE-63799 : version groupée d’authentification OIDC par lot.
* GRANITE-63821 : mise à jour de la version Quickstart vers filevault fixant JCRVLT-831/JCRVLT-839.
* GRANITE-63827 : mise à jour de Quickstart vers la dernière version publique d’Oak (1.90.0).
* GRANITE-63888 : mise à jour de Quickstart vers Jackrabbit 2.22.3.
* GRANITE-64030 : ajoutez des mots-clés et des modèles à la liste autorisée pour le programme de validation de langage d’expression.
* GRANITE-64050 : permet aux dossiers de configuration masqués de masquer les fonctionnalités de produit externes.
* SITES-30452 : API de contenu avec ASO - Suggestions de titre et de description.
* SITES-38099 : mettez à jour `testing-model.txt` pour utiliser une version supérieure des contrôles d’intégrité.
* SKYOPS-43616 : migration des informations d’identification Jenkins vers Vault dans les référentiels du Dispatcher.
* SKYOPS-108584 : outil Bump FACT de 0.6.0 à 0.6.10.
* SKYOPS-115691 : mise à niveau du lot de filtres CORS pour ajouter un en-tête Vary Origin aux requêtes de contrôle en amont.
* SKYOPS-123094 : mise à jour des composants HTTP Apache dans Quickstart.
* SKYOPS-123236 : inclusion de `rep:cugPolicy` dans le package de réplication.
* SKYOPS-123240 : mise à jour des dépendances CRXDE dans Quickstart.
* SKYOPS-123247 : mise à jour du lot Sling XSS dans Quickstart.
* SKYOPS-123250 : mise à jour du lot de sécurité Sling dans Quickstart.
* SKYOPS-123327 : nécessite Java 21 pour le SDK AEM-CS.
* SKYOPS-125574 : mise à jour des lots d’outils netcentric AC dans Quickstart.
* SKYOPS-126150 : amélioration de la commande supérieure pour le script du générateur d’images mémoire de threads.

### Problèmes résolus {#fixed-issues-24222}

* FORMS-23687 : correction de l’échec de validation du SSV lorsque la règle contient est utilisée sans valeur par défaut.
* GRANITE-48472 : erreur de localisation lors de la modification du mot de passe dans l’onglet Modifier les paramètres utilisateur .
* GRANITE-50286 : correction d’un problème de mise en page dans la colonne de statut de la boîte de dialogue modale User Management.
* GRANITE-52301 : localisation Impossible de valider les modifications apportées à la chaîne de session dans les groupes de sécurité.
* GRANITE-52920 : erreur de localisation lors de la création d’un utilisateur dans Sécurité Créer un utilisateur.
* GRANITE-54654 : localisez la chaîne dans la boîte de dialogue de vérification des configurations Adobe IMS de sécurité .
* GRANITE-56371 : correction d’un format de données incorrect dans le Trust Store de sécurité.
* GRANITE-62717 : mettez à niveau le KeyStore de chiffrement pour la gestion des mots de passe JSafe avec des caractères non-ASCII.
* GRANITE-62789 : mettez à jour messaging-client pour prendre en charge le mode aucune reprise sur la distribution de contenu.
* GRANITE-62824 : correction des `NullPointerException` lors de l’accès à l’onglet Groupes dans l’éditeur utilisateur.
* GRANITE-63080 : rendre l’importation des `org.slf4j.spi` compatibles avec les `slf4j 2.x`.
* GRANITE-63210 : mettez à jour le cœur de distribution pour corriger l’invalidation du Dispatcher au démarrage de la publication.
* GRANITE-63293 : correction du champ de chemin obligatoire qui perd l’astérisque requis après la première création.
* GRANITE-63360 : correction des informations incorrectes affichées lorsque plusieurs chemins d’accès sont sélectionnés.
* SITES-36242 : affinez l’expression régulière d’exécution GraphQL pour corriger le contournement du filtre du Dispatcher.
* SKYOPS-84379 : utilisez le dernier outil FACT pour que les RDE choisissent correctement les fonctionnalités.
* SKYOPS-121216 : restauration de la mise à jour des bibliothèques Jackson 2.20.0.

#### AEM Guides {#guides-24222}

* GUIDES-38198 : lors de la mise à jour d’une équation MathML intégrée à l’aide de l’option Modifier MathML du menu contextuel, la valeur mise à jour n’est pas reflétée tant que la page n’est pas actualisée.
* GUIDES-38276 : impossible de supprimer les libellés de version du panneau Historique des versions dans l’interface utilisateur d’Assets.
* GUIDES-36641 : lors de la génération de la sortie AEM Sites, les titres de mappage contenant des mots-clés et des titres de rubrique avec `<ph>` élément ne sont pas inclus dans la sortie publiée.
* GUIDES-37837 : lors de la tentative d’enregistrement d’une rubrique ou d’un mappage, l’opération peut échouer par intermittence avec une erreur Échec d’enregistrement de fichier, en particulier lors de tâches de traitement intensif des ressources ou de workflows de traduction exécutés en arrière-plan.
* GUIDES-27774 : le rapport Liste interrompue inclut incorrectement des liens externes, des `keyrefs` valides et des mots-clés qui sont correctement résolus dans la portée du mappage actuel.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-24222}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-24222}

* AEMSRE-2896 : correction de la gestion de la configuration du gestionnaire de journal personnalisé.
* GRANITE-62802 : suppression de la dépendance `commons-lang` obsolète de `granite.auth.saml`.
* GRANITE-62805 : suppression de la dépendance `commons-lang` obsolète de `granite.httpcache.core`.
* GRANITE-62864 : suppression de la dépendance `commons-lang` obsolète de `granite.jobs.async`.
* GRANITE-62865 : suppression de la dépendance `commons-lang` obsolète de `granite.replication.core`.
* GRANITE-62868 : suppression de la dépendance `commons-lang` obsolète de `granite.rest.api`.
* GRANITE-62895 : suppression de la dépendance `commons-lang` obsolète de `translation.connector.msft.core`.
* GRANITE-63069 : `com.adobe.granite.httpcache.core` obsolète.
* GRANITE-63179 : suppression de la dépendance `commons-lang` obsolète de `cq-workflow-impl`.
* GRANITE-63180 : permet de supprimer l’exportation de `commons.lang` obsolète `cq-mailer` lot.
* SKYOPS-123329 : abandon de la prise en charge de Java 11 pour les déploiements AEM Ethos et mise à jour des `commons-lang3`.
* SKYOPS-124983 : suppression des `nashorn.args` obsolètes des scripts de démarrage d’AEM.

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-24222}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 10 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-24222}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.90.0 | [API Oak 1.90.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.30.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
