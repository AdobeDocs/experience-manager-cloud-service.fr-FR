---
title: Guide de migration de Experience Manager en tant que Cloud Service pour les partenaires
description: Guide de migration de Experience Manager en tant que Cloud Service pour les partenaires
exl-id: 4d1addcf-b22d-41a3-ba5c-e5c42244e5cd
source-git-commit: f193c4e81b9b16d07e7ccff6c2f9705b7234f80b
workflow-type: tm+mt
source-wordcount: '2112'
ht-degree: 97%

---

# Guide de migration vers Adobe Experience Manager en tant que Cloud Service pour les partenaires {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration_overview"
>title="Migration vers AEM as a cloud Service"
>abstract="Présente l’approche échelonnée recommandée pour faire assurer la transition des clients de divers déploiements d’Experience Manager vers Experience Manager as a Cloud Service et aider les clients existants à fournir des expériences connectées et continues"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=fr" text="Quelles sont les nouveautés et les différences ?"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=fr" text="Présentation d’AEM as a Cloud Service."

Adobe Experience Manager (AEM) as a Cloud Service propose un socle restructuré pour Experience Manager, qui s’appuie sur une infrastructure basée sur le conteneur, un développement piloté par les API et un processus DevOps guidé, permettant aux professionnels du marketing et aux développeurs de toujours garder une longueur d’avance sur les innovations en matière de gestion de l’expérience client.

Cloud Service associe de riches capacités prêtes à l’emploi et l’extensibilité d’Adobe Experience Manager avec l’agilité de l’architecture cloud native moderne permettant aux marques de répondre à la demande toujours croissante des consommateurs.

Ce document d’une page unique présente l’approche en plusieurs étapes recommandée pour la transition des clients vers Experience Manager as a Cloud Service à partir de divers déploiements d’Experience Manager, et aide les clients existants à proposer des expériences connectées et continues avec cette plateforme moderne créée spécialement pour la gestion de l’expérience.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

<br>

## Prise en main d’Adobe Experience Manager as a Cloud Service {#getting-started}

| Qu’y a-t-il de différent ? | Aperçu de l’architecture |
|--------------------------|--------------------------|
| <ul><li>[Architecture moderne](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html?lang=fr)</li><li>[Mises à jour automatiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/aem-version-updates.html?lang=fr#aem-version-updates)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=fr)</li><li>[Microservices de ressources](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=fr)</li><li>[Fichiers binaires en accès direct](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=fr#asset-upload-with-direct-binary-access)</li><li>[Séparation du code et du contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=fr#developing)</li><li>[Réplication en tant que service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/replication.html?lang=fr)</li><li>[Admin Console, appartenance à un groupe/utilisateur et listes de contrôle d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=fr)</li></ul> | <ul><li>[Présentation d’AEM Architecture](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html?lang=fr#underlying-technology)</li><li>[Pile d’environnements](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[Niveau de création](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=fr#underlying-technology)</li><li>[Niveau de publication](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=fr#content-delivery)</li><li>[Réseau de diffusion de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/cdn.html?lang=fr#content-delivery) </li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) (CI/CD)</li><li>[Gestion des identités](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=fr#onboarding-users-in-admin-console) via [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li><li>[Asset Compute Service](https://experienceleague.adobe.com/docs/asset-compute/using/home.html?lang=fr)</li></ul> |

![AEM as a Cloud Service – Architecture d’exécution](/help/core-concepts/assets/concepts-03.png "AEM as a Cloud Service – Architecture d’exécution")

<br>

## Parcours du développeur dans Adobe Experience Manager as a Cloud Service {#developer-journey}

### Développement

Les principes fondamentaux du développement de code sont similaires dans Adobe Experience Manager as a Cloud Service par rapport aux solutions Adobe Experience Manager On Premise et Managed Services.

Les développeurs écrivent du code et le testent localement. Il est ensuite envoyé vers les environnements distants Adobe Experience Manager as a Cloud Service.

Consultez des ressources d’aide autonome sur la mise en œuvre pour Experience Manager as a Cloud Service pour apprendre comment personnaliser votre déploiement Experience Manager as a Cloud Service.

| Configuration du développement local | Les choses à savoir avant de démarrer |
|-----------|------------|
| <ol><li>Consultez la documentation du [SDK Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=fr#developing) pour en savoir plus.</li><li>Regardez la vidéo relative à l’[installation du SDK Dispatcher](https://video.tv.adobe.com/v/30601) pour comprendre comment procéder</li><li>Regardez la vidéo relative à la [configuration du SDK Dispatcher](https://video.tv.adobe.com/v/30602) pour comprendre comment procéder</li><li>Consultez la documentation sur la [configuration du développement local](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=fr#local-development-environment-set-up) pour en savoir plus</li><li>Configuration de l’accès à la [présentation guidée](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=fr#accessing) d’Experience Manager</li></ol> | <ol><li>[Éléments essentiels du développement](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[Conseils de développement ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#developing)</li><li>[Présentation de la structure de projet Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr)</li><li>[Plan directeur de Digital Foundation](https://solutionpartners.adobe.com/content/dam/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[Système de style](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/style-system.html?lang=fr#authoring)</li><li>[Recouvrements](/help/implementing/developing/introduction/overlays.md)</li><li>[Référence de l’API Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/)</li></ol> |

>[!TIP]
> Voir le tutoriel sur la façon de [développer et de déployer WKND sur le SDK Experience Manager local](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html).

### Déploiement

Les développeurs écrivent du code et le testent localement. Il est ensuite envoyé vers les environnements distants AEM as a Cloud Service.

Cloud Manager, qui était un outil de diffusion de contenu facultatif pour Managed Services, est requis. Il s’agit désormais du seul mécanisme permettant de déployer du code vers les environnements AEM as a Cloud Service.

Consultez les ressources d’aide autonome sur la configuration et le déploiement d’environnements AEM as a Cloud Service.

1. [Configurer les pipelines CM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=fr#using-cloud-manager)
   * Pipeline de production
   * Pipelines de qualité de code et hors production uniquement
2. [Déploiement du code](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#using-cloud-manager)
3. [Présentation des résultats de test](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/overview-test-results.html?lang=fr#using-cloud-manager)
4. **Accès aux journaux**
   * [via l’interface utilisateur de CM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=fr#using-cloud-manager)
   * [via l’interface de ligne de commande Adobe I/O](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=fr#debugging)
5. [Exploitation et maintenance](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/home.html?lang=fr)
   * [Configuration d’OSGI](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#deploying)
   * [Sauvegarde et restauration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/backup.html?lang=fr)

>[!TIP]
> Voir le tutoriel sur la façon de [déployer WKND sur Experience Manager Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html).

### Aide et ressources

1. [Conseils et astuces sur le débogage](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=fr#debugging-aem-as-a-cloud-service)
2. [Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=fr#debugging)
3. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=fr#debugging) (disponible uniquement sur les environnements de développement Experience Manager Cloud et SDK local)
4. [Journaux et journalisation](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
   * [Journaux CM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=fr#debugging) (test d’unité de construction, analyse de code, image de construction, déploiement)
   * [Journaux Experience Manager Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging) (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * Journaux du SDK local (sous host:port/crx-quickstart/logs)

>[!NOTE]
> Pour obtenir une aide supplémentaire, vous pouvez :
>1. [Contacter l’équipe d’assistance Experience Manager](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=fr)
>2. Explorer les [communautés et forums Experience Manager](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)


<br>

## Passage à Adobe Experience Manager as a Cloud Service {#move-to-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_move_to_cloud"
>title="Passage à Adobe Experience Manager as a Cloud Service"
>abstract="Ce document d’une page unique présente l’approche en plusieurs étapes recommandée pour la transition des clients vers Experience Manager as a Cloud Service à partir de divers déploiements d’Experience Manager, et aide les clients existants à proposer des expériences connectées et continues avec cette plateforme moderne créée spécialement pour la gestion de l’expérience."

**Experience Manager as a Cloud Service constitue une base technologique évolutive, sécurisée et agile pour les plates-formes Experience Manager Sites et Assets, qui permet aux spécialistes du marketing et de l’informatique de se concentrer sur la diffusion à grande échelle d’expériences performantes.**

Avec Experience Manager as a Cloud Service, vos équipes peuvent se concentrer sur l’innovation plutôt que sur la planification des mises à niveau de produits. Les nouvelles fonctionnalités du produit sont soigneusement testées et mises en permanence à la disposition de vos équipes, qui ont toujours accès à l’application la plus avancée.

Le parcours de transition vers Cloud Service comprend trois phases : planification, exécution et post-activation.
Pour une transition réussie et fluide, vous devez veiller à une planification adéquate et respecter les bonnes pratiques décrites du présent guide.

La figure ci-dessous est une représentation graphique du parcours recommandé de transition vers Cloud Service.

![image](/help/move-to-cloud-service/assets/home-img1.png)

<br>

### Planification

Avant de commencer votre parcours de transition vers Cloud Service, vous devez vous familiariser avec Experience Manager as a Cloud Service, mais aussi examiner les modifications notables qui y ont été apportées, ainsi que les fonctionnalités remplacées ou obsolètes.

<table>
<tr>
<td>Découverte et évaluation des projets</td>
<td><ul><li>Voir <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=fr">Modifications notables apportées à Experience Manager as a Cloud Service</a> pour comprendre les différences importantes entre Adobe Experience Manager as a Cloud Service et Experience Manager 6.x.</li><li>Consultez <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html?lang=fr#deprecated-features">Fonctionnalités obsolètes</a> pour en savoir plus sur les fonctionnalités qui ont été marquées comme obsolètes.</li><li>[Pour les migrations de Cloud Service uniquement] Évaluation de la préparation de Cloud Service : exécutez <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration">Best Practices Analyzer (BPA)</a> sur l’environnement source. </li><li>Procédez à une évaluation des modifications notables et des fonctionnalités obsolètes dans Experience Manager CS.</li></ul></td>
</tr>
<tr>
<td>Révision</td>
<td><ul><li>En fonction de la découverte, réalisez des exercices d’estimation des efforts et d’allocation de ressources</li></ul></td>
</tr>
<tr>
<td>Mesure</td>
<td><ul><li><a href="https://experienceleague.adobe.com/welcome/aem/part6.html">Définissez les IPC</a>, les critères de succès et la chronologie du projet</li></ul></td>
</tr>
</table>

>[!NOTE]
>Le rapport d’analyse des meilleures pratiques accélère le processus d’évaluation du délai et du coût de la transition vers AEM as a Cloud Service en apportant des informations qui, en son absence, auraient dû être collectées et évaluées manuellement.


<br>

### Exécution

Avant de démarrer la phase d’exécution d’un projet, vous devez être intégré à Cloud Service. Vous devez également vous familiariser avec Cloud Manager. Il s’agit du mécanisme de déploiement du code de projet sur une instance Experience Manager Cloud Service.

Cloud Manager permet aux entreprises de gérer elles-mêmes Experience Manager sur le cloud. Il comprend une structure d’intégration et de diffusion continues ([CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/overview/ci-cd-pipeline.html?lang=fr#overview)) qui permet aux équipes informatiques et aux partenaires d’implémentation d’accélérer la diffusion des personnalisations ou des mises à jour sans compromettre les performances ou la sécurité.

#### Migration du contenu

1. [Outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=fr#migration) : permet de déplacer du contenu existant d’une instance d’AEM source (sur site ou AMS) vers l’instance AEM Cloud Service cible.
2. [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=fr#package-manager) : permet d’importer et d’exporter du contenu modifiable du référentiel.


#### Restructuration/Optimisation

| Prise en main | Révision et code de restructuration | Révision du Dispatcher |
|---|---|---|
| <ul><li>[Configuration du développement local](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up)</li><li>[Configuration du Dispatcher local](https://video.tv.adobe.com/v/30602/)</li><li>[Compilation de votre code à l’aide du fichier JAR de l’API SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[Révision des directives de développement AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)<ul><li>Tâches en arrière-plan et tâches à long terme</li><li>Planificateurs Sling</li><li>Utilisation du flux d’entrée et plus</li></ul></li></ul> | <ul><li>Exécutez l’[analyseur de bonnes pratiques (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=fr#cloud-migration) sur l’environnement source.[**Migration uniquement**]<ul><li>Considérations relatives à la structure du projet (basées sur l’[archétype du cloud](https://github.com/adobe/aem-project-archetype))<ul><li>Séparation du code et du contenu (modifiable ou immuable)</li><li>[Définitions d’index personnalisées](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=fr#indexing)</li><li>[Modes d’exécution personnalisés](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=fr#runmodes)</li></ul></li></ul></li><li>Révision et exécution des modifications nécessaires</li><li>[Déploiement ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=fr)sur le SDK local</li><li>Tests de fumée via le SDK AEM</li></ul> | <ul><li>Contrôle des [configurations du Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=fr#local-validation-of-dispatcher-configuration) pour la restructuration</li><li>Utilisation de l’outil [Convertisseur du Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/dispatcher-transformation-utility-tools.html?lang=fr#introduction-dispatcher), le cas échéant. [**Migration uniquement**]</li><li>Les tests peuvent être réalisés à l’aide du [SDK Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=fr#prerequisites)</li></ul> |

>[!TIP]
> Clients Ressources : contrôlez et restructurez les workflows de ressources à l’aide des outils de [migration du cloud de ressources](https://github.com/adobe/aem-cloud-migration)


#### Déploiement/Activation

1. [Déploiement sur le git Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html?lang=fr#managing-code)
2. Exécutez le code client via le [pipeline de qualité de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=fr#how-to-use).
3. [Déploiement sur l’environnement de développement](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging)
4. [**Migration uniquement**] Transfert de contenu à l’aide de packages ou de l’[outil de transfert de contenu ](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md)(CTT)
5. Réalisez les cycles de test recommandés (détection de fumée, contrôle qualité et autres)
6. Convertissez vers le pipeline de production de Cloud Manager
7. Validation du test de fumée
8. Activation

<br>

### Post-activation

Lors de la phase de post-activation, vous devez veiller à nettoyer les fichiers temporaires, revoir les bonnes pratiques de développement continu et gérer les journaux.

>[!TIP]
> Des outils sont disponibles pour résoudre les problèmes liés aux environnements AEM as a Cloud Service
>1. [Developer Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#aem-as-a-cloud-service-development-tools)
>2. [CRX/DE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging)
>3. [Gestion des journaux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)


<br>

### Outils et ressources

| Évaluation | Refactorisation | Modernisation d’Experience Manager | Migration du contenu |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[Analyseur de bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration)</li></li> | <ul><li>[Plug-in Expérience unifiée](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=fr#refactoring-tools)</li></ul> | <ul><li>[Les modèles statiques en modèles modifiables](https://opensource.adobe.com/aem-modernize-tools/pages/tools/page-structure.html)</li><li>[Les configurations de la conception en stratégies](https://opensource.adobe.com/aem-modernize-tools/pages/tools/policy-importer.html) <li>[Les composants de base en composants principaux](https://opensource.adobe.com/aem-modernize-tools/pages/tools/component.html)</li><li>[L’interface utilisateur classique en interface utilisateur tactile](https://opensource.adobe.com/aem-modernize-tools/pages/tools/dialog.html)</li></ul> | <ul><li>[Outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=fr#cloud-migration)</li><li>[Gestionnaire de modules](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=fr#contentmanagement)</li></ul> |

>[!NOTE]
> Pour obtenir une aide supplémentaire, vous pouvez :
>1. [Contacter l’équipe d’assistance Experience Manager](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. Explorer les [communautés et forums Experience Manager](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)

